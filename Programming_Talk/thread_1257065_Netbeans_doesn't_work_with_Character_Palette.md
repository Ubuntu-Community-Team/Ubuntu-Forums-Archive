---
title: "Netbeans doesn't work with Character Palette"
date: 2009-09-03
forum: Programming Talk
---

### Post by s.b.cohen on 2009-09-03
In linux i cannot use alt+ascii key to input some special character so I'm using Character Palette(which is part of gnome-applets) but i am unable to do this in netbeans. I tried version 6.5 and 6.7.1 but always the same: when i select the character and press ctrl+v(paste) nothing happen. Does somebody have any idea how to fix this?

---

### Post by howlingmadhowie on 2009-09-03
> **s.b.cohen said:**
> In linux i cannot use alt+ascii key to input some special character so I'm using Character Palette(which is part of gnome-applets) but i am unable to do this in netbeans. I tried version 6.5 and 6.7.1 but always the same: when i select the character and press ctrl+v(paste) nothing happen. Does somebody have any idea how to fix this?

i don't know why netbeans doesn't allow that.  maybe ctrl-V has been clobbered by some netbeans specific key combination.

what you can do under gnome (and i very much hope netbeans will allow it) is shift-ctrl-u #UNICODE NUMBER#
for example, to get ü, i type shift-ctrl-u 0 0 f c #enter#

maybe this will help.

---

### Post by s.b.cohen on 2009-09-03
> **howlingmadhowie said:**
> i don't know why netbeans doesn't allow that.  maybe ctrl-V has been clobbered by some netbeans specific key combination.

what you can do under gnome (and i very much hope netbeans will allow it) is shift-ctrl-u #UNICODE NUMBER#
for example, to get ü, i type shift-ctrl-u 0 0 f c #enter#

maybe this will help.

Netbeans supports ctrl-V but problem is when i select the character and press ctrl-V  than instead of the desired character is the previous content of the clipboard insert. Unfortunately, unicode numbers are different from ascii so it is impossible for me to remember them.

---

### Post by howlingmadhowie on 2009-09-03
> **s.b.cohen said:**
> Netbeans supports ctrl-V but problem is when i select the character and press ctrl-V  than instead of the desired character is the previous content of the clipboard insert. Unfortunately, unicode numbers are different from ascii so it is impossible for me to remember them.

actually unicode numbers are the same as ascii with two zeros in front, so ascii 78 becomes unicode 0078 (the letter 'x').

i've just installed and tried netbeans 6.5.1 on my system (amd64, jaunty) and it doesn't like ctrl-shift-u #number#.  stoopid netbeans. however using the gnome character table and pasting the character works for me.

---

### Post by s.b.cohen on 2009-09-03
Now i found out that character is copied into clipboard automatically when i select it on my character palette on gnome panel but when my netbeans is in the foreground this never happen - really confusing for me....

---

### Post by s.b.cohen on 2009-09-03
> **howlingmadhowie said:**
> however using the gnome character table and pasting the character works for me.
Yes this works but i think it is little uncomfortable. I just want to paste it directly from character palette from gnome panel and not from gnome character table.

---

