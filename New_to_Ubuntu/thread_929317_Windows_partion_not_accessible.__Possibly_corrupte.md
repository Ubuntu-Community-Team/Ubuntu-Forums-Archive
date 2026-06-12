---
title: "Windows partion not accessible.  Possibly corrupted.  Can Ubuntu help?"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by curiousnoob on 2008-09-24
I noticed some problems with games while on the Windows side and decided to try chkdsk but it would never start after restarting the computer.  
It also will not work with the Windows Recovery prompt.  
Anything Ubuntu can do?

---

### Post by curiousnoob on 2008-09-24
When I try to mount it I get this message: 

sudo mount /dev/sda1 mount
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 mount -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 mount ntfs-3g force 0 0

---

### Post by nkri on 2008-09-24
I'm pretty sure this means that you used the power button to kill the system or it died from lack of power, or it just didn't shut down properly.  If you boot into Windows, there'll probably be a message about checking the file system; this will check it for errors and make sure it isn't corrupted.  Let it run, then go back into Ubuntu and see if you can access the partition.

Good luck!
-nkri

---

### Post by curiousnoob on 2008-09-24
> **nkri said:**
> I'm pretty sure this means that you used the power button to kill the system or it died from lack of power, or it just didn't shut down properly.  If you boot into Windows, there'll probably be a message about checking the file system; this will check it for errors and make sure it isn't corrupted.  Let it run, then go back into Ubuntu and see if you can access the partition.

Good luck!
-nkri

The problem is that as soon as I see the Windows logo with the bar at the bottom on bootup the computer immediately shuts down and restarts.  I can't even boot into Safe Mode.

---

### Post by AndrewTheArt on 2008-09-25
Did you try

```
mount -t ntfs-3g /dev/sda1 mount -o force
```

---

### Post by curiousnoob on 2008-09-25
> **AndrewTheArt said:**
> Did you try

```
mount -t ntfs-3g /dev/sda1 mount -o force
```

I get this message: 
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint mount: No such file or directory

---

### Post by AndrewTheArt on 2008-09-25
> **curiousnoob said:**
> I get this message: 
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint mount: No such file or directory

Looks like you need to set the mount folder.

```
mkdir /media/mydisk; mount -t ntfs-3g /dev/sda1 /media/mydisk -o force
```

---

### Post by curiousnoob on 2008-09-25
> **AndrewTheArt said:**
> Looks like you need to set the mount folder.

```
mkdir /media/mydisk; mount -t ntfs-3g /dev/sda1 /media/mydisk -o force
```

When I try that I get this message: 
 mkdir /media/mydisk && mount -t ntfs-3g /dev/sda1 /media/mydisk -o force
mkdir: cannot create directory `/media/mydisk': Permission denied

Am I doing something wrong with this command?

---

### Post by AndrewTheArt on 2008-09-25
> **curiousnoob said:**
> When I try that I get this message: 
 mkdir /media/mydisk && mount -t ntfs-3g /dev/sda1 /media/mydisk -o force
mkdir: cannot create directory `/media/mydisk': Permission denied

Am I doing something wrong with this command?

```
sudo mkdir /media/mydisk && mount -t ntfs-3g /dev/sda1 /media/mydisk -o force
```

As a general principle you can type "sudo" before a command to get super permissions.

---

### Post by curiousnoob on 2008-09-25
> **AndrewTheArt said:**
> ```
sudo mkdir /media/mydisk && mount -t ntfs-3g /dev/sda1 /media/mydisk -o force
```

As a general principle you can type "sudo" before a command to get super permissions.

Sorry, rookie mistake.  I now get this: 
sudo mkdir /media/mydisk && mount -t ntfs-3g /dev/sda1 /media/mydisk -o force
mkdir: cannot create directory `/media/mydisk': File exists

---

### Post by AndrewTheArt on 2008-09-25
> **curiousnoob said:**
> Sorry, rookie mistake.  I now get this: 
sudo mkdir /media/mydisk && mount -t ntfs-3g /dev/sda1 /media/mydisk -o force
mkdir: cannot create directory `/media/mydisk': File exists
That just means that you already created the /media/mydisk directory. 
First go into the mount folder and see if it's been mounted.

```
cd /media/mydisk && ls -l
```If you see a list of your files, your disk is mounted. You can now access it by going to Places -> Computer. In the "Location" bar, type /media/mydisk and press Enter.

If you do not see any output, you probably did not mount the folder. Run

```
mount -t ntfs-3g /dev/sda1 /media/mydisk -o force
```

