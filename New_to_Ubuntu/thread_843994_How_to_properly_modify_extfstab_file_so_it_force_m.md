---
title: "How to properly modify /ext/fstab file so it force mounts my external HD"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by KuroYoma on 2008-06-29
I am trying to mount the second partition of an external HD.  I get a mounting problem everytime i plug it in.  I have tried lots of stuff and have tried modifing the fstab file myself but it errors everytime.  I am running 8.04 and would like to know what would be the proper way to modify the file 

This is the original:  The bold is what i add
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a453e473-6f4b-4102-8841-4320b0d4bd50 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2a252cb0-198e-4367-bb41-5721b61ad607 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
**_[COLOR="Red"]/dev/sdb2       /media/SG       ntfs-3g force           0       0[/COLOR]_**

can anyone help plz

reminder i am looking to force mount the partition.

---

### Post by svk on 2008-06-29
After you connect the external hard drive, wait a couple seconds, open the terminal and type in **dmesg | tail -n 30**.  This will print the last 30 lines of the kernel log.  Copy what that says -- that would help us in fixing the problem.

---

### Post by LuisGMarine on 2008-06-29
Sweet, lets figure out how to find an answer for your problem. 

By the looks if it your /etc/fstab is a mess.  At leas the part where you tried to edit it, but hey no problem!  That's what Linux is for, learning from breaking things!

I like to do things completely proper.  I like to edit files and edit them in a way where it looks like pros did it.  So that is what we are going to do for your partition.

First fire up a terminal window and type in this command, post the output of it:
```

sudo blkid
```

Look for the line that the disk and partition number you want to add.  In this case look for *dev/sdb2*

keep it open and fill in the info highlighted here with the values that you get from running *sudo blkid*

This is what the entry should resemble:

```
# /dev/sdb2
[COLOR="Red"]UUID=a453e473-6f4b-4102-8841-4320b0d4bd50[/COLOR] [COLOR="Blue"]/[/COLOR] [COLOR="Lime"]ext3[/COLOR] defaults,errors=remount-ro 0 1
```

Substitute the corresponding data with the outputs from sudo blkid

Red - UUID
Blue - mount point ( You can always redirect where you want it to be mounted)

       For example make a directory in /media called /external_hdd_p2
       with sudo mkdir /media/external_hdd_p2

green - substitute the correct file system.

hope this helps.

---

### Post by KuroYoma on 2008-06-29
/dev/sda1: UUID="a453e473-6f4b-4102-8841-4320b0d4bd50" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="2a252cb0-198e-4367-bb41-5721b61ad607" 
/dev/sdb1: UUID="8dc03886-f437-495f-aad6-b99edfef9081" TYPE="ext3" 
[COLOR="Red"]**/dev/sdb2: UUID="E2FC6C96FC6C66AF" LABEL="STORAGE GOD" TYPE="ntfs"**[/COLOR] 
/dev/sdb3: UUID="607C87A47C877396" TYPE="ntfs" 

this is the results for "sudo blkid", the red is the one i want to force
I tried what u said and it didn't load at all.  I waited for 15 minutes or so

and this is for dmesg|tail -n 30

[ 2025.658199] sd 16:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 2025.658826] sd 16:0:0:0: [sdb] Write Protect is off
[ 2025.658832] sd 16:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 2025.658837] sd 16:0:0:0: [sdb] Assuming drive cache: write through
[ 2025.658844]  sdb: sdb1 sdb2 sdb3
[ 2028.636936] sd 16:0:0:0: [sdb] Attached SCSI disk
[ 2028.637019] sd 16:0:0:0: Attached scsi generic sg2 type 0
[ 2055.057375] usb 5-1: USB disconnect, address 16
[ 2055.598271] usb 5-5: new high speed USB device using ehci_hcd and address 17
[ 2055.629160] usb 5-5: configuration #1 chosen from 1 choice
[  948.536423] scsi17 : SCSI emulation for USB Mass Storage devices
[  948.540954] usb-storage: device found at 17
[  948.540958] usb-storage: waiting for device to settle before scanning
[ 2056.252014] usb-storage: device scan complete
[ 2056.291147] scsi 17:0:0:0: Direct-Access     SAMSUNG  HD501LJ               PQ: 0 ANSI: 2 CCS
[ 2056.293285] sd 17:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 2056.302382] sd 17:0:0:0: [sdb] Write Protect is off
[ 2056.302391] sd 17:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 2056.302396] sd 17:0:0:0: [sdb] Assuming drive cache: write through
[  948.820263] sd 17:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[  948.820889] sd 17:0:0:0: [sdb] Write Protect is off
[  948.820893] sd 17:0:0:0: [sdb] Mode Sense: 00 38 00 00
[  948.820895] sd 17:0:0:0: [sdb] Assuming drive cache: write through
[  948.820898]  sdb: sdb1 sdb2 sdb3
[  948.821606] sd 17:0:0:0: [sdb] Attached SCSI disk
[  948.821645] sd 17:0:0:0: Attached scsi generic sg2 type 0
[  949.501305] kjournald starting.  Commit interval 5 seconds
[  949.513667] EXT3 FS on sdb1, internal journal
[  949.513674] EXT3-fs: recovery complete.
[  949.513679] EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by KuroYoma on 2008-07-01
Well i am still not sure how to modify the fstab file but i learned how to properly do it in the terminal.

