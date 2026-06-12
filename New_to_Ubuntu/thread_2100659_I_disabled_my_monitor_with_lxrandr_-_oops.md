---
title: "I disabled my monitor with lxrandr - oops"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by Mr Flathead on 2013-01-02
My system is Ubuntu 12.04 running LXDE and OpenBox (in order to match rhe raspberry pi)    I was messing about last night trying to reset my screen resolution using lxrandr, got something very wrong and did not pay attention to the warning message.  Since then The machine boots OK and lets me ssh into it but no longer sends anything to the screen.   Please can anyone offer help on how to re-enable my screen from the command line.    I have so far failed in the following ways:  1) Running lxrandr with $DISPLAY set to the raspberry pi failed with the message "unable to get monitor information" (lxterminal is redirected OK)  2) Running x11vnc (server) gives me a desktop where I could try to correct things but for some reason this is only giving me a 320x320 desktop !  TIA  Mr Flathead

---

### Post by steeldriver on 2013-01-02
Hello and welcome

You should be able to query / change things via ssh using the command line xrandr - however you will need to specify the DISPLAY explicitly since it won't be set in the ssh session e.g.

```
xrandr -q -d :0
``````
xrandr -d :0 --output <OUTPUT> --auto
```where <OUTPUT> is the display device you are trying to set the mode for taken from the query ('-q') output above e.g. 

```
xrandr -d :0 --output DVI-0 --auto
```'auto' should enable the display and select the preferred mode

---

### Post by Mr Flathead on 2013-01-02
Thank You O Wise One ! 
Your solution worked perfectly (though I do feel dim that I could not work that out from the man pages).
Now to mark the thread as solved....

---

### Post by steeldriver on 2013-01-02
Glad it worked! tbh I wasn't sure :D

---

