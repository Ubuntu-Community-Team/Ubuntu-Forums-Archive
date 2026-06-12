---
title: "What to do next?"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by AdrenalineJunkie on 2008-09-23
Well I have had a problem loading up the LiveCD in my iMac G3 (500mhz)

I was suggested using the command:

live-nosplash-powerpc video=ofonly

Which works, to a point-

I am now stuck on a terminal screen with all of the writing showing that its startng bluetooth etc.

And now I am prompted with 

ubuntu@ubuntu$


What do I do now to get into the Live Desktop so that I can install?

Thanks.

---

### Post by Titan8990 on 2008-09-23
Although you should not have to do this, try:


sudo /etc/init.d/gdm start

---

### Post by AdrenalineJunkie on 2008-09-23
I'm now just given:

*Starting GNOME Display Manager....    [Fail]

:(

---

### Post by Titan8990 on 2008-09-23
I would try the alternate CD. The live CDs have not worked on about half of the computers I have tried. Alternate CD has not failed on me yet.

---

### Post by LowSky on 2008-09-23
which version are you trying to install?

7.10 is the last version that supported PowerPC computers... you can get it here
[http://cdimage.ubuntu.com/ports/releases/7.10/release/](http://cdimage.ubuntu.com/ports/releases/7.10/release/)

---

### Post by AdrenalineJunkie on 2008-09-23
Kwl thanks, ill see if it works.

---

