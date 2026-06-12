---
title: "Trouble rebinding close window key to &lt;CTRL&gt; + q"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by tabruhn on 2013-05-02
[COLOR=#000000]I'm trying to bind <CTRL> + q to close active windows the way <Alt> + F4 is set up to by default. I'm using the unity interface and use Compiz Config Setting Manager (CCSM) to change some other bindings. [/COLOR]

[COLOR=#000000]I've tryed to use Compiz Config Setting Manager (CCSM) General Options>Keybindings to change the close window binding to <CTRL> + q but I've had no luck. It will allow me to input the new binding but when I close the manager the new binding doesn't work. I return the CCSM to find the binding has changed back.[/COLOR]

[COLOR=#000000]I've also tried setting in the keyboard>application shortcuts a number of different commands which haven't worked yet.[/COLOR]

[COLOR=#000000]Is there anything I can do or try to make the <CTRL> + q to function the way <ALT> + F4 does by default installation?[/COLOR]

[COLOR=#000000]I'm running 12.04 LTS[/COLOR]

---

### Post by Sef on 2013-05-02
moved  to AB.

---

### Post by tabruhn on 2013-05-03
Perhaps there are some better ways to approach this problem? Do you any of you have advice to make a consistent close window button? For me it is not acceptable to have to continually guess between <ctrl> w, <ctrl> q , <ctrl> q + shift ...etc .... need a more consistent solution but to use <Alt> f4 requires <alt> <function> <f4> .. too spread out. Please, if you have any advice.

---

### Post by Isamu715 on 2013-05-03
There is a "Close window" keybinding in System Settings > Keyboard > Shortcuts > Windows. Try changing it to CTRL+q.

---

### Post by tabruhn on 2013-05-05
I appreciate the suggestion but I wasn't able to get it to work. I was able to make the change and it appears as my binding in the menu but when I try to use it in chromium, document viewer, nautilus, etc. it doesn't appear to be working.

---

### Post by Isamu715 on 2013-05-05
If that doesn't work you may try a workaround. Install *wmctrl* and set a custom keyboard shortcut to:
```
wmctrl -c :ACTIVE:
```
bind it to <CTRL> + q and it should work.

---

### Post by tabruhn on 2013-05-05
It worked! Thanks a million!

---

