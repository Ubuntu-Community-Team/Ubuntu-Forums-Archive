---
title: "going back to open source driver after envy screw up"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by tysonh on 2008-06-18
I tried using envy to install a driver for my ati 7500.  It did not work.  Now im stuck in a super low resolution.  How can I go back to the open source driver mesa I think its called.  How do I start the video card config in terminal?  Or what do I download in the package manager to replace the file.  I already removed envy and uninstalled the envy provided driver.

---

### Post by overdrank on 2008-06-18
> **tysonh said:**
> I tried using envy to install a driver for my ati 7500.  It did not work.  Now im stuck in a super low resolution.  How can I go back to the open source driver mesa I think its called.  How do I start the video card config in terminal?  Or what do I download in the package manager to replace the file.  I already removed envy and uninstalled the envy provided driver.

Hi and have you tried to reconfigure your xorg via the terminal 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then restart x with the ctrl, alt, backspace keys

---

