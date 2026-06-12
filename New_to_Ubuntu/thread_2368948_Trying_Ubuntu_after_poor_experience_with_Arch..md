---
title: "Trying Ubuntu after poor experience with Arch."
date: 2017-08-17
forum: New to Ubuntu
---

### Post by elanachan on 2017-08-17
Hello there. I am on the search for a replacement for windows once windows 7 becomes outdated, and I intend on making this replacement the primary operating system for the new computer I'm building. I had started with Arch Linux due to my experience running command line level stuff with MS-DOS/command prompt/DOSbox, with the idea that some of the experience of working without a GUI would be transferable, and something I could probably handle. However, my new system's intended hardware use is much more complex than the traditional setup. And so I'm trying to move on, and to see if I might have any better luck with Ubuntu.

Before I grab the ISO and do a fresh install, I would like to address some of the difficulties I had setting up Arch, in hopes that someone here would be able to give me some guidance and give a yay or nay in regards to weather or not Ubuntu could fill the role. To give a bit of background for how far I got with the Arch installer, I was able to understand it well enough to do a basic install as a practice run on a USB stick, to the point of going from the basic terminal to my first taste of using cinnamon, while also having to deal with the situation of not having a wired LAN connection, which added some early complications to the install.

The complex setup I spoke of earlier is tied to the hardware that the new comp will be using, and it's intended use. Some of the hardware to be used is yet to be installed and will be added down the line as finances permit.


The drives on the machine are intended to be used in a series of arrays, and some of these arrays, depending on the optimal configuration, would require software RAID to work, as the onboard fakeRAID doesn't cover all of the SATA ports on the motherboard:

```
Drive count Type         Use
2x          M.2 SSD      Boot drive/operating system/system related programs such as: antivirus, java, peripheral software/drivers for printers/gaming mouse/keyboard, and Virtual Machines
4x          5400RPM HDD  Programs not related to the core system such as: Games, Web browsers, Office Suites, Photo editors, etc, and temporary media storage*
2x          SATA SSD     RAID 0 Scratch Disk*
8x          10TB HDD     Primary media storage**

*note: due to limitations of the motherboard, only two 5400RPM drives are able  to be controlled via fakeRAID, and the scratch disks would need to be setup with software RAID due to the SATA header only supporting AHCI.
**note: This array will be using a dedicated controller, separate from the motherboard.
```

Before my attempt at seeking help on the other forum ended, I was starting to learn about just how different the file system is from MS-DOS or windows, and it was suggested that with this kind of setup, the 5400RPM array would serve as both /home and /opt, having been given the impression that the directories were (somewhat) analogous to My Documents and Program Files respectively. I do not know if this is also true of Ubuntu or not. If it is, I would eventually want /home to be transfered to the 10TB array once I get the hardware installed.

In addition to using multiple RAID arrays in this setup, the system uses a UEFI BIOS, the two compounding togeather into a situation that prevented me from figuring out how to set up Arch on my own, ultimately leading me here to look for an alternative.

---

### Post by mastablasta on 2017-08-17
avoid fakeraid. use software raid (mdadm).

also avoid raid 0 (one drive is bad all is lost) - why do you need scratch disk?. antivirus in linux only checkes for windows viruses which can't spread on linux anyway.

as for /home and /opt you are partially right in your interpretation of similarities. however also you should know that linux can use symlinks. so you can later on link additional disk and they are all udner home. 

the 10 TB array. is it RAID? i hope it is not meant to be raid0. :)

anyway Ubuntu should be easier. just don't overcomplicate things. keep it simple.
programs should go on SSD. programs in linux share libraries so they are a lot smaller than on windows. i installed many and haven't passed the 20 Gb yet. basic OS install with XFCE is arorund 6 GB. i think games can go on HDD and you can symlink them, so they appear as if they are on SSD but actually they are on HD. but then what is the use of SSD if you habe the programs on slower drive? to boot faster? who needs to constantly reboot in linux anyway?

as for media and other data it doesn't really matter where those are (just avoid system folders for obvious permission reasons).

---

