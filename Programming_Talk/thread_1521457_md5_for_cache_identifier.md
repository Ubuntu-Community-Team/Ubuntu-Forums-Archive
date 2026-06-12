---
title: "md5 for cache identifier?"
date: 2010-06-30
forum: Programming Talk
---

### Post by NoBugs! on 2010-06-30
[This page]("http://developer.yahoo.com/python/python-caching.html") has Python code to make a downloader with disk cache. It stores files to disk with a filename of MD5(url), and checks if MD5(url) already exists, then it doesn't re-download it. This seems to be a good idea, except for the fact that some values may have the same MD5, for example:
[http://www.mscs.dal.ca/~selinger/md5collision/](http://www.mscs.dal.ca/~selinger/md5collision/)

Is there any function like md5, but without the possibility of collision? Or will it not likely happen on something as short as a url? Is there a better way to do this, something similar to how Firefox/chrome/etc handle cached pages?

---

### Post by MadCow108 on 2010-07-01
a hash always has collisions if the key is larger than the hash (or even when smaller depending on algorithm).
on something as small as an url the chance of collision is very small when using a good algorithm.
md5 uses 128 bit. if you just want a bit more there is SHA1 which uses 160 bit.
But these are general purpose hashing algorithms which may not be very appropriate for small strings
you may want to have a look at djb or sdbm

if you want a way of handling these collisions have a look at hash tables:
[http://en.wikipedia.org/wiki/Hash_table](http://en.wikipedia.org/wiki/Hash_table)

---

### Post by soltanis on 2010-07-01
First of all, I'm not sure about what you're talking about with this cache thing, but wget has several options for effectively "mirroring" a website by downloading all publicly visible portions of it and storing it to disk. It can also intelligently mirror a website, i.e. only download pages that have changed.

Second, about your MD5 question; MD5 was originally designed as a security algorithm (it is absolutely not suitable for this anymore, see [MD5 considered harmful today]("http://www.win.tue.nl/hashclash/rogue-ca/")) and so the probability of collisions occurring is exceedingly small (it took the authors of the MD5 paper on the order of several years with a lot of computing power to find one). If all you are using it for is something like hashing a file to see if its contents have changed (which is how I'm reading your question) then this is still a perfectly acceptable use of it.

If you are looking for security in your hash functions, you should avoid using MD5 as well as SHA0 and SHA1 (the SHA2 family of functions is still considered secure as of now), since these have identified weaknesses that either have been or could be exploited in the near future.

---

### Post by jpkotta on 2010-07-01
The probability of collision is vanishingly small.  It's really not worth worrying about, unless you're writing something that cannot fail (a downloader cache can fail, flight control software cannot).  If you are worried about it, you can check that there is no collision every time you add a URL (starting with no URLs), but that is overkill.

---

