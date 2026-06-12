---
title: "Evoltion removal ?"
date: 2005-01-21
forum: Repositories &amp; Backports
---

### Post by ThePainter on 2005-01-21
Hi,
Basically I didnt like evolution so Ive installed Thunderbird.
I then went to uninstall evolution and it prompted me that it was going to uninstall Ubuntu Desktop as well ?
What does it mean ?
Will my os become unusible ?

---

### Post by Quest-Master on 2005-01-21
Nope, I uninstalled both packages and my Ubuntu works perfectly fine.

---

### Post by ThePainter on 2005-01-22
Hi,
So why do you think it says it is going to remove the ubuntu desktop ?
I also tried to remove totem (cos it wont play avi,s but VLC does) and it gave the same   prompt ?

---

### Post by Quest-Master on 2005-01-22
It's just a metapackage of programs that came installed with your desktop. You don't need it at all. Just think of it as a placeholder you no longer need.

---

### Post by ThePainter on 2005-01-23
Hi,
OK last night I tried to uninstall Evolution.
I got the prompt saying that it was also going to remove Ubuntu Desktop.
I clicked Ok and let it go.
Everything went OK until I rebooted a while later.
Yes youve guest it, my ubuntu desktop had gone.
I logged in and got my wallpaper but no task or launch bar.
Luckily I managed to open the terminal from a right click menu and fiddled about until I got the file browser open and got into the Applications launch folder and opened synaptic and reinstalled ubuntu desktop and Im up and running again.
I think these programs are like IE in XP they are part of the system and cant be removed without losing the whole package.
Im probably wrong but I think Ill just remove the icons and pretend they arent there  :D

---

### Post by RU63 on 2005-01-24
This happened to me awhile back.. The way i solved this was reinstall gnome (not being able to minamize windows is anoying): 

sudo apt-get install gnome

Just remove the evolution mail... not evolution.. i jsut removed it from the panel...

It would be nice if someone told us why we can't remove Evolution without losing the desktop.

PEace,

---

### Post by digitalpure on 2005-01-24
this has been talked about in a few other threads, and I am not a expert by any means, but my understanding is that Evolution is part of Gnome and not Ubuntu.... They have dummy packages that link to the ubuntu-desktop.

You can fully uninstall the evolution packages and ubuntu desktop, and then just readd the launch bars, and tray notification area sections.

I hope this helps, otherwise I woudl search for evolution removal on the forums.

---

