---
title: "Script-command to raise window above others"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by joehc on 2013-06-02
Hello

I'm writing a script to run a program inside the terminal. I want that terminal-window to always be on top. But neither Compiz or Devilspie seem to work. So, I was wondering if it is possible with some scripting to make that window always on top.

My script looks like this:

```
#!/bin/bash
gnome-terminal --profile=twitter --geometry=120x10+50+1000 -e ttytter

```

---

### Post by stinkeye on 2013-06-02
Try **wmctrl** (need to install)
Give your terminal twitter profile a unique name in the title and command tab for initial title
and choose to keep initial title.
[ATTACH=CONFIG]243425[/ATTACH]
eg If I wanted to start htop in terminal and above
I could use a script like...
```
#!/bin/bash

gnome-terminal --profile=myhtop --geometry=120x10+50+1000 -e htop 
sleep 3
wmctrl -a [COLOR="#EE82EE"]myhtop[/COLOR] -b toggle,above
```

The wmctrl command needs to use the [COLOR="#EE82EE"]title of the terminal window[/COLOR].
[ATTACH=CONFIG]243426[/ATTACH]

Edit: Just had a look at ccsm and can add the window to be always above
in the window rules plugin, so no need for the wmctrl command.
It doesn't allow me to grab a window using title but I can add manually.
eg
```
title=[COLOR="#EE82EE"]myhtop[/COLOR]
```
[ATTACH=CONFIG]243428[/ATTACH]

---

### Post by joehc on 2013-06-02
Thanks for your reply!

But seriously I dont get it

Here is my window:
[IMG]http://i.imgur.com/IY73AD3.png[/IMG]

and in windows rules (above) I write: "title=Terminal".

But it still does not work :s

---

### Post by stinkeye on 2013-06-02
> **joehc said:**
> Thanks for your reply!

But seriously I dont get it

Here is my window:
[IMG]http://i.imgur.com/IY73AD3.png[/IMG]

and in windows rules (above) I write: "title=Terminal".

But it still does not work :s
What release are you using?

Is compiz the window manager?
```
wmctrl -m
```

What session?
```
echo $DESKTOP_SESSION
```


> [COLOR="#008000"]glen@Raring:~$[/COLOR] **wmctrl -m**
Name: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF

[COLOR="#008000"]glen@Raring:~$[/COLOR] **echo $DESKTOP_SESSION**
ubuntu


Does the wmctrl command work.
Eg
```
wmctrl -a [COLOR="#EE82EE"]MyWindowTitle[/COLOR] -b toggle,above
```

---

### Post by joehc on 2013-06-03
Hey it worked!
compiz was not the windows manager - dont know why

So I just made compiz the window manager and with "title=Terminal" in Above it works like a charm.

Many thanks!

---

