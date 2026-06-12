---
title: "[SOLVED] help, i cant turn off emerald"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-09-25
i installed emerald theme manager a long time ago (like the first day hardy was released)

after choosing my theme i was instructed to run the command 
emerald --replace 
to make emerald run

and so i did 

then i added the command emerald --replace to the startup programs (system-preferences-sessions) 


but now ive decided i want to stop using emerald and go back to the original gnome themes


so i removed emerald from the startup programs, but it didn't work

emerald still starts up every time i login even though i removed it from the startup apps


what do i do now?

---

### Post by RequinB4 on 2008-09-25
Easiest way is to do it from the compiz icon menu:

```

sudo apt-get install fusion-icon

```

---

### Post by mike1234 on 2008-09-25
> **tjwoosta said:**
> i installed emerald theme manager a long time ago (like the first day hardy was released)

after choosing my theme i was instructed to run the command 
emerald --replace 
to make emerald run

and so i did 

then i added the command emerald --replace to the startup programs (system-preferences-sessions) 


but now ive decided i want to stop using emerald and go back to the original gnome themes


so i removed emerald from the startup programs, but it didn't work

emerald still starts up every time i login even though i removed it from the startup apps


what do i do now?

Startup Apps? Just go to system -preferences - appearance and turn off visual effects. I wouldn't bother using that cli replace thing. Too much trouble. Gnome is a nice GUI. I suggest using it so you can "see" what goes on.

M.

---

### Post by tjwoosta on 2008-09-25
nevermind i figured it out on my own again

(i have a habbit of doing that)

the problem was because i installed compiz fusion icon after installing emerald 


then i used compiz fusion icon for a day before deciding to delete it from the panel

so all i had to do was re-open compiz fusion icon and change the setting for window decorator to gtk, then delete the icon again

---

### Post by Tatty on 2008-09-25
```
metacity --replace
``` should have done it too.

---

### Post by tjwoosta on 2008-09-25
> 
metacity --replace

should have done it too. 


that would work to stop emerald but it would also stop compiz 

i still wanted to keep my desktop effects on but i didnt want the emerald theme manager window boarders

---

### Post by NullHead on 2008-09-25
You can use *"gtk-window-decorator --replace"* to replace emerald with the default ubuntu GTK theme.

---

### Post by darkblade009 on 2010-02-23
thanks .

this helps me

---

