---
title: "How can I get a list of open windows?"
date: 2009-08-31
forum: Programming Talk
---

### Post by Flimm on 2009-08-31
In python, how could a get a list of the titles of all currently open windows?

Would I have to use Xorg API? Does Xorg API exist for python?

---

### Post by lykwydchykyn on 2009-08-31
There's python-xlib, though I'm not sure how you'd get it to give you a list of open windows.

---

### Post by spupy on 2009-08-31
A more crude approach is to use the commands module to call "wmctrl -l" and parse the output. But first look into the python xlib documentation.

---

### Post by Flimm on 2009-08-31
Thanks for the tips! I've now got this far:
[php]import Xlib
import Xlib.display

display = Xlib.display.Display()
screen = display.screen()
root = screen.root
tree = root.query_tree()
wins = tree.children

for win in wins:
    print win.get_wm_name()[/php]

And I get the following output:
```
x-nautilus-desktop
None
The Python X Library - Window - Mozilla Firefox
Guake!
None
Inbox (# unread, #### total) - Evolution
None
None
None
seahorse-agent
None
gnome-session
None
gnome-settings-daemon
None
<unknown>
None
None
None
None
None
Panel
None
None
None
None
None
None
None
None
None
Top Expanded Edge Panel
Bottom Expanded Edge Panel
None
File Manager
None
Deleted Items Applet
None
Tracker
None
NetworkManager Applet
None
notify-osd
None
update-notifier
None
Power Manager
update-notifier
File Manager
None
None
None
<unknown>
<unknown>
None

None
None
<unknown>
None
skype
None
Do
None
tomboy
None
guake.py
None
Keyboard Indicator
None
Conduit
None
WebilderApplet
File Manager
None
indicator-applet
None
Volume Applet
None
Fast User Switch Applet
indicator-applet
Panel
None
gnome-screensaver
WebilderApplet
Fast User Switch Applet
Fast User Switch Applet
None
evolution-alarm-notify
None
evolution-exchange-storage
None
applet.py
evolution-exchange-storage
None
File Transfers
None
None
None
gtk-window-decorator
None
gtk-window-decorator
None
gnome-screensaver
None
dropbox
dropbox
None
Firefox
Firefox
None

Firefox
Firefox
Firefox
Firefox
Firefox
Firefox
Firefox
Firefox
Firefox
Firefox
Firefox
None
evolution
evolution
evolution
evolution
guake.py
guake.py
Firefox
Firefox
Firefox
Firefox
Firefox
Firefox
Firefox
Firefox
```

Any idea why I get so many duplicates? I only have one Firefox and one Evolution window open.

---

### Post by Jimleko211 on 2009-08-31
looks to me like it's listing processes or something...

---

### Post by spupy on 2009-08-31
> **Jimleko211 said:**
> looks to me like it's listing processes or something...

All programs that have or can open some sort of GUI must make a connection to the X server. I don't know about the duplicates, though.

EDIT: Here is some code. Try it out. It requires the "**wmctrl**" util to be installed:
```
import commands
"""
    Each window is 4-tuple: (id, desktop number, host, window title)
"""
lines = commands.getoutput("wmctrl -l").split("\n")
windows = []
for line in lines:
    line = line.replace("  ", " ")
    win = tuple(line.split(" ", 3))
    windows.append(win)

for win in windows:
    print win
```

---

### Post by stroyan on 2009-08-31
It is listing many unmapped windows.
You can look at get_attributes and check for a map_state value of X.IsViewable.
You can also see more about windows that are transient for other windows, such as a popup menu window for an application.
For that look at the get_wm_transient_for() result.
```

#!/usr/bin/python

from Xlib import display, X

display = display.Display()
win_list = display.screen().root.query_tree().children
for win in win_list:
    name = win.get_wm_name()
    transient_for = win.get_wm_transient_for()
    attrs = win.get_attributes()
    if attrs.map_state == X.IsViewable:
	print win, transient_for, name

```

---

### Post by lucasmocellin on 2010-03-31
hi,

I got a problem related to that.

I wrote an app in python, and I would like this app to have control of "firefox" to set it as active, I mean, to minimize my app or put in background and show firefox instead.

do you guya know how to do that?

thanks in advance,

Lucas.

---

### Post by alex_o on 2010-04-16
> **lucasmocellin said:**
> hi,

I got a problem related to that.

I wrote an app in python, and I would like this app to have control of "firefox" to set it as active, I mean, to minimize my app or put in background and show firefox instead.

do you guya know how to do that?

thanks in advance,

Lucas.

look into devilspie :guitar:

---

### Post by sgnn7 on 2012-08-07
> **lucasmocellin said:**
> hi,

I got a problem related to that.

I wrote an app in python, and I would like this app to have control of "firefox" to set it as active, I mean, to minimize my app or put in background and show firefox instead.

do you guya know how to do that?

thanks in advance,

Lucas.

I know it's an ancient post but you can use the following:
from Xlib import Xatom, display, X

self._display = display.Display()
self._screen = self._display.screen()
clientmessage = Xlib.protocol.event.ClientMessage(
                client_type=self._local_display.intern_atom('_NET_ACTIVE_WINDOW'), 
                window=window, data=(32, (2, X.CurrentTime, 0, 0, 0))
            )
            self._screen.root.send_event(clientmessage, (X.SubstructureRedirectMask|X.SubstructureNotifyMask))

---

### Post by Cheesehead on 2012-08-07
You should be able to list windows, select windows, etc, using the dbus module.

---

