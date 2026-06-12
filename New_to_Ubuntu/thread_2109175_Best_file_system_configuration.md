---
title: "Best file system configuration"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by ooleyguy on 2013-01-26
I've been reading about file systems and partitions and such and have some questions.
 
I currently use Win7 64bit and am pissed off so much by it today that I am pulling the trigger and going 100% linux.
 
I have the following hard drives:
120 GB SSD in SATA0
250 GB 7200 RPM in SATA1
500 GB 7200 RPM in SATA2
1000 GB 7200 RPM in SATA3
DVD R/W in SATA 4
BluRay in SATA5
 
I have an AMD dual core 2800ghz socket AM3 processor on a Gigabyte MB with 8GB ram and a GeForce 550 Ti video card.
 
I want to know what file system would make my system run fastest.
I know I need at least a / and swap partition, but do I need a /boot and /home partition? And where do those partitions go? Where will programs get installed and where will pictures/video files/music files go? I currently have all my HUGE number of mp3 files (audiobooks and music) on my 1000 GB and most of the rest of the stuff on my 500 GB disk. I tell Windows to put My Documents, My Videos, etc on the 250 GB disk. Does the linux partiuoning system work somewhat the same?
 
I know thgat's a lot of questions, but i don't want to be resinstalling over and over. I want to do it once and be done with it for as long as possible.
 
One last thing: How vulnerable is Ubuntu to viruses?

---

### Post by oldfred on 2013-01-26
What's a virus? ok it is not totally resistant to a virus but most are designed for Windows and just will not work on Linux. Also the Linux file system requires permissions and ownership so any virus also has to get you to give specific permission to install, it cannot just install in background & run.

Best to backup Windows as many users find one app or game they cannot live without and come back asking how to reinstall Windows. It took me about 5 years before I stopped booting XP.
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
I like small system partitions of 25GB with all data in other partitions often on other drives. A bit more complex to set up than the default of just / (root) and swap for entire drive or the separate /home, but worth it if you have multiple drives.

I also subscribe to one drive at least one install so every drive is bootable, but I have Ubuntu on every drive except my old XP one.

       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

     
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one, so if already existing do not attempt another)
1 MB bios_grub no format (for BIOS boot not required for UEFI)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

    
       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

After you have absorbed some of this feel free to ask more questions. I have posted a lot of data and if not familiar with Linux will take a while. Oh, and there is no one best system. Even my own optimum system a year later is not so good and two years later I buy a new drive and have to reorganize. :)

---

### Post by ooleyguy on 2013-01-26
Thank you fo the info. I'll look through it all and see what I can make of it. Hopefully it is written in such a way as someone like me who was raised on DOS and progressed from MSDOS 3.0 and took every single upgrade step from that to Win7 (except that atrocious Windows Millennium) can understand it and draw some comparisons.

---

### Post by Sef on 2013-01-26
> I know thgat's a lot of questions, but i don't want to be resinstalling over and over. I want to do it once and be done with it for as long as possible.

Use 12.04 since it is supported for 5 years. As for the fastest file system, use the default ext4 as unless you do something really graphics intensive, it will not make much of a difference.

---

### Post by ooleyguy on 2013-01-26
Ok, I looked through all that and some new more specific questions arose. (I have the 12.04 DVD and the 12.04 Live USB)
 
I have Parted magic. Should I use it to make my partitions before the Ubuntu install?
 
1) Apparently the /home partion/directory holds user settings and such, not data, correct?
 
2) If I am correct on number 1, where does data like MP3s, AVIs, DOCs, TXT, etc. go?
 
3) Is there a reason to make a disc into GPT system instead of MBR (speed advantages maybe)?
 
4) In regards to Knoppix, that's just another distro of linux, right? And you are just using it to make sure you have access to data on drives if the main OS gets hosed?
 
5) How does that work on a system like Ubuntu, where Grub2 is used?
 
6) Basically the same question based on that Knoppix doc where they suggest that a GRUB partition be made on each physical disk. How does that work when Ubuntu uses GRUB2?
 
7) Lemme tell you exactly how I want my system and then you point me in the right direction:
 
I want my SSD to contain executable programs for speed. I like the /home partition idea with user settings. I want my programs to have easy access to all the various data files (music, video, graphics, document, etc.) that will and should be located on my larger, slower drives. I would also like to put some programs like word processor type programs that don't require alot of power and speed on another drive besides my SSD.
 
Hopefully answers to 1-6 will andwer number 7. Hopefully, I am explaining things in such a way as you can see what my end goals are. I don't always explain things in such a way that people unfamiliar with how my thought processes occur can understand. Sorry if that is the case.

---

### Post by sandyd on 2013-01-26
> **ooleyguy said:**
> Ok, I looked through all that and some new more specific questions arose. (I have the 12.04 DVD and the 12.04 Live USB)
 
