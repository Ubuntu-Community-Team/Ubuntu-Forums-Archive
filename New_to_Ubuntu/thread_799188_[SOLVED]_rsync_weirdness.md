---
title: "[SOLVED] rsync weirdness"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by binHEX on 2008-05-18
I am trying to synch a folder across two servers.
 The folder is called public and is off the root of the drive, /public
I am using the commandline:
rsync -avz --progress --stats root@sourcecomputer:/public /public

BUT, instead of copying the contents of /public, the command creates another public folder: /public/public and copies everything to there!
Should I be using:
source:/public/ /public
source:/public/ /public/
source:/public/* /public
source:/public/ /public
or what?  This is driving me nuts!
Please, someone give me a hand.  I have studied all the docs I can find on this, and being new to linux I am having a tough time figuring out the path weirdness here.
Thanks in advance!

---

### Post by jpeddicord on 2008-05-18
```
rsync -avz --progress --stats root@sourcecomputer:/public /
```

That should do it. :)

Specifying /public for the destination made rsync assume to copy the source folder *inside* the destination.

---

### Post by binHEX on 2008-05-18
Thanks jacobmp92!

I was on my way back here to delete the post when I saw that someone had already replied! heheheh
I found that if I used /public/. /public/ the command worked properly.
*sigh*
As is oftent he case, there is ALWAYS more than one way to skin a cat.

Thanks!

---

