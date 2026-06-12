---
title: "JFS Defrag"
date: 2008-07-15
forum: Programming Talk
---

### Post by solarwind on 2008-07-15
Anyone interested in making a JFS offline defrag tool with me?

---

### Post by articpenguin on 2008-07-15
I would if i knew how to code but.

  Do you know all the internal structures of JFS. Like the dtree and AGs and all that?

---

### Post by solarwind on 2008-07-15
> **articpenguin said:**
> I would if i knew how to code but.

  Do you know all the internal structures of JFS. Like the dtree and AGs and all that?

I know how to code, so that's not a problem. I downloaded the JFS structures and documentation PDFs. I'll be able to figure that out.

The biggest thing is the defrag algorithm.

---

### Post by articpenguin on 2008-07-15
IRC the JFS maintainer said he would help people if they were to right a defragger.

---

### Post by solarwind on 2008-07-15
> **articpenguin said:**
> IRC the JFS maintainer said he would help people if they were to right a defragger.

Pardon me, but I don't understand that sentence. Could you rephrase?

---

### Post by articpenguin on 2008-07-15
There was a defragger for JFS. But it never got ported. David said that it only defragged free space but not files.

 I think if you ask The jfs maintainer about writing a defragger for JFS he will give you some help

---

### Post by samjh on 2008-07-15
> **solarwind said:**
> Anyone interested in making a JFS offline defrag tool with me?

JFS defrag exists for OS/2, but wasn't ported to Linux.

You should try to email the developers for advice on your project.

See: [http://jfs.sourceforge.net/](http://jfs.sourceforge.net/) (scroll to "JFS Core Team")

---

### Post by solarwind on 2008-07-15
> **articpenguin said:**
> There was a defragger for JFS. But it never got ported. David said that it only defragged free space but not files.

 I think if you ask The jfs maintainer about writing a defragger for JFS he will give you some help

Yes, the defrag function still exists in the JFS source tree in the kernel source. It never got ported because ioctl never got implemented on Linux (I think). And yes it only defrags free space. I think I can write an algorithm to defrag very well if I got all the low level stuff down like moving files, inodes and restructuring things - that's the biggest challenge for me.

---

