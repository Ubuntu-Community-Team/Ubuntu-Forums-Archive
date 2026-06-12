---
title: "Fresh install of 8.04"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-07-27
I just performed a fresh install of Ubuntu 8.04 on my Thinkpad T61 with Intel X3100.  I never could get dvd's to plays on 8.04, just 7.10 using xine backed Totem.

How do I go about setting up 8.04 to play dvd's using xine backed Totem?

---

### Post by tuxxy on 2008-07-27
Did you install the **ubuntu-restricted-extras** package to allow mp3, flash, java, codecs for dvd playback etc

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Vivaldi Gloria on 2008-07-27
**1)** Enable medibuntu repos following the "Repository HowTo" here:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

You need to enter the following commands as explained there:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

**2)** Then install the following programs using the command

```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential ubuntu-restricted-extras
```

**3)** Check if encrypted DVDs work. If not try this command in a terminal:

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

That should do it.

---

### Post by subaruwrc01 on 2008-07-27
Yes, and tried multiple guides, but nothing worked.

---

### Post by hansdown on 2008-07-27
> **subaruwrc01 said:**
> I just performed a fresh install of Ubuntu 8.04 on my Thinkpad T61 with Intel X3100.  I never could get dvd's to plays on 8.04, just 7.10 using xine backed Totem.

How do I go about setting up 8.04 to play dvd's using xine backed Totem?

This is one of the most helpful collections of info.  [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by subaruwrc01 on 2008-07-27
Nevermind.

---

