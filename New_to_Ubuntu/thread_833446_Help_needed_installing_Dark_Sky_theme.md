---
title: "Help needed installing Dark Sky theme"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Hamstermerc on 2008-06-18
I recently found a theme dark sky that i love from gnome-look.org

[http://www.gnome-look.org/content/show.php/Dark+Sky+Suite?content=80947](http://www.gnome-look.org/content/show.php/Dark+Sky+Suite?content=80947)

However i have no idea how to install it. I want to install it using gtk rather than emerald (emerald seems to be problematic as on log in the window borders are missing and i have to switch between gtk and emerald again to get them back.). 

In the tar.gz there is the .emerald package and a gtk-2.0 folder. The file gtkrc looks useful but i have no idea really. Still getting my head around Linux.

Any help is much appreciated :)

---

### Post by steve101101 on 2008-06-18
i think you need to use emerald to use this.

---

### Post by phidia on 2008-06-18
Have you tried clicking on System>Preferences>Appearance and then clicking install and naviagate to the new theme package you want?

---

### Post by steve101101 on 2008-06-18
> **phidia said:**
> Have you tried clicking on System>Preferences>Appearance and then clicking install and naviagate to the new theme package you want?

thats just what i was going to say.

---

### Post by steve101101 on 2008-06-18
i was going to test it for you, but there site isn't loading right now.

---

### Post by steve101101 on 2008-06-18
okay if you download the tar to your desktop. then click system -> preferences -> appearance ... click the install button and select the tar. this will install it for you.

---

### Post by tjwoosta on 2008-06-18
this theme i believe requires both the gtk and emerald parts to work correctly

to install the .emerald theme do this

go to System-Preferences-Emerald then click import and find your theme

then to initiate the theme do this

**press alt-f2** to open the run dialouge (this is important)

then type this in the box
```
emerald --replace
```

[B]i believe the only reason your window boarders dissapear is because you are running the command in a terminal, as i said its important to use the run dialouge instead of the terminal
[/B]

also to add the emerald --replace command to the list of startup apps do this

go to System-Preferences-Sessions and click add

then put the command in the command box and whatever you want in the other two

---

### Post by Hamstermerc on 2008-06-19
Thanks tjwoosta and everyone. The emerald --replace command worked and adding it to the startup commands solved my early problem so now i can use emerald properly. :) Thanks for the speedy help, this is why I'm slowly falling in love with Ubuntu.

---

