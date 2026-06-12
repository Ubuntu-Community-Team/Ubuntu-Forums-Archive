---
title: "S-video from laptop to TV issue"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by stardustmz on 2011-12-04
I updated to Ubuntu 11.10 and now when I connect my laptop to the TV with the s-video cable there is a flicker like I just turned it on or changed the channel every few (5-20) seconds.  I'm pretty new to linux, I've only been using it for a couple months so I have no clue how to go about fixing this.  

My laptop is an Acer Aspire 3690 2672 and I unfortunately don't know the model of my TV because it was a hand me down from a friend, all I have to go on is the logo, which is an oval with a D and a reverse crescent in sliver around the D.

Any help will be greatly appreciated.

---

### Post by jtokarchuk on 2011-12-04
Hi there, 

Have you confirmed that the cable is good? Was it functioning proper on Windows (if you had ever used?)

Are any pins bent on the cable?

Had you installed any video drivers (From additional drivers)?

---

### Post by stardustmz on 2011-12-04
The cable was working well up until I updated Linux.  It worked with Windows and the previous form of Ubuntu I had.  

The pins are not bent, the cable seems sound, and I don't know what additional drivers I might need.  It worked just plug and play before.

---

### Post by jtokarchuk on 2011-12-04
If you open the dash, and navigate to "Additional Drivers", are there any video drivers there for you to install? Perhaps they might provide a more solid picture. Perhaps your driver had changed between Ubuntu versions.

---

### Post by stardustmz on 2011-12-04
It says there are no proprietary drivers in use on this system.  Is there somewhere I could look to find some?

---

### Post by stardustmz on 2011-12-04
I've tried some to use the info on s video on the Ubuntu wiki.

This is what I put in:

 xrandr --output S-video --set load_detection 1

This is what I get out:

warning: output S-video not found; ignoring
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  30
  Current serial number in output stream:  30

So apparently the s video isn't being detected.  :(

---

### Post by stardustmz on 2011-12-06
I was prompted to update to 11.10 (again...which seems odd)  and now the issue has resolved itself.  Thanks for the advice.

---

