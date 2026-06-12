---
title: "howto pipe command to gdm from console"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by usererror on 2008-05-27
I am logged into my ubuntu box.

I press ALT + F6 for a terminal window.

I want to run an app (say gedit) and sent it to the ALT + F7 window...how do I do that?

---

### Post by Joeb454 on 2008-05-27
Why would you want to do that? You could just open Gedit from the Applications > Accessories > Text Editor

And you can also open a terminal from the same menu :)

---

### Post by beren.olvar on 2008-05-27
you can do that by using the gconf-editor tool:

in a terminal run
$gconf-editor

there you go to apps>metacity>global_keybindings
select the run_command_1 for example and put <Alt>F7

then go to keybinding_commands and where it says command_1 put gedit

that way you can customize your bindings to run some app...

hope it helps!

cheers

...................nvm 
didnt understood wat you wanted.

i think you can do something like 
$DISPLAY=:1 gedit

hope this time helps

Edit #2
use 
DISPLAY=:0 gedit

before i thoght you had 2 VT running X

cheers

---

### Post by wootah on 2008-05-27
If I read this correctly, you are wanting to start a program on a different display (vt - virtual terminal, what X runs on) ?

---

### Post by usererror on 2008-05-27
> **wootah said:**
> If I read this correctly, you are wanting to start a program on a different display (vt - virtual terminal, what X runs on) ?

Yes that is correct.

I have a linux Kiosk that I built today.  The user that is auto logged in with GDM is NOT in the sudoer's list.

When I need to do something with the gui (because I don't know how via the terminal)

I hit ALT + F6 for a VT and then do what I need there, but again sometimes I can't do everything via command line because I don't know how so I want to run something and pipe it to VT-7 as a sudoer.

in VT7 there is NO menu, only a desktop icon for Firefox.  It is completely locked down.

---

### Post by wootah on 2008-05-28
> **usererror said:**
> Yes that is correct.

I have a linux Kiosk that I built today.  The user that is auto logged in with GDM is NOT in the sudoer's list.

When I need to do something with the gui (because I don't know how via the terminal)

I hit ALT + F6 for a VT and then do what I need there, but again sometimes I can't do everything via command line because I don't know how so I want to run something and pipe it to VT-7 as a sudoer.

in VT7 there is NO menu, only a desktop icon for Firefox.  It is completely locked down.

Hmmm... I know what you want, unfortunately I have no idea how to do it. Let this serve as a bump :)

---

### Post by The Cog on 2008-05-28
This may not be exactly what you are looking for, but on a tty terminal such as you get with ctl-alt-F6 you can log in and then use the command:
```
startx -- :1
```
which launches a full GUI for that user. Log out when you are done and the GUI goes away. I just tried it on Hardy and it returned me to the first login GUI rather than the tty, so I had to use ctl-alt-F6 again, then logout, then ctl-alt-F7 back to the original GUI.

---

