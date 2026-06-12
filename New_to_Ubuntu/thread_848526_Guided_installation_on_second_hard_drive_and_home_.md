---
title: "Guided installation on second hard drive and home partition"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by silps on 2008-07-03
Hi,

I want to install Ubuntu on a WinXP system onto the second hard drive to create a dual boot. I will use the guided option. Will this create a home partition and what are the advantages of using a home partition?

If I can help it I don't really want to manually partition the drive.

If ever I want to remove Ubuntu from the system how would I do this and what would I have to do regarding the Ubuntu boot manager as well?

Thanks for any help.

---

### Post by kansasnoob on 2008-07-03
> "I will use the guided option. Will this create a home partition and what are the advantages of using a home partition?"

No! You can read about creating a home partition after installation here:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You'll notice in the first paragraph there's a link for creating a home partition before installing.

> "If ever I want to remove Ubuntu from the system how would I do this and what would I have to do regarding the Ubuntu boot manager as well?"

You would have to restore the Windows mbr (master boot record). Not horribly difficult, and I won't bother getting into it now.

I suggest reading the following tutorial (also browse all of the links in the aforementioned tutorial) and look at a lot of the different install methods just to get some ideas about how both the Live CD installation goes and also the Alternate CD method.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Honestly as one nOOb to another, if you're comfortable unplugging and replugging hard drives (if not forget it) I'd disconnect the XP drive and fiddle only with other hard drive until I get some idea how partitioning works, how GRUB works, etc.

I'll bet almost everyone here can tell you that they hosed things at some point during their first few weeks of experimenting with Ubuntu. I can tell you that it's generally worth it unless you find that you have hardware that's just not compatible with Ubuntu.

The thing about using different hard drives for Ubuntu and Windows is great, but you'll still have to mess with GRUB at some point, and you'll need to understand how GRUB's numbering system works:

[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

---

### Post by ajgreeny on 2008-07-03
If the second drive is to be just ubuntu, don't be afraid of manual partitioning; it's really not difficult.

Guided partitioning doesn't make a separate /home partition, as far as I can remember, but I have not used that way for about 3 years when I first installed ubuntu.

I suggest yo use the live ubuntu CD and run partition editor (gparted) from the System>>Administration menu.  Delete all the partitions on your second disk sdb or hdb, if there are any, with that and then make 3 new partitions. 

The first should be about 8GB, formatted as ext3.
The second should be all the rest of the disk, except for about 512MB - 1GB left free at the end, and again formatted as ext3
The third should be the 512MB - 1GB and formatted as linux-swap.

Now shutdown gparted and install the system.  Use manual partitioning and make sure you chose sdb or hdb, not sda or hda, your windows install disk.  The table that appears will show all the new partitions in the second disk and you can click on them one by one, click on **Edit partition** and set the mount points as / for the first, /home for the second and use as swap for the third, so it does not have a mount point.

Although it sounds complicated it really isn't, and it will give you a lot of information and practice about partitioning so you will soon be able to do this without fear.  Just make sure you do not do anything to sda or hda, and you shouldn't do anything that upsets your windows install.

Sorry if this is long winded, but I am trying to guide you into the best way to get what you want.

---

### Post by Lifeis on 2008-07-03
Iv been using Ubuntu on one of my laptops for a few weeks now, and fedora on a desktop for about a year before hand. And today I got a new computer (well an older computer actually) for nothing at work, and I stuck in a hard disk from another computer, and memory etc, and on both hard disks it had Windows XP Pro, but I just formatted the slave disk (in windows) command: format :<drive>, and then ran the Ubuntu installer and selected the drive. Cant remember what option I used, but it's been working fine since I installed it. And iv installed alot of files, on both XP and Ubuntu and both have worked fine. Ubuntu sees the PC as a Linux install only and XP sees it as a windows install only if you get me.
Hope that helped.
And if not someone write back and tell me what iv let myself in for!
=)

---

### Post by kansasnoob on 2008-07-03
If you really just want to jump right in this should be helpful:

[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

but you really need to know how to identify hard drives in Gparted which is an integral part of the Ubuntu installation!

Just don't be afraid to keep asking questions until you're comfortable about installing.

---

### Post by Lifeis on 2008-07-03
> **kansasnoob said:**
> 
Just don't be afraid to keep asking questions until you're comfortable about installing.

Yep. Ask questions for sure. The community here is awesome.
Im still trying to find my way around Ubuntu also. And Linux in general.

---

### Post by silps on 2008-07-03
Wow, thanks for all your replies.

I am eager to get started with Ubuntu so I think for now I will use the Wubi install method so I can play around with Linux on an old WinXP PC. Then once I am more comfortable I will probably install on my Vista machine as a duel boot.

---

### Post by k3lt01 on 2008-07-03
> **ajgreeny said:**
> The first should be about 8GB, formatted as ext3.
The second should be all the rest of the disk, except for about 512MB - 1GB left free at the end, and again formatted as ext3
The third should be the 512MB - 1GB and formatted as linux-swap.You don't even know the machines specs and your making suggestions like this.

Silps do yourself a favour and make the swap partition as big as you can, I do 2gb for everything as it helps to take up the slack that the RAM doesn't handle.

What are your machines specs? how big is the second hard drive? no-one can give you anything but a guesstimate if you don't give more info.

---

### Post by redchief on 2008-07-03
i have 2 drives, both set as cable select for master / slave.
I have Installed 8.4  on the C or master drive with the second drive unplugged.  2nd drive D has xp pro. and bootable in the master position
I'd like to dual boot.
Is there an easier way that a fresh install on 8.4.1 desktop?
No problem reinstalling  since it's a fresh install with no files of consequence.

thanks

D

---

### Post by kansasnoob on 2008-07-03
Silps,

I'm sure you can see by now that if you ask ten Ubuntu users how to install Ubuntu you're likely to get more than ten answers!

But, it would be helpful to know everything about your hardware!

---

### Post by kansasnoob on 2008-07-03
> **redchief said:**
> i have 2 drives, both set as cable select for master / slave.
I have Installed 8.4  on the C or master drive with the second drive unplugged.  2nd drive D has xp pro. and bootable in the master position
I'd like to dual boot.
Is there an easier way that a fresh install on 8.4.1 desktop?
No problem reinstalling  since it's a fresh install with no files of consequence.

thanks

D

I never use cable select, but I never install two drives on one cable.

Now, with almost all mobo's coming out with only one IDE port I might have to.

It's getting interesting to deal with huge TB drives and mobos that have only two SATA ports. I don't like it!

---

### Post by redchief on 2008-07-03
no problem,
Antec designer case (I heard white cases run faster), Abit NF7 Ver 2 MB with XP mobile OC's to 2.6 Ghz SLI 120 HSU with 120mm nexus fan + two 120 mm fans front & back set up for push pull airflow. CPU temp 108 degrees F, two x512 OCZ memory with heat spreaders, two 300 GB IDE drives, Dual layer DVD burner, Antec 850W PSU  IBM keyboard & logitech trackman marble FX moose.
what else would be helpful?:)

