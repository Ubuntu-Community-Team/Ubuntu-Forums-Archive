---
title: "prjector problems"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by kobra_877 on 2008-09-12
i tried to plug my laptop into a prjector the other day and the projector would not display my screen but it would show up on the external display. but when i loged out i could see my log in screen but after i loged in it went blank again 

is there a driver i need to down load 

o ya i am running the newer version of ubuntu

---

### Post by HalPomeranz on 2008-09-12
Hmmm, the usual default behavior is that your laptop screen and the external device show the same image.  You can force this behavior with a command like:

```

xrandr --output LVDS --auto --output VGA --auto --same-as LVDS

```

If you wanted to force a particular screen resolution for both screens, you could use something like:

```

xrandr --output LVDS 1024x768 --output VGA --auto --same-as LVDS

```

---

