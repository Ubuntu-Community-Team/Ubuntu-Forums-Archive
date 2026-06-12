---
title: "Gnome-Terminals won't quit"
date: 2011-08-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2011-08-08
When I close a terminal it seems to run in the background and if I open it again its a new one.
Ive had 4 running in the back and it takes all the memory.
Trying to restart or shutdown hangs and waits for all of them to stop, which they don't.
Any solution ?

---

### Post by cecilpierce on 2011-08-08
Just opened 3 more and Lock-up trying to do a screen shot,bummer
:confused:

---

### Post by watsbe on 2011-08-08
Me too, but when I tried to recreate it with another terminal window open, it didn't happen.
Not sure if it occurs with terminal session, or just when I exit using CTRL-D, or when I've used ssh to look at another box.

---

### Post by cecilpierce on 2011-08-08
@watsbe
Looks like we are the only ones :P
Ive tried Ctrl+D, the close button and exit, nothing seems to kill it from running in the background eating up memory !
Even the screen-shot thing was running twice,
Oh well, I'm going to see if there is a bug report.

---

### Post by mc4man on 2011-08-08
iF you are using nvidia drivers then read Thru here
[http://ubuntuforums.org/showthread.php?t=1818790](http://ubuntuforums.org/showthread.php?t=1818790)
gist of it - downgrade nvidia or provide yourself cairo libs without gl support, ppa linked for convenience near end of thread

---

### Post by cecilpierce on 2011-08-08
@mc4man
Thats it for me, haven't used synaptic in awhile so I didn't notice it locking up to.
Was thinking of going back to nouveau driver for now, ya think that would work ?

Thanks for the info

---

### Post by mc4man on 2011-08-08
> Was thinking of going back to nouveau driver for now, ya think that would work ?
nouveau should be fine or if wanting to keep nvidia then I'd use the non gl cairo libs, easiest thru the ppa linked in post 25
(non gl cairo also prevents the dirtying of memory currently seen with the gl cairo and nvidia

---

### Post by cecilpierce on 2011-08-08
> **mc4man said:**
> nouveau should be fine or if wanting to keep nvidia then I'd use the non gl cairo libs, easiest thru the ppa linked in post 25
(non gl cairo also prevents the dirtying of memory currently seen with the gl cairo and nvidia

Thanks for the help, I would have never figured that out (CRS) :P :P

Back to nouveau, works fine, got memory back, cpu is cooling off :D and Im a 'crappy hamper' I mean 'happy camper'   :confused:

Thanks again

---

