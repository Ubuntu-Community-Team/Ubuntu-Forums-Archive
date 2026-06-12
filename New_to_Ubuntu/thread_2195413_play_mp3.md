---
title: "play mp3"
date: 2013-12-24
forum: New to Ubuntu
---

### Post by meetsbs2099 on 2013-12-24
i am unable to play mp3 songs please help me.I am unable to download Gsteamer.

---

### Post by deadflowr on 2013-12-24
Try this  in a terminal ( to open a terminal press ctrl+alt+t, or press the windows-icon button on the keyboard and type, terminal)
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```
if either gives an error(or two) post it here, in this thread.

Added info: this installs extra codecs and at one point during the install, a EULA will appear
Use the tab button and the left/right button to navigate the yes or no options.

The above assumes you're running default Ubuntu.

---

### Post by Bucky Ball on 2013-12-24
Welcome. Which Ubuntu release are you using and please give more detail; how are you attempting to download gstreamer, what is happening when it stops and anything you've done to remedy the problem? Include exact error messages you're getting, if any.

Please try an update and report back with any errors you get there. If that works out, go to Software Centre or Synaptics Package Manager and try for gstreamer again. Report exactly what happens if it doesn't install.

* ... and +1 to deadflowr's suggestions in post #2 which I read after posting.

---

### Post by claracc on 2013-12-24
I observe you are double posting your problem. Don't do that, instead answer the questions asked in this post. I think, that your posts will be merged soon.

Have you follow deadflowr advice?, please post the results you obtain when running in a xterm (ctrl+alt+T) the commands provided (in order to see the errors produced):i.e.:

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

Also, as Bucky Ball points it would be good to know what ubuntu are you running: 12.04, 13.04, 13.10?, what way you have installed: dual boot, only ubuntu, wubi?, what are your hardware specifications: processor, ram, HD, graphics card. Have you tried to install any other software in the past, what were the results?

---

### Post by Bucky Ball on 2013-12-24
> **claracc said:**
> I observe you are double posting your problem.

Dealt with, OP aware, all good.

---

