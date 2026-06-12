---
title: "I've got flash 10 but bloomberg says I need higher than 8"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by kramer65 on 2008-08-22
Hello,


I recently installed flash 10 (Shockwave Flash 10.0.0 d569) but when I go to [a chart on bloomberg.com]("http://www.bloomberg.com/apps/cbuilder?ticker1=NDX1%3AGR") it says that I need a flash version higher than 8.

Does anybody know a solution to this?

---

### Post by oliviacond on 2008-08-22
downgrade to flash 9. i have no problem viewing the chart using flash 9.

---

### Post by kramer65 on 2008-08-22
The problem is that I upgraded to flash 10 because youtube sound wasn't working and it constantly crashed with 9. I think youtube is still more important than bloomberg (I'm not a stockbroker or anything, just sometimes interested..).

Is there not a solution to this? Is it actually the fault of flash or of bloomberg?

---

### Post by bikeboy on 2008-08-22
Any chance you're blocking javascript on that site? That will cause sites to not recognise you have flash (no matter which version).

---

### Post by Majorix on 2008-08-22
Flash 10 is not officially out (yet), that might explain why the site doesn't recognize it.

---

### Post by philinux on 2008-08-22
This thread got me digging and this is weird.

I've got the backports selected and in synaptic it shows I've got flash version 10.0.1.218. however if i look at firefox plugins it says 
File name: npwrapper.libflashplayer.so
Shockwave Flash 9.0 r124

---

### Post by forger on 2008-08-22
> **philinux said:**
> This thread got me digging and this is weird.

I've got the backports selected and in synaptic it shows I've got flash version 10.0.1.218. however if i look at firefox plugins it says 
File name: npwrapper.libflashplayer.so
Shockwave Flash 9.0 r124

perhaps this could help:
close firefox
```
sudo aptitude purge flashplugin-nonfree nspluginwrapper
sudo aptitude install flashplugin-nonfree
```

open firefox, and see if it's fixed with flash 10 now :)

---

### Post by billgoldberg on 2008-08-22
Some other sites also have this problem.

Try watching a video on cnn.

This problem will solve itself when flash 10 comes out officially (or maybe some time for that).

Most sites don't have a problem though.

---

### Post by bikeboy on 2008-08-23
> **philinux said:**
> I've got the backports selected and in synaptic it shows I've got flash version 10.0.1.218. however if i look at firefox plugins it says 
File name: npwrapper.libflashplayer.so
Shockwave Flash 9.0 r124

The Ubuntu guys backported a version of Flash 10 beta (beta 2 iirc) but it caused a lot of problems so they reverted. If you look at the full name of the backports version it says something like 10.0.0.218~really9.xxx

In other words you're using Flash 9, therefore Firefox displays it as such.

---

### Post by alienexplorers on 2008-08-23
I put in a problem report to state running flash 10 does not work.  Waiting for there reply.

---

### Post by gjoellee on 2008-08-23
many web-sties doesn't recognize flash 10 yet

---

### Post by Kinetic_lord on 2008-08-23
I also had a problem with the flash player, my You Tube videos didn't worked but i found " flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb " There you go...

Google search it, the post was supposed to have an attachment! X( X(

---

### Post by Kinetic_lord on 2008-09-10
Well? it worked? you could at least say thanks if you don't want to close the thread...

---

### Post by kramer65 on 2008-09-15
Hey sorry. I didn't watch my own topic for a while. The thing is that it took me ages to get youtube videos working and now they finally do bloomberg doesn't work. Since youtube is a bit more important to me than bloomberg (am not an active trader, just want to check out some things sometimes..), I think I will just leave things as they are now and wait for flash 10 to come out officially.

In the meantime, I'll watch the charts on yahoo finance instead of bloomberg. 

Thanks anyway!

---

### Post by SunnyRabbiera on 2008-09-15
Flash 10 is still a beta.

---

