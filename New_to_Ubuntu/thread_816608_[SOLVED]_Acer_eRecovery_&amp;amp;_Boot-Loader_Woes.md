---
title: "[SOLVED] Acer eRecovery &amp;amp; Boot-Loader Woes"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Jesdisciple on 2008-06-02
I installed v7.10 on my Acer laptop, and it worked fine.  But I was hoping to dual-boot it, and when I tried booting WinXP I ran into Acer eRecovery.  I entered my password (which I found in aimdrs.dat on the PQService drive via Ubuntu), and got some error, the content of which I don't recall.

Frustrated, I booted on the Ubuntu Live CD and formatted my hard drive except the partition where I believe WinXP to be.  Then I tried to boot but ran into Error 17, which I think indicates that GRUB is missing.

I found the GRUB project site and tried to find the most recent GRUB Legacy (because it's stable), but 1.98 is called GRUB2 and the border version isn't indicated.  **What's the latest release of GRUB Legacy?**

Also, I apparently need to download several GNU libraries to run GRUB; **can I get a comprehensive list of those?**  (The 1.98 release has a list of several including "Other standard GNU libraries" or the like, which isn't very helpful.)

And of course, **am I trying to apply the correct solution?**

Thanks!

---

### Post by Xiong Chiamiov on 2008-06-03
[SuperGrubDisk]("http://supergrubdisk.org") will save you a lot of time.  It will guide you through installing GRUB and getting it configured the way you want.  You can also use it to easily boot into a certain partition to see if it works before adding it to GRUB.

---

### Post by Jesdisciple on 2008-06-03
When I tried to burn SuperGrubDisk to a blank CD-R (via [ISORecorder]("http://isorecorder.alexfeinman.com/isorecorder.htm")), I got error 80010105 and Windows (on a different computer) said IMAPI had encountered a fatal error.  ???

EDIT: And yet I find files on the CD; is it safe to boot off of that?

---

### Post by Jesdisciple on 2008-06-04
Well, I left the CD in the other computer while waiting for a reply.  When it booted up this morning I found SuperGrubDisk apparently uncorrupted, lol.

Now, what do I do with SGD?  I'm exploring the wiki but not recognizing any relevant signposts yet...

---

### Post by Jesdisciple on 2008-06-06
Well, come to find out Windows was gone anyway.  I used the second Guided installation option (which appeared after I went back and forth several times) that promised to only take the pieces of the hard disk that weren't already taken.  I guess I misunderstood it...

So I reinstalled Ubuntu using the first Guided option and it took the entire hard drive.

---

