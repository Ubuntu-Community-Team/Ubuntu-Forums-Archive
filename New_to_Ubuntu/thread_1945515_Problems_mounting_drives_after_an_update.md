---
title: "Problems mounting drives after an update"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by Bean12345 on 2012-03-23
Prior to doing a recent update I was having no problems and all my drives mounted fine on startup. After updating I found my drives vanished and that my fstab file had been almost completely re-written. I did some fiddling and now have my hard drives back.

My problems now are that my dvdram drive wont mount and there is some reference to mount point 0 not existing.

Here are the contents of my fstab file

```
UUID=B850B07F50B045C2 /media/New ntfs-3g defaults,rw,auto,user,exec,locale=en_GB.UTF-8 0 0
UUID=9CD4B767D4B741F6 /media/sdb1 ntfs-3g defaults,rw,auto,user,exec,locale=en_GB.UTF-8 0 0
/dev/sda2 /media/New_Volume ntfs
defaults,rw,auto,user,exec,locale=en_GB.UTF-8 0 0
UUID=da1f56bc-ea3d-4c3c-950a-cac44f5fb126 /swap swap rw 
/dev/sg0 /media/d udf,iso9660  
defaults 0 0
```Hope you guys can help please

---

### Post by ajgreeny on 2012-03-23
Not sure I can specifically help without more info, but you should not be using /dev/sda2 in your fstab file to name a partition but the UUID as in the first two lines and the swap line of the file.  This can save problems if the system makes changes to device names, which can sometimes happen with no input from yourself.  Did the system make those changes, or was the old fstab also using /dev/sdx# naming?

/dev/sg0 is probably OK as I assume that is your dvdram drive.  However, I assume that the dvdram drive system handling must be different from a normal dvd drive, as a dvd is not listed in fstab any more.

See what happens if you comment out the /dev/sg0 line with a # at the start, then use command ```
sudo mount -a
``` to see if any error messages appear.  If no errors, try using the dvdram drive, as I admit to knowing nothing about the way they are handled in ubuntu.

---

### Post by Bean12345 on 2012-03-23
I have only used the /dev tags because I'd forgotten the command to find the UUID's for drives. I have unfortunately already tried the # to rem out the /dev/sg0 line and it gives me 

```
mount point 0 does not exist

```

---

### Post by ajgreeny on 2012-03-23
For your info the command for finding UUID is ```
blkid -c /dev/null
```

I have no idea why the system says that mount point 0 is not available as nothing seems to point to it in fstab, and if the /dev/sg0 line is commented out it can not be that drive at fault.

Very odd!  Sorry, but I am baffled.

---

### Post by jerome1232 on 2012-03-23
edit: nvm

---

### Post by jerome1232 on 2012-03-23
ui> **Bean12345 said:**
> Prior to doing a recent update I was having no problems and all my drives mounted fine on startup. After updating I found my drives vanished and that my fstab file had been almost completely re-written. I did some fiddling and now have my hard drives back.

My problems now are that my dvdram drive wont mount and there is some reference to mount point 0 not existing.

Here are the contents of my fstab file

```
UUID=B850B07F50B045C2 /media/New ntfs-3g defaults,rw,auto,user,exec,locale=en_GB.UTF-8 0 0
UUID=9CD4B767D4B741F6 /media/sdb1 ntfs-3g defaults,rw,auto,user,exec,locale=en_GB.UTF-8 0 0
[COLOR="Red"]defaults,rw,auto,user,exec,locale=en_GB.UTF-8 0 0[/COLOR]
UUID=da1f56bc-ea3d-4c3c-950a-cac44f5fb126 /swap swap rw 
/dev/sg0 /media/d udf,iso9660  
defaults 0 0
```Hope you guys can help please

Is that actually a newline? Make sure the line highlighted in red is in fact on the same line above it, I "feel" like that is the issue, it thinks your trying to mount the "device" defaults,rw,auto....etc at 0 as fstype 0

edit: Actually on a second look, it's just hanging out by itself, needs to be commented out.

---

### Post by oldfred on 2012-03-23
Your entries in fstab look like they are on two lines, which is not correct. 

> /dev/sda2 /media/New_Volume ntfs
[COLOR=Red]defaults,rw,auto,user,exec,locale=en_GB.UTF-8 0 0[/COLOR]
UUID=da1f56bc-ea3d-4c3c-950a-cac44f5fb126 /swap swap rw 
/dev/sg0 /media/d udf,iso9660  
[COLOR=Red]defaults 0 0[/COLOR]> /dev/sda2 /media/New_Volume ntfs defaults,rw,auto,user,exec,locale=en_GB.UTF-8 0 0
UUID=da1f56bc-ea3d-4c3c-950a-cac44f5fb126 /swap swap rw 
/dev/sg0 /media/d udf,iso9660  defaults 0 0

# Make permanent mount point (unmount if already mounted):
sudo mkdir /media/Data2
# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

---

### Post by Bean12345 on 2012-03-23
ok guys most were on the same line i just didn't have my editor maximised when i copied the code, but now added most of the proper UUID's it now looks like this

```
UUID=B850B07F50B045C2 /media/New ntfs-3g defaults,rw,auto,user,exec,locale=en_GB.UTF-8 0 0
UUID=9CD4B767D4B741F6 /media/sdb1 ntfs-3g defaults,rw,auto,user,exec,locale=en_GB.UTF-8 0 0
UUID=9038B7A038B783AE /media/New_Volume ntfs defaults,rw,auto,user,exec,locale=en_GB.UTF-8 0 0
UUID=da1f56bc-ea3d-4c3c-950a-cac44f5fb126 /swap swap rw 
/dev/sg0 /media/d udf,iso9660 defaults 0 0
```at terminal: sudo mount -a gives me 

```
/dev/sg0 is not a block device

```note I still do not know how to obtain the UUID for the DVDRAM drive as blkid just lists hard drives it would seem

---

### Post by ranger1021994 on 2012-03-23
I think ntfs-3g is a nice tool that lets you auto-mount drives at boot....
try it.... 
:) :)

---

### Post by Bean12345 on 2012-03-23
yes ranger its a nice tool and it did solve a problem i had a while back but current issue is with dvdram drive and what looks like a swap file partition, neither of which are ntfs, but thanks for your input :)

---

### Post by jerome1232 on 2012-03-23
Sounds like sg0 isn't a block device, are you positive that's your dvd-ram device?

```
cat /var/log/dmesg | grep dvd-ram
ll /dev/sg0
```

edit: I also wanted to note I have a dvd-ram drive, it does not have an fstab entry, it just mounts presumably via udev when I insert a disc.

---

### Post by ajgreeny on 2012-03-23
Your swap line does also look very odd.  It should be 
```
UUID=da1f56bc-ea3d-4c3c-950a-cac44f5fb126 none            swap    sw              0       0
```

---

### Post by Bean12345 on 2012-03-23
My apologies if I'm being dense but it would appear that my dvdram drive does mount if I put a disk in it. Is this normally the case ie the drive is invisible until used, maybe my too many years under windows rule. I switched to ubuntu for faster boot time and performance and it has so far delivered on both counts. I just need to learn the tech stuff

---

### Post by Bean12345 on 2012-03-23
Many thanks guys

Jerome1232 yes you are right the line for dvdram isn't needed and it mounts on request when discs are inserted

Ajgreeny the line you supplied works perfectly thank you

---

### Post by jerome1232 on 2012-03-23
whoops, fixed my command above, forgot to add the path to dmesg.


Glad you got everything working!

---

