---
title: "Is remapping broken . and , keys to the right ALT and CTRL keys possible ?"
date: 2018-01-05
forum: New to Ubuntu
---

### Post by j0hnick on 2018-01-05
Hi,

I have an old Dell Inspirion 6400, and Lubuntu has brought new life to it. The , and . keys no longer work on the keyboard, and I am having to reply on copying and pasting them from a text file on the desktop, less then ideal, I was wondering if it was possible to remap the keys to 2 other keys I rarely use such as the left ALT and CTRL keys ?. I have done this on Windows before, but no luck so far on Linux.

Thanks in advance

---

### Post by Holger_Gehrke on 2018-01-06
xmodmap can do this and more.```
man xmodmap
``` in a terminal for all the gory details. You will also need xev to get the numerical keycodes for the keys you want to change. Don't forget to remove the keys from the modifier maps before re-assigning them.

Holger

---

### Post by j0hnick on 2018-01-07
Ill give it a shot, thanks

---

