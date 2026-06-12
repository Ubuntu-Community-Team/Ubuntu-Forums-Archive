---
title: "Data Transfer Rate"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by qaissi on 2011-10-19
Ok so I am transferring data from a Fatom 2TB external drive over eSata connection.  And I mean a massive amount of data frequently.  It is getting moved to a 1TB internal WD sata drive.

Windows 7 has an almost consistant data transfer rate of 61 MB per Second.

Ubuntu 11.10 is doing the same transfer at about 20 MB per Second.

So yes I am used to the transfer dialogue box lying to me in both windows and ubuntu.

But today I did a comparision and in Windows 7 it took 2.5 hours to transfer 584 GB.

I deleted that transfer and did it again in Ubuntu and it took 4.25 hours.

So.  I am not going to bother arguing about MB vs Mb and which dialogue lies the most and which is the most accurate.  Instead I will simply state that an addition 1.75 hours to transfer the same data from point a to point b is obviously wonky.

Has anybody got any suggestions that don't include which bridge to jump off of.  lol

---

### Post by 3rdalbum on 2011-10-19
If the destination drive is formatted as NTFS, this would explain it.

NTFS writing is slower than writing to a native filesystem.

---

### Post by qaissi on 2011-10-19
Thanks for the quick response.

Both drives are formatted as NTFS.  But are we really willing to accept that as a definative statement and that nothing can be done about it?

I do realize that both windows and Ubuntu can do FAT32 but that is not really a valid option either.

So just accept it?  That hardly seems like an answer for an OS that is trying to replace windows does it?

---

### Post by 3rdalbum on 2011-10-19
> **qaissi said:**
> Thanks for the quick response.

Both drives are formatted as NTFS.  But are we really willing to accept that as a definative statement and that nothing can be done about it?

You could port the NTFS-3G driver to be native, and therefore faster.

The NTFS-3G developers have always focussed on improving stability and being able to work with damaged filesystems, rather than optimising and improving speed.

I don't know how fast your CPU is, but a faster CPU tends to result in a faster transfer in Ubuntu.


> I do realize that both windows and Ubuntu can do FAT32 but that is not really a valid option either.

There's an Ext2 driver for Windows.

> So just accept it?  That hardly seems like an answer for an OS that is trying to replace windows does it?

Once you've replaced Windows, you don't need to be using NTFS drives :-)

---

### Post by qaissi on 2011-10-19
> You could port the NTFS-3G driver to be native, and therefore faster.


Could you give a little more detail about this.

> Once you've replaced Windows, you don't need to be using NTFS drives

Unfortunately I am repairing Windows computers so NTFS will always be an issue.  I am just surprised that Ubuntu is willing to accept slow data transfer rates from NTFS drives since they are trying to convince people to switch from windows.  NTFS will always be an issue to Ubuntu.

> There's an Ext2 driver for Windows.

Got it and using it - thank you.

---

### Post by 3rdalbum on 2011-10-20
Ahh, I see your problem then.

There's no solution, other than rewriting the current NTFS driver. Of course, you'd need to be a pretty reasonable kernel programmer to do that. Sorry.

---

