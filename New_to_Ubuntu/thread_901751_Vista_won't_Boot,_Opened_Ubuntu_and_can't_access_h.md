---
title: "Vista won't Boot, Opened Ubuntu and can't access hard drive"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Sweep on 2008-08-26
This morning my Vista wouldn't boot and so I used the Ubuntu 7.10 to start my computer. I had been wanting to switch to LINUX for a long time so this seems like the time. The problem is that when I click on the hard drives it says they are not mounted. 

Could someone walk me through the way to mount these hard drives. I have done some preliminary research but the answers were all above my technical expertise. I don't have any Linux experience.

---

### Post by WRDN on 2008-08-26
If the drive cannot be mounted in Ubuntu, then this may be because of an unclean shutdown in the past, when the OS could not unmount the drive properly.

To mount the drive, open the Terminal, and first type:

```
sudo fdisk -l
```

From the output to this, you will be able to identify which partition Vista is on. The devices will be named /dev/sdaN or /dev/hdaN, where N represents a number.

Now, create the mount point by typing:

```
sudo mkdir /media/vista
```

You can replace the word "vista" if you wish.

Finally, type:

```
sudo mount /dev/[device] /media/vista
```

If this does not work, you can force mount the partition by typing:

```
sudo mount /dev/[device] /media/vista -o force
```

---

### Post by jbrown96 on 2008-08-26
First you need to find out which partition and drive Vista is on. If you only have one drive, you do not need to repeat the following step. Do all of these steps from a terminal
1. fdisk
```
sudo fdisk -l /dev/sda
```
This will show you all the partitions on the first hard disk. If you have multiple drives, repeat this process (changing sda to sdb, sdc, sdd and so on) until you have the partition maps for all the drives. If you only have one Windows partition (default) then you should come across an entry that has a "*" in the "boot" column and says something/NTFS in the system column. Remember this partition name. It will be of the format /dev/sda1 (note that the "a" and "1" will vary). 
2. Create a directory in which to mount the windows partition
```
sudo mkdir /media/windows
```
You can change "windows" to another name but will also have to change the following direction to the same name
3. Mount
```
sudo mount -t auto /dev/sda2 /media/windows
```
obviously change "/dev/sda2" to the partition number that was determined in step 1 and "/media/windows" if you changed the location in step 2. 
You may have trouble with permissions too. Use ```
sudo chown -R USERNAME:USERNAME /media/windows
``` where USERNAME is your username (note the colon and that is typed twice.)
If windows did not shut down correctly, you may need to force mount. ```
sudo mount -t auto /dev/sda1 /media/windows -o force
```
Now you can browse to /media/windows and check out your files.

---

### Post by Sweep on 2008-08-26
Thank you both...I did what you suggested and this came up:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /media/windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /media/windows ntfs-3g defaults,force 0 0


Now what I am wondering is there a consequence to 'forcing'...is there any harm that can come to the Windows system or my data files...I just wanted to check before doing it...

---

### Post by Sweep on 2008-08-26
Also you both offered different code to use to 'force' it...and the response I received offered a 3rd choice...is there a difference between them and which is better to use?

---

### Post by WastePotato on 2008-08-26
I had this problem with XP about a week ago and I forced a mount. It didn't destroy any of my files, but my OEM's restore disk did. :(

I'm not encouraging or discouraging you to do it, but if you do, you better backup those files _quick_ in case anything happens.

---

### Post by Sweep on 2008-08-26
The problem is I can't access them. Vista won't boot. I don't know why...I do have a back-up on an external hard drive but its a couple months old and there is some new work there.

---

### Post by WastePotato on 2008-08-26
Have you tried using WinRE to repair the startup files? 
If you can't access even that, do you have an original Vista DVD?

---

### Post by Sweep on 2008-08-26
I ran it a couple of times and it didn't do anything. Now it doesn't come on anymore....The VISTA came with the computer without the disks...

---

### Post by WastePotato on 2008-08-26
Yeah, a lot of OEM's do that. They're too stingy to provide Vista DVDs.

Your best bet is to force the drives to mount, transfer the files to your other HD and then reinstall Vista.


What actual error message appears? Is it a Blue Screen? Could you provide us with an error code, if any?

---

### Post by Sweep on 2008-08-26
[COLOR="Blue"]Ok I chose the first suggestion to do the 'force':[/COLOR]

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/vista -o force

This came up:

$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.

[COLOR="Blue"]I checked to see if I could access the drive and it said no...[/COLOR]

The details of the Failed to Mount Screen said the resource was temporarily unavailable.Error opening partition device.

---

### Post by Sweep on 2008-08-26
WP,

In  regards to the error screen, are you referring to Vista not working or Getting the hard drive to mount?

---

### Post by Sweep on 2008-08-26
Well I tried all 3 'force' suggestions and each one was not successful.

The message that is there presently when I attempt to 'mount'

The last message was CANNOT MOUNT VOLUME

Unable to mount the volume 'Enterprise' (my C Drive)

ntfs_attr_pread: ntfs_pread failed:input/output
error Failed to read NTFS $Bitmap: Input/output 
error Unmounting /dev/sda2

Any suggestions on how to proceed in the quest for the Enterprise?

---

### Post by WRDN on 2008-08-27
I'm guessing you tried the suggestion given by the OS:

```
mount -t ntfs-3g /dev/sda2 /media/windows -o force
```

It's very odd that you can't mount the partition, and this leads me to believe that, before you started any of this, the NTFS partitions filesystem was already corrupted. If you can't reinstall Vista, then you may have to start from scratch and wipe it from the HDD then install again [though this is the last solution].

As a possible alternative to this, are you able to boot into Vista's recovery mode? If so, open the command prompt (cmd) and type:

```
CHKDSK /f
CHKDSK /r
```

This will try to find and repair any problems. You may also be prompted to schedule a startup check. If so, allow this to occur. If it does not prompt you, then you may type:

```
CHKNTFS
```

Are you able to access System Restore in any way, to you can revert the drive to a previous state?

---

### Post by Sweep on 2008-08-27
I couldn't find the command prompt in set up utility (f2)....I did get suggestion to do an f8 and gained access to the path to command prompt but wasn't able to get the prompt...instead the drivers loaded and it stopped in the middle of that part of the process.

Nothing from the f8 page worked including restoring the system to when it last booted properly (that would have been sweet).

The only think that is working is Ubuntu except that I can't access my hard drives. 

I do have a couple of Recovery Discs I made a while back from a Toshiba program but it seems they would be used if I have given up trying to access the hard drives.

Does anyone have nay other suggestions in regards to "mounting' the hard drive. Any direction is hugely appreciated....

---

### Post by WastePotato on 2008-08-27
> I did get suggestion to do an f8 and gained access to the path to command prompt but wasn't able to get the prompt...instead the drivers loaded and it stopped in the middle of that part of the process.

It sounds like one of the system's vital files has gone corrupt or missing. Do you have any friends who have a Vista DVD?

---

