---
title: "Grub Error,  ubuntu partition is gone"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by surfboard3r on 2011-12-19
ok im freaking out right now because I have no idea how to fix this.  

I had windows 7 (64 bit) and ubuntu dual booted on my laptop, the other night i decided that i didnt want ubuntu anymore because i needed more space on my hard drive for windows.  So, i just formatted the ubuntu partition and added it back into the windows partition.  But, now when i try to boot the computer grub is still installed and says **error:no such partition **. Other instructions i have seen say to use a windows recovery disk, but i dont have one with me.  what can I do?

---

### Post by critin on 2011-12-19
> say to use a windows recovery disk, but i dont have one with me.  what can I do?

Go to the computer manufactor's web site and ask for a recovery disk.  They will charge you, but you need one.  Or borrow a similar disk from a friend or neighbor.  Also check microsoft's site for a disk download--ask on the microsoft forums if you need to.   I believe they have them available.

Someone will probably help you recover from this, but you should get yourself a copy for future problems.

---

### Post by hhh on 2011-12-19
@surfboard, you just need to reinstall the Windows Master Boot Record (MBR). The easiest way I know of to do that is to use another computer to download and burn SuperGrubDisk or RescaTux, boot the broken computer with the CD in it and follow the on-screen instructions...
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by *^kyfds( on 2011-12-19
i had a similar problem ( i also tried to format my linux partition).

it's basically a problem with the bootloader config.

see this for a temp fix until you can find a boot cd to fix your bootloader.

it's what i used.


[http://s13.zetaboards.com/TheEverythingForum/topic/6855062/1/](http://s13.zetaboards.com/TheEverythingForum/topic/6855062/1/)

---

### Post by BC59 on 2011-12-19
> **surfboard3r said:**
> ok im freaking out right now because I have no idea how to fix this.  

I had windows 7 (64 bit) and ubuntu dual booted on my laptop, the other night i decided that i didnt want ubuntu anymore because i needed more space on my hard drive for windows.  So, i just formatted the ubuntu partition and added it back into the windows partition.  But, now when i try to boot the computer grub is still installed and says **error:no such partition **. Other instructions i have seen say to use a windows recovery disk, but i dont have one with me.  what can I do?

You can download from [here]("http://http://www.mydigitallife.info/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/") the Windows 7 .iso. Burn it to a disc and run the boot repair.

---

### Post by Michael Dooley on 2011-12-19
> **BC59 said:**
> You can download from [here]("http://www.mydigitallife.info/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/") the Windows 7 .iso. Burn it to a disc and run the boot repair.

I corrected the provided URL in your quote above BC49. Try the following URL if my quote edit doesn't take:

[http://www.mydigitallife.info/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/](http://www.mydigitallife.info/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/)

---

### Post by BC59 on 2011-12-20
> **Michael Dooley said:**
> I corrected the provided URL in your quote above BC49. Try the following URL if my quote edit doesn't take:

[http://www.mydigitallife.info/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/](http://www.mydigitallife.info/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/)

Thanks, -failed copy paste.

---

### Post by rng on 2011-12-20
I am not sure if in this situation following commands may work (on grub prompt) and start windows: 

```

> root (hd0,1)
> chainloader +1
> boot
```

---

### Post by lindsay7 on 2011-12-20
download and burn this iso disk.

[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

here is some info on it,

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

