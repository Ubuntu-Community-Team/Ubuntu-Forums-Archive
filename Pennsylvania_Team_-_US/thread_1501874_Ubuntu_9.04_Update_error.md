---
title: "Ubuntu 9.04 Update error"
date: 2010-06-04
forum: Pennsylvania Team - US
---

### Post by skip2525 on 2010-06-04
Too All
For the last 2 weeks whenever I get an notice to update it will ask to do a partial update. See screenshot-1.png.  I can cancel out and do the update, but not all update will run.
If I say to do the partial update I get this (screenshot-2) It will come to an end when it's looking for the CD for Ubuntu 5.10. (screenshot -5)
Which is odd since I've only had 8.04 and 9.04 installed on this machine, and only started using Ubuntu at 7.04
It doesn't give me any other error messages.
Is their a work around or a way to clear up the problem ?
Skip

---

### Post by kejava on 2010-06-06
Hi Skip,

Could you post your /etc/apt/sources.list file?  It looks like it could be messed up.  Below is the contents of my custom (trimmed) sources.list file used in ubu 10.04.  Just four lines does it all.

```
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb http://archive.canonical.com/ubuntu lucid partner
deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
```

---

### Post by jedijf on 2010-06-15
Skip,

You can also try: System-->Administration-->Software Sources

then under 3rd party (or somewhere in the tabs)

UNCHECK the CD 5.10.

That should help with that part - but if you could open a terminal (Applications-->Accessories-->Terminal

and type 'cat /etc/apt/sources.lst'  <enter>

then copy and paste the output here and people can help even more.

Good luck.

---

