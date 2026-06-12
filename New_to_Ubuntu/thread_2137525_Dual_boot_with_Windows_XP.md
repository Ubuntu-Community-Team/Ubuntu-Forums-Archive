---
title: "Dual boot with Windows XP"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by Mag107 on 2013-04-21
Hello again :smile:  System is the same as my last thread except the following changes - No  NVIDIA GeForce 210 Graphics card now - No 160GB IDE spare HDD..

Windows XP Pro is on C: WD640GB and the F: WD500GB is now empty..

What I wish to do is (with your help) make this a dual boot system with  Ubuntu 12.04.2 Alt AMD64 version on half the F: HDD and other half  storage.  O:)

Just have to finish the defrag on C: after moving and cleaning up..

So before I do anything else is there anything I need to get or do before running the install disk?

---

### Post by Dreamer Fithp Apprentice on 2013-04-21
That depends on whether there is anything on F. If not you're good to go.

If there is stuff you don't want to risk on there, it is a bit more complicated. If the drive is not allready divided into 2 or more partitions of suitable size I'd back up everything if you haven't allready. Actually you probably should do that anyway. If you have stuff on there you don't want to wipe out, you'll need to do the partitioning either from Windows or after booting the live CD (i.e., the installer) and selecting the "try" option, not the "install" option. The install option gives you limited repartitioning capabilities but in this case you will need something a little more sophisticated that will allow you to shrink or grow the partition or partitions on there so that you create in the resulting empty space a partition (or as many partitions as you want to use to install Ubuntu to) or if you already have enough partions adjust the sizes as seems appropriate. So you end up with one or more partitions you plan to install Ubuntu to that don't have any of your data on them.

---

### Post by mörgæs on 2013-04-21
Please use a more informative thread title. 
Changed.

---

### Post by Mag107 on 2013-04-21
Thanks Dreamer Fithp Apprentice :D

The F: HDD is now empty but not partitioned yet, don't know how yet lol
I guess it's still got the windows partition as it was for storage..

---

