---
title: "Dual boot problem"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by falro on 2012-07-27
Hello.  I am completely new to Linux of any kind.  I just installed Ubuntu with windows 7, and now I can't use my laptop.  It shows the normal. Dell logo, then quickly goes to a drmk v8.00 page.  I have absolutely no idea what to do.  I have no way of reinstalling the OS, and I have lots of stuff I can't lose.  Extra info: I was able to boot Ubuntu the first time.

---

### Post by f1tz on 2012-07-27
I assume that you have windows 7 and ubuntu on the same disk? Usually the problem  is that part of the windows boot loader is overwritten and it fails to boot. DRMK (Dell Real Mode Kernel) is what Dell uses when booting to the Restore or Utility partitions. So, I guess that is what it is trying to load. This might be solved by restoring the windows boot loader. A quick google turned up this: [http://www.linuxbsdos.com/2012/03/10/restore-the-windows-bootloader-to-mbr-after-dual-booting-with-linux/](http://www.linuxbsdos.com/2012/03/10/restore-the-windows-bootloader-to-mbr-after-dual-booting-with-linux/) (which looks promising if you do not have discs to reinstall stuff, but I dont have experience of using it myself). If you do have a windows 7 installation disk, or can boot from a recovery partition, I would use that instead.

But, probably the most important thing is to back up your important data **before doing anything else**! Did you install ubuntu from a live cd? If so, you can boot up off of that and back up stuff to an external hard drive/ CD/ DVD/ other media. If not, you may be able to burn a livecd, or boot ubuntu (or another linux distro) from a USB stick.

Also, another thing that might help us... when your system is booting, do you see any mention of "GRUB"?

---

### Post by ikt on 2012-07-27
> **falro said:**
> Hello.  I am completely new to Linux of any kind.  I just installed Ubuntu with windows 7, and now I can't use my laptop.  It shows the normal. Dell logo, then quickly goes to a drmk v8.00 page.  I have absolutely no idea what to do.  I have no way of reinstalling the OS, and I have lots of stuff I can't lose.  Extra info: I was able to boot Ubuntu the first time.

Don't freak out, worst case scenario you can just run the ubuntu live cd which will give you access to all your files again.


> **f1tz said:**
> But, probably the most important thing is to back up your important data **before doing anything else**! Did you install ubuntu from a live cd? If so, you can boot up off of that and back up stuff to an external hard drive/ CD/ DVD/ other media. If not, you may be able to burn a livecd, or boot ubuntu (or another linux distro) from a USB stick.

^ Strongly agree with the above.

---

### Post by falro on 2012-07-27
Thank you!  I am in a car right now, but I'll try that when I can.

---

### Post by TheStrategist on 2012-07-27
> **falro said:**
> Hello.  I am completely new to Linux of any kind.  I just installed Ubuntu with windows 7, and now I can't use my laptop.  It shows the normal. Dell logo, then quickly goes to a drmk v8.00 page.  I have absolutely no idea what to do.  I have no way of reinstalling the OS, and I have lots of stuff I can't lose.  Extra info: I was able to boot Ubuntu the first time.
Yeah, your top priority in this case should be getting access to your files in order to make a backup for just in case.  

If you've installed the latest Ubuntu 12.04 from disc, you can use that as a live cd in order to backup your files. 

By default, Linux can recognize your Windows partitions, so you should be able to make a backup.  I'd recommend doing this before anything else, especially if you have very crucial files stored on the hard drive.

---

### Post by falro on 2012-07-29
Thanks, everyone!  I was able to load Ubuntu from a USB, and I will back up my files ASAP!

---

### Post by wildmanne39 on 2012-07-29
Please use descriptive titles - this is a support forum so unsurpringly everyone starting a thread wants help. 
[http://ubuntuforums.org/showpost.php...11&postcount=1](http://ubuntuforums.org/showpost.php...11&postcount=1)

---

