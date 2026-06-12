---
title: "Shadows regression from Natty"
date: 2011-10-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Is Mise on 2011-10-11
Anyone else having this problem?

Compiz seems to ignore shadow settings for windows in Oneiric. All window shadows appear to be drawn like unfocused windows were in Natty.

[Bug #864694: Shadow settings only effect menus and tooltips]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/864694")

---

### Post by phibxr on 2011-10-11
> **Is Mise said:**
> Anyone else having this problem?

Compiz seems to ignore shadow settings for windows in Oneiric. All window shadows appear to be drawn like unfocused windows were in Natty.

[Bug #864694: Shadow settings only effect menus and tooltips]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/864694")

Yep, same here. I'll need to check that bug report out, thanks for pointing it out.

Edit: Added a solution to the above bug report. It's actually a bug in the theme itself, Ambiance.

For the records.

```
$ sudo gedit /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml
```

Find the line

```
<frame_style name="normal_focused" geometry="frame_geometry_normal">
```

Scroll down to

```
<shadow radius="[COLOR="DarkRed"]8.0[/COLOR]" opacity="0.75" color="#abde4f" x_offset="1" y_offset="4"/>
```

And change it to read

```
<shadow radius="[COLOR="DarkGreen"]24.0[/COLOR]" opacity="0.75" color="#abde4f" x_offset="1" y_offset="4"/>
```

Save the file.

Switch to another theme and back again, or log out and in again. It should now work as intended.

---

### Post by Is Mise on 2011-10-11
Thanks, the fix works great. I've uploaded a branch to light-themes with the fix and proposed a merge.

---

