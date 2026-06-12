---
title: "problem installing PRECISE in Win 7 laptop"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by mark allyn on 2012-12-02
Hello everyone,

I am trying to install 12.04.1 in a Win7 HP laptop.  I tried using a DVD with a ISO image.  However, when I get to the setup page where I have a choice of what I want to do, I get only TWO choices: install UBUNTU, or SOMETHING ELSE.  There is no option to install it alongside WINDOWS, which is really what I want to do.  I'm making a guess here, but could someone confirm whether or not this is because all the primary partitions on my hard drive are used up by WINDOWS 7.  If so, what should I do?

Thanks,
Mark Allyn

---

### Post by The Enigma on 2012-12-02
Hi, i'm having the same issue as you . please see my post here:

[http://ubuntuforums.org/showthread.php?t=2090523](http://ubuntuforums.org/showthread.php?t=2090523)

Maybe we can help each other out

---

### Post by mark allyn on 2012-12-02
Hello Enigma,
Hello Enigma,

Certainly if I can be of help, or this thread, by all means let it happen.

One option you might consider, and possibly have considered, is to use WUBI.EXE to install UBUNTU "inside" the Windows filesystem.  On booting, you get an option to load either Windows or Ubuntu.  It's not as clean as a separate partition, but it is very easy to do and does not require messing around with partitioning.  It has all the look and feel and functionality of a stand alone installation.

WUBI can be downloaded from the Ubuntu website under the guise of "Windows Installer".

Cheers,
Mark Allyn

---

### Post by Bartender on 2012-12-02
What's the exact model of the laptop?

Unfortunately for me, I've got to start being more careful about handing out installation advice because of UEFI and the upcoming Windows Secure Boot nonsense.  I'm OK with the old-school BIOS but don't have a handle on this new stuff.  

Do you have a thumb drive laying around?  If so, go ahead and boot from the 12.04 install disc again.  Go into "Try Ubuntu".  When you have the desktop up, plug in the USB thumb drive.  It should mount and appear in the upper-left hand corner as a "Device" when you click on "Home Folder" in the Launcher (the launcher is that vertical bar on the left-hand side of the screen).

Once you've checked to see that the thumb drive mounted, and noted what it's called, I need you to open the Dash.  Either click on the Super key on your keyboard (the one with the Windows icon, lower left hand corner) or go back to the Launcher and click on the Dash icon (the one on top).  Start typing in 

gparted

You'll probably only get to "gp" before Dash offers to start "GParted Partition Editor".  Click on that, wait for it to come up.  Once it gives you a picture of your partitions, go back to Dash, click on it, and start typing

screenshot

Again, you'll probably only get to "sc" before Dash offers to start "Screenshot".  Start that.  Choose "Select area to grab", then click "Take Screenshot" and draw a box around the GParted window.  When it asks where to save, save it to that thumbdrive.  

Then come on back here and attach that image to another post.  

Oh, yeah, one thing - the Screenshot app tends to give the screenshots goofy, long-winded names that may not work when attaching.  So rename the attachment something really simple, like "gp1.png" or what have you.

If we can see the partitions, we can tell you whether there are four primary partitions, and whether the PC uses UEFI or BIOS.

If all that was too complicated, just go back to Dash, and start typing 

terminal

Click on "Terminal" and copy/paste this command

```
sudo fdisk -l
```

Copy/paste the output to the forum.

I prefer the gparted screenshot, because it's easier for me to read and it definitely identifies EFI partitions, but the above works too.

---

### Post by monkeybrain2012 on 2012-12-02
I never used "install along side", when I dual booted briefly with XP (before getting rid of it  altogether) I manually shrinked the XP partition first and then installed Ubuntu on the space thus freed up.

---

### Post by oldfred on 2012-12-02
The issue is with Windows 7 almost all vendors have the drive configured to use all 4 primary partitions. Windows uses 2 directly, a hidden 100MB boot/repair and the main install. Then the Vendor uses 2 - one for the Vendor recovery which is just the image of the hard drive as when you purchased it and a smaller vendor Utilities which often is not worth much. 

Post partition layout as requested by Bartender, so we can offer suggestions.

If you know you have all 4 primary partitions you can read ahead. :)

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by The Enigma on 2012-12-03
Mark: i have no intention of installing ubuntu via WUBI, even though it is present on the install usb/disc image. i want a real install on a real partition that lives on an actual hdd. using WUBI would most likely cause minor performance issues, however slight, and besides that WUBI is also akin to running Ubuntu or another OS in a virtual machine. but thanks for the suggestion anyway.

