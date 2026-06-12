---
title: "Can Not Install On a LSI MegaRAID controller!"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by ML570 on 2008-05-08
Hello friends!

I need some help with my ML570 that runs 6 15k drives on a LSI MegaRAID SCSI 320-2 Dual-channel [
[http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_scsi/megaraid_scsi_3202/index.html](http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_scsi/megaraid_scsi_3202/index.html) ] with the latest BIOS.

I had FreeBSD installed (no problem), but need to use VMware for work so I chose to switch to Ubuntu.

I am a *NIX newbie.

1. Server boots with Ubuntu 8.0.4 Desktop
2. I select language
3. Server goes through the loading animations
4. Server spits out error
5. No more progress is made



Here is the error I get when I try to install Ubuntu:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [  133.830297] sd 2:2:0:0: [sda] Asking for cache data failed
[  133.830387] sd 2:2:0:0: [sda] Assuming drive cache: write through
[  133.830734] sd 2:2:0:0: [sda] Asking for cache data failed
[  133.830826] sd 2:2:0:0: [sda] Assuming drive cache: write through
```



I did some research and it seems that Ubuntu for some reason has problems with LSI Megaraid controllers (I think):

[http://ubuntuforums.org/archive/index.php/t-208510.html](http://ubuntuforums.org/archive/index.php/t-208510.html)


[SIZE="2"]> ssjoholm
September 2nd, 2006, 07:48 AM
Hi,

I don't have that RAID controller, but I found following info;

Intel SRCS16 and SRCS28X Serial ATA RAID Controller PCI cards — real hardware RAID. These are six-port PCI and eight-port PCI-X cards (respectively) for servers, based on an LSI Logic MegaRAID chipset, driving SATA-I output using Silicon Image SiI3112A SATA-I chips (one for each channel pair) and an Intel GC80302 or IOP331 (respectively) dedicated I/O processor with 64MB or 128 MB of ECC SDRAM (respectively) for processing XOR logic. Use the kernel's "megaraid2" driver (For LSI Logic MegaRAID). The Silicon Image chips are not the system-facing chipsets (1 2), and so don't determine driver support. An optional battery-backup daughterboard is available.

source:[http://linuxmafia.com/faq/Hardware/sata](http://linuxmafia.com/faq/Hardware/sata)

It's seem that "megaraid2" has to be inserted to the kernel, maybe this should be checked if it's loaded correctly.[/SIZE]



These threads could be of value to a more experienced user:

[http://ubuntuforums.org/showthread.php?t=661598](http://ubuntuforums.org/showthread.php?t=661598)
[http://ubuntuforums.org/showthread.php?t=201858](http://ubuntuforums.org/showthread.php?t=201858)

It seems that both of the links that I posted, even though related (MegaRAID issue) do not describe hardware I run.

The former link is about SAS card and the later about seemingly antiquated SCSI card.



What is the deal with Linux an MegaRAID cards?

How to fix this?



Thank you in advance!

---

### Post by dstew on 2008-05-08
Have you installed the [dmraid package]("http://packages.ubuntu.com/hardy/dmraid")? It should have support for LSI MegaRAID controllers. You can install Ubuntu using dmraid to access the RAID. See the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto"). There is also a kernel module with the name megasas that might be useful, but I don't know much about this.

---

### Post by ML570 on 2008-05-08
dstew, thank you very much for your response!

Unfortunately it looks like I have to be able to boot in to Linux environment to be able to install these device drivers.

I am unable to install or boot into linux.

I only have access to the 6 RAIDed drives, a CDROM drive and a floppy drive as the means on storage.


AFIK, as long as Linux does not see my raided hardware it can not install. I was able to run Puppy Linux from RAM, I do not know if this is useful...

---

### Post by quelx on 2008-05-08
Those shell errors are not critical, it's just probing the cache on the drive and not finding any, that's okay

Have you tried booting a vanilla live CD?  Have you tried a different distribution (I'd start with CentOS since you have a server on your hands)?

That's a true raid card, unlike some cheaper models so linux should have no trouble with it (I use a 4-port SATA LSI card on my office Ubuntu box)

The packages mentioned won't help because they are for creating/managing software raid devices, your card should be handling all of that if it's configured properly, Ubuntu should not even be aware that there are 6 drives attached (unless you use the LSI management software).

---

### Post by ML570 on 2008-05-08
quelx, thank you for response!

I did consider CentOS.

The reason I have chosen Ubuntu was because I need to create the following setup:

[http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1238129,00.html#](http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1238129,00.html#)

Unfortunately, due to my newbie *NIX status, I need step by step instructions to achieve results. I also need a Linux distribution that will accommodate my newbiness while I am learning.


I am unsure what you mean by a vanila live CD. If you mean any live Linux distro, then yes, Puppy Linux ran fine from memory. If you mean live Ubuntu, then no, I was also left with the following error when I attempted to do a live CD boot.


My card is currently configured correctly and hard drives have FreeBSD 7 set up on them.



Please point me to a next step in resolving this issue.

---

### Post by quelx on 2008-05-08
No to try and steer you away from Ubuntu, but if it's not working it's not working, sometimes it is easier to find a different solution than working out the kinks in another.

You can find an rpm package here for RHEL (i.e. CEntOS)
[http://register.vmware.com/content/download-a.html](http://register.vmware.com/content/download-a.html)

I would at least download the centos iso and try to boot it, if that works try to install it, if that works try to install vmware on it.

[http://communities.vmware.com/message/886403#886403](http://communities.vmware.com/message/886403#886403)

---

### Post by ML570 on 2008-05-08
I am very disappointed with this kink in Ubuntu.

I do believe that you are correct on moving on to CentOS.

I can only hope that CentOS will provide a *NIX newbie a friendly desktop environment.

---

### Post by dstew on 2008-05-08
> AFIK, as long as Linux does not see my raided hardware it can not installMy point was you *can* install to a RAID if you install the dmraid program onto the Live CD system using the synaptic package manager. Look at that HowTo. You can install dmraid, then install Ubuntu and the grub bootloader. You have to install Ubuntu "by hand", instead of automatically, but it can be done. I think the HowTo has not been updated for Hardy though.

---

