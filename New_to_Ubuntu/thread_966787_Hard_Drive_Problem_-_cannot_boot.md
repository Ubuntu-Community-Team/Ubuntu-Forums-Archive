---
title: "Hard Drive Problem - cannot boot"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by carusoswi on 2008-11-01
So, my master drive has stopped identifying itself properly to my system.  I pulled it and popped it into one of my external firewire boxes, plugged it into my second Ubuntu box and up comes two drives, disk 1 and disk 2 - one is my XP partition, the other contains all my Ubuntu partitions and files.

I can browse these disks/folders, and all the data appears to be fine.

My question:  Is there a way to copy an image of this disk to save it as is, then, perhaps, try to use a disc utility to wipe it and then copy the image back onto the disk (or even another disc if I cannot get this one to properly enumerate itself)?

Most of the data is nothing valuable - just system files, etc.

Some of the data is important (which I would obviously copy to back it up).

Has anyone had this sort of experience?  When I boot with this drive installed, I get an os error, or, if I go into my bios setup, I can auto-detect the drive, but the result is some gobbly-gooked up version of the drives name (it should be a WD-xxxx...) but is now a w#@@, etc. some characters only found in computer gobblygook that I can't even find on the keyboard.

Advice welcome and appreciated.

Thanks.

Caruso

---

### Post by cdtech on 2008-11-01
It sounds like a corrupt boot sector.

You could use this link: [http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/) for using the dd command to copy the contents of the drive.

---

### Post by carusoswi on 2008-11-02
Thanks for your reply.  I pulled the drive out, popped in another that I had used to test out Linux Mint, reinstalled XP, then a fresh install of 8.10 since my existing installation was an upgrade.  This allowed me to make proper partition arangements which weren't quite to my liking anyhow.

I'm in the process of reloading all my XP aps at the moment, and will simply copy the important data from the problem drive a little later in the day.

Talk about a pain, getting XP to install over a drive 100% formatted for Linux was truly a pain.  I finally succeeded by using the XP repair console to format the drive (first couple of attempts were not successful . . . don't know why).  Unlike XP, when you install Linux, it just does what you tell it to do, no complaints.

My dual boot is installed now, so, I'm a happy camper except that I have to sit here an load up all my XP aps (not that many, but it's a slow process.  

Thanks again.

Caruso

> **cdtech said:**
> It sounds like a corrupt boot sector.

You could use this link: [http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/) for using the dd command to copy the contents of the drive.

---

