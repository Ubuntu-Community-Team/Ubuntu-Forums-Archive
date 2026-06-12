---
title: "ram indexing"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by win22lin on 2012-05-14
Hello and thanks for the forums.    I am interested to know how Ubuntu uses RAM concerning indexing.    Vista indexes predefined files/directories/system-components into RAM for quick access.  When you touch the win-key (Super-L) and start typing, a search instantly begins.  This is perhaps the most powerful benefit M$ has developed, IMHO.    I perform a search (search = terminal) in Ubuntu and it is similarly quick, but I have a fresh install with no personal files.  So I need a little information to fill this void.

---

### Post by roelforg on 2012-05-14
Someone correct me if i'm wrong, but i don't think it does any indexing.

---

### Post by prshah on 2012-05-14
> **win22lin said:**
> I am interested to know how Ubuntu uses RAM concerning indexing.    Vista indexes predefined files/directories/system-components into RAM for quick access.  When you touch the win-key (Super-L) and start typing, a search instantly begins.  This is perhaps the most powerful benefit M$ has developed, IMHO.    I perform a search (search = terminal) in Ubuntu and it is similarly quick, but I have a fresh install with no personal files.  So I need a little information to fill this void.

Some slight misconceptions:
a) Vista does not load search indexes into RAM. However, common results may be cached.
b) This search (called "live search") was NOT developed by Windows. Among others, Google Desktop (now discontinued) and AltaVista had notable desktop search software.

Some pointers for functionality:
c) On Ubuntu/Linux, you can use Beagle for similar functionality.  You can also try to get hold of an old installer for Google Desktop for Linux.
d) In the command line, the "locate" tool (in conjunction with update-db) offers a similar function for FILENAMES only. The new Unity interface also offers a similar, though not quite as efficient search for programs and recently used files (NOT CONTENTS).

---

### Post by Lisiano on 2012-05-14
As prshah said, there is no RAM precaching of your search index, if there was, then if you were a developer and had tons and tons of source files, the Start menu would take a long time to open due to said caching and you would notice that your HDD is seeking a lot.

Either way, when you search using the Start menu, it looks up stuff in an index on the disk, the results you get are cached though.

Same in Linux, when you open anything, that item is cached in memory and the next time you start or open that thing, it will start/open almost instantly. For searches, the same applies, when you look for something, it checks a local database and caches the results so the next time you search for the same thing, it finds it faster, though the RAM cache is dropped whenever more memory is needed by applications or when you try to open a movie or a really big file, or if you reboot.

If I confused you, look here and it should make it more clear as to what Linux does with free RAM.
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

EDIT: A good example of caching would be to try running this
```
time locate .desktop
``` This will try to find every file on your system that ends on .desktop, now write down the time, then rerun the command, you should notice that the time it took to complete the search took less time. That is caching, if it precached, it would take roughly the same amount of time.

---

