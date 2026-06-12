---
title: "Remastersys"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by Javelin Dan on 2014-02-24
Running Ubuntu 12.04 on a dual core Compaq Presario laptop.
 

 

 I'm trying to make a bootable, instalable iso of a slightly customized version of Ubuntu using Remastersys.  
 

 I first installed the software following the instructions found here: [http://askubuntu.com/questions/133272/how-do-i-install-remastersys](http://askubuntu.com/questions/133272/how-do-i-install-remastersys). Next, I tried making a copy using the “Distribution” option. It worked automatically and perfectly, but as most of you know, it is only a bare distribution that contains none of the customization that I am trying to save.  
 

 I next tried the “Backup” option. Again it ran automatically until I got a failure message at the end of the process telling me to check the log. It showed the following output:
 

 

 Distribution Mode Selected 
 Enabling remastersys-firstboot 
 Checking filesystem type of the Working Folder 
 /home/remastersys/remastersys is on a ext4 filesystem 
 Making sure popularity contest is not installed 
 Installing the Ubiquity GTK frontend 
 Checking if the /home/remastersys/remastersys folder has been created 
 Creating /home/remastersys/remastersys folder tree 
 Creating /home/remastersys/remastersys/ISOTMP folder tree 
 Copying /var and /etc to temp area and excluding extra files  ... this will take a while so be patient 
 Cleaning up files not needed for the live in /home/remastersys/remastersys/dummysys 
 Cleaning up passwd, group, shadow and gshadow files for the live system 
 Making sure adduser and autologin functions of casper are set properly 
 Copying memtest86+ for the live system 
 Creating isolinux setup for the live system 
 Checking the ARCH of the system and setting the README.diskdefines file 
 Creating filesystem.manifest and filesystem.manifest-desktop 
 Creating the casper.conf file. 
 Checking and setting user-setup-apply for the live system 
 Setting up casper and ubiquity options for dist mode 
 Creating a new initial ramdisk for the live system 
 Copying your kernel and initrd for the livecd 
 Creating filesystem.squashfs   ... this will take a while so be patient 
 Cannot stat source directory "/New" because No such file or directory 
 ------------------------------------------------------ 
 Mount information 
 /dev/sda1 on / type ext4 (rw,errors=remount-ro) 
 proc on /proc type proc (rw,noexec,nosuid,nodev) 
 sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 
 none on /sys/fs/fuse/connections type fusectl (rw) 
 none on /sys/kernel/debug type debugfs (rw) 
 none on /sys/kernel/security type securityfs (rw) 
 udev on /dev type devtmpfs (rw,mode=0755) 
 devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) 
 tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) 
 none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) 
 none on /run/shm type tmpfs (rw,nosuid,nodev) 
 binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) 
 gvfs-fuse-daemon on /home/daniel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=daniel) 
 /dev/sdb1 on /media/WINE type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks) 
 ------------------------------------------------------ 
 Disk size information 
 Filesystem      Size  Used Avail Use% Mounted on 
 /dev/sda1       118G   36G   77G  32% / 
 udev            1.4G  4.0K  1.4G   1% /dev 
 tmpfs           554M  880K  553M   1% /run 
 none            5.0M     0  5.0M   0% /run/lock 
 none            1.4G   72K  1.4G   1% /run/shm 
 /dev/sdb1       960M   20M  941M   3% /media/WINE 
 ------------------------------------------------------ 
 Casper Script info 
 total 148 
 -rwxr-xr-x 1 root root  297 Jan 22  2013 01integrity_check 
 -rwxr-xr-x 1 root root  467 Jan 22  2013 05mountpoints 
 -rwxr-xr-x 1 root root  571 Jan 22  2013 07remove_oem_config 
 -rwxr-xr-x 1 root root  400 Jan 22  2013 12fstab 
 -rwxr-xr-x 1 root root  830 Jan 22  2013 13swap 
 -rwxr-xr-x 1 root root 1221 Jan 22  2013 14locales 
 -rwxr-xr-x 1 root root 2920 Jan 22  2013 15autologin 
 -rwxr-xr-x 1 root root  577 Jan 22  2013 18hostname 
 -rwxr-xr-x 1 root root 8878 Jan 22  2013 19keyboard 
 -rwxr-xr-x 1 root root  546 Jan 22  2013 20xconfig 
 -rwxr-xr-x 1 root root  624 Jan 22  2013 22gnome_panel_data 
 -rwxr-xr-x 1 root root  867 Jan 22  2013 22screensaver 
 -rwxr-xr-x 1 root root  577 Jan 22  2013 22serialtty 
 -rwxr-xr-x 1 root root  410 Jan 22  2013 22sslcert 
 -rwxr-xr-x 1 root root  380 Jan 22  2013 23etc_modules 
 -rwxr-xr-x 1 root root 3786 Jan 22  2013 23networking 
 -rwxr-xr-x 1 root root 2102 Jan 22  2013 24preseed 
 -rwxr-xr-x 1 root root 3939 Jan 22  2013 25adduser 
 -rwxr-xr-x 1 root root 1996 Jan 22  2013 25configure_init 
 -rwxr-xr-x 1 root root  644 Jan 22  2013 26disable_user_menu 
 -rwxr-xr-x 1 root root 1421 Jan 22  2013 30accessibility 
 -rwxr-xr-x 1 root root 1152 Jan 22  2013 31disable_update_notifier 
 -rwxr-xr-x 1 root root  463 Jan 22  2013 32disable_hibernation 
 -rwxr-xr-x 1 root root  650 Jan 22  2013 33enable_apport_crashes 
 -rwxr-xr-x 1 root root  928 Jan 22  2013 34disable_kde_services 
 -rwxr-xr-x 1 root root  562 Jan 22  2013 35fix_language_selector 
 -rwxr-xr-x 1 root root  407 Jan 22  2013 36disable_trackerd 
 -rwxr-xr-x 1 root root  908 Jan 22  2013 40install_driver_updates 
 -rwxr-xr-x 1 root root  561 Jan 22  2013 41apt_cdrom 
 -rwxr-xr-x 1 root root 1039 Jan 22  2013 43disable_updateinitramfs 
 -rwxr-xr-x 1 root root  640 Jan 22  2013 44pk_allow_ubuntu 
 -rwxr-xr-x 1 root root  594 Jan 22  2013 45jackd2 
 -rwxr-xr-x 1 root root  215 Jan 22  2013 48kubuntu_disable_restart_notifications 
 -rwxr-xr-x 1 root root  169 Jan 22  2013 49kubuntu_mobile_session 
 -rwxr-xr-x 1 root root  346 Jan 22  2013 50ubiquity-bluetooth-agent 
 ------------------------------------------------------ 
 /etc/remastersys.conf info 
  
 #Remastersys Global Configuration File 
  
  
 # This is the temporary working directory and won't be included on the cd/dvd 
 WORKDIR="/home/remastersys" 
  
  
 # Here you can add any other files or directories to be excluded from the live filesystem 
 # Separate each entry with a space 
 EXCLUDES="" 
  
  
 # Here you can change the livecd/dvd username 
 LIVEUSER="custom" 
  
  
 # Here you can change the name of the livecd/dvd label 
 LIVECDLABEL="Custom Live CD" 
  
  
 # Here you can change the name of the ISO file that is created 
 CUSTOMISO="custom-$1.iso" 
  
  
 # Here you can change the mksquashfs options 
 SQUASHFSOPTS="-no-recovery -always-use-fragments -b 1M -no-duplicates" 
  
  
 # Here you can prevent the Install icon from showing up on the desktop in backup mode. 0 - to not show 1 - to show  
 BACKUPSHOWINSTALL="1" 
  
  
 # Here you can change the url for the usb-creator info 
 LIVECDURL="http://www.remastersys.com" 
 ------------------------------------------------------ 
 /etc/casper.conf info 
 # This file should go in /etc/casper.conf 
 # Supported variables are: 
 # USERNAME, USERFULLNAME, HOST, BUILD_SYSTEM 
  
 export USERNAME="custom" 
 export USERFULLNAME="Live session user" 
 export HOST="custom" 
 export BUILD_SYSTEM="Ubuntu" 
 export FLAVOUR="custom" 
 ------------------------------------------------------ 
 /etc/passwd info 
 root:0:0:root:/root:/bin/bash 
 daemon:1:1:daemon:/usr/sbin:/bin/sh 
 bin:2:2:bin:/bin:/bin/sh 
 sys:3:3:sys:/dev:/bin/sh 
 sync:4:65534:sync:/bin:/bin/sync 
 games:5:60:games:/usr/games:/bin/sh 
 man:6:12:man:/var/cache/man:/bin/sh 
 lp:7:7:lp:/var/spool/lpd:/bin/sh 
 mail:8:8:mail:/var/mail:/bin/sh 
 news:9:9:news:/var/spool/news:/bin/sh 
 uucp:10:10:uucp:/var/spool/uucp:/bin/sh 
 proxy:13:13roxy:/bin:/bin/sh 
 www-data:33:33:www-data:/var/www:/bin/sh 
 backup:34:34:backup:/var/backups:/bin/sh 
 list:38:38:Mailing List Manager:/var/list:/bin/sh 
 irc:39:39:ircd:/var/run/ircd:/bin/sh 
 gnats:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh 
 libuuid:100:101::/var/lib/libuuid:/bin/sh 
 syslog:101:103::/home/syslog:/bin/false 
 messagebus:102:105::/var/run/dbus:/bin/false 
 colord:103:108:colord colour management daemon,,,:/var/lib/colord:/bin/false 
 lightdm:104:111:Light Display Manager:/var/lib/lightdm:/bin/false 
 whoopsie:105:114::/nonexistent:/bin/false 
 avahi-autoipd:106:117:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false 
 avahi:107:118:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false 
 usbmux:108:46:usbmux daemon,,,:/home/usbmux:/bin/false 
 kernoops:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false 
 pulse:110:119ulseAudio daemon,,,:/var/run/pulse:/bin/false 
 rtkit:111:122:RealtimeKit,,,:/proc:/bin/false 
 speech-dispatcher:112:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh 
 hplip:113:7:HPLIP system user,,,:/var/run/hplip:/bin/false 
 saned:114:123::/home/saned:/bin/false 
 ntp:115:125::/home/ntp:/bin/false 
 nobody:65534:65534:nobody:/nonexistent:/bin/sh 
 ------------------------------------------------------ 
 /etc/group info 
 root:0: 
 daemon:1: 
 bin:2: 
 sys:3: 
 adm:4: 
 tty:5: 
 disk:6: 
 lp:7: 
 mail:8: 
 news:9: 
 uucp:10: 
 man:12: 
 proxy:13: 
 kmem:15: 
 dialout:20: 
 fax:21: 
 voice:22: 
 cdrom:24: 
 floppy:25: 
 tape:26: 
 sudo:27: 
 audio:29ulse 
 dip:30: 
 www-data:33: 
 backup:34: 
 operator:37: 
 list:38: 
 irc:39: 
 src:40: 
 gnats:41: 
 shadow:42: 
 utmp:43: 
 video:44: 
 sasl:45: 
 plugdev:46: 
 staff:50: 
 games:60: 
 users:100: 
 libuuid:101: 
 crontab:102: 
 syslog:103: 
 fuse:104: 
 messagebus:105: 
 bluetooth:106: 
 scanner:107: 
 colord:108: 
 lpadmin:109: 
 ssl-cert:110: 
 lightdm:111: 
 nopasswdlogin:112: 
 netdev:113: 
 whoopsie:114: 
 mlocate:115: 
 ssh:116: 
 avahi-autoipd:117: 
 avahi:118: 
 pulse:119: 
 pulse-access:120: 
 utempter:121: 
 rtkit:122: 
 saned:123: 
 sambashare:124: 
 ntp:125: 
 winbindd_priv:126: 
 vboxusers:127: 
 nogroup:65534: 
 ------------------------------------------------------ 
 /etc/X11/default-display-manager info 
 /usr/sbin/lightdm 
 ------------------------------------------------------ 
 /etc/skel info 
 /etc/skel 
 /etc/skel/.profile 
 /etc/skel/.bashrc 
 /etc/skel/examples.desktop 
 /etc/skel/.bash_logout 
 ------------------------------------------------------ 
 lsb-release info 
 DISTRIB_ID=Ubuntu 
 DISTRIB_RELEASE=12.04 
 DISTRIB_CODENAME=precise 
 DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS" 
 ------------------------------------------------------ 
 remastersys version info 
 REMASTERSYSVERSION="3.0.4-2" 
   
 ------------------------------------------------------ 
 ISOTMP info 
 /home/remastersys/remastersys/ISOTMP: 
 total 20 
 drwxr-xr-x 2 root root 4096 Feb 14 19:24 casper 
 drwxr-xr-x 2 root root 4096 Feb 14 19:23 install 
 drwxr-xr-x 2 root root 4096 Feb 14 19:23 isolinux 
 drwxr-xr-x 2 root root 4096 Feb 14 19:23 preseed 
 -rw-r--r-- 1 root root  195 Feb 14 19:23 README.diskdefines 
  
 /home/remastersys/remastersys/ISOTMP/casper: 
 total 25240 
 -rw-r--r-- 1 root root    59127 Feb 14 19:23 filesystem.manifest 
 -rw-r--r-- 1 root root    59063 Feb 14 19:23 filesystem.manifest-desktop 
 -rw-r--r-- 1 root root 20681175 Feb 14 19:24 initrd.gz 
 -rw-r--r-- 1 root root      195 Feb 14 19:23 README.diskdefines 
 -rw------- 1 root root  5031904 Feb 14 19:24 vmlinuz 
  
 /home/remastersys/remastersys/ISOTMP/install: 
 total 176 
 -rw-r--r-- 1 root root 176764 Feb 14 19:23 memtest 
  
 /home/remastersys/remastersys/ISOTMP/isolinux: 
 total 400 
 -rw-r--r-- 1 root root  24576 Feb 14 19:23 isolinux.bin 
 -rw-r--r-- 1 root root    896 Feb 14 19:23 isolinux.cfg 
 -rwxr-xr-x 1 root root 220583 Feb 14 19:23 splash.png 
 -rw-r--r-- 1 root root 155792 Feb 14 19:23 vesamenu.c32 
  
 /home/remastersys/remastersys/ISOTMP/preseed: 
 total 4 
 -rwxr-xr-x 1 root root 212 Feb 14 19:23 custom.seed 
 ------------------------------------------------------ 
 /home/remastersys/remastersys/tmpusers info 
 daniel 
 ------------------------------------------------------ 
 Command-line options = dist 
 ------------------------------------------------------ 
 Removing the ubiquity frontend as it has been included and is not needed on the normal system 
 Calculating the installed filesystem size for the installer 
 Removing remastersys-firstboot from system startup 
 The filesystem.squashfs filesystem is missing.  Either there was a problem creating the compressed filesystem or you are trying to run sudo remastersys dist iso before sudo remastersys dist cdfs 
 

 

 

 I'm guessing this last sentence tells me what the problem is, but I don't really understand it. A simple set of instructions from this point would be greatly appreciated.

