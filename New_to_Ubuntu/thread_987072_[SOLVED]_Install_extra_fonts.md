---
title: "[SOLVED] Install extra fonts?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by CinemaScope on 2008-11-19
When I was using kubuntu I drag/dropped some favourite True Type fonts I copied from a Windows machine to a font folder. These were then available in applications like OpenOffice writer. I tried to do the same thing with Ubuntu 8.10 (I moved over because I couldn't live with the changes in KDE 4.1), but I was not allow to do it. Can someone explain how I do this -- full explanation is required (I'm a real newbie).
Many thanks.

---

### Post by LeAstrale on 2008-11-19
In most cases the package named ubuntu-restricted-extras should do the trick for you :)

it has flash, java and non-free fonts.

---

### Post by Elfy on 2008-11-19
If there are any fonts not in the package you want I put them in a hidden foilder in /home - .fonts

Update the font cache

```
sudo fc-cache -fv
```

---

### Post by CinemaScope on 2008-11-19
Many thanks both. Because I wanted to use a special Courier font for screenplays I tried the latter method. However, when I entered the command in the terminal I got back: "sudo: fc: command not found." Before posting this as a problem, I checked OpenOffice Writer and the couple of new fonts were in the font drop down list. I quickly tried the type tool in GIMP and the fonts were also listed in that application too. so, seems to work (I don't know if anyone wants to say anything about the terminal command) -- thankyou once again.

---

### Post by Elfy on 2008-11-19
best paste if you're not too sure - you must have had a space somewhere ;)

---

