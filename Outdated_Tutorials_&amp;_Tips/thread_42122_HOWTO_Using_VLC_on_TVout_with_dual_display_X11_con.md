---
title: "HOWTO: Using VLC on TVout with dual display X11 configuration"
date: 2005-06-16
forum: Outdated Tutorials &amp; Tips
---

### Post by sksbir on 2005-06-16
What is written here is an awfull translation of [this frenchy thread](http://forum.ubuntu-fr.org/viewtopic.php?id=6761).

If you have configured X11 in order to get :0.1 display on your TV set, and :0.0 display on your standart PC display, then you should try to use VLC like this:
```

vlc --alsadev hw:1,0 --vout x11 --x11-display :0.1 --fullscreen --no-wxwin-embed
```

You will get the control windows on your display, but once you have select a video and it start to play, it will play on TV set, in fullscreen mode.( the control windows remains on your main display)

--alsadev hw:1,0 : Use it if you have two sound cards, and the second one is linked to TV set
--vout x11 : to invoke X11 mode
--x11-display :0.1 : to get the video windows on :0.1 display
--fullscreen ( ok, it is already translated...  :grin:  )
--no-wxwin-embed : mandatory! : in order to separate control window and display window. VLC will fail without this.

In order to get dual X11 configuration, you can take a look at xorg.conf configuration file [here](http://forum.ubuntu-fr.org/viewtopic.php?id=3902), and i'm sure that a lots of thead already exists on this forum about this subject.


hope it will help  ;-)

---

### Post by dysphasi on 2007-12-13
I know this is yonks after this thread was started, but just for a bit of an update, the switch to use now is  '--no-wx-embed'

---

### Post by morganGDFP on 2008-11-17
It doesn't work for me :(
if I try to run ```
vlc --no-wx-embed
``` from the command line I get:

```
vlc: unknown option or missing mandatory argument `--no-wx-embed'
```

If I run VLC without the no-wx I can get fullscreen on my TV for about 3 ms before VLC crashes..

Please help

---

