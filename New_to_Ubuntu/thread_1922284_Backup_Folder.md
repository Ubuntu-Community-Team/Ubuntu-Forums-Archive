---
title: "Backup Folder"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by BEARSPIDER on 2012-02-08
I have Ubuntu 11.10 running and i would like to know what folders i should backup so that is i had a crash or i deleted the OS i could do a system restore and my system would be just as i left it. 
I am trying to keep my backup small I currently have a 10Gb backup folder which is basically everything but my home folder. That just seems to big or is that just me.

---

### Post by pixiq on 2012-02-08
I suggest that you get an external drive (USB or eSATA) and have enough space to backup all you want or need. It is very convenient to restore a system if you backup it regularly. One simple way (but time-consuming) is to make complete images with a cloning tool, for example ***Clonezilla***. This also works for dual boot systems with Windows and Ubuntu.

You can also make a script using ***rsync*** for backup or use some more or less advanced system. This works for Ubuntu.

Because actually, your personal data (at /home) is more valuable than the system and its settings. So if you want that, you should definitely also backup /home.

---

### Post by HermanAB on 2012-02-08
Howdy,

This is a common concern for new Linnux users.  I have been there myself 15 years ago.  However, after a few years of using Linux, one realizes that backing up the whole system is a total waste of time.  Just backup your data.

The reason is that Linux is extremely stable and simply doesn't screw up the way you fear it would.  Secondly, when your hard disk fails one day, you would want to install the latest version of Linux and would not want to restore an old decrepit version of yesteryear.

---

### Post by oldfred on 2012-02-08
I prefer to use rsync and have everything I need to do a clean install. 

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I modified this:
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

Other applications if data not separate
apache, any sqldb, tomcat

---

### Post by BEARSPIDER on 2012-02-09
Thanks for the Reply all of you. I already back up my personal data from the home folder but i guess what i am looking for is from my drive folder which folders can i exclude using UBUNTU Backup tool. Again so i can make my backup file smaller.
My Drive folder has the following:
/bin
/boot
/cdrom
/dev
/etc
/home
/lib
/lib64
/lost+found
/media
/mnt
/opt
/proc
/root
/run
/sbin
/selinux
/srv
/sys
/tmp
/usr
/var
Out of these which can i exclude from a backup, so i am not backing up system files that will be re-installed when i re-install UBUNTU 11.10 if a crash happened. I just want the files i added or changed. Space is not necessarily a problem I a TB external but i just want to do it right and learn a little in the process.

---

### Post by wolfen69 on 2012-02-09
All you really need is your /home folder. All the rest are system files which will be reinstalled, if the need arises.

---

### Post by grahammechanical on 2012-02-09
A lot of your personal configuration settings are in files in the home folder.

I am testing 12.04 and I recently had to re-install. I did not mark the partition to be formatted and the OS installed but none of the folders and files in the home folder were overwritten. When I rebooted all my settings, such as themes and background images, were in place as were my web browser bookmarks and all that stuff.

This is why we are saying it is the stuff in the home folder that matters. We do a system restore by re-installing.

Regards.

---

### Post by oldfred on 2012-02-10
I just backup /home and keep manual track of any system file in /etc that I manually edit. I also export the list of installed apps.

More detail here:
More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

Files to include or exclude from full system backup.
[http://ubuntuforums.org/showthread.php?t=1903085](http://ubuntuforums.org/showthread.php?t=1903085)

Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
/home/*/.cache
/home/*/.dbus
/home/*/.dropbox
/home/*/.gvfs
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/**
/home/*/.qt
/home/*/.thumbnails
/home/*/Examples
/home/.ecryptfs
/home/lost+found

---

### Post by Damascushead on 2012-02-10
I like to use tar to make a simple backup of the root (/) directory. Because everything in linux is a file, it just creates a tar file of your entire system.
 
This is a great tutorial that recently helped me.
 
[[COLOR=#444444]https://help.ubuntu.com/community/BackupYourSystem/TAR[/COLOR]]("https://help.ubuntu.com/community/BackupYourSystem/TAR")

---

