---
title: "Enabling Verbose x.Org Logging"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by UltraAnders on 2008-08-08
Hello all,

This is the first time I've not managed to find the answer in these forums, so here goes ...

[http://mythtv.org/wiki/index.php/Working_with_Modelines#Troubleshooting_modeline_validation](http://mythtv.org/wiki/index.php/Working_with_Modelines#Troubleshooting_modeline_validation) <- This link suggests I can get more info out of the Xorg.log.0 by "starting X with a higher log verbosity setting ie... startx -logverbose 20". Can someone explain where I need to add this option please? 

I have tried stopping x by using this command:
-  sudo /etc/init.d/gdm stop
Then:
-  CTRL+ALT+F1
Then:
-  startx -logverbose 20

I breiefly see the Nvidia logo, followed by a screen that looks like noise on an analogue TVs, then I'm dumped back to command line. :frown:

Not sure if you need to know system info. I'm using 8.04.1, kernel 2.6.24-19.

Thanks.

---

### Post by eightmillion on 2008-08-08
Try it with:
**startx -logverbose [20]**
Edit: Nevermind, I get the same result as you.

---

### Post by eightmillion on 2008-08-08
**sudo Xorg -logverbose 20** gets Xorg going, but unfortunately nothing else. :(

---

### Post by eightmillion on 2008-08-08
I don't know if this actually enables verbose logging, but you can edit **/etc/X11/xinit/xserverrc** and add the option there. For example:
```

#!/bin/sh

# $Id: xserverrc 189 2005-06-11 00:04:27Z branden $

exec /usr/bin/X11/X -nolisten **-logverbose 20** tcp

```
It at least doesn't have any ill effects as far as I can see.

Edit: **scratch this too. It doesn't appear to work.**

---

### Post by UltraAnders on 2008-08-09
Appreciate your help Eightmillion. I am pleased and also disappointed that it doesn't appear to be an entirely silly question!

Tried editing my /etc/X11/xinit/xserverrc, no change to the log file. I also tried **exec /usr/bin/X11/X -logverbose 20 -nolisten tcp**.

It doesn't seem to be widely mentioned option on x.org. Perhaps it is no longer in use?
[http://www.x.org/archive/X11R6.8.0/doc/Xorg.1.html](http://www.x.org/archive/X11R6.8.0/doc/Xorg.1.html)

---

### Post by UltraAnders on 2008-08-09
I've sort of got what I want via this link - [http://redhatcat.blogspot.com/2007/09/xorg-for-sharp-aquos-and-nvidia-8800.html](http://redhatcat.blogspot.com/2007/09/xorg-for-sharp-aquos-and-nvidia-8800.html) - which mentions an option -verbose.

- So, showdown x by typing this into terminal:
```
sudo /etc/init.d/gdm stop
```
- Then press: CTRL+ALT+F1
- Login
- Use command:
```
startx -- -verbose 6 2> /tmp/startx.log
```
This gives me far more info in file /tmp/startx.log. Hopefully enough to work out why the ModeLines for my HDTV are being rejected.

I'm still interested to here where to put this option so that it happens on startup. Didn't have any effect when added to /etc/X11/xinit/xserverrc.

---

### Post by eightmillion on 2008-08-09
I recently learned that you can also use the modedebug option in xorg.conf to enable more verbose logging. Just add:
```
Option "ModeDebug" "yes"
```
to your xorg.conf device section.

---

### Post by UltraAnders on 2008-08-16
Thanks EightMillion. Tried that option and in the xorg.log file I get:
```
NVIDIA(0): Option "ModeDebug" is not used
```
Also tried:
```
Option "ModeDebug" "true"
```
but no joy.

---

