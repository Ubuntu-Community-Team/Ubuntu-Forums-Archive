---
title: "[Ubuntu/Win7] Windows not booting after Ubuntu install"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by Josh_Hopps on 2014-04-29
Hey guys 

Sorry to be a new guy who asks for help. Long time lurker but now I'm in a pickle :( 

Long story short, I installed Ubuntu 13.10 as dualboot with Win7 from a live usb. I've done that before, and all seemed to go to plan. I booted successfully into Ubuntu, but when I tried windows, no luck. 

If I select the windows loader from the grub menu, I get the option to launch windows normally or with startup repair. If I choose 'normally' (without startup repair), I just get stuck at the words 'windows is loading', but not even the coloured windows animation appears. If I choose startup repair, I get a grey bar with 'Windows is loading files', which also hangs there. 

I ran 'boot repair' from Ubuntu, it said it completed successfully but no luck. Here is the paste file from it: [http://paste.ubuntu.com/7359356/](http://paste.ubuntu.com/7359356/) I also tried to use ntfs-3g but for some reason it wouldn't install properly after I ran configure and make commands, so that was a dead end. 

I don't have a win 7 disc, Windows came installed on my laptop already. I need to be able to boot windows for my studies. All my important data is backed up, but there's programs I need to use which are windows - only. 

Please suggest what to do from here to recover windows. Any help is much appreciated, thanks in advance. 
Josh

Edit: and if I choose Windows recovery option (on /dev/sda2 or /dev/sda3)  from the grub menu, I get the same grey bar saying windows is loading files, which just hangs.

---

### Post by oldfred on 2014-04-29
Do not run Windows recovery unless you want to totally restore system. Sometimes that immediately rewrites the partition table and erases the Linux entries in partition table.
There are two recovery with Windows 7 systems. One is Windows repairs which you usually access with f8.
The other is a vendor recovery which may totally erase system and restore to like new. It is just an image of drive as purchased. You often can make a DVD set from that to have it separately so when hard drive fails you can restore system, but usually better to do a full image backup of Windows.

Always better to have repair CD or flash drive for the current version of every system installed. You can easily make a Windows repair flash drive when system is working but it can cost a bit to buy one.
[https://neosmart.net/blog/windows-recovery-discs/?ref=wiki-primary-menu](https://neosmart.net/blog/windows-recovery-discs/?ref=wiki-primary-menu)

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Grub really only boots a working Windows.
ntfs-3g is standard in Ubuntu now. You should not have to install.

Several things to try before buying a repairCD.
You can use Boot-Repair to install a Windows type boot loader and see if you can get into Windows repair console with f8. Grub is usually too quick to Windows for f8 to work. Some have had it work if pressed at almost same time. Then restore grub boot loader with Boot-Repair after fixing Windows.
If you run the auto fix in Windows you have to run it 3 times.

Some third party Windows partition tools also do some repairs/checks.
      
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

Or the EasyBCD may fix BCD issues. Free version is available for home use.
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)


 Hiren's Boot CD, and do a chkdsk on the XP
[http://www.hirensbootcd.org/](http://www.hirensbootcd.org/)

      
 Win7 forum
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by Josh_Hopps on 2014-04-29
> **oldfred said:**
> Do not run Windows recovery unless you want to totally restore system. Sometimes that immediately rewrites the partition table and erases the Linux entries in partition table.
There are two recovery with Windows 7 systems. One is Windows repairs which you usually access with f8.
The other is a vendor recovery which may totally erase system and restore to like new. It is just an image of drive as purchased. You often can make a DVD set from that to have it separately so when hard drive fails you can restore system, but usually better to do a full image backup of Windows.

Always better to have repair CD or flash drive for the current version of every system installed. You can easily make a Windows repair flash drive when system is working but it can cost a bit to buy one.
[https://neosmart.net/blog/windows-recovery-discs/?ref=wiki-primary-menu](https://neosmart.net/blog/windows-recovery-discs/?ref=wiki-primary-menu)

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Grub really only boots a working Windows.
ntfs-3g is standard in Ubuntu now. You should not have to install.

Several things to try before buying a repairCD.
You can use Boot-Repair to install a Windows type boot loader and see if you can get into Windows repair console with f8. Grub is usually too quick to Windows for f8 to work. Some have had it work if pressed at almost same time. Then restore grub boot loader with Boot-Repair after fixing Windows.
If you run the auto fix in Windows you have to run it 3 times.

Some third party Windows partition tools also do some repairs/checks.
      
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

Or the EasyBCD may fix BCD issues. Free version is available for home use.
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)


 Hiren's Boot CD, and do a chkdsk on the XP
[http://www.hirensbootcd.org/](http://www.hirensbootcd.org/)

      
 Win7 forum
[http://www.sevenforums.com/](http://www.sevenforums.com/)


Huge thanks for your help oldfred :) it was actually your comment about 'Grub is usually too quick to Windows for f8 to work. Some have had it work if pressed at almost same time.'... I went for the ninja approach and managed to enter Startup Repair with the F8 key immediately after selecting windows in grub. I got lucky again, it's one of the only times that Startup Repair has done something useful for me, as it was able to repair and boot Windows successfully. 

Huge thanks :)

P.S. As a side note, I couldn't see a way to give 'kudos' or 'thanks' or a 'like' on this forum. If there is a way and I've missed it, I'll come back and do it :)

---

### Post by oldfred on 2014-04-29
You did thank me, forum has no other way.

Glad you got it working. :)

I would not rely on f8 always working and suggest making a Windows repair CD or flash drive while it is working.
I have multiple repair ISO and multiple repair flash drives, most Linux. But then some also have belts and suspenders, but I have not gone that far yet.

---

### Post by Josh_Hopps on 2014-04-30
> **oldfred said:**
> You did thank me, forum has no other way.

Glad you got it working. :)

I would not rely on f8 always working and suggest making a Windows repair CD or flash drive while it is working.
I have multiple repair ISO and multiple repair flash drives, most Linux. But then some also have belts and suspenders, but I have not gone that far yet.

I beat you to it ;) I have already made a bootable usb from a windows 7 ISO. Right now I'm not concerned about losing any Linux data as I have none (clean install), but as soon as I have anything worthwhile I will begin to make backups and recovery methods. 

However, in your opinion is it better to use an ISO such as I have, or create a system repair drive? I guess I can use either hopefully for the same end result, but does one method seem to have more success than the other in your experience?

---

### Post by oldfred on 2014-04-30
I used to reinstall every 6 months and made new CDs for several repair tools each time. I was getting large stacks of CDs as all the repair tools would update by then. 
So I converted to directly booting ISO from a flash drive with grub2's loop feature. Not all can boot that way (Windows does not), but most Linux now do.
So then I can have one repair flash drive for all my repair tools and easily update just by copying the newer versions.

I consider my Ubuntu installer as a repair tool, but like to have others also.

---

### Post by Josh_Hopps on 2014-04-30
Ah I see. Well as of now I have enough backups to recover if the same thing happens to me again, and hopefully anything else as well. I've also bookmarked this thread for reference just in case, you gave me a lot of alternatives! :) 

Thanks once again for your help oldfred! Keep up the good work :)

---

