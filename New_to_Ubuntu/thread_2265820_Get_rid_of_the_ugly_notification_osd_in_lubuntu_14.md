---
title: "Get rid of the ugly notification osd in lubuntu 14.10"
date: 2015-02-18
forum: New to Ubuntu
---

### Post by thomsebastin on 2015-02-18
I installed lubuntu 14.10 recently. I love it so far. It's very fast and all. The only absolute one thing that really annoys me is the "out-of-shape" osd which is used for notifications. I haven't seen anything as ugly as this. I wouldn't mind if it takes to removing it, but I definately don't want it there. Any work-around? Here is an [Image]("http://i60.tinypic.com/2ytwtav.jpg").

---

### Post by kerry_s on 2015-02-18
geez, that is ugly. that don't look like osd notifications.

lets do a test, in terminal run:

notify-send -i info "test" "this is a test"

you should get a pop up somewhere, mine is set for the bottom right. see pics

i think the package you would use is notify-osd, in xfce we have xfce4-notifyd

---

### Post by vasa1 on 2015-02-18
> **kerry_s said:**
> ...
i think the package you would use is notify-osd, in xfce we have xfce4-notifyd
Lubuntu uses xfce4-notifyd as well.

---

### Post by kerry_s on 2015-02-18
> **vasa1 said:**
> Lubuntu uses xfce4-notifyd as well.

if that's true then he just needs to change themes.
what do you think that looks like ?
to me it looks like it could be some kind of zenity script ? cause it's not really under the panel, like proper notifications.

thomsebastin,
 is notification for brightness change or something else ?

---

### Post by vasa1 on 2015-02-18
> **kerry_s said:**
> ...
what do you think that looks like ?
...
I don't know why OP posted that image link instead of using the forum's attachment option. There's so much garbage on that page. It's hard to tell what is what. I'm assuming the osd is in the top-right of the window. That was a known bug which could only be fixed by changing themes as you suggested: [https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/1362555](https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/1362555)

---

### Post by kerry_s on 2015-02-18
i think that's it exactly, looks like panels stacked.

---

### Post by bapoumba on 2015-02-18
Thanks for the bug link, same here but did not really pay attention :)

---

