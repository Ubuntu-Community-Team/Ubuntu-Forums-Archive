---
title: "Wifi connected, but internet not working. Tried fixes but haven't worked...help!"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by helpthefun on 2013-06-06
[COLOR=#333333][FONT=UbuntuRegular]I have a lenovo x230 running ubuntu 12.04lts (network card is intel centrino advanced n6205). I've been using it just fine for a while, but all of a sudden the internet's stopped working. It's connected to the router just fine (I can see the antenna bars saying it's connected) but when I try to go to a webpage, it's just loading forever. I've tried the fix listed here ([http://ubuntuforums.org/showthread.php?t=1985079](http://ubuntuforums.org/showthread.php?t=1985079)) but it hasn't done anything (the instructions are a little confusing though. What am I supposed to type after [COLOR=#000000][FONT=Ubuntu Mono]gksudo gedit /etc/pm/power.d/wireless [/FONT][/COLOR]). 

I'm booting windows 7 right now and the internet works just fine when I'm on windows, so I know it must be a problem with ubuntu. I haven't touched any network settings before this problem happened, and I've been using it just fine for months, so I don't know why I'm getting this problem all of a sudden.[/FONT][/COLOR]

---

### Post by helpthefun on 2013-06-06
There seem to be some common outputs that people seem to ask for questions like mine. I ran some of the ones I saw and uploaded the results that I got here: 
[https://gist.github.com/anonymous/c001b8ac5a7369d46cfc](https://gist.github.com/anonymous/c001b8ac5a7369d46cfc)

---

### Post by Rebelli0us on 2013-06-06
Does it work after you shut off and reboot?  I have an Intel centrino advanced-N 6235 Wireless and it's quirky.

---

### Post by helpthefun on 2013-06-06
That's my go-to solution I always jump to before even googling anything. No luck this time though.

---

### Post by Rebelli0us on 2013-06-06
The kernel in 12.04 has full support for Centrino. Does the connection kick in if you temporarily disable Bluetooth?

---

### Post by helpthefun on 2013-06-06
i'll try that in a bit (im on windows now), but that's the weird thing. It's been working fine for months (with bluetooth on and off) and just suddenly broke.

---

### Post by Rebelli0us on 2013-06-06
I had connect problems with my Centrino too, but after several reboots it fixed itself.       It's supposed to be the best and the latest but it's slow to connect.     And also I think manufacturers in general don't give Linux devs as much cooperation as they give to Microsoft.  But in the end it gets sorted out.  Try a newer kernel if you're handy at such installations.

---

### Post by steeldriver on 2013-06-06
pages 'loading forever' is often a path MTU discovery issue - have you tried reducing the MTU? or trying to diagnose it with a ping test?

---

### Post by helpthefun on 2013-06-06
my bad, not 'forever'. It just keeps loading for a really long time but it'll eventually stop and the browser displays some error message.

---

