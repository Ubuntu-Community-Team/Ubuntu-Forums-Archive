---
title: "Panels disapear after switching workspace?!"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by capncrunch33 on 2012-02-15
I'm running Ubuntu 11.10 in Gnome Classic mode with Compiz.  I'm new to Ubuntu.  The workspace switcher has not been working properly.  When I switch from workspace 1 to another workspace, the top and bottom panels immediately disappear.  The only way I can get back to workspace 1 is by clicking ctrl-alt-delete and clicking cancel.  I've already tried to reset all of the settings in the compiz manager to default.  I'm not sure what the problem is?! Here is a screen shot. Also, I had the same problem when I used the workspace switcher in the cairo dock.

Also, I noticed that this problem affects all types of switchers, e.g., the classic switcher and the switchers from docks such as vwm and cairo and docky.

---

### Post by Bergschreck on 2012-06-04
I have the same bug in 12.04. It only happens with Compiz (Gnome classic). It does not happen with Metacity (Gnome classic no effects).

Is there any solution?

Please confirm this bug report: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1008022](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1008022)

---

### Post by brigantino2 on 2012-07-03
I had the same problem: clicking on another workspace made everything on the screen (except the desktop background) disappear.
This happened after I've changed the configuration of the workspace switcher (I wanted 4 workspaces on 1 line), by right-clicking on it, then selecting "preferences".
The layout of the switcher apparently changed on the panel, but in fact, if I pressed Ctrl+Alt+right arrow, I could see the system did not recognize the change, since the default 2-rows 2-columns grid was popping up in the middle of the desktop.

I've launched "ccms" (no sudo required, if you don't have it, install it) then
General Options > Desktop size

there was something wrong here. I set "number of desktops"=1. Then, in my case, "horizontal size" = 4, "vertical size" = 1

I hope it helps

[IMG]http://i.stack.imgur.com/z3EEA.png[/IMG]

[IMG]http://i.stack.imgur.com/n3wuB.png[/IMG]

---

### Post by Bergschreck on 2012-07-03
Hi brigantino,

this is also described in the above mentioned bug report at launchpad. But then I have the problem that all apps that were started on desktop 2-4 jump to desktop 1 when switching desktops.

Does this also happen to you?

---

### Post by brigantino2 on 2012-07-03
> **Bergschreck said:**
> Hi brigantino,

this is also described in the above mentioned bug report at launchpad. But then I have the problem that all apps that were started on desktop 2-4 jump to desktop 1 when switching desktops.

Does this also happen to you?

Nope, sorry. The only thing I can suggest, if you have old configuration folders in your /home directory, I mean some .gconf .gnome2 .local etc. coming from an old system installation (as I had, since I was installing Ubuntu over Mint, keeping my home partition), trying moving/renaming them and see what happens at restart.
Good luck

---