### Post by Mag107 on 2013-04-21
Much better [**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075"):cool:

---

### Post by prodigy_ on 2013-04-21
You probably should start [here](https://help.ubuntu.com/community/WindowsDualBoot). That's an up to date HOWTO with links to other relevant articles. Feel free to come back with any questions you might have.

---

### Post by Mag107 on 2013-04-21
Thanking you [ 						 					]("http://ubuntuforums.org/member.php?u=518500") 				 				 					 						 	[**[COLOR=#000000]prodigy_[/COLOR]**]("http://ubuntuforums.org/member.php?u=518500"):)

---

### Post by Lars Noodén on 2013-04-21
Also you might look at running XP inside of a VirtualBox VM with Ubuntu as the host and XP as the guest.  One main reason for that is that you can make a clean system and then take a snapshot.  Then whenever you need to run that system you can always start from that clean snapshot.

---

### Post by oldfred on 2013-04-21
IF this is a second drive (not partition) you want to install Ubuntu and the grub boot loader to sdb. Only if your system is pretty old and only boots from sda, then in BIOS make sdb the boot drive and boot Ubuntu. If will find Windows in sda and offer that as a boot choice. Then each drive can be booted without the other drive.

Some suggest disconnecting your Windows drive and if you just want the default install of / (root) and swap that is the easiest way. But anything else and the choice on where to install grub2's boot loader is only offered with Something Else or manual install.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

      
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

### Post by Dreamer Fithp Apprentice on 2013-04-22
> **Mag107 said:**
> Thanks Dreamer Fithp Apprentice

The F: HDD is now empty but not partitioned yet, don't know how yet lol
I guess it's still got the windows partition as it was for storage..
If it is empty I think you can use the installer CD with no problem. If in doubt, you can click the "try Ubuntu" button and look around the system before you start the install with the "install" button on the desktop of the live system's desktop. At that point you'll be back to the same installation program you would have been in had you just clicked "install" to begin with. The only bad mistake you could make would be to accidentally format and/or install to the wrong drive. Just look closely at each screen and make sure you understand it before you click anything. If in any doubt you can tell which drive you are installing to, cancel and back out. Other than that the installation procedure is pretty self explanatory. At one point you will want to select "do something else" instead of the totally inane default of "format and use the whole drive" (Hasn't anyone at Canonical heard of the principal of NOT making a dangerous option a default, but making the user consciously select it?). Then the method of dividing the F drive (which Ubuntu will call something else, probably "sdb", should be pretty self explanatory. If in any doubt about which drive is which, spend some time booting from the live disk and "trying ubuntu" with each disk connected by itself so you ABSOLUTELY know which one you are looking at and using gparted to check out what, if any partitions are there and their sizes. Write down your notes on paper. But when you boot back up to actually install make sure you have both drives connected in whatever fashion (i.e., which wires plugged in where) you had them before. Otherwise you wind might wind up with 2 bootloaders, each of which boots only one OS and with the only way to select which OS you want to boot being to go into the bios setup and select the drive boot order. [ added by edit: OK, I had failed to read Old Fred's post when I wrote that. He is probably more up to date than I am. Disconnecting the Windows drive before installation gave me exactly the problem I describe back in the day. But that was back in "legacy grub" times and I haven't tried since. I remember TRYING to get an effect somewhat like what he describes, having a robust system easily able to boot from either drive regardless of whether the other was present or working or if the drive order got switched around physically. I remember concluding it was probably possible but more trouble than it was worth. I guess the Ubuntu installer has improved.] Now when you boot with both disks connected, and "try Ubuntu" again you can fire up gparted again and look at the two drives and the sizes of their partitions and in that way know FOR SURE which one is being called sda, sdb, or whatever. Then you can go ahead and install with confidence. One caveat in selecting how to use the rest of the F drives space. Linux can read NTFS or FAT filesystems and Windows can read at least some extN filesystems but both have trouble with the permission systems of the other OS's native filesystems. That is no problem when it is just a matter of storage of files. But if any of these are executables or installers or archives of executables or installers it can mess things up if you don't put them on or copy them to a filesystem native to the OS you are running at the moment before you use them. So, if for instance, you have a bunch of SomeprogramInstaller.deb or Someotherprogram.tar.gz files for Linux, move them to an extN filesystem before you actually use them and they are more likely to be trouble free. Probably the same is true of exe files in Windows but I haven't tried.

---

### Post by Mag107 on 2013-04-23
Hello again and thanks for everyone's reply's (I think I understood some);)

I left Windows on the 650GB HDD and Partitioned the 500GB HDD about half for storage and the other half for Ubuntu.
I have just done the install of Ubuntu and rebooted and I get this start up screen [ATTACH=CONFIG]241679[/ATTACH] upon selecting Microsoft Windows XP Professional on (/dev/sda1), I then get the normal screen [ATTACH=CONFIG]241680[/ATTACH] and can boot Windows from there but I can't boot Ubuntu still....

---

### Post by Vulpus on 2013-04-23
At the risk of being controversial, I think the days of dual boot are past and there is little reason to do it anymore.

The reason is the availability of low cost, large capacity USB keydrives and the ease of installing Linux on them. 

[http://www.pqigroup.com/prod_in.aspx?mnuid=1286&modid=138&prodid=557](http://www.pqigroup.com/prod_in.aspx?mnuid=1286&modid=138&prodid=557)

If you want to use Windows you boot as normal.  If you want to use Linux you plug in your keydrive. No hassle with partitioning drives and messing up your boot sector and all the rest of the palaver that goes with it.

I used to dual boot both my laptop (Vista) and desktop (Win7) but now I just have one operating system on each and plug in a keydrive when I want to use Linux (such as for online banking). I keep all my documents in Ubuntu One so I can access them anywhere and keep all my music in a common hard drive. So no more duplication of data and wondering if the files are on the Linux or the Windows drive.

---

### Post by Mag107 on 2013-04-23
Hm interesting [ 						 							]("http://ubuntuforums.org/member.php?u=38156")[**[COLOR=#000000]Vulpus[/COLOR]**]("http://ubuntuforums.org/member.php?u=38156"), a 16GB one is that big enough?

---

### Post by Vulpus on 2013-04-23
> **Mag107 said:**
> Hm interesting [ 						 							]("http://ubuntuforums.org/member.php?u=38156")[**[COLOR=#000000]Vulpus[/COLOR]**]("http://ubuntuforums.org/member.php?u=38156"), a 16GB one is that big enough?

Well I currently use a 16GB but an 8GB would do, the formatting procedure only creates a 4GB partition anyway. I don't actually save anything on the USB, all my data is either in the cloud or on a separate hard drive. That way if you lose the keydrive or it goes faulty you only use your preferences and not any of your data (I learned this the hard way).

If you use the Universal USB Installer it really is as easy as 1-2-3.

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

The only issue you may have is getting your PC to boot from USB. Most modern PCs/laptops allow this but seem to do it in different ways. My Acer laptop sometimes just ignores the USB and boots straight into Windows for no apparent reason. On my work HP laptop you have to press ESC and then select 'boot from USB', my desktop always just works.

---

### Post by Mag107 on 2013-04-23
Thanks again [ 						 					]("http://ubuntuforums.org/member.php?u=38156") 				 				 					 						 	[**[COLOR=#000000]Vulpus[/COLOR]**]("http://ubuntuforums.org/member.php?u=38156") . :)

Well I just had a look in my Bios for boot settings and apart from the usual ones I do have these 3, USB-FDD, USB-ZIP and USB-CDROM...

---

### Post by oldfred on 2013-04-23
If you have all those USB settings you can boot from USB flash drive, but it will be under hard drives, and not any  USB settings. And it usually does not show the "new" hard drive unless it is bootable.

I have a full install of Ubuntu in my 16GB flash drive, using a 8GB partition for the install and 8GB for data.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by Vulpus on 2013-04-23
> **oldfred said:**
> 
       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

That is useful info. It is true that running from a USB stick is slower than an HD install but in my case I am happy to accept this. For fast boot and performance I have Saluki Linux on a pendrive. It is not as elegant as Ubuntu but super fast.

---

### Post by Mag107 on 2013-04-24
Thanks oldfred + Vulpus :cool:

So far straight forward all easy until this error.. I'll show that screens I've had in order..[ATTACH=CONFIG]241704[/ATTACH] Bios can see it yeh lol, [ATTACH=CONFIG]241705[/ATTACH] English Yes,[ATTACH=CONFIG]241706[/ATTACH] OMG look and then [ATTACH=CONFIG]241707[/ATTACH] DOH...

---

### Post by Vulpus on 2013-04-24
What version of Ubuntu are you using? I never saw those option screens when using 12.10.

---

### Post by Mag107 on 2013-04-24
Ubuntu 12.04.2 Alternate amd64

---

### Post by oldfred on 2013-04-24
A user found with the Desktop 12.04.2 a typo in the file names. ....amd64.efi is ...amd6.efi

If the alternative also has the typo please add it to the bug report. With only one person reporting it, they ignore it as just that user having an issue.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1172065](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1172065)

---

### Post by Vulpus on 2013-04-24
Try an alternative 'small' Linux version such as Puppy. This is a very small ISO so is quick to download and install on a USB. If that works then you know the procedure works. Then try Ubuntu gain, it may be that the download was corrupted.

---

### Post by Mag107 on 2013-04-25
Thanks [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711"), the typo could well do it but I've done some homework and from what I can find is that my system can only run the 32bit setup so that's why it can't find the /casper/vmlinuz.efi..My bios hasn't got uefi capability..

---

### Post by Mag107 on 2013-04-25
Thanks also [ 						 					]("http://ubuntuforums.org/member.php?u=38156") 				 				 					 						 	[**[COLOR=#000000]Vulpus[/COLOR]**]("http://ubuntuforums.org/member.php?u=38156")..Trying Puppy right now (well as soon as I download it) :)

---

### Post by Mag107 on 2013-04-25
[COLOR=#000000][FONT=verdana][/FONT]Ohh getting sick of nothing working [/COLOR]](*,)                  Here's 2 more screen shots...[ATTACH=CONFIG]241742[/ATTACH] and then it gets this far and stops[ATTACH=CONFIG]241743[/ATTACH]

---

