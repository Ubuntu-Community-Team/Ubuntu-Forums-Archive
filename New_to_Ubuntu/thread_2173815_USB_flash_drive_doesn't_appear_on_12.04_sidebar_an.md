---
title: "USB flash drive doesn't appear on 12.04 sidebar and doesn't automount"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by mark allyn on 2013-09-11
Hello everyone,

Others have had this problem but I have failed to find a solution.

When I put a USB 8 GB stick in the socket there is no notification icon on the launcher (sidebar) and the drive doesn't automount.  

I have checked using dconf-editor and the automout and automount boxes are both checked.

Using dmsg or sudo fdisk shows that the drive is at /dev/sde.

I CAN mount the drive manuallly using sudo mount /dev/sde1 /mnt/flash and read/write files without a problem.  Moreover, if I plug a 500 GB seagate drive into the socket it doesn't present an icon and doesn't automount either.  So, I think it's likely not a problem with the storage media..

Using palimpsest command indicates a healthy drive and partition (ext2, btw).

Other than rebooting, I haven't got a "next step" in mind.  Rebooting is a pain because I dual boot and first have to boot up Windows 7 and then restart.  Not fun.

Grateful for any ideas.

Mark Allyn

---

### Post by VMC on 2013-09-11
You can rule out the kernel by doing the following. Unplug any USB device, then monitor *syslog* , then plug in the device. If it doesn't mount you need to wait 5 minutes to see if it will mount. From the *syslog*, look for the "trying 30 times and giving up message":
From a terminal type the folowing and then hit return several times so to separate from old message, then plug in USB flash:
```
tail -f /var/log/syslog
```

---

### Post by mark allyn on 2013-09-11
Hi VMC,

Thanks for the suggestion.  Did what you said and here is what syslog contained:

```

Sep 11 12:12:36 mark-HP-ProBook-4525s kernel: [747525.568105] usb 1-1: new high-speed USB device number 82 using ehci_hcd
Sep 11 12:12:36 mark-HP-ProBook-4525s kernel: [747525.706015] scsi83 : usb-storage 1-1:1.0
Sep 11 12:12:36 mark-HP-ProBook-4525s mtp-probe: checking bus 1, device 82: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1"
Sep 11 12:12:36 mark-HP-ProBook-4525s mtp-probe: bus: 1, device: 82 was not an MTP device
Sep 11 12:12:37 mark-HP-ProBook-4525s kernel: [747526.706011] scsi 83:0:0:0: Direct-Access     SanDisk  Cruzer           1.14 PQ: 0 ANSI: 2
Sep 11 12:12:37 mark-HP-ProBook-4525s kernel: [747526.708256] sd 83:0:0:0: Attached scsi generic sg3 type 0
Sep 11 12:12:37 mark-HP-ProBook-4525s kernel: [747526.713333] sd 83:0:0:0: [sde] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
Sep 11 12:12:37 mark-HP-ProBook-4525s kernel: [747526.716367] sd 83:0:0:0: [sde] Write Protect is off
Sep 11 12:12:37 mark-HP-ProBook-4525s kernel: [747526.716379] sd 83:0:0:0: [sde] Mode Sense: 03 00 00 00
Sep 11 12:12:37 mark-HP-ProBook-4525s kernel: [747526.719028] sd 83:0:0:0: [sde] No Caching mode page present
Sep 11 12:12:37 mark-HP-ProBook-4525s kernel: [747526.719040] sd 83:0:0:0: [sde] Assuming drive cache: write through
Sep 11 12:12:37 mark-HP-ProBook-4525s kernel: [747526.724133] sd 83:0:0:0: [sde] No Caching mode page present
Sep 11 12:12:37 mark-HP-ProBook-4525s kernel: [747526.724145] sd 83:0:0:0: [sde] Assuming drive cache: write through
Sep 11 12:12:37 mark-HP-ProBook-4525s kernel: [747526.728178]  sde: sde1
Sep 11 12:12:37 mark-HP-ProBook-4525s kernel: [747526.731705] sd 83:0:0:0: [sde] No Caching mode page present
Sep 11 12:12:37 mark-HP-ProBook-4525s kernel: [747526.731717] sd 83:0:0:0: [sde] Assuming drive cache: write through
Sep 11 12:12:37 mark-HP-ProBook-4525s kernel: [747526.731727] sd 83:0:0:0: [sde] Attached SCSI removable disk
Sep 11 12:12:38 mark-HP-ProBook-4525s logger: root -- plug mounted
Sep 11 12:12:38 mark-HP-ProBook-4525s logger: root--got dbus session bus address--
Sep 11 12:12:38 mark-HP-ProBook-4525s logger: root--went through notify-send call
Sep 11 12:12:38 mark-HP-ProBook-4525s logger: root -- completed the script
Sep 11 12:17:01 mark-HP-ProBook-4525s CRON[5890]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

It appears as I read it that the system "thinks" it has mounted the "plug".  I'm no expert in reading syslogs, however, so I'd appreciate reading your interpretation of its contents.

If I "df -h", however, it will not show up.  If I issue a mount command it will not appear in the list of mounted filesystems.  If I attempt to umount /dev/sde1 the system responds with a not mounted message.  But, if I do sudo fdisk -l /dev/sde or lsusb the response indicates the sys is aware of the flash drive.

So, any further assistance much appreciated.

Mark

---

### Post by VMC on 2013-09-11
That output does look correct, although the 'root' part I'm unsure of. It should have opened nautilus and displayed the contents.
If you open up nautilus yourself, does the device appear?.

Start with the device plugged in type the following:```
sudo fdisk -l
```.
Here is what my Cruzer looks like mounted.
```
Disk /dev/sdd: 2055 MB, 2055019008 bytes64 heads, 62 sectors/track, 1011 cylinders, total 4013709 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44834c70


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          62     4011647     2005793    c  W95 FAT32 (LBA)
```

---

### Post by mark allyn on 2013-09-12
Good morning, VMC.

If I open nautilus it does not show the flash drive.

When I do fdisk I get the following:

```

