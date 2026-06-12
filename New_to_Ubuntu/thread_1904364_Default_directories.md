---
title: "Default directories"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by alanrwood on 2012-01-04
I am a newbie with Ubuntu 11.10 installed a couple of days ago. I have managed to solve most of my problems as it is on a 6 machine Windows network and they all seem to be communicating. I installed Ubuntu on a machine previously installed with Win7 which had been partitioned to keep all my documents off the C: drive (on the D: Drive named FDisk2) in case of windows problems requiring a re-install. Consequently all my original documents are still available and I can access them in Unity/Home Folder as FDisk2 is shown as a Device. I have managed to mount FDisk2 at boot using pysdm utility but I want my original "My Documents" directory to be the default and shown under "Computer".

I have edited <.config/user-dirs.dirs> to achieve this and it works until I reboot at which point the file is replaced again by the default versin and I am back to square one.one.  Please could anyone explain in very newbie simple terms how I can make this change permanent so it is not overwritten at boot.

---

### Post by I_can_see_the_light on 2012-01-04
Try changing the file to "read only". Right click on the file and go to the permissions tab.

---

### Post by alanrwood on 2012-01-05
Hi

Thanks for coming back.I had already tried all combinations of read on Read/Write etc and it still overwrote it on boot up. To add to the woes. I tried to boot this morning after normal shut down and it is not booting. Went through the Grub options to repair but it would not do it so I have just started a reinstall from scratch as it seems the quickest way to get back to square one and try again. As a newbie to Linux I guess I might have done something silly but I have had many years experience with Dos/Windows so I don't think so as I am always careful to back up files before changing them. Anyway I will get back if the problem persists

Thanks again

Alan

---

### Post by I_can_see_the_light on 2012-01-05
> **alanrwood said:**
> I tried to boot this morning after normal shut down and it is not booting. Went through the Grub options to repair but it would not do itEditing the [FONT="Lucida Console"]user-dirs.dirs[/FONT] file should not stop the machine from booting, something must have gone wrong elsewhere. It happens from time to time that updates causes problems but I have not experienced that myself though. 
> **alanrwood said:**
> I am always careful to back up files before changing themThat is really good practice. Make sure you know how to backup and replace from the terminal as well in case you edit any important files.

And welcome to the forums! :)

---

### Post by alanrwood on 2012-01-05
Thanks for replying. It has now taken me all day to reinstall after numerous attempts using the install CD. It kept failing every time for various reasons given (or not given due to complete freeze).

Eventually I had to use Easeus Partition Master CD to boot and delete all existing partitions, create 2 new ones (Main partition and swap) and leave them unformatted then reinstall from CD including format at that point. Am just up and running again so hopefully now that I only have the two partitions my original problem no longer arises. I will use this for learning and then recreate my original separate partitions for data etc and try again with a bit more experience under my belt.

Regards  Alan

---

