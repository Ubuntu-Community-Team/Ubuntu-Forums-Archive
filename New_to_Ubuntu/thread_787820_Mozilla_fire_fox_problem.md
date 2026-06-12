---
title: "Mozilla fire fox problem"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by dankster117 on 2008-05-09
I am currently using ubuntu 8.04 (this was happening before the update)and I have been experiencing very choppy/laggy scrolling in mozilla firefox I have not found a solution and this is really really bothering me.

ANY help what so ever would be greatly apreciate (also this doesn't just happen on flash pages)

---

### Post by sharks on 2008-05-09
I had this problem too in reading pdf's.U have to select ur monitor and graphics card correctly.

---

### Post by dankster117 on 2008-05-09
Okay I solved part of the problem uninstalled compiz. but now it happens on flash sites.

---

### Post by Sef on 2008-05-09
What is your graphics card? system specs?

---

### Post by Tomatz on 2008-05-09
What is your computers spec (e.g. cpu, gpu & ram)?

---

### Post by DrMega on 2008-05-09
> **dankster117 said:**
> Okay I solved part of the problem uninstalled compiz.

I didn't realise you could do this, I thought Compiz had been integrated into Gnome? If you do this do you lose anything (apart from the facncy visual effects, which I don't need)?

---

### Post by dankster117 on 2008-05-09
I am using a dell inspiron 1501 AMD sempron ati card 1gig ram

---

### Post by Tomatz on 2008-05-09
dah dah dunnnnn

ATI!

:lolflag:

If you are using hardy (8.04) in a terminal type:

```
sudo apt-get install envyng
```

Then use envy to install the latest ATI drivers. This may or may not work for you though.

If you are using a previous version of ubuntu go here to download the appropriate envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Hope that helps ;)

---

### Post by dankster117 on 2008-05-09
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng

---

### Post by Tomatz on 2008-05-09
> **dankster117 said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng

Sorry.

First you need to enable **3rd party repository's** in [B]software sources
[/B] 

Alternatively just download envyng from the link below:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by dankster117 on 2008-05-09
Okay that didn't really improve it on sites with flash could it possibly be because my direct rending isn't on?

---

### Post by Tomatz on 2008-05-09
Try **r clicking** on the flash video/animation then click **settings** then **disable hardware acceleration** then **reload** the page.

---

### Post by dankster117 on 2008-05-09
didn't help.

---

### Post by dankster117 on 2008-05-09
maybe should use Firefox 2?

---

### Post by Tomatz on 2008-05-09
I am afraid that you are stuck with flash the way it is until the next update from abdobe.  Basically abdobe have made a right hash up of flash for linux. See below:

[http://ubuntuforums.org/showthread.php?t=769906](http://ubuntuforums.org/showthread.php?t=769906)

Seems to do this for some but not for others???

---

### Post by dankster117 on 2008-05-09
Okay well I guess I will just have to wait it out then :) thanks for you help though! atleast I have my latest ATI drivers :)

---

### Post by Tomatz on 2008-05-09
> **dankster117 said:**
> Okay well I guess I will just have to wait it out then :) thanks for you help though! atleast I have my latest ATI drivers :)

No probs :)

Hopefully you wont have to wait long.

---

