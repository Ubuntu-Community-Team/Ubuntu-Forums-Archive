---
title: "Beginner lost with Ubuntu"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by Ant01 on 2013-04-19
I'm trying to get the hang of Ubuntu again as I used it over 2 years ago but am feeling very frustrated and lost. I made 2 post but haven't resolved any yet and I have not sure if there are tutorials that can help me;
[Im back using Ubuntu and am lost]("http://ubuntuforums.org/showthread.php?t=2135724&p=12604223#post12604223")
[Unmounting External hard drive]("http://ubuntuforums.org/showthread.php?t=2136066&p=12605688#post12605688")

I am also not sure which version of Ubuntu to use. I had loaded version 12.04 but then was having problem with my external hard dive so I loaded 12.1 but still the problem hasn't been resolved.

The 2 main problems I'm having is ;
[LIST]
[*]sharing my external hard drive (NFTS) 
[*]booting up with the external hard drive
[*]
[/LIST]
When I try booting up with the external hard dive plugged in, I get a Grub error saying its not reading .....  
I then have to boot up and then plug in the external hard drive so it can read it.When I share a folder in the external hard drive it shows up on my network but it asks me for username and password and I have tried every username/password but have no idea which username/password its looking for. I tried allowing permission for guest but then get error saying I don't have permission.

