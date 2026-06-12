---
title: "automatically move gnome (3) panels to 2nd screen from command line"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by freak42 on 2012-01-24
Hi all,

I used a little script with disper to automatically enable a 2nd screen if available. 

With gnome 2 I was able to automatically move the top and bottom gnome panels to the 2nd (larger) screen with
```
gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/monitor" --type integer "1" 
```

Now I am using Ubuntu 11.10 and Gnome 3 and this doesn't work anymore.
Does anybody have any way to move the Gnome Panels automatically from one screen to another from the command line?

Any help is appreciated.

Matthias

---

### Post by freak42 on 2012-01-25
bumpidiy.. anyone? :(

---

