---
title: "Windows Vista and Ubuntu 8.04 Dual boot"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Flarinon on 2008-05-24
I was thinking of dual booting vista and ubuntu 8.04
I am going to make a recovery disc before doing this. I'm probably going to recover vista because i've tweaked too much in it. What program should I use to make partition for ubuntu and how much space on the partition would you recommend, I was thinking 15 gigs to 20 gigs. help appreciated.

I need vista for my zune and games. thats why i decide to do a dual boot.

---

### Post by Sarah L on 2008-05-24
Gparted is a good partition manager in Ubuntu.

You should manage your partition sizes based on whether you use Ubuntu or Vista more, and on how much hard disk space you have. 20 gigabytes sounds like a reasonable amount for basic use, and if you ever need more space, you can always edit your partition tables again.

---

### Post by shifty_powers on 2008-05-24
> **Sarah L said:**
> Gparted is a good partition manager in Ubuntu.

You should manage your partition sizes based on whether you use Ubuntu or Vista more, and on how much hard disk space you have. 20 gigabytes sounds like a reasonable amount for basic use, and if you ever need more space, you can always edit your partition tables again.

all true, but i'd sound a word of warning here. editing and resizing partitions always comes with a risk. there is always a chance that it won't work properly. usually small, but it's happened to me before ;)

always have a back up solution in place, and make sure you've secured any important personal data BEFORE you resize partitions.

plus you can get a gparted livecd which might be usefl. just google it ;)

---

### Post by tom56 on 2008-05-24
The LiveCD does partitioning for you. From what you say it sounds like you'll want to pick the option that resizes the Windows partition and uses the free space. As for the size that's entirely up to you. 20 gigs should be plenty, and you can always resize later. As always when partitioning it is recommended that you back up your data first.

---

### Post by meierfra. on 2008-05-25
> Gparted is a good partition manager in Ubuntu.

yes it is, but it doesn't handle Vista very well.
(Edit: gparted does not damage any data, but it  may prevent you from being able to boot into Vista. For more details and how to fix the booting problem: ) See this link:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") 

 Use Vista's build in Disk management to resize Vista. For all other partitioning use Gparted.

---

### Post by tom56 on 2008-05-26
> **meierfra. said:**
> yes it is, but it doesn't handle Vista very well.See this link:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") 

 Use Vista's build in Disk management to resize Vista. For all other partitioning use Gparted.

I've never heard that - what part of that page are you referring to? I can't find anything there that suggests that Gparted doesn't work on Vista partitions. I'm just curious because I've used Gparted several times to resize my Vista partition and not had a problem.

---

### Post by shifty_powers on 2008-05-26
> **meierfra. said:**
> yes it is, but it doesn't handle Vista very well.See this link:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") 

 Use Vista's build in Disk management to resize Vista. For all other partitioning use Gparted.

the problem that refers to is a problem with the vista mbr, when linux is not present.

if you have grub installed, that shouldn't be a prob...

---

### Post by cyphur335 on 2008-05-26
Another good idea if you're just starting out with Linux or playing around, is to use a separate partition for /home.  That way you can keep re-installing without having to backup your data all the time.

---

### Post by tom56 on 2008-05-26
> **shifty_powers said:**
> the problem that refers to is a problem with the vista mbr, when linux is not present.

if you have grub installed, that shouldn't be a prob...

I see :) I think that that is always a problem resizing a partition, not just Gparted. I expect that the Vista partitioner restores the bootloader after it resizes. But you're right, if you can use the Vista partitioner you might as well because then you don't need to muck around with the recovery CD.

---

### Post by Duck2006 on 2008-05-26
This may help.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by kansasnoob on 2008-05-26
I've used the following tutorial several times to dual boot 7.10 and 8.04 with Vista Home Basic and Home Premium with no problems:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

BUT ......... the very last time (just last Friday) it seemed that everything that could go wrong did go wrong and I finally had to wipe the whole drive and do a fresh install of both Vista and Hardy. Aside from the time involved it was no big deal because I'd backed up everything and had the Vista discs, but the most troubling thing is that I have no idea what went wrong.

That said, this doesn't really apply to you, I also recently had trouble performing a dual boot with XP SP3, but after going to "Add/Remove" in Windows and uninstalling SP3 I was able to complete the dual boot and then successfully update XP again. Weird? Maybe a glitch I somehow created by "slip-streaming" SP3 into my XP installation media?

It just seems odd that I've suddenly had trouble dual booting both XP and Vista recently when I've done so successfully many times before. And I love the freedom of a dual boot environment! That way I still have Windows to fall back on while I'm learning, tweeking, etc.

BTW, regarding games, my daughter has been playing with Cedega and seems pleased so far, but she's still just learning and my idea of games is Spades, Hearts, and Free Cell Solitaire :)

---

### Post by arcarsenal on 2008-05-26
Sorry to miller... but I just installed Ubuntu and dual-boot with XP. I have a 160 GB HD, and basically I just am realizing now that I should have partitioned differently. I alloted too much space to Ubuntu about 80 GB and left only somewhere between 5-10 GB of free space on XP. I want to give XP some more disc space, but I don't want to lose anything or have to start all over again. I know there's a small risk involved in partitioning again, but it's probably going to be necessary if I want to have this all set up to my liking. 

Any suggestions would be greatly appreciated.

---

### Post by Duck2006 on 2008-05-26
> **arcarsenal said:**
> Sorry to miller... but I just installed Ubuntu and dual-boot with XP. I have a 160 GB HD, and basically I just am realizing now that I should have partitioned differently. I alloted too much space to Ubuntu about 80 GB and left only somewhere between 5-10 GB of free space on XP. I want to give XP some more disc space, but I don't want to lose anything or have to start all over again. I know there's a small risk involved in partitioning again, but it's probably going to be necessary if I want to have this all set up to my liking. 

Any suggestions would be greatly appreciated.

Try partitioning the drive with the live cd of parted magic.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

Read

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted)

on using parted magic.

---

### Post by meierfra. on 2008-05-26
> I've never heard that - what part of that page are you referring to? 

Last sentence of the first paragraph:

> The problem is that if you resize your boot/system partition, you will be completely unable to boot without repairing windows.

And justing fixing the MBR and the Boot sector will not solve the problem. Lucky  the page tells you how to solve the problem.

Also there are plenty of cases where people on this forum ended up reinstalling Vista after resizing Vista with gparted.

 gparted is aware of the problem: [http://gparted.sourceforge.net/faq.php]("http://gparted.sourceforge.net/faq.php")  (Bottom of the page, item #9)

---

### Post by tom56 on 2008-05-27
> **meierfra. said:**
> Last sentence of the first paragraph:



And justing fixing the MBR and the Boot sector will not solve the problem. Lucky  the page tells you how to solve the problem.

Also there are plenty of cases where people on this forum ended up reinstalling Vista after resizing Vista with gparted.

 gparted is aware of the problem: [http://gparted.sourceforge.net/faq.php]("http://gparted.sourceforge.net/faq.php")  (Bottom of the page, item #9)

Yeah, and the problem is the broken bootloader like I said.
> File: \Windows\system32\winload.exe
Status: 0xc0000225
Info: The selected entry could not be loaded because the application is missing or corrupt.
My point is that saying that Gparted doesn't play nice with Vista partitions is misleading because it implies it will damage your data which isn't true.

---

### Post by meierfra. on 2008-05-27
> My point is that saying that Gparted doesn't play nice with Vista partitions is misleading because it implies it will damage your data which isn't true.

O.K. that's a valid point. I'll fix up my original post.

---

