---
title: "Transparent windows"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by fractalman on 2011-10-22
Ok, i was playing about with the look of the windows and wanted to know if there's anyway i can get windows that have a transparent background. At the moment they only have a section along the top that is transparent but i wanted them to look like my terminal where i can see my desktop wallpaper behind the text that is being output.  do i need a certain theme installed or can i do this with compiz, i couldn't find any settings that offered a transparent background.  basicly i want all my windows to bee see through,   Thanks

---

### Post by Foxheadz on 2011-10-22
Its somewhat harder with normal windows, but most terminals, under the preferences, have the option to make the window transparent, or to mimic the desktop image that's under the window. In terminal go to edit>profile preferences>background

---

### Post by fractalman on 2011-10-23
Cheers Foxheadz.   I have already set the background of my terminal to transparent.  I think it looks really cool which is why i wanted to be able to achieve the same with my other windows. ie: i'd like to have the same effect  in nautilus and the text exditor and anything else i open.  Was hoping there might be a fairly simple way to achieve this.

---

### Post by 3rdalbum on 2011-10-23
You used to be able to do with using an RGBA plugin. Unfortunately there were a bunch of programs it didn't work with, necessitating a "blacklist" of programs where the RGBA would not apply.

It was planned for Ubuntu a while back, but it appears to have been forgotten about. Or abandoned due to the blacklisting issue, or because Gnome has switched to GTK 3 now and that doesn't work with the RGBA plugin.

Programs such as Gnome Terminal and System Monitor that define RGBA colours can be semi-transparent, but there's currently no way to do it across the whole system with GTK 3. There was with GTK 2, but that's gone now.

Sorry!

---

### Post by verymadpip on 2011-10-23
It could be done with Compiz config settings manager in opacity, saturation & brightness.  The trouble with that is it makes EVERYTHING transparent (or translucent if you keep some opacity) including the text.  I'm guessing that's not really what you want.

I did make ALL of my windows COMPLETELY invisible once, which was a bit hair raising.  That's another story though.

If you're going to try with compiz set the opacity to a reasonable level, say 80%, & it can be lowered from there.  I'd also recommend changing the opacity before you tell it which windows to apply it to.  I can't stress enough do not set opacity to 0 (zero) for all your windows.

[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)


I also don't know how much messing with opacity will interfere with Unity.

---

