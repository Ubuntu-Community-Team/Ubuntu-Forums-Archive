---
title: "help with screen resolution"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by btp1095 on 2008-09-23
Hey everyone,

After trying to get my s-video to work properly (based on instruction from this forum) with no success, my resolution is now messed up.  When my computer boots up it says it can no longer detect my Intel GMA video card.  I have a Dell Inspiron 1420 with Ubuntu 8.04 Hardy.

1) how do I get my computer to detect my Intel card?

2) how do I get my resolution back to the default way it used to be?

Please help!  Thanks

---

### Post by Sorivenul on 2008-09-24
First, if you could link to the tutorial/advice you were following so we can see what may have been changed, that would be great.

To attempt to fix your problem with your card try:
```
sudo dpkg --reconfigure xserver-xorg
```
If you can't log in, you may have to boot into recovery mode to do this.

---

