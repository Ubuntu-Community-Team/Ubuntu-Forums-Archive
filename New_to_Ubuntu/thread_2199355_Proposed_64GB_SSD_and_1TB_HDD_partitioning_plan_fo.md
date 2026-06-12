---
title: "Proposed 64GB SSD and 1TB HDD partitioning plan for new build. Comments please"
date: 2014-01-13
forum: New to Ubuntu
---

### Post by technology4 on 2014-01-13
Hi. I'm planning to cross the great divide to Linux now that XP is in it's last gasps of life ;)  Been in IT for 45 years: mainframes, then DOS/Windows for 30 years. Going back to using the command line and learning a new environment is going to be strange ;) 

I'm about to order a new system box (see below) and my existing box will be a hand-me-down to my wife and will also have Linux put on it (maybe PCLinuxOS which I did install on my laptop many years ago when it died after a Windows update). Enough rambling, so to my first question.

I would be grateful if someone could review the partition plan below. In particular the SSD allocation and size before I submit the order. If 64GB is too small then I could go to 120GB but, due to cost, would probably have to go for a cheaper SSD. My aim is to backup frequently changing data daily and to avoid data spread (current & previous PCs had 17 partitions).

[IMG]http://www.alancooper.me.uk/images/Partition%20Plan%20v1.jpg[/IMG]

Alan in the UK

My use: Heavy office user with typically 5-10 apps open + typically 10 Firefox tabs open + 5 or more folders open. Lots of firing up of apps and can be slow to close them. Constantly flicking between windows (Alt+Tab is my favourite keystrokes). Occasionally heavy graphics with Gimp (high res print quality posters and banners). Some PC web development increasingly with a CMS. Looking to learn CAD for 3D printing. Increasing amounts of video streaming and Flickr. No gaming. I try to hot key rather than use slow mouse.

Planned hardware: Fractal Design Define R4 Gaming White Midi Tower, XFX XXX Edition 650W Power Supply 80 Plus Bronze, Gigabyte 990FXA-UD3 rev 4, AMD FX-6300 Black Edition 3.5GHz Socket AM3+ 8MB cache, Arctic Cooling Freezer 7 Pro Quiet (Rev 2), Corsair Vengeance Red LP 8GB DDR3 1866MHz, PNY NVIDIA Quadro 600 1GB PCI-Ex16, Corsair Corsair Neutron Series 2.5" 64GB SSD 3yr, Western Digital Black 1TB SATA III 7200RPM 64MB 5yr, Pioneer DVR-S20LBK 24x DVDÝRW Black SATA II, BenQ BL2405HT 24" Full HD LED Monitor

Planned software: Ubuntu latest release full distro, Wine, Virtual Box if Windows apps don't work under Wine

---

### Post by Jason_Gibson on 2014-01-13
I'm not understanding why you need separate partitions for stuff like /tmp, and /var. You don't have to make a NTFS to share with your Win XP computer just set up a samba share from a given folder. I personally would put 20 or 25gb for / on the ssd,  and rest for /apps. Move wine installs & virtual machines folder into /apps and link them to /home on the spinner. Put swap on the spinner as well. I wouldn't bother with a specific backup partition on the machine itself rather set up an rsync script to run every hour or so ( mine runs every half hour ) to backup the directories you want to the nas. Mount the nas to maybe /media/backups? Everything else I would personally just put in /home. I would like to know the reason for so many partitions in your plan though as I just don't see the need or point. Seems to over complicate things to me.

*EDIT* EFI is annoying with linux. If the hardware can boot bios mode I would suggest that instead of messing with EFI... Unless you need some feature it has or something. Other thing. Your 1tb hdd won't format out at 1000gb. Mine is 931gb available due to overhead I guess. I would imagine the ssd would be similar. May want to go 128gb on the ssd

---

### Post by technology4 on 2014-01-13
Hi Jason, many thanks for a prompt and helpful reply.

