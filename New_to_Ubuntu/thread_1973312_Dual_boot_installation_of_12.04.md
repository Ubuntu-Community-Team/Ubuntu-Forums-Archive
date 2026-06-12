---
title: "Dual boot installation of 12.04"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by ajdrew06 on 2012-05-04
Hi All,

I downloaded Ubuntu 12.04 to a USB stick. I booted in the Live "CD" mode on the USB stick. I want to install Ubuntu along side with Windows 7. However, when I get the option of installing side by side, it reboot. There must be something I'm doing wrong. Please advise.

-Drew

---

### Post by 2ta8gdfte on 2012-05-04
> **ajdrew06 said:**
> Hi All,

I downloaded Ubuntu 12.04 to a USB stick. I booted in the Live "CD" mode on the USB stick. I want to install Ubuntu along side with Windows 7. However, when I get the option of installing side by side, it reboot. There must be something I'm doing wrong. Please advise.

-Drew
 Hard to say with that information. Many computer manufacturers release windows with four primary partitions, that is that limit on one HD, look in gparted on the ubuntu live cd session and see if this is the case. 

You also really to be safe would let windows resize itself leaving a unallocated for ubuntu to be installed in. This lets you confirm that windows is booting and running after a resize before installing. Also back up the windows with its imager and make a recovery disc as well before you do anything.

You also can check the md5sum of the ISO to see if it is good.    

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by *^kyfds( on 2012-05-04
if you're trying to install Ubuntu alongside windows you may as well used [wubi.]("http://www.ubuntu.com/download/desktop/windows-installer")

if you don't want to, check your live cd. the same happened to me when the iso downloaded incorrectly.

---

### Post by Toporagno on 2012-05-04
I don't know if you have already see this, is a guide on how to install from a usb stick [https://help.ubuntu.com/12.04/installation-guide/amd64/boot-usb-files.html](https://help.ubuntu.com/12.04/installation-guide/amd64/boot-usb-files.html)
Hope this can help..

---

### Post by chehsunliu on 2012-05-05
> **ajdrew06 said:**
> Hi All,

I downloaded Ubuntu 12.04 to a USB stick. I booted in the Live "CD" mode on the USB stick. I want to install Ubuntu along side with Windows 7. However, when I get the option of installing side by side, it reboot. There must be something I'm doing wrong. Please advise.

-Drew

I have the same problem on my laptop. I use "Universal usb installer" to build my live usb. I have checked the md5 of the iso file (Ubuntu 12.04 desktop amd64), and it's correct. I still don't know why the laptop reboots every time I click this button...

---

### Post by ajdrew06 on 2012-05-05
I tried Wubi. I got it to work, but with a high level of dissatisfaction. It was ridiculously slow; I uninstalled it after I read that Wubi is significantly slower than other dual boot options. However, I have not been able to find any other options. I had XP and Ubuntu 10.04 with no problems on my old laptop. I installed XP, then used the Live CD to install 10.04 with dual boot. I don't get why the Live CD doesn't work. Please advise.

---

### Post by chehsunliu on 2012-05-06
> **ajdrew06 said:**
> I tried Wubi. I got it to work, but with a high level of dissatisfaction. It was ridiculously slow; I uninstalled it after I read that Wubi is significantly slower than other dual boot options. However, I have not been able to find any other options. I had XP and Ubuntu 10.04 with no problems on my old laptop. I installed XP, then used the Live CD to install 10.04 with dual boot. I don't get why the Live CD doesn't work. Please advise.

Yesterday I noticed that the option display on the installation menu is "inside Windows 7" instead of "alongside Windows 7". And I found that my disk has reached the maximum of four partitions (three primary and other logical partitions). So I backup D: (primary one) and delete it, and the problem is solved.

---

### Post by Prescilla on 2012-05-06
Have you tried a LiveCD in an actual CD?
Maybe there's something wrong with the LiveCD on your USB stick.

---

### Post by anthony two tees on 2012-05-06
Real beginner and at age 86.  Old dog, new tricks?
Anyway Had trouble with version 12.04.  would not boot up.  Tried version 11.10 and updated to 12.04.  All in unison for keeping my Windows 7 OS.  Now it boots up to ubuntu only.  How do I get to the boot giving me a choice?  Is there any way to see if Windows 7 still exists on my computer? Any help will be a learning process.

---

### Post by wilee-nilee on 2012-05-06
> **anthony two tees said:**
> Real beginner and at age 86.  Old dog, new tricks?
Anyway Had trouble with version 12.04.  would not boot up.  Tried version 11.10 and updated to 12.04.  All in unison for keeping my Windows 7 OS.  Now it boots up to ubuntu only.  How do I get to the boot giving me a choice?  Is there any way to see if Windows 7 still exists on my computer? Any help will be a learning process.

Try running in the Ubuntu terminal.

```
sudo update-grub
```

If this does not work start your own thread, if we mix users and problems things can get a bit hard to  follow. :)

In that new thread from your Ubuntu install run this script extract it to your desktop and run this command and post the results.text that will appear on your desktop

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

