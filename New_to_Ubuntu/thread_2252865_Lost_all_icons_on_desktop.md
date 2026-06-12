---
title: "Lost all icons on desktop"
date: 2014-11-15
forum: New to Ubuntu
---

### Post by victoria10 on 2014-11-15
Hi.  I'm new to Ubuntu and have found myself in a sticky situation immediately. I was having problems with the display from my zotac box on my Sony TV. Eventually I messed things up completely, the windows on the screen were far to big and I could not change it back. I trawled through Google looking for help, I tried everything I could find trying to change the resolution through the terminal.  I saw somewhere that downloading virtual box would get the parameters back.. So I did that,  then found I have no icons. I've gone into root to remove virtual box and tried everything to get unity back... Nothing seems to be working. Is there anything else I can try? I'm running Ubuntu 14.04... Thanks and sorry for being stupid!

---

### Post by grahammechanical on 2014-11-15
So, what is the problem? No Unity user interface? Or messed up video settings? For Unity we can try resetting Compiz which is the window compositor

```
dconf reset -f /org/compiz/
```

We can also try restarting Unity

```
setsid unity
```

You may need to revert to an open source video driver. If you have created a special configuration file to adjust video settings then you will have to do something about that. Linux/XServer usually gets it video settings from the Extended Display Identification Data (EDID) in the monitor's electronics every time Linux loads. If that process has be overridden by a custom configuration file, then the situation will have to be reversed.

If we select Recovery mode at the Grub boot menu Advanced Option for Ubuntu sub-menu and then select Resume Ubuntu will load using a fall back open source video driver. Doing that may get you somewhere.

Regards.

---

### Post by victoria10 on 2014-11-15
Sorry I wasn't clear. It's the unity interface.. There are no icons to the left at all.,  just the blank screen and wallpaper. I'll give it a go with what you have told me. Can only access the system through recovery mode. Have been tinkering with it this morning to no avail. Thank you very much.

---

### Post by victoria10 on 2014-11-16
That hasn't worked for me. Still no icons...Looks like I'm going to have to reinstall 

Thanks for the info

---

