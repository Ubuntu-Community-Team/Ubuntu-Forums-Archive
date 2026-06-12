---
title: "Creating several instances of a persistent (partition!) Ubuntu live USB pendrive"
date: 2014-12-15
forum: New to Ubuntu
---

### Post by lavikl on 2014-12-15
Hi All!
I have prepared a persistent Ubuntu live USB pendrive with a large (10Gb) casper-rw partition which holds all kinds of bioinformatics tools for my students.
I wish to make several instances of this pendrive, so the students could use it as a standalone linux for a class I'm giving.
I need to prepare 20 pendrives which will be exact copies of my master-pendrive. These instances must  include every partition and file from the master-pendrive and of course be bootable just like the master-pendrive.
I've been looking at Clonezilla but I'm not sure that this is the tool I need. I might be wrong but clonezilla makes images (not bootable) of the source right ?

I would appreciate a recommendation on tools to make these bootable instances (which will include all partitions and files)

Thanks!

---

### Post by sudodus on 2014-12-15
Hi again *lavikl*,

Yes you can do it with ***Clonezilla***. It can create a cloned copy of the whole drive, and it can create a compressed image (of the same whole drive).

So you can either clone directly from the pendrive or from the compressed image. Maybe it is better to create a a compressed image and expand it into the 20 pendrives.

It is also possible to do with ***dd***, but

1 - dd is more risky - it is nick-named 'disk destroyer' for a reason: it does what you tell it to do without questions, and if you tell it to do something you did not intend to do, for example by a typing error, you might destroy important data.

2 - Clonezilla is faster - only used blocks in partitions are saved and restored (it skips the un-used block, which saves time and effort).

But there is one problem. You can clone to drives of at least the same size, but not to smaller drives, and USB pendrives can vary in size. Often they are not exactly the nominal size, sometimes bigger, sometimes smaller (quite often smaller than the nominal size), so this can be a problem, if you are not aware of it, and plan how to avoid it.

-o-

I have been using Clonezilla for complete backups for years now.

---

### Post by sudodus on 2014-12-15
What computers will your students use? And what version of Ubuntu did you use? Can you expect it to work in all the computers?

If you can run in BIOS mode, there are ways to make the pendrives independent of the size (as long as there is space enough for the files). But if you need to run in UEFI mode, I think the Clonezilla method is best.

---

