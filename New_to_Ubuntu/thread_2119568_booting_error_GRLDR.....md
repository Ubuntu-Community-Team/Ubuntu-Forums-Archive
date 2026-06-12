---
title: "booting error GRLDR...."
date: 2013-02-24
forum: New to Ubuntu
---

### Post by hemandr on 2013-02-24
I installed ubuntu on Windows vista a few weeks ago. It has been working without any problem during all this time but today trying to reboot my laptop, I had the error cannot find GRLDR in all devices. Press Ctrl + Alt + Del to restart

---

### Post by oldfred on 2013-02-24
Is this a wubi install or are you using EasyBCD?

I think grldr is from grub4dos which is a version of grub for use with Windows.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Mark Phelps on 2013-02-24
One problem with using Wubi is that you rely on Windows to get you into a situation where you can boot Ubuntu, and if the NTFS partition gets corrupted, you run into the very problem you're experiencing.

So, you could try booting into Windows and running CHKDSK, but in some cases, that has prevented running Ubuntu to the degree that it had to be uninstalled and reinstalled.

---

### Post by bcbc on 2013-02-24
See this: [http://ubuntu-with-wubi.blogspot.ca/2011/01/wubildr-wubildrmbr-and-grldr.html](http://ubuntu-with-wubi.blogspot.ca/2011/01/wubildr-wubildrmbr-and-grldr.html)

It means that your /wubildr file cannot be found. If you have more than one partition, copy it to them. e.g. D:\wubildr etc. Sometimes (for whatever reason) the one on C:\ might not be picked up (or if it's deleted, copy it back there).

---

