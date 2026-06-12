---
title: "wmv ubunto 8.04/amd64"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by cmdr_anomic on 2008-11-24
i have been using the vlc player but on newer wmv files it will not play; so i read up on mplayler on here; downloaded all the codecs etc.  so i could play the newer files; i get sound but i get this msg; and no video

>>
error opening/intializing the selected video_out (-vo)_ device

the other players work still; and this player will give sound but not video for all the formats ive tried

ubuntu 8.04 with all updates

---

### Post by magli on 2008-11-25
Hey.

you need to change the default video device. Did the version of mplayer you installed come with a GUI? If so: 
-> Open mplayer
-> Right click on the mplayer window.
-> Go to Preferences-> Video
You should see a list of potential video drivers. Names like xv, x11, etc. I have xv selected, so you could try this - but if it does not work, try a different one.

If you don't have a GUI, and you are starting mplayer from the command line, then you can change the video out device with the -vo option. Like this:

```
mplayer -vo xv,x11 FILENAME
```

Which will make mplayer first try the xv driver, then the x11 driver.

---

