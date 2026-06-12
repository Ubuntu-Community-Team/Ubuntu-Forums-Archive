---
title: "enter shortcut into a bash script"
date: 2020-03-27
forum: New to Ubuntu
---

### Post by navido on 2020-03-27
Hi everyone..i am new here.

I have Ubuntu 18.04 and 4 workspaces (0-3). What i want to do is to run a simple bash script with wmctrl that opens Vivaldi browser with 3 tabs in workspace 1. 

So i made this:

#!/bin/bash
wmctrl -s 1 #Switches to workspace 1 [workspaces are numbered from 0]
&vivaldi url1 &vivaldi url2 &vivaldi url3 & #Opens tabs with specific urls.

The problem is that if i have vivaldi allready opened at workspace 0 and not in workspace 1, then this script creates those tabs in workspace 0.

To start a new instance of Vivaldi in workspace 1 i can however use Ctrl+n. And then off course run the script. 

So how can i enter the shortcut "Ctrl + n" into this script?

Thanks

---

### Post by TheFu on 2020-03-27
i doubt it will help, but **xdotool** is how to accomplish this.
A different WM, like fvwm, will control placement of windows onto specific workspaces if the one you are using doesn't support that.

BTW, **&vivaldi ** is incorrect.  Remove the &.  it belongs on the end of the prior line.

---

### Post by bestucan on 2020-04-04
"setting" -> "keyboard" could set shortcuts to open vivaldi.
"tweaks" -> "extensions"  - "auto move windows" could set default workspace when software open.

---

### Post by CatKiller on 2020-04-04
Assuming Vivaldi accepts the same command line options as chromium, you could add the *--new-window* switch to your first invocation of Vivaldi. If you haven't got Vivaldi running, you'll be opening a new window anyway, and if it is already running a new window is what you want. It's possible that the command line option is called something different with Vivaldi, but it's a pretty standard function for browsers.

---

