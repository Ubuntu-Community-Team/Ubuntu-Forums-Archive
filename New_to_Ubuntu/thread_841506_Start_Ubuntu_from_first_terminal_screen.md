---
title: "Start Ubuntu from first terminal screen"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by twibbz89 on 2008-06-26
Hello. I was givin a laptop from family of a friend who passed away. I've used Linux before, but i'm not too familiar with Ubuntu. I've changed the password on the laptop. Now when I boot the pc, I get a screen that says Kubuntu. After it loads, Im stuck at a black terminal screen that asks for the username and pw. I enter the info, press enter and more info comes up and the last two lines are:     

You have new mail.
twibbz@twibbz-laptop:~$

What am I supposed to continue start up so that I can access files on the pc?? Thanks in advance

---

### Post by conscious on 2008-06-26
I can think of several options (not sure which, if any, will work).
- press Ctrl-Alt-F7
- enter "startkde"
- enter "/etc/init.d/kdm start"
- enter "startx"

---

### Post by twibbz89 on 2008-07-13
Hello. I really do thank you for your reply. The last option started the laptop right up. I highly appreciate you. I CAN'T SAY IT ENOUGH.  THANK YOU!!! :) :KS

---

### Post by nowshining on 2008-07-13
i think in hardy they changed it to alt+f8 :)

as for /etc/init.d/kdm start

u need to add a sudo, this starts up the kdm login manager. :)

ur pw won't show as u type.

as for accessing files, u can thru the command line, etc.. linux isn't dependent on the GUI like windows is.

---

