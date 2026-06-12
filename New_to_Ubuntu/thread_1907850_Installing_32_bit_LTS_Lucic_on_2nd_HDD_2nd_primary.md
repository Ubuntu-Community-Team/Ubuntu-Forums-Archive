---
title: "Installing 32 bit LTS Lucic on 2nd HDD 2nd primary partition"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by aka-John99 on 2012-01-12
I am new to this and have two related enquiries,I will start a second thread about the 64 bit question but the two are related so I will mention them both here.

   1.** this question & thread**: installing 32 bit LTS Lucid on 2nd HDD 2nd primary partition
   2. thread to follow: Installing Lucid 64 bit over Lucid 32 bit on laptop partition

_**Question**_
How do I go about installing 32 Bit Lucid to a 2nd HDD on a Windows XP desktop, installing after a primary partition for Wiindows use.


_**My System & thoughts**_

I must say immediately thanks for any help.
It is a lot easier for me to ask a question of someone who already has aquired that knowledge than trying to slowly look up all the information myself, only to then miss out on something that in hindsight is obvious.


Rather  rambling  but it gives you an idea of my current intentions and my reasoning, some of which may of course be flawed.

This is an older pc with a failing main hdd, with Windows XP, which I wish to keep, but a second newish drive available for installing Ubuntu on, and I would prefer to install in a second partition on that drive. I am trying to not spend money on it, but have been swapping some components from other systems.


[LIST]
[*] HDD:   The Windows drive is failing as evidenced by s.m.a.r.t reports. It is a 32bit FAT 160GB drive
[*]2nd HDD: The one I have not yet installed 500GB (need cable yet in order to install it)
[*]USB1:  is available, but currently only USB1 so not only unable to boot from USB sticks, they are too slow for most purposes. External HDD available but limited currently by USB1. (Version One)
[*]CD:     It does have a CD.RW drive, but is rather unreliable in booting Ubuntu from that.
[*]RAM:  The RAM is max allowable 1GB, but some of that is used on integrated graphics
[*]CPU:  AMD Athlon single core
[*]BIOS:  This will allow boot from 2nd internal HDD, it will not boot from USB.
[/LIST]
 
I have already

[LIST]
[*]made and integrity checked Lucid CDs for 32 bit desktop, 
( and 64 bit desktop and alternative install 64 bit)
[*] installed Lucid on a laptop (see other question)
[*] by the time I come to try this I will have the 2nd hdd installed, and if necessary formatted and partitioned
[/LIST]
 Ubuntu Install Easy Options Dismissed
I could install in 1st primary partition, of prospective 2nd hdd using Desktop Live CD, but would prefer not to do that, I think any Windows install would normally have to be in 1st primary partition.
I could install alongside current Window OS but that is a non starter
- space is going to be limited, and I have loads elsewhere
- the hdd may well fail soon

Me
Newbie to Linux. Have forgotten a lot about Unix, DOS, & Cobol, even Basic at one line per punched card! so not totally new to computers. Would currently prefer to avoid unnecessary use of CLI, as will be too slow looking up and trying to remember all the required commands and their syntax.
I do not know anything much about modern partitioning & file systems, but note Lucid is installed on Ext4.
I certainly do intend to learn about using the terminal emulator, and have already played around on it.
 

[B][U]
Windows[/U][/B]
I wish to keep Windows. I will leave it where it is for now. Curently it is backed up using Norton (Norton Ghost 14 ). Using NG14 on a system with grub is apparently a known issue, (I think NG14 recovery may rewrite the MBR).
 I may have to reconsider backup options,presumably I can discover methods of making and restoring disk images. It has some sort of hidden partition recovery system, but that looses any changes and additions I have made. Also is no good if/when HDD fails.
(Kosher OEM install on original machine, so at some stage I may be able to plead with MS for installing on a replacement drive or partition as a repair solution - a replacement Windows OS is pointless on a machine of this age/value)    
At present if no other option, unpluging any additional drive and using the recovery cd the current HDD can be restored to a factory style default. Then programs and personal documents etc may be restored from whatever backups I have. But it is easier using NG14. Once Ubuntu is installed and working I can rethink strategies.


