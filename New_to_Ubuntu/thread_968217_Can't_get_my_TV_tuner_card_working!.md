---
title: "Can't get my TV tuner card working!"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by doctorbighands on 2008-11-02
I bought a Hauppauge WinTV-PVR-150 tuner card specifically because I read it's compatible with Ubuntu. It's installed and working in Windoze, but I can't get it to function with any TV software in Ubuntu. I don't want to deal with the migraine headache that is MythTV; besides that, I don't need all of its features. I just want TV working in Linux. Is that so much to ask?

Anyone who could help me would be very much appreciated!

---

### Post by doctorbighands on 2008-11-02
...bump!

---

### Post by fooman on 2008-11-02
here is one that will work:

[http://home.arcor.de/saedelaere/info_eng.html](http://home.arcor.de/saedelaere/info_eng.html)

i have used it before with a pvr-250 in gutsy x86....i just got though installing it with my pvr-500 in intrepid x64.

works great! :)

---

### Post by oldos2er on 2008-11-02
Which tv software besides MythTV have you tried? Does the system recognize that the card's installed? Run the commands "lspci" or "lsusb" depending on which type of card you have, to see if it's recognized.

---

### Post by fenian on 2008-11-02
Mplayer will work.
Open mplayer from the terminal with the command...

> mplayer /dev/video0

That should open an Mplayer window,depending on what channel your card is set to and how you receive your TV signal (from an antenna,direct cable or set top box) you may or may not see any picture until you tune the card to the correct channel.To do this install ivtv-utils...

> sudo apt-get install ivtv-utils

Set the channel from the terminal.If you are getting your signal from a cable/satellite box tune to channel 3 with this....

> ivtv-tune -c 3 -d /dev/video0

If you ae connecting with an antenna or directly to analog cable just replace 3 from above with he channel you want to watch.

---

### Post by saedelaere on 2008-11-02
> **doctorbighands said:**
> I bought a Hauppauge WinTV-PVR-150 tuner card specifically because I read it's compatible with Ubuntu. It's installed and working in Windoze, but I can't get it to function with any TV software in Ubuntu. I don't want to deal with the migraine headache that is MythTV; besides that, I don't need all of its features. I just want TV working in Linux. Is that so much to ask?

Anyone who could help me would be very much appreciated!

Like fooman said try TV-Viewer.

If you got any problems with installation read the user guide. It is included in the program.
Oh and first install the packages
tcl, tk, libtk-img, xosd-bin, xdg-utils and scantv.
using synaptics.

If you want to try out the latest beta you don't need to install scantv.

Run 
```

sudo ./tv-viewer_install.sh

```

after the installation
```

tv-viewer

```

create a working configuration and then scan for available stations. Thats it

Saedelaere

---

