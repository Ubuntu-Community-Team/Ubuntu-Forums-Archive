---
title: "Flash DriveConstantly Flashing And Suddenly Not Showing On Ubuntu Desktop"
date: 2020-03-20
forum: New to Ubuntu
---

### Post by mogruith2 on 2020-03-20
Hi,

Today for some reason the flash drive, which was working perfectly on my Ubuntu 18.04 laptop is not showing on the desktop. On connection
 it just flashes constantly.

Checked all the ports with other USB sticks and being detected no problem.

Run daily update/upgrade.

Tried the flash drive on a Windows 10 system and its operating without any issue.

Via terminal ran sudo fdisk -h and -l but the USB drive is not showing.

Yet via 'Show Applications' -> Disks it shows up, albeit displaying as 'no data' See print-screen via link below

[[IMG]https://ibb.co/48RkQXz[/IMG]]("https://ibb.co/48RkQXz")

I have no desire to wipe/delete any data from the flash drive, especially as it works in my other laptop, but wondered if there's a solution
to this issue?

Hope someone can help me get this issue fixed. Thanks

---

### Post by Impavidus on 2020-03-20
Not much more than a wild guess, but there may be filesystem damage involved. As the drive works on WIndows, it must use a Windows filesystem. Windows is better than Linux at working around filesystem damage on Windows filesystems. Some filesystem checks on Windows might help.

---

### Post by oldfred on 2020-03-20
If used in Windows, did Windows update & turn fast start up back on?
Fast start up can set hibernation flag on all NTFS partitions.

I thought I did see where Windows knew about issue as users may want to use with another system, but did not see details.

---

### Post by mogruith2 on 2020-03-20
Impavidus, thanks for the suggestion, I ran the Flash Drive through a file system check on my Windows 10 laptop and it showed no issue and required no repair.

---

### Post by mogruith2 on 2020-03-20
Fred, thanks for your comment. I booted my W10 laptop first and then plugged in the  flash drive, so saw none of the responses you mentioned. As the USB drive has been working
without any issue all this time on both the Ubuntu and Windows laptop I wonder if an update done yesterday may have triggered the issue.

---