(In a separate thread to follow

Next q re: 

Lucid 64 bit over Lucid 32 bit on laptop partition
This is a recent laptop, Windows 7 installed on primary MBR NTFS
Single internal 750GB hdd,  USB connectors, and internal CD/DRD rewriter
Lucid 32 bit installed and working on 2nd partition
)  

oops
Typo in title says Lucic not Lucid !
Appears title may not be edited by poster.

---

### Post by oldfred on 2012-01-12
Any install to a second drive or external drive should be partitioned in advance and use manual install or Something else to choose which partitions to use for what.

Install to external drive 11.04.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)
B

My standard suggestion for partitioning, but that can vary a lot depending on what you what or need.
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by lechien73 on 2012-01-12
Am I understanding correctly that you wish to install Windows to the 2nd hard disk, and have that co-exist with Ubuntu?

If so, then install Windows first, either customising the partitioning scheme on installation so that not all of the hard disk is used, or having pre-partitioned in advance.

Then, boot the LiveCD and choose to install Ubuntu. Again, you can choose your partitioning scheme on the 2nd hard disk, so that Ubuntu takes the remaining space.

When Ubuntu asks you to confirm the location where GRUB should be installed, then  check the advanced options to make sure that it installs to the boot sector of the second hard disk, and not the first.

---

### Post by Double.J on 2012-01-12
Hi there! I think I got it all, but of course, if I missed something, shout!

Right I think the first thing to address is this failing drive - if it looks as though it's on it's way out, i think it's really important that the first thing to do is back it up; everything - if there's anythin on there you don't have a copy of consider it at risk, drives can go 2 hours or 2 years after they first deisplay issues.. or they can go without any warning what so ever, and depending on the fault it may be impossible to recover anything from it.

as for installing it's a fair bit easier to install XP first, and since you're HDD's at risk I definately suggest doing that.

I'd say get the live cd, which it sounds like you have and boot it up, clicking on "try" not "install". On the Desktop is a program called Gparted - load this up and select your 500GB device from the drop down list on the top right - not the 160GB of XP.

In order from left to right, I'd advise 40GB free space for XP, then a 30GB Extended partition for Ubuntu then the rest of the drive used as an NTFS formatted primary partition, then restart and run the installers

XP first - tell it to use the free space on the disk - the first 40GB it'll format it as NTFS, and the computer will now auto boot to XP - don't install updates or move data yet, if you make a mistake and have to re-install you'll kick yourself! If you get a warning about primary partitions, you've selected the logical partition, create a 40GB primary filesystem.

Ubuntu second - run the installer, and this time click install :) when you get to the install options you don't want "install along side" or "use whole drive" you want "use free space" which will be in the logical partition. 

Advanced mode is for adding ubuntu partitions such as /home - but you don't need this if you're going to put all your data on  a shared partition.

finish the installer and restart you should now get a menu that let's you choose either. You will now be dual booting! start with XP - there's mosre to do post-install so more room for errors, get your anti virus, updates user accounts, blah blah windowsy blah set up so you know your not about to mess it up and need to reinstall/repair install!

Then set up ubuntu how you want it - any drivers you need, add the ntfsprogs package, then copy all your data into the shared partition This should leave you with 40GB windows 30GB linux and over 400GB data storage that Both OS can read and write to - anything stored in linux, windows can't "see".

Hope that helps a bit, as I say first things first - back up all your data :) If you have any questions, please just ask!

All the best!

---

### Post by aka-John99 on 2012-01-12
Thanks for the replies. The failing disk is backed up, but relies on a method that either conflicts with Ubuntu, or relies on a partition within that disk!!

I may not initially try to transfer Windows  to use the 2nd hdd, but will make a space there for it. I am going to need permission from MS so I comply with EULA. In any event I still need a power cable for the new hdd and to fit it so I will not be doing anything till the weekend. Meanwhile I will read the replies and the linked articles that have been provided.

I will post back in due course with a progress report and  any further questions, 

John

---

