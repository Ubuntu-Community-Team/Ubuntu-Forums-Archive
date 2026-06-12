---
title: "i need help with my graphics and wifi card"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-04-27
ok i am completly new to linux but i though id give it a try and learn to use it. i found this fourm and have seen that a lot of people are having the same kind of problems as me.they include my nvidia go 7400 graphics card sayin its installed but "not in use" and also my wifi card doesnt seem to be workin but im actually not sure how to activate it...any help would be most welcome but please remember that i am new to ubuntu and i migh need step by step help on how to do stuff.

info that might help - 
graphics = geforce go 7400
wifi = intel pro wireless 3945abg
memory 2gb
dual boot vista/ubuntu 8.04

---

### Post by Gambini on 2008-04-27
So I am assuming that you are using a laptop. I am unskilled in the wireless area, because my intel wireless worked right off the bat, but have you tried installing the video card drivers? Either through "envy" or the restricted drivers manager.

---

### Post by betterthanjordan79 on 2008-04-27
yh i am using a laptop-forgot 2 mention that-its a hp pavilion dv6000 series!and i dont no were to got the drivers or how to install them and as i mentioned earlier i have no internet connection so i cant download them through linux-just vista!

---

### Post by betterthanjordan79 on 2008-04-27
can anyone help me at all??im really :confused: by this whole problem:(

---

### Post by cubeist on 2008-04-27
start here:

[https://wiki.ubuntu.com/HP_dv6000_Series](https://wiki.ubuntu.com/HP_dv6000_Series)

if you still have questions, post back

---

### Post by abhiroopb on 2008-04-27
So as you can see from my specs I have the EXACT same specs as you (including my wireless card). 

If you look at my thread here ([http://ubuntuforums.org/showthread.php?t=768515](http://ubuntuforums.org/showthread.php?t=768515)), basically the wireless card driver has been updated from an open source one to an intel one, and so there have been problems. Not really sure what was wrong with the nvidia card, but again I had a problem.

Personally I suggest using 7.10 at least temporarily because all my hardware works with it. 

Read my thread, as you can see the only solution I could find for the wireless card was to use the older kernel, this is a bit of a workaround rather than a solution.

As for the graphics card you can use scrren and graphics:
Go to: System>Administration>Screen and Graphics (password). Click on the graphics card tab and select the "nv" driver. Then the screen tab and configure the resolution as you need to.

Hope this helps, please ask for anything else, since we have basically the same laptop I'm sure I've had virtually all the problems you could encounter.

---

### Post by abhiroopb on 2008-04-27
So as you can see from my specs I have the EXACT same specs as you (including my wireless card). 

If you look at my thread here ([http://ubuntuforums.org/showthread.php?t=768515](http://ubuntuforums.org/showthread.php?t=768515)), basically the wireless card driver has been updated from an open source one to an intel one, and so there have been problems. Not really sure what was wrong with the nvidia card, but again I had a problem.

Personally I suggest using 7.10 at least temporarily because all my hardware works with it. 

Read my thread, as you can see the only solution I could find for the wireless card was to use the older kernel, this is a bit of a workaround rather than a solution.

As for the graphics card you can use scrren and graphics:
Go to: System>Administration>Screen and Graphics (password). Click on the graphics card tab and select the "nv" driver. Then the screen tab and configure the resolution as you need to.

Hope this helps, please ask for anything else, since we have basically the same laptop I'm sure I've had virtually all the problems you could encounter.

---

### Post by betterthanjordan79 on 2008-04-27
thanks everyone who posted with help-i will try all this out now and let you'se no how i got on!!

---

### Post by abhiroopb on 2008-04-27
Forgot to mention, the older kernel is 2.6.22-14-generic. Not sure if this is installed when you install 8.04 so this may not be possible. During boot press escape when a message appears about grub loading, then look for the 2.6.22-14-generic kernel. This will make your wireless card work at least.

---

