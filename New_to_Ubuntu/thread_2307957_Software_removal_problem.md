---
title: "Software removal problem"
date: 2015-12-29
forum: New to Ubuntu
---

### Post by Jacob_Tennant on 2015-12-29
I have installed Eclpise Mars (4.5) via their new Installer system and now need to remove the version installed for a previos version to meet my needs.

However I have not been able to figure out how to properly uninstall it.

I have tried the Ubuntu Software Center and it shows that Eclipse is not installed.

I tried sudo apt-get autoremove eclipse also sudo apt-get remove eclipse and sudo apt-get purge eclipse and all of these return that eclipse is not installed.

Any suggestions???

---

### Post by ian-weisser on 2015-12-29
Well, stop trying to remove a package that isn't installed.
How else have you installed the software?

---

### Post by CharlesA on 2015-12-29
Have you checked /usr/local by chance?

---

### Post by Jacob_Tennant on 2015-12-29
nothing found relating to Eclipse in /usr/local

The only thing I have found is in my home directory 

/.eclipse

I found mention of running "rm -r ~/.eclipse" in another thread but concerned about causing problems when I go to reinstall a older version of Eclipse.

---

### Post by Jacob_Tennant on 2015-12-29
This was the first time I installed any software on linux this way.

80% of the time I use cli, the rest is by Ubuntu Software Center.

---

### Post by HermanAB on 2015-12-30
Why uninstall?  Just keep the old version.  Hard disks are so big nowadays, it simply doesn't matter how many version you keep.

---

