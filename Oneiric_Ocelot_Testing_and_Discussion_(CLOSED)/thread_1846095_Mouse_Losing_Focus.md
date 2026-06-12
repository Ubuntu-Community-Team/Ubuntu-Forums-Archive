---
title: "Mouse Losing Focus"
date: 2011-09-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by whinis on 2011-09-18
I am unsure what exactly is happen so I explain what I see. 
Sometime when running more than one application/window if a new window pops up my mouse seems to lose focus with the entire desktop. I can see the new windows however I can not click anywhere including the revealed side bar. I can however type in the windows and even switch focus with alt+tab or the side bar. Some times I can get it to refocus by launching a new application or closing the frozen application. Only constants between "crashes" for lack of a better term is terminal open and folders(nautilus) open.

Ubuntu 11.10 64-bit
Nvidia 260m
Intel i7
4gb ram
Laptop asus g51j-a1

---

### Post by mc4man on 2011-09-18
If it any point in your session (unity 3d only) you're minimizing a window(s) then bad behavior will occur. 
If this is happening without ever minimizing  a window then don't know

To workaround the min window issue till fixed run this, log out/in
```
gconftool-2 -s -t boolean /apps/compiz-1/plugins/unityshell/screen0/options/show_minimized_windows false
```
or ck. in ccsm > unity > switcher

---

### Post by whinis on 2011-09-18
Ill try that, However the part that I find odd is that when the desktop gets screwed up the power cog in the corner disappears and the user name buts right up to the edge of the screen.

---

### Post by PaulInBHC on 2011-09-18
> **whinis said:**
> Ill try that, However the part that I find odd is that when the desktop gets screwed up the power cog in the corner disappears and the user name buts right up to the edge of the screen.

I get the same thing sometimes.

Last night I had the launcher stay on screen and I could not get it to close. I had to restart.

---

### Post by berthiggins on 2011-09-19
Thanks Mc4man I had the same issue it was chronic at times.
I ran the command that you posted it  now seems to be cured

---

### Post by whinis on 2011-09-23
After messing with it for a few more days, It appeared to be tied to the sleep function as my mouse becomes unresponsive after resuming from sleep ( give or take a few minutes)

---

