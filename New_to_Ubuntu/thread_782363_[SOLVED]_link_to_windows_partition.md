---
title: "[SOLVED] link to windows partition"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-05-04
im trying to make a link on my desktop ,or possibly one for AWN, that will bring me to my windows partition 
(rather than going to the menu to Places-Computer then clicking the windows drive)

can anyone help me out?

---

### Post by otrojake on 2008-05-04
All you have to do is figure out your mount point for you Windows drive.  It will be under the /media directory.  If you have multiple mounted partitions with generic names (such as disk1) then just go to the /media folder and start clicking to figure out which one it is.  Then--if you want to go the icon on the desktop route--right-click on the desktop and select "create launcher."  In the dropdown box select "location."  Type in the name you want for the icon and then--this is important--where is says location type in "file:///media/name_of_your_mounted_drive" without quotes.  You can also change the icon by clicking on the launcher emblem and navigating to a folder with the appropriate icons for your theme (/usr/share/icons).

For AWN go to the Awn Manager under System>Preferences and navigate to the launchers tab.  Click Add for a new launcher and using the /media directory for your disk and enter in all the information.  The only thing you'd have to do differently is instead of putting file:// before the directory just type in "nautilus /media/name_of_your_mounted_drive" without quotes.  Hope that helps. :)

---

### Post by Victormd on 2008-05-04
To properly mount the windows partition, you'll need to edit fstab...
Here are a few checks before you edit your fstab.
When you boot into ubuntu, even though you don't have your ntfs partitions on the desktop, they should be listed in the menu "Places". Simply click on it and it should show up on your desktop.

Now, if you want to leave the same mount point as the ubuntu default, browse to your media folder (or in the terminal type **cd /media** then **ls**) and look at the mountpoint given to your ntfs partition (i.e. folder called backup - in my case).

Now from the terminal, type
```
sudo fdisk -l
```

this will list all your partitions. This is what my looks like:
> Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2550 20482843+ 7 HPFS/NTFS
/dev/sda2 2551 4400 14860125 83 Linux
/dev/sda3 4401 4462 498015 82 Linux swap / Solaris
/dev/sda4 4463 9725 42275016 7 HPFS/NTFS
So from this list, I know I want to mount /dev/sda1 and /dev/sda4

Now, from the terminal type
```
sudo gedit /etc/fstab
```

this will open your fstab. Let's say I wanted to mount my /dev/sda1, then I would add this to the last line:
> /dev/sda1 /media/backup ntfs defaults,umask=007,gid=46 0 1
This will mount /dev/sda1 in the /media/backup folder (as explained above)
simply keep adding lines as you need more partitions. Save your fstab and reboot. You should now get the partitions automatically mounted and the respective icons on your desktop
Another alternative is to add a line to the end of fstab using the UUID option instead of /dev/sda1. You can determine the UUID by using (i.e., for sda1)
```
sudo vol_id -u /dev/sda1
```
so your fstab file will have this line
> UUID=NUMBER_ID /media/backup ntfs defaults,umask=007,gid=46 0 1
where NUMBER_ID is the output from vol_id for your device, i.e.:
> UUID=78980E1B980DD890 /media/backup ntfs defaults,umask=007,gid=46 0 1
instead of
> /dev/sda1 /media/backup ntfs defaults,umask=007,gid=46 0 1
I found this to be more stable/suitable than using the /dev/sda1 option but both work...

---

### Post by tjwoosta on 2008-05-04
> All you have to do is figure out your mount point for you Windows drive. It will be under the /media directory. If you have multiple mounted partitions with generic names (such as disk1) then just go to the /media folder and start clicking to figure out which one it is. Then--if you want to go the icon on the desktop route--right-click on the desktop and select "create launcher." In the dropdown box select "location." Type in the name you want for the icon and then--this is important--where is says location type in "file:///media/name_of_your_mounted_drive" without quotes. You can also change the icon by clicking on the launcher emblem and navigating to a folder with the appropriate icons for your theme (/usr/share/icons).

For AWN go to the Awn Manager under System>Preferences and navigate to the launchers tab. Click Add for a new launcher and using the /media directory for your disk and enter in all the information. The only thing you'd have to do differently is instead of putting file:// before the directory just type in "nautilus /media/name_of_your_mounted_drive" without quotes. Hope that helps. 

thank you, that worked perfectly

that was easy because my windows partition is named Windows

---

### Post by otrojake on 2008-05-04
No problem.  Glad to help.:)

---

### Post by tjwoosta on 2008-05-04
> 
To properly mount the windows partition, you'll need to edit fstab...

i dont understand what do you mean to properly mount it?

it seems to be working fine

---

### Post by otrojake on 2008-05-04
His post was in regards to having Ubuntu automatically mount your Windows partition every time you start up, which is very nice if it's not being done already.  For example, having that launcher on your desktop is only going to work if the partition's already mounted in the media directory.  I guess I took for granted that your Windows partition is automatically being mounted every time you start up.  If it's not it would probably be worth your while to go through the steps victormd outlined above.

---

### Post by tjwoosta on 2008-05-04
> umask=007,gid=46 0 1 

what does this part mean? do i just put exactly what you put?

---

### Post by tjwoosta on 2008-05-05
ok i just did it like that and it worked great thanks guys, but im still interested in finding out exactly what that is for

---

### Post by otrojake on 2008-05-05
The umask and gid both deal with who can read or write to the drive.  Someone please correct me if I'm wrong on this, but I really don't think that the umask and gid options are necessary in this case.

The 0 and the 1 after those two options are for backup and checking of the partition (respectively).  The 0 means that the drive won't be backed up and the 1 means that the partition can be checked for errors with fsck (filesystem check).  Again, someone please correct me if I'm wrong, but since you're dual-booting, Windows will do fine with checking the integrity of the drive, so I don't think you really need to add the option of having fsck check that partition every once in a while.

---

### Post by tjwoosta on 2008-05-05
thanks,

im just going to keep everything the way Victormd suggested, i was just curious as to what that stuff actually did, it sounds like its not a bad idea to just keep it on there

---