Please can someone assist :(

---

### Post by mastablasta on 2013-04-19
for drive mounting check fstab. you probably messed up that one.

for sharing - it mightbe better to use ext4 or some other linux file system instead of widnows file system on linux. anyway i suggest you respond to the posts you already posted as there was some information already provided there.

samba sharing (SAMBA is the porgramme that handles shairng linux os files with widnows os) requires propper setup. computers should be in same group. furthermore the username and password is from the linux operating system. or it could be you've set up something in samba shares.

[https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html)

[http://www.techrepublic.com/blog/opensource/the-easiest-way-to-set-up-samba-for-file-sharing/1847](http://www.techrepublic.com/blog/opensource/the-easiest-way-to-set-up-samba-for-file-sharing/1847)

---

### Post by ibjsb4 on 2013-04-19
For mounting drives I find "pysdm" easier to use than fstab.  It gives you a user interface and it can be found in the software center.

[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

---

### Post by Ant01 on 2013-04-19
Can someone tell me whats the difference between the 2 versions of Ubuntu and which one to use, either 12.04 or 12.10 I assumed 12.10 would be the latest version

---

### Post by ibjsb4 on 2013-04-19
12o4 will be supported until 2017.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by coldraven on 2013-04-19
I have a 1TB external drive formatted NTFS. When I plug it in it just automatically appears in the Nautilus file browser.
I have no problems reading or writing to it, I do not have to add a share I can just copy/paste files.
To unmount it I just click the little triangle next to it's label.

I can only suggest doing a fresh install and this time make a note of the password and username that you set.

---

### Post by Ant01 on 2013-04-19
I've read the reports but am still confused!! I understand 12.04 has long term support and 12.10 short term support. Why does Shuttelworth release 2 versions and which one should we use, when the support runs out for 12.10 surely we can just upgrade.




Ubuntu 12.04 LTS (Precise Pangolin) is the current Ubuntu Long Term Support (LTS) release, made available on schedule on 26 April 2012.[135] Ubuntu 12.04 is Canonical's 16th release of Ubuntu and its fourth long term support version.[136] The name for the release was announced by Shuttleworth on 5 October 2011 and is named after the pangolin anteater.[137] Unlike previous LTS releases that have been supported for three years for the desktop version and five years for the server version, this release will be supported for five years for both versions.[138][139]

Ubuntu 12.10 (Quantal Quetzal)
On 23 April 2012 Shuttleworth announced that Ubuntu 12.10 would be named Quantal Quetzal. As this will be the first of a series of three releases before the next LTS release, Shuttleworth indicated that it will include a refreshed look, with work to be done on typography and iconography. The release takes its name from the quetzal, a species of Central American birds.[149] Ubuntu 12.10 was released on schedule on 18 October 2012.[150]

---

### Post by Ant01 on 2013-04-19
> **coldraven said:**
> I have a 1TB external drive formatted NTFS. When I plug it in it just automatically appears in the Nautilus file browser.
I have no problems reading or writing to it, I do not have to add a share I can just copy/paste files.
To unmount it I just click the little triangle next to it's label.

I can only suggest doing a fresh install and this time make a note of the password and username that you set.

I've done a fresh install, I changed from 12.04 to 12.10 but still have the same problems when booting up with the external drive plugged in. When I plug it after booting I can see and read and write to the files but I can't share the files on my LAN network

---

### Post by sudodus on 2013-04-19
> **Ant01 said:**
> Can someone tell me whats the difference between the 2 versions of Ubuntu and which one to use, either 12.04 or 12.10 I assumed 12.10 would be the latest version

12.04 was released in April 2012 and has LTS (long time support) until April 2017 (Ubuntu and Ubuntu Server) and until April 2015 (Xubuntu). 12.10 was release in October 2012 and has support until April 2014 (18 months).

Technically the main differences are that the linux kernels of the newer version has newer drivers, so it can manage more new hardware (computer parts as well as peripheral devices). The older version has older drivers and it can manage more old hardware. Generally, the LTS versions are more stable and can be expected to work without problems in a production environment (except for the first few months after the release date).

Examples: There was no support for dual boot with Windows 8 (in UEFI environment) in the original Ubuntu 12.04 LTS, but it is available from Ubuntu 12.04.2 LTS, and should be smoother in the newer versions. Xubuntu 12.04 LTS can run with old CPUs without PAE (physical address extension) for example Pentium M (on some laptops 8-10 years old), but Xubuntu 12.10 cannot because the non-pae kernel was abandoned in that release.

---

### Post by zombifier25 on 2013-04-19
> **Ant01 said:**
> I've read the reports but am still confused!! I understand 12.04 has long term support and 12.10 short term support. Why does Shuttelworth release 2 versions and which one should we use, when the support runs out for 12.10 surely we can just upgrade.

Well 12.04 (and LTS releases in general) is designed to be extremely rock solid, suitable to corporations or people who prefer to use their system for a long time without having to reinstall, however it won't have the new features and improvements of the newer releases (they would still receive bug fixes). 12.10 (and non-LTS releases) has more features, but it's also supported for a less amount of time and it's also less stable, suitable for those who want the greatest and latest, and don't mind upgrading their system every year or so.

So what do you want? Note that you can easily upgrade your Ubuntu when it runs out support, LTS or not.

---

### Post by sudodus on 2013-04-19
> **Ant01 said:**
> I've done a fresh install, I changed from 12.04 to 12.10 but still have the same problems when booting up with the external drive plugged in. When I plug it after booting I can see and read and write to the files but I can't share the files on my LAN network

Maybe you have managed to put some boot information on your external drive, or pointing to it, so that the computer tries to boot from it and fails. This needs to be cleared out in order to make it boot properly.

Please post the output of the following commands and put it within

[noparse]```
tags
```[/noparse]

High-light the output text and use the # icon above the editing window. Run the commands, when your external drive is connected and mounted.

```
sudo fdisk -lu
```
```
sudo blkid
```
```
cat /etc/fstab
```
```
cat /etc/mtab
```

And please let us know your computer's specs (at least the CPU, RAM and graphics card). It will help us give relevant advice :-)

---

### Post by Ant01 on 2013-04-19
When I boot up with external hard drive I get the following;
[I]error:no such device: 2ed6...........
grub rescue>
[/I]

Computer specs;
[I]Memory: 2.8 GiB
Processor: AMD Athlon(tm) II Neo N36L Dual-Core Processor x 2
Disk: 243.1GiB[/I]

---

### Post by Ant01 on 2013-04-19
**tova@tova-Server:~$ sudo fdisk -lu**
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007e531
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   482369535   241183744   83  Linux
/dev/sda2       482371582   488396799     3012609    5  Extended
/dev/sda5       482371584   488396799     3012608   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x99863243
 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    7  HPFS/NTFS/exFAT
_________________________________________________________________
**tova@tova-Server:~$ sudo blkid**
/dev/sda1: UUID="92721d58-39dc-4391-88a3-5f40a528e50b" TYPE="ext4" 
/dev/sda5: UUID="fce279d8-9331-4b50-957d-2d94e6f193a5" TYPE="swap" 
/dev/sdb1: LABEL="External" UUID="76D45FFCD45FBD55" TYPE="ntfs"
_________________________________________________________________
**tova@tova-Server:~$ cat /etc/fstab**
# /etc/fstab: static file system information.
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=92721d58-39dc-4391-88a3-5f40a528e50b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fce279d8-9331-4b50-957d-2d94e6f193a5 none            swap    sw              0       0
_________________________________________________________________
**tova@tova-Server:~$ cat /etc/mtab**
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfsd-fuse /run/user/tova/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=tova 0 0
/dev/sdb1 /media/tova/External fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
tova@tova-Server:~$

---

### Post by sudodus on 2013-04-19
- That processor is rather old, so I think Xubuntu will be better than standard Ubuntu. Try it live before installing :-)
- There is enough memory (also for Ubuntu or Kubuntu).
- What about the graphics card/chip?

You can get that information from ***hardinfo***

---

### Post by Ant01 on 2013-04-19
The machine is a HP server designed to be a small server so there is no on board graphic card

---

### Post by sudodus on 2013-04-19
Questions:

The computer name indicates that it's a server. Are you running Ubuntu Server? Without a graphical desktop environment?

Which version of Ubuntu are you running? 12.04 LTS, 12.10 or some older version? If you are not sure, check with

```
lsb_release -a
```

Answers and tips:

The output of the commands looks OK (but a little hard to read without the code tags). **[FONT=courier new]/etc/fstab[/FONT]** is OK :-)

Check the boot order in the BIOS menu system: I think that booting from USB or booting from that particular HDD partition 'External' is before the internal HDD in the boot order in BIOS. And you have something left from an attempt to boot from the USB drive, grub in the MBR and or a boot directory but no operating system, so you arrive at *grub rescue>*.

Either you change that boot order in BIOS, or remove what is left from the boot drive system from the external drive. See this link

[[COLOR=#ff0000]https://help.ubuntu.com/community/Grub2[/COLOR]]("https://help.ubuntu.com/community/Grub2")

---

### Post by Ant01 on 2013-04-19
GREAT THANKS A LOT, It was the boot order somehow my BIOS set up the USB as the first drive boot.

Now I need to figure out how to share the External drive on my LAN Network :)

---

### Post by Ant01 on 2013-04-19
When I look at Personal File Sharing preferences its Greyed Out, the message reads 
This feature cannot be enabled because the required packages are not installed on your system.

Idon't know which packages to load..

---

### Post by sudodus on 2013-04-19
I think the easiest way to share the drive is ssh. If there are Windows computers, you need winscp or some similar free software to connect. Another alternative is samba, which is harder to set up in the server, but needs no special software in Windows computers.

See this link to set up an ssh server. Within a local area network the default setting with password authentication is OK. If you intend to share the drive via the internet, passwords are not secure enough. Use public key authentication instead.

[[COLOR=#ff0000]https://help.ubuntu.com/10.04/serverguide/openssh-server.html[/COLOR]]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html")

---

### Post by Ant01 on 2013-04-26
Thank you for all the help so far but I'm really struggling with Ubuntu 12.04 Im not sure but it seems the older versions of Ubuntu seemed to be more stable or maybe I'm relying more on plug & play and not getting into the coding aspect of Ubuntu.

I've been having a lot of problems with running my HP 4L printer on Ubuntu. Initially it loaded the drivers and it was working. I struggled with networking the printer but eventually got it working. For some reason the network printing wasn't working so I deleted the printer and rebooted the machine so it would pick up the drivers again. After rebooting there was no printer loaded and when I click on add printer it does't see the printer and it asks for a URI. All this configuring is very frustrating especially for beginners I also can't get to share the external drive which is why I set up the ubuntu machine in the first place. When I was running Ubuntu 11.04 I had everything working perfectly but somehow I can't get it right again.

---

### Post by sudodus on 2013-04-26
If you ask specific questions, it is easier to help. You should even go one step further: make a new thread for each specific problem. Write a good descriptive title, that will attract people who know about that particular problem! 'Beginner lost' is not very specific, even if that is your feeling right now ;-)

Good luck, maybe we see each other again in your next thread :-)

---

### Post by DuckHook on 2013-04-26
It is important to note the philosophical differences between Linux and Windows. Linux is modular whereas Windows is monolithic. In practical terms and especially as it applies to you, this means that you must specifically add functionality in Linux whereas Windows will have more functions included by default. Users from Windows often consider this a Linux shortcoming until they start dealing with security: the modular nature of Linux enables it to load only such modules and services as are needed for specific tasks which means that there are almost no holes for malware to exploit. In contrast, the monolithic nature of Windows is a large part of why it blows chunks security-wise. However, this fine granularity of control in Linux (and by extension Ubuntu) does make it more complicated.

In your case, you cannot get your external disk visible across the network because:

1. External disks are removable and therefore assumed to be impermanent, like CDs, DVDs etc. It used to be that the default behaviour for such drives was to restrict them to local access only, which is not only reasonable, but a highly logical default. After all, if such disks are readily shareable across a network, what happens to the poor sod who has files open on your external drive should you decide to unplug it? I believe that the newer distros now allow such sharing, although I haven't experimented with this for years.

2. Linux desktop distros (of which Ubuntu is an example) are generally set up to act as clients only and not as servers. This is the reason why you hear some people (mistakenly) telling you that a firewall is superfluous because the default Ubuntu install has "no ports open". Since the default desktop install does not include server capabilities, it indeed opens no ports to the outside world and is far more secure than Windows because of this. However, this also means that it won't automatically share files with another computer because it doesn't have the required server software. If you want to share files from your box, you will have to install server software (Samba or NFS) and expand its role beyond that of a desktop so that it becomes a server. This will open security holes, and you should take care to guard these holes and harden your box properly. BTW, you should still activate Ubuntu's firewall. It's good security practice to have it running even if all ports are closed by default. It's very easy to download GUFW from the repositories and simply turn it on.

3. The HP 4L is an ancient warhorse and does not have the circuitry needed to be automatically recognized by Avahi or Bonjour. Please specify what you meant by network? It only has a 36 pin Centronics interface, so is it hooked up directly to your computer (and you want to share it with others)? Or did you install a network card? Or is it connected to a HP printer server? Please clarify. At any rate, it too will require a few more steps to set up.

Re: turning your box into a server.

Make no mistake... this is what you are trying to do the moment you want to "share files across a network". If you are sharing with other Windows boxes, then the best method is to install Samba. You might observe that your box already has some Samba software running. However, this is only client-side--that is, it only allows you to see Windows shares, not export them. If you want to install Samba server, there are many guides on the internet, but this is an easy one to follow.

[http://www.liberiangeek.net/2012/10/share-files-between-windows-7-and-ubuntu-12-10-quantal-quetzal/?ModPagespeed=noscript](http://www.liberiangeek.net/2012/10/share-files-between-windows-7-and-ubuntu-12-10-quantal-quetzal/?ModPagespeed=noscript)

Once installed and configured, you need to use nautilus to allow (set permissions) those specific directories that you want to share. Think twice about sharing external drives. If you physically unplug one while files are open, not only do you hose the work of the connected user, but you will usually corrupt the file structure of your external drive and may cause a kernel panic in the remote users' computers as well. External drives really aren't meant to be shared this way.

As sudodus suggests, should deal with your printer issue on a separate thread. If you post, be sure to provide missing details as asked in question 3 above.

---

