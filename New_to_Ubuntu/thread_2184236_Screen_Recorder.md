---
title: "Screen Recorder"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by illage2 on 2013-10-28
Hi there,

I'm looking for a screen recorder that actually works.  I've tried RecordMyDesktop and it doesn't work the way I want it.  I know this has been asked multiple times but I only started using Linux yesterday so I'm still pretty new to the OS.

Thanks

---

### Post by david98 on 2013-10-28
[COLOR=#000000]kazam is the best and easy to use. in my opinion[/COLOR]


[https://launchpad.net/kazam](https://launchpad.net/kazam)

---

### Post by BrunoLotse on 2013-10-28
Hi:)Another suggestion:```
sudo apt-get install ffmpeg 
``````
ffmpeg -f x11grab -s wxga -r 25 -i :0.0 -sameq my_screen_output.mpg
```Yet another soft you can find here [http://www.webupd8.org/2013/06/simplescreenrecorder-powerful-screen.html](http://www.webupd8.org/2013/06/simplescreenrecorder-powerful-screen.html)Cheers, Bruno

---

### Post by FakeOutdoorsman on 2013-10-28
Do not use [-sameq: it does not mean same quality](http://superuser.com/a/478550/110524), this option has been removed upstream, and it most definitely does not belong in a command that is capturing from x11grab.

See [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719).

---

### Post by BrunoLotse on 2013-10-28
```
-sameq  Use same quantizer as source (implies VBR).
```This option is still on ffmpeg man pageCheers,Bruno

---

### Post by philinux on 2013-10-28
I tried VLC [http://www.howtogeek.com/120202/](http://www.howtogeek.com/120202/)

But in 13.10 it just crashes.

---

### Post by philinux on 2013-11-01
VLC works a treat now thanks to this fix that turned up in todays updates to saucy.

[https://bugs.launchpad.net/ubuntu/+source/x264/+bug/1241772](https://bugs.launchpad.net/ubuntu/+source/x264/+bug/1241772)

---

