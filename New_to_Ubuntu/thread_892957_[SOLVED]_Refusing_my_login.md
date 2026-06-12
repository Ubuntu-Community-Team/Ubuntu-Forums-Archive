---
title: "[SOLVED] Refusing my login"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Cuttysark on 2008-08-17
I've been running hardy heron on an old laptop for a few weeks now, and like it enough to change my desktop too. So that's what I did this evening. Everything went well, until the install finished and rebooted. When I was presented with the login screen, I put my details in and after putting my password in and hitting enter, it sits for a couple of seconds, the screen goes blank, then the log in screen reappears asking me for my details again.

Trust me, I'm not putting the wrong details and the case is correct, I always write this stuff down as I'm creating it, and double check before moving on. Plus, I would assume that if I was misspelling, or had the wrong case somewhere, the screen would tell me, it's not, and neither am I.

So can anyone tell me what I can try to correct this please?

---

### Post by loboc on 2008-08-17
> **Cuttysark said:**
> I've been running hardy heron on an old laptop for a few weeks now, and like it enough to change my desktop too. So that's what I did this evening. Everything went well, until the install finished and rebooted. When I was presented with the login screen, I put my details in and after putting my password in and hitting enter, it sits for a couple of seconds, the screen goes blank, then the log in screen reappears asking me for my details again.

Trust me, I'm not putting the wrong details and the case is correct, I always write this stuff down as I'm creating it, and double check before moving on. Plus, I would assume that if I was misspelling, or had the wrong case somewhere, the screen would tell me, it's not, and neither am I.

So can anyone tell me what I can try to correct this please?

hit CTL ALT F1 to get to a terminal 

login as root

issue 

passwd username

to reset the passwd for your default username

---

### Post by JillSwift on 2008-08-17
It sounds like you're getting logged in, but X is crashing, restarting and sending you back to GDM.

What desktop did you start with, and which did you just install?

---

### Post by MuH4hA on 2008-08-17
Maybe your system-partition is full... ?

(type *df* after hitting CTL ALT F1 to check)

---

### Post by arkhitekton on 2008-08-17
Hi Cuttysark,

[It looks like others have replied before I finished typing!  :-) ]

I'm not sure I can help recover the password but you might want to try this as an alternative tocheck if you have the correct user name and password details.

Press **<ctl><alt><F1>** at the same time and you should get a terminal session screen with a logon.  Enter your user name and then, when prompted, the password.  If you manage to log in then you know the user name and password are correct.  If not, then you have a problem.

Unfortunately if the user name and password are not being accepted your only option is likely to be a reinstall.  However wait to see if any other suggestions are coming from the community.

To end the terminal session type **exit**.  To get back to the gnome window manager session, type **<ctl><alt><F7>** at the same time.

Are you entering your user name rather than your full name.  When you install Ubuntu it asks for your full name, e.g. Fred Bloggs and then generates a username, e.g. fred, which you can accept or change.  The generated user name is all lower case.  If you enter the username with a capital letter, e.g. Fred it will not be accepted.

Sorry if the above is telling you what you know already.

Good luck.

Arkhitekton

---

### Post by Cuttysark on 2008-08-18
Trying Ctrl Alt F1 just freezes the keyboard and mouse, everything in fact. It would sit there all day if I let it. The only way I can move is to pull the power cord.

Thinking that the disk drive might be at fault, I found a really good tutorial on creating a bootable thumb drive, and did a fresh install from that. It went very smoothly. However, on being presented with the login screen, the exact same thing happened. Please believe me when I tell you I got the login and password correct. 

I clicked on the Options button at the bottom left hand corner and chose Select Session, and from the list presented, selected Failsafe Gnome, and finally got to the desktop, whereupon, I was presented with a list of updates which downloaded and installed just fine, but after rebooting, same problem.

I'm thinking maybe my hardware is at fault, although it ran XP with no problems before trying this install of Hardy. One thing I did note, was a message just after the Grub Loader text, which said "16.54634885 MP-BIOS Bug: 8254 Timer Not Connected To IO-APIC.

It's not a huge inconvenience to choose Failsafe Gnome each time but I'm thinking this is something like Windows safe mode and shouldn't be used for general use? I really want to solve this because I'm running Hardy on my laptop and loving it.

---

### Post by markbuntu on 2008-08-18
When you get to the login screen, click on the little icon on the bottom left and change session to gnome safe mode. See if that works. If it does:

You can go to System/Adminstration/System log and look at the logs to see where the problem is. Start with the messages log and the syslog. You can also look in the Xorg.0.log to see if there is a problem with the video driver.

---

### Post by Cuttysark on 2008-08-19
I did that very thing this morning, options, new session, failsafe gnome. That got me in okay. I was looking around to see what I could do and ended up installing the proprietory driver for the video card in this machine. After I rebooted, I could log in with no problem.

Thanks for the advice guys, now I just need to get busy setting it up the way I want it.

---

