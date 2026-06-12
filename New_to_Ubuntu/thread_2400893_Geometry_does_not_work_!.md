---
title: "Geometry does not work !"
date: 2018-09-11
forum: New to Ubuntu
---

### Post by panikim on 2018-09-11
[COLOR=#212121][FONT=arial]I'm using Exec=lxterminal --geometry=40x4+0-24 on a .desktop boot, however only window size works (40x4), window position (+0-24) does not work anyone know why?[/FONT][/COLOR]

---

### Post by yetimon_64 on 2018-09-12
> **panikim said:**
> [COLOR=#212121][FONT=arial]I'm using Exec=lxterminal --geometry=40x4+0-24 on a .desktop boot, however only window size works (40x4), window position (+0-24) does not work anyone know why?[/FONT][/COLOR]
I don't think it is supposed to going by "man lxterminal"; the description for the "--geometry" switch is in the next code box ...
```
        --geometry=CHARACTERSxLINES
           Set the terminal's size in characters and lines.

```
It seems like it will only set "characters by lines" as there is no mention of x,y positioning in the man file.

I often use the devilspie/gdevilspie packages to control positioning  of windows for specific locations on the screen like you seem to be wanting here. It may be worth you having a look into "gdevilspie" for such. In the gdevilspie interface you can add new rules for any specific application or window for various aspects including "geometry" (which is the setting you would use for "x,y" screen location for any particular windows).

---

### Post by again? on 2018-09-12
Consider using another terminal that observes X window geometry.
eg xfce4-terminal

You can position and resize where you want it then run
```
xwininfo
```
Copy and paste the geometry info from last line into
```
xfce4-terminal --geometry=
```
[ATTACH=CONFIG]281056[/ATTACH]

xfce4-terminal also has a Quake-style terminal console option as shown in above gif.
```
xfce4-terminal --drop-down
```
[ATTACH=CONFIG]281057[/ATTACH]

---

### Post by panikim on 2018-09-14
@guber2 Thank you my friend, it worked perfect!!

---

