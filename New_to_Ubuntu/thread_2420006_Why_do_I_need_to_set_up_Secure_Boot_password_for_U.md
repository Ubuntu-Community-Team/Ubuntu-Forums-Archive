---
title: "Why do I need to set up Secure Boot password for Ubuntu to install drivers?"
date: 2019-05-28
forum: New to Ubuntu
---

### Post by debofsky on 2019-05-28
[COLOR=#1A1A1B][FONT=&quot]Why do I need to set up Secure Boot password for Ubuntu to install drivers?[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]I installed it with secure boot unchecked, so I don't know if I have those drivers? Firefox seems to tear when scrolling so I think there are some old default linux graphics drivers.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]If I set it up, do I need to enter this password every time GRUB loads?[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]Or is it similar to Windows' BitLocker, only asks for key if somethings changed (f.i. there's connected new USB drive)[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]Don't know if it matters I dual boot Windows 10 + Ubuntu 19.04[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]Many thanks in advance![/FONT][/COLOR]

---

### Post by LwIh%*7 on 2019-05-28
Is Secure Boot enabled in your BIOS Motherboard setting? Secure Boot isn't 100% yet for Ubuntu if I'm not mistaken and thus I've set the configuration for Secure Boot to "Other OSes" setting to disable Secure Boot then it won't request passwords or shouldn't. Please see [https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot) for further details.

---

