---
title: "NTFS formatted USB loses data, FAT 32 formatting doesn't"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by venom104 on 2012-09-17
Okay here is the thing.

I had an 8 GB USB flash drive. I formatted it NTFS and it worked fine for years. Then weird things started happening...Eventually (only on ubuntu) it would mount itself after I unmounted it. 

Anyway, I formatted it to NTFS thinking it might have had some corrupt sectors or something and gave it to my brother. I ordered a new one and formatted it as NTFS...then the same thing started happening. 

At one point, there was one part of my flash drive that would spit out a read error whenever I opened it. I had to run checkdisk under windows to repair it, then I backed up my data, formatted it NTFS again, then copied my data over.

Then I can't access the same folder again! 

Thinking it was a bad drive, I got it RMAed to kingston. I received a new one in the mail, and formatted it as NTFS...well...right after I copied my data over, I unmounted it and remounted it. All my data was gone.

So I formatted the drive as FAT 32 and I haven't had problems since.

I was hoping to keep it as NTFS as FAT 32 can't handle more than a 4GB file and I go back and forth between windows, but I'm over it. 

I'm just wondering what the problem could be. I dual boot ubuntu and windows 7; I've never had a write error or anything like that under windows. Also, why did my old flash drive work fine for years as NTFS?

Can someone explain this to me?

---

### Post by tienlbhoc on 2012-09-17
your ubuntu can be error, format it with ubuntu cd or the best is format partion and reinstall

---

### Post by venom104 on 2012-09-17
> **tienlbhoc said:**
> your ubuntu can be error, format it with ubuntu cd or the best is format partion and reinstall


Actually I run a few different linux distros on different computers. Same thing happens on linux mint debian edition, so I would assume this eliminates a software issue.

---

### Post by irv on 2012-09-17
When sharing files between Linux and Windows under NTFS format problems will arise because if a file or folder does not close properly it will get corrupt. On all my USB driver I keep them formatted with Fat32 for this reason. Fat32 seems to close everything properly so there is no problems with corruption. There, now you have the answer.

---

### Post by Paddy Landau on 2012-09-17
> **venom104 said:**
> …. Same thing happens on linux mint debian edition…

[LIST]
[*]Does the same thing happen on Windows? If so, it is hardware. Try a different make.
[*]Otherwise, does the same thing happen on non-Ubuntu distros? (Mint is Ubuntu-based — try something like [Fedora]("http://fedoraproject.org/") or [Crunchbang]("http://crunchbanglinux.org/").) If so, it is a software issue: Linux.
[*]Otherwise, it is a software issue: Ubuntu.
[/LIST]
 
If you don't need to access your USB from Windows, try formatting to ext4. NTFS and ext4 are not really recommended because of the extra writes to the flash, but it's worth a try.

---

### Post by Paddy Landau on 2012-09-17
> **irv said:**
> … if a file or folder does not close properly it will get corrupt.
If that is what is happening, try *Safely Remove* with the disk before physically removing it. You can do this from Disk Utility. It should always ensure that the file system has been properly closed.

---

### Post by irv on 2012-09-17
> **Paddy Landau said:**
> If that is what is happening, try *Safely Remove* with the disk before physically removing it. You can do this from Disk Utility. It should always ensure that the file system has been properly closed.

You are right on this, I have notice Window users are in a habit of just pulling the USB out with our using safely removing. Linux is not so forgiving. I have corrupted my files on my Nook because of this. You can also corrupt file on cameras and any other devices you plug into your computer.

---

### Post by 1clue on 2012-09-17
I use USB sticks all the time, moving data between disconnected Mac, Linux and Windows systems.  And an aftermarket car stereo.

The ONLY filesystem which is installed by default on all 3 computer operating systems is FAT.  The only filesystem understood by the stereo is FAT, and to make things worse it only understands about 4g of data, then it loses track.  All 4 systems understand the extra naming extensions.

Also, the guilty bit for data loss is a cache in the driver.  The driver generally has a cache, and that cache is not always immediately flushed.  If you don't "safely remove" or whatever it is on your current OS then you probably didn't get your cache flushed, and that's where the data corruption happens.

---