mark@mark-HP-ProBook-4525s:~$ sudo fdisk -l
[sudo] password for mark: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5147c726

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      616447      307200    7  HPFS/NTFS/exFAT
/dev/sda2          616448   589488127   294435840    7  HPFS/NTFS/exFAT
/dev/sda3       589490176   620947455    15728640    7  HPFS/NTFS/exFAT
/dev/sda4       620947456   625131519     2092032    c  W95 FAT32 (LBA)

Disk /dev/sdb: 2000.4 GB, 2000398933504 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00063e80

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     7813119     3905536   83  Linux
/dev/sdb2         7813120   300781567   146484224   83  Linux
/dev/sdb3       300781568   316405759     7812096   82  Linux swap / Solaris

Disk /dev/sdc: 8004 MB, 8004304896 bytes
126 heads, 16 sectors/track, 7754 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005ecac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048      206847      102400   83  Linux
mark@mark-HP-ProBook-4525s:~$ 

```

Dev sda is the internal hard drive on my laptop.  Dev sdb is an external Seagate hard drive that has my 12.04 linux distro on it.  Dev sdc is my 8 GB flash drive.  So, the system is aware of the flash, but won't mount it automatically.

Your thoughts would be appreciated.

Mark

---

### Post by VMC on 2013-09-12
Maybe the way its formatted. If nothing important is on that flash disk, try re-formatting and make sure you add a partition.
Also what's the output of this command ```
 uname -r
```

---

### Post by mark allyn on 2013-09-12
Hi  VMC,

uname -r yields:

```


3.2.0-51-generic-pa


```

OK, I''ll delete the current partition and put a new one in.  After starting this thread, I have just discovered that it won't put a disc icon on the sidebar or automount a disk (dvd) either.  

Cheers,
Mark

---

### Post by mark allyn on 2013-09-12
Hi VMC,

Sorry to report that deleting the old partition and adding a new linux 100 MB partition didn't fix the problem.

The fact that the disk drive also seems compromised in the same fashion as the usb port is quite disoncerting.  Maybe it will give you a clue, however.

Mark

---

### Post by VMC on 2013-09-12
> **mark allyn said:**
> Hi VMC,

Sorry to report that deleting the old partition and adding a new linux 100 MB partition didn't fix the problem.

The fact that the disk drive also seems compromised in the same fashion as the usb port is quite disoncerting.  Maybe it will give you a clue, however.

Mark
Not sure what you mean. It appears your hard drive is ok.

---

### Post by mark allyn on 2013-09-12
Hi VMC,

My apologies.  The hard drive to which I was referring is not the internal drive.  It's fine.  The drive in question is the internal DVD optical drive located at sr0.

Sorry for misleading you.

Mark

---

### Post by mark allyn on 2013-09-12
Hello VMC,

Please disregard the last post.  I made a whopper of a mistake.  Careless.  The drive that also doesn't pop an icon and get mounted is the internal dvd optical drive (sr0).  

Sorry about the confusion.  

Mark

---

