---
title: "Facing problems installing Ubuntu 14.04 on my Dell Inspiron i5 6300HQ"
date: 2016-04-12
forum: New to Ubuntu
---

### Post by c.tejas.rao on 2016-04-12
When I try to install ubuntu from a boot able USB stick, the initial load screen starts but hangs immediately. Is there any specific reason for this? Does Ubuntu not support the skylake processors? Or is it something to do with UEFI secure or legacy boot options? Below is an image of the text installation where it gets stuck. I've read a lot of threads but got confused even more. Need some help. Thank you.

---

### Post by mastablasta on 2016-04-12
NVidia chip inside....

try to use nomodeset boot option to get to desktop. [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

install the OS there, then add nvidia drivers and possibly bumblebee and configure it appropriately. hope it works.

---

### Post by mörgæs on 2016-04-12
> **c.tejas.rao said:**
> Does Ubuntu not support the Skylake processors?

14.04 does certainly not but you could try 16.04.

---

### Post by Geoffrey_Arndt on 2016-04-13
First , , , don't use 14.04 with Skylake g6 intel.   Second, the nVidia drivers are not included by default in iso re legal issues (closed, proprietary graphics).   So, you may not get a suitable display using alternate video driver.    The nomodeset boot option provides a way to get a usable screen display (using the basic VESA graphic standard).   This allows the user to use the gui to navigate to the place in system settings where the nvidia drivers may be downloaded and installed.

---

### Post by mastablasta on 2016-04-13
> **mörgæs said:**
> 14.04 does certainly not but you could try 16.04.

now even with HWE?

---

### Post by mörgæs on 2016-04-13
Not in any thread I've read.

Hardware enablement is a way to make 14.04 behave 15.10-ish, but as 15.10 is not necessarily new enough to support Skylake I wouldn't recommend it.

---

### Post by c.tejas.rao on 2016-06-03
the problem is that i can't reach the menu with nomodeset. the ubuntu loading screen either stops running or just doesnt reach the select your language option.. any other solutions? would disabling secure boot be an option? i really want to install ubuntu with eufi secure mode enabled.

Update: Finally managed to get Ubuntu 16.04 running on my laptop! Thanks for the help guys! I managed to install ubuntu 16.04 on my skylake processor with an Nvidia graphic card with UEFI Secure boot mode itself.

How I managed to run ubuntu alongside windows:
1. Create a bootable usb stick.
2. When you boot from USB choose try ubuntu first.
3. Load in text mode (I played with F6 option) and it loaded the OS.
4. I installed Ubuntu once my OS loaded from trying Ubuntu.
5. I did not select installation of 3rd party software during installation as it requested me to turn UEFI Secure boot to disabled.
6. After Ubuntu gets installed, update software via software updater.
7. Go to additional drivers and switch to the proprietary drivers.
8. Once this is done restart your system with your USB stick still connected. ( I did this because when I tried otherwise I faced the soft bug lock up problem which prevented the system from shutting down or restarting)
9. After system restarts you are set to go. Every thing has worked smoothly so far in the last hour for me and I am able to boot both Ubuntu and Windows!

Cheers!

Guys do update any other techniques that you have managed to be successful with!

---

