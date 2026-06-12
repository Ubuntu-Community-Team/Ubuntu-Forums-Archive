---
title: "Advice re configuring for Win 7 &amp; Ubuntu dual boot"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by flyingsolo on 2012-02-04
I had to get a windows computer for running a certain remote application at work but would rather run Ubuntu on it when I'm not using the work app.
It came with a large 2TB drive that has 3 existing partitions:
14 GB unnamed
WIN7(C: ) partition of 745GB
and DATA (D: ) of 1.1TB

So, my goal is to shrink the WIN7 partition (but not too much!), install Ubuntu with separate /home.
I'd like, if possible, for both OS's to share data files (music, pix, video, docs) if that's possible. (there is a slightly [older Lifehacker tut]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") that suggests this can be done.

Suggestions please or links to favourite existing tutorials. Thanks!

---

### Post by westie457 on 2012-02-04
Try it this way.


Boot into Windows and defrag the hard drive twice using the Windows Defrag tool.

Then open the MMC console to look at the partitions already there. If you only see two partitions in this window no need to worry. The one you cannot see is probably the recovery partition.

Select the C:\ drive and right-click > shrink this partition. Take it down as far as Windows will allow. Wait for this to finish.
Next take some space from the Data partition by moving on end to the right - 200 Gigs will be more than enough - leave all of this new space unformatted.


The above is the easy part. How you deal with the partitioning for the Ubuntu/Linux install depends on wether the Hard drive has a normal MBR partition table or a GPT partition table. If you do not know or are unsure wait for further guidance. I personally do not know if there are limits on the number of partitions with a GPT table so I am not offering further advice. 

The advice already given will clear the ground and should not break anything.

Hope this helps.

---

### Post by joetait on 2012-02-04
Well Ubuntu can use NTFS, so if you install it in a small separate partition you could just use that and then mount it. This could be done manually, as in [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows).
Alternatively you can edit the fstab file (/etc/stab) so that it loads at boot.

Alternatively, there is software available for windows to read ext4, so you can install that and make use your /home directory as your main place of storage. Searching something like "accessing ext4 in Windows" or anything like that should throw up a lot of results. I think this would be better if you plan on using windows a minimal amount.

Edit: Sorry, didn't see the first question, guess answering the second one first isn't too useful!

---

### Post by oldfred on 2012-02-04
gpt restricts you to 128 partitions.:)

Although with MBR(msdos) you can have virtually unlimited logical partitions in the extended partition but most systems run of of letters and stop at 16 or 32. So you can create them but then probably not use them.

You will only have gpt with Windows 64 bit if you are booting with UEFI not BIOS. Most new computers now have UEFI, but still can boot in BIOS mode with MBR(msdos) partitioning.

Most new Windows systems use all four primary partitions as they have hidden boot/repair and/or vendor recovery partitions. Then you have to decide which partition to delete. 

Make good backups & a Windows repairCD.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by flyingsolo on 2012-02-04
Thanks westie. My 1st post included the existing 3 partitions. I think the first, unnamed, small partition is something sacred to windows that LH warns to leave alone.  The computer is very new, so not at all cluttered with programs or data--I'll defrag but I don't expect there's much disorganization anyway.

---

### Post by oldfred on 2012-02-04
If you have room for one more primary partition as the extended partition, then you can make all the Linux partitions for Ubuntu as logical partitions inside that extended partition.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

I prefer smaller system partitions and larger shared or data partition(s).

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by kherring7383 on 2012-02-04
Dual booting is a good idea, the only drawback is not being able to use both operating systems at the same time. When you want to use Win7, you have reboot to get to it.

If you don't mind not having the Aero effects in Windows 7, you may consider installing Virtualbox and install Win7 in a virtual machine. During the setup, you can choose how much drive space and  memory to create for it. 

Like you, I too need Win7 for certain job related tasks so on My Mint 12 box, I have Virtualbox installed and can run Win7 in full screen or a smaller window but still have full use of Mint.

If you have a second display you can have Win7 on one display and Ubuntu on the other and be able to switch back and forth without having to reboot.

See my attached png file

---

### Post by flyingsolo on 2012-02-10
I was too busy to stay on top of these posts but back now. Thanks for advice. I'm still looking for advice on management of the existing partitions which are:
1.  14.18 GB Healthy (Primary Partition)
2.  WIN7 (C: ) 745 GB NTFS Healthy (System, Boot, Page File, Active, Crash Dump, Primary Partition)
3.  DATA (D: ) 1103 GB NTFS Healthy (Primary Partition)