---

### Post by curiousnoob on 2008-09-25
> **AndrewTheArt said:**
> That just means that you already created the /media/mydisk directory. 
First go into the mount folder and see if it's been mounted.

```
cd /media/mydisk && ls -l
```If you see a list of your files, your disk is mounted. You can now access it by going to Places -> Computer. In the "Location" bar, type /media/mydisk and press Enter.

If you do not see any output, you probably did not mount the folder. Run

```
mount -t ntfs-3g /dev/sda1 /media/mydisk -o force
```

You rock!  
I now have access to the files.  At the very least I can get what I need off of it.  
I will attempt to run chkdsk now.

---

### Post by curiousnoob on 2008-09-25
Even though it is now mounted I cannot seem to run ntfsfix.  I get this: 
ntfsfix /dev/sda1
Refusing to operate on read-write mounted device /dev/sda1.

---

### Post by AndrewTheArt on 2008-09-25
> **curiousnoob said:**
> Even though it is now mounted I cannot seem to run ntfsfix.  I get this: 
ntfsfix /dev/sda1
Refusing to operate on read-write mounted device /dev/sda1.

Try unmounting the drive first - running this program on a mounted drive apparently doesn't work -

```
sudo umount /disk/mydisk
``````
sudo umount /dev/sda1
```Now run the ntfsfix command. By the way, ntfsfix (apparantly) only tells Windows to check the drive for consistency on bootup - it doesen't actually repair the disk on the spot... So restart your computer after all of this and boot into Windows, hopefully a checkdisk will be run.

---

### Post by lisati on 2008-09-25
> **curiousnoob said:**
> When I try to mount it I get this message: 

sudo mount /dev/sda1 mount
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported


I've only ever had this kind of error message pop up within Ubuntu if Windows hasn't shut down properly. The easiest "cure" I know of is to restart Windows and let it start up fully, but that assumes that Windows "wants" to start up! 

Some of the previous ideas suggested look promising.

EDIT: Forgot to say that if Windows manages to start properly, shut it down properly with the Start->Turn off computer menu option and don't touch the power switch, otherwise the Ubuntu error message will persist.

---

### Post by AndrewTheArt on 2008-09-25
Yep, that would be a good idea, but for now the -force command gets the job done. (In fact I took it for granted that he understood the reason for that error message, but still wanted to mount be force for whatever reason :P)

---

### Post by curiousnoob on 2008-09-25
> **AndrewTheArt said:**
> Try unmounting the drive first - running this program on a mounted drive apparently doesn't work -

```
sudo umount /disk/mydisk
``````
sudo umount /dev/sda1
```Now run the ntfsfix command. By the way, ntfsfix (apparantly) only tells Windows to check the drive for consistency on bootup - it doesen't actually repair the disk on the spot... So restart your computer after all of this and boot into Windows, hopefully a checkdisk will be run.

OK, so when I unmount it I get the following message: 
ntfsfix /dev/sda1
Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.

The problem is I cannot start windows to run chkdsk.

---

### Post by AndrewTheArt on 2008-09-25
> **curiousnoob said:**
> OK, so when I unmount it I get the following message: 
ntfsfix /dev/sda1
Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.

The problem is I cannot start windows to run chkdsk.

Add a sudo to the front of the command and see what happens

```
sudo ntfsfix /dev/sda1
```

If that fails, I'm pretty much at a loss.

---

### Post by AndrewTheArt on 2008-09-25
As a general note, the TestDisk program can help you repair corrupted partitions.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by curiousnoob on 2008-09-25
> **AndrewTheArt said:**
> Add a sudo to the front of the command and see what happens

```
sudo ntfsfix /dev/sda1
```

If that fails, I'm pretty much at a loss.

Putting the sudo in front worked but when I attempted to boot to xp the computer still restarts as soon as the XP splash screen appears.  
I put in the original XP disc and under the recovery dos prompt typed in chkdsk and got this response:

This partition contains unrecoverable errors

---

### Post by dido__15 on 2008-09-25
It seems you have the good old problem where windows decides to kill itself. We run into this problem at work all the time. When starting windows you should have the option to load the last known good configuration, safe mode or start windows normally, starting normally will just keep restarting (exactly 27 seconds each time, time it ;). If you select last known good save it will just BSOD about a memory parity error and die. If you're lucky, before you select last known good save, swap the memory modules around in their sockets. Note i said if you're lucky, it rarely actually works. Your best bet is to back up anything you need through ubuntu and format and reinstall your windows partition. Sorry for the bad news.

---

