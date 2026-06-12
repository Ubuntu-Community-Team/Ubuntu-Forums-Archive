---
title: "Can't install Wubi"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by carusoswi on 2013-02-17
Need to load 12.10 onto my son's new laptop, win8 64.
Live disc does not see the win8 partition, so we decided to go with WUBI.

When we click on the WUBI.exe file from within windows, a dialog box pops up offering us these choices:

Install Ubuntu - reboot now
Learn more

If I reboot, the live cd boots into the familiar installation screen where we are presented with the problem that Ubuntu does not find another OS on the machine.

How do I get WUBI to install from within win8?

I'm really not new to this.  Have installed dual boot machines aplenty, have installed WUBI, no previous problems.

What is going on?

Help needed/appreciated.

Caruso

---

### Post by bcbc on 2013-02-17
If the computer came with Windows 8 preinstalled then Wubi will not work. Wubi only supports computers that boot with BIOS, not UEFI (all new computers use UEFI).

See [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system]("http://askubuntu.com/q/221835/14916")

---

### Post by presence1960 on 2013-02-17
You are going to have to install Ubuntu in UEFI mode because that is how windows 8 is booting. As bcbc already said wubi is out. I would check out the how to on installing Ubuntu in UEFI before attempting to do so.

---