### Post by Impavidus on 2017-08-17
I never used Arch, but I think Ubuntu may be easier. It's meant to be Linux for human beings.

Don't overcomplicate things. Your boot drive/operating system/system related programs/programs not related to the core system all combined (but without the virtual machines) shouldn't be more than about 10 or 15 GB. Using 6 drives for that seems a bit overly complex to me. Games might take quite some space in /usr/share/games to store their data files (but their executables will be somewhere else). Using symlinks (or even bind mounts) it should be easy to move those data files elsewhere if you need.

Furthermore, the way files a spread over directories makes it hard to make such a distinction between OS-related and non-OS-related files. All software from the official sources that's not vital for booting or fixing the system (so that includes web browser, java, office suit, antivirus (if you want that), desktop manager) goes to /usr, with the executables in /usr/bin, data files in /usr/share, shared libraries in /usr/lib, et cetera. Files are mostly sorted by usage pattern, not software bundle, so it's very hard to distribute this in another way over your hard drives. /opt is mostly used by some third-party stuff, like software from Google (like Chrome).

---

### Post by elanachan on 2017-08-17
The four arrays were designed into the system with the purpose listed in the opening post before I started looking into the idea of using linux. Until this point I had been using windows exclusively, and I had been following the philosophy of keeping the OS drive to the OS, games and other programs on their own drive, and media files on their own drive (if possible) so as not to clutter up the first two. I was simply following and expanding on that by taking advantage of my computer's ability to run such a system with multiple arrays, adding redundancy to the OS drive, while expanding capacity and performance of the other two.

Following the same order as in the opening post, the array RAID types are to be as follows:
```

Drive count Type         Array type
2x          M.2 SSD      RAID 1
4x          5400RPM HDD  RAID 5/10 or 2x RAID 0 with 2x for backup
2x          SATA SSD     RAID 0
8x          10TB HDD     RAID 5/6/10/50/60 or ZFS
```
In regards to avoiding RAID 0, that would only be used as a scratch disk, or in the case of array #2, paired with a set of backup drives for recovery if the array goes down. 

Why do I need a scratch disk? I work with programs like photoshop to do post-processing work on very high resolution photographs, and I would prefer to have the temporary files held on the RAID 0 array instead of bogging down the rest of the system. The array designated for use as a scratch disk will only ever be holding temporary files.

Edit: @impavidus: With what you said about /usr, the intention would be to put that onto array #2 along with /opt.

---

### Post by Impavidus on 2017-08-17
If you put /usr on array #2, you'll have less than 2GB left to put on array #1. On most Ubuntu systems, /opt is rather empty.

The distinction between OS and other programs is not very clear-cut in Linux. The kernel, which includes drivers, would be considered OS by all. A web browser is an application separate from the OS. Java is definitely not a core component either; the OS doesn't need it, I don't have it installed because to me it would only be a security risk. Python is a different matter, as so many components of Ubuntu depend on python that it's practically unusable without. A desktop manager isn't vital; servers do without. But all of these things other than the kernel are just another program as far as the OS is concerned (whatever the OS is exactly). Many things in /usr would be considered part of the OS in the Windows world, but in the Linux world the distinction is not so clear. Do you consider the stuff you need for a console and a text editor the OS and everything else other programs?

Note that mirrors or RAID are no substitute for versioned backups. And opinions differ on the following, but I only keep backups of my documents. If my system breaks, I'll just reinstall – never happened though. Keeping the OS backups up-to-date is more work than an extra reinstall once every five years.

---

### Post by oldfred on 2017-08-17
I do not think they have yet fixed the Desktop installer to install with RAID. With 12.04 they had an alternative desktop installer that was somewhat like the server installer and supported RAID & LVM. The alternative installer was obsoleted and they said they later would add LVM & RAID to standard desktop. LVM is now supported with desktop and you can see RAID drives, but grub does not seem to install correctly with RAID from a desktop installer.

