---
title: "Trying to Copy a Partition to a smaller Partition."
date: 2008-11-10
forum: New to Ubuntu
---

### Post by KuroYoma on 2008-11-10
I am try to copy my sda4 ubuntu 8.10 partition to sda3, a smaller partition, and keep all my permissions and boot-ability.  I have tried dd bet because the partition is smaller than the original the file system became corrupt.

Any help would be appreciated.

---

### Post by caljohnsmith on 2008-11-10
You could copy the entire file system over to the new partition with "cp -ax", and then you have to update your /boot/grub/menu.lst and /etc/fstab. Also you will need to reinstall Grub to the MBR (Master Boot Record) of your HDD. If you want more details of how to do all that, please post:
```
sudo fdisk -lu
```
And we can work from there.

---

### Post by KuroYoma on 2008-11-10
```

sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1         1028160     5221124     2096482+  82  Linux swap / Solaris
/dev/sda2              63     1028159      514048+  83  Linux
/dev/sda3        43327305    78140159    17406427+  83  Linux
/dev/sda4         5221125    43327304    19053090   83  Linux

```

---

### Post by bumanie on 2008-11-10
Yo will have that problem with any partition you copy - rule of thumb is to copy a partition to another partition of equal or greater size. You could to try shrinking sda4 to the same size as sda3 with gparted, otherwise copy to a different drive/partition with equal or greater capacity.

---

