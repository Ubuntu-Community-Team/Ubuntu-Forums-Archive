---
title: "External Hard drive name changes on reboot"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by john225 on 2014-05-14
I am having an issue with the names of my external hard drives changing after some reboots.  For instance my external hard dive was called MediaExternalDrive.  On two occasions now after a reboot it has changed to MediaExternalDrive1 and MediaExternalDrive2. Attempts to open the original drive produce this error message -  Error opening directory '/media/john/MediaExternalDrive': Permission denied

This then requires me to change any programs such as back up programs or samba shared file paths to the "new" drive.

I have attempted to attach a screenshot of the media folder shoing multiple renamed drives.

I have a fresh install of lubuntu 14.04LTS 32 bit with a dual boot to windows vista.  It is an older machine and performs very well with lubuntu however this issue causes quite a bit of work each time it happens.

Thanks for any help

---

### Post by capscrew on 2014-05-15
> **john225 said:**
> I am having an issue with the names of my external hard drives changing after some reboots.  For instance my external hard dive was called MediaExternalDrive.  On two occasions now after a reboot it has changed to MediaExternalDrive1 and MediaExternalDrive2. Attempts to open the original drive produce this error message -  Error opening directory '/media/john/MediaExternalDrive': Permission denied

This then requires me to change any programs such as back up programs or samba shared file paths to the "new" drive.

I have attempted to attach a screenshot of the media folder shoing multiple renamed drives.

I have a fresh install of lubuntu 14.04LTS 32 bit with a dual boot to windows vista.  It is an older machine and performs very well with lubuntu however this issue causes quite a bit of work each time it happens.

Thanks for any help
I believe this is a Lubuntu specific problem.  Read all the posts in [this bug report ]("https://bugs.launchpad.net/ubuntu/+source/biosdevname/+bug/1293633").  Note posts #5 and later.

---

### Post by dannyboy79 on 2014-05-15
how are you mounting the external drive? it sounds like you're just plugging it in and hoping it gets mounted in the same spot again. in theory it should but it sounds like the shutdown isn't properly unmounting your drive so the system thinks there's already something mounted at MediaExternalDrive when it tries to mount it upon restart so it'll mount it at MediaExternalDrive1

if you want it always in the same spot I highly suggest you use fstab and mount it using it's UUID to where ever you want it mounted. if /media/john/MediaExternalDrive is the folder you always want it mounted at that's fine. just change it's permissions to allow you access to it.

---

### Post by john225 on 2014-05-15
Thanks folks for the replies.  I will read the bug report, however, dannyboy may have it.  I'll need to read up on fstab and permissions.  I have just plugged these drives in and I thought I had mounted them simply by opening the file manager and clicking on them which gave me the eject button symbol beside them.  I also had to format the disks to use them and had mounted and unmounted them using gparted which required a mount and un-mount but that was before the were used with this install.
  
I would like them to be in the same spot all the time.  This is my third week using Lubuntu and my first open source experience so I'm on quite a bit of a learning curve having come from windows.  I'm not afraid of the command line but need some time to get used to how it all works and which programs to get me there.

I'll try and figure out fstab and see if that does it.

Accepting any advice you can give

Cheers

---

### Post by john225 on 2014-05-15
Ok if i understand this fstab is a configuration file that would need to be edited to mount both external hard drives on boot up.

I'd need to follow the steps found here [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
 
I am able to get my uuid's for both devices using blkid

/dev/sdh1: LABEL="MediaExternalDrive" UUID="26FD21DB4C7B918E" TYPE="ntfs" 
/dev/sdi1: LABEL="MediaBackup" UUID="7B6E43EC7E590CAF" TYPE="ntfs"

would my mount point be /media/john/MediaExternalDrive for the first hard drive?

file type is nfts

next would be options dump and pass, however,  I am unsure what I would need to include here. 

Question,  what should i be reading as a beginner to better understand how this all works?   At this point I feel rather overwhelmed.  

Thanks again for any help I can get on how to edit fstab for my set up.

Regards

---

### Post by dannyboy79 on 2014-05-16
> **john225 said:**
> 

would my mount point be /media/john/MediaExternalDrive for the first hard drive?

your mount point can be anywhere you want. that previous location is just where the system auto-mounts external drives. everyone will tell you something different, it's totally a preference thing. some say to leave /media/ alone as that's where external removeable drives get auto-mounted. some would say to create a folder within /mnt/ and mount it there. If you do that permissions become an issue due to /mnt/ being owned by root. if it were me i would just create a folder within your /home/john/ directory. you can create any named folder you want within /home/john/, whatever folder you create would be the mount point for your hard drive 1 in your fstab

in linux there's mount points/folders which are where a partition is mounted to show that partitions contents. Windows does it with drive letters, linux does it with folders/mount point.

i don't use NTFS myself so I am not sure what fstab options you want for a ntfs formatted drive, i would just google ntfs fstab entry and i'm sure you'll find something helpful.

---

### Post by john225 on 2014-05-23
Thanks very much.
 
I was able to edit fstab and mount these drives permanently on boot up.

I used this to help.  Nice and straight forward.  [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

My last question before I mark this as solved is how do i clean up the references to the other drives in the media folder. I have a folder /media/john that has MediaExternalDrive1 ect.  I have permanently mounted to /media/MediaExternalDrive.

---

### Post by sotiris2 on 2014-05-23
If and only if you are certain that it is not mounted there. 
```
sudo rm -r /media/john/MediaExternalDrive1
```

---

### Post by john225 on 2014-05-23
Seems easy enough.  Is there a terminal command to show all mounted drives?  I would definitely like to be certain.

---

### Post by CharlesA on 2014-05-23
> **john225 said:**
> Seems easy enough.  Is there a terminal command to show all mounted drives?  I would definitely like to be certain.

```
mount
```

---

### Post by steeldriver on 2014-05-23
If you use rmdir instead of rm -r it will only remove if empty

```

sudo rmdir /media/john/MediaExternalDrive1

```

```

NAME
       rmdir - remove empty directories

SYNOPSIS
       rmdir [OPTION]... DIRECTORY...

DESCRIPTION
       Remove the DIRECTORY(ies), if they are empty.

```

---

