---
title: "Can't find where to enable Compiz..."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by norfair on 2008-04-27
According to the system's documentation there should be a section under System>Preferences for Advanced Desktop Effects, but I don't have that listing. So, I searched Add/Remove for Compiz and the only thing that comes up is: Desktop Effects, Compiz Setup. This seems like it's it, but the discritions states it as being a "compiz setup tool for KDE." But I'm under GNOME. Does it matter? Is this what I want? Also, when I look under the "Synaptic Package Manager" and search for Compiz, there are lots of entries with the Ubuntu logo, but none are checkable. The little squares are blackened. I just wanted to play around with it, but can't even find where to enable it. Can anyone point me in the right direction, please? Thanks.

(Oh, I'm currenly using 8.04, but couldn't find it under 7.10 either before I upgraded.)

---

### Post by Google Spider on 2008-04-27
```
sudo apt-get install compizconfig-settings-manager
```

You also need emerald

```
sudo apt-get install emerald
```

---

### Post by lamalex on 2008-04-27
You want to install compizconfig-settings-manager

---

### Post by okey666 on 2008-04-27
Ok... To access the basic menu go System>>Preferences>>Appearance and then go to the Visual Effects tab. This will let you enable it and chose from ap pre-set configuration

To access the main configuration menu go Applications>>Add/Remove and then search for Advanced Desktop Effects Settings. When that has installed go System>>Preferences>>Advanced Desktop Effects Settings. This lets you fully customize compiz-fusion.

I hope that helps

---

### Post by elpichi on 2008-04-27
In hardy to enable Compiz effects you can go to appearance preferences and click on the tab "Visual Effects" and pick either normal, or Extra" but if you want to customize it, google spider has the answer to that =]

---

### Post by macogw on 2008-04-27
Don't install Emerald.  
1) Hardy has no themes for it
2) The Compiz team doesn't support it anymore and want to be rid of it...it's very poorly done, and they're considering replacing it.  For now, Compiz can use your regular themes just fine.


Also, I recommend getting the fusion-icon package.  It puts an icon in your notification area so you can switch between Compiz and Metacity (the default) easily, and it gives you quick access to the Compiz settings manager.

---

### Post by norfair on 2008-04-27
I've got it enabled now! Thanks to all. Normally I'd respond to each person to thank them, but you all came through so quickly. Well, you've been thanked via the medal. So, hopefully that'll do!

---

### Post by Google Spider on 2008-04-27
> **macogw said:**
> Don't install Emerald.  
1) Hardy has no themes for it


uh!? I'm using [this]("http://gnome-look.org/content/show.php/Vista-Linux?content=42875") theme on hardy

>  

2) The Compiz team doesn't support it anymore and want to be rid of it...it's very poorly done, and they're considering replacing it.  For now, Compiz can use your regular themes just fine.




Thanks didn't know that.

---

