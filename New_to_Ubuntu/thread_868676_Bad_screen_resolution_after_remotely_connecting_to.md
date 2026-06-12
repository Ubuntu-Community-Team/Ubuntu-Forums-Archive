---
title: "Bad screen resolution after remotely connecting to gnome session"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by tjosan on 2008-07-24
I have a problem with the screen resolution: suddenly it won't let me use a decent screen resolution.

I have a brand new installation of Ubuntu. Worked fine, until I tried remotely connecting to the gnome session from another computer on my home network, via realvnc & windows. That worked well too. But the next time I turned on the computer, ubuntu seemed to have forgotten about the properties of my screen (a Dell Trinitron).
The login screen looks fine, but after I log in, the screen resolution was set to 800x600, which it thinks is the maximum according to the Systems->'screen resolution' menu entry. It says screen type 'unknown'.

In other words, the computer must know how to display 1600x1200 since that is what is used on the login screen( I believe), but then it insists that I as a logged in user cannot use more than 800x600.

As a comical (?) aside, I tried setting it to a lower resolution just to experiment: right now I can't even set it to 800x600 again because the ok button of tSystems->'screen resolution' is hidden under the bottom panel! :-)

-- Thomas

---

### Post by Hospadar on 2008-07-24
What video hardware/drivers are you using?

Ye olde solution to this problem is Ctrl-Alt-F1, log in, "sudo dpkg-reconfigure xserver-xorg" default through a ton of menu options until you get to resolution, choose the max resolution you want with spacebar, finish defaulting through the dialog, "sudo /etc/init.d/gdm restart" (restart your X server).

Depending on your video hardware and drivers there may or may not be a better way to do this.  I don't know why vnc would set your res so low.  This fix may solve the problem permanently (so you can login with vnc) but it may not, so give it a try.

---

### Post by tjosan on 2008-07-24
How do I see which hardware/drivers etc I'm using? Ie without opening up the box and stare at the chip, that is. It's a Dell box, anyway.
--Thomas

---

