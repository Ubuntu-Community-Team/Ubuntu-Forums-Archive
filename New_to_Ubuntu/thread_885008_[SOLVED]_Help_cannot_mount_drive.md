---
title: "[SOLVED] Help: cannot mount drive?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by BeccyBug on 2008-08-09
Firstly, very sorry if the answer to this is elsewhere - I installed ubuntu 7.1 about 3 hours ago, and have been searching for the answer to this ever since, so any help is much appreciated.

Since this is a 'spare' puter, I just installed ubuntu, without leaving windoze on here.  I have a spare hdd, that I keep backups on, that I now can't access.  First off it tells me I need administrator rights to access it, although my login password works for this.  After that, it tells me:

unable to mount the volume 'Backup'
$LogFile indicates unclean shutdown (0, 0) failed to mount '/dev/hdb1' operation not supported, mount is denied because NTFS is marked to be in use

It goes on to suggest a couple of actions - one I can't do as I uninstalled windoze, the second (at my own risk) to use the following in the terminal:
mount -t ntfs-3g/dev/hdb1/media/Backup -o force
results in a whole page of explanations that I can't even begin to understand right now, and the third option, to add a line in the /etc/fstab file just didn't work (and that took some messing about and renaming of files, and backing up of files, which I have restored all to original again)

Sorry for the long winded explanation - hope it makes some sense to someone who can help!!

Thanks in advance

Beccy

---

### Post by sisco311 on 2008-08-09
open a terminal(Applications -> Accessories -> Terminal) and
copy/paste this in:
```
sudo mount -t ntfs-3g /dev/hdb1 /media/Backup -o force
```press Enter. type your password and press Enter again(there is no visual feedback when you type your password).

Your partition should be mounted in the /media/Backup directory.

---

### Post by BeccyBug on 2008-08-09
Thanks for that i it came back with a warning 
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/Backup: No such file or directory
FUSE mount point creation failed
Unmounting /dev/hdb1 (Backup)

but it was there, like you said it would be

Many thanks  :KS

---

### Post by user_of_linux on 2008-09-17
I tried for days to get my freeagent to mount with no success.  I tried all of the help tips that were posted but still no go.  Then I got the error message that you posted.  

Solution that worked for me:  Log into windows, Click on the little icon that says safely remove hardware.  Select your back up disk.  Once it says you can now remove go ahead and unplug the USB cord from the computer.  Log into Linux then plug your back up disk back into the computer and it should pick it up.  If you have trouble get your back up to remove on the windows side (can not stop dive it is in use) just unplug it then plug it back up and follow the steps above.  Hope this helps.  It worked for me.

---

