---
title: "Searching for Plugins or DVD"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by prodriver on 2013-01-14
Hello, I'm new and this is my first post. I using 12.04. When I put in a dvd movie and select movie player a box comes up saying "Srching for missing pugins,"and then a box comes up "required plugin could not be found. Phyton (v2.7) requires to install plugins to play media files of the following type: DVD subpicture decoder" I'm lost how do I correct this? Thank you

---

### Post by GrouchyGaijin on 2013-01-14
> **prodriver said:**
> Hello, I'm new and this is my first post. I using 12.04. When I put in a dvd movie and select movie player a box comes up saying "Srching for missing pugins,"and then a box comes up "required plugin could not be found. Phyton (v2.7) requires to install plugins to play media files of the following type: DVD subpicture decoder" I'm lost how do I correct this? Thank you

I am not familiar with Phyton, but VLC seems to play just about everything.

---

### Post by SeijiSensei on 2013-01-14
First, I encourage you to use a search engine and browse the Ubuntu knowledge base.  Searching for "play dvd ubuntu" brings up the standard help document: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs).

Start by installing ubuntu-restricted-extras by opening a terminal and typing the command:

```
sudo apt-get install ubuntu-restricted-extras
```

Then read the section in the documentation above on installing libdvdcss.

BTW, my preferred video player is [SMPlayer]("http://smplayer.sourceforge.net/").  You can install it with the command:

```
sudo apt-get install smplayer
```

---

### Post by prodriver on 2013-01-17
Thank you the code for restricted extras did the trick. I  did the smplayer also. Thanks again.

---

