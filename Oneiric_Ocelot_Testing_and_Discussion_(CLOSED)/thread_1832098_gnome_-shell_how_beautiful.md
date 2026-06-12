---
title: "gnome -shell how beautiful"
date: 2011-08-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rbrick49 on 2011-08-24
This is what I relly love about gnome it has been so faithful through the ages not  so for unity

---

### Post by lkjoel on 2011-08-24
Really? I think that Unity is much simpler than GNOME 3.

Look at what Linus has to say about GNOME 3: [http://www.theregister.co.uk/2011/08/05/linus_slams_gnome_three/](http://www.theregister.co.uk/2011/08/05/linus_slams_gnome_three/)

---

### Post by pferraro on 2011-08-24
> **rbrick49 said:**
> This is what I relly love about gnome it has been so faithful through the ages not  so for unity

Are you referring to the retro window borders?  That's not gnome-shell's fault - this is a bug in the Ambiance/Radiance metacity theme:
[https://bugs.launchpad.net/light-themes/+bug/816953](https://bugs.launchpad.net/light-themes/+bug/816953)
You have 2 options:
1. Fix it yourself.  Edit /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml and comment out the problematic lines.
2. Switch your window border theme to one that works in mutter, e.g. Adwaita

---

### Post by kmsalex on 2011-08-25
i think your being sarcastic.... in which case don't expect people to have to read into your sarcasim and try to help you. if your not being sarcastic... are you blind?

I my self am running gnome 3 but I've got mine looking a bit less... clashy XD

lkjoel I don't believe that he liked unity any better. Thats my problem with both. They seem to try and over simplify everything, gnome 3 for me is liveable but unity is just a step to far.

---

### Post by pressureman on 2011-08-25
The "retro window borders" were fixed yesterday with the upload of new mutter/clutter packages.

---

### Post by xebian on 2011-08-25
> **lkjoel said:**
> Really? I think that Unity is much simpler than GNOME 3.

Look at what Linus has to say about GNOME 3: [http://www.theregister.co.uk/2011/08/05/linus_slams_gnome_three/](http://www.theregister.co.uk/2011/08/05/linus_slams_gnome_three/)

I went back to the classic Gnome as well for the last 2 days.  Does great minds really think the same?  :lolflag:

---

### Post by pferraro on 2011-08-25
> **pressureman said:**
> The "retro window borders" were fixed yesterday with the upload of new mutter/clutter packages.

Are you sure about that?  If I revert my Ambiance theme changes, I still get the default metacity borders.  Doesn't look fixed to me.

---

### Post by sanderd17 on 2011-08-25
> **lkjoel said:**
> Really? I think that Unity is much simpler than GNOME 3.

Look at what Linus has to say about GNOME 3: [http://www.theregister.co.uk/2011/08/05/linus_slams_gnome_three/](http://www.theregister.co.uk/2011/08/05/linus_slams_gnome_three/)

Only because he didn't try Unity, and all things he mentioned can be solved with extensions (and yes, Gnome-Shell is made to be extended).

---

### Post by rbrick49 on 2011-08-25
to whoever it was said I was being sarcastic sorry but you didnt understand I was implying unity3d was useless compared to gnome shell ok gnome shell works just fine thank you

---

### Post by pressureman on 2011-08-25
> **pferraro said:**
> Are you sure about that?  If I revert my Ambiance theme changes, I still get the default metacity borders.  Doesn't look fixed to me.

Yep. Pretty sure.

Are you using gnome-tweak-tool to set your theme/window borders?

---

### Post by mdhollis on 2011-08-25
I use the airlines window borders from bisigi-themes(lucid ppa) and adwaita and I think it looks ok.

---

