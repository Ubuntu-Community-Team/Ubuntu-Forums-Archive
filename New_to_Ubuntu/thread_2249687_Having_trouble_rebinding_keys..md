---
title: "Having trouble rebinding keys."
date: 2014-10-23
forum: New to Ubuntu
---

### Post by christheung on 2014-10-23
Trying to rebind keys so that I can use my Dell XPS 12 in tablet mode optimally.
 
1. Want to rebind the left Windows key and trick the system into thinking that it is the right windows key. This Dell has no right Windows key.


2. Want to rebind the left Windows key afterwards to be Ctrl+` (tilde key) so that I can assign it to bring up the onscreen keyboard. There is a built in shortcut: [http://askubuntu.com/questions/73667/keyboard-shortcut-to-reveal-onscreen-keyboard](http://askubuntu.com/questions/73667/keyboard-shortcut-to-reveal-onscreen-keyboard)


Racking my brain trying to solve this. Should take no more than 5 min for an expert to help me out. Thanks!

---

### Post by JazzPotato on 2014-10-24
I did this by creating a custom Xmodmap file, placing it in ~/.Xmodmap, and then running the command:
```

~$ xmodmap ~/.Xmodmap

```
on startup.

You'll have to find the keycodes with a command like
```

xev

```

before you can do anything however.
A quick google should reveal a tutorial for xmodmaps.

All the other ways of remapping keys in ubuntu I have found were quite temperamental or badly supported.
Cheers, and good luck

---

