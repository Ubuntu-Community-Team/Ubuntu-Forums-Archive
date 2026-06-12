---
title: "remote access"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Malice007 on 2008-07-06
I just got my mother a computer and installed Ubuntu on it for her and I was wondering if there was anything I could use just like Pc Anywhere?
I would like to update her computer and fix any problems she may have at my house using my Ubuntu machine being that she lives so far away.. Also I would need a good tutorial for myself to know how to install it and use it.. thanks in advance. also it has to be easy for her to use also...

---

### Post by lisati on 2008-07-06
There's gnome-rdp and a couple of others. I use gnome-rdp on my ubuntu box, together with a VNC server on my XP machine, to monitor and control my XP machine from my Ubuntu machine.

Ubuntu also has a remote login option.

EDIT: To enable the remote login, go to the System->Administration->login menu, click on the Remote tab., and choose "same as local". There will be other steps you'll need to take to connect thru internet, but I'm noit sure of the details

---

### Post by edm1 on 2008-07-06
it kind of depends exactly what you're after. The best and most secure option would be to connect using ssh but this would give you command line access only. For remote graphical login you have the option of using XDMCP which can be configured under System>Admin>Login window, or install a VNC server from the repositories. There will be a few howto's around the forum. Of course once set up you will have to configure your router so that your mum's pc has a static lan IP and have whichever necessary ports forwarded to it.

---

