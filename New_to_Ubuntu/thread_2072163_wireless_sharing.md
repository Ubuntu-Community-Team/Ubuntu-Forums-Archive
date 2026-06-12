---
title: "wireless sharing"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by deezdrama on 2012-10-17
Im ready to try ubuntu. Only thing im worried about  is how to setup my wireless sharing network if im running ubuntu.

Im good friends with my neighbor and he has given me his wifi network passphrase and allows me access to it.

Im running windows7 pro on a desktop and 2 laptops.
On my desktop i have an alfa usb wifi antenna that connects to neighbors  wifi, i then run an ethernet cord on this machine to a linksys  wrt54gl (running tomato firmware) which rebroadcasts the signal through  my home with my own encryption and password.

Im worried about how much of a pain this setup will be to mimic on a new  OS I know nothing about. I guess I could live without the  rebroadcasting router, but really do need it for my phones while at home  because I get crap service on them.

Any insight , advice, or tutorial links would be greatly appreciated.

---

### Post by Tralce on 2012-10-17
Doesn't Tomato allow you to configure the router as a repeater or a client-bridge? That's how I'd do it. If tomato doesn't support it, look into DD-WRT.

---

### Post by grahammechanical on 2012-10-17
You should download a copy of Ubuntu and burn it to a DVD and try it in Live mode.

You will find an icon for the network Manager to the right of the top panel. Click on it and it should show you a list of nearby wireless access points. If you see anything in that list that you recognise as being the Linksys wrt54gl then all you need to do is to try to connect to it and authenticate using the passphrase/password/key for the Linksys.

If you are unable to connect when trying Ubuntu from a live DVD then you will need to do further research.

Regards.

---