No doubt I'm bringing some baggage from a Windoz environment. Like I'm using True Image (TI) to backup whole partitions and for speed and for keeping the images small I spread the data according to type of data and speed of change. TI is nice in that I can mount a backup and see all the folders in their normal hierarchy and quickly navigate to a particular file - zip files (winzip) is not so friendly. I've also been wary of massive zip files.

Currently I don't backup directly to the NAS. I've only just got it (using external USB drives before and DVDs prior to that). I'm very disappointed with the speed of the NAS even on a GB network with CAT6 cables. I suspect it's my current PC with a slow bus. We shall see when I get the new PC. So now I quickly backup my active data to the /backup partition using a schedule task and then afterwards in the background move to the NAS. 

Some very good suggestions like moving wine and VM to /apps and mounting the NAS. Your rsync script will be very useful :) 

Many thanks for the EFI suggestion. Critical to get that right at the beginning :)  No reason to use it other than Logical partitions seem ancient, but as they work, I'm happy to continue using them. 

Alan

---

### Post by Bucky Ball on 2014-01-13
Welcome.

Rule of thumb: OSs and programs on the SSD, data on the HDD. If you are sharing data with Win on the same computer, yes, NTFS partition for sharing.

EFI: If you have Win already installed in EFI Ubuntu MUST be installed in EFI. There will already be an EFI partition created by Win but Ubuntu will not necessarily show it with a label. If you install Ubuntu in EFI then it will 'automagically' recognise the EFI partition created by Win and install grub to that. Yes, you DO need to switch off secureboot, fastboot, and any other Win related boot options and also disable faststart from within Win software itself (there are numerous how-tos on this).

If installing in EFI you MUST choose 'Something Else' and manually partition at the partitioning section of the Ubuntu install.

