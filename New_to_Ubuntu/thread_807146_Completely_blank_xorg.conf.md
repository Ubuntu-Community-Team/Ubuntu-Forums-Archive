---
title: "Completely blank xorg.conf?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Raavea on 2008-05-25
Hi all, I've just built a new computer. Problems galore, and I'm in far over my head.

It's a 64-bit crossfire machine, with two Sapphire Radeon HD 2600 Pro in it. And I can't get them to work.

 It keeps booting into safe mode and I don't know what to do. So I've been following all the guides I can find as it must be a graphics card issue. I've had to reinstall four times so far, and I've wasted every one of my weekends to no avail. I reinstalled AGAIN a short time ago but now that I'm trying to follow [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way"), I notice that my xorg.conf is COMPLETELY BLANK!!!

I'm pretty sure this is uberbad and I don't want to turn my PC off as I'm pretty sure it won't turn back on and I really don't know what to do!

 Can anyone help? Quickly, if possible?

---

### Post by trebor on 2008-05-25
> **Raavea said:**
> Hi all, I've just built a new computer. Problems galore, and I'm in far over my head.

It's a 64-bit crossfire machine, with two Sapphire Radeon HD 2600 Pro in it. And I can't get them to work.

 It keeps booting into safe mode and I don't know what to do. So I've been following all the guides I can find as it must be a graphics card issue. I've had to reinstall four times so far, and I've wasted every one of my weekends to no avail. I reinstalled AGAIN a short time ago but now that I'm trying to follow [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way"), I notice that my xorg.conf is COMPLETELY BLANK!!!

I'm pretty sure this is uberbad and I don't want to turn my PC off as I'm pretty sure it won't turn back on and I really don't know what to do!

 Can anyone help? Quickly, if possible?

If you have your xorg file backed up you can use that.  If not you can run this code

"sudo dpkg-reconfigure -phigh xserver-xorg"

Taht will recreate your xorg file to a default state.  You will have to edit it agian if you made any edit to it before.  If not, then you will not lose anything by using this code.  good luck.

---

