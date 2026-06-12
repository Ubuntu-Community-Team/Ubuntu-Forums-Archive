---
title: "First time user: Problems with sound and file system."
date: 2008-09-01
forum: New to Ubuntu
---

### Post by kpmoore on 2008-09-01
First problem, a hear a looping crackle coming from my speakers and playing music/system sounds do nothing to change it. I have a Creative X-Fi, so I installed OSS according to this website:[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

I didn't follow the "stopping ALSA" steps because I hadn't installed ALSA... was this correct or does ALSA come default with Ubuntu?

Also, I wasn't sure what to do for "System sounds on GNOME" or "System sounds on KDE" because I don't know what GNOME or KDE are or if I have either of them. 

Any suggestions as to how to get my sound up and running?


Second problem, my file system. Let me briefly explain my hard drive setup:
disk 0- 1TB- Contains media files only (music, movies, etc.)
disk 1- 250GB- Contains Windows Vista installation
disk 2- 400GB- Contains Ubuntu Installation (root and swap partition)

I've got the system dual booting just fine my putting the GRUB loader on disk0 and selecting that as my first boot device.

My problem is that I want to be able to access my media files (disk0) from both OS's. So my idea was to format it as FAT32 so both OS's could read and write to it. However, I have 300GB of stuff on the drive which I do not want to lose. What I did was shrink the volume to 500GB in windows and formatted the unallocated space as FAT32 in GParted. I then transferred the 300GB of files from the NTFS partition to the FAT32 partition. It all worked except for all my files which were over ~4GB. Is is possible to store large files in FAT32? Anyway, I deleted the NTFS partition, hoping to be able to extend the FAT32 partition across the entire 1TB drive. I cannot seem to find a way to do this, however. Is it possible? or should I just move the 300GB of media on to my linux drive, format the 1TB as FAT32, and move it all back? Let me know the easiest way to do it. Also let me know if you think theres a better way I could setup these three hard drives.

One last random thing, there is a little strip of pixels coming from the top of my screen, about 1cmx3cm in which all the pixels keep turning random colors. Looks like a tube of confetti. I can make it temporarily disappear by dragging windows over it, but I can't seem to get rid of it. Any suggestions?


I appreciate the help.

---

### Post by mikewhatever on 2008-09-01
> **kpmoore said:**
> Is is possible to store large files in FAT32? 

No, I don't think so. 4 GB is the limit for FAT32. You can use either ntfs or ext3. Ubuntu can read and write ntfs quite well, and to enable Windows to recognize ext3, check the link below.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by OutOfReach on 2008-09-01
As far as I know, ALSA is installed in Ubuntu, but I think PulseAudio is default.
And FAT32 can't go passed 4GB I imagine.

---

### Post by kpmoore on 2008-09-01
Ubuntu can write to NTFS?? Is there something I have to do to enable that feature? I thought I remember trying it and it not working...

---

### Post by mikewhatever on 2008-09-01
> **kpmoore said:**
> Ubuntu can write to NTFS?? Is there something I have to do to enable that feature? I thought I remember trying it and it not working...

Yes, ntfs-3g is pre-installed.

---

### Post by cariboo on 2008-09-01
If you use gparted or any other partitioning software you can format a fat32 disk as large as you want. The problem you will run into is with files larger then 4GB, such as dvd images. NTFS would be a much better choice for your large disk, Ubuntu can access NTFS just as well as Windows and you don't have the 4GB file limit. 

I've got a 320GB external that is formatted as vfat, it works well as long as I keep file sizes below 4GB.

Jim

---

