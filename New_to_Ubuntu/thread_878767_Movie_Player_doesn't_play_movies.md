---
title: "Movie Player doesn't play movies"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by DrScum on 2008-08-03
installed Xubuntu 8.04, everything worked great "out of the box" including SMC wireless lan. However, when trying to play a DVD Totem gives the following message:
"Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc."

What do I do now?

I already downloaded and installed all upgrades from the repositories and was told: "your system is up to date".

Thanks for your consideration

---

### Post by sisco311 on 2008-08-03
install xubuntu-restricted-extras from add/remove, synaptic or
from the terminal:
```
sudo aptitude install xubuntu-restricted-extras
```

also take a look here:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by billgoldberg on 2008-08-03
Open up a terminal (xterm) and copy/paste this:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y xubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

And you'll be good.

---

### Post by james_vanb on 2008-08-03
I've never been able tp get Totem working in Xubuntu.  Follow this guide:

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

In the middle it recommends installing Mplayer.  I ultimately uninstalled Totem.

Good luck.

---

### Post by sisco311 on 2008-08-03
> **james_vanb said:**
> I've never been able tp get Totem working in Xubuntu.  Follow this guide:

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

In the middle it recommends installing Mplayer.  I ultimately uninstalled Totem.

Good luck.
+1 for mplayer or vlc

---

### Post by DrScum on 2008-08-03
Thanks for your help guys, I did what was suggested and that way solved several problems I didn't mention in the original post (nvidia graphics, sound card and flashplayer).

I also ended up installing VLC but I still can't play DVD's.
 
It turns out that the problem seems to be related tthe drive configuration. When inserting a DVD I see the icon on the desktop but when clicking on it there is an error message saying "failed mounting /dev/sdc". To me it looks like the DVD drive is mounted on /media/cdrom and the system tries to mount it as /dev/sdc as well.

How do I go about diagnosing and fixing that problem?

On BIOS level I have a harddrive as primary master, the DVD drive as secondary master and a CD R/RW drive as secondary slave.

Thanks for your consideration!

---

