---
title: "How To: Automatic Backups on Network Hard Drive"
date: 2010-05-03
forum: Outdated Tutorials &amp; Tips
---

### Post by undoIT on 2010-05-03
I have been trying to figure how to set up the perfect automatic backup system for my needs with *buntu. I think I finally got it and I'm writing it down while it is still fresh in my mind so I can reference it later in case I forget. Hopefully, this is helpful for other people who have similar needs.

Backing up to a network hard drive (NAS) is more complicated in Linux than it should be. This tutorial describes all the steps necessary to get an automatic backup system running. I have only tested this with Kubuntu / Ubuntu 10.04 Lucid, but it should work for other versions and could also be adapted for other distros.

Don't be intimidated by the length of the tutorial, it is actually very easy to set this up if you follow it step by step. And, it is well worth the trouble if your computer hard drive ever fails.

***If anything can be improved, please let me know!***

Resources (read these later if you want more in depth info about the software used in this tutorial):

cifs configuration: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
rync commands: [http://linux.about.com/library/cmd/blcmdl1_rsync.htm](http://linux.about.com/library/cmd/blcmdl1_rsync.htm)
cron: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

[CENTER][SIZE="5"]Automatic Backups to the Network Hard Drive[/SIZE][/CENTER]

**1. Install necessary software**

Ubuntu:
```
sudo apt-get install smbfs libnotify-bin
```
(libnotify-bin is for alerts when the backup has failed)

Kubuntu:
```
sudo apt-get install smbfs
```

**2. Create mount folder**

```
sudo mkdir /media/backups
```

then, set ownership:
```
sudo chown USERNAME:GROUP /media/backups
```
"USERNAME" is what you use to login and "GROUP" is the same as your username.

**3. Create credentials file to mount drive**

Ubuntu:
```
gksudo gedit /etc/samba/user
```

Kubuntu:
```
kdesudo kate /etc/samba/user
```

in the empty file, paste the following (and save after adjusting settings):
> username=USERNAME
password=PASSWORD
replace USERNAME with the username you use to login and replace PASSWORD with the password you use to login.

then, change the permissions on the file to read only for security:
```
sudo chmod 0400 /etc/samba/user
```

**4. Setup network hard drive to always mount**

Ubuntu:
```
gksudo gedit /etc/fstab
```

Kubuntu:
```
kdesudo kate /etc/fstab
```

at the bottom of the file, add the following (and save after adjusting settings):

> //192.168.XXX.XXX/backups  /media/backups  cifs  credentials=/etc/samba/user,noexec,uid=1000,gid=1000  0 0


replace "192.168.XXX.XXX/backups" with the IP address of your network hard drive along with the path to the folder you have setup on the hard drive to store backups and hit enter after you have pasted the line in for an extra carriage return.

my fstab file looks like this:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6ce894a4-c599-46a4-810e-8e7a82e9a8c2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=585686b0-4158-4615-822d-2fbab12a2126 none            swap    sw              0       0

//192.168.1.100/backups  /media/backups  cifs  credentials=/etc/samba/user,noexec,uid=1000,gid=1000  0 0


**[COLOR="Red"]IMPORTANT: Make sure there is an extra carriage return after the last line in the fstab file, otherwise things will be broken next time you reboot and you will have to repair the fstab file with a Live CD.[/COLOR]**

**5. Reboot**
At this point it may be a good idea to reboot and check to make sure the network hard drive is being mounted. After reboot, navigate to /media/backups. You should see any files you already have in your backup folder listed there.

**6. Create a folder for current backup**

```
sudo mkdir /media/backups/lucid
```

then, set ownership:
```
sudo chown USERNAME:GROUP /media/backups/lucid 
```

Since I like to do a fresh install every six months when the new version of *buntu is released, I like to keep the backups in separate folders reflecting the current version I am using. Then, every time I install a new version I create a new folder to have the live update in, and compress the previous folder using bz2 for an archival backup (.i.e. karmic, jaunty etc). This works well for me, and you can set this up in whatever way makes sense for you.

**7. Create file to test if mounted**

```
sudo touch /media/backups/mounted
```

**8. Create the backup script**

Ubuntu:
```
gksudo gedit ~/backup.sh
```

Kubuntu:
```
kdesudo kate ~/backup.sh
```

paste the following and adjust the warning message as you see fit ;):

Ubuntu:

> #!/bin/sh
if [ -f "/media/backups/mounted" ]
then
rsync -rlptgo --delete --delete-excluded --exclude=**~ --exclude=**/*cache*/ --exclude=**/*Cache*/ --exclude=.local/share/Trash ~/ /media/backups/lucid/
else
notify-send 'Backup Failed' 'Please connect hard drive and back up your daturz ASAP!'
fi

Kubuntu:
> #!/bin/sh
if [ -f "/media/backups/mounted" ]
then
rsync -rlptgo --delete --delete-excluded --exclude=**~ --exclude=**/*cache*/ --exclude=**/*Cache*/ --exclude=.local/share/Trash --exclude=**/*trash*/ ~/ /media/backups/lucid/
else
kdialog --title "Backup Failed" --passivepopup "Please connect hard drive and back up your daturz ASAP!" 3600 &
fi

