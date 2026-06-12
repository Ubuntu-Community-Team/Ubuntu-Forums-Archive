---
title: "Wine does not work"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by PoopyTheJ on 2008-04-27
Every application I've installed in Wine does not work. I get an error of some sort about missing components for Steam, Adobe CS2, Firefox and another program, which I forget what it is off the top of my head. Is there some way to uninstall Wine and all apps installed to it, clean up and reinstall and try again? I'm wondering if I did something wrong. I'd really like to use Adobe CS2 and Steam in Ubuntu but as of now I'm relegated to continuing to use windows till I can get them working.

---

### Post by mc4man on 2008-04-27
If you have troubles with specific apps in wine it is worth going here to ck. and look for tips, install instr. or if no go. [http://appdb.winehq.org/](http://appdb.winehq.org/)
remove wine thru synaptic, then go to home directory and delete the .wine folder (hidden)

edit: wine specific forum [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by bodhi.zazen on 2008-04-27
Wine works "out of the box" for simple applications, like utorrent and the like. The more complex the more you will need to follow a tutorial specific to each application.

To remove wine completely :

```
sudo apt-get remove --purge wine && rm -rf $HOME/.wine
```

---

### Post by PoopyTheJ on 2008-04-27
Thanks! I'll do some digging, any alternative to illustrator or a pagemaker style app? I need to create brochures and flyers.

---

### Post by bodhi.zazen on 2008-04-27
I suggest the gimp.

---

