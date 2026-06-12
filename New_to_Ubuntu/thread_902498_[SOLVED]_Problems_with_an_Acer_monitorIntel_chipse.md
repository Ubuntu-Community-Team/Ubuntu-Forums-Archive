---
title: "[SOLVED] Problems with an Acer monitor/Intel chipset"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by vckeating on 2008-08-27
Hey all,

I've got and Acer X193W monitor running on an Intel 82810E graphics card - it's an old HP Pavilion machine.  

My problem is that, in an attempt to get fix a problem I encountered using the highest resolution, I broke everything (as happens from time to time).  I used to have it set up using a generic monitor and some type of 'experimental' intel driver - I can't remember the name of this right now.  But it was not displaying properly when I went to 1440x900; everything was squished in the centre.

So in my attempts to fix it, I changed the monitor to the one that I have and changed the 'experimental' intel driver to whatever the 'default' one was, I think i710.  However, now I just get garbage when the logon screen is supposed to come up.  After reading some other posts I've done a safe boot and changed the xorg.conf driver from the i710 to vesa, but I still have the same problem of getting garbage once I get to the logon screen.

Does anyone out there have any ideas as to what I can change in order to get things back to normal?

Thanks!

---

### Post by vckeating on 2008-08-27
Oh, it's all good.  Just used sudo dpkg-reconfigure -phigh xserver-xorg and everything is working again.

---

