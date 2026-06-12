---
title: "Need Help With Themes"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by StardustLuna on 2012-10-24
I'm running ubuntu 12.04 and for the life of me I am not able to install any properly working gtk+ themes!

I am able to install them so that they show up in the tweak tool, yet they're all not working...right. Like the color of the font will be really light and everything just generally does not look like the preview. 

I'm using Gnome-Shell, and I'm able to install and use shell themes just fine, it's the gtk ones that do not work. 

Also, I have not been able to change my icons at all, nor my cursor. I've installed both of them into the /usr/share/icons through nautilus AND in /home/stardustluna/.icons. The cursors do not show up in gnome tweak, and the icons do, but like the gtk, do not work. 

I'm sure the answer is obvious, it's just I feel like I've tried everything, and I'm following the directions that the authors gave me to a 'T' so I don't know what else to do. 

~Stardust

---

### Post by Immolatus on 2012-10-24
you might want to try qt or Metacity themes as Unity3D does not run on gtk but I believe for some reason there are gtk bindings for Unity2D.

If you ran KDE you'd be able to modify everything.

Interesting, I'll keep looking.:guitar:

---

### Post by Dennis N on 2012-10-25
> **StardustLuna said:**
>  

Also, I have not been able to change my icons at all, nor my cursor. I've installed both of them into the /usr/share/icons through nautilus AND in /home/stardustluna/.icons. The cursors do not show up in gnome tweak, and the icons do, but like the gtk, do not work. 

~Stardust

As to changing the cursor (mouse pointer), try the method described in this post:

[http://ubuntuforums.org/showpost.php?p=11929215&postcount=17](http://ubuntuforums.org/showpost.php?p=11929215&postcount=17)

I know this works for Unity and LXDE, and I think it will work for Gnome Shell as well. 

Where it says 'Create cursor.theme file if needed' it looks like this:

```
[Icon Theme]
Inherits=Theme-Name

```

and goes inside the theme's folder. Theme-Name is the exact name you find on the theme's folder.

The 'advanced settings' mentioned there in the last step is the same as gnome tweak. (For someone using Unity, you can use 'My Unity' instead).

As to themes, if a theme doesn't show in gnome tweak tool, I think that tells you it's not compatable for some reason.

---

### Post by StardustLuna on 2012-10-25
Just installed kde. And I love it. Took me just a few minutes to get my desktop exactly how I like it.

---

