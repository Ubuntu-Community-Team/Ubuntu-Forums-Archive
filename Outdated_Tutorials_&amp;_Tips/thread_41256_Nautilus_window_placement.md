---
title: "Nautilus window placement"
date: 2005-06-12
forum: Outdated Tutorials &amp; Tips
---

### Post by luxer on 2005-06-12
Does anyone know how to make nautilus leave its window in the same place everytime? I find it profoundly startling when I click on some folder and the window pops up wherever it was last left.

A side rant:

You know I've been using linux since gnome since the 1.2 days and I've decided that nautilus is just a turd. It's made many lateral movements in useability and functionality over the years but this just makes it... different every release, it never seems to make much progress in being less turdly. It's the achilles heel of gnome,  an example of the sort of dilletantish poorly planned, unfinished project that gives opensource a bad name.

Anyone know of any possible replacements on the horizon?

Cheers-
Luxer

---

### Post by Sionide on 2005-06-12
Last edited by luxer : Today at 10:42 PM. Reason: posted to wrong thread but can't delete... sigh.

Ok I'll let you off then :)

---

### Post by jzke on 2005-07-15
Far off in the distance is Thunar, the replacement for Xffm in XFce... but that'll be a while off. Looks very promising though. See here:

[http://thunar.xfce.org/wiki/](http://thunar.xfce.org/wiki/)

---

### Post by Wolki on 2005-07-15
[QUOTE=luxer]Does anyone know how to make nautilus leave its window in the same place everytime? I find it profoundly startling when I click on some folder and the window pops up wherever it was last left.[/quote]

This is not a bug but a feature, the window is supposed to be where you left it so hat you can use it faster and so that it'll remember you settings (like having a bigger window if it's a directory with lots of files, or a smaller one if there's hardly anything in it. Spatial Nautilus however woks best with a certain file management structure, most important having a rather flat, balanced structure (not having thousands of nested directories only containing a few files)

If you want to disable the benefits of spatiality, simply choose "Always use browser mode" in the Nautilus Settings.

> 
You know I've been using linux since gnome since the 1.2 days and I've decided that nautilus is just a turd. It's made many lateral movements in useability and functionality over the years but this just makes it... different every release

Well, you can't make something better and still keep it the same. I've grown to dislike using a browser with a tree view on the side, because i want to do stuff with my files, not micromanage an additional view that always does what it wants. Nautilus works well once you get used to it.

> Anyone know of any possible replacements on the horizon?

Well, you can always use ROX, there's a Howto here that allows you to replace Nautilus. For a browser-type file manager, i really like that one, especially since it's drag&drop based, has nice ideas and is lightning fast. The ubuntu version however is imho not well preconfigured (for example compared to the Mandriva version) so you'll have to set up file bindings etc for yourself.

---

### Post by SKLP on 2005-07-15
[QUOTE=Wolki]If you want to disable the benefits of spatiality, simply choose "Always use browser mode" in the Nautilus Settings.[/QUOTE] I concur, however, if you like spatial nautilus but not the crap "ubuntu-spatial" that is in hoary then that can be disabled: ```
gconftool-2 --type bool --set /apps/nautilus/preferences/no_ubuntu_spatial true
```

---