Bartender: the exact model of my laptop is an ASUS G75VW, it's relatively new and was only released to market about midway thru this yr. I will get around to posted the screenshots later today, because shortly after you posted (but before i had a chance to read it just now), my 8 install crashed, and it seems to have botched both itself and the Server partitions. so i'm just going to wipe the hdd clean, reinstall 8 and Server 2012 exactly as i've described before. i'm 100% certain that the issue will come back once again. I'll also do the command you talked about and post the output of that as well.

However, i'm sure that i'm only using 3 out of 4 available primary partitions, since the 8 and Server installs would have their own partitions, which makes 2, and i'm also certain that they would also share a common boot partition, which makes 3, as would both Vista and 7 as well (if they were being installed in my case, which they're not). but i could be wrong. this time around i'll be careful to check in Disk Management during partitioning in 8 to see if i'll end up using 3 or 4 primary partitions. also, like i said, the 20 gigs allocated for Ubuntu was unformatted and in RAW mode, not sure if that makes a difference, and not sure whether the partition would be primary or not. I'm also certain that both 8 and Server 2012 utilize UEFI by default. but i'm confused about your mention of BIOS utilization. all PCs have a BIOS, i'm sure, so wouldnt they use the BIOS as well? if someone can clarify this, then thanks.

oldfred: my laptop came with a recovery partition, however i wiped the hdd clean when i first installed 8 in lat Oct/early Nov, and deleted the recovery as well. so that possibility of the recovery using up a primary partition is out in my case. the utilities/drivers installers were also rolled up into the recovery partition, in addition to being included on a separate dvd that was also included during purchase. however, the drivers are for 7, and obviously are no help in regards to drivers for Ubuntu. and they're outdated at that, some of them dont even work properly, if at all, on 8 (i tested). and thanks for the link.

Lastly, i would like to "chainload" (after installing Ubuntu), so that GRUB will hand off control to the Windows bootloader if i choose to load 8/Server, but yet still have all 3 OSes included in the same menu to be chosen from. once the Windows bootloader gets control, i would also like it to display its' own default options (boot normally, Safe Mode, choice between the 2 Windows OSes, etc), as if Ubuntu werent even present at all. is this scenario possible since 8/Server 2012 both use UEFI, and if so, can someone provide links with more info? on a side note, i'm also looking into using EasyBCD as an alternative to GRUB for choosing between the 3 OSes. anyone have any experience with this?

Well, thanks for the help!

---

### Post by mark allyn on 2012-12-03
Good morning, everyone.

Had to attend my 70th birthday party so couldn't respond quickly to all the folks who wrote in.

Bartender: The specific model of my laptop is HP ProBook 4525s.  I have to reread your extensive response, but it appears to do the job.  I need to read what everyone else has contributed.  I'm terrified of messing with my hard drive....

More later.

Thanks,
Mark

---

### Post by mark allyn on 2012-12-03
Hi Bartender:

I did the fdisk -l command on the laptop and got this:


administrator@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5147c726

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      616447      307200    7  HPFS/NTFS/exFAT
/dev/sda2          616448   589488127   294435840    7  HPFS/NTFS/exFAT
/dev/sda3       589490176   620947455    15728640    7  HPFS/NTFS/exFAT
/dev/sda4       620947456   625131519     2092032    c  W95 FAT32 (LBA)

Looks  like 4 partitions to me.

Any guidance much appreciated.

Mark

---

### Post by oldfred on 2012-12-03
Happy birthday mark allyn. :popcorn:

You will have to decide what partition to delete. See the links I posted above. Ofter you can backup or copy vendor utilities into the Windows partition as it is small to give you another primary partition. You still have to shrink Windows from inside Windows with its MMC tools to make enough space for Ubuntu. Reboot a couple of times to get Windows to see its new size. It usually runs chkdsk and may make other updates.

Then you make the last primary the extended partition and can put as many logicals in it that you want. Some make the vendor utilities & have said it stiil works as a logical, others do not really care. I also usually suggest making Windows a bit smaller and create a shared NTFS data partition for any data you may want in both systems. I had my Firefox & Thunderbird profiles & all photos for Picasa in my shared and used each application in Windows or Ubuntu to access the same data.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by mark allyn on 2012-12-03
Good afternoon, OldFred,
 
Thanks for the good wishes. Time does indeed fly...
 
Your discussion has been very helpful and I must thank you for the amount of effort you have put into this personal tutorial. I haven't yet read the materials at the URLs you have included and I need to do this.
 
The process looks complex, but evidently the starting point is to copy the recovery disk, which I will do onto a external hard drive. Besides copying the recovery disk, however, I wasn't clear on what you mean when you refer to "windows repair CD".
 
I have read and reread your second reply to this thread. In particular, the first paragraph--which makes it sound almost as if all I have to do is shrink the main windows partition:
 
