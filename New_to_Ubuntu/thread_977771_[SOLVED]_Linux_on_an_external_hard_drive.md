---
title: "[SOLVED] Linux on an external hard drive"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by rare-beast on 2008-11-10
I am going to buy an external hard drive mainly to install some form of Linux on but I also want to back up my Mac and Xp machines on to it, is this possible? oh yeah I would like to be able to change distros every so often, thanks for any help.

---

### Post by Carl Hamlin on 2008-11-10
> **rare-beast said:**
> I am going to buy an external hard drive mainly to install some form of Linux on but I also want to back up my Mac and Xp machines on to it, is this possible? oh yeah I would like to be able to change distros every so often, thanks for any help.

Sure. The Ubuntu installer will treat your external drive like any other block device. However - I'd recommend against installing on a flash drive. Flash can only sustain a finite number of write/erase cycles before failing, and if you run a swapfile on the flash you're going to severely shorten the lifespan of your drive.

---

### Post by rare-beast on 2008-11-10
Do I have to partition the drive or what do I have to do?

---

### Post by jimv on 2008-11-10
Yes, you want to partition it up.  For the Windows backups, you'll want to create a FAT or NTFS partition.  For Linux, you'll need EXT3 and swap.  Ubuntu can install on a 4 gig partition, but it would be more comfy to put it on a 20 or so gig partition.  The swap partition only needs to be about 2 gigs.

You can set this all up during the Ubuntu install.  Just remember to choose "/" as the mount point for the Ubuntu partition.  Also, at the final step of the installation, click Advanced and set it to install GRUB onto your portable drive, not the drive inside your machine.

---

### Post by rare-beast on 2008-11-10
So I need two partitions for Linux (OS and Swap), what about the Mac backups, what is GRUB and what will I have to do if I want to change the distro?

---

### Post by Carl Hamlin on 2008-11-10
> **rare-beast said:**
> So I need two partitions for Linux (OS and Swap), what about the Mac backups, what is GRUB and what will I have to do if I want to change the distro?

GRUB is your bootloader.

What you'll have to do to change the distribution depends somewhat on the distribution, but for most you can assume you'll have to wipe your existing linux partition and install the new distribution to it.

---

### Post by rare-beast on 2008-11-10
How would I wipe that partition and would it actually wipe the partition or the contents of the partition?

---

### Post by Carl Hamlin on 2008-11-10
> **rare-beast said:**
> How would I wipe that partition and would it actually wipe the partition or the contents of the partition?

Again, it depends on the distribution. Some distribution have a utility to take care of that for you during installation. If you're installing a distribution that doesn't, you'd have to make use of a partition editor like PartEd.

Wiping the partition makes the contents generally inaccessible in preparation for them to be written over.

---

### Post by rare-beast on 2008-11-10
How would I make the other partitions for my backups? Thanks for your help.

---

### Post by tahitiwibble on 2008-11-10
> **rare-beast said:**
> Do I have to partition the drive or what do I have to do?

You'll **definitely** want to create a separate partition for your "HOME" folder. This means one partition (ext3) for the Ubuntu system files and one partition (ext3) for your "Home" folder which is where all your documents and settings etc. are stored. I only just found out about this but believe me you won't regret it!

