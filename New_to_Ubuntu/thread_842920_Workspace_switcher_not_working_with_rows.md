---
title: "Workspace switcher not working with rows"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by leemajors on 2008-06-27
Hi

My workspace switcher won't let me use rows!

With 1 row, 2 columns i can switch back and forth between workspaces, merrily, happily and without a care in the world. I can even (i know crazy but true) add more columns and the switcher seems content to let me continue the madness.

But if I switch to 2 rows, 1 column, I can't switch to the second workspace! Clicking on it even doesn't work.

Can anyone tell me why?

---

### Post by Journeyman on 2008-06-27
what version of ubuntu are you using? and have you tried doing alt-ctrl-UP/DOWN or just clicking on the space viewer?

---

### Post by leemajors on 2008-06-27
using 8.04. yes, tried using both the keyboard shortcut and clicking on the space viewer.

clicking each space with a single row configuration works perfectly. change it to 1 column 2 rows however and you can't click on the second workspace. it just ignores it.

---

### Post by mcduck on 2008-06-28
Are you using desktop effects? In that case install the compiz settings manager, and configure your workspaces from there.

---

### Post by mc4man on 2008-06-28
If you have compiz adv. effects - with Desktop Cube enabled you can access up to 16 columns in 1 row. You can either slide them linearly or flip them by enabling Rotate Cube. If you have Desktop Wall enabled you can have up to 16 columns in 16 rows. (how you'd keep track I don't know) Super+e works ok up to 8/8

---

### Post by leemajors on 2008-07-04
yeah, i'm using compiz to configure the cube. still nothing -- i can switch horizontally but not vertically.

---

### Post by viralbug on 2008-07-17
have you found a solution to this? im also facing the same problem.

---

### Post by mcduck on 2008-07-17
If you use the cube plugin, you can't have more than 1 horizontal row of workspaces. There is nothing where to switch vertically. The cube only has one row of usable faces. If you want more desktops, you can:

1) Use more virtual desktops, which means you get more than 1 cube.

2) Use Desktop Wall plugin instead of Cube. This allows as many desktops in both directions as you want, but of course without the cube effect.

3) Increase the horizontal size to get more faces for the "cube", changing it from a cube to  more complex polygon.

---

### Post by LtPitt on 2008-12-21
So...
If I got it right...

When I use the cube and I want to get 4 faces I have to put in compiz config horizontal virtual size = 4 and vertical virtual size = 4, right?

So, in that case, I have to switch off normal workspace switcher because he believes I have 16 desktops, right? 

Is there any way to let 8.04 count correctly my number of desktops with workspace switcher even if I use compiz cube?

Thanks :D

---

### Post by LtPitt on 2009-01-04
A little...
Bump!

---

### Post by Forlong on 2009-01-07
> **LtPitt said:**
> When I use the cube and I want to get 4 faces I have to put in compiz config horizontal virtual size = 4 and vertical virtual size = 4, right?
Only **Horizontal Virtual Size** needs be changed &#8211; the other values should be left at 1 for cube.

btw: are you on GNOME, Xfce or KDE?
Because in GNOME, all settings should be parsed from gconf, thus you shouldn't need to go there at all. Just change the number in the first value of the workspace switcher settings.

---

### Post by LtPitt on 2009-01-14
You did it, again =D

---

