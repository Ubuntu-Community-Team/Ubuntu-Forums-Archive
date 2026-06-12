---
title: "Win 7 install errors"
date: 2009-11-25
forum: Recurring Discussions
---

### Post by bruno9779 on 2009-11-25
I had the most awful experience with the last piece of malware from M$.

I have tried to install Win7 on my desktop a few days ago and the experience was most infuriating.

I have multiple partitions on my HDD:
sda1 : 9.10 (/)
sda2 : 9.10 (/home)
sda3 : empty for other OS testing
sda4 : Haiku
sda5 : empty prepared for Win7
sda6 : Linux swap

The installer was painstakingly slow, after about 35 minutes i got to the partitioner, where i have just asked win7 to go to the partition I reserved for it.

The "thing" went off working for some other 20 minutes, the returned an error (800x... kind of error, no verbose) and said said it could not continue.

A chill run down my spine.
I rebooted, and the machine started on normally, grub2 booted almost to the login screen, where i got an error for 2 disks missing.

I then popped in karmic live CD to see what happened.

Malware7 had destroyed sda2 sda5 and sda6. 
And I mean destroyed, not even TestDisk was able to recover them.

I understand something could have gone bad, and Win7 could have destroyed contiguous partitions (since I put it on sda5, i expected something bad to happen to either sda4 or sda6), but the way it targeted my /home (sda2), and the way it wrote an huge amount of overhead data to the clusters, making any data recovery impossible, shows its intentionality.

I did a backup just 2 days earlier, so the damage was quickly contained, but you can be sure that this is the last  time I allow a M$ install disk near one of my computers.

---

### Post by Jerry N on 2009-11-25
I could just as easily claim that Ubuntu is "malware" since I have had Ubuntu destroy a Windows installation.  Of course I have had many successful Linux installs that were quite compatible with Windows.  I have also made several Win 7 installs, including dual and triple boot with Ubuntu, but I have never tried to install Win 7 _after_ installing Ubuntu.  It looks to me like that might be especially hazardous on a drive having extended partitions.

Jerry

---

### Post by wilee-nilee on 2009-11-25
If you didn't just leave a open space and use the custom install to point the installation at it then you were bound to fail, leaving out the not mentioned install source. What are you using to install and where did you get it?

---

### Post by bruno9779 on 2009-11-25
I installed using an original win7 ultimate disk. My company wants us to get a feel of it for tech support purposes.

The MBR was originally written by a win XP professional installation I had installed BEFORE Ubuntu to avoid this kind of problems.

I also expected it to have some issues, so I installed it between 2 "disposable" partitions (swap and Haiku). The way it went and overwrite the biggest partition without being asked to get even close to it, shows intentionality to me.

PS: I have successfully setup several multiboots before. This box had 9.04, XP, Haiku and frontline (not too sure the name is right) running fine before, side by side.

---

### Post by wilee-nilee on 2009-11-25
> **bruno9779 said:**
> I installed using an original win7 ultimate disk. My company wants us to get a feel of it for tech support purposes.

The MBR was originally written by a win XP professional installation I had installed BEFORE Ubuntu to avoid this kind of problems.

I also expected it to have some issues, so I installed it between 2 "disposable" partitions (swap and Haiku). The way it went and overwrite the biggest partition without being asked to get even close to it, shows intentionality to me.

PS: I have successfully setup several multiboots before. This box had 9.04, XP, Haiku and frontline (not too sure the name is right) running fine before, side by side.

A very strange occurrence you obviously know how to partition and multi boot. I am curious though did you use the custom install and point it at the correct partition. W7 also has a 100 Mib booting file set up that will go into another partition so this may be why it went haywire.

---

### Post by julianb on 2009-11-25
> shows intentionality to me.

There are zillions of accidental ways Windows can totally foul up your computer. Plenty of them could involve carelessness but they won't delete your data intentionally.

No more than Ext4 filesystem deleted people's data intentionally (it didn't). And it's not malice that makes Ubuntu installation crash and burn on certain machines, either. (and darn it my Karmic iMac install still doesn't display colors correctly.)

---

### Post by jrrader on 2009-11-25
Win 7 and Ubuntu (plus many others) coexist happily on my computer but not because I just threw them on and told them to play nice.  You have to be careful whenever you add another OS.  Fedora or Solaris will mess things up as well if you don't do it properly.

