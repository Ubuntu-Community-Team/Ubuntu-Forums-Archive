---
title: "Powersaving of Monitors and xset"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2013-09-11
My screen (s) turn off after a time.
I have, in system settings, under brighness and lock, made sure screen turn off never. Despite this, after a time the screen(s) turn off. I know its not just my main monitor, since both screens (different make and models) switch off at the same time.

Is there a config file that has a setting that I could edit. Is it a window manager thing? 

I have tried instructions in :
[http://ubuntuforums.org/showthread.php?t=2090285&highlight=turning+monitors](http://ubuntuforums.org/showthread.php?t=2090285&highlight=turning+monitors)

Ive tried running 
```

xset s off  

```
from the command line, and putting xset s off in my /etc/X11/xinit/xinitrc but it doesn't seem to make any difference.

Any suggestions?

---

### Post by Senior_Buckethead on 2013-09-23
bump

---

### Post by SantaFe on 2013-09-26
I think xset -s off turns off the screensaver. I saw somewhere that turning off DPMS would stop it, so I typed in the terminal xset -h and there was this bit of info.
```
    To control Energy Star (DPMS) features:
    -dpms      Energy Star features off
    +dpms      Energy Star features on
     dpms [standby [suspend [off]]]     
          force standby 
          force suspend 
          force off 
          force on 
          (also implicitly enables DPMS features) 
          a timeout value of zero disables the mode 

```

Typed in xset -dpms, then entered xset -q & it said DPMS was disabled.

You might try that.  ;)

---

