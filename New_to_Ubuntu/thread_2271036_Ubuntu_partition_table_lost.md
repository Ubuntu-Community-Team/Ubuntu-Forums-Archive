---
title: "Ubuntu partition table lost"
date: 2015-03-27
forum: New to Ubuntu
---

### Post by nacra60 on 2015-03-27
Hi,

I have a dual boot pc with win7 and ubuntu 14.04. Windows gave 'some' problems so I have re-installed windows (Yeah, I know, but I need it for my work). The problem now is that the the boot menu is gone. I have tried boot-repair, but that didn;t help. Trying to fix this problem, I started Ubunut with a USB stick and checked the harddisk with GParted. There I noticed that the Ubuntu partition was gone (unallocated). Searching with Google I found TestDisk. I followed te instructions, but have the feeling that if I do something wrong, all data will be lost. So before I do anything, I would like to make 'sure' that I am doing the right thing. In Boot-Repair, there is a "Create a Bootinfo summery" option. This is the result: [http://paste.ubuntu.com/10687865/](http://paste.ubuntu.com/10687865/)

So I think getting back the partition has to be done first, then the boot menu.

I am still a newbe, most of what I have done so far is not based on knowledge, but what I found on forums.

Any help is very much appreciated.

Regards,
Ufo

---

### Post by nacra60 on 2015-03-27
This is where I get stuck. I don't know what to do next. I have read all the examples, but I do not understand then.

[ATTACH=CONFIG]260920[/ATTACH]

[ATTACH=CONFIG]260921[/ATTACH]

---

### Post by westie457 on 2015-03-27
Welcome to UF nacra60

Looking at your testdisk pic, this is your current partitions listed after a 'quick search'.
Next if you hit 'Enter to continue' you will have the option for a 'Deeper Search'. This will read every sector of the hard drive looking for partition information and will take a long time, for example a 160GB drive takes about 40 minutes. do not interrupt the deeper search otherwise you have to repeat the whole process.
The 'deeper search' will hopefully find every partition ever created on the drive. Some will be recoverable, some will not. Testdisk will let you know.

The steps after the deeper search can be quite involved and may cause information overload this early in the process.
Will check back later when you hopefully post a pic of the complete partitions list.

---

### Post by nacra60 on 2015-03-27
Thanx for your reply. It's still in progress, but this is the result so far:

[ATTACH=CONFIG]260922[/ATTACH]

---

### Post by nacra60 on 2015-03-27
Ok, this is the result:

[ATTACH=CONFIG]260925[/ATTACH]

---

### Post by oldfred on 2015-03-27
If you repartitioned multiple times, testdisk will find all the old versions.

I think in your first screen you showed three partitions.
And you show this:
```
/dev/sda1    *             63   783,185,917   783,185,855   7 NTFS / exFAT / HPFS
/dev/sda2         783,185,918 1,953,523,711 1,170,337,794   5 Extended
/dev/sda5       1,937,713,152 1,953,523,711    15,810,560  82 Linux swap / Solaris

```

Testdisk will not show the extended partition but will put all logical partitions in the extended. All logical partitions must be adjacent as you only can have one extended partition.

Windows always seems to rewrite extended partition without the Linux partition. Your partition list shows a large gap (unallocated in gparted) that was your Linux partition. It probably was sda5 and swap was sda6 but order is not important, system now works off UUIDs.

You should just restore from first screen. The NTFS partition must be primary bootable (*) and the Linux & swap logical (L).

Many that correct partitions with testdisk if they have made no other changes have been able to reboot from grub still in MBR as it then finds restored partition correctly.

---

### Post by nacra60 on 2015-03-27
Thanx for your advise. I have tried it, but it came with "Bad Structure". If I continue, it states: Invalid partition structure.


[ATTACH=CONFIG]260928[/ATTACH]

P.s. If I select the middle one en press "p" (list files) I see all the Ubuntu files, including my data. So nothing is lost (so far)

---

### Post by oldfred on 2015-03-27
Not sure why it is saying structure bad. Does not look like overlapping and both logical are next to each other. 
You can try with Linux partition as primary as you can have another primary, but it looked like Linux was a logical. But perhaps the rewrite by Windows changed it?
 Or try without swap. 
System will boot, but will give error with swap missing. You then can recreate it and edit fstab with new swap's UUID.

---

### Post by nacra60 on 2015-03-30
Ok, I couldn't fix it, so I have brought it to a specialist. It took him 6 hours to fix the boot, but it's working fine now.

Everybody thanx for the help !!

---

### Post by moonsky219 on 2015-08-04
Hello all, it seems I am suffering a similar situation here.

I have created a new thread here:
[http://ubuntuforums.org/showthread.php?t=2289509](http://ubuntuforums.org/showthread.php?t=2289509)

Please guide me through...... 

Thank you guys!

---

