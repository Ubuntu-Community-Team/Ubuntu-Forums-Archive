---
title: "Trouble with server repositories?"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by yarrumretep on 2012-06-27
Greetings all,

I've installed a fresh server 64 bit 12.04 and am having trouble installing anything else.

1) There appears to be no emacs in my apt universe: [https://help.ubuntu.com/community/EmacsHowto](https://help.ubuntu.com/community/EmacsHowto) says 'apt-get install emacs' should work, but it says its unable to locate package

2) Trying to get the add-apt-repository script I tried 'apt-get install python-software-properties' which says: 
```
Package python-software-properties is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

```

3) When I do 'apt-get update' I get many errors like this: ```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages  400  Bad Request ( The data is invalid.  )

```

Can someone point me in the right direction?  Did my sources.list get jammed somehow?

---

### Post by yarrumretep on 2012-06-27
Solved - it turned out my proxy setting was bogus.  apt is kickin' it now! :guitar:

---

