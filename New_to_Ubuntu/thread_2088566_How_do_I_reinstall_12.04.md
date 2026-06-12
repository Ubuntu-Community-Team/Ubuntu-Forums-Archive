---
title: "How do I reinstall 12.04?"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by JSF16 on 2012-11-26
How do I re install 12.04 after updating to 12.10?

---

### Post by BertN45 on 2012-11-26
From scratch, you cannot undo the 12.10 install.

---

### Post by JSF16 on 2012-11-26
Yes, cleary. How do I do this however? To be honest, I'm unsure if I have 12.04 or 12.10 installed. Terminal tells me 12.10, but my the text on the wallpaper of the login screen says 12.04

Now I have the disc I used to install ubuntu 12.04 the first time. Can I use this to reinstall 12.04 from scratch on 12.10 or 12.04? How?

---

### Post by monkeybrain2012 on 2012-11-27
> **JSF16 said:**
> Yes, cleary. How do I do this however? To be honest, I'm unsure if I have 12.04 or 12.10 installed. Terminal tells me 12.10, but my the text on the wallpaper of the login screen says 12.04



In the terminal type

```
lsb_release -a
```

It will tell you the installed version.

Yes, you can use the same disc to reinstall.

---

### Post by newb85 on 2012-11-27
Boot from that disc and run the installer.  It should recognize your Ubuntu install, and will probably give you an automatic option fitting what you want.

---

