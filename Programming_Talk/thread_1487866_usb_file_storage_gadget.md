---
title: "usb file storage gadget"
date: 2010-05-19
forum: Programming Talk
---

### Post by teachop on 2010-05-19
Don't know where to ask this...

I have Linux ported to an embedded device.  It can look like a mass storage device, like a flash stick or camera or whatever.  I have g_file_storage loaded up with a backing file to do this.  My windows machine can use this just like a flash drive, and linux can get the files out later with the loop driver.

All good.  However, if Windows deletes files, it creates a recycle bin on the backing file.  This is bad in my case, I want it to just delete, like it would a regular USB flash stick.

Any ideas how to get windows to think that way?  Is there some paramteter of my driver that needs set?

---

### Post by yaaarrrgg on 2010-05-20
If I understand correctly, you might try using rm under cygwin.  That should do a hard delete without putting it into a recycle bin.

---

### Post by teachop on 2010-05-20
I need to have the device act like a flash stick in the general case, so users don't do any additional action.

If I run modprobe on g_file_storage with "removable" option, it causes Windows to see the device as removable, however, this doesn't prevent the creation of a recycle bin on the device.

I tried building the driver with several changes in the Inquiry response, and nothing helped there.

One characteristic that I see is with all the flash sticks, Windows say partition type is "Not Applicable".  With my device, it say partition type is "MBR".  I don't know what this means, but perhaps the creation of my backing file partition/format is the problem.  Have played with that a lot to no avail as well.

---

### Post by yaaarrrgg on 2010-05-20
Is it possible to partition the device (so the first one holds the recycle bin)?  I don't think windows would alter the MBR.

---

### Post by teachop on 2010-05-20
I did some experiments with 2 partitions, without hitting on the right formula.  But...

Somehow, I got this working.  The backing file is almost identical to the one created by the "official instructions", except smaller.  It was not working, but after going back to it and reformatting from Gparted (done that many times), it finally worked.  Windows likes it and makes no recycle bin.  No clue what the change was, having tried so many combinations with partitioning and formatting with different utilities and from different OS, meh.

I copied the working file into my rfs image, created a system from scratch, and took a walking tour of plug-n-play operating systems in the office.  It works with them all, no problem.

Now I need to learn what the original problem actually was.  Sure seems to have been backing file related.

---

