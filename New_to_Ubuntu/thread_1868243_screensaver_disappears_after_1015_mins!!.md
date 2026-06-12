---
title: "screensaver disappears after 10/15 mins?!!"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by mani2604 on 2011-10-24
hi there

          i do have like 30 pics in the PICTURES folder & I set it as Screensaver.. It activates aftr 5mins idle time...  

         so the problem is the pics appear for like 10-15 mins & the screen goes blank.. Cant figure out how to make the screensaver visible all the time 

  any ideas plz

   thanks,

---

### Post by -kg- on 2011-10-24
One thing I can suggest to check:

Launch System Settings, then click on the "Power Icon."  Make sure the setting under the appropriate column for "Suspend when inactive for:" is set to "Don't Suspend."  The computer suspending is one of the things that will make the screen go blank.

Other than that, is the monitor Energy Star compliant?  Is the monitor being put into power saving mode?  If so, you'll have to turn that feature off.  I'm not sure if there is a way to set that via a GUI, but it can be turned off (and on) via the terminal:

```
xset -dpms
```

...will turn it off ("xset +dpms" turns it on).

---

### Post by mani2604 on 2011-10-24
hey thanx a lot... I think the monitor code worked!! Today morning I came to the office & the screensaver is still ON...

thanqqq

---

### Post by mani2604 on 2012-01-14
Well i thot the problem solved the previous time.. my mistake

One of frns got this Inhibit applet installed on my machine now tht disables the monitor inactive mode activation aftr 30 mins!! its cool nw...

---

