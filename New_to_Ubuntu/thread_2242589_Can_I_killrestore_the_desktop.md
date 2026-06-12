---
title: "Can I kill/restore the desktop?"
date: 2014-09-02
forum: New to Ubuntu
---

### Post by kglading on 2014-09-02
I'm new to Ubuntu and used Unix long ago (but never was a guru or power user) and I'm working my way towards a home network where the ubuntu box would be a server with a router so only the server was connected (directly) to the web and my home network would be isolated.  Ideally the server would be a file server as well as a "firewall."  I'll have more questions later no doubt.  I have Samba providing access to several external drives and I use the Ubuntu desktop to simplify my life BUT can I turn it off and on from the terminal so when I don't need it I can let the server run without the overhead?  I'm running 14.04 and using the Flashback Metacity desktop.

---

### Post by deadflowr on 2014-09-02
Sure can.
run
```
sudo stop lightdm
```
to kill X, and
```
sudo start lightdm
```
to start X again.

See if that helps.

---

### Post by kglading on 2014-09-06
> **deadflowr said:**
> Sure can.
run
```
sudo stop lightdm
```
to kill X, and
```
sudo start lightdm
```
to start X again.

See if that helps.

Must be a blue moon.  That works.

Only thing is I had to hit F2 and login again to get a command line.

Thanks.;)

---

### Post by deadflowr on 2014-09-06
My bad, I forgot to mention you should login to a console session ctrl+alt+f2 and then run the command(s).
Killing it from an X terminal just leaves you with a blank monitor screen.

At least you figured that out.

Also, here's something if you want to set it to boot into a console, instead of a gui login
[http://askubuntu.com/questions/148717/how-do-i-boot-into-the-console-and-then-launch-the-ubuntu-desktop-from-it](http://askubuntu.com/questions/148717/how-do-i-boot-into-the-console-and-then-launch-the-ubuntu-desktop-from-it)

---

