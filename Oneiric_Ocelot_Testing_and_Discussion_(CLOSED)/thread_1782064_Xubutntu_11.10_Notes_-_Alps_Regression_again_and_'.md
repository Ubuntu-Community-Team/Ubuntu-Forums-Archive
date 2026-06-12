---
title: "Xubutntu 11.10 Notes - Alps Regression again and ?'s"
date: 2011-06-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kaehny on 2011-06-14
Hi,
  Trying xubuntu in the Ocelot version and so far ok. Most things are fine but there are a couple of glitches, plus an old regression.

1. Let's see 10.4, 10.10, 11.4 and 11.10 I am perfect on this regression such that ALPS trackpad on my old Vaio is broken the same way with every single release of Ubuntu, Kubuntu and now Xubuntu. I guess this comes of not going upstream to report problems. Basically the trackpad loses the side scroll wheel and double tap click emulation. This can be fixed (and I did it) by creating a psmouse.conf in /etc/modprobe.d and putting the line
options psmouse proto=imps
in the file. Then on reboot I have the gestures back. This doesn't give double touch stuff, but I don't like that anyways. Oh well 2 years of the same thing ... it is usually fixed by the general release.

2. I cannot add users or such using xubuntu system tools. It will not even launch the menu item. I suspect I am not understanding something about permissions and admin rights for the logged in user. I can just sudo command line what I needed, but still.

A couple of "can I make it work like gnome 2?" questions:
3. Is there any way to get the click on window header to vertically maximize the window? i.e. like the gnome option.

4. Is there any way to get the top panel to have the little slide arrows in xfce like in gnome-panel that let you hide it off to the side? No big deal, but it would be nice. 

So far so good otherwise. I can't get Unity to even let me use the app launcher out of the box (11.4 or 11.10) so I moved to xubuntu. I'd rather stay with a base distribution then have to add a bunch of extra stuff.

---

