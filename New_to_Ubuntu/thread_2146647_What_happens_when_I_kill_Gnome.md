---
title: "What happens when I kill Gnome?"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by abexman on 2013-05-19
Was working in Ubuntu 12.04 and closed a program and immediately the screen locked up. Switched to ctrl+f1 and tried killing various PID but none worked. I then saw somewhere I can kill gmone, which I did which seemed to put me back at a login. What happens to everything when you 'kill gnome'? Do all the other programs I have open have their process killed too? I get a little worried if this kind of thing might corrupt a mounted Truecrypt volume/container or my Thunderbird email profile for example. Is this the best command to kill a GUI-only freeze (of course I'm not sure if mine was GUI only)?

---

### Post by Frogs Hair on 2013-05-19
Looking at the manual page may help and there is other information as well . ```
 man kill
```

---

### Post by Hekabe on 2013-05-19
All processes that run a GUI are children of the GNOME process, so if you kill gnome they would go too. For a better command, you might try ```
sudo restart gdm
``` if you use GNOME.

---

