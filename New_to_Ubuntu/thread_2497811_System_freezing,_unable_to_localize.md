---
title: "System freezing, unable to localize"
date: 2024-05-18
forum: New to Ubuntu
---

### Post by jacobjons on 2024-05-18
Hello everyone,

Thank you in advance for reading this.

The other day, I reformatted my Win11pro C: drive to a full install of ubuntu desktop 24.04, and the process went smoothly. However, since then, my system has been randomly freezing and rebooting. Sometimes while I'm at the system, sometimes when I'm out of the room or sleeping. (Screensaver disabled.)

My system is a Minisforum HX90 mini pc: AMD Ryzen 9 5900HX, 32GB RAM, 1TB M.2 NVMe boot, 2x 1TB SSD, ZFS chosen during the install.

The freezing seems to be happening without rhyme or reason, lightweight loads of mainly youtube and other research on firefox (125.0.2) and using VLC (3.0.20) for background music. I am also using PIA (v3.5.7) as a VPN. Connected via wi-fi, bt for speaker, mouse/kbd are usb wired. Nothing exotic or fancy.

The default system monitor and snap installed psensor do not show any resource challenges or heat issues. I used the boot option memtest to check my ram (it passed, no faults found).

I don't know where to find relevant logs, or even if I need to initiate log generation. I don't know what to check next. I'd appreciate ideas.

Thank you,
JJ

Edit to add:
x@x-HX90:~$ last
x        tty2         tty2             Sat May 18 13:14   still logged in
x        seat0        login screen     Sat May 18 13:14   still logged in
reboot   system boot  6.8.0-31-generic Sat May 18 13:14   still running
x        tty2         tty2             Sat May 18 04:00 - crash  (09:13)
x        seat0        login screen     Sat May 18 04:00 - crash  (09:13)
reboot   system boot  6.8.0-31-generic Sat May 18 04:00   still running
x        tty2         tty2             Sat May 18 02:09 - crash  (01:50)
x        seat0        login screen     Sat May 18 02:09 - crash  (01:50)
reboot   system boot  6.8.0-31-generic Sat May 18 02:09   still running
x        tty2         tty2             Fri May 17 20:41 - crash  (05:27)
x        seat0        login screen     Fri May 17 20:41 - crash  (05:27)
reboot   system boot  6.8.0-31-generic Fri May 17 20:40   still running
x        tty2         tty2             Thu May 16 20:47 - crash  (23:53)
x        seat0        login screen     Thu May 16 20:47 - crash  (23:53)
reboot   system boot  6.8.0-31-generic Thu May 16 20:45   still running

wtmp begins Thu May 16 20:45:57 2024

---

### Post by currentshaft on 2024-05-19
2

---

### Post by jacobjons on 2024-10-23
My apologies for bringing this thread back up, but I do so with an update and question... 

The update is that the system still won't boot. During the boot-up sequence, the system freezes immediately after the usb devices are recognized. I don't know if the freeze occurs during the usb initialization sequence or as the next step begins.

During boot-up, what is initialized/loaded after the usb devices are identified? (I'm looking for an idea as to what part of the hardware failed.)

Still using 24.04 with Livepatch updates (moved the boot m.2 to another system).

Thank you,
JJ

---

### Post by him610 on 2024-10-25
Logs can be found at */var/log*

Have you tried booting with *Try Ubuntu* from the installation media?

Just so we can see more about your system, please post results between code tags,
```
lsblk && inxi -bxz
```

---

### Post by vmpx on 2024-10-31
Try nomodeset parameter in GRUB.

---