This script will backup everything in your home folder and exclude stuff you don't need to backup, like your trash and browser cache. For more advanced usage of rsync commands check out the rsync resource at the top of the tutorial.

**9. Make the script executable**

```
sudo chmod +x ~/backup.sh
```

**10. Set the backup to run automatically**

```
crontab -e
```

type or paste in the following, replacing the example (right-click or Ctrl Shift V to paste in terminal):

> 0 13 * * *     /home/USERNAME/backup.sh

this will run the backup every day at 1 PM. If you would like the backup to run once a week on every Sunday at 9 AM, add this:

> 0 09 * * 0     /home/USERNAME/backup.sh

replace "USERNAME" with your username.

press Ctrl O and then hit Enter to save the changes. then press Ctrl X to exit crontab.

I recommend running the backups daily. After the first backup is completed, only the changes will be copied over. rsync quickly compares all the files in the backup folder on the network hard drive with all the files in your home folder and only transfers what has changed so that the backup is an exact duplicate of your current home folder.

**11. Test that it doesn't work ;)**

```
sudo umount /media/backups
```

this will unmount the network hard drive. then run:

```
~/backup.sh
```

because the network hard drive is not mounted, the backup will fail and you should see the warning pop up.

**12. Test to make sure it does work**

```
sudo mount /media/backups
```

this will remount the hard drive (remember, the hard drive will automatically mount every time you boot up the computer, as long as the network hard drive is accessible, so you only need to run this if you have manually unmounted the hard drive).

then run:

```
~/backup.sh
```

the backup will start running in the background.

in your file browser (nautilus for Ubuntu / dolphin for Kubuntu) you can browser to your external hard drive by navigating to smb://192.168.XXX.XXX (of course replace with actual IP address) in the address bar. if you check your backups folder, you will see everything from your home folder is there (or in the process of being copied).

**13. Final step**

Do the happy dance, because you now have daily automatic backups that will keep your important files synced in case your computer hard drive ever fails.

---

### Post by snyderxc on 2010-06-03
Thanks!
Now I don't have to worry about anything awful happening to my beloved Ubuntu!
Just appreciated it, and wanted to say so! :)

---

### Post by CoreJohnson on 2010-06-16
Yeah. Thank you.=D> That's as good as awesomesauce!

---

### Post by luvallcomputers on 2010-12-27
I am trying to do an automatic backup to an extra hard drive in my computer.  I tried to follow the steps but make changes from network to local disk but missed something and wanted to know if someone could write the step but change from network drive to local drive.  I sure like the network backup and when my NAS is online I will be using this to backup to it also.

Thank you

---

### Post by xyepblra on 2011-01-04
Despite the fact that I totaly agree with the user of this forum who once said that backup is an act of cowardry, I really do find this tip awesome.
I was wondering though, is there any way to append
```
dpkg --get-selections > ~/my-packages
```to backup.sh? I think it could be very-very useful to have a chance of making a list of packages currently installed in your system and as well to have a chance of re-installing them with a single line command in terminal.

Another thing I'd like everyone to take a look at and correct me where I'm wrong is the notification about backup operation launch.
```
#!/bin/sh
if [ -f "/media/data/backups/mounted" ]
then
rsync -rlptgo --delete --delete-excluded --exclude=**~ --exclude=**/*cache*/ --exclude=**/*Cache*/ --exclude=.local/share/Trash ~/ /media/data/backups/lucid/
&&
notify-send --urgency normal --expire-time=10000 -i typing-monitor -h int:x:500 -h int:y:500 --icon ~/images/scripts/backup.png "Backup operation is launched" && mplayer ~/sounds/backup-sound.wav
else
notify-send 'Backup Failed' 'Please connect hard drive and back up your daturz ASAP!'
fi 
```

---

### Post by ivesjd on 2011-02-21
Nice writeup. The issue that I'm running into now is the script does not have permission to backup certain files. For example .smbcredentials which is owned by root:root. What is a way around this with out changing the permissions for such files?

---

### Post by mr.peeters@gmail.com on 2011-04-14
Hi, 

Sounds like exactly the thing i was looking for.
But before I try: do I need a static ip-address for my network drive?
I have a LacieNetworkspaceMax, and running ubuntu 10.10 on a Lenovo Thinkpad X201.

Thanks a lot!
d.

---

### Post by imac_89 on 2011-04-15
It is an advantage to have a static IP set on the device. It can either be done on the device itself, or your router.
If you configure it on your device, take note of the 'Gateway' and 'Subnet Mask' that is in the field (if you can see them, it can also be copied from your settings of the computer). The IP address should either be the same as it is, or if you are careful, one that you specify.

I stumbled upon this and hope to implement it on my Ubuntu server and DN-323 (RAID 1).

---

### Post by alfalfa55 on 2011-04-16
Use: Back In Time see [http://freshmeat.net/projects/backintime](http://freshmeat.net/projects/backintime) or [http://lifehacker.com/#!5212899/back-in-time-does-full-linux-backups-in-one-click]("http://lifehacker.com/#%215212899/back-in-time-does-full-linux-backups-in-one-click")

---

