---
title: "Deli Linux on Fujitsu Lifebook"
date: 2008-12-10
forum: Other OS Talk
---

### Post by spoons34 on 2008-12-10
Well I started out to do my first install of Ubuntu on a 4 year old desktop packed away in a box for the last 2 years, found a much older Fujitsu lifebook 790Tx with P266, 96MB and 4GB drive and I kind of got sidetracked.  Tried Ubuntu and it wouldn't go so read up a bit and tried again with DeLi.

It installed OK, even got the GUI running but have a couple of problems:

USB port is not recognised, lsusb returns nothing, also nothing available on Fujitsu site, not surprised really as this was a Windoze 95 machine so must be over 10 years old.  Any ideas?

Keyboard is not quite right, I chose UK but Shift/3 give # instead of £, also the | and a few others are wrong, is there a better keyboard to choose?

I should also mention that I have 2 identical Lifebooks so I am able to cross check and eliminate hardware problems.

Hope someone can help resurrect these old machines before I get back to my original task of installing Ubuntu on the desktop machine.

(edit) not able to reply to this post so editing it (17 Feb 2009) - never did get any form of linux working on these old Fujitsu so I reinstalled Windows 95 and got rid of them.



\Paul

---

### Post by kerry_s on 2008-12-10
have you tried a custom debian install?
net installer:
[http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso)

at package selection uncheck the desktop, that will give you a base install, cli system.

log in as root:
**apt-get install xorg lxde**
(deli uses icewm, i think you should try lxde instead, but if you prefer you can use what ever you like)
press **ctrl+alt+delete** to reboot

---

### Post by zmjjmz on 2008-12-10
It's entirely possible that USB support is lacking in DeLi, but I wouldn't know.
I personally would recommend trying Damn Small Linux.

---

