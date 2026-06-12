---
title: "Using CVS to Pull Source Code"
date: 2008-04-17
forum: Programming Talk
---

### Post by tonyr1988 on 2008-04-17
[http://wiki.services.openoffice.org/wiki/Odf4j](http://wiki.services.openoffice.org/wiki/Odf4j)

I'm trying to download that through CVS. This is what they give me:

> To checkout the source code from the CVS repository use : pserver:anoncvs@anoncvs.services.openoffice.org:/cvs as CVSROOT and checkout odftoolkit/odf4j.

(there isn't really a space between : and p at the beginning of "pserver:anon...", but it avoids causing :p)

I've installed cvs, but don't really know where to go from there. I've heard CVS talked about tons of times, but have never used it - I figure now would be a good time to learn. So....teach me the basics! :P

(all the tutorials I've seen online deal with uploading your own source code to your own cvs repository....I want to know how to do stuff on the other end)

---

### Post by tonyr1988 on 2008-04-17
I used this command:

> cvs -d :pserver:anoncvs@anoncvs.services.openoffice.org:/cvs checkout odftoolkit/odf4j

And it seemed to work - is that the proper way of doing it, or am I wrong?

---

### Post by geraldm on 2008-04-17
looks OK to me.   You should already know if it has worked by the code that you received.  I have been following a cvs project, and from that I usually tar and compress what I downloaded.  Next time, after uncompresssing and untar the saved source,  instead of checkout I would use update.  

Gerald

---

