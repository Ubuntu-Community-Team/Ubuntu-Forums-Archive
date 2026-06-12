---
title: "wxPython - Visual problems"
date: 2009-05-26
forum: Programming Talk
---

### Post by MaxVK on 2009-05-26
Hi. I have been programming wxPython for well over a year now on Gutsy and I recently upgraded (full install from disk) to Jaunty. 

Iv not been doing much development recently and today when I started, to my horror I discovered that the wxWidgets in my applications are all horribly flat!

The most obvious problem being the wxPanel, where it looks flat and nasty no matter what settings I use for a border.

Of course Iv been installing and tinkering with the system since installing, so this could be caused by anything that Iv done, but I have no idea where to start looking.

Can anyone give me a pointer please - I'm a bit lost and I cant possibly put up with these horrible looking controls!

cheers

Max

---

### Post by MaxVK on 2009-05-27
Well, Iv peered into lots of places but to avail - Now I really want to know where the config files for wxPython reside, so I can take a look at them.

Any ideas?

cheers

Max

---

### Post by cdekter on 2009-05-27
If you are running on GNOME then your wxPython install is just a wrapper around GTK (or rather wxGTK, which is a wrapper around GTK). Any theming/appearance would be controlled through the standard GNOME methods.

---

### Post by MaxVK on 2009-05-28
Thanks cdekter - I'm glad you answered this post because Id forgotten it in the excitement of realising that Id changed the theme without paying attention.

Its all sorted now - I had customized a theme but used a set of controls that made the wxWidgets (and anything that might wrap them up) appear flat.

regards

Max

BTW - Does anyone know what happened to the "Mark this thread as Solved" button?

---

### Post by Volt9000 on 2009-05-29
> **MaxVK said:**
> BTW - Does anyone know what happened to the "Mark this thread as Solved" button?

That was taken out some time ago because apparently it caused forum database corruption.

---

### Post by MaxVK on 2009-05-30
> That was taken out some time ago because apparently it caused forum database corruption

Ahh, thanks for that, I didn't know - I got so used to using it and then it was gone!

Cheers

Max

---

