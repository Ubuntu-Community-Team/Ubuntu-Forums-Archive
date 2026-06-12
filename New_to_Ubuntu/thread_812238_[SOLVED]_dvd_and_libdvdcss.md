---
title: "[SOLVED] dvd and libdvdcss"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by cane1832 on 2008-05-29
(Totem Movie Player)
Error:The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

That is the error i keep getting when trying to play the movie "war games"
I have libdvdcss installed and ive tried vlc, Mplayer, and Movie player totem (xine backend), oh and gxine none of which work. The only one that comes remotely close to working is Mplayer i see the video but the audio is all messed up. And in Movie player i can hear audio and:evil: not see video.

   codecs installed Gstreamer ffmepeg video plugin
                    gstreamer extra plugins
                    Ubuntu restricted extras
                    Gstreamer plugins for aac,xvid,mpeg2,faad
                    gstreamer dirac video plugin
                    gstreamer plugins for mms, wavpack,whicktime, musepack

packages installed  libdvdcss2
                    libdvdnav4
                    libdvdread3

if anyone has any idea what is going on here i would apprieciate the info 

Thank you 

Cane

---

### Post by stchman on 2008-05-29
> **cane1832 said:**
> (Totem Movie Player)
Error:The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

That is the error i keep getting when trying to play the movie "war games"
I have libdvdcss installed and ive tried vlc, Mplayer, and Movie player totem (xine backend), oh and gxine none of which work. The only one that comes remotely close to working is Mplayer i see the video but the audio is all messed up. And in Movie player i can hear audio and:evil: not see video.

   codecs installed Gstreamer ffmepeg video plugin
                    gstreamer extra plugins
                    Ubuntu restricted extras
                    Gstreamer plugins for aac,xvid,mpeg2,faad
                    gstreamer dirac video plugin
                    gstreamer plugins for mms, wavpack,whicktime, musepack

packages installed  libdvdcss2
                    libdvdnav4
                    libdvdread3

if anyone has any idea what is going on here i would apprieciate the info 

Thank you 

Cane

You need to install the proper packages.

First install the proprietay CODECs.

[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Then install Medibuntu and the CSS decoder.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

You will be playing Hollywood encrypted DVDs in no time.

---

### Post by cane1832 on 2008-05-29
ok i did everything it said in the first url: and i already had vlc installed so i skipped the next one 

still no dice i get the audio in vlc but no video

---

### Post by mc4man on 2008-05-29
vlc can be helpful for troubleshooting - open vlc from terminal, try the dvd and see what error messages come up.

---

### Post by cane1832 on 2008-05-29
Ok problem solved sometimes a reboot can help. :popcorn:

---

