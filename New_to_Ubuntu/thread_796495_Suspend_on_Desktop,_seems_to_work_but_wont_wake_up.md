---
title: "Suspend on Desktop, seems to work but wont wake up, REISUB, logs attached no eros"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by philinux on 2008-05-16
No errors in log have to hit the power button, reisub.
```
 cat /var/log/pm-suspend.log
Fri May 16 15:30:44 BST 2008: running suspend hooks.
===== Fri May 16 15:30:44 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Fri May 16 15:30:44 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Fri May 16 15:30:44 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Fri May 16 15:30:44 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Fri May 16 15:30:44 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Fri May 16 15:30:44 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Fri May 16 15:30:45 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Fri May 16 15:30:46 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Fri May 16 15:30:46 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Fri May 16 15:30:46 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Fri May 16 15:30:46 BST 2008: done running suspend hooks.
philcb@philcb-desktop:~$ cat /sys/power/disk
[platform] test testproc shutdown reboot 
philcb@philcb-desktop:~$ cat /var/log/pm-suspend.log
Fri May 16 15:30:44 BST 2008: running suspend hooks.
===== Fri May 16 15:30:44 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Fri May 16 15:30:44 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Fri May 16 15:30:44 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Fri May 16 15:30:44 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Fri May 16 15:30:44 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Fri May 16 15:30:44 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Fri May 16 15:30:45 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Fri May 16 15:30:46 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Fri May 16 15:30:46 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Fri May 16 15:30:46 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Fri May 16 15:30:46 BST 2008: done running suspend hooks.
```

---

### Post by philinux on 2008-05-17
bump

---

