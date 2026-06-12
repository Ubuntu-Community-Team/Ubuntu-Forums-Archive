---
title: "HOWTO edit your keyboard mappings"
date: 2005-10-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Jenda on 2005-10-26
[EDIT: Xkeycaps is a program that can do most or all of the work below better and easier. The reason I used the method described below is that xkeycaps didn't let me click anything in its context menus. If this happens to you, the cause is NumLock. If turning it off doesn't help, then use this HOWTO. I managed to use xkeycaps in the end.]
OK. I thank for this solution to a problem I long had to the anonymous person who helped me on his private GNU/Linux forum.

If you need to change just a few things on your keyboard - like switch CapsLock and Shift if you're used to Sun keyboards (or typewriters :) ), this is the place to find out. What I wanted was to use a [dvorak keyboard](dvzine.org), whilst keeping Czech symbols. I sacrificed the top row of numbers, but now I never have to switch keyboard layouts.
I know a guy that insists on having his keyboard arranged alphabetically.

Well, anyway to get to the HOWTO:

---

1. Run: ```
sudo nautilus /usr/share/xmodmap
```
2. Look around. Every xmodmap.something file is a keyboard layout
3. Open the one you wish to edit. This'll be the one that has your language's code after the dot. In my case it was xmodmap.dvorak, for swiss german keyboard it's xmodmap.ch_de etc.
CAUTION: The next step WILL disable the former function of the altered key
4. Find the key you wish to change and change it. You will have to know the keysym for the character or action you want the key to do. If you're just switching two keys, it shouldn't be a problem.
5. Save and exit.
6. The new settings will become active after next login or after you run: ```
xmodmap /usr/share/xmodmap/xmodmap.wha'ever
```
NOTE: replace "wha'ever" with your modified file name

Hope someone finds this useful.

---

### Post by Mujaheiden on 2005-10-30
Is there an easy tool to review my keysims? I have no clue which is which, and my keyboard isnt too near to an other one. (See[ http://www.ubuntuforums.org/showthread.php?t=83251]("http://www.ubuntuforums.org/showthread.php?t=83251"))

---

### Post by Jenda on 2005-11-05
A very easy one indeed. Sorry for the delay - I was away.

```
xmodmap -pke
```

If you check the xmodmap files mentioned above, you can see the keysyms for the layout in question.

---

### Post by Mujaheiden on 2005-12-05
what about the keymapper utility? isnt it available anymore?

---

