---
title: "Truely 'absolute beginners talk'"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by Turbo36 on 2011-12-08
Hello to all, this is my first (of many i hope) posts here so apologies if the mods need to move this.
I recently installed Xubuntu from CD (the only ubunutu derivative to get through my company webfilter) to run alongside Win 7 on my Acer 4820.
I was mightly fed up with Windows bloat and boy was i pleased with Xubuntu: simple, fast and great looking. 
However i am a bit of a 'meddler' and after updating and removing some of the pre installed games etc i have managed to break it!
The login panel appears, i enter my password and it loads the desktop image but i get no right click options, no menus etc. However if i press esc i do get options (restart, logoff etc)
Have i managed to damage the desktop environment during my fiddling?
After a while fiddling i got thinking, i now know i want to run a Linux of some kind, (love the software manager) but there are so many choices.
So do i repair Xubuntu (with your kind help) or go for a different choice?
My shortlist is:
Mint (supposedly more user friendly, with less need for fiddling, but looks as though it is going closer to windows in terms of bloat)
Xubuntu, love the software bundel (firefox, thunderbird etc)
Lubuntu, looks quick but would need to change the software to meet my preferences (ie FF, TB)
 
My PC is fairly powerful (2GB Ram to be 6 after xmas) and a core i3 processor) so i am not sure if X or L would be overkill but i do like streamlined and quick.
 
Ideally i would like to fix Xubuntu and then make my decision on what to go for with your advice.
I consider myself to be an experienced Win user but have no programming experience, something i would like to remedy in due course.
 
Sorry this thread is a mess, but your help/advice would be appreciated.

---

### Post by nothingspecial on 2011-12-08
Hi, welcome to the forums. Sounds like you have removed your panel. Can you remember exactly what you removed?

Your computer will happily run any 'buntu with 2gig of Ram.

Try them all, run them all, see which you like best. :)

---

### Post by Turbo36 on 2011-12-08
I think your advice on trying them all seems like a plan.
I suspect the issue with Xubuntu stems from me trying to close a program by right clicking in one of the 2 rectangluar boxes in the top right hand corner. It popped up with a warning/confirmation box (something about it being permement?) but before i got a chance to read it i had accidentally clicked ok (not used to new touchpad)
 
Before anyone asks yes i realise this probably sounds like i am an idiot :(

---

### Post by nothingspecial on 2011-12-08
If you still have a panel you can add back whatever you removed by right clicking an empt area of the panel and choosing Panel > Add new items

---

### Post by Turbo36 on 2011-12-08
unfortunatly i have no right click options. in the top left corner there is a small grey block (maybe 1.5mm square) but again i cant do anything with it

---

### Post by Turbo36 on 2011-12-08
update:
Xubuntu has jst showed me an update regarding my battery life (as normal) but when i interact with it it turns to a grey box.
When i suspend it shows me the volume, network messages as normal but then dies to a grey background.
It feels like xu is working behind the scenes but i cant use it.

---

### Post by blackbird34 on 2011-12-08
in gnome i think you can get a panel up by typing: ```
 gnome-panel 
``` in Terminal. In xfce the command ```
 xfce4-panel 
``` exists, i checked, maybe you could try it to get a new panel up. if in doubt type ```
 man xfce4-panel 
``` to check if it really is that.

---

### Post by Turbo36 on 2011-12-08
> **blackbird34 said:**
> in gnome i think you can get a panel up by typing: ```
 gnome-panel 
``` in Terminal. In xfce the command ```
 xfce4-panel 
``` exists, i checked, maybe you could try it to get a new panel up. if in doubt type ```
 man xfce4-panel 
``` to check if it really is that.
 
 
Blackbird thank you for this.
i have tried xfce4-panel, it reports as not installed.
I followed:
 
sudo apt-get install xfce4-panel.
 
I now get my menus! (hurrah!) but when i select and de select they leave a grey outline after.

---

### Post by LewisTM on 2011-12-09
If you were missing xfce4-panel, you are probably missing a lot more stuff, maybe even a window manager.
If you can get to a terminal, enter 
```
sudo apt-get install xubuntu-desktop
```
This should restore everything.
If it works, you can go on to install xfce4-goodies and xubuntu-restricted-extras which should be the first step for any new Xubuntu user.

Then enjoy!

---

