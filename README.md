# uptime

Monitor externo de los sitios de Victor Llerena, con GitHub Actions.

- **Cada 5 minutos** revisa que cada sitio responda (2xx o 3xx y, si se pide, un texto esperado), con tres intentos antes de darlo por caído.
- **Si algo cae**, abre un issue «Caído: …» que menciona al dueño, y la ejecución falla (GitHub avisa por correo). Cuando vuelve, el issue se cierra solo.
- **Certificados:** abre un issue si alguno vence en menos de 14 días.
- Vive fuera del servidor a propósito: si el servidor cae, el vigilante interno cae con él.

Los objetivos están en el secreto `MONITOR_TARGETS`, una línea por sitio: `alias|url|texto-esperado-opcional`. Las líneas que empiezan con `#` se ignoran. Las URLs y los hosts se enmascaran en los logs.

GitHub puede retrasar unos minutos las ejecuciones programadas. El workflow `keepalive` hace un commit al mes para que GitHub no apague el cron por inactividad.
