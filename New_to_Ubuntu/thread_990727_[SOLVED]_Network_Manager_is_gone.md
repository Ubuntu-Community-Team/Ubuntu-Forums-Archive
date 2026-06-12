---
title: "[SOLVED] Network Manager is gone"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by k33bz on 2008-11-23
I recently fixed my problem with Pidgin not connecting to the server by running a command I had found in the forums (didnt work, also cant find the thread now) as well as upgrading my pidgin which had worked.

However here is the problem, after restarting my laptop again today, my network manager had disapeared. I went to add to panel and added the the notification applet, which controls the network admin, laptop battery state, and blue tooth connection. However adding the applet did not work. Only thing that appears from the applet is the blue tooth connection icon. Nothing else.

Has anyone else come across this problem, and has anybody fixed this?

---

### Post by adult swim on 2008-11-23
try running ```
nm-applet
``` from a terminal and see what it says

---

### Post by k33bz on 2008-11-23
Bare with me, I have to reboot my machine to go to the install, I am using my backtrack 3 live cd to get to the net.

anyway, nm-applet didnt read out any info, all it did was just hang there, and when I punch <cntrl>+z it stops it.

by the way the code i used that didnt work is:

sudo chmod -x /usr/sbin/NetworkManager

I hope that didnt screw things up

---

### Post by k33bz on 2008-11-23
FOUND THE SOLUTION, I WOULD PUT THE CODE THING IN, BUT SINCE I AM ON A LIVE CD, LITTLE BIT HARDER, FOUND THIS ON ANOTHER THREAD:



Eiríkr
March 23rd, 2008, 11:20 PM
I'm baffled why this thread is marked as SOLVED when there's no solution evident, so I thought I'd add one. ;)

When you ran chmod before, you removed (the minus sign) the execute permission on the /usr/sbin/NetworkManager program. To make it executable again, you need to do the reverse -- add (a plus sign) the execute permission, like so:
sudo chmod +x /usr/sbin/NetworkManager

Incidentally, what thread did you see this in, and who recommended you do this? This seems like a bad "mess up the noobie" prank, but I suppose the thread context might make it clear.

Let us know if you need help with anything else.

Cheers,

Eiríkr

---

### Post by adult swim on 2008-11-23
the command that you ran made network manager not executable.  my guess would be to make it executable with sudo chmod +x /usr/bin/NetworkManger  and then try to run nm-applet again

---

### Post by k33bz on 2008-11-23
ya, I saw the post some where else, I copied and posted here for others to see.  So now it is there, after a reboot of course. nm-applet still doesnt read out however it does give me another network manager in my panel. Thanks

---

### Post by hommydc2 on 2009-08-08
Im having a similar problem on  my eee901. Network Manager disappeared a while ago and  ive had to figure out new ways to get my computer to connect. When I run nm-applet I get:


** (nm-applet:6585): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:6585): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed



Does anyone have a clue whats going on?

---

