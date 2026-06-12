---
title: "[SOLVED] Screen flicker when moving mouse -after return from Suspend !"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by pjnsmb on 2008-05-24
Have not been able to solve my problem since moving over from "The dark side -Windows" a few months ago..............

After using the "Suspend" button in Gutsy and now Hardy my computer returns to use o.k -but- when I move the mouse my screen flickers like crazy !and I have to restart the computer to clear the problem.

I know suspend and hibernate are problems for a lot of us............ I have managed to get hibernate working only through "uswsusp" but have had no luck at all getting suspend to work !


I do not know enough to understand what is causing the problem (obviously) but is there a terminal command to restart "one of the services" to solve the flicker problem to avoid the computer restart  ?

Using Intel graphics card if that helps.

Tried a wired mouse but still the same effect.

thanks to anyone that can help

---

### Post by pjnsmb on 2008-05-25
bump

anyone any ideas please ?

---

### Post by pjnsmb on 2008-05-25
update

almost solved solution

I updated programme "uswsusp" to latest version 0.7-1.1

now I can s2ram and s2disk command o.k

but.............

I can use the  suspend button o.k

if I use the hibernate button my system resumes but without an internet connection !

if I then use the suspend button the system resumes with internet.....

weird but a lot of progress

---

### Post by prshah on 2008-05-25
> **pjnsmb said:**
> 
not know enough to understand what is causing the problem (obviously) but is there a terminal command to restart "one of the services" 

I suspect compiz: you can use Alt+F2 then type in ```
compiz --replace
``` that will restart compiz, without affecting any other programs. If that works, we can then troubleshoot why you're facing the compiz problem in the first place.

If it doesn't try restarting the entire X server; a quick way is Ctrl+Alt+BkSpace but it will drop you back to the login screen. If that too doesn't work, try restarting the gdm as below; this will also drop you at the login screen, but at least you can avoid a restart cycle.

To restart GDM, switch to Ctrl+Alt+F1, login, give the command```
sudo /etc/init.d/gdm restart
```, then when you get the [OK], switch back with Ctrl_Alt_F7.

If any of these work, we can then attempt to see why the problem occurs in the first place.

---

### Post by pjnsmb on 2008-05-25
PRShah
thanks for your advice..........

as I say in my previous post I have suspend working (which I use often) and hibernate with a struggle !

 Now suspend is working ok I do not suffer the flickering screen but I tried your tip about compiz and will keep it for future use. 

I tried your other tip about GDM and it was unsuccesful- I never got the chance to switch back as I got moved to the log in screen............

from my previous post -
if I use the hibernate button my system resumes but without an internet connection !

if I then use the suspend button the system resumes with internet.....

Can you suggest a command to avoid me having to do the above

---

