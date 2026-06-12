---
title: "anyway to backdade KDE?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by phread59 on 2008-05-03
I just upgraded to Hardy.  I had to do a clean install to correct a botched update from 7.10.  I had KDE 3.5 installed with Gnome before.  The new 4.0 just leaves me cold.  I do NOT like the sliding windows for the system.  It irritates me to no end.  I like the older fixed widows as intusive as they were. Is there a way to backdate it or to switch the system application windows back to 3.5 type?  Otherwise I think 4.0 is nice.  I have only started to tinker with the widgets.  is there one in there that will do the older style menu?

Mark Shuman

---

### Post by angry_johnnie on 2008-05-04
You can just install kde 3.5 from a package manager.

```
sudo aptitude install kde-core
```

wil install only the very basic packages (it's still quite usable).

```
sudo aptitude install kubuntu-desktop
```

will install everything from a regular kubuntu system.

The downside is your menus will be all messed up, with apps from both kde 3.5 and kde4.  You'll have to edit those yourself.

You could also try removing kde4, after installing kde 3.5.
If you install kubuntu-desktop, it should ask you whether you want kdm (since kde4 uses kdm-kde4), just choose yes, and you'll be good to go.

Open Adept, and look for anything with kde4 in it. It should be safe to remove it, if you've already installed kde 3.5, and have kdm.

Or, you could keep both.  Kde4 needs a little more polish, but it promises to be good.

---

### Post by Joeb454 on 2008-05-04
I think Kubuntu 8.04 does actually come with KDE 3.5, but there is a separate disc image for KDE 4

---

### Post by T-Virus on 2008-05-04
I had no problem (well at least nothing major) downgrading from KDE 4 to KDE 3. Well... my Login Manager got all messed up but that's pretty much it.

---

### Post by phread59 on 2008-05-04
Thanks for the help.  When I got the 8.04 up and running in Gnome I had it add the Kubuntu desktop or so I thought.  I ended up with 4.0.  I really just wanted 3.5.  I am now installing the K desktop I will see what happens.

Mark Shuman

---

### Post by phread59 on 2008-05-04
I downloaded the Kubuntu desktop.  it asked me to conigure the display manger for the proper default.  I could not get that so I shut the box down.  I logged out and back in and found only 4.0.  I checked in add/remove and found the Kubuntu desktop to be 4.0 not 3.5.  I may need to go somewhere else to get it.  I'm gonna rummage around in Synaptic to see if there is 3.5 in there.

Mark    Shuman

Looked in Synaptic there are no 3.5 repositories in there.  I may have to add the 7.10 repositories and nab it from there.  or download and install it manually.  Gonna give that a go and see where that leads me.

---

### Post by phread59 on 2008-05-04
I couldn't figure out how to find the correct file in the mirrors.  So I just said poop on it.  I used a widget in KDE4 that creates an old style menu from a drop down box.  It's not as nice as the 3.5 version but it'll do.  So I'm just gonna leave it be for now.

Mark Shuman

---

