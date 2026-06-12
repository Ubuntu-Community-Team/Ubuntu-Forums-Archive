---
title: "using kdialog in a bash script"
date: 2005-08-28
forum: Programming Talk
---

### Post by PokerFacePenguin on 2005-08-28
Attention scripting gurus:

why would running the kdialog --msgbox command produce the following when run by a sudo su session ? and not when regular user?

> root@ltop:/home/joe # kdialog --msgbox "test"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdialog: cannot connect to X server :0.0 

it's gotta  be a simple thing....

im new to bash scripting so cut me some slack please :P

---

### Post by toojays on 2005-08-30
This is something to do with the X server access controls. The X server has a complicated scheme for figuring out whether a given user is allowed to write to a particular display. In this case, your X session will only allow the user which started it to write to the display.

I don't have a particularly great understanding of how this works, but I'd say the problem is definitely with your X setup and not with kdialog. Check the environment variables in the rootshell, particularly DISPLAY and XAUTHORITY. When I tried the command you said from a rootshell, it worked fine for me, but my XAUTHORITY variable pointed to my personal Xauthority file, not the Xauthority file for root. The man page Xauth(1x) might be a good starting point.

---

