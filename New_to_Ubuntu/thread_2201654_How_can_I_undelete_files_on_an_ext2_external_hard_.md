---
title: "How can I undelete files on an ext2 external hard drive?"
date: 2014-01-25
forum: New to Ubuntu
---

### Post by palawanbeach on 2014-01-25
[SIZE=4]What must I do to (try to) undelete files from a 1 TB external hard drive with an ext2 filesystem?


[/SIZE][COLOR=#696969]Backstory
I ran *shred *on an external hard drive that I borrowed, hoping that the files I temporarily stored on it cannot be recovered. But I want to verify that the files are in fact unrecoverable. 
[/COLOR]

---

### Post by sudodus on 2014-01-25
Try with [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) and please report your result.

If you really wiped the whole drive with shred, I think you will find nothing. Extremely expensive methods might manage to detect magnetic traces and interpret them.

See also this link [best way to wipe a drive]("http://ubuntuforums.org/showthread.php?t=2124829")

---

### Post by palawanbeach on 2014-01-25
sudodus, thanks for your reply.

The external hard drive was in ext2 when I temporarily stored my files on it, and while I ran shred. I then ran gparted and changed to fat32. Does changing filesystem help me in my goal of making my files unrecoverable?

---

### Post by sudodus on 2014-01-25
The advice to use ext2 was due to the fact that ext2 does not use journaling, which might preserve some data. Repartitioning might obscure the data for some people, but not for real experts. PhotoRec uses the raw data stored on the disk surface, not the file system or partition table. So if there are only random data from shred, you should find nothing (unless the unlikely happens, that it will be Shakespeare's Collected Works).
'

---

### Post by palawanbeach on 2014-01-25
sudodus, thanks for informing me that changing filesystems doesn't help my goal.

---

### Post by palawanbeach on 2014-01-26
Report:
On ext2 filesystem external hard drive, I put files (wav, aup, mp3, mp4, html, pdf, jpg, ogv, sh, png, etc.). 
I then moved them (using Nautilus) back to my internal hard drive. I then ran gparted and changed to fat32. 
I then ran shred with 5 passes. 
I then put 2 png onto the external hard drive. 
I then deleted one PNG file (using nautilus), and made sure to delete the resulting .Trash folder.
I then ran PhotoRec.
PhotoRec only found the one PNG I deleted after shredding.  I'm happy to report that PhotoRec did not find any files that I shredded.:)

Question: Is PhotoRec as good as or better than the Windows program called Recuva?

---

### Post by sudodus on 2014-01-26
I think you can relax now. The drive is wiped well enough. I don't know Recuva, but I think PhotoRec is good enough in finding what is left on the drive surface.

---

### Post by palawanbeach on 2014-01-26
Ok. I hope you're right that I can rest easy now, sudodus.;) Because I'm now going to return the external hard drive to the owner.

---