I've listed them with all the info given in Windows Disk Management. So Windows program is installed on a partition separate from its data which I suppose is similar to Ubuntu / and /home.
I was going to shrink the Win7 partition to ~100 GB and shrink its Data partition to ~500 GB, allowing for Ubuntu to have access to ~1.4 TB leftover. Do I need to get the Win 7 and its DATA partitions contiguous so that Ubuntu's / and /home are contiguous? (am I being clear enough?)
I think I recall in the past running into issues of not being able to create enough partitions for some reason or is that ancient history? (it's been awhile since doing a new install as my old U. has been working flawlessly for years but is on a very old, slow computer)
Thanks again.

---

### Post by oldfred on 2012-02-10
You can only have one extended partition, so if you have used 3, then you do have to move d: to be next to c:. That has a bit more risk as any system shutdown will cause issues, so have good backups. You will also need to run chkdsk on the d: after moving it.

How old is computer. Some very old one's could only boot from the first 137GB of a drive.

---

### Post by flyingsolo on 2012-02-10
HI Oldfred--the current computer I'm asking about is brand new & it's the one I'm reconfiguring.  The 'old' one I referred to is a generic Dell XP desktop that the kids used in high school, probably dating from 2000 maybe.
For the current computer that has 3 partitions as listed above, that's just the way it came so I had no hand in the decisions about partition number or size.

---

### Post by oldfred on 2012-02-10
Are you sure you do not have four partitions? Windows 7 installs have a 100MB boot/repair partition that is normally hidden. Shink partitions with Windows, but use gparted to create new partitions or else Windows may convert to dynamic which does not work with Linux.

Post this from liveCD, you can copy & paste into a terminal & copy output back:
```

sudo fdisk -lu 
```

---

### Post by Learning Linux 2011 on 2012-02-11
I would recommend shrinking one of the partitions (either the Windows 7 or the Data, doesn't matter)
Then create 2 new partitions in the new free space.  Install Ubuntu in one of the partitions using the ext4 file system.  The other new partition should probably be FAT32, which will be limited to 32GB, but that is the only type that both Windows and Ubuntu can access.  I'm not sure if you can install /home to FAT32 though.
You could also buy a new hard drive and install Ubuntu on that.  Then you could have multiple partitions with little worry.

---

### Post by flyingsolo on 2012-02-11
I ran fdisk -lu and it returns:
> Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf9ae2f37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    29747199    14872576   1b  Hidden W95 FAT32
/dev/sda2   *    29747200  1592555519   781404160    7  HPFS/NTFS/exFAT
/dev/sda3      1592555520  3907026943  1157235712    7  HPFS/NTFS/exFAT


So, I think it is just 3 partitions as I said. Also, when I try to shrink the Win7 partition, it will only allow it to go down to ~365 GB in spite of defragging & this being essentially a new, barely used computer, so not many files at all are present to be spread across the disk. I figured I should be able to get Windows into a smaller partition than that.
And for Learning LInux, I thought about getting the second drive & going that way but the disk that came on it is 2TB which is plenty for my limited Windows needs; I just want to push Windows into a smaller corner, maybe total 500 GB for program & data and use the leftover 1.5 TB for Ubuntu.

---

### Post by oldfred on 2012-02-11
This was for Vista but I think the same issues apply for 7.

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)

Best to also have backups &  recovery disks or USB to repair Windows.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Mark Phelps on 2012-02-11
> **flyingsolo said:**
> ... it will only allow it to go down to ~365 GB in spite of defragging ...

While you certainly CAN force it to be shrunk a LOT more, using Linux apps, I strongly recommend AGAINST doing that.

Instead, suggest the following:
1) Download the FREE disk image for Partition Wizard (MS Window app)
2) Burn that image to a CD
3) Boot from CD -- and use Partition Wizard to shrink Win7.  It's a windows app, so you won't risk damaging it by using this.

You can also use Partition Wizard to move other partitions around to end up with all your free space on the "right".

I would check one more thing ...

You mentioned about Windows having the OS in one partition and data in another.  It's not configured by default to do that.  I think if you check, you will find that the Program Files directory is in the same partition as the Win7 OS files.

If that is indeed the case, then instead of creating a HUGE Linux partition, I would create one no bigger than 20GB and use the existing NTFS data partition for both Win7 and Ubuntu.

---

### Post by flyingsolo on 2012-05-03
Pardon the long interval between posts ('life' distracted me from this)

I've used Partition Wizard to shrink the C:WIN7 partition and expanded the D: DATA(NTFS) partition which has left an 'Unallocated' space between C: & D: where I intend to put Ubuntu (12.04, now)
I like the idea of Windows, Ubuntu sharing the large data partition but need advice on formatting & installing the Ubuntu to the unallocated space.
Summary of current drive space allocations, in order: Recovery (NTFS), C:WIN7(NTFS), Unallocated, D: DATA(NTFS)

Besides advice/reassurance before proceeding with Ubuntu install, one extra newbie question. When Windows or Ubuntu install new programs, do they 'reside' with the OS's in their partitions (that's what I thought) or do they go onto the DATA partition?