---

### Post by beelzebufo on 2014-02-24
remastersys has been discontinued if I am not mistaken, which is sad, it was a great tool.  If you are simply trying to create a backup, I would recommend just using deja-dup.  Another tool you could use which is available in the ubuntu software center is called ubuntu customization kit, I have not used it, can't vouch for it, but it may solve some of your problems, although it sounds like you would have to manually add all the packages you want. yet another tool I found is this [https://ubuntufriends.wordpress.com/2007/03/31/edit-and-create-your-bootable-iso-image-the-easy-way/](https://ubuntufriends.wordpress.com/2007/03/31/edit-and-create-your-bootable-iso-image-the-easy-way/)  Again, I have not tried it, I just found it in a google search. But, anyway, back to your question.  I think it's telling you to run "sudo remastersys dist cdfs" before you run the iso creation, that will create a file system that it can use to create a bootable iso.. I think, anyway, I remember running into that same problem and you have to do things in a specific order to get it to work properly, your iso also can't be over a certain size.. I think it was 4 gigs, I could be wrong on that.  anyway, my guess is that the iso is just too big for it to save properly.  I am not an expert (obviously) but I hope I was able to help a little.

---

### Post by Javelin Dan on 2014-02-24
Thanks for the response, beelzebufo. I already use deja-dup for back-ups, but here I am actually trying to generate a live DVD. I mistated in my post - I am actually trying to remaster Lubuntu, not Ubuntu, so I THINK I can make it under 4 gigs. Got a lot on my plate for the next few days, but I'll look into all you suggested and report back. Thanks for the help!

