---
title: "[SOLVED] Deleting ubuntu broke my eee?"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by ZankerH on 2008-09-28
So I've tried installing ubuntu-eee on my new netbook. I've set aside a half of the 16gb SSD for it, keeping the rest of the default xandros installation intact. Dual booting worked fine, until I've decided I prefer shorter boot times and stable networking, so I've decided to delete ubuntu by deleting it's partitions and extending the Xandros ones back across the entire disk. Now, when I try to boot, I get a GRUB error 22.

Did I just become a proud owner of a $400 brick?

---

### Post by jamesrfla on 2008-09-28
What you need to do is reinstall Xandros boot loader. If you want GRUB boot loader go hear. [http://supergrubdisk.org/](http://supergrubdisk.org/) Then put it on a CD, or flash drive.

---

### Post by kansasnoob on 2008-09-28
I see from a little googling that Xandros could use either Lilo or Grub, and I don't know Xandros. But you need to restore the bootloader. How I'm not sure in Xandros:confused:

---

### Post by ZankerH on 2008-09-28
> **jamesrfla said:**
> What you need to do is reinstall Xandros boot loader. If you want GRUB boot loader go hear. [http://supergrubdisk.org/](http://supergrubdisk.org/) Then put it on a CD, or flash drive.

How can I reinstall the xandros boot loader? I can't even boot from a flash drive, I get the error right away.

---

### Post by kansasnoob on 2008-09-28
[http://forums.xandros.com/viewtopic.php?t=32635](http://forums.xandros.com/viewtopic.php?t=32635)

---

### Post by jamesrfla on 2008-09-28
You should be able to get into the BIOS before you get the error. It is different on all computer but try Esc, Del, or F1 when you turn it on before you get the error. After you get in their look for something about boot priority's and change it so you can boot of off USB.

---

### Post by ZankerH on 2008-09-28
> **kansasnoob said:**
> [http://forums.xandros.com/viewtopic.php?t=32635](http://forums.xandros.com/viewtopic.php?t=32635)

You don't appear to understand my problem. I'm unable to boot from any device at all, I get the error right at the start up.

---

### Post by panhandle on 2008-09-28
1

---

### Post by ZankerH on 2008-09-28
> **panhandle said:**
> 1


What was that?

---

### Post by panhandle on 2008-09-28
read the reason for editing!:)

---

### Post by ZankerH on 2008-09-28
OK, a little update: I'm able to get into BIOS by holding F2 during startup, but no matter how I change the boot device priority, I still end up with the GRUB error.

---

### Post by panhandle on 2008-09-28
Start here:

[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

Also, the eee pc forums:

[http://forum.eeeuser.com/viewtopic.php?pid=392901](http://forum.eeeuser.com/viewtopic.php?pid=392901)

---

### Post by jamesrfla on 2008-09-28
Seems like it is not booting off the flash drive. Are you sure you put that program on right? Do you have a USB CD drive you can use other than a flash drive?

---

### Post by ZankerH on 2008-09-28
> **jamesrfla said:**
> Seems like it is not booting off the flash drive. Are you sure you put that program on right? Do you have a USB CD drive you can use other than a flash drive?

I don't have a usb CD drive, but I'm pretty sure GRUB was installed right, I could dual-boot between xandros and ubuntu just fine.

---

### Post by ZankerH on 2008-09-28
When I set removable media as the first boot device and disabled the SSD boot option, I get the following error, with my flash drive inserted:

Reboot or Select proper Boot device
or Insert Boot Media in selected Boot device and press a key

---

### Post by jamesrfla on 2008-09-28
Something isn't right. It isn't seeing anything to boot of off on the flash drive. Make sure you downloaded the right file hear [http://www.supergrubdisk.org/index.php?pid=7](http://www.supergrubdisk.org/index.php?pid=7) If the file is zipped you need to unzip it to your flash drive. This should help you boot off of the USB flash drive. [http://www.supergrubdisk.org/wiki/SGD_Howto_Boot](http://www.supergrubdisk.org/wiki/SGD_Howto_Boot) Good Luck!!

---

### Post by ZankerH on 2008-09-28
> **jamesrfla said:**
> Something isn't right. It isn't seeing anything to boot of off on the flash drive. Make sure you downloaded the right file hear [http://www.supergrubdisk.org/index.php?pid=7](http://www.supergrubdisk.org/index.php?pid=7) If the file is zipped you need to unzip it to your flash drive. This should help you boot off of the USB flash drive. [http://www.supergrubdisk.org/wiki/SGD_Howto_Boot](http://www.supergrubdisk.org/wiki/SGD_Howto_Boot) Good Luck!!

I've done that. I've also tried booting from the ubuntu live flash drive, and likewise, it isn't recognised. The data access light on the drive flashes during startup, but then it stops and I get the error.

---

### Post by ZankerH on 2008-09-28
I've miraculously managed to boot into the ubuntu live flash drive. How do I fix/remove grub from there? Keep in mind I don't have any networking on the eee.

EDIT: An idea, is this a strike of genius or a bad case of "3am maths"? : 

I'm going to install ubuntu, with a separate /boot/ partition, then delete everything but the /boot/. Will this work?

---

### Post by jamesrfla on 2008-09-28
This might help [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by aysiu on 2008-09-28
I think you press Escape while booting up to boot from USB instead of heading to Grub.

---

### Post by ZankerH on 2008-09-28
> **jamesrfla said:**
> This might help [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

The merciful and allmighty God bless you. Thanks!

---

### Post by ZankerH on 2008-09-28
> **aysiu said:**
> I think you press Escape while booting up to boot from USB instead of heading to Grub.

Yeah, that was it. I had to go to bios and disable the built-in SSD (on which ubuntu installed GRUB, I presume) as a boot device first for that to work, though.

Problem fixed! I love you guys.

---

### Post by jamesrfla on 2008-09-28
You are very welcome. :D If you ever have any problems with Ubuntu or Linux just come hear and we will be able to help you. :guitar:

---

