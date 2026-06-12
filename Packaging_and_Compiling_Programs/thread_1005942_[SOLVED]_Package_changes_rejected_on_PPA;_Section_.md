---
title: "[SOLVED] Package changes rejected on PPA; Section not valid"
date: 2008-12-08
forum: Packaging and Compiling Programs
---

### Post by Sam Lars on 2008-12-08
I'm trying to set up my PPA on Launchpad, and I've gotten all the way to the uploading part.  It appears to upload fine, but I then get an email saying this:
```
pidgin-facebookchat_1.42~ppa1.dsc: Section 'Networking' is not valid
```
I've searched Google, the Ubuntu forums, and this forum specifically, and I've found almost nothing.  One thing I found suggested the person's version being wrong (using periods instead of dashes), but isn't mine right?
I've also tried for the section main, universe, Net, and unknown, and all have failed.
I'm sure this is something simple, what am I doing wrong?


Anyone know what I'm doing wrong?

Thanks.

SOLUTION:
I finally decided Debian might actually have something good to say about their packaging system... I found a list of possible sections [here]("http://www.debian.org/doc/debian-policy/ch-archive.html#s-subsections").  I used "net" and it worked.  *Finally.*

---

