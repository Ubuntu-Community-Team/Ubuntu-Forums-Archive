---
title: "Is it possible to execute bash script in fluxbox right click menu?"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by NotLikingIt on 2008-10-05
I think I have done playing around with the startup in fluxbox, and I decided to move on to menu today.

I made a bash script that copies the current menu file to a .menu_old
while cping the one in /usr/X11/fluxbox/fluxbox-menu (some path like that.., well..where the auto-generated menu is) to my ~/.fluxbox/menu


I ran it in terminal and it worked fine

but It doesn't seem to be working on the actual menu

I have 
 [exec] (Recover Menu) {bash recovermenu.sh}<>
in my menu file, but it doesn't seem to be doing anything when I click on Recover menu

Any idea would be appreciated, thanks in advance

Sorry..I was being dumb -_-

---

### Post by cardinals_fan on 2008-10-05
> **NotLikingIt said:**
> 
I have 
 [exec] (Recover Menu) {bash recovermenu.sh}<>
in my menu file, but it doesn't seem to be doing anything when I click on Recover menu

Do you have ```
[exec] (Recover Menu) {bash **/path/to/recovermenu.sh**}<>
```in the file?

---

