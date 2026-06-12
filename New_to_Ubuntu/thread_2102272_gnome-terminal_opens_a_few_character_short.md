---
title: "gnome-terminal opens a few character short"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by Pletched on 2013-01-06
The terminal is opening with smaller y-axis of about 2-3 characters shorter. I'm using a Ubuntu 12.04.

---

### Post by fdrake on 2013-01-06
> **Pletched said:**
> The terminal is opening with smaller y-axis of about 2-3 characters shorter. I'm using a Ubuntu 12.04.

can you post a screen shoot, I don't quite get what you mean. Also check (from terminal menu bar) Edit> Profile prefe; see if you can fix it.

---

### Post by llamabr on 2013-01-06
also, which terminal?  And how are you opening it?  you can effect gnome-terminal's geometry with the --geometry flag.

Everyone always makes a big deal and loses their entire mind when I suggest you read the man page, but in this case (as with most cases actually), it would help.

---

### Post by Pletched on 2013-01-06
I'm opening it the most usual way by clicking it in the gnome-panel. What I mean by shorter is it isn't opening in its default or whatever size I set it too.

It usual opens 2 or 3 characters short vertically, e.g. if it's set to 80x24 it would open 80x21 or 80x22.

---

### Post by Impavidus on 2013-01-07
(Possibly) the same happens using the xfce4-terminal. I open all of my terminals from the launcher on the xfce panel. All are 80 columns wide, but the first I open always has 22 rows, subsequent ones have 24 rows. When I close all of them and open a new one, it again has 22 rows. To me it isn't annoying, just peculiar. I never bothered finding a way to change it.

---

### Post by Calinou on 2013-01-07
On Xfce 4.10, this happens when "rolling" gnome-terminal's window. xfce4-terminal works just fine, though. Maybe try installing xfce4-terminal then use it.

---

### Post by Pletched on 2013-01-08
I found out what was causing it. Using gnome-panel(I mean gnome classic) makes it happen, however using Unity makes it go away.

---

### Post by tgalati4 on 2013-01-08
Try Edit-->Profile Preferences-->set column and width to whatever you want.

Or Edit-->Profiles-->Default-->set column and width.

Or define a custom profile and call the program with a launcher shortcut to load that profile.

---

### Post by Pletched on 2013-01-08
I don't know what I was thinking using gnome-panel(classic) for something that disregards it. I've started using lubuntu.

---

