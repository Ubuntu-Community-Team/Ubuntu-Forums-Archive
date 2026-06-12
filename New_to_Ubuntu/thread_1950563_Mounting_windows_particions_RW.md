---
title: "Mounting windows particions R/W"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by pdr2esmolbra on 2012-03-31
Hello everyone, 

I am going slightly mad at trying to get my windows 'data' particion to work read/write in Ubuntu 10.10.

I have been changing fstab. I can change options and remount the particion. For a while it works! I can change files and create folders, but it works only in the terminal. I promise this is the strangest thing that has ever happened to me! I can create test documents and folders right when I remount my drive in the terminal, but the second I open a folder (with the GUI: AltF2 .. /dos/ )and try the same it blocks everything returning the disk to 'read-only' mode? Going back to terminal (even in SUDO mode!!) blocks every write action!
I.e, it spits out

mkdir: cannot create directory `test4': Read-only file system

Any idea why this happens!?

Here's my fstab line on the problematic disk:

#Entry for /dev/sda4 :
UUID=E51F-9C31 /dos vfat uid=1000,umask=000,gid=100,users,rw 0 0 

Here's the result of fdisk -l

/dev/sda4 9292 14594 42584064 b W95 FAT32


Apparently 0x0b FAT is ancient but would that help?? Not sure I want to try changing that in case it screws up windows and data stored...

Mount command returns:

/dev/sda1 on /XP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
pedrito@pedros-HPdv6120:~$ mount
/dev/sda3 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/pedrito/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pedrito)
/dev/sda1 on /XP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /dos type vfat (rw,noexec,nosuid,nodev,uid=1000,umask=000,gid=100 ,utf

There are some errors above but don't seem related to "/dos" are they?

I am going insane! I released the disk from any windows business by shutting it down properly.

I am just about to reformat this particion to NTFS!
But I have come this far: HEEEELP :) :confused:

Thanks!

---

### Post by oldfred on 2012-04-01
Please do not keep opening threads on the same issue.

See also
Changing read/write permissions of file-system folder? 
[http://ubuntuforums.org/showthread.php?t=1945155](http://ubuntuforums.org/showthread.php?t=1945155)
this referred to a Mac?
Help with changing permissions on an external drive?
[http://ubuntuforums.org/showthread.php?t=1946755](http://ubuntuforums.org/showthread.php?t=1946755)

I am closing other threads.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by pdr2esmolbra on 2012-04-01
Sorry about the multiple post, I only did so in an attempt of reaching a larger audience. It won't happen again.

My problem is not with a Mac.
My problem is not with NTFS, but with FAT32.
My problem is with a static disk partition not an external drive.

I repeat my question:  why does the Ubuntu GUI change the read-write permissions of the disk when the terminal had everything working? See command responses and fstab line above, they are seemingly RW friendly, what am I doing wrong?!

Thanks!
Pdp

---

### Post by oldfred on 2012-04-01
I do not think it is the issue but your gid is 100? should be 1000?

Post your fstab:

This is my mount & fstab from years ago. I have not mounted my FAT partition for ages as I lost a lot of large files. FAT does not support files over 4GB, so I converted to NTFS for the partition I share data with XP.

Did you look at the instructions in the psychocats link above? The only real difference is drives are now sda not hda.

My old mount from a run (maybe my first)  of boot_info script 3 or 4 years ago.
```
/dev/sda4 on /home/fred/share type vfat (rw,noexec,nosuid,nodev,fmask=0111,dmask=0000)

# before uuid  /dev/sda4 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0
UUID=46CD-C9B2 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0

```

---

### Post by pdr2esmolbra on 2012-04-08
Hi again, 

I have tried everything, (psycho cats and your lines) still no luck. Again terminal seems OK but the GUI somehow reverses partition to read-only.

I have decided to just reformat to NTFS, will keep you updated on how that one works!
Cheers

---

### Post by pdr2esmolbra on 2012-04-11
Halleluyah!

I formatted my disk NTFS and with 3g it works like a charm!

From my experience, I don't think Ubuntu should recommend people to format their 'share with windows' drives as FAT32. It is ancient, less efficient than NTFS, and most importantly not fool-proof :)

I feel the problem was that I started playing around with chmod first and somehow told ubuntu - the Gui=GNOME?- that the system was read-only. The recently mounted drive would work great in the terminal, but once GUI rw was attempted, it would switch back to read-only mode.

Thanks a lot you for your time and feedback!
Pdp

---

