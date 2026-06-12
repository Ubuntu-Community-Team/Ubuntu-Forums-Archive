---
title: "Help! Blender, Snowballz, and GLXgears cease to function!"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by mac9416 on 2008-07-30
All three, when run from the terminal, give me some kind of error something like "display has no GLX tag" or something loosely to that effect. Also: at the same time my hibernate function has stopped working. I hibernate and then Ubuntu boots up as if I had reboted! Related? I haven't the faintest idea.

---

### Post by jdoliner on 2008-07-30
Hmm do

```
cat /etc/X11/xorg.conf >~/Desktop/xorg.conf
glxinfo >~/Desktop/glxinfo
```

and post the results

---

### Post by mac9416 on 2008-09-20
Thanks, man! Found the problem!

As you suspected, the problem was in /etc/X11/xorg.conf. The fix?

~$ cd /etc/X11/
/etc/X11/ $ sudo cp xorg.conf xorg.conf.backup
/etc/X11/ $ sudo nano xorg.conf

Then, in nano, you should find near the top a line reading "disable: glx", or something close. Remove that line, press ctrl-o to save, then reboot. Problem solved!

---