---

### Post by TheNessus on 2009-11-25
NEVER install windows (any version) AFTER linux. That's asking, no; begging, for trouble.

---

### Post by overdrank on 2009-11-25
Moved to  Recurring Discussions
Remember the COC.

---

### Post by armandh on 2009-11-25
+1

I dont know about 7 but xp likes to be the first primary  partition and only active partition.

my best luck in getting things where I want them to be is.....
leave unpartitioned space and instruct whatever else to install there.

when I do ubuntu by the above method selecting 'largest unpartitioned space' it always works for me

---

### Post by wilee-nilee on 2009-11-25
> **armandh said:**
> +1

I dont know about 7 but xp likes to be the first primary  partition and only active partition.

my best luck in getting things where I want them to be is.....
leave unpartitioned space and instruct whatever else to install there.

when I do ubuntu by the above method selecting 'largest unpartitioned space' it always works for me

I +1 your +1 pre formatting partitions is not for the beginner user.

---

### Post by liamnixon on 2009-11-25
I think calling it malware is rather extreme, but I can understand your frustration.   Windows 7 is pretty ballin' once you get it installed.

---

### Post by bruno9779 on 2009-11-25
> **wilee-nilee said:**
> I +1 your +1 pre formatting partitions is not for the beginner user.

I Left an empty unpartitioned space of 55 GiB for win7. Unlabelled and unformatted

I pointed the installer to it.

The first OS to be installed on this drive was win XP, so it didn't have to moan about MBR written by linux.

The first Logical partition wasn't /home but /, and it has been left untouched and working.

I just can't find any reasonable technical explanation for this, and that's why I am calling Win7 malware

---

### Post by Wiebelhaus on 2009-11-25
Yea , you have to install Windows first then your Linux distribution.

---

### Post by -grubby on 2009-11-25
> **bruno9779 said:**
> that's why I am calling Win7 malware

Yeah, and despite your bad experience Windows 7 isn't malware, and there exists no company named "M$"

---

### Post by bruno9779 on 2009-11-25
By malware I mean:

Any piece of software that can potentially harm me or my computer, not by chance but by design.

---

### Post by bruno9779 on 2009-11-25
> **-grubby said:**
> Yeah, and despite your bad experience Windows 7 isn't malware, and there exists no company named "M$"

If you say that there is no company called M$, it means that you know I am talking about a company, and since I didn't say that, it also means that you know which company I am referring to with the acronym M$

---

### Post by SunnyRabbiera on 2009-11-25
> **Jerry N said:**
> I could just as easily claim that Ubuntu is "malware" since I have had Ubuntu destroy a Windows installation.  Of course I have had many successful Linux installs that were quite compatible with Windows.  I have also made several Win 7 installs, including dual and triple boot with Ubuntu, but I have never tried to install Win 7 _after_ installing Ubuntu.  It looks to me like that might be especially hazardous on a drive having extended partitions.

Jerry

When you dont partition right you just ask for trouble.

---

### Post by Tipped OuT on 2009-11-25
> **bruno9779 said:**
> By malware I mean:

Any piece of software that can potentially harm me or my computer, not by chance but by design.

How can Windows 7 harm you, or your computer, unless there's some sort of user error?

I fail to see this.

---

### Post by wilee-nilee on 2009-11-25
> **bruno9779 said:**
> If you say that there is no company called M$, it means that you know I am talking about a company, and since I didn't say that, it also means that you know which company I am referring to with the acronym M$

That is his pet peeve. ;) we all need a pet of some sort.

---

### Post by lancest on 2009-11-25
> **TheNessus said:**
> NEVER install windows (any version) AFTER linux. That's asking, no; begging, for trouble.
Yes for sure. Windows will never be allowed on my machines (except in VM) taking the fastest cylinders of my hard drive.

---

### Post by Frak on 2009-11-25
> **bruno9779 said:**
> By malware I mean:

Any piece of software that can potentially harm me or my computer, not by chance but by design.
Still isn't malware. Also, there is no company named M$.

---

### Post by hoppipolla on 2009-11-25
> **bruno9779 said:**
> I did a backup just 2 days earlier, so the damage was quickly contained, but you can be sure that this is the last  time I allow a M$ install disk near one of my computers.

