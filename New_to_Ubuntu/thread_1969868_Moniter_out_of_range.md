---
title: "Moniter out of range"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by robbietea on 2012-04-30
I installed ubuntu 12.04 clean, when I chose ubuntu from the grub my moniter goes blank and says "out of range" but I can hear ubuntu starting up

I can get into recovery mode and terminal, any ideas what to do?

---

### Post by jtarin on 2012-04-30
If it's Grub related you can try this [fix.]("http://ubuntuguide.net/monitor-signal-out-of-range-problem-in-ubuntu-12-04-precise-fresh-installation")

---

### Post by pqwoerituytrueiwoq on 2012-04-30
from root console
Xorg -configure
mv ./xorg.conf /etc/X11/
nano /etc/X11/xorg.conf
look for a part with screen resolution in it and make the appropriate changes and save it then reboot

---

### Post by robbietea on 2012-05-01
**"Re: Moniter out of range** 			
 			 			 		   		 		 		If it's Grub related you can try this [fix.]("http://ubuntuguide.net/monitor-signal-out-of-range-problem-in-ubuntu-12-04-precise-fresh-installation")"

I did step 1 and 2 but how can I do step 3 if I cant get into the ubuntu gui?

"from root console
Xorg -configure
mv ./xorg.conf /etc/X11/
nano /etc/X11/xorg.conf
look for a part with screen resolution in it and make the appropriate changes and save it then reboot 	"

After Xorg -configure I get 

"Server is already active for display 0
if this server is no longer running remve /tmp/.X0-lock
and start again

please consult X.org foundation for support wiki.x.org for help"

and after
mv ./xorg.conf /etc/X11/

"I get file ./xorg.conf cannot be read"

Any further help would be appreciated
****

****

---

