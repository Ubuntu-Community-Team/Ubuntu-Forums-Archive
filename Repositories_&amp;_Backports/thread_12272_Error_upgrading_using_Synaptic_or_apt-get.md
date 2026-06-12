---
title: "Error upgrading using Synaptic or apt-get"
date: 2005-01-23
forum: Repositories &amp; Backports
---

### Post by pedx1ng on 2005-01-23
Hi all.

Recently I installed Ubuntu on a small hard drive to test it out.  Everything went well and I liked what I saw, so I decided to put it on a fresh, larger hard drive.   On my old install I was able to use both Synaptic and apt-get to upgrade my packages.  But after trying it on my fresh install, I get this error:

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/login_1%3a4.0.3-28.5ubuntu6.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `ubuntu-artwork': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/login_1%3a4.0.3-28.5ubuntu6.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


It doesn't matter if I use apt-get or Synaptic, the same error appears.  Any idea on where I should look to fix this?

Thank you.

---

### Post by mendicant on 2005-01-23
Perhaps a corrupt file?  Try deleting /var/cache/apt/archives/login_1%3a4.0.3-28.5ubuntu6.1_i386.deb and doing it again.  I'm not sure why it references ubuntu-artwork though.  Maybe that's the corrupt file.

---

### Post by pedx1ng on 2005-01-23
[QUOTE=mendicant]Perhaps a corrupt file?  Try deleting /var/cache/apt/archives/login_1%3a4.0.3-28.5ubuntu6.1_i386.deb and doing it again.  I'm not sure why it references ubuntu-artwork though.  Maybe that's the corrupt file.[/QUOTE]

I have tried deleting all of /var/cache/apt/archives and starting over.  I have tried upgrading just one package rather than all that could be upgraded.  I have tried re-installing the 'ubuntu-artwork' package.  I have tried un-installing 'ubuntu-artwork'.  In every case, I get the SAME error:

 failed in buffer_read(fd): files list for package `ubuntu-artwork': Input/output error

What is going on??   :sad: 

The whole reason I moved to Ubuntu was a frustration with Mandrake -- I couldn't install simple security upgrades without it erroring out.  Since I am not a Linux expert, I need a distro I can install security upgrades to without much hassle.  So I do a test install of Ubuntu, and I am able to upgrade without problems.  Then I do a fresh install for my home server and now I can't upgrade anymore.  I am so frustrated...  Why would it work before and not now?  Only difference is I am using a brand new, bigger hard drive.

Frustrated............

---

### Post by pedx1ng on 2005-01-23
I am still having problems but I have some more information.  Viewing /var/log/syslog I get this message right after trying to upgrade a package (any) with Synaptic.

Jan 23 16:58:45 haven kernel: attempt to access beyond end of device
Jan 23 16:58:45 haven kernel: hde6: rw=0, want=8589934600, limit=154304262
Jan 23 16:58:45 haven kernel: attempt to access beyond end of device
Jan 23 16:58:45 haven kernel: hde6: rw=0, want=8589934600, limit=154304262

hde is my boot drive.  It's not on hda because the drive is 160GB and the motherboard's BIOS has that >137GB drive size limitation.  I couldn't install Ubuntu until I moved the drive to a PCI ATA133 card.

hde6 is my / partition, ext3.

Is my file system corrupted?

---

### Post by mendicant on 2005-01-23
Sounds like the kernel thinks the partition is a different size than you do.  You might want to check your logs for other messages; maybe like this:

dmesg | grep hde 

to see if there's anything else.  You can also check to make sure that the partitions with

fdisk -l /dev/hde (or use cfdisk /dev/hde to check in MB)

also check if it matches up with the output of df (approximately).

---

### Post by pedx1ng on 2005-01-23
Output of "dmesg | grep hde":

Kernel command line: root=/dev/hde6 ro quiet splash
    ide2: BM-DMA at 0xcc00-0xcc07, BIOS settings: hde:pio, hdf:pio
hde: WDC WD1600JB-00GVA0, ATA DISK drive
hde: max request size: 1024KiB
hde: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
Adding 979924k swap on /dev/hde5.  Priority:-1 extents:1
EXT3 FS on hde6, internal journal
EXT3 FS on hde1, internal journal
EXT3 FS on hde7, internal journal
hde6: rw=0, want=8589934600, limit=154304262
hde6: rw=0, want=8589934600, limit=154304262
hde6: rw=0, want=8589934600, limit=154304262
hde6: rw=0, want=8589934600, limit=154304262
hde6: rw=0, want=8589934600, limit=154304262

Output of "sudo fdisk -l /dev/hde":

Disk /dev/hde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1           4       32098+  83  Linux
/dev/hde2               5       19457   156256222+   5  Extended
/dev/hde5               5         126      979933+  83  Linux
/dev/hde6             127        9731    77152131   83  Linux
/dev/hde7            9732       19457    78124063+  83  Linux

Output of "df":

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hde6             75940832   1552800  70530428   3% /
tmpfs                   258304         0    258304   0% /dev/shm
/dev/hde1                30075      7437     21034  27% /boot
/dev/hde7             76896316     46980  72943136   1% /home
/dev/md0             480726864 131454704 324852572  29% /datastor1


I'm no expert, but only thing that looks amiss to me is that dmesg output with the hde6: rw=0, want=8589934600, limit=154304262.

Isn't the file system checked for inconsistencies each boot?  Wouldn't it find this problem and fix it?

---

### Post by mendicant on 2005-01-24
To force an fsck on reboot, try shutting down with:

% sudo shutdown -F -r now

which will do an immediate reboot, and request an fsck

---

### Post by pedx1ng on 2005-01-24
Thank you for your continued assistance.

Sure enough, fsck found problems.  Unfortunately, now the system is caught in an fsck check / fix fail / reboot loop.  I can't cut/paste error messages because I don't know how to get into the system now.

Basically this happens:  System starts booting and runs fsck.  It finds inconsistencies, says it will fix and that fsck has requested a reboot.  However I see a [ Fail ] message off to the right.  The system then reboots, and it does the exact same thing the next time around.  It's like it's not actually fixing it even though it says it is and so it just keeps rebooting and trying to do it over and over.

I don't know how the system got so messed up so soon.  It's a fresh install and I've barely used the system.  I have not done any abnormal reboots/shutdowns to mess up the file system either.

What do you recommend at this point, should I wipe the system and start from scratch?

---

### Post by mendicant on 2005-01-24
That seems to be indicated.  If you want to try one thing, you can try doing an fsck from a Live CD.  But it certainly appears to be fubar'd.  If this has happened when you used Mandrake, it's possible you have a hardware issue.

---

