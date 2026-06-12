---
title: "Help needed with installation"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by obasan on 2011-12-02
OK, the background first. I have been a Microsoft o/s user since dos 1.0. I am not a complete noob (perhaps close, but still I have been writing C and C++ code for scientific applications for 25 years). I have a retired desktop computer (Intel Pentium 4; 1.6Gh, 2 GB memory, 2 HDs each 80+GB) currently running Win XP and I decided it would be educational at least to install Ubuntu as a second o/s on this machine. In preparation I completely reformatted the second HD (about 80GB), leaving the windows o/s on the first drive.
 
I downloaded Ubuntu 11.10-desktop-i386.iso, and burned the iso image to CD. Confirmed that all the various files and folders appeared on the CD. Set the bios to boot from the CD and started the session. After the preliminary screens and securing an internet connection, the screen for selecting the method of installation came up and I selected "something else". I was advised to do this in order to install Ubuntu to its own partition on the HD, rather than having it share a partition with my current o/s. 
 
Next came the partition dialog, and that's when the fun began. I was able to see the 2nd HD and the (empty) partitions it contained. I selected a 40GB partition and was asked to enter a file system choice (at least I knew what that was), and mounting point (assuming sex is not part of the equation, no clue about this term). So I tried various combinations starting with ntfs. From memory there is a choice of 9 file systems and about 6 mounting points; 54 possible combinations; give or take. With the first 10 or 15 trials I was advised that "no root file system had been defined" and told to go back to the partition dialog and correct this problem; no clue how to make this correction. Stubborness kept me at it until I hit upon one combination ("JFS" & "/") that allowed the installation to continue.
 
After specifying another HD partition to be used as the scratch disk, the installation continued, and continued, and continued. After 2 hours of not seeing any movement of the progress bar, I gave up and quit. I tried the whole thing again the next day, with the same results. At this point my feeling is: if the software is this difficult to install, using it must be even more a PITA. But I'm keeping an open mind. Any suggestions anyone?
 
And thanks for allowing me to get this off my chest.:P

---

### Post by themusicalduck on 2011-12-02
You can't install Ubuntu on an NTFS partition. Your best bet is to format as EXT4. Then you will need to set that EXT4 partition mount point as / (this option is found somewhere in the partition dialog). "/" refers to the root of the filesystem (like C:/ on Windows). You could also make another partition (EXT4 or EXT3) and mount it as Home if you'd like, but that isn't necessary.

It might be possible if you don't select "something else" and instead go through the normal process, you can select the right harddrive by selecting "Use entire disk". Just make sure you are able to pick the right drive instead of the Windows one, or everything on the Windows drive will be deleted.

Otherwise the manual partition like you tried should work fine.

---

### Post by mikewhatever on 2011-12-02
Well, welcome, I guess, and thanks for asking.:roll:

---

### Post by oldos2er on 2011-12-03
> **obasan said:**
> Next came the partition dialog, and that's when the fun began. I was able to see the 2nd HD and the (empty) partitions it contained. I selected a 40GB partition and was asked to enter a file system choice (at least I knew what that was), and mounting point (assuming sex is not part of the equation, no clue about this term). So I tried various combinations starting with ntfs. From memory there is a choice of 9 file systems and about 6 mounting points; 54 possible combinations; give or take. With the first 10 or 15 trials I was advised that "no root file system had been defined" and told to go back to the partition dialog and correct this problem; no clue how to make this correction. Stubborness kept me at it until I hit upon one combination ("JFS" & "/") that allowed the installation to continue.

A mount point is a place in the file system where a partition is mounted. "Mounted" simply means the partition is made available for use. "/" is the "root" mount point for the entire system. 

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

Edit: I've changed your subject title to something that might attract more help.

---

### Post by obasan on 2011-12-03
> **oldos2er said:**
> A mount point is a place in the file system where a partition is mounted. "Mounted" simply means the partition is made available for use. "/" is the "root" mount point for the entire system. 
 
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
 
Edit: I've changed your subject title to something that might attract more help.
 
Thanks for that.  I have it up and running (sort of), and am still trying to make it work.

---

### Post by oldos2er on 2011-12-03
No problem. You might want to start a new thread for any further issues, and if you do please give full details about your hardware, any error messages, etc.

Hope you enjoy Ubuntu!

---

