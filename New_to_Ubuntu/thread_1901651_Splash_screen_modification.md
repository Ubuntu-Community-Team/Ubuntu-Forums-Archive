---
title: "Splash screen modification"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by arockiyaselva on 2011-12-29
Hi all!
I'm new to ubuntu.I dont know how to change the splash screen. I have Ubuntu 10.10 with amd64 architecture.Is there any methods to change the splash screen using terminal? or any softwares available for this(amd64)?

---

### Post by orange2k on 2011-12-29
Do you mean the login screen?

---

### Post by cortman on 2011-12-29
I assume you're talking about the login screen. You can do this graphically with Ubuntu Tweak. To install:

```

sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

```

---

### Post by arockiyaselva on 2012-01-03
No.I mean Splash screen which displays at booting with Ubuntu logo

---

### Post by MartijnNL on 2012-01-03
Have a look at for example:

[http://www.ubuntugeek.com/plymouth-manager-simple-tool-to-change-splash-screen-themes.html](http://www.ubuntugeek.com/plymouth-manager-simple-tool-to-change-splash-screen-themes.html)

or

[http://ubuntuguide.net/howto-change-plymouth-themes-initial-splash-screen-in-ubuntu-10-04](http://ubuntuguide.net/howto-change-plymouth-themes-initial-splash-screen-in-ubuntu-10-04)

You want to change the Plymouth theme.

If you google for "ubuntu change plymouth screen" or "ubuntu change plymouth theme" you'll find a lot more info.

---

### Post by DS McGuire on 2012-01-03
> **cortman said:**
> I assume you're talking about the login screen. You can do this graphically with Ubuntu Tweak. To install:
 
```

sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

```
 
 
When using Ubuntu tweak the login background picture format has to be PMG otheriwse it will not show. Plus you have to add it to a certain folder in the file system but I can't remember which one it is because I'm at college at the moment :L.

---

### Post by MartijnNL on 2012-01-03
> **DS McGuire said:**
> When using Ubuntu tweak the login background picture format has to be PMG otheriwse it will not show. Plus you have to add it to a certain folder in the file system but I can't remember which one it is because I'm at college at the moment :L.

The OP isn't talking about the login screen, but about the Plymouth theme (other people just assumed it was the login screen).

---

### Post by arockiyaselva on 2012-01-08
At last I found a software called Zorin OS Splash Screen Manager 1.2 and it works fine in amd64. I changed my splash screen. Thank you guys for your replies.

---