---

### Post by ZabiGG on 2008-07-03
Silps, you're wise and I hope you enjoy the experience.  ;)

Just keep in mind that the performance might not be that great using wubi.

If you'd like to get more info about Ubuntu, there are many posts and links with great information.

I'd suggest you invest a few hours in reading, to really get better insight on what Ubuntu (and linux) is all about.

New to Ubuntu? Start here is a great sticky for starters

You can also click on "Look here" in my signature below for other great sources of basic info.

I hope you'll have fun with your new discoveries, and welcome to Ubuntu.

Z.

---

### Post by silps on 2008-07-04
Thanks ZabiGG and everyone else. I spent the whole day yesterday reading up (I like the psychocats site) hence I wanted to clarify the instalalation procedure.

First I am going to go the Wubi route with a old PC that is an Intel Pentium 3 700mhz, 640MB Ram and two 20GB hard drives with WinXP on the first (nearly full) hard drive.

Then I will probably experiment with duel booting on the same PC.

The goal is to install duel boot on to my Dell PC which is a Core 2 Duo 4600, Vista, 2GB Ram, 250GB primary Sata and 500GB secondary sata hard drives.

The Dell has a restore partition, will the install of Ubuntu and its boot loader effect the operation of the restore partition if ever needed?

I really like the feel of Ubuntu compared to Windows, I was quite disappointed by Vista especially compared to Mac OS X which is great, so it would be nice to see how Ubuntu rocks on my PCs.

---

### Post by silps on 2008-07-04
Okay I did the Wubi install and it works fine.

I do find it a lot slower than the WinXP on the computer. Would I be correct in assuming that if I do the proper partitioned install then Ubuntu should run as fast if not faster than WinXP?

Cheers.

---

### Post by ZabiGG on 2008-07-04
The computer is old, but your assessment is correct, in my opinion. Hermanzone's illustrated dual-boot install (**Dual install 101** in my newbie 101) is user-friendly and will avoid mistakes if you follow it carefully. Always read ahead completely before you follow a how-to so you'll be prepared for anything.

I personally dual booted for a while before I leaped. It did not alter Windows recovery at all: grub (the boot) will include a Windows start up option. Ubuntu performance was flawless.

If you do decide to dual boot, I'd suggest you follow the Psychocats guide to installing /home on a separate partition before you install (creating partitions is relatively easy and well explained on that site), the reason why I'm advising you to do so is simple: /home on a separate partition saves our documents and time when we need to reinstall or install another version of Ubuntu, but that's a matter of personal preference...

Since I enjoy tinkering and experimenting, /home on a different partition is a life saver when my system gets broken and I need to make a clean install, which only takes about an hour on Ubuntu -- as opposed to being a matter of days on Windows.

Hope this helps,

Z.

---

### Post by redchief on 2008-07-04
...and a pleasant reinstall  was had by all. that was the practice unit.
now on to the main box.
quad 6600,  gigabyte board, two gb ddr, two 750 gb seagate sata, 9600 video card, WinTV HD tuner, wireless kb, moose, +outboard two crown d75 amps for surround. + amped sub & center & hd projector for ~10ft " screen".

---

### Post by Lifeis on 2008-07-04
Yeah your right man. Ubuntu runs alot faster when its fully installed and not running along side all the over sized windows OS.
I used a live CD I got years ago of Ubuntu of a friend, I cant remember what version it was, and it worked perfectly. Iv not used it for quite some time as my main OS though, so im kind of new to all this too.
The machine im typing this from has two 40gb Hard Disks, one Windoze XP, the other Ubuntu Hardy Heron.
And it works a treat, an the machine isnt high spec.
The best machine I own runs Ubuntu as its only OS and it is much faster than any other computer I have ever used.
When I first used it I was amazed at the speed. Even the first time I looked at a website in Firefox. Everything about it is miles better.
Id say yeah, go for it and you'll love it.
It will out perform your Windows install for sure. And most predominantly on your best spec machine.
Good luck man, and the community is always here to help.

---

### Post by Lifeis on 2008-07-04
One thing I would say though is, prepare to face some hardware problems at some point. Whether it be wirless, ethernet (although networking is excellent in Ubuntu), sounds, graphics, whatever. All your hardware manufacturers make Windows drivers, and it can be tricky at times getting things to run properly.
My wireless card on my best machine still doesnt work. So im gonna buy a new one that I know is supported "out the box" by Ubuntu.

---

