---
title: "[C] Memory leak using CUPS libraries"
date: 2008-05-06
forum: Programming Talk
---

### Post by nvteighen on 2008-05-06
This may be an overspecific question regarding Apple's CUPS API ([http://www.cups.org/documentation.php/api-cups.html](http://www.cups.org/documentation.php/api-cups.html)).

I'm using the cupsGetDests() function to get the list of available printers. As it uses dynamic memory allocation, I have to use cupsFreeDests() afterwards... But no matter what I do, I get a 170000 bytes big memory leak (according to valgrind: over 9200 mallocs, and only 2900 free'd). Using free() makes libc complain...

So, question: Has someone experienced something like this before? I've been googling around and haven't find any reference to a memory leak in CUPS.

If not, possibly I'm causing this and I'm the one to blame, not Apple.

Thanks!

---

### Post by nvteighen on 2008-05-06
False alarm: it's valgrind's fault, not detecting memory managed by SSL and other surrounding buffers used by libcups. Refer to [http://www.cups.org/str.php?L2437](http://www.cups.org/str.php?L2437)

Sorry if someone was annoyed because of this.

---

