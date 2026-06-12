---
title: "Changed Login Screen Now cannot boot"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by gentlemanmasher on 2008-08-15
I changed my login screen to a different one, which I've done a thousand times, and now I can boot to right before where my login screen is supposed to come up and it just hangs.  The circle keeps moving like it's trying to load the login screen but it goes no further. 

How can I get my login to skip my login screen so I can just go back in anch change it back again?  

can I run somthing from the command line to skip logging in so I can fix this?

---

### Post by DGortze380 on 2008-08-15
> **gentlemanmasher said:**
> I changed my login screen to a different one, which I've done a thousand times, and now I can boot to right before where my login screen is supposed to come up and it just hangs.  The circle keeps moving like it's trying to load the login screen but it goes no further. 

How can I get my login to skip my login screen so I can just go back in anch change it back again?  

can I run somthing from the command line to skip logging in so I can fix this?

Try booting the recovery kernel and change it back.

---

### Post by gentlemanmasher on 2008-08-15
I did try recovery and still a no go.

---

### Post by tahina on 2008-08-15
Can you get to terminal by pressing ctrl-alt-F1 ?

If so, logging in there might let you get into the graphical system, past gdm (the login manager) with the command "startx", or maybe you could remove and reinstall gdm from the terminal...

edit: As was pointed out below, the X server would be running all ready and that gdm should first be stopped with the command " sudo /etc/init.d/gdm stop " Then the startx command should work.

---

### Post by gentlemanmasher on 2008-08-15
How would I remove and reinstall GDM?  I am going to try to use the startx command and see if that works.

---

### Post by gentlemanmasher on 2008-08-15
I tried startx and it says that the server is alrady active for my display.

---

### Post by gentlemanmasher on 2008-08-15
> **tahina said:**
> Can you get to terminal by pressing ctrl-alt-F1 ?

If so, logging in there might let you get into the graphical system, past gdm (the login manager) with the command "startx", or maybe you could remove and reinstall gdm from the terminal...


It says the server is already active for this display.

---

### Post by Gannon8 on 2008-08-15
Type:
```
sudo /etc/init.d/gdm stop
```
After getting in the console. Then type startx

---

### Post by tahina on 2008-08-15
the command "sudo apt-get purge gdm" would remove it. That would also say you'd be removing other packages, among them ubuntu-desktop, which is a meta package (= no applications in itself, just a collection of packages).

"sudo apt-get install ubuntu-desktop" would then reinstall the removed packages.

At least I think this is how it would work... I'll give it a try myself first. :)

Yes... I tried it and it removed gdm, fast-user-switch-applet and ubuntu-desktop. Then, when I told it to install ubuntu-desktop, it installed all those back again. Of course, I don't know if it would solve your problem, but maybe it's worth a try if the startx way doesn't work.

---

### Post by gentlemanmasher on 2008-08-15
> **tahina said:**
> the command "sudo apt-get purge gdm" would remove it. That would also say you'd be removing other packages, among them ubuntu-desktop, which is a meta package (= no applications in itself, just a collection of packages).

"sudo apt-get install ubuntu-desktop" would then reinstall the removed packages.

At least I think this is how it would work... I'll give it a try myself first. :)

Yes... I tried it and it removed gdm, fast-user-switch-applet and ubuntu-desktop. Then, when I told it to install ubuntu-desktop, it installed all those back again. Of course, I don't know if it would solve your problem, but maybe it's worth a try if the startx way doesn't work.

well I'm into the desktop but now it appears my nvidia drivers won't work and I am to able to launch system administratio login window.
I receive the error failt to run /usr/sbi/gdmsetu as user root.  Unable to copy the users' xauthorization file.

So now I cannot get the resolution back to normal or use some of my menu otions.

---

### Post by gentlemanmasher on 2008-08-15
I ran envy then reconfigured GDM and all is well.  Thanks for your help.

---

### Post by BewareOfDog on 2008-12-27
Thanks, this helped me out. I too could not boot up due to a changed login screen, but removing and then sudo apt-get install ubuntu desktop did the trick.

---

