---
title: "Disable Nautilus menu from Desktop"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sptutusukanta on 2011-09-24
I've installed **gnome-shell** on Ubuntu 11.10 and remove unity. Now** I enabled the icons on desktop** using gnome-tweak-tool .
I found that **_there is a menu beneath the activities panel_** on enabling the desktop icons.
How can I** remove this?**

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=202836&stc=1&d=1316851606[/IMG]

Thanks in advance....!!

---

### Post by howefield on 2011-09-24
Thread moved to development forum - "*Ubuntu +1 (Oneiric Ocelot)*"

---

### Post by VinDSL on 2011-09-24
> **sptutusukanta said:**
> I've installed **gnome-shell** on Ubuntu 11.10 and remove unity. Now** I enabled the icons on desktop** using gnome-tweak-tool .
I found that **_there is a menu beneath the activities panel_** on enabling the desktop icons.
How can I** remove this?**
Interesting!

I tried to disable Nautilus as the desktop manager in GS, but it didn't seem to have any affect on GS.  However...

Doing this disabled Nautilus as the desktop manager in Unity, which was a pleasant side-effect.

Heh!  Go figure...  :)

If anyone has the answer, I'm all ears!

EDIT

Just thinking...

Are you running the Ricotz/testing PPA, by any chance?  That's what I use.

Maybe there's a difference between Ricotz/testing PPA and the official repo version of GS, in this regard.

---

### Post by cariboo on 2011-09-24
@sptutusukanta, did you remove appmenu-gtk, when you removed unity? I'm running gnome-shell from the repositories, and I don't see the nautilus menu when running gnome-shell.

---

### Post by jbicha on 2011-09-24
sptutusukanta, what graphics driver are you using?

---

### Post by fazza on 2011-10-07
> **VinDSL said:**
> 
[snip]
Just thinking...

Are you running the Ricotz/testing PPA, by any chance?  That's what I use.

Maybe there's a difference between Ricotz/testing PPA and the official repo version of GS, in this regard.

I get this menu bar too, and I've got the Ricotz ppa as well so it could be that?
Ricotz' ppa has gnome 3.2 in it for Oneiric, so maybe it's not detecting something properly?

---

### Post by cariboo on 2011-10-07
The gnome-shell version in the repositories is:

```
gnome-shell --version
GNOME Shell 3.2.0
```

I would assume the rictoz ppa would be a newer version.

---

### Post by Atermoon on 2011-10-07
I get that too. First time I noticed it was after some partial upgrade screwed Unity and the only thing visible after logging in was the nautilus menu bar on top and the wallpaper.

---

### Post by Bowmore on 2011-10-07
To get rid of nautilus menubar on the desktop just remove
- appmenu-gtk
- appmenu-gtk3
- appmenu-qt

There a bug reported on that issue not yet solved:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/826771](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/826771)

---

### Post by smallblackanimal on 2011-10-12
Same issue, to resolve (cover up) the problem I set the panel opacity to either 0% or 100% in the unity plugin settings in compiz advanced settings manager. Any number in the middle restores the ghost nautilus menu. Not exactly a fix, but you don't have to stare at it anymore while it mocks you from afar.

---

### Post by lime4x4 on 2011-10-12
i have gnome tweak tools installed and under desktop i turned off "have file manager handle desktop" turned off. And that got rid of it for me

---