I have Parted magic. Should I use it to make my partitions before the Ubuntu install?
**Ubuntu has an partitioning tool called Gparted, included by default on the Livecd ;)**
 
1) Apparently the /home partion/directory holds user settings and such, not data, correct?

**Depends on your configuration. It is a choice. See below**
 
2) If I am correct on number 1, where does data like MP3s, AVIs, DOCs, TXT, etc. go?
[B]In your home directory, which is in your /home partition. For example, if your username is ooleguy, they would be in /home/ooleguy. The MP3s, AVIs, Docs would reside in folders such as /home/ooleguy/Documents, /home/ooleguy/Videos. Of course, you can place it in whatever folder you want (the folders for Video/Music/Documents are already precreated).

However, you can put your data elsewhere (on another partition) as well - it is your decision. I just read over your full post again - in the setup you want, the /home partition would only contain settings/etc, and files like mp3s, avis, docs, would go on another partition. Just for compatability (since Ubuntu by default sees ~/Documents as your document folder), you can even create symlinks to make Documents, Music, Videos, and the other data folders in your home directory to link to another folder on another partition
[/B]

 
3) Is there a reason to make a disc into GPT system instead of MBR (speed advantages maybe)?
**GPT has the advantage of not having a limit of 4 primary partitions (or 3 primary and 1 extended)**
 
7) Lemme tell you exactly how I want my system and then you point me in the right direction:
 
I want my SSD to contain executable programs for speed. I like the /home partition idea with user settings. I want my programs to have easy access to all the various data files (music, video, graphics, document, etc.) that will and should be located on my larger, slower drives. I would also like to put some programs like word processor type programs that don't require alot of power and speed on another drive besides my SSD.

**This, I am not sure about. You can use your SSD for / (root partition), but as far as I know, there is not a way of seperating applications - all the executables are in single folders (i.e. /usr/bin /usr/local/bin /usr/sbin .etc .etc)**
 
Hopefully answers to 1-6 will andwer number 7. Hopefully, I am explaining things in such a way as you can see what my end goals are. I don't always explain things in such a way that people unfamiliar with how my thought processes occur can understand. Sorry if that is the case.
..

---

### Post by ooleyguy on 2013-01-26
Ahh, so programs go in the /usr directory. Is that the default directory, or can I specify a different /usr directory at installation time?

---

### Post by Cheesemill on 2013-01-27
Programs go wherever the developer wants them too, you don't really have a say in where to install programs (there is no equivalent of C:\Program Files\). Also a programs files are spread around the drive depending on their purpose, main binaries live in /usr/bin or /usr/sbin, documentation goes in /usr/share/docs, shared program libraries live in /usr/lib etc...

One thing you haven't mentioned is whether Ubuntu is going to be your only OS or whether you are setting up a dual-boot. This will affect how you should set up your partitions.

---

### Post by GordThompson on 2013-01-27
> **Cheesemill said:**
> One thing you haven't mentioned is whether Ubuntu is going to be your only OS or whether you are setting up a dual-boot. This will affect how you should set up your partitions.
The OP said...

> **ooleyguy said:**
> I currently use Win7 64bit and am pissed off so much by it today that I am pulling the trigger and going 100% linux.
...which sounds like they intend to get rid of Windows completely. If so, then I simply offer my comment from another recent thread:

> **GordThompson said:**
> If someone has a working, legal copy of Windows and they are not starved for disk space then IMO completely wiping out Windows to install Ubuntu is foolish. How many times do we see people asking for help here because their Ubuntu install didn't go quite right, or something else happened to trash their network connectivity, and the only way they can fix it is by downloading stuff via their Windows network connection.

UPDATE: In this case my comment may have come too late...

[http://ubuntuforums.org/showthread.php?t=2109277](http://ubuntuforums.org/showthread.php?t=2109277)

.

---

### Post by ooleyguy on 2013-01-27
I'm going completely Ubuntu (or another distro if Ubuntu can't do it for me).

I had it installed in dual-boot mode for a few weeks and got all my drivers installed ok and all the software was doing what I wanted it to and yesterday Windows just started having fits and I give up on them. I have a licensed copy of XP that I'll put in a virtual box to play the one game that I need windows for, but I haven't played that game in a while, so apparently I don't need it too badly.

---

### Post by Cheesemill on 2013-01-27
In that case I would recommend not using NTFS as the filesystem on any of your storage drives.

Sometimes when there is an issue with an NTFS partition the only way you can fix it is from Windows. If you don't have Windows then you can end up in a situation where you drive becomes unreadable and you have no way to recover it.

Unfortunately there is no way to convert a drive from NTFS to ext4 format, you will need to back up all of your data, then reformat the drive before copying your data back again.

---

### Post by ooleyguy on 2013-01-27
Thanks all for all your help. I think this is closed. I have it running fairly well with a few glitches that hopefully will get sorted soon enough.

---

