---
title: "Re-install ??"
date: 2015-09-08
forum: New to Ubuntu
---

### Post by Dana_Flaherty on 2015-09-08
I have Lubuntu 14.04, trouble` with boot etc etc..Can I just 're-install' from a CD? I burned a new one last week...Will it 'overwrite' the old install??  
Thanx..Dana

---

### Post by sandyd on 2015-09-08
> **Dana_Flaherty said:**
> I have Lubuntu 14.04, trouble` with boot etc etc..Can I just 're-install' from a CD? I burned a new one last week...Will it 'overwrite' the old install??  
Thanx..Dana
During the installation process, the installer will ask you about partitioning:

If you have only one OS on the system, and you do _not_ need anything else on the drive, just choose 'Erase Disk and install Lubuntu'. This will remove ALL your data including other OSes on the drive.

Else, choose 'Something Else' to adjust the partitions yourself.

---

### Post by @Tornado on 2015-09-08
Dana,

I am the type of person where I try to figure out what is happening. Especially in your case, during the boot. When all else fails, Re-Install.

Ohhh and what sandyd said. LoL

~Jason

---

### Post by Dana_Flaherty on 2015-09-10
Ya, I have an old XP in the other partition that I want to keep...( Why,i don't know )....

---

### Post by Dana_Flaherty on 2015-09-10
When I boot from the grub, ( Lubuntu first on the list )it'll just sit on a blank screen. If I boot to Windows first, then just hit restart in Windows, it closes Windows, back comes the Grub, auto boots into Lubuntu, and I'm good....I burned a Super grub 2 disc, boot from that, , after some selections, and a lot of script, it'll boot to Lubuntu, AND reboot from there also, but only once....I'm a stubborn SOB....

---

### Post by oldfred on 2015-09-11
Best to see details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

SuperGrub may run the bootinfoscript which is the same as the first third of Summary Report from Boot-Repair.  But Summary report does have more info.

---

### Post by Dana_Flaherty on 2015-09-11
here's my boot info             [http://paste.ubuntu.com/12350584/](http://paste.ubuntu.com/12350584/)                           I think i did this right...

---

### Post by oldfred on 2015-09-13
Summary Report looks normal, just that you have a lot of kernels. You should houseclean, but if reinstalling that will houseclean everything.

       Updates, backups, delete old kernels - TheFu in Forums
[URL="http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs"]http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs
[/URL]
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
sudo apt-get -s autoremove
      
 I prefer synatic and keeping 2 kernels, current and one known working older on.
[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

If you are going to reinstall make sure you have good backups, particularly /home & a list of installed apps to make it easy to reinstall them.
       
 discussion of alternatives/strategy backups
[URL="https://help.ubuntu.com/community/BackupYourSystem"]https://help.ubuntu.com/community/BackupYourSystem
[/URL]
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)


Then just use Something Else, choose/change your existing sda5 as new / (root) and reinstall.
       
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
      Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)[URL="http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs"]
[/URL]

---

### Post by Dana_Flaherty on 2015-09-14
Thanx very much !!!

---