Idefix82 **really** helped me out in this thread [http://ubuntuforums.org/showthread.php?p=6127634#post6127634](http://ubuntuforums.org/showthread.php?p=6127634#post6127634)

---

### Post by Keen101 on 2008-11-10
I would recommend the Gparted Live-Cd for partitioning. Ubuntu does come with gparted when installing, but i still find the Gparted Live-cd easier for creating partitions. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Now for the windows and OSX backups what are you exactly trying to do? Do you want OSX installed on the external drive? or just to backup random files?

If you are just backing up random files, then i'd just partition the back half of your external drive in FAT32. OSX, and windows can read/write fat32 just fine. And then just leave the first half of your hard drive blank, and select "use largest continuous free space" when installing ubuntu.

---

### Post by rare-beast on 2008-11-10
I am getting confused with what I have to do, could someone point me towards a tutorial or explain to me in simple terms what I have to do, thanks in advance.

---

### Post by rare-beast on 2008-11-10
> **Keen101 said:**
> 

Now for the windows and OSX backups what are you exactly trying to do? Do you want OSX installed on the external drive? or just to backup random files?

If you are just backing up random files, then i'd just partition the back half of your external drive in FAT32. OSX, and windows can read/write fat32 just fine. And then just leave the first half of your hard drive blank, and select "use largest continuous free space" when installing ubuntu.

I am looking to backup using Time Machine, so I want to have bootable backups.

---

### Post by tahitiwibble on 2008-11-10
Sounds like you want three separate bootable systems on the external HD???

What are you going to use to install Linux?

---

### Post by Keen101 on 2008-11-10
I am not familiar with Time Machine, but if it supports FAT32 it should work fine. If not you might have to use gparted to make a HFS+ partition.

---

### Post by malty on 2008-11-10
jimv, sorry to butt in, I am about to do the same, add an external USB drive...
"You can set this all up during the Ubuntu install. Just remember to choose "/" as the mount point for the Ubuntu partition. Also, at the final step of the installation, click Advanced and set it to install GRUB onto your portable drive, not the drive inside your machine."

What is the reason for that, is it in case you need to use the drive on other computers?
Also I use disc director in windows to create free space partitions and let the Ubuntu installation do the rest, will Ubuntu's partitioner do this?

---

### Post by rare-beast on 2008-11-11
> **malty said:**
> Just remember to choose "/" as the mount point for the Ubuntu partition.

What is the reason for that, is it in case you need to use the drive on other computers?


What does "/" mean? I want to be able to use Linux on any computer I plug the hard drive into. I would also like to be able to boot up my backup of Windows on any computer that I plug the hard drive into but I think I have to **install Windows** on the hard drive to do that.

---

### Post by Carl Hamlin on 2008-11-11
> **rare-beast said:**
> What does "/" mean? I want to be able to use Linux on any computer I plug the hard drive into. I would also like to be able to boot up my backup of Windows on any computer that I plug the hard drive into but I think I have to **install Windows** on the hard drive to do that.

'/' is the mount point for your root directory on most (if not all) linux distributions.

However, if you're wanting an installation of linux that's going to work on *every* computer, various and sundry, I'm afraid you're asking for the world. If you're using the x86 instruction set, then your linux drive will only work when connected to a machine that understands x86 instructions. Same for the AMD and PowerPC instruction sets, and indeed the same holds true for your bootable Windows partition. In order to make this happen you'd have to have *6* bootable partitions on your drive, each containing a full installation of a different flavor of linux/windows so you could cover all the common bases, and even *then* there would be esoteric devices your drive wouldn't boot on, not to mention the nightmares associated with juggling userdata between all of those operating systems.

Probably better to pick an instruction model that you work with regularly and stick with it.

---

### Post by caljohnsmith on 2008-11-11
> **rare-beast said:**
> What does "/" mean? I want to be able to use Linux on any computer I plug the hard drive into. I would also like to be able to boot up my backup of Windows on any computer that I plug the hard drive into but I think I have to **install Windows** on the hard drive to do that.
The "/" means the root file system for Ubuntu, or basically the whole file system; when you install Ubuntu, if you choose a partition to install Ubuntu to with a mount point of "/", then that's where your entire Ubuntu installation goes. But you have a choice of putting some of Ubuntu's directories on other partitions if you want; for instance, you can put the "/home" directory on another partition (by setting the mount point of that partition as "/home" in the installer), so that your personal documents are entirely on a separate partition. It's like putting Windows' "My Documents" on a different partition. You don't have to use that feature if you don't want though, it's entirely up to you.

If you want a step-by-step guided tutorial of how to install Ubuntu with lots of great screen shots, you could try [Herman's website]("http://www.herman.linuxmaniac.net/p22.html"). The important thing is to do like jimv said, and at the last part of the installation (step 7 in Herman's guide), click the "advanced" button, and specify Grub to be installed to your external Ubuntu drive, which will most likely be /dev/sdb. Give Herman's tutorial a shot and let me know how it goes. :)

---

### Post by rare-beast on 2008-11-11
Ohhh...!
I didn't realise it would be that hard!
I will just install one version for my computer. If I partiton the hard drive into 3 partitions (mac backup, windows backup and Linux) with gparted, when I go to install Linux (probably Ubuntu) will it recognise those partitions so that I could install it where I want and how much space I want to give it?
Thanks everyone for your help!

---

### Post by Carl Hamlin on 2008-11-11
> **rare-beast said:**
> Ohhh...!
I didn't realise it would be that hard!
I will just install one version for my computer. If I partiton the hard drive into 3 partitions (mac backup, windows backup and Linux) with gparted, when I go to install Linux (probably Ubuntu) will it recognise those partitions so that I could install it where I want and how much space I want to give it?
Thanks everyone for your help!

Yep - during the Ubuntu installation there's a whole section involving specification and possible resizing of partitions. It may sound complicated here in the forum, but when you're sitting in front of it you'll see it's pretty straightforward.

---

### Post by rare-beast on 2008-11-11
Thanks everyone, when I get going I'll let you know how it turns out!

---

### Post by rare-beast on 2008-11-11
> **tahitiwibble said:**
> You'll **definitely** want to create a separate partition for your "HOME" folder. This means one partition (ext3) for the Ubuntu system files and one partition (ext3) for your "Home" folder which is where all your documents and settings etc. are stored. I only just found out about this but believe me you won't regret it!

Idefix82 **really** helped me out in this thread [http://ubuntuforums.org/showthread.php?p=6127634#post6127634](http://ubuntuforums.org/showthread.php?p=6127634#post6127634)

What is the advantage of having your home folder in a different partition?

---

### Post by rare-beast on 2008-11-11
> **caljohnsmith said:**
> 
If you want a step-by-step guided tutorial of how to install Ubuntu with lots of great screen shots, you could try [Herman's website]("http://www.herman.linuxmaniac.net/p22.html"). The important thing is to do like jimv said, and at the last part of the installation (step 7 in Herman's guide), click the "advanced" button, and specify Grub to be installed to your external Ubuntu drive, which will most likely be /dev/sdb. Give Herman's tutorial a shot and let me know how it goes. :)

I had a look at that, it is a great tutorial, very simple to understand, thanks for that!

---

### Post by tahitiwibble on 2008-11-11
> **rare-beast said:**
> What is the advantage of having your home folder in a different partition?

In simple terms, it means that when you update from one version of Linux to the following, all you have to worry about is upgrading/installing the new system files in **their** own partition and all your personal files and settings etc are safe and sound in **their** own **separate** partition. While installing the updated system software you designate your old /home directory as the new system's /home directory and keep all your work files & settings intact and immediately available for the new system to use.

I hope that made sense.

---

### Post by rare-beast on 2008-11-12
It makses sense but can I install a different distro and still use that home folder?

---

### Post by Carl Hamlin on 2008-11-12
> **rare-beast said:**
> It makses sense but can I install a different distro and still use that home folder?

Depends on the distribution, but most should allow you to do so.

---

### Post by rare-beast on 2008-11-12
Would this plan of action be the right way to go about it?

1.Boot up with Ubuntu live cd and make 4 partitons (Mac backups, Windows backups, Home folder and Linux OS files). Do I make a partiton for swap? I have half a gig of ram.
2.Run the Ubuntu installer, installing my home folder in a different partition and in "advanced options" install GRUB.
3.Backup my two computers into the other partitons.

---

### Post by Comhra on 2008-11-12
Welcome to Ubuntu forums.  I know you'll enjoy Ubuntu.  Hope your plan works.  Let us know how you get on. 

Slán ;)

---

### Post by rare-beast on 2008-11-14
While I was waiting to get a hard drive I installed Puppy on a flash drive, it works great!

---

