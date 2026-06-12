---
title: "Ubuntu boot error (No Bootable Devide --Insert boot disk and press any key)"
date: 2015-04-19
forum: New to Ubuntu
---

### Post by benjamin40 on 2015-04-19
WARNING: I am a noob when it comes to computers, so please bare with me.

So, I just started trying to install Ubuntu on my laptop today ([[LEFT]HP Pavilion g6-2253sg[/LEFT]]("http://www.2013laptop.com/hp-pavilion-g6-2253sg-review") running Windows 8.1) and whenever I select my USB Hard drive from the boot options, it goes to a screen that says "No Bootable Devide --Insert boot disk and press any key". I have changed the boot order in the UEFI, disabled secure bootup, and all that. Does anyone know how to fix this issue? Thanks for the help.

---

### Post by ricky-flammia on 2015-04-19
How did you create this bootable device? Does the device contain any other files? Thanks. If you are creating your bootable device on Windows, here is a tutorial. [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by benjamin40 on 2015-04-19
I created this by using to "Universal USB Installer" to put the Ubuntu image on my hard drive. And no, it doesn't have any other files on it.

---

### Post by ricky-flammia on 2015-04-19
Installing Ubuntu from a live USB flash drive or live DVD would probably save you a bit of trouble. Can you do this instead? If not, here is a link that may help you with installing it from your current device. [http://askubuntu.com/questions/501187/installing-ubuntu-from-an-external-hard-drive](http://askubuntu.com/questions/501187/installing-ubuntu-from-an-external-hard-drive)

---

### Post by yancek on 2015-04-19
Looking at the UUI home page, I don't see anything indicating it can do a "frugal install", that is installing to a partition on your drive which can be done with unetbootin.  UUI is meant to create a bootable flash drive which you can then boot to install Ubuntu (or most any Linux) to a hard drive partition.  A little more detail on exactly what you did might help someone to help you.

---

### Post by oldfred on 2015-04-20
Some UEFI also require you to turn of USB bootable device as an option. And maybe UEFI or BIOS as how USB flash drive may be booted.
But if flash drive not correct configured or download not correct then those can also be issues.
A few also have issues with certain brands of flash drives or certain USB ports. Some only let you boot from one port or have issues with USB3 ports. Others have no issues.

Most USB software that creates a bootable image erase entire drive. If an external hard drive you may not want that, and then better to use a smaller flash drive. 2GB or more.

---