---

### Post by Javelin Dan on 2014-02-28
OK, back to this finally. Thanks for the command, beelzebufo. That seemed to do the trick, but at the end my file was just too big. Seems like it would have worked otherwise. After Googling around a little, it seems that I actually want something that would allow me to modify an existing iso. Ubuntu Customization kit looked good from the tutorial I saw and looked like it had a nice GUI. But after I installed it and clicked on it to open, all I got was an open empty terminal. Don't really know what to do with that. I also considered  Reconstructor, a web app which also looked promising. However, the web site wouldn't open and any Ubuntu threads about it said the software had been removed. If anyone has any info, I'd be greatful. I may try a new thread in this regard.

But since beelzebufo's suggestion seemed to work, I'm going to mark this thread "Solved" in the event it helps someone else. Thanks.

---

### Post by justnice980-8 on 2014-10-09
Remastersys has in fact been discontinued. It is now succeeded by Black Lab Imager ( [http://system-imaging.blogspot.com/](http://system-imaging.blogspot.com/) ). As for the reason remastersys did not save any of the customizations is because you need to copy the contents of your home directory and paste them into /etc/skel. After that is done all your customizations will be imported into the custom iso.

---

### Post by chujen on 2014-10-09
There is a great tool that creates a live backup of your system with the updates and changes you have done: 
[http://sourceforge.net/projects/systemback/](http://sourceforge.net/projects/systemback/)
You can find some details in [http://ubuntuforums.org/showthread.php?t=2234619](http://ubuntuforums.org/showthread.php?t=2234619)
And if you can read spanish a detailed explain here: [http://trastetes.blogspot.mx/2014/03/crear-sistema-live-en-ubuntu-1404-con.html](http://trastetes.blogspot.mx/2014/03/crear-sistema-live-en-ubuntu-1404-con.html)
It works very quickly... in less than thirty minutes you will install your own version of Ubuntu in other machine.

---