Unsure why you would have all these separate partitions for things like 'Photos' etc., but perhaps you have your reasons. Creating a large /home partition (or else you will end up with a /home directory in /) will contain directories for personal data by default. (PS: A 9Gb /home directory/partition won't get you far ... that will fill up in no time. ;))

---

### Post by oldfred on 2014-01-13
I have 4 hard drives, two old 160GB, a somewhat newer 640GB (my last MBR drive) and my now two year old SSD. I partitioned with gpt on new drives since 10.10 as you can boot with UEFi or BIOS with Ubuntu from gpt partitioned drives.
Windows only boots from gpt partitioned drives with UEFI, and XP will not even read a NTFS partition on a gpt drive.

I was planning (and still am) a new system with UEFI, so I made both and efi partition and the bios-grub partition so I could move drive to new UEFI system without totally reformatting. And my SSD is 64GB so I created two / (root) partitions, one current install and one next or test install. All data is on rotating drives. But I do not do like the old Redhat server type install I did many years ago and have separate partitions for many system folders. You really only need / and swap. I also want each drive to boot without any other drive, so when one fails I can still boot the other. So essential files are always on same boot drive. Data, swap or those that may give a boot error but will continue then may be on other drives. I also keep /home inside my / and use about 11GB of my 28GB / partition. But all data is in rotating drive and I use linking to include all the data folders normally in /home.

Some systems seem to work better with UEFI than others. There are a few that just do not work or are so difficult to reconfigure that users give up and either only boot Windows or boot Ubuntu in BIOS mode. But some just install and work well in UEFI mode.

---

### Post by technology4 on 2014-01-13
Many thanks Bucky for your advice. Good rule of thumb re the SSD/HDD split.

The PC will be virgin without software or formatted disk. I recall reading that I need to set the BIOS to legacy and boot from CD or USB stick which has the appropriate EFI or non EFI distro on it. [I'll double check that]

The reason for separate partitions is to match the data to backup frequency. My current data partition with my active projects and data is 5GB and backups up as a partition image in a few minutes. 

My thoughts are that a bigger /home will be backing up data that changes infrequently and over time will consume more space on the backup media. If I move to folder backup then I could have less partitions. I could also use incremental backups more - I tend to be wary of these in case one of the increments fails.

On my Windows PC I don't really use Desktop and My Documents (which I guess is the equivalent to /home) but have folder short cuts on the desktop for various active projects. These then point to the relevant folder on the data partition. When a project is finished the data is moved to archive (sometime as a zip). Ditto with the email folders for the project. The archive partition is then backed up again. Been doing this for 15 years or more - old habits die hard ;)

Thanks again,
Alan

---

### Post by Bucky Ball on 2014-01-13
> **technology4 said:**
> 
I ... have folder short cuts on the desktop for various active projects. These then point to the relevant folder on the data partition. When a project is finished the data is moved to archive (sometime as a zip). Ditto with the email folders for the project. The archive partition is then backed up again. Been doing this for 15 years or more - old habits die hard ;)

Good habits to have.

---

### Post by Jason_Gibson on 2014-01-13
> [COLOR=#000000]My thoughts are that a bigger /home will be backing up data that changes infrequently and over time will consume more space on the backup media. If I move to folder backup then I could have less partitions. I could also use incremental backups more - I tend to be wary of these in case one of the increments fails.[/COLOR]

Do you keep old backups or do you overwrite them with the new backup. If you overwrite then rsync is where it's at. > rsync -ru --delete /source /backuplocation is what I use. My scripts run every half hour and my backups are always current, with nothing extra. If I delete something from my working drive then when the script runs the --delete flag cleans up the backup as well. If you keep different backups then this doesn't help obviously.

I know you've been doing it long time a certain way just helping with options. I forget things so I had to automate my backups.

---

### Post by oldfred on 2014-01-14
I prefer to have every hard drive as bootable and put a copy of Ubuntu on every drive. So my SSD includes /home in / but  almost no data. My wife likes Picasa in .wine and it 2GB and most of my /home. My entire / is 11GB including /home. I link data partitions into every install.

I do not back up any system data as I will just reinstall. But I do backup configuration, new list of installed apps, so I can reinstall easily, /home excluding lots of cache & temporary files. Rsync works really well as you can specify what to backup easily and with cron, set frequency. I separately backup my data partitions.

I started with this simple script and then added to it.
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
      
 [URL="https://help.ubuntu.com/community/rsync"]
https://help.ubuntu.com/community/rsync[/URL]
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

      
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by technology4 on 2014-01-14
> Do you keep old backups or do you overwrite them with the new backup. If you overwrite then rsync is where it's at.

I keep them. My daily backup goes to backup\daily and weekly one to backup\weekly. At the end of the month the latest one goes to backup\monthly and then many of the oldest daily ones are deleted and sometimes the oldest weekly ones to free up disk space.

I've read about rsync and need to take the opportunity to re-think my tactics. Thank you for your ideas. Backing up so frequently does have an advantage if one makes a hash of editing a document or a programme and need to go back a short distance in time, rather than to the previous day (as is my case now). Provided the PC has enough guts to do the backup without slowing work down.

Thanks Jason

---

### Post by technology4 on 2014-01-14
Many thanks OldFred for your 2 postings.

Your suggestion of keeping system files on the same partition makes sense so the system stands a chance of booting should a partition or drive fail. 

I've seen others keep their data on HDD saying that SSD will wear out, but other posters say this is no longer true. Obviously, with SSD being more expensive the volume of data is a factor. 

Now to your second post. Great idea about making the SSD bootable with includes /home :)

I see from your comments that using rsync and folder backup and cron gives good flexibility. So back to the drawing board for me  ;) I shall read through all those links you've given - thank you.

> Please use Thread Tools above first post to close thread when/if answered completely.

Thanks guys. I shall close the thread as I have lots of ideas to work on. In the meantime I shall go for the 64MB SSD and work within that size. 

Alan

---

