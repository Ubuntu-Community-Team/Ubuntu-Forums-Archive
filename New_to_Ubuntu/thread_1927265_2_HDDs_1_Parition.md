---
title: "2 HDDs 1 Parition?"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by d4m1r on 2012-02-17
Hey guys, I consider myself an expert when it comes to HDDs...except for RAID related questions [IMG]http://files.overclock.net/images/smilies/biggrin.gif[/IMG] Anyway, I'd actually prefer a software solution than having to actually setup RAID but I am looking to:

-join 2 1TB harddrives into a single 2TB NTFS partition
-one is a Western Digital Black (7200rpm) and the other is a Samsung Spinpoint (7200rpm)
-the WD is external (eSata enclosure) and the Samsung is using SATA II

If need be, I'm pretty sure I can fit the WD inside the case if whatever I need to do isn't support over eSata.

Is there software out there that will reformat 2 harrdrives into a  single partition or will a RAID setup be required? Thanks in advance  guys!

---

### Post by ajgreeny on 2012-02-17
I'm pretty sure it can be done with LVM partitioning, but Ubuntu is not well set up with any LVM packages by default, so you will need to install whatever is needed.

Have a search around and you may figure out how it's possible; I haven't got an inkling, I'm afraid.  I only used LVM by mistake once when I installed Fedora which uses it by default.  However ubuntu which was on the same machine could not then see the Fedora install, so I got rid of LVM and used standard partitions instead.

---