Continued thanks. I hope to get this right once & for all.

---

### Post by oldfred on 2012-05-03
I have not used Windows 7, but the older verions made it real difficult to install programs anywhere else than c:. Many programs did not even work back then as internally they were set to work only from c:.

Ubuntu also installs all programs in / (but you will find they are a lot smaller. I have a lot of applications and only use about 7GB. But I think the largest apps are games in Windows and there are not so many large games in Linux.

I use both a Linux data partition and have my older NTFS shared data partition that I used a lot before when booting XP. I have my Firefox & Thunderbird profiles in the NTFS partition so I have all the same email & bookmarks in both (actually many Ubuntus) systems.

If are are going to put all data into your NTFS data partition you do not have to have a large / (root) or separate /home, but since you have lots of hard drive space you still can be generous on space.

My standard suggestion, you can be a bit larger, but any very large system partition both Windows & Linux slightly reduces speed as hard drive has to search over larger areas.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by flyingsolo on 2012-05-03
Thanks Oldfred. I'm reading your comments carefully but maybe just need clarification. You suggest /home in addition to / and swap. Is not /home the Ubuntu 'data' location in which case, then the data stored there is not accessible to Win7? As I understand, Win7 will store to the D: DATA partition which can be accessed by Ubuntu but will Ubuntu store data (files, folders etc) to /home or the D: DATA (NTFS) space?
Hopefully, I'm being sufficiently clear or am I muddled regarding where data is stored by each? (to me, 'data' means all the folders & contents such as docs, photos, music, video)
Thanks.

---

### Post by Bartender on 2012-05-03
Ubuntu (and all other Linux distros AFAIK) will create a Home folder.  That Home folder will have folders within it for Music, Documents, Videos, etc.    

If you set things up before installation so that the installer puts the Home folder in a separate partition as described by Oldfred, you wouldn't see a difference during your daily operations.  None that I can think of anyway.  Home will act just like it would if you had _not_ created a separate partition.  The advantage to creating a separate partition for Home comes about when you want to move on to a new version of the OS.

Lots of applications that create personal data (whether it be docs, music, video, etc.) are set up by default to look for Home when you use them.  In other words, if you create a document in LibreOffice, it will by default save to Documents in your Home folder.  Banshee, Rhythmbox, RipperX, etc. will all look for your Music folder, or create their own folders within Home.

You can tweak these programs to output to other folders, but the defaults are gonna be Home, or folders within Home.

In your case, you might find it easier to let these programs output to Home, then when you're done you could manually move the data to the shared NTFS partition.  Or you might choose to go into the settings of each app that creates personal data and re-direct their output to your NTFS data folder.  Or it might end up being a combination of both - you might want some apps sending their data to Home, and others sending their data to the NTFS data folder.

Yeah, I know, you're just looking for some simple answers.  Choice is good unless it makes your head hurt.

So, Reader's Digest:
- Make a separate /home **partition**, or don't.  Ubuntu will create a Home **folder** either way.  The separate /home partition is often seen as an advantage when upgrading or starting over, but if you have an external storage device you don't NEED a separate /home partition.
- Ubuntu is smart about NTFS.  It can read/write to an NTFS data partition that you create for shared data.  Windows is stupid about any partition that's not formatted for Windows.
- Any data that's sent to Ubuntu's Home folder can be copied or moved to the NTFS shared folder, and back again to Ubuntu's Home, so don't worry about making some horrific error during installation.

---

### Post by flyingsolo on 2012-05-03
Thanks bartender...I may be approaching clarity! Since mainly I'll use this computer as Ubuntu but need to access Windows occasionally for work, I think I'll drastically downsize the D: DATA (NTFS) partition that Windows needs, thereby creating a much larger unallocated space into which I'll put Ubuntu with /, swap, and /home, of which /home will be the lion's share.
(as I had originally said, this is a large 2T internal drive so space is generous; I'm thinking C: ~75GB, D: ~100GB, unallocated will be the rest (~1.7TB) which will be divided into / of ~50GB, a small swap, and a rather large (~1.6TB) /home) 
Critique welcome. Of course large internal drives put large volumes of data at risk of spontaneous loss from drive failure, so back up data as usual externally.
Thanks.

---

### Post by oldfred on 2012-05-03
Good comments on /home from bartender on why or why not a /home partition.

But /home partition cannot be NTFS as it is a Linux system folder or partition. It has to support permissions & ownership which NTFS does not.

So you may want to keep your NTFS d: or data partition larger?

---

### Post by flyingsolo on 2012-05-03
Thanks again. Perhaps maybe larger D: NTFS but I really don't anticipate using the windows except for a very defined work circumstance (required proprietary software written only for Windows) so the data I might be storing to it will be low volume. And, yes, I was aware that /home would not be NTFS.
Thanks to both of you for quick turnaround on good advice!

---

