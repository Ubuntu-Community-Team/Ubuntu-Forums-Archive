---
title: "Help! Installing ubuntu from flash drive"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by madcow2001 on 2012-08-15
I am running windows 7 64 bit, and wanted to try out linux. I downloaded Ubuntu 12.04 desktop, then downloaded the USB installer mentioned on [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows) . I followed the directions, and installed the ISO onto the flash drive.

I rebooted my machine, and booted from USB. I tried to run linux from the flash drive, then got a lot of text. Eventually, it stopped, and it kept repeating this line over and over:

udevd[169]: timeout : killing ' sbin/modprobe -bv pci ..................................... and a lot of jibberish. I have no way of copying the text that I know of, so that's the gist of it.

I tried using a different program to create the flash booter (unetbootin) and tried running from flash drive, and got the same error.

What is going on? All I want to do is try linux out, but this has been an endless pain.

---

### Post by DisturbedDragon on 2012-08-16
Issue is most likely graphics..  Try booting with      pci=noacpi      flag.  If boot is successful, install system and reboot.  Use flag again if required on first boot and install graphics driver.  Normal reboot.

---

### Post by Khal1d on 2012-08-16
You may want to explain to him how to do that. *wink*

---

### Post by madcow2001 on 2012-08-16
> **Khal1d said:**
> You may want to explain to him how to do that. *wink*

it wouldn't be a bad idea. I am an absolute noob at this.

---

### Post by madcow2001 on 2012-08-16
Ok, I booted from the flash drive into the unetbootin splash screen, and hit tab which brought up the extra info. I cant tell you all of the exact parameters that were there, but it ended in 
"--"  I added  "pci=noacpi" without the quotes, and still got the same result. So, Im still shopping for answers.

---

### Post by Khal1d on 2012-08-16
I may be able to help "slighty".


1. Did you burn it correctly?

You can find a howto on CD burning here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)


2. Did you check to see if the .iso file was complete, as in did not include any errors?

You can find how to check that here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Scroll down to " MD5SUM on Windows " , or just ctr+f and type it in.

That's all I can think of with my limited knowledge...and if my post seems too obvious and insults you in any way, then I apologize in advance... :(

*EDIT*

> **DisturbedDragon said:**
> Issue is most likely graphics..  Try  booting with      pci=noacpi      flag.  If boot is successful, install  system and reboot.  Use flag again if required on first boot and install  graphics driver.  Normal reboot.

I was trying to install Ubuntu on my USB keychain (full install, not persistant), and found what Disturbed Dragon was talking about. Furthermore, I found someone who explains it in detail:

[http://askubuntu.com/questions/129116/12-04-wont-boot-from-live-cd-or-usb](http://askubuntu.com/questions/129116/12-04-wont-boot-from-live-cd-or-usb)

Please scroll down to Irrational John's comment, you will notice the login screen pictures. He explains how by pressing any button with the "keyboard = Happy Man" logos on screen, you can pull up extra info. Hit F6 and go down to nomodereset and press 'space', an (X) should appear next to it.

If that works, and you can boot in then you NEED TO FIND A PERMANENT FIX! This will only work for the current session. I'm unfortunately too tired to even type at the moment, and will se if I can find a permanent fix for you tomorrow.

Regards,

The self proclaimed linux n00b

---

