---
title: "Problems with TightVNC server on Ubuntu-mate 16.04 on Raspberry Pi 3 from Mac client"
date: 2016-10-21
forum: New to Ubuntu
---

### Post by Hunter5117 on 2016-10-21
Ubuntu sort of noob here, been years since I used Linux very much.

Long term I am attempting to set up an INDI server on the Raspberry Pi 3 to control my telescope.

Trying to get started just get familiar again with remote control of a headless Linux machine aka the Raspberry Pi with Ubuntu-mate.

Everything was going well, I installed the Ubuntu-mate distro, was able to connect via ssh, installed TightVNCserver, and was able to connect my Macbook via vnc using the Mac screen share client.

This was all via a hardwire ethernet connection.

I then attempted to switch over to wifi.

Activated my home network wifi on the Rpi3 and killed both ssh and vnc connections.

Plugged back in with keyboard etc and turned off wifi went back to ethernet.

The wifi was working because before I turned it off I could connect to internet etc over wifi only.

Now, ever since then, vnc no longer works in any way.

SSH is fine via ethernet but nothing seems to bring vnc back including purging out the server and reinstalling.

Error I get from my mac vnc client is "Connection failed".

Thanks if anyone has any suggestions.

---

### Post by colmax on 2016-10-21
Is your telescope usb or motors and stuff
So good to hear from someone using raspberry pi
Seems ethernet is the go for now
Maybe erase vnc & re-install with everything plugged in & turned on
ssh is just a secure socket layer methinks
Cheers

---

### Post by steeldriver on 2016-10-21
You will need to do some diagnostics

 - is the vncserver running?
 - is it listening on the expected interface and port?
 - is the port open (not firewalled)?
 - what's in the vnc logs (usually in ~/.vnc/)

---

