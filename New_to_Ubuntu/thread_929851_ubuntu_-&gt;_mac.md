---
title: "ubuntu -&gt; mac"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Dadsgé on 2008-09-25
hellow,

today I installed a MAC-doc on my ubuntu
first it was totaly working fine, but when i rebooted my pc the whole thing was gone, i also can't use my desktop effects anymore...
the strange thing is that the doc is still installed and i can still change the preferences
same goes for the desktop effects

can someone help me with this problem please?

Dadsgé

---

### Post by SpenceMakesSense on 2008-09-25
try running
```
 replace --compiz
```
if that doesnt work try
```
 compiz --replace
```
Then make sure u add the correct command into the sessions menu so it does it on boot up

---

### Post by Dadsgé on 2008-09-25
could it have something to do with the screenlats manager i installed either?
or is it just another malfunction of ubuntu?

---

### Post by SpenceMakesSense on 2008-09-25
well i never really used screenlets I just know that whenever my effects and dock went away(which runs off of compiz) that compiz crashed and I had to restart it with either replace --compiz or compiz --replace. Sorry I cant really check now because I'm at school and I'm lucky this site isn't blocked and they run windows -.-

---

### Post by Dadsgé on 2008-09-25
> **SpenceMakesSense said:**
> try running
```
 replace --compiz
```
if that doesnt work try
```
 compiz --replace
```
Then make sure u add the correct command into the sessions menu so it does it on boot up
owkey, second one worked
but i dont know what kind of command i need to add
i'm having this now:
> hannes@hannes-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 04) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 


---

### Post by SpenceMakesSense on 2008-09-25
Well Im not sure where it is but if you go to system-preferences I think sessions menu is there...if not its in administration. Then add the compiz --replace to the menu. But from the looks of it it might need re installation? Ill check it out when I get home but when files go missing that might be the problem.

---

### Post by Dadsgé on 2008-09-25
hmm but I didn't uninstall or deleted any files xD
don't know how they came to be missing...

could you tell me when you will be back home? 
so i dont have to check this thread every time
eum, it's now 19:00 over here, so i think it would be easier if you would be able to tell it in hours :P

---

### Post by Teamgeist on 2008-09-25
Hi.
Don't type it in a regular terminal.

Hit Alt+F2, then type compiz --replace in the box that appears and hit enter.

This should save the settings.


Also make sure you have Desktop effects enabled in the Appearance window (System --> Preferences--> appearance).

---

### Post by Dadsgé on 2008-09-25
well that is the problem,
if i try to enable it, it gives me a pop-up 'Desktop effects could not be enabled'...

(ps: this was the HOWTO site i followed: [http://blogs.howtogeek.com/tuxgeek/2008/09/08/pimp-your-gnome-in-7-steps/](http://blogs.howtogeek.com/tuxgeek/2008/09/08/pimp-your-gnome-in-7-steps/) )

---

### Post by Teamgeist on 2008-09-25
Ok, don't worry about enabling the desktop effects through the Appearance Window for now.

Just hit Alt+F2 and type ```
compiz --replace
``` This should get it running anyway.

---

### Post by Dadsgé on 2008-09-25
ok, did it
now what?
it still doesnt work...
or is a reboot required?

---

### Post by Teamgeist on 2008-09-25
Actually no reboot required... but try it just for the hell of it. :)

Strange...

What kind of graphics card are you using? Is the correct driver installed?

---

### Post by SpenceMakesSense on 2008-09-25
Hmm...maybe the desktop effects and dock messed with your .xorg file messing up your graphics card installation. I would try reinstaling the graphics card

---

