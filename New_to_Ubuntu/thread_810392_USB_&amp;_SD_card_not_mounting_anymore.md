---
title: "USB &amp; SD card not mounting anymore"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Fenris_rising on 2008-05-28
hi all
wonder if any of you gentlefolks can help me. i installed 8.04 about 4 weeks ago and all went rather well with minimal tweaking needed to get it all up and running perfectly. even my SD card was detected and my usb stick.
any way ive just plugged them both in today and nothing, zilch, zip, de nada. sooooooo ive been running around the forum looking here there and every where to know avail so far. all i want is for the devices to auto mount when inserted as they did when i first started using Ubuntu. fdisk -l produces;

Disk /dev/sdi: 257 MB, 257949696 bytes
16 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xb330c729

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           1         984      251888    b  W95 FAT32


Disk /dev/sdf: 513 MB, 513277952 bytes
9 heads, 40 sectors/track, 2784 cylinders
Units = cylinders of 360 * 512 = 184320 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        2785      501195+   b  W95 FAT32

lsusb -l produces;

fenris@lair:~$ lsusb
Bus 005 Device 004: ID 13fe:1a00 Kingston Technology Company Inc. 512MB/1GB Flash Drive
Bus 005 Device 003: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1241:1166 Belkin optical mouse w/ scrollwheel
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

so it seems they are detected by the system but no longer follow through.
im a noob with ubuntu but having a great time with it but i need a little guidance here please.

---

### Post by PmDematagoda on 2008-05-28
What are the drives you need to mount(sd*)?

---

### Post by Fenris_rising on 2008-05-28
hi there

they are a (generic) 512M usb stick and a Lexar 512M SD card this plugs into my card reader. im just reading a web site, im thinking i might not have a directory /mnt/USB? i have entered them both into the etc/fstab file but probably not quite right.

---

### Post by PmDematagoda on 2008-05-28
If you put some entries for them in /etc/fstab, post the output of:-
```
sudo mount -a
```

---

### Post by bumanie on 2008-05-28
I think your above assumption is correct, to mount new/previously unkown devices through /etc/fstab you first need to specify a directory for them to mount to; hence sudo mkdir <name of device> eg /media/usb (or whatever you want to call it).

---

### Post by Fenris_rising on 2008-05-28
here it is, both are formated to fat 32 so in fstab have i failed to add this heres my fstab as well i have added the mnt/USB dir but the strings in fstab are copy pasted from said site and the drive names match the 2 i am trying to mount.

fenris@lair:~$ sudo mount -a
[sudo] password for fenris: 
mount: mount point  does not exist
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1
UUID=181b9393-f671-46d7-85fb-6a50d00d425c /               ext3    relatime,errors=remount-ro 0       1
#/dev/sda5
UUID=ef97bc65-9c4d-410f-95ba-733adfc65afe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdi1 /mnt/USB auto noauto,owner,kuzu 0 0
/dev/sdf1 /mnt/USB auto noauto,owner,kuzu 0 0
#Added by diskmounter utility
/dev/sdb1 /media/sdb1 ntfs  ,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdc1 /media/sdc1 ntfs  ,user,fmask=0111,dmask=0000 0 0

---

### Post by PmDematagoda on 2008-05-28
Post the output of:-
```
cat /etc/mtab
```

---

### Post by bumanie on 2008-05-28
You say they are both formatted to FAT32, but your /etc/fstab is labelled as ntfs for both devices. Not sure if that's the only issue, however, as far as the usb device goes, it should auto mount when plugged into the usb port.

---

### Post by Fenris_rising on 2008-05-28
fenris@lair:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
/dev/sdc1 /media/sdc1 fuseblk rw,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/fenris/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=fenris 0 0

there ya go

---

### Post by PmDematagoda on 2008-05-28
Ok, I'm confused here, what drive are you trying to mount, please give in terms of sd*. Also, post the output of:-
```
sudo fdisk -l | grep sdb1
```

---

