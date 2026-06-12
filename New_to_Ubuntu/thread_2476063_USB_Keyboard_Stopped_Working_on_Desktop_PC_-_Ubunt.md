---
title: "USB Keyboard Stopped Working on Desktop PC - Ubuntu 20.04"
date: 2022-06-16
forum: New to Ubuntu
---

### Post by penguinize on 2022-06-16
I am new to Ubuntu. I am using standard Ubuntu 20.04, on a Lenovo ThinkCentre. Updated from 18.04 LTS, in Oct 2020.

The keyboard stopped working after recent software updates:

Start-Date: 2022-06-14  03:46:48
Commandline: aptdaemon role='role-commit-packages' sender=':1.2523'
Upgrade: libfprint-2-2:amd64 (1:1.90.2+tod1-0ubuntu1~20.04.7, 1:1.90.2+tod1-0ubuntu1~20.04.8), google-chrome-stable:amd64 (102.0.5005.61-1, 102.0.5005.115-1), xdg-desktop-portal-gtk:amd64 (1.6.0-1build1, 1.6.0-1ubuntu1), libkeyutils1:amd64 (1.6-6ubuntu1, 1.6-6ubuntu1.1), xdg-desktop-portal:amd64 (1.6.0-1, 1.6.0-1ubuntu1)
End-Date: 2022-06-14  03:47:02

After installing & rebooting, the keyboard was completely unresponsive, but the mouse still works.

What I have tried:
1. Different USB ports.
2. The procedures described here: [https://askubuntu.com/questions/1340257/ubuntu-20-04-sometimes-after-boot-the-keyboard-and-trackpad-dont-work-but-the](https://askubuntu.com/questions/1340257/ubuntu-20-04-sometimes-after-boot-the-keyboard-and-trackpad-dont-work-but-the)
   a. Install the Hardware Enablement Stack
   b. Install the X11 Input Drivers
   c. Check the Accessibility Settings

None of these resolved the issue. This keyboard has never failed before now.

---

### Post by Autodave on 2022-06-16
By chance, have you tried another keyboard?

---

### Post by Impavidus on 2022-06-16
Does the keyboard work in bios/uefi? In the grub menu? In recovery mode? On a live disk?

Can you switch to the console (ctrl-alt-F2 or some other F-key, it varies. One of the ctrl-alt-Fx keys should bring you back to the GUI)? If you can, does eveything work there?

[s]Have you tried a different usb port?[/s] Or a different keyboard (if you have one)?

---

### Post by penguinize on 2022-06-23
The keyboard did not work before, during, or after login; could not access bios/uefi. Looks like a hardware failure; obtained new keyboard, which works. Thank you for your help.

---