You probably have to do a server install and then add the desktop flavor of your choice.
[https://www.ubuntu.com/about/about-ubuntu/flavours](https://www.ubuntu.com/about/about-ubuntu/flavours)
This shows desktop packages:
 sudo apt-cache rdepends ubuntu-drivers-common | grep desktop


With UEFI you will need gpt partitioning. Otherwise do not know about server installs nor RAID.

I also started with DOS, but found it took a while to learn Linux. And even after years often have to refer to my notes as I did with Windows XP on commands. In beginning knew there was a way, just did not know command nor syntax/options required.

---

### Post by elanachan on 2017-08-17
[QUOTE=impavidus]If you put /usr on array #2, you'll have less than 2GB left to put on array #1. On most Ubuntu systems, /opt is rather empty.

The distinction between OS and other programs is not very clear-cut in  Linux. The kernel, which includes drivers, would be considered OS by  all. A web browser is an application separate from the OS. Java is  definitely not a core component either; the OS doesn't need it, I don't  have it installed because to me it would only be a security risk. Python  is a different matter, as so many components of Ubuntu depend on python  that it's practically unusable without. A desktop manager isn't vital;  servers do without. But all of these things other than the kernel are  just another program as far as the OS is concerned (whatever the OS is  exactly). Many things in /usr would be considered part of the OS in the  Windows world, but in the Linux world the distinction is not so clear.  Do you consider the stuff you need for a console and a text editor the  OS and everything else other programs?

Note that mirrors or RAID are no substitute for versioned backups. And  opinions differ on the following, but I only keep backups of my  documents. If my system breaks, I'll just reinstall &#8211; never happened  though. Keeping the OS backups up-to-date is more work than an extra  reinstall once every five years.[/QUOTE]

Using the windows analogy again, anything under the windows folder for the purposes of this discussion would be considered part of the OS, which includes notepad (in arch I used nano and vim), so yes, things related to the console and a simple text editor would be included with what I would put into the OS directory, would probably install python onto the OS drive, as it is a dependency for so many things. I need to be able to run java and flash for some things, but due to the security risks, I would separate it out from the main OS directory. I might still have it on the same physical drive, but my intention would be for it to reside outside the encryption locks in such a way that it is unable to effect anything in the root directory.

In regards to the RAID arrays; if the amount that would end up on the boot drive/array is so small, that would leave room for things like virtual copies of other OSs that may be more demanding of the drive space. Part of why I am trying to distribute things like this is keeping backup methods in mind. For array #1, little to no backup would be needed, as I could do a clean install if both drives go down. If I used the RAID 0 approach, for array #2, I would be setting up a method to allow the remaining two 5400RPM drives to serve as a backup for the array. For array #3, I have been considering the idea of using a NAS for backup, given that the total amount of space I could be working with for array #3 could be up to 40TB total.

---

### Post by elanachan on 2017-08-17
> **oldfred said:**
> I do not think they have yet fixed the Desktop installer to install with RAID. With 12.04 they had an alternative desktop installer that was somewhat like the server installer and supported RAID & LVM. The alternative installer was obsoleted and they said they later would add LVM & RAID to standard desktop. LVM is now supported with desktop and you can see RAID drives, but grub does not seem to install correctly with RAID from a desktop installer.

You probably have to do a server install and then add the desktop flavor of your choice.
[https://www.ubuntu.com/about/about-ubuntu/flavours](https://www.ubuntu.com/about/about-ubuntu/flavours)
This shows desktop packages:
 sudo apt-cache rdepends ubuntu-drivers-common | grep desktop


With UEFI you will need gpt partitioning. Otherwise do not know about server installs nor RAID.

I also started with DOS, but found it took a while to learn Linux. And even after years often have to refer to my notes as I did with Windows XP on commands. In beginning knew there was a way, just did not know command nor syntax/options required.

I wouldn't be against the idea of going with a server version of a distro, especially sense I intend on using the system as a part-time server for stuff like minecraft (java!), terraria, starbound and other smallish games that would have a small userbase.

I got the distinct impression using arch that the standard UEFI and gpt partitioning isn't the only step that you needed to take when deploying a RAID array as a boot device, something I found out first hand when I followed the main guide on the arch wiki, only to find out that the firmware wouldn't recognize the array as bootable. The impression was given that the EFI partition had to be held outside of the RAID array, while the filesystem partitions were to be held inside the array.

In regards to your last line "In beginning knew there was a way, just did not know command nor syntax/options required.", this is exactly how I felt that made me think I could handle arch in the first place, if I could learn the syntax and the various needed command lines to get stuff done, I could probably handle it...easier said than done when the required input lines aren't neatly laid out in an intuitive manner.

---

### Post by mastablasta on 2017-08-18
> **elanachan said:**
> 
In regards to the RAID arrays; if the amount that would end up on the boot drive/array is so small, that would leave room for things like virtual copies of other OSs that may be more demanding of the drive space. Part of why I am trying to distribute things like this is keeping backup methods in mind. For array #1, little to no backup would be needed, as I could do a clean install if both drives go down. If I used the RAID 0 approach, for array #2, I would be setting up a method to allow the remaining two 5400RPM drives to serve as a backup for the array. For array #3, I have been considering the idea of using a NAS for backup, given that the total amount of space I could be working with for array #3 could be up to 40TB total.

RAID is not a backup. a corrupted file, for example, will get copied to the other drive. and you may end up with a non functioning PC with a complicated raid arrays setup and no backup at hand.

RAID is meant for servers that need to be on 24/7, so that when one disk fails the server can chug along until the drive is replaced. but that kind of server still needs a backup. so rather than "RAIDing" you might be better off doing versioned backups to the other disk. 

i understand the scratch disk now, in that case RAID0 might improve performance. 

OS backup - just backup the configs and list of programs you have installed. the resintall is fast. if you plan on using wine, then backup the wine folder and you are done.

regarding raid installer, ther eis alos so called mini is. where you install the basic OS in CLI and then add other things to it (whatever you want). not sure if it has the raid option, but if i remember correctly it has same installer as server. or you could juts use the server image and not install the server stuff. 

there are various backup methods. but versioned backups usually offer incremental backups as well as delta backups. so the backup drive needs a bit more space than the original one. i would say at least 30% more. but the point is only the part of the file that changed gets backed up. 

you can use NAS for that or you can also set it up on local PC. NAS might be better since it is a separate unit (e.g. to protect data in case of malware or hack on main PC), but local drives might also be fine.

---

### Post by elanachan on 2017-08-18
Please look at that post more carefully, you will find that most of what you said regarding backups was already addressed.

Backup for arrays:
Array #1, RAID 1:
[QUOTE=elanachan]For array #1, little to no backup would be needed, as I could do a clean install if both drives go down.[/QUOTE]
[QUOTE=mastablasta]OS backup - just backup the configs and list of programs you have  installed. the resintall is fast. if you plan on using wine, then backup  the wine folder and you are done.[/QUOTE]

Array #2, IF RAID 0:
[QUOTE=elanachan]I would be setting up a method to allow the remaining two 5400RPM drives to serve as a backup for the array[/QUOTE]
Meaning two out of the total of four drives would serve as backup instead of being part of the array.


Array #4, Any RAID or ZFS option listed:
[QUOTE=elanachan]I have been considering the idea of using a NAS for backup, given that  the total amount of space I could be working with for array #3 could be  up to 40TB total.[/QUOTE]
[QUOTE=mastablasta]you can use NAS for that or you can also set it up on local PC. NAS  might be better since it is a separate unit (e.g. to protect data in  case of malware or hack on main PC), but local drives might also be  fine.[/QUOTE]

Is there any thing I missed? Array #3 doesn't need backups because it's only for temporary files anyway. Also, good to know about the 30% capacity increase on the backup size.

Edit: the solution for Array #4 could be extended to cover #2.

---

### Post by ClickXT on 2017-08-18
Good luck--that is indeed not a traditional setup and I can imagine the headache. Fortunately, this community is incredible.
...

Welcome to the Ubuntu forums.

---

### Post by mastablasta on 2017-08-21
definitelly explore the ZFS and BTRFS (at least on NAS option if not on the PC).

---

