---
title: "GRUB &quot;hanging&quot; on boot before allowing input (Dual Boot Windows 10, Ubuntu 18.04)"
date: 2020-02-15
forum: New to Ubuntu
---

### Post by ignisnl on 2020-02-15
[FONT=verdana]G'day all.[/FONT]
[FONT=verdana]I've got Ubuntu 18.04 and Windows 10 dual booted on a Surface Laptop 3. I have GRUB configured to allow both Ubuntu and "Windows Boot Manager" to be chosen from it. However, whenever I start the laptop up, and after the initial Microsoft logo splash, there is always a period of about 15 seconds within which no keyboard input registers - not arrows, not Enter, etc. After about 15 seconds, a keyboard icon appears in the bottom right corner, at which point GRUB works completely as normal.[/FONT]
[FONT=verdana]I know that this has nothing to do with GRUB_TIMEOUT, as the timer at the bottom that represents it is also frozen until the keyboard icon appears. I also believe that it is a GRUB-specific issue, as when I change to boot from Windows Boot Manager in the UEFI, Windows boots without any issues.[/FONT]
[FONT=verdana]I've been searching online for a while and can't find anyone with a similar issue. Does anyone know what might be causing this, and what I could do to reduce this "hang" time or avoid it completely?[/FONT]
[FONT=verdana]Let me know if you need any additional info. Thanks in advance![/FONT]

---

### Post by alirezas on 2020-02-16
Have you updated grub yet?

---