sudo mount -t ntfs-3g /dev/sdb2 /media/SG -o force

this seems to work great.  but i would still like to know if anyone knows how to modify the fstab file so i don't have to type this in everytime i switch my external HD from one HD to another like from work to school to laptop to desktop.

---

### Post by Yuki_Nagato on 2008-07-01
I am not experienced enough to be modifying fstab files, but I would recommend creating a launcher with that terminal command until someone more knowledgeable comes around.

---

### Post by ChameleonDave on 2008-07-01
Based on what mine looks like, your fstab should have a line like this:

```
LABEL="STORAGE GOD"  /media/SG  ntfs-3g  defaults,umask=007,gid=46   0   1
```

---

### Post by KuroYoma on 2008-07-01
ok,  i feel pretty silly but how do i create the launcher, because not only this but that sounds like a very useful tool.

And ChameleonDave, do you know if this will cause it to force mount the HD?

---

### Post by ChameleonDave on 2008-07-01
> **KuroYoma said:**
> ok,  i feel pretty silly but how do i create the launcher, because not only this but that sounds like a very useful tool.

And ChameleonDave, do you know if this will cause it to force mount the HD?

I don't know anything about force mounting.  It sounds risky.  Why is it necessary?

Here is a launcher that will work in KDE and perhaps GNOME.

```

Exec=mount -t ntfs-3g /dev/sdb2 /media/SG -o force
GenericName=This will mount Storage God
Icon=drive-removable-media-usb
Name=Mount Storage God
StartupNotify=true
Terminal=false
Type=Application
X-DBUS-StartupType=none
X-KDE-SubstituteUID=true
X-KDE-Username=root

```

Paste that into a text editor, and save it as "Mount.desktop".  Put it on your desktop.

---

### Post by voteforpedro36 on 2008-07-01
Not sure if I'm right, but this is what you should put in your fstab, I believe.

```
# /dev/sdb2, this is a comment but every other line has one too
UUID=E2FC6C96FC6C66AF /media/SG ntfs defaults 0 0
```

That won't force mount it, but I don't see why you should have to. That should mount it in the folder /media/SG (if that folder already exists, but you mounted it there earlier). Hope it works for you.

PS: That UUID looks different than the other ones in the fstab, I don't know why though.

---

### Post by ChameleonDave on 2008-07-01
> **voteforpedro36 said:**
> 

```
# /dev/sdb2, this is a comment but every other line has one too
UUID=E2FC6C96FC6C66AF /media/SG ntfs defaults 0 0
```


Why use a UUID instead of a LABEL?  Surely labels are easier to read (and usually shorter)?

---

### Post by voteforpedro36 on 2008-07-01
> **ChameleonDave said:**
> Why use a UUID instead of a LABEL?  Surely labels are easier to read (and usually shorter)?

