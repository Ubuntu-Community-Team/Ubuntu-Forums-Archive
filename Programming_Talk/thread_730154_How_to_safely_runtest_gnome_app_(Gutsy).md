---
title: "How to safely run/test gnome app (Gutsy)"
date: 2008-03-20
forum: Programming Talk
---

### Post by spaceboy909 on 2008-03-20
I'm wanting to experiment with the 'appearances and preferences' 'applet that runs when you right-click on the gnome desktop and select the menu option for it.

I believe I've downloaded the right source....: gnome-control-center.

I've unpacked the source and am getting ready to take a look at it, but I need to know how I can test any changes I make without interfering with the applet that's already running by default in gnome.  Do I need a chroot environment for that, or something else?  Or is it possible to test this right along side of the default applet without interference?

---

### Post by nhandler on 2008-04-26
gnome-control-center is actually installed by default (as of Gutsy...I think). It just doesn't appear in the menu. You can either edit your menu to make it appear, or launch it from a terminal "gnome-control-center". But there is no need to install it from the source. All gnome-control-center does is display everything under System->Preferences and System->Administration in an easy to navigate, searchable window. You won't mess anything up by using it.

---

### Post by kknd on 2008-04-27
You can install it on another prefix, like

./configure --prefix=/opt/newfolder

This way it won't overwrite the original.

---

