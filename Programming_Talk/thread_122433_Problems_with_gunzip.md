---
title: "Problems with gunzip"
date: 2006-01-27
forum: Programming Talk
---

### Post by sraised2the3rd on 2006-01-27
I downloaded the three cd's of Oracle 9i: Standard/Enterprise Edition and they came compressed as a .gz. The instructions on oracle's website say to run gunzip on the file like so:

    Uncompress the file using "gunzip". Eg.: "gunzip amd64_db_9204_Disk1.cpio.gz"

So I did and got these results:

    gzip: amd64_db_9204_Disk1.cpio.gz: unexpected end of file

So I was wondering if anyone had encountered this problem before and if anyone knew of another way or a workaround to this problem.

---

### Post by Burke on 2006-01-27
This may seem like the obvious non-answer, but I would recommend making sure the file you have is actually complete. Was your download interrupted?

and btw, you don't actually have to run gunzip manually, you can just right-click and click extract.

---

### Post by mexoner on 2008-10-26
Hi 
there is a package called cpio by which you can extract the archive file 


regards 


> **sraised2the3rd said:**
> I downloaded the three cd's of Oracle 9i: Standard/Enterprise Edition and they came compressed as a .gz. The instructions on oracle's website say to run gunzip on the file like so:

    Uncompress the file using "gunzip". Eg.: "gunzip amd64_db_9204_Disk1.cpio.gz"

So I did and got these results:

    gzip: amd64_db_9204_Disk1.cpio.gz: unexpected end of file

So I was wondering if anyone had encountered this problem before and if anyone knew of another way or a workaround to this problem.

---