### Post by Fenris_rising on 2008-05-28
hi they are sdi1 and sdif............at this point dare i ask should i have them plugged in at this time????...........stands well back.

---

### Post by PmDematagoda on 2008-05-28
> **Fenris_rising said:**
> hi they are sdi1 and sdif............at this point dare i ask should i have them plugged in at this time????...........stands well back.

Keep them plugged in, that's fine.

Now do this:-
```
sudo mkdir /media/sdi1 && sudo mkdir /media/sdf1
```

Then mount the drives onto them with:-
```
sudo mount -t vfat /dev/sdi1 /media/sdi1 && sudo mount /dev/sdf1 /media/sdf1
```

Then see if you can access them. Also to fix the sdb1 problem, you will have to post the output of the code mentioned in the previous post.

---

### Post by Fenris_rising on 2008-05-28
fenris@lair:~$ sudo fdisk -l | grep sdi1
/dev/sdi1   *           1         984      251888    b  W95 FAT32
fenris@lair:~$ sudo fdisk -l | grep sdi1
/dev/sdi1   *           1         984      251888    b  W95 FAT32
fenris@lair:~$ sudo mount -a
mount: mount point  does not exist

---

### Post by PmDematagoda on 2008-05-28
No no, not grep sdi1 or sdf1, just grep sdb1 that's all:).

---

### Post by Fenris_rising on 2008-05-28
hi the sdb1 is a alternate drive, i allowed it by accident its now # out just entered your strings i will now try

---

### Post by Fenris_rising on 2008-05-28
mount: according to mtab, /dev/sdi1 is mounted on /media/sdi1
mount failed
fenris@lair:~$ mount /dev/sdf1
mount: according to mtab, /dev/sdf1 is mounted on /media/sdf1

they now are showing in the 'places' tab
do they auto mount now? or is there a bit more to do?


just noticewd they are on the desktop to :)

---

### Post by PmDematagoda on 2008-05-28
> **Fenris_rising said:**
> mount: according to mtab, /dev/sdi1 is mounted on /media/sdi1
mount failed
fenris@lair:~$ mount /dev/sdf1
mount: according to mtab, /dev/sdf1 is mounted on /media/sdf1

they now are showing in the 'places' tab
do they auto mount now? or is there a bit more to do?

That aught to be enough, just check if they work properly.

---

### Post by Fenris_rising on 2008-05-28
fenris@lair:~$ sudo mount /dev/sdi1
mount: wrong fs type, bad option, bad superblock on /dev/sdi1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
didnt mount after a restart, tried to sudo etc got the error string for both as above

---

### Post by Fenris_rising on 2008-05-28
sudo mount -t vfat /dev/sdi1 /media/sdi1 && sudo mount /dev/sdf1 /media/sdf1

just did the above and they mount. if i rt click to unmount they say they are not mounted

---

### Post by PmDematagoda on 2008-05-28
Post the output of:-
```
cat /etc/fstab | grep sdi1
```

Does sdf1 work properly now?

---

### Post by PmDematagoda on 2008-05-28
> **Fenris_rising said:**
> sudo mount -t vfat /dev/sdi1 /media/sdi1 && sudo mount /dev/sdf1 /media/sdf1

just did the above and they mount. if i rt click to unmount they say they are not mounted

Of course that wouldn't work like that, you would need to do:-
```
sudo umount /dev/sdi1
``` or ```
sudo umount /dev/sdf1
```

But you may need to do that only once, so don't do it repeatedly if they work normally.

---

### Post by Fenris_rising on 2008-05-28
fenris@lair:~$ cat /etc/fstab | grep sdi1
/dev/sdi1 /mnt/USB auto noauto,owner,kuzu 0 0

fenris@lair:~$ cat /etc/fstab | grep sdf1
/dev/sdf1 /mnt/USB auto noauto,owner,kuzu 0 0

 no they both failed. also i get an error when trying to drag and drop a file onto either of them.

---

