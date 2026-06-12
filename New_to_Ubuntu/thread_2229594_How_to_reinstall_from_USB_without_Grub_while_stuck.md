---
title: "How to reinstall from USB without Grub while stuck in text only"
date: 2014-06-14
forum: New to Ubuntu
---

### Post by tyler43 on 2014-06-14
Hi all,

I just installed Ubuntu 14.04 (maybe 10 hours ago) and already managed to render my computer useless. Of course I didn't read anything and just started poking around and now I'm stuck on the splash screen. I'd rather not get into figuring out the problem and just start from scratch. My issue is I never edited grub so holding down shift when I boot doesn't do anything. Is there some way to reinstall from a thumb drive without grub or edit it in text only? 

Help would be greatly appreciated because I have an increasingly unbearable urge to throw my laptop out the window.

---

### Post by Bucky Ball on 2014-06-14
Welcome. Why don't you just reinstall as per normal? Why would you want to preserve grub?

Choose to boot from the USB (by entering the BIOS at boot or hitting whatever key you need to to get a list of boot devices) and fire away with the install ...

---

### Post by yancek on 2014-06-14
If you don't get the Grub boot menu when booting your drive, then something obviously went wrong with the install.  There is not way for anyone here to know since we don't know what happened or whether Ubuntu is the only OS on the machine.  There should be no reason to edit Grub as it is generally setup during the installation.  Installing from a flash drive is pretty simple.  What did you use to install the first time and why not use it again?

Incidentally, there are a large number of tutorials on installing Ubuntu, some with images showing practically every step of the install.  Might help to read a few of those.

---

### Post by tyler43 on 2014-06-14
Hey, thanks for the replies. I was convinced I couldn't get it to boot into BIOS...probably pounding on the wrong key like an idiot (new computer). I can't believe I had to resort to starting a thread over something that dumb. Thanks again for the help though, I'm sure I'll have plenty of legitimate questions.

---

### Post by oldfred on 2014-06-14
If a new UEFI system, do not re run an auto install. It will erase entire system.
You really need to back up Windows  & efi partition and review details of installs.

       Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Lots of detail and links in the link in my signature for UEFI installs. Many show screen shots.

Installs to a second drive need to use Something Else to install, which is what you need even if one drive. So many useful screen shots in these links:

 Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by caver12 on 2014-06-14
This is a good resource to have on hand;
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)
Can save you from reinstalling just because of a corrupted Grub and you can't , or don't know how, to get into your installation. Easy to use.

---

### Post by Bucky Ball on 2014-06-14
> **caver12 said:**
> This is a good resource to have on hand;
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)
Can save you from reinstalling just because of a corrupted Grub and you can't , or don't know how, to get into your installation. Easy to use.

Very true, but this is much more informative:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

;)

---

