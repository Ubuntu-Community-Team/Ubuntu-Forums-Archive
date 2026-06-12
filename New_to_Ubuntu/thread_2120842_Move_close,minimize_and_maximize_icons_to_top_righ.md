---
title: "Move close,minimize and maximize icons to top right"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by benjie1 on 2013-02-27
HI. Is there a way to get the min, max, and close icons to the top right of windows vs. the top left. I seem to recall something like tweak that did it but can't find it. Using Ubuntu 12.04, gnome 3 and 32 bit system. Thanks

Bob

---

### Post by ajgreeny on 2013-02-27
> **benjie1 said:**
> HI. Is there a way to get the min, max, and close icons to the top right of windows vs. the top left. I seem to recall something like tweak that did it but can't find it. Using Ubuntu 12.04, gnome 3 and 32 bit system. Thanks

Bob
Use command ```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close" 
```
This does what used to be possible using gconf-editor.

This info from step #6 of [http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) which is for classic gnome desktop in 12.04.  The thread has lots of other useful command shown which you may find useful as well, even thugh you aren't using classic gnome desktop

---

### Post by MadmanRB on 2013-02-27
Ubuntu tweak can do this, if using gnome classic.

Personally I have gotten used to unity but meh.

Anyhow here is ubuntu tweak:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

install it, then after install when you open it go to "Tweak"
then to "window"
change windoiw buttons to right side
and you are done.

---

### Post by gifford on 2013-02-28
Ubuntu Tweak also works for unity to move the window control buttons to the right.

---

### Post by benjie1 on 2013-03-02
Thanks. It worked well. No probs.

---

