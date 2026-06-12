---
title: "none-gui prog with gui dependencies"
date: 2008-10-19
forum: Programming Talk
---

### Post by techmarks on 2008-10-19
so why would the program Devilspie which is a command line window management utility, have a GTK dependency?

It's not a gui program at all, I thought it was odd.

I know I can look at the code and find out, but I haven't had the time to download it yet.

any ideas?

---

### Post by geirha on 2008-10-19
> Description: find windows and perform actions on them
 This tool will find windows as they are created and perform actions on them,
 such as resizing, moving to another workspace, or pinning them to all
 workspaces.

From this it sounds like it needs the gtk library to "talk" with gtk-windows.

---

