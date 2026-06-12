---
title: "blank screen when updating to 8.04"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Jalfro on 2008-10-13
Hi,

I'm pretty new to this, so when the readme that came with my new wireless usb said that hardy would run it out of the box, I thought yes!  I'd had the upgrade 'offer' in update manager for some time so I clicked on it.  Everything seemed to be going smoothly, but no real indication of how long this was going to take, so I went to bed and left it running.  This morning the screen is blank and I can't get any response, though the box is still running. So...

Is it safe to turn it off?

Is there anything I can do instead?

---

### Post by ibizatunes on 2008-10-13
Did you backup your data first?
Have you download a copy of 8.04 cd for recovery yet? 
Do you have space on a harddrove to back your data upto?
I think you will have to turn it off and see what happens...... Fingers crossed 

Maybe someone else has some other ideas!
Sorry!

---

### Post by Orange_and_Green on 2008-10-13
Maybe it failed hybernating. If moving the mouse, hitting a bunch of random keys and pressing the power switch doesn't work, I guess you don't have any other option anyway...

Tell us if you can successfully "hard-restart" or if you need more help. Good luck:KS

P.S don't worry about data, even if it's not backed up, you can always access it by booting into a live CD even in the worst-case scenario...

---

### Post by rybaxs on 2008-10-13
just restart and install again. no problem with that. I've encountered like that before on my laptop. When I install Ubuntu at the evening then when I woke up everything was on black screen. Then I reinstall then everything works nicely. All files are safe, just create partition never format the entire disk.

---

### Post by Orange_and_Green on 2008-10-13
> **rybaxs said:**
> just restart and install again.[...]All files are safe, just create partition never format the entire disk.

rybaxs is correct and that's what I'd suggest too if the PC fails booting up properly, but **only if you have your /home mounted on a separate partition. If you don't, be sure to back it up first!!** You will also have to reinstall all your packages unless you back them up (may I suggest [this thread of mine]("http://ubuntuforums.org/showthread.php?t=915712") if you need a backup of your installed packages)

---

### Post by Jalfro on 2008-10-14
So I shut down, but now can't reboot into 8.04.  Well once I managed to log in, but no mouse.  Since then, I haven't been able to get past the login screen.  

I tried booting in safe mode and got several warnings: 
'could not resolve' e.g. gb.archive.ubuntu.com'
                         security.ubuntu.com'
'failed to fetch'        ditto
etc

tried to run apt-get update as advised, but no joy

I have an 8.04 disc I got with Linux Format Magazine, but this won't run either.

My old 7.10 disc boots, so I'm on the verge of reinstalling Gutsy, unless anyone has a better suggestion?

---

### Post by SpenceMakesSense on 2008-10-14
and for future reference life is mkuch easier if you make install ubuntu with /home being a spereate partition. Because then you just reistall the programs you had installed previously and everything is back to normal because al your settings are saved. Icluding theme and wallpaper ect.
And if your not too worried about losing data then try to do a a clean install of 7.10 and rerunning the upgrade without installing anything(like programs). That worked for me when it was firsted released

---

### Post by rybaxs on 2008-10-14
Would you like to upgrade? try this one..

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)


In my experience.. my previous OS is Gutsy Gibbon, then I've installed the Ubuntu Server disk downloaded from Ubuntu.com. I just curious about Ubuntu Server disk, It takes more than 2 hours to install, I found out that the Ubuntu Server disk is just a Ubuntu 8.04 Hardy Heron. I just wonder if the file I've downloaded is a server or desktop, I think that the new Ubuntu server have GUI and lots of features or etc. but its just like a terminal command like Ctrl+Alt+F1 like the other previous Ubuntu server.

Ubuntu 8.04 installation process will process on the desktop of 7.10. 
We only have 2 Ubuntu CD's in my company got it from OpenSource Conference, Im jealous with the 8.04 because I only have 7.10 CD burned.
It's good to have a printed Ubuntu CD.. I want them!.. but i dont have.. i only have white CD with a marker Ubuntu 7.10.. hahaha selfpity lol. :lolflag:

---

