---
title: "I screwed up Trash Icon, trying to get defaults back."
date: 2008-06-21
forum: New to Ubuntu
---

### Post by pparks1 on 2008-06-21
So, I figured out how to get into gconf-editor and change the nautilus configuration to show the trash can on my desktop.

Then, I stupidly changed the icon to show the empty trash can.svg file.   Of course, now it always shows empty.

I realize now that I was supposed to use an icon set (or something like that) to make this type of change.

Anybody know how I can get back from the dumb custom icon that I picked back to the default that changes from empty to full as I put things into the trash????

---

### Post by drs305 on 2008-06-21
Depending on what exactly you did while in gconf-editor, this *should* restore the trash icon to the desktop. This is just the command line version of ticking the trash icon box in gconf-editor:

```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'true'

```

Did you copy the trash svg icon or move it from somewhere?

---

### Post by pparks1 on 2008-06-21
I simply right clicked on the trash can on the desktop, clicked on the icon, navigated out to /usr/share/icons/theme_in/question/scalable/places and picked user-trash.svg.

So, of course, now I have that icon and I always have that icon.  Regardless of whether there is trash in the trashcan or not.

Using gconf-editor, I can toggle whether I see it or not...but I always see the darn icon that I picked.  I want to get back to the system default where it toggles between the two icons depending upon the presence of trash.

---

### Post by drs305 on 2008-06-21
Right click on your inadvertently selected new icon, select Properties, then click on your new icon image. Once you have selected it, does a 'Revert' option appear at the bottom of the window. If so, it should change it back to the original icon (which will hopefully change empty/full).

---

### Post by pparks1 on 2008-06-21
Thank you very much....that worked exactly as you thought.  Now, I'm back to where I was.

I appreciate your assistance.

---

