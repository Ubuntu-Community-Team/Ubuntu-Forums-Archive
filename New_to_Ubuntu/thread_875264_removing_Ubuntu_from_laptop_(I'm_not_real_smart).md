---
title: "removing Ubuntu from laptop (I'm not real smart)"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by kmm_tm on 2008-07-30
[[ repost from [http://forums.afterdawn.com/thread_view.cfm/687777](http://forums.afterdawn.com/thread_view.cfm/687777) ]]

(Very sorry if this question has been asked before; I searched Google and Afterdawn, and none of the solutions worked)
(and I looked at these forums. I don't understand any of it. At all)

I'm not a very smart guy.
Linux/Ubuntu is for the more...intellectually inclined.

Anyways...

I'm working on a Dell 5150 laptop with Windows XP service pack 2.
It holds approx 27 GB of memory and has 256 MB of RAM.

Here is what I did:
1) Downloaded the ISO from Ubuntu's website
2) burned it to disc
3) Opened the disk in Windows
4) Look at it for a bit.
5) Opened Partition Magic and backed up all information to "drive s"
6) Made an "Ubuntu" partition on my external hard drive.
7) Booted from the Ubuntu disc.
8) Did the CD integrity check thing, found 0 problems.
9) In confusion, opened the CD in Windows and tried to install to the "u drive"
10) rebooted
11) When the computer asked which OS to boot to, I chose Ubuntu
12) Got horrible, horrible time on it. (I waited 30 minutes; very non-responsive)
13) Figured the hassle is not for me, and decided to get it off.
14) Loaded XP installation disc, went to recovery console and gave commands "fixmbr" and "fixboot".
15) Restarted, but still found the boot menu.
16) Deleted the Ubuntu Partition
17) Repeated step 14
18) Restarted, but still found the boot menu.

So, I want to take everything Ubuntu off my computer.
But, I'm not so good at this kind of thing, so you might want to use as non-technical terminology as possible.

I want it all off. The GRUB and everything.

---

### Post by steveneddy on 2008-07-30
256 mb of RAM is the bare minimum to run Ubuntu.

I think it may take 512 mb to run well.

Just Partition Magic to reformat the partition and then merge it with the Windows partition.

You might your hardware compatibility to see if that machine works well on Linux in general.

---

### Post by pi.boy.travis on 2008-07-30
Did you install via Wubi?  What do you mean by "In confusion, opened the CD in Windows"?

---

### Post by Helios1276 on 2008-07-30
Sounds like you had too little ram to me, try running vista on 512 ;) Use gpart/parted magic etc to delete all partitions but the windows one. Then 'grow' the Windows partition to fill the drive. Your Windows cd will let you fix booting I think. Correct me if I'm wrong here guys.

---

### Post by JoneYee on 2008-07-30
If you want to go through with it, to remove GRUB:

Boot to the Windows Recovery console: 
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

To remove grub, from recovery console type:
```
fixmbr
```

That will change the Master Boot record and remove Grub from the boot sequence and make Windows the default.

---

### Post by kmm_tm on 2008-07-30
> 256 mb of RAM is the bare minimum to run Ubuntu.

I think it may take 512 mb to run well.

Just Partition Magic to reformat the partition and then merge it with the Windows partition.

You might your hardware compatibility to see if that machine works well on Linux in general.
A new lesson: always exceed recommendations!

I actually did that. It still has the "select OS" screen.

> Did you install via Wubi? What do you mean by "In confusion, opened the CD in Windows"?
I'll clarify. I went to [this site](http://www.ubuntu.com/getubuntu/download) and downloaded the ISO file. Then, I burned to a disc. I opened the CD in Windows and it gave me a dialogue box. It gave me 3 options:
"Install Ubuntu as a Windows app", "Install Ubuntu", and "Learn More"

> Sounds like you had too little ram to me, try running vista on 512 Use gpart/parted magic etc to delete all partitions but the windows one. Then 'grow' the Windows partition to fill the drive. Your Windows cd will let you fix booting I think. Correct me if I'm wrong here guys.
Ack! Vista on 512 o.O
You mean like Partition Magic? So, lemme get the straight. You want me to (of course back up first) format all of the partitions EXCEPT the main partition. Then, redistribute space. Did that already. XP
And yes, one can fix booting with the Windows CD.

> If you want to go through with it, to remove GRUB:

Boot to the Windows Recovery console:
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

To remove grub, from recovery console type:

Code: fixmbr

That will change the Master Boot record and remove Grub from the boot sequence and make Windows the default.
Oh, I did the "fixmbr" and "fixboot" thing in the Windows recovery console. It didn't work though. o.O

(BTW, thank you all for trying to help)

---

