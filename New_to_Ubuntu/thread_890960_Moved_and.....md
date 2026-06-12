---
title: "Moved and...."
date: 2008-08-15
forum: New to Ubuntu
---

### Post by gatordoc on 2008-08-15
Hi all.

I was connected to a university computer via specific ip numbers etc and have moved. I just plugged in my computer and was hoping to change stuff that I needed but here's the problem

Of course it cannot ypbind anything because its not connected. But what happens next is weird. My desktop stuff shows up (loads very slowly) and an error box comes in about 10 min later and none of my icons at the top of my screen (like the application buttons etc) never load in after even an hour of waiting (praying) they did.

thus I cannot open a terminal etc to even do anything. I can open the files on the desktop (albeit really slowly).

oh i'm running hardy heron

I have no idea what to do and I need to get this computer up and running asap!

thanks

---

### Post by finer recliner on 2008-08-15
switch to tty1 by pressing ctrl+alt+F1

log in.

type the command 'top' and see what is hogging all of your system's resources. if you know what the process is (like firefox-bin or something) and you know its safe to kill, take note of the PID in the first column. press 'q' to quit top, and then type 'kill *PID*' where *PID* is the PID of the process you want to kill.

switch back to your desktop (tty7) by pressing ctrl+alt+F7.

hope this helps.

---

### Post by phidia on 2008-08-15
You can drop to a shell from your laggy desktop press the Alt+Ctrl+F1 keys.
Type dmesg and use cat to get logfiles from /var/log.

Are you saying everything was fine before the move? If so check for unseated ram.

---

### Post by gatordoc on 2008-08-15
Yep everything was fine before the move. I will check the ram now (everythign boots up fine so it seems) I just doesnt finish loading everything into the gui????

I did ctr+alt+f1 and did top, nothing is hogging anything that I can see.

If this doesnt work i'm screwed! i need my programs to finish up some work!

argh

---

### Post by gatordoc on 2008-08-15
RAM, cables, ..etc. are all seated fine! Same problem.

I repeat that I cannot even open a terminal or see the icons in the applications/places/system..etc are usually located (and clock)

and everything is running very slowly still. I see the hardy heron background and a couple of things on my desktop, but everything else is unavailable, and the error messege window remains even after closing (like a windows ghost window)

frustrating

---

### Post by ByteJuggler on 2008-08-18
Try logging on via a console (ctrl-alt-f1) then adding a new user.  ("adduser newuser" etc)

Then try logging into your desktop with the new user.  Does that make any difference?

---

### Post by gatordoc on 2008-08-18
Sorry about that, continuing on this thread now: 

here was a new suggestion

Your .gnome .gnome2 etc would be present under /home/<your username>

To delete them, try this on a terminal

Quote:
figo@zion$ cd
figo@zion$ rm -rf .gnome .gnome2 .gconf .gnofd  

Leave the /etc folders alone 


------------------------

Ok I did this and 
1) never saw the files there
2) didnt seem to do the trick for me

Here is some new info

It keeps trying to ypbind even though I erased all of my ypbind settigns in my /etc files that I changed for my dedicated IP. However the start up always fails at ypbinding still (why is it still trying?)

---

### Post by finer recliner on 2008-08-18
you didnt see the files because they are hidden files (any file that starts with a dot is hidden)

you need to log out and log back in to see the effect of deleting those files. let us know if anything changes after that.

---

### Post by gatordoc on 2008-08-18
Thanks Recliner,

I am rebooting as of this email and it failed at ypbinding again.

for some reason the NIS server still thinks i'm at my old place and is trying to connect, this may be part of the problem as well but I dont see how this effects the GUI loading up!

It still hangs after the login screen ( I am logging in as root)

its taking forever to do anything and it fails to load up the upper and lower panels (where all the applications..etc are) So its the same as before exactly

---

### Post by finer recliner on 2008-08-18
your GUI problem and your network problem are probably seperate issues.

regarding your network issues, have you tried uninstalling ypbind/NIS?

if you installed NIS from the repository, then you just type:

```
sudo apt-get remove nis
```

again, restart the computer (in this case) to see if anything changes.

---

### Post by gatordoc on 2008-08-18
Ok I will try to uninstall NIS

I am not connected to the internet right now because I just moved and was trying to get the system running period, first.

It took a while, as it this process was slow in the failsafe terminal window. When performing it looked liked it finished but at the very end it said something about an unknown operator.

... ok so it does now finish loading without any fails, but I am still stuck at the login/GNOME screen.

The error window that has continuously popped up says tha tI should restart the Settings Daemon next time I log in?

Also I notice that the computer still thinks it is cd-whatever.domain.edu (what I called it when i was hard lined) Is there a way to change that? We also had NFS-mounted our systems (I had to install nfs-common) should i uninstall that?

i've looked at (in /etc) rc.local, yp.conf, host.conf, hosts, and passwd and got rid of all th estuff I added to make it work with my old network.

---

### Post by finer recliner on 2008-08-18
one thing at a time.

did you ever try making a new user as ByteJuggler suggested? create a new user, and try to log in as him. This should load up gnome with no problems.

---

### Post by gatordoc on 2008-08-18
I created a newuser and the problem after logging in persists.

... after logging in.. it hangs forever and then the heron backdrop comes in and the error window is all greyed out until it finally loads up, I click close (or not close it) and a minute later it goes away (or grey's out) and I cannot access anything in the toolbars as they disappear or grey out. some things on the desktop i can access, but that is about it. I can see my mouse curser no problem, and it doesnt trail or anything

:(

---

### Post by finer recliner on 2008-08-18
you should back up your data, because it's probably easier to do a fresh resinstall of ubuntu at this point.

sorry if that's not the answer you wanted :(

---

### Post by gatordoc on 2008-08-18
I figured this would be the case.

I cant figure out how to get all the stuff I want off my HD's..

:/

---

### Post by finer recliner on 2008-08-18
if you arent comfortable doing it from the command line, then i suggest booting from a linux live disk (like the ubuntu install disc), mount your local partition (if not done automatically), put in a USB thumb drive. drag and drop the files you want to backup onto the thumb drive, then do the reinstall.

---

