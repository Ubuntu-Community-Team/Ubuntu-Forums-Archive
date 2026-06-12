---
title: "rdesktop from xubuntu precise to win 7 - blank screen"
date: 2013-08-01
forum: New to Ubuntu
---

### Post by benchatt on 2013-08-01
I'm back to Xubuntu after a brief foray into Crunchbang, and I've found that my rdesktop no longer works. I try to log into my work computer (which is running win 7)  and I get a black screen with no login. This is the command I'm using: 

[FONT=System]rdesktop -u username -d DOMAIN -r sound:local:alsa -x b -g 1280x800 x.x.x.x[/FONT]

VNC works just fine. I had this exact same setup a few months ago and it worked fine. Xubuntu 12.04 Precise (Raring had some bugs I couldn't deal with, hence the adventures in Crunchbang.)

---

### Post by TheFu on 2013-08-01
I'm not on 13.xx - still 12.04 here, but this works for me.
$ rdesktop -u $USER -g $RES $WIN-HOSTNAME:3389

It has been a few years since I set this up, but I thought there was something on the Windows7 side to force legacy RDP authentication support for non-NLA clients - or it didn't work.

I hope this is helpful, but it probably isn't.

---

### Post by benchatt on 2013-08-01
Thanks for responding, at least. Sorry, that didn't do anything. I don't know if this helps anyone, but I can use Windows RDC from my Vista machine and it works to connect to the Win 7 machine.

---

### Post by TheFu on 2013-08-01
Vista is an NLA client, so that should work. On the Win7 machine, did you disable NLA clients and enable "legacy RDP" support?

---

