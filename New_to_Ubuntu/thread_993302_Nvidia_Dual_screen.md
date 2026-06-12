---
title: "Nvidia Dual screen"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-11-25
Okay, so I have dual screen set up on an nvidia 8600 card and it works fine except for one thing.  I hate how twin view stretches my desktop background.  Is there any way to make it so that the background is just the same picture on each desktop instead of the stretched one?

I use the nvidia-settings app btw.

---

### Post by fooman on 2008-11-25
in nvidia-settings > x server display configuration > display > configure... try "separate x screen" instead of twinview

---

### Post by CryptiniteDemon on 2008-11-25
I'd like to do it without using a separate X screen.  One reason is that I can do dual screen without constantly changing my config file.  Having twin view does not require me to restart X each time. I'm on a laptop and sometimes I have dual screen.  Other times I don't.

---

### Post by fooman on 2008-11-25
not sure what you mean,  but to make the settings "stick"....you need to run nvidia-settings *as root*.  like this:

```
gksudo nvidia-settings
```

and when your done with your settings,  you need to click on the "save to x configuration file" button.

sorry if you already knew that.

---

### Post by CryptiniteDemon on 2008-11-25
yeah I know that.  I usually don't make them stick though given the variety of monitors or no monitors that I use.

---

