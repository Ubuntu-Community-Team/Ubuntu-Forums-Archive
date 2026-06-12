---
title: "installed XBMCbuntu, CentOS won't boot"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by KY Metro on 2012-07-04
Hello, another Linux noobie here. A friend lent me a spare laptop running CentOS, he said dont worry about screwing it up, he would wipe and reinstall when I'm done. So I jumped in at the deep end trying to dual-boot to Ubuntu, and now I'm stuck... but rather than reinstall everything from scratch I really want to learn how it works. I'm trying to learn Linux so that I *can *fix it when it really matters...

The laptop is running CentOS 6 on a HP Pavilion dv6. Here's what I wanted to do, installl XMBCbuntu to an external HDD and store some media on it. Hopefully when I want to run on a different machine I can just plug in the drive and go - sort of like a LiveCD but fully installed and with storage.

I got the CD and it works fine. Installer didn't recognize CentOS, said no operating system - offered to wipe the main drive - no thanks! I manually set up some partitions on the ext drive - 500MB primary for boot, then an extended partition with 4GB swap, 4GB root, and the rest as home, for file storage. All ext3. Installer had no issues. 

Boot new system and says ```
Error loading operating system
``` Checked the BIOS, it's trying to boot off the external HDD like it should, not working though. Back to safety - CentOS please. Unplugged the drive and set to boot from internal drive, like it used to - expecting CentOS to pop up. Get message: ```
error: no such device: 039bf99a-fc2a-4d64-8d8e-175212a7b962
grub rescue>_
```

Plug the drive back in, try once more to boot from internal disk. Now it boots into XBMCbuntu! :o


So my questions:

1. Is this idea going to work? Can you install Ubuntu to an external drive and expect it to boot on multiple machines? If not then can I swap machines infrequently with some amount of work?

2. What did I do wrong with the partitioning and the install?

3. Also need to fix CentOS boot... hopefully without reinstalling.

4. What info do you need from me?

Thanks in advance!

---

### Post by cipherboy_loc on 2012-07-04
I can't tell you the specifics of what you need to do, but from what it sounds like, you put the XMBCbuntu boot loader on the CentOS hard drive. To fix it (general over view, nothing specific) you need to re-install grub2 on the XMBCbuntu disk and the CentOS boot loader (not sure what version of grub, or if lilo, etc) on the CentOS disk. I would do this by booting the LiveCD and chrooting into each installation and installing grub to the root of each device. When you install to flash medium, make sure you look under advanced options (just before you install) and change the drive to install grub to. 


Cipherboy

---

### Post by KY Metro on 2012-08-11
OK, it's been on the shelf for awhile, but I'm back at it. 

It looks like the easiest fix is to run "rescue mode" off of the installation disk. I got a live CD of CentOS 6 and pulled up the boot prompt. Did this by hitting ESC while it says "10 seconds to auto-boot" and then I have several GUI boot options. I hit ESC again and landed at a boot terminal. Great! Typed in "linux rescue", got this:

boot: linux rescue

could not find kernel image: linux

Now I'm confused, because it says quite clearly in the documentation (links below) that you find the boot prompt and simply type "linux rescue", that's it. Maybe there's a different boot prompt somewhere?

What am I doing wrong??

[http://www.centos.org/docs/4/html/rhel-sag-en-4/s1-rescuemode-boot.html](http://www.centos.org/docs/4/html/rhel-sag-en-4/s1-rescuemode-boot.html)

[http://www.centos.org/docs/2/rhl-cg-en-7.2/rescuemode.html](http://www.centos.org/docs/2/rhl-cg-en-7.2/rescuemode.html)

[http://www.centos.org/docs/5/html/Installation_Guide-en-US/s1-rescuemode-boot.html#s2-rescuemode-boot-reinstall-bootloader](http://www.centos.org/docs/5/html/Installation_Guide-en-US/s1-rescuemode-boot.html#s2-rescuemode-boot-reinstall-bootloader)

---

### Post by KY Metro on 2012-08-12
Anyone?

---

### Post by mansonfan78 on 2012-08-13
You should consider using Rescatux ([http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)) to repair the bootloader on your internal hard drive first (without the external one connected).  Then try it on your external hard drive.  In order to boot to the external your computer would have to be set up in bios to boot to usb before internal hdd.  You should be able to use your external hard drive to run Ubuntu on any computer that is set up properly in it's bios.

---

### Post by mastablasta on 2012-08-13
i am not sure how it's done in centos (it might be using LILO) but cipherboy_loc is correct in the procedure required to fix this.
 
edit: if centos uses grub you can try using boot repair tool. unplug ubuntu disk, run a live ubuntu cd and use the tool to repair grub. then install another grub to the external disk.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

