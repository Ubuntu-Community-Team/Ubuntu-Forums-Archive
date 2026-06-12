---
title: "How to confirm version lxde or xfce in Lubuntu?"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-03-12
How to confirm whether I have lxde or xfce in Lubuntu?

I think I have LXDE but am not 100% sure.

The "recently used" system doesn't work properly so I used synaptic to install 
xfce-places-plugin
but it doesn't seem to have appeared on the panel.

---

### Post by Bucky Ball on 2013-03-12
If you installed Lubuntu you have lxde. You would manually need to install xfce4 and you would need to manually change to that desktop environment via the 'Sessions' pop-up during login to be using xfce, neither of which it appears you have done. You have installed an xfce plugin which I doubt would work in lxde. But then, no experience of it.

---

### Post by vasa1 on 2013-03-12
How about:
```
env | grep XDG_CURRENT_DESKTOP
```?

---

### Post by Kevin McCready on 2013-03-12
WOW env is powerful.
Thanks Guys
AND thanks thanks thanks for the Bach.

I guess I'll stick with lxde but the "recently used" problem is annoying.
Maybe I could learn to run a little batch file in the console. I think they call it a script in linux, but I've never done one. It would display a screenful of the latest files I've used and let me click to open.

---

### Post by vasa1 on 2013-03-13
> **Kevin McCready said:**
> ... but the "recently used" problem is annoying.
Maybe I could learn to run a little batch file in the console. I think they call it a script in linux, but I've never done one. It would display a screenful of the latest files I've used and let me click to open.

Several, but not all, programs offer the option of opening recently accessed files created or modified by those programs.

The thing is that Lubuntu is a light distro and doesn't come with all the features that Unity, for example, has. So while Unity's Dash provides what I think you want, Lubuntu doesn't do so out of the box.

Anyway, if you describe what exactly you're looking for, there are people here who can script in their sleep! But you maybe better off starting a new thread for this specific aspect.

---

### Post by Bucky Ball on 2013-03-13
> **vasa1 said:**
> 
Anyway, if you describe what exactly you're looking for, there are people here who can script in their sleep! But you maybe better off starting a new thread for this specific aspect.

+1.

---

### Post by vasa1 on 2013-03-13
> **Kevin McCready said:**
> How to confirm whether I have lxde or xfce in Lubuntu?

I think I have LXDE but am not 100% sure.

The "recently used" system doesn't work properly so I used synaptic to install 
xfce-places-plugin
but it doesn't seem to have appeared on the panel.
Well, it's xfce_4_-places-plugin. And its description has this:
> This plugin brings much of the functionality of GNOME&#8217;s Places menu to Xfce.
It puts a simple button **on the panel**. Clicking on this button opens up a menu
with 4 sections:
 - System-defined directories (home folder, trash, desktop, file system)
 - Removable media (using thunar-vfs)
 - User-defined bookmarks (reads ~/.gtk-bookmarks)
 - Recent documents submenu

IMO, the panel referred to is the xfce4 panel and not LXDE's! So you may have to find a way to use Xfce's panel rather than LXDE's. I have no idea how well that'll work!

---

### Post by Bucky Ball on 2013-03-13
> **vasa1 said:**
> 

IMO, the panel referred to is the xfce4 panel and not LXDE's! So you may have to find a way to use Xfce's panel rather than LXDE's. I have no idea how well that'll work!

+1.

---

