---
title: "transparent window borders"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by DarinB on 2008-07-10
I have an old video card geforce 4mx 440...i have been trying to get transparent window borders, i tried simple-ccsm compiz manager but nothing happened or i couldn't get it to work.
i tried installing emerald but couldn't get that to work
i can't figure out how to install GTK 2.0 theme.
either my video card can't do it or i have been doing something wrong for each attempt...any ideas...note i am only into ubuntu for a little over a year.>>>>>I do love it and have converted 5 people away from WindoW$!!!!!!!!
i haven't seem that much, i have messed things up quite a few times though.
any ideas??????????????????????????????????????????

---

### Post by markbuntu on 2008-07-10
You can do this in Emerald. Open the Emerald Theme Manager and click on Edit Themes. The current theme will be there, click on it and a list of frame engines will open, click on your current one and a new window will pop up underneath it. You can adjust the Opacity of the colors there to make the frames transparent.

---

### Post by tjwoosta on 2008-07-10
to install gtk2 themes you can just drag and drop your .tar.gz right into the theme window (system-preferences-appearance  and click the theme tab)

alternatively you could click import and browse to the theme

EDIT: also sometimes people pack the .tar's twice  (dont ask me why) but if it wont install for you take a look inside the .tar.gz and see if there is another inside

---

### Post by DarinB on 2008-07-10
in emerald the themes was empty
how can i get it there?

---

### Post by tjwoosta on 2008-07-11
> in emerald the themes was empty
how can i get it there? 

first find an emerald theme at gnome-look.org  (under beryl)

save to wherever   (remember where)

if the file is compressed (.tar or other) then extract it

you should end up with a .emerald

open emerald theme manager 

click import

now browse to wherever you saved the .emerald

then to make it activate 

press alt-f2

type emerald --replace in the box and hit enter

if it works and you are satisfied with it you can add emerald to the list of startup apps

to do that go to system-preferences-sessions then click "add"

put emerald --replace in the box that says command (whatever you want in the other two)

---

### Post by DarinB on 2008-07-11
i got emerald from synaptic
when i open emerald edit themes says untitled beryl
whet i hit import and browse to .emerald and open thon alt f2 nothing happens
i tried .themes where my themes are it also won't import anything
i wonder what i am doing wrong usually its something silly...its just figuring it out.

---

