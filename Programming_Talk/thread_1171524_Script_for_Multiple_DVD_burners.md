---
title: "Script for Multiple DVD burners"
date: 2009-05-27
forum: Programming Talk
---

### Post by MepisReign on 2009-05-27
Hi:
I've trying to write a script so I can burn the very same ISO image on different DVD burners. So far and using cdrecord I've accomplished to burn on the 2 drives but it burns on the first one and then burns on the second. I mean that is burning on one at a time. You Oh Scripting Wizards could lead me so I can get the job done? :P

The script (which is very simple) since I'm a complete n00b is as follows:

#!/bin/bash
cd /home/bob/DVD
cdrecord dev=4,0,0 -data -eject speed=4 DVDVIDEO.iso
cdrecord dev=5,0,0 -data -eject speed=4 DVDVIDEO.iso

I would also like and once the script is complete, add it to nautilus. The final idea is right click on the ISO image and set it to burn right away.

Please let me know if you need more information, even that is a very simple "project" script.

Best Regards and Thank YOU in advanced,

MepisReign

P.S.: Also tried wodim, here is the script

#!/bin/bash
cd /home/bob/DVD
wodim -dao -data -eject dev='/dev/scd2' speed=4 DVDVIDEO.iso
wodim -dao -data -eject dev='/dev/scd3' speed=4 DVDVIDEO.iso

---

### Post by UbuKunubi on 2009-05-27
What happens if you use separate terminal instances to burn to each drive?

Just wondering,
Ubu

---

### Post by MepisReign on 2009-05-27
I definitely could try, most probably will make the burn at the same time, but that's precisely the main idea, with a single script burn the discs (in this case 2) simultaneously. :)
There is a software called turbojet2 which is a front end of cdrecord, was written to run in KDE and it misses some things when is executed on gnome.
I know that little script of mine is missing something, and also I know for sure that I need to add just a detail in order to work properly and that's the issue, I just don't know what it is...:(

Greetz!!

MepisReign

---

### Post by necromantula on 2009-05-27
Put a single ampersand (&) on the end of each cdrecord command, and it will run them in the background

---

### Post by MepisReign on 2009-05-27
> **necromantula said:**
> Put a single ampersand (&) on the end of each cdrecord command, and it will run them in the background


You mean like this?
#!/bin/bash
cd /home/bob/DVD
cdrecord dev=4,0,0 -data -eject speed=4 DVDVIDEO.iso &
cdrecord dev=5,0,0 -data -eject speed=4 DVDVIDEO.iso &

---

### Post by MepisReign on 2009-05-27
Could somebody point to me into the right direction?
All I need is to be able to burn 2 DVD discs at the same time and the very same iso image. For somebody who knows how to write down scripts shouldn't be too difficult, Am I mistaken?

Greetings

MepisReign

---

### Post by MepisReign on 2009-05-28
bump :(

---

### Post by necromantula on 2009-05-28
> **MepisReign said:**
> You mean like this?
#!/bin/bash
cd /home/bob/DVD
cdrecord dev=4,0,0 -data -eject speed=4 DVDVIDEO.iso &
cdrecord dev=5,0,0 -data -eject speed=4 DVDVIDEO.iso &

yeah, just like that. did you test it? unless cdrecord requires user input after it gets ran, it should work great

---

### Post by soltanis on 2009-05-29
Forking them to the background with the & should get the job done for you perfectly.

---

### Post by MepisReign on 2009-05-31
Ok, I will give it a try

Thx for your replies

MepisReign

---

### Post by MepisReign on 2010-12-14
Coming back to my old threat, testing here and there the best results were using the script like this:

#!/bin/bash
cd /home/bob/DVD
cdrecord dev='/dev/scd0' -v  -sao -data -eject speed=4 DVDVIDEO.iso &
cdrecord dev='/dev/scd1' -v  -sao -data -eject speed=4 DVDVIDEO.iso &


Greetz!

---

