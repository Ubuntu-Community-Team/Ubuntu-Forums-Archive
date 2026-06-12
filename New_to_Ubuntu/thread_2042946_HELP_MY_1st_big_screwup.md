---
title: "HELP MY 1st big screwup"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by Darkhaund on 2012-08-15
i "lost" all my unity environment... i was playing with ubuntu tweaks janitor..and i "cle3aned everyhing"

once i login... i have nothing but my wallpaper andi get this

 p, li { white-space: pre-wrap; }  No system tray detected on this system.
 Unable to start, exiting.


help... how can i fix this

---

### Post by mkstallings1 on 2012-08-15
Try this in a terminal.

sudo apt-get update 
sudo apt-get install --reinstall ubuntu-desktop 
sudo apt-get install unity

---

### Post by Darkhaund on 2012-08-15
let me try this and reboot brb 

i managed to login to "genome claisc" but i now miss and love unity

---

### Post by Darkhaund on 2012-08-15
nope.. did and and still nothing

---

### Post by Darkhaund on 2012-08-15
I apologize for bumping this, but I really need assistance on this matter

---

### Post by mick8985 on 2012-08-15
Don't trust any Janitor application, they are far more trouble then they are worth.

I am not at all familiar with Ubuntu-Tweak or what it's janitor function does, but it may uninstall packages that you may well actually need, I know Ubuntu used to ship with a janitor application which would do this, glad that's gone.

If you had proprietary nvidia drivers install perhaps it has uninstalled them?

you could always try

sudo dkpg-reconfigure unity

---

### Post by Darkhaund on 2012-08-15
Nope.. that did not work either.

i can only see my background but no unity side bar or top bar or anything... 

i would appreciate assistance.


all i did was "clean everything" with ubuntu tweak janitor

---

### Post by Bashing-om on 2012-08-15
Darkhaund;

  you might try this this option:
 we'll try to get the desktop back the quick and easy way:
Code:sudo apt-get purge ubuntu-desktop
This will get rid of any desktop packages currently installed AND the config files. This gives us a nice blank slate to re-install the desktop.
Code:sudo apt-get install ubuntu-desktop
This will install the desktop environment again. After that, reboot and (fingers crossed) you'll get a desktop again.

[INDENT]HTH <==BDQ
[/INDENT]

---

### Post by Darkhaund on 2012-08-15
Fingers crossed... let me try that... 

I really appreciate all the people that have taken time in helping me sort this out

---

### Post by HermanAB on 2012-08-16
Howdy,

Usually, you can easily fix a desktop issue like this by making a new user account, then moving your data over to the new account.

(Remember to fix /etc/sudoers before deleting the old account!)

---

### Post by Darkhaund on 2012-08-16
THANK YOU BASHING-OM it worked!!!!!
Thank yous o ver ymuch


Now... should I say away for ever from ubuntu tweaks janitor?

And what do you mean by

(Remember to fix /etc/sudoers before deleting the old account!) 	

i am a noob

---

### Post by Vaphell on 2012-08-16
he means: give your new user account admin powers because by default only original user account is. If you deleted the account before passing the torch, you would pretty much lock yourself out of administration of your machine.

---

### Post by Darkhaund on 2012-08-16
And how do i do that?
How do i give the new account admin powers?

Keep in mind that i am new to this

---

