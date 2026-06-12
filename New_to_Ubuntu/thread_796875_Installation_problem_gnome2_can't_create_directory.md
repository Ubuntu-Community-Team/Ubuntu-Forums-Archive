---
title: "Installation problem gnome2 can't create directory"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-05-16
I did a clean install on HH on a 320 gig drive today. Immediately after that, I created a separate /home partition. Once that was done, I rebooted and got:

A triangle with a yellow exclamation point followed by:
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by others.

With some help, in Recovery Mode, I did:

chmod 700 /home/mark

but when I 

chmod 644 /home/mark/.dmrc

I received: No such file or directory.

Dismissing the first error message, brought this one next:

Your session lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix the problem.

View details:

/etc/gdm/Xsession: Beginning session setup

can't create dir /home/mark/Desktop
can't create dir /home/mark/Templates
can't create dir /home/mark/Public
can't create dir /home/mark/Documents
can't create dir /home/mark/Music
can't create dir /home/mark/Pictures
can't create dir /home/mark/Videos

setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/Xinit/xinput.d/all-ALL linked to /etc/X11/Xinit/xinput.d/default

(seahorse-agent: 5411) Libgnomevfs-WARNING**: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory `/home/mark/.gnome2/": Permission denied

I would prefer to re-install Ubuntu HH, but I want to know if the problem is with the hard drive, the install of Ubuntu or making a separate home. Once I downloaded HH, I ran the integrity check and it was clean.

---

