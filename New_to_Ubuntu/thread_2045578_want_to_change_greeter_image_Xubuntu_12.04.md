---
title: "want to change greeter image Xubuntu 12.04"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by aem0512 on 2012-08-21
Well, another post here about the way Xubuntu stores its wallpapers. Annoyingly enough it stores them in /usr/share/xfce4/backdrops

When I try to add an image to this location, it doesn't actually work as an image any longer. I can sudo cp the image into the location, but when I try to open it, it just shows a png logo and doesn't open the image. So when I try to use it for anything such as the login wallpaper or desktop wallpaper, it doesn't work at all.

I was able to create a ~/.local/share/xfce4/backdrops folder which I can store images in to use for the desktop wallpaper but I still can't figure out how to use them for the lightdm login.

I first put filename.png into ~/.local/share/xfce4/backdrops.

I've tried: sudo leafpad /etc/lightdm/lightdm-gtk-greeter.conf

and changed the:
background=/usr/share/xfce4/backdrops/xfce-stripes.png

to:
background=~/.local/share/xfce4/backdrops/filename.png

no luck

to:
background=/usr/share/xfce4/backdrops/filename.png

no luck

to: (after moving filename.png home dir)
background=/home/filename.png

no luck

I've tried everything I can think of to change to one of my own images. Nothing seems to work. Any suggestions?

---

### Post by december0123 on 2012-08-21
Does it work when you try to set any other picture from that folder?
Make sure your picture has set right permissions.

---

### Post by brainwash on 2012-08-21
You have to edit the actual config file /etc/xdg/xdg-xubuntu/lightdm/lightdm-gtk-greeter.conf and not the template one.

---

### Post by aem0512 on 2012-08-21
> **december0123 said:**
> Does it work when you try to set any other picture from that folder?
Make sure your picture has set right permissions.

It does work when I use any of the "stock" pictures in the /usr/share/xfce4/backdrops just not when I try to use the one I put in there.

How do I set the right permissions on a picture?

---

### Post by december0123 on 2012-08-21
Use the "chmod" command and make sure that it's readable.
I set mine like this, but it's up to you.
```
 chmod 644 <file> 
```
It gives "read" and "write" to the owner and only "read" to the rest.

---