### Post by caljohnsmith on 2008-11-10
OK, you should do the following from your Live CD so none of your file systems are currently mounted, and please post the output of all commands so I can check that everything went OK:
```

sudo mkdir /mnt/sda4 /mnt/sda3
sudo mount /dev/sda4 /mnt/sda4
sudo mount /dev/sda3 /mnt/sda3
sudo cp -ax /mnt/sda4/* /mnt/sda3/.
```
Then you will need to reinstall Grub so that uses your new partition:
```
sudo grub
grub> root (hd0,2)
grub> setup (hd0)
grub> quit
```
Next, modify your fstab:
```

sudo cp /mnt/sda3/etc/fstab /mnt/sda3/etc/fstab.backup
sudo blkid -c /dev/null
gksudo gedit /mnt/sda3/etc/fstab
```
And in your fstab, find the line with the mount point of "/", and use the UUID for sda3 given by the blkid command above, so it will look similar to:
```
# /dev/sda3
UUID=[COLOR="Blue"]77677cb5-6e56-4936-a373-80c15de06bca /[/COLOR] ext3  relatime,errors=remount-ro 0 1

```
So replace the UUID with your UUID for sda3, but you shouldn't need to change any of the options you all ready have after the "ext3" since yours may be entirely different than what's above. Next open your menu.lst:
```
gksudo gedit /mnt/sda3/boot/grub/menu.lst
```
And for all your Ubuntu entries, change the UUID in the kernel line to use your UUID for sda3, and also make sure the "root" line uses (hd0,2):
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd0,2)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=[COLOR="Red"]77677cb5-6e56-4936-a373-80c15de06bca[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
And change the "# kopt" line to use the UUID of sda3:
```
# kopt=root=UUID=[COLOR="Red"]77677cb5-6e56-4936-a373-80c15de06bca[/COLOR] ro
```
And lastly, change the "# groot" line in menu.lst to:
```
# groot=[COLOR="Red"](hd0,2)[/COLOR]
```
Save, reboot, and if all goes well you should be able to boot into Ubuntu on sda3. Let me know how it goes.

---

### Post by KuroYoma on 2008-11-11
when i used the 'grub> setup (hd0) i got this error

```

Checking if "/boot/grub/stage1" exists... no
Checking if "/grub/stage1" exists... no
Error 15: file not found

```

I tried a couple of other things but still got errors. I moved on and got everything else done and got fdisk and grub set up with my sda4 partition.
Is there anyway to just add sda3 to my current grub so i can boot into either one at anytime during boot.

fdisk -lu
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1         1028160     5221124     2096482+  82  Linux swap / Solaris
/dev/sda2              63     1028159      514048+  83  Linux
/dev/sda3        43327305    78140159    17406427+  83  Linux
/dev/sda4         5221125    43327304    19053090   83  Linux

Partition table entries are not in disk order

```

sudo blkid -c /dev/null
```

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="e22464cd-5fe3-4fda-9df6-699ccb4407dd" TYPE="swap" 
/dev/sda2: UUID="89f1b0e4-e1c9-4a30-8266-7b6ae3888dfa" TYPE="ext2" 
/dev/sda3: UUID="3bb60a74-4353-46c7-acc7-eb462b8fb021" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="a4ec31ad-9337-407e-9de6-29e8c61c21c8" TYPE="ext3" 

```

---

### Post by caljohnsmith on 2008-11-11
You probably got that Grub error because sda2 is your boot partition, is that true? If so, I would copy those boot files to your sda3 partition, because it probably is not a good idea to have sda3 and sda4 share the same boot partition, depending on what you do with sda3 and sda4. So if sda2 is your boot partition, you could do the following:
```
sudo mkdir /mnt/sda2 /mnt/sda3
sudo mount /dev/sda2 /mnt/sda2
sudo mount /dev/sda3 /mnt/sda3
sudo cp -ax /mnt/sda2/* /mnt/sda3/boot/.
```
And then rerun the Grub commands I gave in my last post if you want sda3 to be in charge of the Grub menu on start up. If you want sda2 to control the Grub menu on start up, you don't have to do anything.

---

### Post by KuroYoma on 2008-11-11
Yes it is true that sda2 is my boot partition.  Why is it not a good idea to has sda3 and sda4 share the same boot partition?  How do I add sda3 to my current grub setup so that both partitions are boot-able?

---

### Post by caljohnsmith on 2008-11-11
Since sda3 and sda4 also share the same swap partition, I think you could have both sda3 and sda4 share the boot partition if you are careful enough, but you will have to manually update your Grub menu.lst every time you get a new kernel. So if that is what you want to do, you could just modify your menu.lst with:
```
sudo umount /mnt
sudo mount /dev/sda2 /mnt
gksudo gedit /mnt/grub/menu.lst

```
And then for your sda3 boot stanzas, you would use something similar to:
```
title		Ubuntu on sda3, kernel 2.6.24-19-generic
root		[COLOR="Blue"](hd0,1)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=[COLOR="Blue"]77677cb5-6e56-4936-a373-80c15de06bca[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```
So the boot stanzas for both sda3 and sda4 will use the same "root (hd0,1)" since they share the sda2 boot partition, but you will need to make the UUID above the UUID for sda3. So just take your sda4 Ubuntu entries, copy and paste them, and change the UUIDs for sda3, and also change the "title" line so you know it is sda3.

---

### Post by KuroYoma on 2008-11-11
Well it starts to load until it reaches gdm then it stops.  Comes up with an error and gives me a command line log in.  I log in and try to start gdm... fail.  Try to start x... fail.
I am going to go through the logs on sda3 from my normal boot into sda4.

I am finding this error in Xorg.20.log
```

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.0
[COLOR="Red"](EE) [drm] Could not set DRM device bus ID.
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.[/COLOR]
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
```

and this

```
(II) intel(0): EDID vendor "AUO", prod id 4164
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle seperate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "AUO", prod id 4164
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle seperate sync.
[COLOR="Red"](EE) intel(0): underrun on pipe B![/COLOR]
(II) intel(0): EDID vendor "AUO", prod id 4164
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle seperate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "AUO", prod id 4164
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle seperate sync.
[COLOR="Red"](EE) intel(0): underrun on pipe B!
```[/COLOR]

and i am getting this in /var/log/gdm/:20.log
```
(==) Log file: "/var/log/Xorg.20.log", Time: Sun Nov  9 12:27:01 2008
(==) Using config file: "/etc/X11/xorg.conf"
[COLOR="Red"](EE) [drm] Could not set DRM device bus ID.
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.
(EE) intel(0): underrun on pipe B![/COLOR]
AUDIT: Sun Nov  9 12:27:14 2008: 12495 X: client 4 rejected from local host ( uid=0 gid=0 pid=12530 )
AUDIT: Sun Nov  9 12:27:18 2008: 12495 X: client 4 rejected from local host ( uid=0 gid=0 pid=12537 )
AUDIT: Sun Nov  9 12:27:18 2008: 12495 X: client 4 rejected from local host ( uid=0 gid=0 pid=12538 )
AUDIT: Sun Nov  9 12:27:18 2008: 12495 X: client 4 rejected from local host ( uid=0 gid=0 pid=12539 )
[COLOR="Red"](EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B![/COLOR]
```




EDIT:  I just compared it and my successful login on this partition and found the "underrun on pipe B!" was still there but the 
(EE) [drm] Could not set DRM device bus ID.
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI
was still there.

---

### Post by KuroYoma on 2008-11-13
*bump*

---