### Post by oldfred on 2014-01-14
With SSD you can make some setting changes to reduce writes. My SSD is now a two year old Housebrand Microcenter SSD which is not fast by current standards. 

I used ext4, but turned journal off. Supposedly some advantages to ext4 over ext2 which has no journal. Some now say with new drives to leave journal on. I also only use gpt partitioning for new drives, even though my old system is only BIOS.
       With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.

 You normally want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

I have 4GB of RAM and almost never use swap, so I leave swap on hard drive. But since it is never used the logic that says it will wear out SSD makes no sense. So I do not think it matters if on SSD with systems with 4GB of RAM or more.
Even on hard drive system should boot from SSD if hard drive fails, but give errors on mounting swap & my data partitions.

I changed from discard in fstab to using a cron task. Ubuntu 14.04 is planning a weekly cron task as default for SSDs. 

 Shows both discard & fstrim methods for trim, I used script and cron daily entry as shown here:
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

---

### Post by Bucky Ball on 2014-01-14
Invaluable information, oldfred. I'm about to buy an SSD and am testing 14.04 which I will be installing on it so I can try your instructions and the cron job first hand.

@technology4: You can't close a thread but you can help others by marking it as solved by using the instruction in my signature. Good luck. ;)

---

### Post by DuckHook on 2014-01-14
Never much to add to any oldfred posting, but:> Supposedly some advantages to ext4 over ext2 which has no journal...only one I'm aware of is trimming. ext2 does not support trimming whereas ext4 does. Ergo, no point in ext4 on USB drives because USB does not support trimming of any kind, whereas SATA does and it makes sense to use ext4 even if journalling is turned off.> After installing, change the fstab so that everything gets mounted with noatime...will work for 99% of users, but there are some for whom this will break app functionality. I use *mutt*, which relies on last access time to track read/unread mail etc. A better option for me is to use *relatime* which is almost as good as *noatime*. I believe that *relatime* is the default since 13.04, but am not sure about this. If so, then access timing no longer needs to be defined as it is set to best compromise setting already. However, no harm in making this setting explicit in fstab either.

Re: journalling

My understanding is that journalling not only speeds up file recovery, but also enhances file integrity. Therefore, still a real advantage over even a successful *fsck* which might repair an inode, but not recover from file corruption. Example: journalling will recover from a power outage in the midst of a write whereas *fsck* will not. I may be barking up the wrong tree here, but I've never lost a file since using journalled ext4 whereas I have lost files in ext2—almost always from power/network outtages.

I now have an SSD but keep journalling on because, to me, data integrity is more important than SSD longevity.

---

### Post by Jason_Gibson on 2014-01-14
> **oldfred said:**
> I changed from discard in fstab to using a cron task. Ubuntu 14.04 is planning a weekly cron task as default for SSDs. 

 Shows both discard & fstrim methods for trim, I used script and cron daily entry as shown here:
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

I hate to go off topic here but I have to ask. Does that need to be done in /etc/cron.daily/ or can I add it to cron with a simple ```
sudo crontab -e
``` I prefer to keep all of my scripts in a central location. Don't want to put something there if I don't have to otherwise I lose track of it.

---

### Post by oldfred on 2014-01-15
Thanks Duckhook for explanation of some of the settings I was not sure about. Recommended settings for SSDs have changed a lot. 

I do not know cron. All I did was put it into daily as suggested. Since I only backup /home regularly, I manually copy anything I edit in / into /home. Then a new clean install will let me restore /home and copy back the few files I have modified in /.

---

### Post by Jason_Gibson on 2014-01-15
Just now figured why not test it. Works fine. Ran my ramdisk backup script just fine and the backup was all owned by root (Run a backup every 10 mins of Minecraft which is loaded into the ramdisk.) May be a safer way of doing it instead of messing with the cron folders like that. Same reason they always say to edit personal crontab with **crontab -e.**

---

