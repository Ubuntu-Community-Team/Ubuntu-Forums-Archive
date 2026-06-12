---
title: "Where can I find the config file for system shortcuts? (11.10)"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by decktrio on 2012-01-11
If someone is kind enough to help me:

Where can I find the config file for system shortcuts?

- I would like to make Ctrl+Q my system-wide shortcut for quitting an app/closing a window. I had already disabled this function, when I made a custom (Alt+F4) shortcut to shutdown ( '/usr/lib/indicator-session/gtk-logout-helper --shutdown' ).

- If I try to do it using the GUI keyboard settings menu, the menu closes as soon as I press the shortcut, instead of recording the change. To be clear, Ctrl-Q currently closes certain windows, but it's not a system-wide shortcut. For example, pyNeighborhood doesn't close with it.

- After some searching I found this XML file ( '~/.gconf/apps/metacity/global_keybindings/%gconf.xml' ) for metacity global shortcuts, but it clearly doesn't have all my shortcuts. More specifically it doesn't have my system or custom shortcuts. Anyone know where can I find that file?

Thanks for reading all the way down, whether or not you can help. :)

---

### Post by Spruce49 on 2012-01-14
sorry I can't help, I have a similar problem. I'm trying to use CTRL+ALT+G to open up gedit, but I get this error 
'Error while trying to run (Ctrl+Alt+G)
which is linked to the key (<Control><Alt+g>)

---

### Post by decktrio on 2012-02-21
I never did find the config file... but for anyone that uses Openbox*, [ObKey]("http://www.ohloh.net/p/obkey") worked for me.

---

### Post by wildmanne39 on 2012-02-21
Hi, please mark thread solved using thread tools, it will help the next person having the same issue.
Thanks

---

