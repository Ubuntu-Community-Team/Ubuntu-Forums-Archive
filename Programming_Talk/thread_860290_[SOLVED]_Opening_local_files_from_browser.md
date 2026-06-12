---
title: "[SOLVED] Opening local files from browser?"
date: 2008-07-15
forum: Programming Talk
---

### Post by billynomates on 2008-07-15
Hi, I'm currently implementing [FLAX]("http://www.flax.co.uk/index.shtml") to make all files and folders on a drive searchable.

However, I cannot figure out how to open the files (the program 
works perfectly and allows me to search the files).

So my question is, to open a local file from a link in a browser (preferably on Firefox and IE), what do I make the link? 

I've tried file:/[path], file:///[path], file://///[path] and all variations thereof. Any ideas?

---

### Post by nanotube on 2008-07-15
> **billynomates said:**
> Hi, I'm currently implementing [FLAX]("http://www.flax.co.uk/index.shtml") to make all files and folders on a drive searchable.

However, I cannot figure out how to open the files (the program 
works perfectly and allows me to search the files).

So my question is, to open a local file from a link in a browser (preferably on Firefox and IE), what do I make the link? 

I've tried file:/[path], file:///[path], file://///[path] and all variations thereof. Any ideas?

heh, you tried a lot, but you missed one:
```
file://
```
(analogous to "http://" and friends)
note that for an absolute path (which is what you [almost?] always use in the url bar), you'd end up with three slashes:

**file://**/home/yourusername/somefile.html

but the actual protocol is "file://"

---

### Post by billynomates on 2008-07-16
Ah, excellent. The only one I didn't try. Thanks a lot.

---

