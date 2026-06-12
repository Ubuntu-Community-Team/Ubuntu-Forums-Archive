---
title: "Urllib2 without high cpu usage?"
date: 2010-02-09
forum: Programming Talk
---

### Post by NoBugs! on 2010-02-09
I'm using urllib2 to download files, but there seems to be a bug in the read() function. It uses way too much cpu, even when I use it in a while loop such as:

```

            next = a.read(1000)
            total+=next
            while (len(next)>0):
                next = a.read(1000)
                total += next

```
A sleep() in the while loop helps, but slows the download.

Apparently it is a [bug in python]("http://bugs.python.org/issue1411097"), is there any way to get around this?

---

### Post by wmcbrine on 2010-02-09
It's not clear to me that the bug you link to is related to the problem you describe.

I suspect you'll see better performance if you increase the size of the chunk you read. Like, 1000000 instead of 1000.

---

### Post by NoBugs! on 2010-02-10
Yeah, after further testing it seems urllib2 isn't the problem, it's something else. Maybe the downloader should be in a thread.

---

### Post by wmcbrine on 2010-02-10
> **NoBugs! said:**
> Maybe the downloader should be in a thread.I can't see how that would help.

Did you try increasing the block size?

---

