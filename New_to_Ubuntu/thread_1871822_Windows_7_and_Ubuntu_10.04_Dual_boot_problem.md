---
title: "Windows 7 and Ubuntu 10.04 Dual boot problem"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by nykkhsd on 2011-10-29
Hi all , i installed windows 7 after that ubuntu ! in grub windows isn't showing , i was trying to recover grub , but every time grub is not finding windows 7 . Please help me !

ubuntu is on sda2
windows 7 on sda7

---

### Post by LinuxFan999 on 2011-10-29
Try downloading and burning the GParted live CD.
Link: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Then boot from the CD and Open GParted.
Do you see an NTFS partition?
If not, you accidentally deleted Windows 7 while installing
Ubuntu, and will need to reinstall it.

---

### Post by nykkhsd on 2011-10-29
> **LinuxFan999 said:**
> Try downloading and burning the GParted live CD.
Link: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Then boot from the CD and Open GParted.
Do you see an NTFS partition?
If not, you accidentally deleted Windows 7 while installing
Ubuntu, and will need to reinstall it.

no , windows is installed 100%!

---

### Post by abedayyad on 2011-10-29
You just said that you couldn't see it though ... if you go to a command line, and type "df", what do you get? Do you see the NTFS partition any where?

---

### Post by nykkhsd on 2011-10-29
> **abedayyad said:**
> You just said that you couldn't see it though ... if you go to a command line, and type "df", what do you get? Do you see the NTFS partition any where?

yes ,i see it !
***i saw that windows partition is logical !***

---

### Post by tartalo on 2011-10-29
Does this help?
[http://www.linuxquestions.org/questions/debian-26/debian-squeeze-grub-doesnt-detect-windows-partition-on-install-830836/](http://www.linuxquestions.org/questions/debian-26/debian-squeeze-grub-doesnt-detect-windows-partition-on-install-830836/)

---

### Post by nykkhsd on 2011-10-29
> **tartalo said:**
> Does this help?
[http://www.linuxquestions.org/questions/debian-26/debian-squeeze-grub-doesnt-detect-windows-partition-on-install-830836/](http://www.linuxquestions.org/questions/debian-26/debian-squeeze-grub-doesnt-detect-windows-partition-on-install-830836/)

no :(

---

### Post by ubu_dynamite on 2011-10-29
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by nykkhsd on 2011-10-29
> **ubu_dynamite said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

tried , don't help

---

### Post by Hreinsi on 2011-10-29
[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

this has save me 4-5 times after installing win 7

just boot from live cd and install in terminal

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair-ubuntu

---

### Post by nykkhsd on 2011-10-29
> **Hreinsi said:**
> [http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

this has save me 4-5 times after installing win 7

just boot from live cd and install in terminal

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair-ubuntu

tried , don't help


now i'm trying to install windows 7 on primary partition , i will post result later ;)

---

### Post by satanselbow on 2011-10-29
It can be done - but I doubt you will find (m)anyone that has done it successfully longterm.

Link of doom: [http://www.goodells.net/multiboot/](http://www.goodells.net/multiboot/)

I would seriously suggest backing up any data (on w7 and/or ubu) to an external drive - format your hdd and then install w7 1st to a primary partition and create an extended partition and logical partitions for ubu :(

---

### Post by tartalo on 2011-10-29
Also:
[http://ubuntuforums.org/showthread.php?t=1705363](http://ubuntuforums.org/showthread.php?t=1705363)

---

