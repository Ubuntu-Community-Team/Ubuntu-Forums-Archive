---
title: "mv -b reliable?"
date: 2011-02-16
forum: Programming Talk
---

### Post by jdb91 on 2011-02-16
Hi all, 

Just doing a simple archiving script and was just wondering whether mv -b does a checksum to check that the origin and dest file are identical before removing the original, or is it more wise to do a cp with a checksum before rming?

Cheers.

---

### Post by slavik on 2011-02-16
rsync

---

### Post by psusi on 2011-02-16
You seem to misunderstand what -b does.  If cp would otherwise overwrite the destination file because it already exists, -b has it rename the existing file instead.

---

### Post by wmcbrine on 2011-02-17
mv does not validate, no.

If you're moving a file within the same filesystem, then mv doesn't rewrite the file data per se. If you're moving a file to some other filesystem, and you think your media is unreliable, then you probably don't want to use mv. cp, cmp, rm. (I don't see how a checksum is better than a simple cmp.)

---

