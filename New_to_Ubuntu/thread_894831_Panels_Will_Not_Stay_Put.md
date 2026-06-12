---
title: "Panels Will Not Stay Put"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by RKCole on 2008-08-19
Hello, everyone.

This is quite a minor problem, but I am unsure as to how to resolve it.  The attached screenshot shows how I have everything set up, and how I **would like** ti to stay concerning my gnome-panels.

For some odd reason, unknown to me, when I power up or reboot my system, the position of the panels is always reversed.  I have no idea as to how to fix this so that this does not continue.  If I run

```

killall gnome-panel

```

from the Run Applications dialog, this sets thigns to normal.

I know that this is rather minor concerning myself, as I am familiar with the terminal and command line, but my wife is not, and I want to make thigns as easy for her as I can.

Is there any way to fix this so the panels stay as they should be?

Thank you for nay help.

Please take care.

**EDIT:**  My apologies.  I posted this yesterday, and I forgot to attach the above mentioned screenshot.

---

### Post by guardsman85 on 2008-08-20
What happens when you just log out and log back in without rebooting?

---

### Post by Too Late on 2008-08-20
Ok, so what happens, when you do NOT set things to normal? After next boot, will they be reversed (back to normal again), I think no? I mean, why don't you just move every item from one panel to another.

I think that putting panels on top of one another is not well supported in gnome (because in gconf-editor (at /apps/panel/toplevels), it says the following: "The orientation of the panel. Possible values are "top", "bottom", "left", "right""). In fact, I was never seen anything like that before.

edit: In case you don't know how to move your panel items. Right-click and unselect "Lock To Panel". Then middle-click and drag the item to another location. (And then select "Lock To Panel" again, if you want.)

---

### Post by ellaivarios on 2011-07-29
> **Too Late said:**
> Ok, so what happens, when you do NOT set things to normal? After next boot, will they be reversed (back to normal again), I think no? I mean, why don't you just move every item from one panel to another.

I think that putting panels on top of one another is not well supported in gnome (because in gconf-editor (at /apps/panel/toplevels), it says the following: "The orientation of the panel. Possible values are "top", "bottom", "left", "right""). In fact, I was never seen anything like that before.

edit: In case you don't know how to move your panel items. Right-click and unselect "Lock To Panel". Then middle-click and drag the item to another location. (And then select "Lock To Panel" again, if you want.)


I've tried this. I have the same problem. This is a bug and can be repeated on every Ubuntu distro that runs Gnome on pretty much every computer if you put one panel on top of the other at the bottom ONLY. Weird as hell! To make this clear. I have two panels at the bottom one on top of the other. I want them to stay this way, but the one on the bottom always comes to the top whenever I reboot. It is sooooo annoying. I have tried your suggestion even before I read it, and I took the time to meticulously move to the bottom panel every single item from the top panel that the OS loves to place on the top, BUT THEN AFTER REBOOT IT DID IT AGAIN!!! SO I deleted both panels and then recreated them just the way I like them, and when I rebooted, it did the same thing AGAIN! This is mental masturbation. Ubuntu still has many many such dumb little bugs all over. I've been using it for about three years now, and I discover one little thing every day. Thank God for the customizeability of Linux, otherwise we would be swamped in bugs. Instead of fixing these little dumb things all over, the developpers of ubuntu have created Unity, the biggest mental masturbation ever created.

---

### Post by overdrank on 2011-07-29
Thread is almost three years old. If you have support issues please create a new thread. Thread closed.

---

