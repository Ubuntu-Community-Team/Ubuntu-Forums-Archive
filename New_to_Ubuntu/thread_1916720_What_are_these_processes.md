---
title: "What are these processes?"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by jpdeaton on 2012-01-28
I just did a clean install of 11.10, ran the updates, installed gnome shell as well as a couple programs.    running "sudo sysv-rc-conf" to edit the run levels these are the services I'm not sure if I can disable. Any idea what they are and if I can turn them off?

 cryptdisk$ 0,6 
cryptdisks 0,6 
grub-comm$ 2,3,4,5  
kerneloops 2,3,4,5
 killprocs 1,4,5 
ondemand 2,3,4,5 
pcmciauti$ s
 rc.local 2,3,4,5
 saned 2,3,4,5
 speech-di$ 2,3,4,5 
unmountroot 0,6
 unattende$ 2,3,4,5,0 
x11-common s 
sudo 2,3,4 --(default is "s" i read!!??)

 Also, sudo htop shows "Tasks: 98, 182 thr; 1 r" at the top... I dont know what it means but does 98 tasks not seem high? This is just a personal laptop, not a server or anything.

---

### Post by anewguy on 2012-01-28
Google is your friend with this.  Try a Google search with, as an example, 

ubuntu cryptdisks  (assuming you copied it right in your list)

Then move on to the next.

pcmcia are the utilities controlling your pcmcia slot.

saned is the sane deamon for scanning.

etc..

These things should be okay just to leave alone.

Dave ;)

---

### Post by Double.J on 2012-01-28
> **jpdeaton said:**
> 
 Also, sudo htop shows "Tasks: 98, 182 thr; 1 r" at the top... I dont know what it means but does 98 tasks not seem high? This is just a personal laptop, not a server or anything.

+1 to anewguy, nothing stands out as wrong here - my system's currently reading 116 in htop :). A lot of different programs go into a modern operating system.

If anything a server may well be running less tasks, as you wouldn't necessarily need to be using sudoers, X11 etc, just the basics to do the job as reliably and securely as possible :)

Hope it helps!

Edit: it's probably not a good idea to run htop with sudo just to check what's running ;)

---