### Post by PmDematagoda on 2008-05-28
You have to change the entries to make them look like this:-
```
/dev/sdi1 /media/sdi1 vfat defaults 0 0
```
and
```
/dev/sdf1 /media/sdf1 vfat defaults 0 0
```
Then try them again.

---

### Post by Fenris_rising on 2008-05-28
hi there done that and still no auto mount. i have done a dmesg and heres the bit about the USB devices
[   78.871978] NET: Registered protocol family 17
[  102.402465] usb 5-8: new high speed USB device using ehci_hcd and address 4
[  102.538397] usb 5-8: configuration #1 chosen from 1 choice
[  102.547591] scsi7 : SCSI emulation for USB Mass Storage devices
[  102.551762] usb-storage: device found at 4
[  102.551767] usb-storage: waiting for device to settle before scanning
[  107.538645] usb-storage: device scan complete
[  107.539300] scsi 7:0:0:0: Direct-Access              USB DISK 28X     PMAP PQ: 0 ANSI: 0 CCS
[  107.699337] sd 7:0:0:0: [sdi] 503808 512-byte hardware sectors (258 MB)
[  107.699960] sd 7:0:0:0: [sdi] Write Protect is off
[  107.699963] sd 7:0:0:0: [sdi] Mode Sense: 23 00 00 00
[  107.699967] sd 7:0:0:0: [sdi] Assuming drive cache: write through
[  107.702577] sd 7:0:0:0: [sdi] 503808 512-byte hardware sectors (258 MB)
[  107.703203] sd 7:0:0:0: [sdi] Write Protect is off
[  107.703206] sd 7:0:0:0: [sdi] Mode Sense: 23 00 00 00
[  107.703208] sd 7:0:0:0: [sdi] Assuming drive cache: write through
[  107.703211]  sdi: sdi1
[  107.704008] sd 7:0:0:0: [sdi] Attached SCSI removable disk
[  107.704046] sd 7:0:0:0: Attached scsi generic sg9 type 0
[  135.489763] sd 6:0:0:2: [sdf] 1002496 512-byte hardware sectors (513 MB)
[  135.490637] sd 6:0:0:2: [sdf] Write Protect is off
[  135.490640] sd 6:0:0:2: [sdf] Mode Sense: 03 00 00 00
[  135.490642] sd 6:0:0:2: [sdf] Assuming drive cache: write through
[  135.492254] sd 6:0:0:2: [sdf] 1002496 512-byte hardware sectors (513 MB)
[  135.492879] sd 6:0:0:2: [sdf] Write Protect is off
[  135.492882] sd 6:0:0:2: [sdf] Mode Sense: 03 00 00 00
[  135.492884] sd 6:0:0:2: [sdf] Assuming drive cache: write through
[  135.492887]  sdf: sdf1

they are being picked up by the system but thats it. i have conky running on sektop and when ever i plug either of the mem devices in i see hald_addon_stor, scsi_eh_7 and usb-storage on the list of apps in ram.
i dont know specifically when this went wrong as i havent had reason to use either device since last week. i wonder if an update has thrown it?
thanks for your input btw.

---

### Post by Fenris_rising on 2008-05-28
hey up just found a thread thats about missing tabs in removable drives and media. specifically they may be what we need to look at. they have been moved to file manager...........i cant find it. the 2 tabs are storage and multimedia.

---

### Post by PmDematagoda on 2008-05-28
They are now found in Preferences in Nautilus.

---

### Post by Fenris_rising on 2008-05-28
now ive heard of that abd seen the name scroll up on my conky list, ill see if i can find it..........hint :)

---

### Post by Fenris_rising on 2008-05-28
well if nautilus is on my PC captain nemo has long since taken it out to sea. ive checked where the files say it is and its not there, i dont even know if thats hwat i need to sort out this bloody problem, i havent a clue why they have stopped mounting and its been a long bloody day trying to get the ^&&^%^&*(s working. i wish i had a gas oven.](*,)


i think at this point i may go for a full re-install and see what occurs. cheers for your help and input much appreciated ticked your thanks button :)

---