No reason, do they do the same thing (I'm not sure on these things)? And in the first place, where the TS edited fstab, I think had he replaced ntfs-3g with just ntfs, and added a "defaults," before "force", so it read "defaults,force" (if force is an option in fstab, which I am not sure of), it should have been fine.

---

### Post by KuroYoma on 2008-07-01
I need to force because with windows at work and school it "activates" a partition and then when i connect it to Ubuntu it reads the partition as busy, occupied, or not athorized.  So i force it in the terminal and it deactivates the windows in the way and mounts it.  Another example of windows being a pest in any way possible. 

For both chameleon and voteforpedro i have tried both and because it is not set to force it comes up with the mounting error.

---

### Post by voteforpedro36 on 2008-07-01
> **KuroYoma said:**
> I need to force because with windows at work and school it "activates" a partition and then when i connect it to Ubuntu it reads the partition as busy, occupied, or not athorized.  So i force it in the terminal and it deactivates the windows in the way and mounts it.  Another example of windows being a pest in any way possible. 

For both chameleon and voteforpedro i have tried both and because it is not set to force it comes up with the mounting error.

Question: If you "Safely Remove Hardware" in Windows, does this error in Ubuntu go away? I've heard that if you don't unmount it in Windows it won't mount in Linux...

---

### Post by Yuki_Nagato on 2008-07-01
Are we using GNOME?  Right-click on a panel, and find the command to create a launcher.  The GUI will walk you through the steps.

---

### Post by ChameleonDave on 2008-07-01
> **KuroYoma said:**
> I need to force because with windows at work and school it "activates" a partition and then when i connect it to Ubuntu it reads the partition as busy, occupied, or not athorized.  So i force it in the terminal and it deactivates the windows in the way and mounts it.  Another example of windows being a pest in any way possible. 


That's an NTFS problem.  If you could change the filesystem to FAT or Ext3, it would work much better.

If you want to stick with evil NTFS, try doing a disk check on it in Windows, safely unmount it from Windows, and then try to mount it on Linux.

I don't believe it is possible to force-mount in fstab.  The whole point about forcing is that it is not normal, and should not be done automatically.  It ought only to happen if a user with admin privileges specifically types "force" on the command line.

---

### Post by KuroYoma on 2008-07-02
I use NTFS for game dvd that are larger than 4.1 gigs.  The other formats does not support single files larger and some of the iso files are larger than that.  The other reason i need windows is for game compatibility.  I do understand what you mean about the force command.  The only reason i thought it might is because when the mount error comes up and it gives possible fixes one is the terminal the other was putting a force command in the fstab file.  

i really appreciate all of everyones help. thanks

and voteforpedro yes it does but my schools computer let me use the external HD but won't let me "Safely Remove ..." because i don't have i don't have administrator privileges.  Makes no sense i know.

---

### Post by bab1 on 2008-07-02
The man page will explain all the options.

Try
```
man fsab
```

The entries will be:
the block device -- the mount point -- the file system type -- mount options -- diagnostic options -- fsck passes (checking the file system)

The following should work:

```
/dev/sda2 /media/SG ext3 defaults 0 2

```

i understand that you are using this partition with Windows.  You should properly "unmount" the drive.

Remember the fstab file just lists all the "mount" commands you are using, so read the man pages for "mount" for complete understanding.  That is:
```
man mount
``` and ```
man umount
```

-BAB1

---

### Post by kevmitch on 2008-07-02
I would generally agree, that you don't want to force mount something by default unless you absolutely have to. The reason being that you might loose your data if you end up writing to a disk that is in an inconsistent state due to an unclean dismount. 

If you are willing to accept that risk and neither

```

/dev/sdb2 /media/SG ntfs-3g force 0 0

```

or

```

/dev/sdb2 /media/SG ntfs-3g defaults,force 0 0

```

do it for you, then I'm afraid you'll have to create a script or launcher as suggested previously. I guess the problem is that there is no "proper" way to do what your are trying to do because it is dangerous.

The only other thing I could think is that you could try mounting it read only if you do not need to write on it from Linux. 

```

/dev/sdb2 /media/SG ntfs-3g defaults,ro 0 0

```

or 

```

/dev/sdb2 /media/SG ntfs defaults 0 0

```

Note that unlike "ntfs-3g", the plain "ntfs" fs type is always read-only.

---

### Post by ChameleonDave on 2008-07-02
> **KuroYoma said:**
> I use NTFS for game dvd that are larger than 4.1 gigs.  The other formats does not support single files larger and some of the iso files are larger than that.  

According to [http://en.wikipedia.org/wiki/Ext3#Size_limits](http://en.wikipedia.org/wiki/Ext3#Size_limits), Ext3 is quite capable of that sort of file size.  Drivers are available for Windows.

If you can't install drivers, then that sucks.

If you can't safely remove, then that sucks.

A launcher that forces the drive to mount is your only option then.

---

### Post by KuroYoma on 2008-07-02
I can't use ext3 on my windows, i have tried tons of different ways for days and nothing works,(thnx though) which i use for games that linux does not YET support so it is not an option.

bab1 i just said that in one of the cases i need my External HD, school, the PCs won't let me unmount it because of admin privliges.  That is the only reason i need this.

Yugi i wanted to thank you for showing me that usful little tool.

---

### Post by boblemur on 2008-07-12
rarther late... but still

UUID=ACB8DAE5B8DAAD58 /media/data ntfs-3g defaults,force 0 0

works for me... when windows says its in use...or at least when i go mount -a it works..

i use it on my 3 windows partitions...

---

