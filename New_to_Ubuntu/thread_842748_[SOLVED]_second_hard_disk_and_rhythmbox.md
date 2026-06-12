---
title: "[SOLVED] second hard disk and rhythmbox"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by azery on 2008-06-27
I recently installed ubuntu (8.04) but I'm having a number of problems. Being new to Linux, I'm looking here for some help. I'll post different problems in different topics, in order improve the readability of the answers.

The second problem is rhythmbox:

My pc has two hard disks: 1 with a windows and linux partition and a second hard disk with user data (music,pictures, etc, so that the data can be easily accessed from both windows and linux) This second hard disk also contains my mp3 collection.

If I start rhythmbox, he will remove all my music from its database. As far as I can see, this is caused by the fact that the second harddisk with the music is not yet mounted. I suspect that Rhythmbox scans its database for changes and it no longer sees the music files. If I first access the second harddisk via e.g. a filebrowser, then it appears on the desktop and in addition, rhythmbox will not empty its database.

The behaviour of ubuntu suprises me here (but hey, maybe i'm thinking windows xp like). I can perfectly well understand that I should mount an external HD, usb device, etc, but this is an internal harddisk. 

Is it possible to let rhythmbox mount the drive?
Would it be better to let ubuntu mount the drive at boot time?
Will other progrmas have the same problem (e.g. F-spot)?

---

### Post by Bastaard on 2008-06-27
Mount the drive at boot time, for ntfs see [http://ubuntuforums.org/showthread.php?p=4863122#post4863122](http://ubuntuforums.org/showthread.php?p=4863122#post4863122) or edit your fstab to do it, there's many tutorials on doing this.

Or use different software. I'm not sure if Amarok behaves the same way but I think it doesn't and it's the best piece of audio software I've ever seen. Be sure to check it out.

---

### Post by azery on 2008-07-13
problem solved with NTFS configuration tool.

thanks for the info...

---

