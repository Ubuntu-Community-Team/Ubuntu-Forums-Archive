---
title: "[SOLVED] Help me find my lost menu bar"
date: 2013-08-14
forum: New to Ubuntu
---

### Post by Ayel on 2013-08-14
Not sure what it's called, it's the one where you see the clock, and various little icons.

Could be that I did something with MyUnity to cause this.

Edit: Thanks, resetting worked

---

### Post by stinkeye on 2013-08-14
Not sure  if you mean the entire panel or just the indicator applet.
What release are you using?

This is if you have no panel or launcher.
Install compizconfig-settings-manager and check the unity plugin is enabled.

Using terminal...
```
sudo apt-get install compizconfig-settings-manager
```

To run in terminal (if no dash) use the command...
```
ccsm
```

---

### Post by SweetAurora on 2013-08-14
You can also do 
```
unity --reset
```
to completely reset Unity and Compiz's settings. That should get your desktop back.

---

### Post by stinkeye on 2013-08-14
> **SweetAurora said:**
> You can also do 
```
unity --reset
```
to completely reset Unity and Compiz's settings. That should get your desktop back.
The **unity --reset** command is deprecated in 13.04, hence the release question.

---

