---
title: "Videos appear lacking in color."
date: 2008-05-27
forum: New to Ubuntu
---

### Post by ralphygarfield on 2008-05-27
It seems that most, if not all of my videos in Linux are appearing lacking in color. Windows gives them much more color and character. 

Some of my videos are even appearing nearly entirely in black and white. 

This is happening in multiple players. 

What could be the problem? How do I fix it?

---

### Post by sayakb on 2008-05-27
Open totem (movie player). Goto Edit->Preferences
Click Display tab and drag the Saturation slider towards right..

---

### Post by ralphygarfield on 2008-05-27
> **LinuxIsInnovation said:**
> Open totem (movie player). Goto Edit->Preferences
Click Display tab and drag the Saturation slider towards right..


I can't find anything called totem. And this is happening in multiple players, not just one.

---

### Post by Maestro23 on 2008-05-27
> **ralphygarfield said:**
> I can't find anything called totem. And this is happening in multiple players, not just one.

Totem (Movie Player) in your App menu.  If you are running Gnome.

Have you tried adjusting video settings in the other media players you have installed?

---

### Post by saratchandra on 2008-05-27
Totem is the "movie player" in your sound and video menu

---

### Post by billgoldberg on 2008-05-27
If you already have vlc installed, remove it and install the vlc player from the medibuntu repo:

[link]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/")

Now take a look here for the issue:

[link]("http://linuxowns.wordpress.com/2008/03/18/messed-up-picture-with-vlc/")

That should fix the problem.

It also couldn't hurt to make sure you installed your graphics cards driver
(system -> administration -> hardware drivers).

---

### Post by sayakb on 2008-05-27
> **ralphygarfield said:**
> I can't find anything called totem. And this is happening in multiple players, not just one.
Applications->Sound and Video->Movie player

---

### Post by ralphygarfield on 2008-05-27
> **LinuxIsInnovation said:**
> Applications->Sound and Video->Movie player


I looked before, and I didn't see anything called Totem. 

But I'm not on Linux right now so I can't re-check.

---

### Post by ralphygarfield on 2008-05-27
> **billgoldberg said:**
> If you already have vlc installed, remove it and install the vlc player from the medibuntu repo:

[link]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/")

Now take a look here for the issue:

[link]("http://linuxowns.wordpress.com/2008/03/18/messed-up-picture-with-vlc/")

That should fix the problem.

It also couldn't hurt to make sure you installed your graphics cards driver
(system -> administration -> hardware drivers).



Looked at your second link - my video problem is NOTHING like that. 

THIS PROBLEM IS HAPPENING IN *ALL* VIDEO PLAYERS, NOT JUST VLC!!

I am experiencing LACK OF COLOR - not a green line at the top of my screen.

---

### Post by Bubba64 on 2008-05-27
> **ralphygarfield said:**
> I looked before, and I didn't see anything called Totem. 

But I'm not on Linux right now so I can't re-check.

Every player has some sort of color adjustment just look for it.

---

### Post by sayakb on 2008-05-27
> **ralphygarfield said:**
> I looked before, and I didn't see anything called Totem. 

But I'm not on Linux right now so I can't re-check.

Forget totem at the moment ;)
Just run Applications->Sound and video->Movie player

(btw, that movie player itself is totem movie player)
Anyway, then follow what I posted (regarding saturation)

---

### Post by billgoldberg on 2008-05-27
> **ralphygarfield said:**
> Looked at your second link - my video problem is NOTHING like that. 

THIS PROBLEM IS HAPPENING IN *ALL* VIDEO PLAYERS, NOT JUST VLC!!

I am experiencing LACK OF COLOR - not a green line at the top of my screen.

The green line is just an example, changing the output to x11 should help with all colour problems.

---

### Post by sayakb on 2008-05-27
> **billgoldberg said:**
> The green line is just an example, changing the output to x11 should help with all colour problems.

X11 output is pixelated and looks ugly with small sized video outputs.

---

