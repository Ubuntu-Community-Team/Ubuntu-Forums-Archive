---
title: "Intelligent terminal binding"
date: 2007-02-13
forum: Outdated Tutorials &amp; Tips
---

### Post by brohan on 2007-02-13
As a constant user of the terminal, I'm sometimes forced with opening up new windows some of the time. Because I use a window multiplexer like screen it makes it difficult to use completly new windows.

This little script will open up a terminal window if none is currently open. It will move the terminal window to your workspace and activate it if there is a terminal currently running.

It's magic starts with wmctrl, a beautiful window control program.

```
sudo apt-get install wmctrl
```

Make an executable file somewhere handy
```
#!/bin/bash
PID=`pidof Terminal`
if [ "$PID" = "" ]; then
	Terminal --command screen --title terminal
fi

wmctrl -R "terminal"


```

Replace 'Terminal' with your proper terminal, it's the xfce4 one.

If you don't know about screen, I suggest you find out. It makes terminals fun.

---

### Post by deodatus on 2007-02-27
I use this command:

wmctrl -r "quake_console" -b toggle,shaded
It is bound to <Alt>Escape
(I launch a terminal named quake_console on start-up)

the only problem is the terminal stays below everything.  it receives focus but will not go to "above" state

do you know how to correct this??
thanks in advance

---

