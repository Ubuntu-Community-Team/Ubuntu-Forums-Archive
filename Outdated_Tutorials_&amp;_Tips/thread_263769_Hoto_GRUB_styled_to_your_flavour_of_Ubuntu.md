---
title: "Hoto: GRUB styled to your flavour of Ubuntu"
date: 2006-09-23
forum: Outdated Tutorials &amp; Tips
---

### Post by alecjw on 2006-09-23
This really quick and easy howto is about making your GRUB menu fit the theme of you flavour of Ubuntu.

In the terminal, type gksudo gedit /boot/grub/menu.lst (or kdesu kate /boot/grub/menu.lst in kubuntu)

Then find the line beginning, "#Pretty Colours"

On the next line, add the appropriate text as shown below....

(thanks to gimfred for telling me about the menu.lst thing)

[SIZE="5"]Ubuntu[/SIZE]
Type in "color yellow/brown yellow/red" without the quotes. Press save and exit.

[size="5"]Kubuntu/Xubuntu[/size]
Type in "color light-gray/blue dark-gray/cyan" without the quotes. Press save and exit.

---

### Post by gimfred on 2007-03-25
Alternatively, in a terminal in your favourite gui, 
type:
```
kdesu kate /boot/grub/menu.lst

``` Sorry couldn't remember Gnomes equivalent command for kdesu (gedit would be the equivalent text editor)

and scroll down to:
```

# Pretty colours

```
and type the following _directly_ underneath:
```

color light-gray/blue dark-gray/cyan

```
If there is already something there, put a # symbol before it.

No need to wear out your esc button :)

---

### Post by Nikron on 2007-03-25
It's gedit in gnome..

Anyway, you press escape when the GRUB is counting down..

---

