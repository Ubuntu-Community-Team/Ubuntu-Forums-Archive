---
title: "Remote access to home computer."
date: 2008-07-16
forum: New to Ubuntu
---

### Post by jerrynewt on 2008-07-16
Just wondering what would be the best setup for accessing my home computers from my laptop out here on the road. I want to be able to access both of them (not at the same time) and change settings, download updates and such. Laptop is Toshiba Satellite Pro with 7.10 and 8.04 dual boot using Sony Ericsson GC89 broadband card for internet access. Home comps are both 8.04 with cable internet connection, 250 and 350 gig hd, 1 and 2 gig ram. Both home comps are networked (hard wired via router) and share a network printer. Any suggestions or tips are appreciated. Thanks!

---

### Post by phidia on 2008-07-16
[This page]("https://help.ubuntu.com/community/InternetAndNetworking#Remote%20Access") from the community documents may help.

---

### Post by Inxsible on 2008-07-16
1) SSH - terminal access
 2) VNC
3) VNC over SSH - more secure
4) NX Server

---

### Post by jimv on 2008-07-16
VNC would probably work.  All you would need to do is:

Forward ports through your router to 5900 on each machine.  It doesn't matter what the external ports are...just make sure they point to 5900 on each of the machines.  So you could forward 11111 to one machine, and 22222 to the other machine.

Make sure that both machines are logged in...Ubuntu's remote desktop won't work unless you're logged it.  Unless you run it as a daemon, which I don't know how to do.

If you just want to get in quick without a GUI, SSH is the way to go.  In that case, forward ports through the router to 22 on each machine.  You'll need to install openssh-server on each machine as well.

---

### Post by kpatz on 2008-07-16
> **jimv said:**
> VNC would probably work.  All you would need to do is...

If you just want to get in quick without a GUI, SSH is the way to go.If you want to use VNC, it's better (much more secure) to use a SSH tunnel.  All your communications are encrypted, only port 22 needs to be open to the outside world, and no one can do anything without authentication first.

---