I don't blame you to be honest. I have seen similar things, but never anything that bad. I do hate the way Windows does things that are very harmful without even asking or warning you it is doing them :(

I am running 7 happily on here, but it's on a separate disk and I have a very simple set up. I do quite like it overall other than a fair few little niggles, but I also understand my experience has been better than quite a few people's.

Just use an older version of Win, or a separate drive :)

Sorry to hear about your loss of partition data ._.

---

### Post by Skripka on 2009-11-25
> **bruno9779 said:**
> I Left an empty unpartitioned space of 55 GiB for win7. Unlabelled and unformatted

I pointed the installer to it.

The first OS to be installed on this drive was win XP, so it didn't have to moan about MBR written by linux.

The first Logical partition wasn't /home but /, and it has been left untouched and working.

I just can't find any reasonable technical explanation for this, and that's why I am calling Win7 malware

Sandbox HDDs grasshopper. You got 2 OSes, use 2 HDDs.

---

### Post by MasterNetra on 2009-11-25
I thought you couldn't have more then 5 partitions? And btw Win7 adds two. Aside from the regular partition that it installs in, it reserves a 100mb "recovery" partition as well. Just thought ya should know.

---

### Post by KiwiNZ on 2009-11-25
Thread title edited

---

### Post by Frak on 2009-11-25
> **KiwiNZ said:**
> Thread title edited
Winnar

---

### Post by jrrader on 2009-11-26
> **bruno9779 said:**
> I Left an empty unpartitioned space of 55 GiB for win7. Unlabelled and unformatted

I pointed the installer to it.

The first OS to be installed on this drive was win XP, so it didn't have to moan about MBR written by linux.

The first Logical partition wasn't /home but /, and it has been left untouched and working.

I just can't find any reasonable technical explanation for this, and that's why I am calling Win7 malware

