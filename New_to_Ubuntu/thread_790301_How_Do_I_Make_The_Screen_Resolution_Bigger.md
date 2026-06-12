---
title: "How Do I Make The Screen Resolution Bigger?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by jonnie2004jonniesweb on 2008-05-11
Hello,

I just installed ubuntu and I like it. The only problem is that the max screen resolution that I can currently view is 800 x 600. I have a 1440 x 900 widescreen. How can I make the resolution bigger?

Jonnie

---

### Post by SunnyRabbiera on 2008-05-11
To start off: what version are you using?

---

### Post by natirips on 2008-05-11
Try System->Settings-> (something with screen resolution (I don't have english version)).

---

### Post by SunnyRabbiera on 2008-05-11
> **natirips said:**
> Try System->Settings-> (something with screen resolution (I don't have english version)).

Well I am under the impression that didn't work for him/her thats why he/she is asking this.
I am also under the impression that he/she is using hardy, but I am waiting for conformation.

---

### Post by dwaynebrown2k6 on 2008-05-11
i have that same problem too...im a newbie and im using ubuntu 8.04..im using a old amd duron processor which is at 900mhz and im only able to get 800x600 resoultion.. i need to have some bigger resoution i cant stand the big icons really.. im new to this linux thing and chose to use that machine for experiments so please bear with me ok..everything is onboard but i cant seem to find the model mobo nothing is on the mobo itself...please help

---

### Post by SunnyRabbiera on 2008-05-11
> **dwaynebrown2k6 said:**
> i have that same problem too...im a newbie and im using ubuntu 8.04..im using a old amd duron processor which is at 900mhz and im only able to get 800x600 resoultion.. i need to have some bigger resoution i cant stand the big icons really.. im new to this linux thing and chose to use that machine for experiments so please bear with me ok..everything is onboard but i cant seem to find the model mobo nothing is on the mobo itself...please help

well for you the screens and resolutions app might be for you, its hidden so you have to unhide it by going up to your menu, right clicking it and selecting "edit menus"
in the menu editor go down to "other" and scroll down to "screens and graphics" and click on the little box next to it and close the menu editor.
open the app up now you have it in your menus and play around with the monitor settings in the first tab, I know I had to play around a bit before I got my monitor the way I want it.

---

### Post by jonnie2004jonniesweb on 2008-05-11
The version that im running is: Ubuntu 8.04 LTS

---

### Post by fatherdaly on 2008-05-11
I think you might have to alter the xorg.conf file to allow your resolution.

go the the terminal and paste in this:


sudo gedit /etc/X11/xorg.conf

Then find the bit about resolutions and add in the one you want.

It worked for me in 7.10 - so I'm not entirely sure its the same in 8.04. Worth a try though.

---

### Post by SunnyRabbiera on 2008-05-11
> **jonnie2004jonniesweb said:**
> The version that im running is: Ubuntu 8.04 LTS

then the instructions I gave above will apply...
That should work for you, the screens and graphics approach worked for me.

> **fatherdaly said:**
> I think you might have to alter the xorg.conf file to allow your resolution.

go the the terminal and paste in this:


sudo gedit /etc/X11/xorg.conf

Then find the bit about resolutions and add in the one you want.

It worked for me in 7.10 - so I'm not entirely sure its the same in 8.04. Worth a try though.


well with any luck they wont even have to touch the xorg file.

---

### Post by jonnie2004jonniesweb on 2008-05-11
> **SunnyRabbiera said:**
> well for you the screens and resolutions app might be for you, its hidden so you have to unhide it by going up to your menu, right clicking it and selecting "edit menus"
in the menu editor go down to "other" and scroll down to "screens and graphics" and click on the little box next to it and close the menu editor.
open the app up now you have it in your menus and play around with the monitor settings in the first tab, I know I had to play around a bit before I got my monitor the way I want it.

I tried this and it seems to work but my widescreen lcd can only run at 56hertz. what can i do to change the hertz?

---

### Post by SunnyRabbiera on 2008-05-11
> **jonnie2004jonniesweb said:**
> I tried this and it seems to work but my widescreen lcd can only run at 56hertz. what can i do to change the hertz?

well that part I cannot help with, even if your monitor is listed it might be best to experiement with the others.
My monitor is usually picked up as a generic plug and play monitor, but I get better performance by using one of the LCD options...
Just experiment a bit, if something goes wrong we can teach you how to fix it id needed.

---

### Post by jonnie2004jonniesweb on 2008-05-11
okay. I changed the screen resolution in system to 56 hertz whenever I try to change the resolution in system and graphics preferences to 1440 x 900 the hertz changes to either 60 or 75 hertz.

---

### Post by jonnie2004jonniesweb on 2008-05-11
> **SunnyRabbiera said:**
> well that part I cannot help with, even if your monitor is listed it might be best to experiement with the others.
My monitor is usually picked up as a generic plug and play monitor, but I get better performance by using one of the LCD options...
Just experiment a bit, if something goes wrong we can teach you how to fix it id needed.

Okay I'll Experiment.

---

### Post by jonnie2004jonniesweb on 2008-05-11
it doesn't seem to be working for me. Is there another way to do this?

---

### Post by SunnyRabbiera on 2008-05-11
well is using lower hertz causing you issues?
if not I would ignore it and just stick with what works.
You getting screen flicker or anything odd like that?

---

### Post by jonnie2004jonniesweb on 2008-05-11
when I go for higher hertz the screen adjusts and a messed up black and white pattern shows up. then the screen and graphics program pulls me back to normal settings. it then says "the configuration test failed".

---

### Post by SunnyRabbiera on 2008-05-11
what about lower hertz?
what is the max hertz of your monitor?

---

### Post by jonnie2004jonniesweb on 2008-05-11
lower hertz works but the resolution is bad.
the max hertz for my lcd monitor is 56 hertz.

---

### Post by SgtLegend on 2008-10-30
Hi,

I just recently started getting into Linux Ubuntu 8.04 and i have this problem. The drivers for my motherboard come with Ubuntu but its not showing the full resolution sizes that my screen can reach.

Ive tried everything from this post but it doesnt help. Im using a 17" moniter CRT with a SIS 661FX i think it is.

Really need to make the resolution smaller

Cheers,
Chris

---

