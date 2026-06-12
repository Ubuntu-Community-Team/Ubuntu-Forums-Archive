---
title: "black screen after log -switching gui (KDE to UNITY)"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by donsedin on 2013-01-03
I had dualboot kubuntu/win7, and it was working fine until i decided to switch back to unity.I did a research and used this to do that [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu).

Now when i did reboot and login screen came up, entered usn/pass, than hit login, and i got black screen. 
So i did terminal and got this:

Ubuntu 12.10 x-homePC tty1
x-homePC login: [50.968110] ata3.00:exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[50.968164] ata3.00: failed command: IDENTIFY PACKET DEVICE
[50.968214] ats3.00: cmd a1/00:01:00... tag 0 pio 512 in
[50.968214]          res 50/00:03:00... Emask 0x4 (timeout)
[50.968276] ata3.00 status: {DRY} 

I dont know how to read this (still noob at this), but someone of u could, so can U help me.
I will mention that i have normal login screen, taskbar and rest.

specs:
amd 1055t
asus m4a88t
nvidia 450 GTS
6 Gb DDR3

EDIT:

I still have these error's when i login, but i found out there was somekind of bug in GUI.I installed gnome 3 and i menage to log in, now can anybody help me with errors.
SOLUTION

The bug was with nvida drivers, so go back to open source and it worked. I don have any more error like this one up, or compiz crashes.

---

