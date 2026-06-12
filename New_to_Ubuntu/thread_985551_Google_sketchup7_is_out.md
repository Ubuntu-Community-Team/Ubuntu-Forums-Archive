---
title: "Google sketchup7 is out"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Vyaas on 2008-11-17
Sketchup7 is out. And as usual, there's no linux version.
Has anybody gotten it to work on intrepid? And if so, how?

---

### Post by C.S.Cameron on 2008-11-17
I have only gotten it to work using Nvidia drivers, Black screen with ATI.
After installing with wine,
Go to /home/YOURNAME/wine/drive_c/windows/regedit.exe
expand HKEY_CURRENT_USER
expand software, google, sketchup, glconfig, display and click HW_OK
Change the value to 1.
In wine configuration add SketchUp to applications and set windows version to XP.
open SU and close the startup windows as quick as possible, may need a reboot.

---

### Post by Vyaas on 2008-11-18
I tried what you said. Didn't work. Keep getting a reportable error message.
Dangnabit!

---

### Post by C.S.Cameron on 2008-11-18
I'll try SU 7 today.
What video card are you using?

---

### Post by C.S.Cameron on 2008-11-18
SU 7, (free), seems to work ok in 8.10.
After doing what I mentioned above I rebooted.
Upon starting SU, I closed the initial help windows after selecting "do not show on startup", (have to work fast to get this done before Bug Splat).
Then went to Window, Preferences, OpenGL, then selected what was not default under Capabilities.
Good luck

---

### Post by dankegel on 2008-11-23
Sketchup 7 is working fine for me once I follow the tips in [http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)
but I'm no expert.  Can anybody who's having problems
report them to the wine appdb or bugzilla?
I'll try to get them fixed, if I can.
Thanks!

---

### Post by Sam3280 on 2008-11-29
Hi,
I have successfully installed Sketchup but I get this problem when I try to do anything
[IMG]http://linuxwarrnambool.googlepages.com/Screenshot-2.jpg[/IMG]
Anybody know if there is a fix for it?

---

### Post by damonVT on 2008-12-21
I have the same problem as Sam. Mine's Kubuntu 8.10, and I have an ATI Radeon Mobility 9600, using the open source Radeon drivers, which give me direct rendering, but slowly. So I'm trying to get ATI's driver going (a whole different issue of course) and hope that will help. 

Sam what's your configuration? And for that matter, what drivers are working?

Cheers!

---

