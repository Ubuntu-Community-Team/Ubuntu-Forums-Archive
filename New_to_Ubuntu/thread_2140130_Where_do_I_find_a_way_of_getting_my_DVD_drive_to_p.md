---
title: "Where do I find a way of getting my DVD drive to play movies in Ubuntu 11.10?"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by zoot6 on 2013-04-28
Hi There, I have Ubuntu 11.10 on a dual boot with Win XP Professional. When I loaded these on my Dell 1545 laptop I lost Win 7 and the drivers to play movies for my laptop. Microsoft has recently stopped supporting Win XP for drivers....so all is lost there.

How do I get my DVD drive to recognize and play movies or data DVD's (For my piano learning course) in Ubuntu 11.10

Thanks in advance, Paul...Noobie.

---

### Post by Frogs Hair on 2013-04-28
Try this first: ```
[COLOR=#333333][FONT=UbuntuMono]sudo apt-get install libdvdread4[/FONT][/COLOR]
```

If that doesn't work you  may need win32/64 codecs  libdvdcss2 . I found a 12.04 link for the package but I don't know if it works in 11.10 .The second link is for 11.10 but you will have to try it out. 11.10 is no longer supported as of may 9th, so you may just want to upgrade to 12.04 or install a newer version. 



[http://www.ubuntuupdates.org/package/medibuntu_free/precise/free/base/libdvdcss2](http://www.ubuntuupdates.org/package/medibuntu_free/precise/free/base/libdvdcss2)

[http://www.noobslab.com/2011/10/install-mplayer-with-multimedia-codecs.html](http://www.noobslab.com/2011/10/install-mplayer-with-multimedia-codecs.html)

---

### Post by zoot6 on 2013-04-28
Hi There
            Has anyone got any ideas to install a good media player in Ubuntu 11.10?

            I want to play movies and data DVD's for my piano learning course.

            I have installed the drivers to get my DVD drive working, but when play music the page goes grey and I cannot click on anything as the player crashes.

            Do you think I should have connected to the internet first before I installed the drivers?

Thanks, Paul.....noob.

---

### Post by lmarmisa on 2013-04-28
I like vlc.

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

The end of life date for Ubuntu 11.10 will be very soon: May 9, 2013. Consider to upgrade to a newer release. Ubuntu 12.04 is long term support:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by deadflowr on 2013-04-28
+1 for vlc

+2 for upgrading to a newer release soon.

Install Ubuntu-restricted-extras.

The dvd player is just a dvd player.
You'll need the codecs to play the content.

This might give more guidance

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by oldos2er on 2013-04-28
Threads merged. Please don't start more than one thread for the same question, it's confusing and it dilutes community effort.

---

