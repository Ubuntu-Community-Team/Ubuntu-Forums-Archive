---
title: "DVD won't play movies"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by DavidVS on 2008-11-26
My DVD drive is only partly functional.

It works with files.  The drive mounts and unmounts correctly, and I can browse a DVD in file manager.  Certainly it worked to install Ubuntu from CD.

But none of the movie player or DVD rippers work.  Some produce an odd display with a mix of tiny boxes.  Most simply crash.

I've tried installing all sorts of packages hoping that at least one would include whatever drivers I'm missing.  But no luck.  (The application dvd::rip did ask me to install all sorts of packages; it was nice and thorough but did not fix my problem.)

I have installed: AcidRip, OGMRip, dvd::rip, GnomeBaker, Totem Movie Player, MPlayer, VLC, and xine.  I'm using Ubuntu 8.10 on an Acer Extensa 4620Z laptop.

Based on [this thread]("http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux") I checked that libdvdread3 is installed (it is) and even tried installing w32codecs (which only made things worse: now Totem crashes instead of displaying that mesh of little boxes).

What else might I need to do to play a DVD movie?

---

### Post by mc4man on 2008-11-26
Start by installing libdvdcss2, available here (probably the i386 ver. (32 bit intrepid install

[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

Then try again with anything but totem movie player (gstreamer)

If you want a decent totem player then run
```
sudo apt-get install totem-xine libxine1-ffmpeg
```

Will show up in menu as Totem Movie Player (Xine)

If you have any further issues then you may need to adjust your audio or video outputs or set a region on your dvd drive.

---

### Post by TFX360 on 2008-11-26
Starting Totem with an unsupported file automatially asks for a codec search. Or does that depend on the Ubuntu distrubution?

VLC works better for me, personally.

```
sudo apt-get install vlc
```

---

### Post by DavidVS on 2008-11-26
> **mc4man said:**
> Start by installing libdvdcss2

Ah!  Thank you.  I installed that (and ubuntu-restricted-extras as well) and now I can watch Firefly.

Shiny!

---

### Post by dwilson89 on 2008-11-27
I am having the same problem. I have tried watching smallville on my laptop, I have VLC installed but it won't play it. It won't even open a dvd menu.

If there is any advice please help

---

### Post by PriceChild on 2008-11-27
> **dwilson89 said:**
> I am having the same problem. I have tried watching smallville on my laptop, I have VLC installed but it won't play it. It won't even open a dvd menu.

If there is any advice please helphave you installed vlc and are still trying to play it in totem? Applications > Sound & Video > VLC Media Player.

Have you tried installing libdvdcss2 as suggested above?

---

### Post by mapes12 on 2008-11-27
This thread resolved my wows: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by acreech on 2008-12-01
> **mapes12 said:**
> This thread resolved my wows: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

That did the trick for me too. Thanks

---

