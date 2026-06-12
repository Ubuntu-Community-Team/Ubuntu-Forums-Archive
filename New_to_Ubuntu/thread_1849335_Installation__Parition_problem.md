---
title: "Installation / Parition problem"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by cressrt on 2011-09-24
I've been asked to install Ubuntu onto a friends PC which has Win7 already on, to create a dual boot. However during the install there is not an install option as there are not enough partitions available. I have looked at all posts on this but cannot see the way to create the it. Can someone tell me in easy steps how to do this as I do not want to mess up the PC as it's not mine.
I'm installing by a USB.
Thanks in advance

---

### Post by Karlchen on 2011-09-24
Hello, cressrt.

Before anybody will be able to give you a step by step instruction, more details on the current disk structure will be needed.
So, please, let us know
+ the total size of the disk
+ the existing partitions, their types and their sizes
+ the amount of unassigned disk space
You can get all these details e.g. by using diskpart or diskmgmt.msc.

Moreover, tell us which kind of dual-boot installation do you have in mind? - [A Wubi installation](http://www.ubuntu.com/download/ubuntu/windows-installer) or a normal Ubuntu installation where Ubuntu gets its own partition of the disk?

Kind regards,
Karl

---

### Post by cressrt on 2011-09-24
Hi,
I am running from the USB stick and used GParted to get the following, I want a normal Ubuntu installation.

Total size 320GB
/dev/sda 298.09GB
/dev/sdb 1.87GB
/dev/sdc 15.12GB

Partition        File        Label          Size       Used    Unused    Flags
Dev/SDA1    NFTS    System       199MB    67MB    132MB    Boot
Dev/SDA2    NFTS                      275GB    89GB    186GB
Dev/SDA3    NFTS    Recovery    23GB      19GB    4GB
Dev/SDA4    FAT32    HP Tools    103MB    11MB    92MB       lba
unallocated                                  1MB

Dev/SDB1    FAT16                      1.87GB    303MB    1.57GB

Dev/SDC1    FAT32  Transcend    15,12GB    5.08GB    10.04GB    boot,lba

Hopefully this is everything
Thanks

---

### Post by coffeecat on 2011-09-24
@cressrt, you are trying to install to a HP machine which has four primary partitions, the maximum allowed. You will have to delete either the recovery or HP_TOOLS partition before you can create logical partitions for Linux. My preference is the latter. But whichever partition you decide to delete, make sure your friend has created a set of recovery DVDs from the HP utility. Also a Windows 7 repair disc from Windows 7 would be more than a good idea.

So that I don't have to type out all the other details again, have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1847433](http://ubuntuforums.org/showthread.php?t=1847433)

And follow all the links in my post #2 there - + all the links in the links! :)

Good luck.

---

### Post by cressrt on 2011-09-24
Thanks for all the info, will go back in windows and get started.

---

