---
title: "minor terminal transparency issue"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-06-19
This is a piece of pie, I know it is ... but I cannot remember how to do it - so I come in search of some words of wisdom. 

The transparency is turned on, inside the terminal properties and also enabled in compiz configuration. Yet for some reason, it refuses to show the windows behind it - only the background. 
I am running Ubuntu 12.04 in Gnome Classic. 

Thank you ever so much, as you'll be relieving a huge headache from my brain. 

K.m

Edit - Gnome Classic in Ubuntu 12.04

---

### Post by kabukiM0n0 on 2012-06-20
Noone? someone? anyone? 
Even using the tilda terminal ... the same issue happens ... 
so it has to be something from within my system - i'm assuming. 

k.m

---

### Post by kanikilu on 2012-06-20
For Compiz, make sure the Composite Plugin is enabled. You can do this in ccsm - if it's not installed, do that first: ```
sudo apt-get install compizconfig-settings-manager
``` and then run ccsm and see if the composite plugin is enabled.

I know you said you are using Compiz, so these metacity settings may not help, but I don't think it'd hurt to enable compositing there too: ```
gconftool-2 --set --type=bool /apps/metacity/general/compositing_manager true
gconftool-2 --set --type=bool /apps/metacity/general/compositor_effects true
``` Other than that, I'm not really sure...

---

### Post by kabukiM0n0 on 2012-06-20
Oh wow ... it didn't work at first. Now I've just suddenly opened my terminal and it's properly transparent. Amazing! 

thank you ever so much - no idea what exactly did it, but still ... cheers11 :popcorn:

---

### Post by kanikilu on 2012-06-20
No problem :) It'd be nice for future reference to know which one worked, but I guess doing both changes (compiz composite plugin, and metacity) covers all your bases in case you need to start the "Gnome Classic (No Effects)" session.

---

### Post by kabukiM0n0 on 2012-06-21
I'm not too sure which one worked. 
I went into cssm first - unchecked and rechecked Composite - then with a terminal that was already open (nothing had changed) typed the codes in. 
Again, nothing was different immediantly. i had to restart my computer (for a different reason) and when I opened a terminal it was showing the windows instead of only the back ground. 

I'm assuming, unless something activated when rechecking the Composite option is was the codes for Metacity. But that's only an assumption.

---

### Post by auddin2 on 2012-10-30
For me, the composite plugin was already enabled (which I could see after I installed ccsm), but running the CL commands worked for me immediately (no restart needed)

---

