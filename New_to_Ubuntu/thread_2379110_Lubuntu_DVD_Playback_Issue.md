---
title: "Lubuntu DVD Playback Issue"
date: 2017-12-01
forum: New to Ubuntu
---

### Post by ryersondale on 2017-12-01
[ATTACH=CONFIG]277704[/ATTACH]

Hello. I just freshly installed lubuntu on a 2002 Sony Vaio. My laptop has limited RAM so I choose the Artful Aardvark 17.10 Alternate 32-bit release. The install went fine but I've tried to play dvds and I get back an error that says "Playback was terminated abnormally. Reason: unrecognized file format." My laptop has a DVD-ROM drive, and my only media player is the GNOME MPLAYER, or GNOME MPV. I have tried several different dvds, but all to no avail- I get the same error every time. I was wondering, am I getting this problem because my laptop doesn't have the right hardware to play the dvds, or is it some other problem? Please let me know what the problem might be, and if there is anything I can do to fix it. Thanks!

P.S. I have posted a screenshot of the optical disk drive model number.

---

### Post by leunam12 on 2017-12-01
See if this helps:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by ryersondale on 2017-12-01
I looked and my OS already has libdvdread4 installed. I got regionset in my downloads folder but I don't know how to install it. My laptop is offline only. What can I do?

---

### Post by Geoffrey_Arndt on 2017-12-02
Did you follow the link instructions EXACTLY???   Also, . . need to be online.

---

### Post by cariboo on 2017-12-03
Installing libdvd-pkg is the preferred way to install libdvdcss. Follow the instructions given while the package is installed. In case you miss it, in a terminal type/copy/paste the following command:

```
sudo dpkg-reconfigure libdvd-pkg
```

---

