---
title: "[SOLVED] Manpages in another language"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by WitchCraft on 2008-06-21
Hi!

Question:
I've downloaded manpages-ru, for having a look at the Russian manpages (to improve my Russian). 

But now that they are downloaded, how can I read manpages in another language ???

I've also downloaded the German and French manpages, but the same problem there...

---

### Post by sdennie on 2008-06-21
I'm able to switch between Argentine Spanish and English using:

```

export LANG=es_AR.UTF-8

```

and

```

export LANG=en_US.UTF-8

```

So, if you know the locale name, you should be able to switch it to whatever you want.  It defaults to English if no man page is available in the locale specified in $LANG.

---

### Post by WitchCraft on 2008-06-21
Doesn't work for me, I get:

man: can't set the locale; make sure $LC_* and $LANG are correct

---

### Post by sdennie on 2008-06-21
What did you try setting the locale ($LANG) to?

---

### Post by WitchCraft on 2008-06-21
> **vor said:**
> What did you try setting the locale ($LANG) to?

export LANG=de_DE.UTF-8
export GDM_LANG=de_DE.UTF-8

I also installed the spanish manpages and tried
export LANG=es_AR.UTF-8
man ls

but it didn't work.


when I type locale -a i get
```

root@all:~# locale -a
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX
root@all:~# 

```

Do I need to install additional language support (codepages, etc)?

---

### Post by phirestalker on 2008-06-21
TESTING

sorry didn't want to make my own thread for this, just testing my signature

UGH the button says edit OR delete but I see no way to delete this message :(

---

### Post by sdennie on 2008-06-21
That wouldn't be surprising.  It should be easy to do with System->Administration->Language Support.

---

### Post by WitchCraft on 2008-06-21
> **vor said:**
> That wouldn't be surprising.  It should be easy to do with System->Administration->Language Support.

O.K. i did so. Now it works, thanks!

PS: You can get the name of the locales installed with locale -a 
which now looks this way:

```

root@all:~# locale -a
C
de_AT.utf8
de_BE.utf8
de_CH.utf8
de_DE.utf8
de_LU.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
fr_BE.utf8
fr_CA.utf8
fr_CH.utf8
fr_FR.utf8
fr_LU.utf8
POSIX
ru_RU.utf8
ru_UA.utf8
root@all:~# 

```

FMI:To install on Debian:
Need to run it as root, else it fails.
```

apt-get install debconf
dpkg-reconfigure locales

```

---

