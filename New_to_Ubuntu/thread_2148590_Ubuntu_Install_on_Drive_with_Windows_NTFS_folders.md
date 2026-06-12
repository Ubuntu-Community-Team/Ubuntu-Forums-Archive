---
title: "Ubuntu Install on Drive with Windows NTFS folders"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by skiakbc49 on 2013-05-25
So, I think I screwed up....

I had a drive with one partition with Windows XP installed on it.  There were a few folders (Documents, Pictures, Music, Movies) that were in the generic C:/ directory.  I decided to install Ubuntu on this drive, and installed 12.10 on the drive without reformatting.  I then booted in Ubuntu, and deleted all of the windows program and system files, but left the windows "My Documents" folder and figured I would just access these folders through ubuntu.  I then made links to these folders on my ubuntu Desktop.  I was able to access all of them just fine and figured I had just saved myself time by not copying these huge folders over into the ubuntu home folders.    

One day, this hard drive did not boot...it just hung at "AHCI drive init...". I had purchased a new hard drive and installed ubuntu on the new drive, and then accessed the original drive via an external sata dock.  The old drive showed up with all of my ubuntu files and folders intact, but the big folders that I had in the C:/ directory were not showing up.  Looking at the desktop links, they should have been in the path "/media/disk2/My Documents".  

I then did some research, and realized I may have made a critical error-- Windows and Ubuntu use different filesystems (NTFS vs. ext4) and that is probably what caused my problem on boot.  I am hoping the community can confirm this for me, and tell me what recourse I have to recover those folders that were in the "/media/disk2/" directory.  Is this something I will be able to do myself or do I need to ship the drive off to recovery specialists?  Any ideas?

---

### Post by newb85 on 2013-05-25
If your files on C:/ still existed after you installed Ubuntu, you probably used the Wubi installer.  Wubi is a little bit of a different animal, as it installs Ubuntu on a virtual filesystem within a windows-readable filesystem (NTFS or maybe FAT32).

Installing through Wubi if you're not planning to keep Windows intact is a bad idea (read recipe for disaster).



As to your current situation: the contents of /media are virtual.  They only exist while the system is running.  While exploring from a different HDD or a Live session, you will not find anything there.  You instead need to look on the C:/ partition itself.

---

### Post by fantab on 2013-05-25
How did you install Ubuntu on the 'new HDD'? Is it WUBI or 'true' Ubuntu?

Regarding the XP error on your 'Old HDD', "AHCI drive init..." (wish you had posted the complete error); XP has problem reading the drive when the SATA mode is set to "AHCI" in the BIOS. Had you changed the SATA mode to AHCI when you were still using the 'Old HDD'? 

Ubuntu can read from and write to NTFS partitions. So look carefully by mounting your 'c' partition from Ubuntu those "big folders" might still be there. If not then, you can try Windows recovery tool like, [THIS ONE]("http://www.powerdatarecovery.com/power-data-recovery.html") to recover your DATA since your 'Old HDD' is Windows basically, and only Windows Data Recovery tools work best with Windows partitions and DATA. You may have to pay the Licence fee if you use the above Data Recovery tool if you have DATA more than 1GB. If the DATA is worth it then....

---

### Post by newb85 on 2013-05-26
> **fantab said:**
> How did you install Ubuntu on the 'new HDD'? Is it WUBI or 'true' Ubuntu?

Would Wubi be possible, given the circumstances?  (Windows was no longer bootable...)

---

### Post by Paqman on 2013-05-26
> **newb85 said:**
> If your files on C:/ still existed after you installed Ubuntu, you probably used the Wubi installer.

Not necessarily, the installer will quite happily partition a drive and keep an existing NTFS partition around.

Look in the filesystem. If there's a location called /host then it's a Wubi install, and all the data on the NTFS partition will be in /host. If there's no /host then it's not a Wubi install.

> 
As to your current situation: the contents of /media are virtual.  They only exist while the system is running.  While exploring from a different HDD or a Live session, you will not find anything there.  You instead need to look on the C:/ partition itself.

Correct, however when you mount that partition in your system it will be given a new mount point in /media on the fly. It should be showing as "XXGB disk" or some such in  the file browser. Click on it and you should be able to browse to your data.

---

### Post by newb85 on 2013-05-26
> **Paqman said:**
> Not necessarily, the installer will quite happily partition a drive and keep an existing NTFS partition around.

Look in the filesystem. If there's a location called /host then it's a Wubi install, and all the data on the NTFS partition will be in /host. If there's no /host then it's not a Wubi install.

Good catch.  I misread the OP.  They said they installed Ubuntu "on this drive", and for some reason, I read it "on this partition".  Major difference.

---

### Post by skiakbc49 on 2013-05-26
It was a clean ubuntu install, not wubi.  I double checked and there was no "host" folder.  

As far as the boot error  (AHCI drive init...)  I don't believe I changed any BIOS settings, but I'll check that when I get home tonight.  It was a while back, so I apologize for my fuzzy memory.

---

