---
title: "conky settings for gnome classic"
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Gnurfos on 2011-10-07
The best I could find is:

[PHP]own_window yes
own_window_type desktop
own_window_transparent yes[/PHP]

The problem is that conky disappears if I click on the desktop background anywhere not on the conky display. It disappears only for the current workspace.

Is there a solution to have it run perfectly with gnome classic ?

---

### Post by Quackers on 2011-10-07
Have you tried ```
own_window_type override
``` instead of ```
own_window_type desktop
```

---

### Post by Gnurfos on 2011-10-07
Yes, conky does not show up at all with that.

---

### Post by Quackers on 2011-10-07
Hmm, here are my settings for a Natty installation, but that's using Unity, not classic gnome. It may give you a pointer, and whatever you try that doesn't work you can just comment that line out with a # at the start of the line
```
own_window yes
own_window_class Conky
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar

```

---

### Post by Gnurfos on 2011-10-07
Not showing either, with this.

I found settings that make it show and not hide, in this post: [http://ubuntuforums.org/showthread.php?t=1309306](http://ubuntuforums.org/showthread.php?t=1309306)

But there is still a problem: the wallpaper is "torn". There is a vertical shift at the conky border, as if conky did not capture the right zone.

Is there a solution for this, or a way to have real transparency ?

---

### Post by Quackers on 2011-10-07
I wouldn't have thought that the settings for gnome-shell would work in gnome classic.
What are your "own_window " entries in .conkyrc now?

---

### Post by Gillingham on 2011-10-07
> **Gnurfos said:**
> Not showing either, with this.

I found settings that make it show and not hide, in this post: [http://ubuntuforums.org/showthread.php?t=1309306](http://ubuntuforums.org/showthread.php?t=1309306)

But there is still a problem: the wallpaper is "torn". There is a vertical shift at the conky border, as if conky did not capture the right zone.

Is there a solution for this, or a way to have real transparency ?

If you use
```

#own_window_transparent yes
own_window_argb_visual yes
own_window_argb_value 00

```
it should work, and I'm using a "normal" window.

David

---

### Post by Gnurfos on 2011-10-07
This combination, for example, works (except the wallpaper alignment):

```
own_window_class Conky
own_window yes
own_window_type conky
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_hints undecorated,sticky,skip_taskbar,skip_pager
```

---

