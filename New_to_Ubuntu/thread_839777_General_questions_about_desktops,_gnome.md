---
title: "General questions about desktops, gnome"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Homesrfan on 2008-06-24
I'm really confused here, and this is a simple, easy question probably, but I'm having trouble wrapping my head around it.

As I understand, Gnome is... what powers your desktop. Now, where I get confused with is stuff like Beryl. Beryl works with Gnome, but what exactly does it do? Does it just add effects? It doesn't totally take over Gnome, I guess. But then why are there specific themes for Beryl and Gnome? Also, depending if you are using Gnome or KDE, do applications have to be made to each one. For example, is there a KDE FireFox and a Gnome FireFox. 

Maybe I'm completely off and thinking too much in a Windows mindset, I'm not sure.

---

### Post by RomeReactor on 2008-06-24
Hi. As I understand it, in Ubuntu the X server is the first 'layer' of display: this program and its libraries is what allows Ubuntu to display a graphical desktop, and lets you interact with the windows with the mouse and keyboard.

Gnome is a graphical desktop environment, with its look and feel, and its set of applications, and uses a window manager called Metacity to do the actual drawing of the windows. Compiz is also a window manager, which uses the hardware acceleration capabilities of the video card to draw images in 3D; when you use Compiz, you're replacing Metacity, but still using Gnome. Gnome uses GTK+ as it's widget toolkit--a set of tools to create the graphical user interfaces.

KDE (used in Kubuntu) is another desktop environment, with its own look and set of applications, and uses KWin as its window manager (which can also be replaced by Compiz). KDE uses the QT widget toolkit for the user interfaces.

XFCE (used in Xubuntu) uses xfwm as its window manager. It also uses GTK+.

You can use KDE applications in Gnome or XFCE, and viceversa; all that's needed is the installation of a few libraries needed by the programs which usually are not installed by default in the other desktop environment.

Firefox is the same for Gnome or KDE, and as of version 3 it even uses the icon set you have in your desktop. Firefox also uses GTK+.

---

### Post by Homesrfan on 2008-06-24
Thanks a lot! That really helps.

---

### Post by Eric Qel-Droma on 2008-06-24
Does that mean that if I install something from the Applications --> Add/Remove option in the upper left of my Ubuntu 8.04 screen, and that something is meant for KDE, that Ubuntu will automatically make it work with Gnome?

Thanks!

Eric

---

### Post by bluepowder7 on 2008-06-25
> **Eric Qel-Droma said:**
> Does that mean that if I install something from the Applications --> Add/Remove option in the upper left of my Ubuntu 8.04 screen, and that something is meant for KDE, that Ubuntu will automatically make it work with Gnome?

Thanks!

Eric

generally yes.  it may not "look right" (as in, it may have quite a different look to the window borders and colour schemes and buttons), but it ought to function just fine.

---

### Post by Eric Qel-Droma on 2008-06-25
So all of the correct buttons and stuff will be there, eh?  Super!

---

