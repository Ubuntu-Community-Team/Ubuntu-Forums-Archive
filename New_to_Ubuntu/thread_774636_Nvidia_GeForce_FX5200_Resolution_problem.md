---
title: "Nvidia GeForce FX5200 Resolution problem"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by tjpatton on 2008-04-29
I guess I have a Command Line problem in getting Ubuntu to recognize my graphics card.  I've tried installing Ubuntu, Fedora 8 and Kubuntu, all with the same results.  It wants 640 x 480 and that's that.  My screen fonts are like 20 font size.  I can't solve this.  There must be some trick to it, or, I'm simply as dumb as a bucket of rocks.  BTW, I had Ubuntu 7 working fine.  The resolution was perfect, but as soon as I upgraded this started.   Anyone?   Tim

---

### Post by sailor2001 on 2008-04-29
easiest way is to go into your files.  /usr/applications/screen & graffics

---

### Post by tjpatton on 2008-04-30
I'll try that, thanks.   Tim

---

### Post by tjpatton on 2008-04-30
Tried that.  I can't find any reference to fixing this problem in there.  Hard to navigate in there, too, because the font is so HUGE.  Thanks for the effort, I appreciate it.

---

### Post by lazyart on 2008-04-30
```
sudo dpkg-reconfigure xserver-xorg
```
Follow it through and be sure to select all the resolutions you want available.  I have a 5200 as well and it drives two monitors quite happily.
I'm still running 7.10 (Gutsy) just for this reason--  You guys work through the issues, and in a couple weeks the updates will take care of 'em and I'll join the party.

---

### Post by 67GTA on 2008-04-30
> **lazyart said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```Follow it through and be sure to select all the resolutions you want available.  I have a 5200 as well and it drives two monitors quite happily.
I'm still running 7.10 (Gutsy) just for this reason--  You guys work through the issues, and in a couple weeks the updates will take care of 'em and I'll join the party.

The dpkg tools have been removed in Hardy. ```
dpkg-reconfigure xserver-xorg
``` no longer works. If you can't see to use the "Screens and Graphics" tool, you will have to manually edit xorg.conf.

---

### Post by lazyart on 2008-04-30
> **67GTA said:**
> The dpkg tools have been removed in Hardy. ```
dpkg-reconfigure xserver-xorg
``` no longer works. If you can't see to use the "Screens and Graphics" toll, you will have to manually edit xorg.conf.

Ouch.

---

