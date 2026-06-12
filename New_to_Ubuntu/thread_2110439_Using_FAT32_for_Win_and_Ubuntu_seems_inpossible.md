---
title: "Using FAT32 for Win and Ubuntu seems inpossible"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by 1002285 on 2013-01-30
I am trying to set up a system with Win 7 and a Ubuntu 12.04 based distro.

As regards using a storage/documents partition for both systems:
ext3 not an option - drivers for reading that system in Windows do not work in Windows 7. Tried several combinations for hours.

decided to use fat32:
1) only possible mount point of fat32 in ubuntu is: /windows
2) changing permissions for /windows - not possible.
(gksu nautilus, sudo chown, etc give the same result - cannot change permissions for this folder).

I am not able to build the system at all this way.

---

### Post by Lars Noodén on 2013-01-30
FAT32 is not really suitable for data storage.  It has way too many shortcomings.

Is there a module that you can add to Windows to get it to read EXT2?  If so, that would be the way to go.

---

### Post by furything on 2013-01-30
Windows natively recognizes that there is a linux partition but you cannot access it.

You can persist with fat32 (or ntfs) but you have to sort the read write permissions to the drive from windows first. Right click and go into security settings. You want everyone as full control (may have to use advanced button cannot remember). You can use a guest account.

I am making the assumption that the windows partition is not encrypted by windows.

You can then make sure you fstab entry is correct with the read write options turned on.

I don't tend to auto mount my drives in fstab but just click and mount from dolphin automatically and read write data across to a 500gb ntfs disk. This method allows me to access the windows drive and system reserved as well.

Edit - You can do this from nautilus as well I just prefer kde

---

### Post by audiomick on 2013-01-30
My "communal" data partition is NTFS. In fact, it was already on the Vista install when I got the laptop, but that is beside the point. I don't know about windows drivers for Linux file systems. There probably are some, but I don't know about them, I get along alright with the NTFS partition.

Bear in mind that no Windows file system supports Linux permissions. I gather it is possible for a mount point to belong to root and not to the user who is logged on. That seemed to be the cause of a problem in a thread I read here. As far as the directories and files on the partition with a windows file system goes, they will not take any linux permissions.

---

### Post by prodigy_ on 2013-01-30
NTFS offers good compatibility. The Linux driver (ntfs-3g) is mature and reliable.

Generally, when I install a dual boot system, I reserve a separate (large) partition for data and format it with NTFS. Then I move **/home/<myusername>/Documents** folder to this partition and replace it with a symlink. In Windows I move **My Documents** folder (easily doable via folder properties). I also move **Downloads**, **Pictures**, **Music**, etc.

This way I see the same data folders in both OS which I find quite handy.

---

### Post by Bucky Ball on 2013-01-30
Don't bother with any dodgy patches or tweaks for getting Windows to read EXT* anything. Just use an NTFS partition. Create it and it should be seen when you open a file manager in Ubuntu. Click to mount, I wouldn't bother about adding it to fstab.

---

### Post by Morbius1 on 2013-01-30
I'm confused by your original post:
> **1002285 said:**
> 1) only possible mount point of fat32 in ubuntu is: /windows
I assume you mean when you did your original install. There was a bug way back when where it limited all windows filesystem types to /windows but I though that was fixed well before 12.04.
> 2) changing permissions for /windows - not possible.
(gksu nautilus, sudo chown, etc give the same result - cannot change permissions for this folder).That is not a bug it's a statement of fact. You can't change linux permissions on a windows filesystem because there aren't any linux permissions bit's to change. You can create a "view" to make it appear that they do however and that is done via fstab.

If you still want a fat32 partition and you want to change permissions on it please post the output of the following commands and we can assist:
```
cat /etc/fstab
```And tell us what ownership and permissions you want to apply to the mounted fat32 partition. 

If it's currently not mounted or not in fstab post the output of this command as well:
```
sudo blkid -c /dev/null
```

---

### Post by Mark Phelps on 2013-01-30
Would avoid using Fat32.  Win7 is designed to use NTFS and I have used that filesystem for sharing data with Linux distros for years now -- ever since the day when you had to go out of your way to install NTFS-3G!

I read about folks having problems with this approach is when they tried to have /home on an NTFS volume -- which clearly will not work because NTFS can't mirror Linux filesystem permissions.

---

### Post by 1002285 on 2013-01-30
OK, thank you for the help.

I could still rather easily format the partition - into ntfs, for example.
But when it was so difficult to get permissions for a fat32 partition - because it is a windows FS - won't there be the same problems with ntfs?

---

### Post by 1002285 on 2013-01-30
I logged on to my Ubuntu again and now seem to be able to write and delete on in the /windows folder, where I also see folders and files that I created while in Windows 7 system. I surely could not do that there the last time.
Here's the output of fstab.

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=9fbc258d-1f6d-4daf-a934-7f9a7803365f /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=4761f45f-8a8e-4c13-80e6-856fd6981a9c /home           ext3    defaults        0       2
# /windows was on /dev/sda7 during installation
UUID=3CF1-FA23  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=a43efe04-3209-49b4-977c-ee5fcbbc4f13 none            swap    sw              0       0

---

### Post by 1002285 on 2013-02-02
> **prodigy_ said:**
> NTFS offers good compatibility. The Linux driver (ntfs-3g) is mature and reliable.

Generally, when I install a dual boot system, I reserve a separate (large) partition for data and format it with NTFS. Then I move **/home/<myusername>/Documents** folder to this partition and replace it with a symlink. In Windows I move **My Documents** folder (easily doable via folder properties). I also move **Downloads**, **Pictures**, **Music**, etc.

This way I see the same data folders in both OS which I find quite handy.

I have formatted that large partition to ntfs now, did it in Windows.
I think I am able to do the necessary linking in Windows to make it work as My Documents.
However, in Ubuntu, I would appreciate help.
1) How to mount the partition? the fstab looks like this:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=9fbc258d-1f6d-4daf-a934-7f9a7803365f /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=4761f45f-8a8e-4c13-80e6-856fd6981a9c /home           ext3    defaults        0       2
# /windows was on /dev/sda7 during installation
UUID=3CF1-FA23  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=a43efe04-3209-49b4-977c-ee5fcbbc4f13 none            swap    sw              0       0

2) How to create the link to make it work as my /home (if that is not yet done in step 1)

3) I guess the ntfs-3g still needs to be installed, too?

---

