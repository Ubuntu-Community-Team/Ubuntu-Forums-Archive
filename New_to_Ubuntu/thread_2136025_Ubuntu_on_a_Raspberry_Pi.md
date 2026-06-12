---
title: "Ubuntu on a Raspberry Pi"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by Denis BJ on 2013-04-16
Hi all,
I'm in the process of developing my Raspberry Pi.

Has anyone out there tried to load Ubuntu and how did it go?

I'm hoping eventually to have a small, hand-held, Powerpoint player using perhaps Kingsoft Powerpoint and the HDMI output.

Silly idea??

---

### Post by Paqman on 2013-04-16
There's a distro for the RPi called Raspbian which is Debian, same as Ubuntu. You'd probably feel very familiar with it.

---

### Post by mastablasta on 2013-04-16
Ubuntu doesn't support it's processor. Use Raspbian instead. it's not that much different to ubutnu. Afterall they are both based on Debian.

---

### Post by Diametric on 2013-04-22
Ubuntu does support the ARM architecture, just not the one raspberry pi uses.  Check this video...pretty cool: [http://www.youtube.com/watch?v=6DWnwMZxIW0](http://www.youtube.com/watch?v=6DWnwMZxIW0)

---

### Post by zero2xiii on 2013-04-23
> **Diametric said:**
> Ubuntu does support the ARM architecture, just not the one raspberry pi uses.  Check this video...pretty cool: [http://www.youtube.com/watch?v=6DWnwMZxIW0](http://www.youtube.com/watch?v=6DWnwMZxIW0)


+1 for this,

However, if just for "testing and playing around" kind of stuff. You can get older kernels and distros that still support ARMv6. I think support was dropped 9.10 so 9.04's arm release should still work on the Raspberry.

You can have a look into that. But as stated above, debian and ubuntu under the hood (where you will be working) is so similar you will probably never run into any of the "differences".

Cheers and have fun!

---

