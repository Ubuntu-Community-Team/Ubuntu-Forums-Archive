---
title: "How to write the changelog when it is the very first release?"
date: 2014-07-24
forum: Packaging and Compiling Programs
---

### Post by Dr._Valy_G._Rousse on 2014-07-24
Hello,

I'm trying to create a deb package from a QT application that I wrote, and I have a problem with the changelog file. It seems that I'm forced to give a bug number that my deb package is supposed to fix. But what if this is the very first release of my package? If I don't include the changelog file, then I get an error like "bzr: ERROR: Could not find changelog at...".

So, currently I can overcome this problem by giving a fake bug number, so my changelog looks like:
```
sgf-bose-hubbard-client (1.0-1) trusty; urgency=low

  * Initial release (Closes: #100)

 -- Dr. Valy G. Rousseau <Valy.Gator@free.fr>  Thu, 24 Jul 2014 15:41:10 -0500

```

Is there a way to tell that it is actually the very first release?

---

### Post by ptn107 on 2014-08-08
I use git to manage my source files.  I am not required to give bug numbers.  You can edit your changelog afterwards and remove them if you would like.
```
dch -e
```
from the top of your source tree.

---

