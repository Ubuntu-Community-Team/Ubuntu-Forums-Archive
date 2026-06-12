---
title: "Problem with VNC"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Exuus on 2008-08-09
I was wondering if anyone could give me a hand figuring out whats wrong here:

After following these instructions

[http://altitude5.blogspot.com/2008/02/remote-desktop-in-ubuntu-in-9-easy.html](http://altitude5.blogspot.com/2008/02/remote-desktop-in-ubuntu-in-9-easy.html)

I managed to get VNC up and working using putty and tightvnc. At some point last night I was booted off of tightvnc and was unable to reconnect, since then I've tried reinstalling putty, tightvnc, ultravnc and even ubuntu itself. No matter what I've tried I manage to connect through putty just fine but when I go to connect using a vnc viewer it says "Connection closed" straight away.

I'm very new to using ubuntu so any help at all would be greatly appreciated!

---

### Post by jamesrfla on 2008-08-09
All you really need to do is go to system>preferences>remote desktop and enable it their.

---

### Post by Exuus on 2008-08-09
I've turned that on, but I've been trying to tunnel vnc through ssh as in that guide since I'll be accessing that machine from at work.

---

### Post by jame86 on 2008-08-09
I have found this recently too.  My quick 'n' dirty solution is to "sudo reboot" via the ssh tunnel.  And the vnc server then seams happy.

I am still trying to work out what causes this, but as the machine that is affected is not a server, rebooting for 30secs isn't to much worry!

Would be interested if anyone has any more info. :popcorn:

Damingo

---

### Post by Exuus on 2008-08-09
I've tried rebooting too, like I said, I've went as far as reinstalling ubuntu, but it still refuses to start working again. It's certainly an odd problem! :)

---

### Post by jame86 on 2008-08-09
Sorry I missed that bit.

In that case...

If it was a clean install of ubuntu, then it cant be anything with the install its self.  Unless you missed a step in the VNC-SSH install! (no offence).

Are you using a router / firewall-box / software-firewall that might need some extra configuration.  Does the box you are vnc-ing from have a firewall, and has it managed to blacklist the other pc's ip ???

Damingo  :confused:

---

