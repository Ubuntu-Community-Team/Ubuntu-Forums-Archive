---
title: "[SOLVED] Slow startup HH 8.04"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by ThomasWM on 2008-10-25
My machine is a dedicated 8.04 Ubuntu. My wireless router is wired to my XP machine, but I work wirelessly to my linux.   I am networked to the XP machine.

Until recently bootup was fast.

Recently, after inputting user and password, the system pauses for a couple of minutes with a paler panel in the top LH part of the screen.
If I leave it, it eventually displays a message in the panel:-
[I][U]
[I]""There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will try to restart the Settings Daemon next time you log in.""[/U][/I]


If I reset the machine as soon as I see that it is going to pause, it starts up normally after user and password.

I'm fairly new to ubuntu, so bear with me if this is a simple problem!

---

### Post by ibuclaw on 2008-10-25
[Dozens of other people have experienced this]("http://ubuntuforums.org/showthread.php?t=577946"), someone has found a fix though, and [put it up in his blog.]("http://arunpc.com/2008/06/01/ubuntu-there-was-an-error-starting-the-gnome-settings-daemon/")

Tell us how it goes.

Regards
Iain

---

### Post by ThomasWM on 2008-10-25
Thanks, Tinivole.

I'll give it a go, and get back to you.

---

### Post by ThomasWM on 2008-10-25
Update............

I tried the procedure by Guille (No. 3) in the blog you recommended and it seems to work.
I'll try it out over a few days to be sure it's solved the problem.

Many thanks for the suggestion...................Tom.

---

### Post by ThomasWM on 2008-10-26
Further update..................

Bootup now seems normal.

The problem was apparently as the No.3 message from Guille in the blog,  i.e.

system-administration-network-hostname

having no similar name in

system-administration-network-hosts

---

