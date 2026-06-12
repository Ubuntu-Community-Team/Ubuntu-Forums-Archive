---
title: "Ready to make the switch... last couple question on partitioning"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by nickman1993 on 2013-01-06
Hey guys,

I'm excited yet nervous about switching to Ubuntu, but before I do anything serious I need a couple questions answered.

Background Info:
- I want to dual boot my Windows 7 with Ubuntu
- I plan to use Ubuntu for everything except gaming (I.e. all school stuff, productivity, media, etc [I am a sophomore in college])
- I cannot afford to lose Windows 7. Need to be as safe as possible during installs, setups, etc. I do not have a recovery disk.
- I know very little technical knowledge, but I'm also not challenged when it comes to computers. The more information during explanation the better.

1) I only have 49gbs of my 150gbs hard drive left. Is that enough to warrant using Ubuntu? How much should I allocate to Ubuntu to avoid problems and how much practical space would I have left over for other files and documents. 

2) Should I partition out space for data specifically. Is it better for me to have a place for windows, a place for Ubuntu, and a place for cross OS data storage. (Data I can pull from on windows & Ubuntu. Is this hard to do? Is it worth doing considering the small amount of space I have on my HDD?) OR should I just stick with only partitioning out Ubuntu through a livecd and not worrying about the rest

Non-Ubuntu based question, but that still is important:

