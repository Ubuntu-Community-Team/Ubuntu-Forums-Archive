---
title: "Dual boot Win7 and ubuntu 14 - issue when booting to Win"
date: 2015-12-04
forum: New to Ubuntu
---

### Post by ericj2 on 2015-12-04
Hi:

New to Linux (sort of) but well versed in MSDOS and pretty competent with Windows.

Just set up a dual boot with Win7 and Ubuntu 14 and for the most part working well. But now when I select the option to boot to Win from the boot menu I keep getting a message that there might be an issue with one of my disk drives and Windows wants to check. I have (so far) pressed a key to bypass this and then Windows seems to run fine but if I miss the time frame to skip this I am afraid something might get messed up.

How can I stop this or should I let it go ahead and do the check?

Thanks a lot,
Eric

---

### Post by oldfred on 2015-12-04
Ubuntu normally runs it fsck on its ext4 partitions every 40 or 60 boots. But cannot run chkdsk.

Windows may want to run chkdsk if it starts to see issues. So you should let it finish running chkdsk on its reboot. And it can take a long time.
May also indicate it is time to do other Windows housecleaning.

---

### Post by ericj2 on 2015-12-04
Thanks for the reply...

I find it hard to believe that there are any issues on the Windows part of the drive, I had recently run chkdsk (took hours), and I also recently removed a lot of junk files, etc. before installing Ubuntu. My fear is that Windows will mess something up if I let it run this... if I keep getting the message I guess I'll have to.

---

### Post by Vladlenin5000 on 2015-12-04
> **oldfred said:**
> May also indicate it is time to do other Windows housecleaning.

+1
-and-
It is time to start checking that drive for physical errors instead of just logical ones.

---

### Post by ericj2 on 2015-12-04
Thanks

Just seems a bit odd that I had no issues beforehand... before installing Ubuntu. And other than that message everything seems great. I'll post back with what I come up with since it may help someone else.

---

### Post by oldfred on 2015-12-04
Windows always has to run chkdsk after any NTFS partition resize. 
That is also to update the PBR or NTFS partition boot sector which must have the same sector start & size as partition table.

---

### Post by ericj2 on 2015-12-04
OK thanks, did not know that... as much as I have used and tweaked (and even written software for) various Windows versions I never had to mess with boot issues, partitioning and the like. I'm going to reboot into Windows and let it do what it keeps asking.

I also have another computer I have running Win 8.1 and installed Ubuntu along side Windows on there. On that one if I leave from a Windows session I get no bootloader menu at all. If I close out an Ubuntu session when I reboot I get the Ubuntu selection boot menu. Have tried changing boot priority but it still happens.

---

### Post by oldfred on 2015-12-04
Post another thread with brand/model and Win8 dual boot as the should be UEFI issues.
(if you want to read ahead, just about all my answers are in link in my signature below, but it tries to cover just about everything so can be a bit much.)

---

### Post by ericj2 on 2015-12-04
Allowing Windows to do the chkdsk at boot seemed to work. I have logged out, into ubuntu, shut that down and back to Windows and did not get that error message. Thanks a lot, already this is better support than I ever got from MS

Computer running Win 8.1 is a HP P6-2378pc with 8 GB Ram

I'd never own a computer with any Win past 7 on it but inherited it.... I hope to like Ubuntu enough to eventually remove Windows off that one. That is the one that I mentioned in above post that boots back to Windows with no choices after exiting Windows.

I have a friend who is a computer sciences professor at a local university and he told me a while back when 8 came out he would NEVER "upgrade" to 8... I am doing most of what I am doing now because I did not like 8 but 10 is simply evil :)

---

### Post by oldfred on 2015-12-04
I have posted a lot of UEFI info on HP. They violate UEFI standard which specifically says they are not supposed to use description as part of boot and only valid description is "Windows". There are several work arounds, posted in many of my threads, link below in my signature. What may be best may depend on if dual boot, whether primary Windows or Ubuntu or some other factors(whatever actually works).

Some others HP threads.
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try different USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by ericj2 on 2015-12-04
Thanks for the info, I will check it out. the issue isn't real bad, just annoying cause if I have left Windows, next time I boot I have to go to the Windows boot menu if I want to run Ubuntu. 

I have learned the hard way in the past that sometimes an annoyance is better than trying to fix it if you don't exactly know what you are doing cause then you end up with worse issues... that is why I was concerned about allowing Windows to do the chkdsk at boot.

Thanks again for all the info, I owe you at least a beer .

---