> Ofter you can backup or copy vendor utilities into the Windows partition as it is small to give you another primary partition. You still have to shrink Windows from inside Windows with its MMC tools to make enough space for Ubuntu. Reboot a couple of times to get Windows to see its new size. It usually runs chkdsk and may make other updates.
 
If you wouldn't mind clarifying this, I'd be grateful.
 
Now, supposing I manage somehow to get (at least) two partitions available, what next. If I put the 12.04 DVD into the drive and bring up the installation pages, what will I need to do when I hit the page that asks me "What do you want to do?"
 
Thanks for helping me along on this.  I appreciate your patience.
 
Mark

---

### Post by oldfred on 2012-12-03
I have actually never used Windows 7. (Do not tell anyone as I have many posts on fixing Windows 7 somewhere in forum. :) )

You want to use the vendor tools to write the recovery partition not just back it up separately. But I only think that has value if you ever want to sell computer and buyer wants Windows. Better to backup your install after housecleaning, updating and shrinking, but before installing Ubuntu.

Many of my links are similar just slightly different ways to explain the same thing as one may make more sense than the other. Basically create Vendor recovery, full system backup, and a Windows repairCD or flash drive. Then start modifying system.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Also both the Vendor and Windows call it restore. 
The vendor restore is the image of the drive as purchased in lieu of providing the Install DVDS, requires several DVD. 
The Windows restore is just a repair and is tiny or about 256K, so easily fits on CD or smaller flash drive.

---

### Post by Bartender on 2012-12-03
> **oldfred said:**
> You want to use the vendor tools to write the recovery partition not just back it up separately. 

OOH OOH 

I may actually have something of merit to add

I have an HP 4520S, which is I'm sure is quite similar to mark's 4525S.  My 4520S did not come with a recovery disc utility.  You have to buy the discs from HP.  I don't know if this is just HP being jerks, or maybe they don't put recovery utilities on their "corporate" laptops?

I begrudgingly called HP and ordered discs.  The cost wasn't prohibitive; $12 or $15 if I recall.

So, marc, before you go any further, I'd suggest finding out for sure if you have to buy discs or not.  If I had HP's number handy I'd give it to you but I'm at work.  If it were me, I'd get the discs before doing anything more to this laptop, or at least get them headed your way.

I wish I could give you better guidance re: what to do about your laptop, but I'm woefully ignorant about how to deal with UEFI.  

Wait, did we figure out for sure whether you've got UEFI or BIOS?  That's one of the things I like about the gparted screenshot - it identifies an EFI partition as such.  I don't think 

```
sudo fdisk -l
``` 

tells you that.  Does it?

---

### Post by Pilot6 on 2012-12-03
This happens on some laptops.  You need to partition and install Ubuntu manually and then install grub from console.

---

### Post by oldfred on 2012-12-03
If gpt partitioned fdisk fails to tell much as it only sees the protective MBR.

Better to use parted.

       sudo parted /dev/sda unit s print
    
or download (in repository)  and use gdisk as that is the fdisk for gpt drives.

       sudo gdisk -l /dev/sda

---

### Post by mark allyn on 2012-12-03
Good afternoon, Bartender, OldFred,
 
As a matter of fact I have bios rev 15 installed.  I checked this early this morning.
 
I have been busily backing up my C drive onto a Toshiba external drive.  Plus cut a repair disk for Win 7 32 bit machine.  What fun....
 
You know, I take Enigma's point about not wanting to put Ubuntu "INSIDE" windows.  But, it works pretty darn well, as far as I can see.  So, I'm asking myself whether all this is worth it, or if it's just for the sport of it...rather like scaling Everest.
 
Cheers, 
Mark

---

### Post by mark allyn on 2012-12-04
Hello Bartender, OldFred, and Enigma,
 
Before I attemp to install 12.04 alongside Win 7, should I UNinstall the WUBI-installed version?  
 
Bartender:  I will follow your advice and get restoration disks from HP.
 
Regards, 
Mark Allyn

---

### Post by oldfred on 2012-12-04
Do you have any data in the wubi install you want to save?

If so you can follow these scripts to copy data. You still have to create partitions in advance.

       HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F]("https://wiki.ubuntu.com/WubiGuide#How")

    
If you have nothing to save, then deleting it first will make it easier to shrink Windows.

Not sure if you can make all the DVD images from your HP recovery and the Windows repairCD if you need the disks from HP. But never hurts to have additional ways to repair system. Full image backup is good as then you do not have to houseclean cruft & run all the updates again.

---

### Post by mark allyn on 2012-12-04
Good afternoon, OldFred,
 
