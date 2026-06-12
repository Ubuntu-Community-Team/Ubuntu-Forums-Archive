---
title: "make CTRL+ALT+DELETE have system task manager"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by shevin on 2011-11-05
I wonder what people do when ubuntu crashes, 
ALT-BACKSPACE no longer works
CTRL-ALT-DELETE doesnt run the system manager...

how can I make CTRL ALT DELETE , show task manager , so I could kill processes ... it is very handy, I wonder why ubuntu developers never think to add it

---

### Post by llamabr on 2011-11-05
[https://wiki.ubuntu.com/XorgCtrlAltBackspace](https://wiki.ubuntu.com/XorgCtrlAltBackspace)

I know -- the hand holding is enough to drive you back to debian.

---

### Post by shevin on 2011-11-05
what is that link , 
is there any solution for that ?

---

### Post by llamabr on 2011-11-06
For which one, the ctrl alt delete?  I solved it by switching away from ubuntu.  But of course -- what you love about linux is that it's infinitely configureable.  You can always change it back:

[http://www.ubuntugeek.com/enable-ctrl-alt-backspace-in-ubuntukubuntu-10-04lucid-lynx.html](http://www.ubuntugeek.com/enable-ctrl-alt-backspace-in-ubuntukubuntu-10-04lucid-lynx.html)

regarding something like a task manager, look at:

```
top
```

---

### Post by 3rdalbum on 2011-11-06
> **llamabr said:**
> [https://wiki.ubuntu.com/XorgCtrlAltBackspace](https://wiki.ubuntu.com/XorgCtrlAltBackspace)

I know -- the hand holding is enough to drive you back to debian.

Control-Alt-Backspace was disabled in Xorg upstream, and the new key combination is Alt-Printscreen-K.

Using an Alt-Printscreen combination means that it is caught by the kernel, so it can kill X even when X has entirely frozen.

---

