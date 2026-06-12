---
title: "xfce loading programs over top task bar"
date: 2011-07-23
forum: Programming Talk
---

### Post by bcz on 2011-07-23
Hi All

A while ago I loaded Ubuntu 11.04 64-bit server as a LAMP server and setup xfce as a gui.  All worked fine for a few weeks.

Now I get a problem if I load firefox or terminal;  Synaptic and a few other programs dont have this problem.

The program loads at coordinate 0,0 on the physical desktop, so the left part of the menuline at the top of the screen is no longer useable.

The first time the program is loaded, the file menu can be used to exit the program.  The second time the program is loaded, you click on the file tab and the file menu displays as expected, but if you move the mouse on to the file menu it closes the menu.  If you exit using Ctrl-Q the close menu issue may clear, but it comes back.

Ctrl-Q closes the program

Ctrl-N opens another copy of the program at 0,0 completely obscuring the original copy, so you can effectively run only a single program.

Other possible symptoms (may just be xfce; I use gnome 2 normally):

.  No close/minimise/fullscreen icons at top right of window
.  Cannot move window by dragging the title frame

The problem appeared shortly after I tested a php script using graphics, so there may be a link if somehow php grahics corrupted X, which seems unlikely.

Any suggestions appreciated.  Reloading the server might be expedient, but it would be nice to understand what has happened.  Not critical as is just a home server to teach myself about Ubuntu server.

Bill

---

### Post by bcz on 2011-09-07
Solution was to use gnome 2 instead.

Might be a bit more overhead, but I can live with it as its not a live webserver.

Rgds Bill

---