Thanks for the response.  The answer is that I have a very small GTK+ program that I was  nurturing, but that's easily reconstructed.  The other files that would be destroyed that I value are a dowload of GTK-3.0 (obviously), GSL, DDD, and one or two others (automake, autoconfig, libtool, etc  --autotools generally).  So, based on your comments, I think best course is to uninstall the existing Wubi Ubuntu.
 
Your second comment re recovery is of considerable interest at the moment.  Yesterday I made a full disk image of my hard drive on an external hard drive.  I also created a repair disk.  HP does not appear to make CD copies of the RESTORE partition available for sale or download.  (Maybe Bartender can explain how he got them).  Moreover Sys 7 on my laptop does not have the ability as far as I can see to create the four (mythical?) DVD's with the restore parition files the way XP can.  So, I'm naturally concerned that the full disk image I created yesterday includes the restoration partition before I set about deleting it.  Looking at the contents of the disk image copy gives no clue as to whether the restore files are there or not....just a bunch of XML files with names that give no hint.
 
Can you verify whether or not I am equipped to restore the system if need be?
 
BTW, the one page partition discussion from Full Circle was very good.  Thanks.
 
Regards,
Mark

---

### Post by oldfred on 2012-12-04
I do not know any details on HP and how they handle DVDs for restore. Vendors all vary.
Most do offer for nominal charge the DVDs as hard drives do fail and users do not make the backup DVDs so they just about have to offer something.

---

### Post by mark allyn on 2012-12-05
Good evening, oldfred,
 
A follow on to the matter of getting HP recovery disks.  After quite a frustrating session on HP's on-line site I finally got the phone number to call for HP notebook (ProBook 4525s, Win 7 32-bit) and a helpful rep placed the order.  Arrive in 2-3 business days, price is $10.60.  The phone number is 1-800-888-0262. 
 
Thought you and others might like to know this.  
 
Regards,
Mark Allyn

---

### Post by Bartender on 2012-12-07
Sorry, mark, when I got home I shoulda dug up my paperwork and posted back with the HP phone #.

There's a possibility that installing from the discs will remove some of the partitions.  I'm not sure about that.  My Win7, non-UEFI 4520S has one big partition now after I reinstalled from the recovery discs that HP sent me.  But I don't remember how bad it was beforehand.  

Dangit, I'm lost again - did we establish that yours boots from an UEFI partition, rather than BIOS?

Anyway, what I'm getting at is that you may - or may not - get a partition or two back by reinstalling Windows from the recovery discs.  I just don't know for sure.  If it's UEFI you *might* wind up with as few as two partitions.  One for EFI and one for Windows.  

Have you signed up at the HP forums?  I've gotten help there.  The HP forums can be hit-or-miss.  There's less traffic than here, and I've seen questions that seemed completely valid go unanswered.  But I was on there not too long ago asking about a dc7800 desktop, and one of the senior guys stuck with me for several days until we'd resolved it.

---

### Post by oldfred on 2012-12-07
The fdisk showed 4 primary partitions, so it is BIOS/MBR.

If you have a full recovery set of DVDs you do not have to keep the recovery partition, most suggest backing up and copy the HP utilities into the main partition. On user said he copied back to a logical partition and the HP utilities still worked, others have not missed HP's utilities.

Use Windows to shrink the Windows partition to make more space, but not  to create partitions. You can partition in advance with gparted, partition during install with Something Else or use auto install which just installs a default / (root) & swap into the unallocated space. I usually suggest manual partitioning & adding /home and if dual booting with Windows a shared NTFS data partition. These all are logical partitions.

Several discussion and some with screen shots so you can see exactly what you will be doing.

       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

    
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by Bartender on 2012-12-07
Thanks, oldfred.  It takes a village -

mark, if you can hang tight until the HP recovery discs arrive, I'd suggest:

1) Back up anything you can't afford to lose.
2) Reinstall Windows from the recovery discs.  I'm cautiously optimistic that the recovery discs will do what they did on my 4520S - get rid of the non-essential partitions and leave you with one Windows partition, formatted as ntfs.
3) Make sure Windows works.
4) Use the Windows tools (find Administrative Tools>Computer Management>Disk Management) to Shrink the Volume.
5) Check again that Windows is working after shrinking the volume.
6) Install Ubuntu as a "genuine" dual-boot.

A variant of the above would be to use an Ubuntu LiveCD or GPartedLiveCd to create an ntfs primary partition first, then boot from the recovery discs.  The recovery discs *should* recognize only the ntfs partition, leaving the rest of the drive alone for Linux.

Everything changes with time, and I'm not entirely sure that what worked for me a year or more ago will work for you.  So the variant is offered as purely experimental!  I try to avoid offering ideas that may or may not work until I know that the recipient has options, and utter failure is not the end of the world.

---