3) I am going to make a system image disk for my windows PC. In the event of a problem, will that be able to restore my windows OS? (I know that that includes my current files, which is fine. In other words, If something goes terribly wrong I wont to have a fail safe that I can say, "sorry, Ubuntu, I tried but I cant afford to risk losing my windows 7.

(P.S If I need to provide any other information, just ask)
Thank you guys for reading and for any future responses

---

### Post by LiamOS on 2013-01-06
If you only plan on using Windows for games, here's my recommendation.

Back up music, videos, data, etc. to an external drive and uninstall and delete anything you do not need anymore. Defragment your hard drive, and then use Windows' disk manager to shrink the windows partition as much as possible. 
Ubuntu's installation should automatically handle the rest, unless you'd like to put a bit of personalisation into it.

---

### Post by JiuJitsu500 on 2013-01-06
You can quite easily do all of those things and more.

49GB is WAY enough to run ubuntu. And with Ubuntu One, you have and extra 5GB of cloud data for your school things you can acces anywhere (I have 2 android tablets, a mac, windows, and ubuntu and can see and edit my files from anywhere I have data connection).

Make a live USB first, and we can get started. I recommend Ubuntu 12.04, I prefer it over 12.10 because it's an LTS release and more stable. Not to mention it's supported for 5 years from release.

Once you have the bootable USB and can boot from it (hit "try ubuntu" and you won't affect your computer at all)... once you're in the live envirnment, we can partition, install, do anything you like. Dual-boot works very well, and it's worth it for sure. If you plan on using ubuntu for school only, I'd keep a mere 20-30GB of ubuntu space.

OR, back up all your data minus some space for games on windows, and then delete most of it to free up space on the rest of the HDD, that way ubuntu can breath with everything you have easily. Also, it can see and edit windows files from it's own manager, so you can freely open and close anything in that partition from ubuntu. I'd free up 20 or so GB at least, and let ubuntu have half or more of the HDD... but's that's just me.

Backing up your windows 7 HDD is very easy too, and can be done from linux live CD's or from various other tools. In any event, get into the live environment!

---

### Post by offgridguy on 2013-01-06
All good advice, i would add if you shrink your windows partition, leave a minimum
30% of free space as windows does not like it when partition gets too small.

---

### Post by Bartender on 2013-01-06
Wait a minute.  You've got a fairly modern PC that's running Windows 7, and it's only got a 150GB HDD??  That seems weird.  Is this an SSD we're talking about?

'Cause that's different, and there are a few tweaks that you need to perform (or at least check out) after installing to an SSD.

None of that matters in this case.  There's an old rule of thumb that I've heard repeated more than once, and AFAIK it applies to Linux as well as Windows.  I'm not really sure if it applies to SSD's??

Once you go under 20% free space the OS will start to slow down.  If you allocate almost all of the remaining free space to an Ubuntu partition you're going to have trouble on the Windows side for sure, and possibly the Linux side too.

I'm reading over your first post again - do you know what you've got now for partitions?  It's all too common nowadays for Windows PC's to have 4 primary partitions on them.  That's a game-stopper unless you're willing to do some data destruction, which of course means taking a risk with the existing Windows install.

You mention that you cannot lose Windows.  And your HDD is too small.  The simple answer is, "Don't do it."

If you have a desktop PC I'd say the only option that solves both problems is to get a second HDD, install Ubuntu to that HDD completely independent of the Windows drive, then use your BIOS "quick boot" option when you want to boot to Ubuntu instead of Windows.  In other words, unplug the Windows drive, install Ubuntu to the second drive, then plug the Windows drive back in.

If this is a laptop we're talking about, then I'd say "don't do it".  Not without dropping in a bigger HDD or SSD.

Another option, which LiamOS mentions, is to strip everything you can from the Windows install, defrag a few times, and go from there.  If you can get W7 down to 40 or 50GB (I don't know how much space Windows hogs nowadays) then you could split the drive about 60/40 Windows/Linux.  But you'd have to be on the alert for data creep.

---

### Post by Impavidus on 2013-01-06
I agree with the previous posters.

Ubuntu needs about 7GB for the system and the more or less default applications, so 49GB is plenty. If you want to share data between windows and ubuntu it's best to have a separate data partition (maybe you already have), formatted NTFS (windows format). Ubuntu can read and write windows file systems, although writing on the "windows C drive" is not recommended, but windows cannot read nor write the linux file system.

Ideal sizes of your partitions depend on how you want to use your computer, but if windows is just for gaming, I suggest you make the windows partition small (use the windows partition editor). Make a shared data partition for files you want to access from both systems (don't make it too big, games won't need your ubuntu files) and a couple of linux partitions. The installer can hangle most of it automatically, but you may want manual finetuning.

One important point though, not mentioned by the others: how many partitions do you have now on your computer? Using MBR formatting (most likely in your case) you can have four primary partitions at most. If the computer came with four primary partitions preinstalled, what frequently is the case with win7, depending on your vendor, repartitioning the hard drive without losing important data is a bit tricky.

Oh, just read Bartenders reply:
Indeed, your windows will get really squeezed into its partition. It may indeed be time for an extra drive or a good cleanup of your media files (maybe move them to an external drive). Most people who fill their hard drive do so by collecting media. Otherwise, it may be possible to install ubuntu on an external drive.

---

### Post by Mark Phelps on 2013-01-06
> **nickman1993 said:**
> ...- I cannot afford to lose Windows 7. Need to be as safe as possible during installs, setups, etc. I do not have a recovery disk...

Then, BEFORE you do anything else, use the Win7 Backup feature to create and burn a Win7 Repair CD.  At least, this way, you will have a way to repair the Win7 boot loader -- should anything happen during your dual boot install.

And, to emphasize what others have mentioned, do NOT use the Ubuntu installer, or GParted, to shrink thw Win7 OS partition.  This can lead to corruption of the Win7 file system, rendering it unbootable.  Instead, use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition.

And, when in the Win7 Disk Management utility, be sure to confirm that you do NOT already have 4 partitions (the utility will call them "drives") on the disk.  IF you do, and you force the creation of a fifth partition, that will convert your partitions into Dynamic Disks -- something you do NOT want to do.

---

### Post by offgridguy on 2013-01-06
If you need it, there are some links in this thread, on making a repair CD

[http://ubuntuforums.org/showthread.php?t=2102257](http://ubuntuforums.org/showthread.php?t=2102257)

---

### Post by nickman1993 on 2013-01-06
Okay, so I checked my HDD to make sure there weren't any other partitions and when i went into the disk manager it said that there wasn't any other partitions.

This laptop (Latitude E6500) initial had Windows Vista (I believe 64bit) on it and it was given Windows 7 professional (32bit) by the previous owners business company.

I think what I plan to do is this:
 - Get an external drive and drop pretty much everything from my mydocuments into here. That should hopefully clear up at least like 20/30gbs+ 
 - Use 30gbs for Ubuntu and then partition the other 30/40gbs for data usage (as NTFS) and swap data using external HDD if needed
 - Use windows disk manager to shrink the windows partition
 - lastly, use the ubuntu livecd to start the installation.
 - Prior to this I will have: compressed HDD, Defragged it, created both a repair disc and a system image disc

Are there any flaws with this plan? Anything I should not do? I tried to listen to all of the advice given and I appreciate all that you guys had to say. Thank you again

---

### Post by offgridguy on 2013-01-06
> **nickman1993 said:**
> Okay, so I checked my HDD to make sure there weren't any other partitions and when i went into the disk manager it said that there wasn't any other partitions.

This laptop (Latitude E6500) initial had Windows Vista (I believe 64bit) on it and it was given Windows 7 professional (32bit) by the previous owners business company.

I think what I plan to do is this:
 - Get an external drive and drop pretty much everything from my mydocuments into here. That should hopefully clear up at least like 20/30gbs+ 
 - Use 30gbs for Ubuntu and then partition the other 30/40gbs for data usage (as NTFS) and swap data using external HDD if needed
 - Use windows disk manager to shrink the windows partition
 - lastly, use the ubuntu livecd to start the installation.
 - Prior to this I will have: compressed HDD, Defragged it, created both a repair disc and a system image disc


Are there any flaws with this plan? Anything I should not do? I tried to listen to all of the advice given and I appreciate all that you guys had to say. Thank you again
It looks to me like you have things well in hand. :D  Good luck.

---