Any time you install an OS it will try to write the MBR at the start of hard disk unless you tell it not to (I don't believe Windows gives you the option not to, which is why it's important not to install Windows after Linux unless you're trying to teach yourself how to fix bad installs).  My brother-in-law dropped his laptop yesterday right before he was ready to go on a trip and XP would no longer boot.  I could still get into his files with a live CD but did not really have the time to fix it before he had to leave.  I ended up installing Ubuntu on a 4GB flash drive and tweaked it a little so he could get to his files easily.  Although it was installing to sdg1, install was still planning on writing the MBR to sda for some reason.

---

### Post by Frak on 2009-11-26
> **jrrader said:**
> Any time you install an OS it will try to write the MBR at the start of hard disk unless you tell it not to (I don't believe Windows gives you the option not to, which is why it's important not to install Windows after Linux unless you're trying to teach yourself how to fix bad installs).

You can, but it requires a custom winnt.sif file to be loaded at installation. I can't recall the exact flag right off hand, but I remember it was rather not documented well.

---

### Post by schauerlich on 2009-11-26
Installing 4 OS's with a complicated partitioning scheme is HIGHLY UNLIKELY to lead to data loss. There's absolutely no explanation for this other than that M$ is trying to destroy Linux one install at a time. You're a brave soul. Have you considered contacting Wikileaks with this information?

</sarcasm>

---

### Post by Tipped OuT on 2009-11-26
> **EDavidBurg said:**
> Installing 4 OS's with a complicated partitioning scheme is HIGHLY UNLIKELY to lead to data loss. There's absolutely no explanation for this other than that M$ is trying to destroy Linux one install at a time. You're a brave soul. Have you considered contacting Wikileaks with this information?

</sarcasm>

Damn, almost had me there, until I saw your sarcasm meter. I was about to go off. :p

---

### Post by Frak on 2009-11-26
> **Tipped OuT said:**
> Damn, almost had me there, until I saw your sarcasm meter. I was about to go off. :p
I know, realistic amirite?

---

### Post by wilee-nilee on 2009-11-26
So why are the two posters on here who have negative responses to M$; members of the linsux community one is a admin seems kind of contradictory.

---

### Post by KiwiNZ on 2009-11-26
> **wilee-nilee said:**
> So why are the two posters on here who have negative responses to M$; members of the linsux community one is a admin seems kind of contradictory.

Lets stop the Linsux references NOW . It  will help nothing.

---

### Post by wilee-nilee on 2009-11-26
> **KiwiNZ said:**
> Lets stop the Linsux references NOW . It  will help nothing.

Sorry man it wasn't meant as a reference to that group other then both terms mean nothing, and are basically meaningless. I could have worded it differently, and I suspect that this response is borne on a report of at the least of one the two members of the UF addressed. Personally I don't have a problem with any group or OS but a contradictory use of opinions even when parsed as they were in this thread just seem strange. It is the bullies pulpit to report rather then realize, if that is what has happened.

---

### Post by hoppipolla on 2009-11-26
> **EDavidBurg said:**
> Installing 4 OS's with a complicated partitioning scheme is HIGHLY UNLIKELY to lead to data loss. There's absolutely no explanation for this other than that M$ is trying to destroy Linux one install at a time. You're a brave soul. Have you considered contacting Wikileaks with this information?

</sarcasm>

joke is... if they were all Linux-based OSs... you'd probably be fine. It really is only Windows that keeps doing this over and over and over again. Windows does seem to destroy Linux very quickly if it gets the chance, without warning. Maybe it's just accidental, but even then, it's still sloppy :(

---

### Post by Frak on 2009-11-26
> **hoppipolla said:**
> joke is... if they were all Linux-based OSs... you'd probably be fine. It really is only Windows that keeps doing this over and over and over again. Windows does seem to destroy Linux very quickly if it gets the chance, without warning. Maybe it's just accidental, but even then, it's still sloppy :(

Fedora's default install will wipe all your Linux partitions, not wipe the disk, wipe Linux partitions.

Sloppy by design, see?

---

### Post by KiwiNZ on 2009-11-26
> **wilee-nilee said:**
> Sorry man it wasn't meant as a reference to that group other then both terms mean nothing, and are basically meaningless. I could have worded it differently, and I suspect that this response is borne on a report of at the least of one the two members of the UF addressed. Personally I don't have a problem with any group or OS but a contradictory use of opinions even when parsed as they were in this thread just seem strange. It is the bullies pulpit to report rather then realize, if that is what has happened.

The post was made as we are not going to tolerate sniping at other Web sites and members.

---

### Post by wilee-nilee on 2009-11-27
> **KiwiNZ said:**
> The post was made as we are not going to tolerate sniping at other Web sites and members.

I am sorry, I will keep my sniping to the people I love. ;)
Actually I like both of the people it looked as though I  was sniping @. I also stated my agnostic view of others=forums and OS.

---

### Post by schauerlich on 2009-11-27
> **hoppipolla said:**
> joke is... if they were all Linux-based OSs... you'd probably be fine. It really is only Windows that keeps doing this over and over and over again. Windows does seem to destroy Linux very quickly if it gets the chance, without warning. Maybe it's just accidental, but even then, it's still sloppy :(

Nearly all the time, a computer with Windows will only have Windows. A lot of the time, a computer with Linux will have something else on it, whether that's another distro or Windows/OS X/BSD/etc. It makes sense that Linux would be better in an environment in which it frequently finds itself, and Windows would be somewhat less adept.

---

### Post by hoppipolla on 2009-11-27
> **Frak said:**
> Fedora's default install will wipe all your Linux partitions, not wipe the disk, wipe Linux partitions.

Sloppy by design, see?

Ah fair do's although I never said I liked Fedora. I actually think Fedora is quite poor, at least in my experience. Ubuntu with KDE is my choice of Linux distro by far, and I make sure to point that out when people start dissing "Linux".


EDIT -- Although openSUSE occasionally has it's moments :)

---

### Post by Diluted on 2009-11-28
There may be an explanation for this: [http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html)

In short, Vista and 7 uses different cylinder boundaries for the partitions they create. Apparently this is good for larger disks in the future, RAID and SSDs. Mixing this with old cylinder boundaries can causing partitions to disappear.

If you want to install Vista/7 or create partitions from them onto a disk where old cylinder boundaries are in use, you should use your existing operating systems (e.g. Linux, GParted) to create the partition first, then having Vista/7 format it and install it. There is no problem on installing Vista/7 on a partition created using old cylinder boundaries.

---

