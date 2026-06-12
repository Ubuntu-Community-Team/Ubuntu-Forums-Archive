---
title: "Installation Issue"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by pccruzadas on 2013-03-07
Hi,
I am an absolute beginner, I am trying to install Ubuntu with the Windows installer, but unfortunately the installation freezes, how can i solve this issue, thank you.

---

### Post by Ediaan on 2013-03-07
Hi pccruzadas, you need to put your installation file on a DVD or USB Flash Drive and then boot from the DVD or Flash disk.

---

### Post by oldfred on 2013-03-07
What system?

 Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

---

### Post by pccruzadas on 2013-03-07
Thank you Ediaan for replying my post. If i install from a DVD/CD do i loose my Windows XP?

---

### Post by pccruzadas on 2013-03-07
> **Ediaan said:**
> Hi pccruzadas, you need to put your installation file on a DVD or USB Flash Drive and then boot from the DVD or Flash disk.

do i lose Windows XP if i install from a CD?

---

### Post by pccruzadas on 2013-03-07
> **oldfred said:**
> What system?

 Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

do i lose Windows XP if i install from a CD?

---

### Post by bcbc on 2013-03-07
No you don't lose Windows, but make sure that the Ubuntu Installer recognizes Windows and shows you how it is splitting the drive before proceeding. In some cases, the installer won't see Windows and some people have assumed that it will be okay and it is overridden.

If Wubi froze, and you have an nvidia or radeon graphics card, then try booting with nomodeset (and this will be required on a normal install as well): [http://askubuntu.com/q/162075/14916](http://askubuntu.com/q/162075/14916)

---

### Post by Impavidus on 2013-03-07
Asking the same question three times within an hour is overdoing things.

If you install from the cd/dvd/usb you don't have to lose your win XP, because they can be present together as dual boot. However, it's quite common that people do something wrong leading to the loss of windows nonetheless. Therefore you'll have to pay attention and have backups ready of everything important. Instructions can be found here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot). Most reliable way is to make sure you have at most three primary partitions and enough unallocated space on your disk, shinking partitions as necessary using windows tools. It seems that win XP is quite easy in that respect, allowing you to use the linux installer to modify partitions; later windows versions can easely be broken if the partitions are modified by the linux installer.

---

### Post by Mark Phelps on 2013-03-07
> **pccruzadas said:**
> do i lose Windows XP if i install from a CD?

You were already told by oldfred that you NOW have to install wubi from a download, you can't do that anymore from disk.   So, the advice to burn the ISO to DVD or flash drive, for a Wubi install, is incorrect. 

You didn't say what version you were trying to install, but Ubuntu 12.10 will not fit on a CD, anyway, it's too large.

When you do a Wubi install, the Ubuntu installer creates a virtual filesystem INSIDE the Windows filesystem, so you do not lose your existing Windows installation.

---

