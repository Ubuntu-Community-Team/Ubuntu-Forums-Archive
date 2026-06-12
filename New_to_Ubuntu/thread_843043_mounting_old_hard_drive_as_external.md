---
title: "mounting old hard drive as external"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by hardyheronnewb on 2008-06-27
I have been trying to mount my drive for the entire day. Xp recognizes it fine. I took an old ide (ntfs, 80gb,) hdd and put it into an enclosure. Here is some more information. I am not able to see it in the list of drives, how to find a mount point? or create one so that it will mount.
Please help. 

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9774    78509623+   7  HPFS/NTFS
/dev/sda2            9775       19078    74734380   83  Linux
/dev/sda3           19079       19452     3004155    5  Extended
/dev/sda5           19079       19452     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)
__________________________________________________________________________

Bus 005 Device 006: ID 413c:3200 Dell Computer Corp. 
Bus 005 Device 005: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 005 Device 004: ID 1058:0910 Western Digital Technologies, Inc. 
Bus 005 Device 002: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 046d:c509 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

the w95 is my other external that mounts fine and i did not have to install any drivers for it. it was plug and play. 
Is it true that some enclosures "dont support" linux? that doesnt seem to make much sense. 
Please help.
Thank you.

---

### Post by buntunub on 2008-06-27
Does Ubuntu recognize your drive upon bootup, and where does udev mount it? Here's how it works:

1. Your BIOS picks up the drive and recognizes that something new is there.
2. During the boot process, Ubuntu will recognize the new drive and use udev to figure out where it gets mounted (/dev/sda, /dev/sdb, etc.).
3. Some things should get written to your /etc/fstab for your drive automatically. This is probably where your troubles lie btw.

Assuming 1 and 2 got done, then you need to setup your fstab so that its to your preference. You can check to see where/how your drive got placed via

```
fdisk -l
```

and

```
df -h
```

If all is well there, and you see your drive, then all you need to do is modify your fstab to your liking.

---

### Post by hardyheronnewb on 2008-06-28
here is the output of the above commands. When I checked bios/setup in the beginning, it does not recognize either usb device ( i have a western digital external attached as well, though it mounts and fstab did not get modified to add any entry for it. Am i not checking bios properly?

Disk /dev/sda: 160.0 GB, 160000000000 bytes *(this is my internal drive)*
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9774    78509623+   7  HPFS/NTFS
/dev/sda2            9775       19078    74734380   83  Linux
/dev/sda3           19079       19452     3004155    5  Extended
/dev/sda5           19079       19452     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes *(this is my external wd drive)*
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)
_________________________________________________________________________
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              71G  6.4G   61G  10% /
varrun                501M  100K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   72K  501M   1% /dev
devshm                501M   12K  501M   1% /dev/shm
lrm                   501M   38M  464M   8% /lib/modules/2.6.24-19-generic/volatile
/dev/sda1              75G  6.0G   69G   8% /media/windows
/dev/sdb1             299G  157G  142G  53% /media/My Book

will be awaiting your response. thank you.

---

### Post by buntunub on 2008-06-29
Just looking at what you've provided, I really have no clue as to which drive is the one you are having trouble with. What your showing me with that is all your drives which are recognized and mounted properly, so all looks well to me. I have several external USB drives which work beautifully in hardy and were picked up on first boot after I plugged them in. I did have to modify fstab to get them to mount the way I needed them to so that Mythtv wouldn't have any trouble recognizing the proper partitions on them. There are some really great wiki's on how to setup your fstab on Ubuntu wiki and elsewhere, and that's where you need to be looking IMO.

---

### Post by hardyheronnewb on 2008-06-29
fuega24@fuega24-desktop:~$ lsusb
Bus 005 Device 006: ID 413c:3200 Dell Computer Corp. 
Bus 005 Device 005: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge *I believe that this is the enclosure's bridge*
Bus 005 Device 004: ID 1058:0910 Western Digital Technologies, Inc. 
Bus 005 Device 002: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c509 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

However, the hdd doesnt show up anywhere. thats why everything looks mounted because the hdd does not show up in any of those outputs. 
This is the output from  ls /dev/s*
/dev/scd0  /dev/sda2  /dev/sdb1        /dev/sg0  /dev/sg4       /dev/sr1
/dev/scd1  /dev/sda3  /dev/sdc *could this be the hdd, but doesnt mount?*        /dev/sg1  /dev/snapshot  /dev/stderr
/dev/sda   /dev/sda5  /dev/sequencer   /dev/sg2  /dev/sndstat   /dev/stdin
/dev/sda1  /dev/sdb   /dev/sequencer2  /dev/sg3  /dev/sr0       /dev/stdout

/dev/shm:
pulse-shm-1779383839

/dev/snd:
controlC0  pcmC0D0p  pcmC0D2c  pcmC0D4p  timer
pcmC0D0c   pcmC0D1c  pcmC0D3c  seq

---

### Post by tannedin on 2008-09-05
bump...
i have a converter that shows the same via "sudo lsusb"
and a working ntfs drive that is tested under a windows xp pro install

however, the device will not mount nor show in "sudo fdisk -l"

---

