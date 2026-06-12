---
title: "[SOLVED] help with screensaver compiz plugin"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-07-06
i just compiled the screensaver plugin for compiz

the problem is that the screensaver only runs once.

if i login it takes 5 minutes for the screensaver to turn on
but if it comes on and i move the mouse to turn it off, it never comes back on

in CCSM i setup an activation key 
(so now i can press ctrl-s and the screensaver comes on) 
and that works every time, but if i jsut let the computer sit then the screensaver never comes on after the first time

so basically is there a fix?

or, is there any way that i can make the button combinaion (ctrl-s) automatically happen after 5 minutes of inactivity?

i know its kindof a ghetto idea, but if thats possible can someone show me how?

---

### Post by ChameleonDave on 2008-07-07
It works fine for me.

That plugin is, I believe, beta software.  It cannot therefore be relied upon.  You might consider reporting the bug to the Compiz developers.

---

### Post by tjwoosta on 2008-07-07
yea i know its a bug and i know this is an unsupported plugin

but is there any way that i can do what i said above?

---

### Post by superbenny on 2008-07-07
You could write a script that sends a faux-keypress to the system, and then set it up to go off after 5 min of inactivity. I know its do-able, I just am not sure how. But that should point you in the right direction.

---

