---
title: "ive got a problem with booting"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Periswell on 2008-09-28
hello

my sister has an eee and today i thought i would put ubuntu on it so i followed the instructions on [https://help.ubuntu.com/community/EeePC/Installation](https://help.ubuntu.com/community/EeePC/Installation) using my dell laptop but i did  not realise that it would put my computer on the usb stick as well as what i had intended. now i cannot run my computer without having the usb stick in. and also it does not work on the eee. please can someone tell me how to put my partition back on my computer preferably without losing my documents and settings.
-josh

---

### Post by kansasnoob on 2008-09-28
> **Periswell said:**
> hello

my sister has an eee and today i thought i would put ubuntu on it so i followed the instructions on [https://help.ubuntu.com/community/EeePC/Installation](https://help.ubuntu.com/community/EeePC/Installation) using my dell laptop but i did  not realise that it would put my computer on the usb stick as well as what i had intended. now i cannot run my computer without having the usb stick in. and also it does not work on the eee. please can someone tell me how to put my partition back on my computer preferably without losing my documents and settings.
-josh

We need to know what the operating system is on your computer.

 I Think what's happened is that Grub overwrote the mbr.

---

### Post by Periswell on 2008-09-28
the operating system i have is openGEU and the one i wanted to put on my sisters eee is ubuntu

---

### Post by kansasnoob on 2008-09-28
And it's openGEU that won't boot without the external drive plugged in?

---

### Post by kansasnoob on 2008-09-28
> **kansasnoob said:**
> And it's openGEU that won't boot without the external drive plugged in?

If so I'm looking to be sure that openGEU uses the grub bootloader, if so you just need to restore grub, but I don't know open GEU.

I'm looking:

[http://opengeuwiki-en.intilinux.com/index.php?title=Main_Page](http://opengeuwiki-en.intilinux.com/index.php?title=Main_Page)

---

### Post by kansasnoob on 2008-09-28
Since it's an Ubuntu derivative you should be able to do this:

[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)

Basically same instructions here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Of course you'll want the external drive unplugged when you do this.

---

### Post by kansasnoob on 2008-09-28
Once you've recovered your grub here's a good source for pendrive installations:

[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

---

### Post by telltommy on 2008-09-28
I have an eee pc and it can be restored to factory by hitting f9 on boot up. you really have to hammer on it. I don't know if it's still there. The recovery is on a hidden partition. I just ordered on ebay  a flashdrive with Ubuntu on it for my eee pc.

---

