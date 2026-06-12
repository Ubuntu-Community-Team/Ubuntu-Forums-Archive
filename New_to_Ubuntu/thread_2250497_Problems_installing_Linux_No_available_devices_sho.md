---
title: "Problems installing Linux: No available devices shown after/dev/sda"
date: 2014-10-29
forum: New to Ubuntu
---

### Post by cameron16 on 2014-10-29
I've been trying to install ubuntu alongside Windows 8.1 with a dvd. I have already disabled secure boot and created empty space on my hard drive to create the root partition, and I have been able to start the installation process. For some reason, I do not get an option during the Installation Type step; instead it goes straight to what seems to be the "something else" step. This would not be a problem, except there are no displayed devices under Device for boot loader installation. Did I skip a step or do something wrong? I haven't been able to find this problem anywhere else, so it is entirely possible that I screwed something up, since I am very new to this.

---

### Post by yancek on 2014-10-29
If you have windows 8 pre-installed, you are probably booting in uefi mode and you need to install Ubuntu uefi also or you will have problems.  I don't use uefi so the best I can do is suggest you read the information at the Ubuntu site below which explains it:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by grahammechanical on 2014-10-29
Are you trying to install Ubuntu inside Windows 8 by using wubi.exe? If so. don't. Wubi.exe is not developed or supported any more and it does not work with Windows 8.

Regards.

---

### Post by cressrt2 on 2014-10-29
I followed this link to install [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html). You may have an issue with the "Boot Repair" but can normally find a way to resolve.

---

### Post by cameron16 on 2014-12-07
Sorry for not replying to the thread for so long. I actually gave up on installing it on my desktop for awhile and just installed it on my laptop, which worked fine. Decided to give it another try recently and found this article: [http://www.pendrivelinux.com/ubuntu-installer-cant-find-my-sata-drive/](http://www.pendrivelinux.com/ubuntu-installer-cant-find-my-sata-drive/) . This solved my problem, if anyone else has this issue. Thank you for your advice.

---

