---
title: "How to recover lost storage space after format?"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by beyondwithinitself on 2011-09-30
I recently reformatted my external hard drive from ext4 to NTFS in order to be able to use it with my Windows partition.  Unfortunately, I overestimated the power of a format, so after backing up to a different drive, I did not manually delete the old files from the drive.

As a result, I am looking at an "empty" drive with no visible files but with almost third of its space showing up as "used."  Apparently the old files were not deleted during format but the access to them is gone.

What can I do to regain full storage capacity?  Is there a way to effectively wipe the drive of its non-existent (or at least invisible) files?[LEFT][/LEFT]

---

### Post by wildmanne39 on 2011-09-30
Hi, you probably did not reformat all the partitions just some of them, run the livecd and use gparted to format the rest.
That is if you have not installed windows already, otherwise you can format it with windows but I do not know how to relciam the space by drive C: it will want to give it another drive name.
Thank you

---

### Post by HereInOz on 2011-09-30
You may be able to use an undelete program but it is probable that the best way to get the data is to send the drive to a professional data recovery company.  

If you are were in Australia I could refer you to a good one, but you are probably not, so I am of no use to you there.  Data recovery companies do not do things for free, so expect to pay.  If you can't afford their services, try this:
[http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)

It looks like it might help in some way.

---

### Post by beyondwithinitself on 2011-09-30
It was an external hard drive, so I wouldn't need to bother with any Windows software.. Only music, video, documents and stuff like that.  I'd just like to be able to use it between systems -- Gparted says the drive did successfully get formatted to NTFS.  

I just made the mistake of not deleting the files (~600 gigs) manually and now I only have 1.2 TB free instead of 2 TB.  I want to reclaim that space but there are no files visible that I can delete.

---

### Post by HereInOz on 2011-09-30
Sorry, misread the post.  I initially thought you wanted to recover the files.  My apology.  Should have read your post better in the first place.

---

### Post by beyondwithinitself on 2011-09-30
I do not need to recover any files.  I want to get my storage space on the drive back to what it was initially before format.  There was about 600 gigs of files that should have been erased in the format, but are still taking up space for some reason.  I'm trying to reclaim that space.

---

### Post by beyondwithinitself on 2011-09-30
> **HereInOz said:**
> Sorry, misread the post.  I initially thought you wanted to recover the files.  My apology.  Should have read your post better in the first place.

All good!  Any ideas welcome. :)

---

### Post by wildmanne39 on 2011-09-30
Hi, this might help, but I do not know that for sure, some times gparted does not see all the partitions so have a look at this link.
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
Thank you

---

### Post by beyondwithinitself on 2011-09-30
GParted shows the NTFS partition as being 1.82 TB and that all but around 100 megs are unused... so, is this an issue of Nautilus just not displaying the correct drive information?

---

### Post by beyondwithinitself on 2011-09-30
It appears my hunch was correct.. sort of.  Upon closer inspection in GParted, I noticed the partition on the drive changed from sdc1 to sdd1.  So, I opened terminal and entered the command:

sudo mount -t ntfs /dev/sdd1 /media/sdc1

All appears to be back to normal!  The "space free" is showing up correctly in Nautilus as 1.8 TB.  I may have to change the UUID in fstab to have the drive automount at startup, but aside from that I'd call this SOLVED!

Thank you all for your suggestions.

---

### Post by wildmanne39 on 2011-09-30
Hi, that is great did the link I gave you help?
Thank you

---

### Post by beyondwithinitself on 2011-09-30
I just did something FAR worse.... in the process of mounting dev to media, I believe I overwrote where my backup external drive (with all the files) was sitting.  In the process, I seem to have damaged the MFT.

I fixed the boot sector with TestDisk, but both the MFT and the MFT mirror appear to be bad.  I tried using chkdsk with windows to no avail.

---

