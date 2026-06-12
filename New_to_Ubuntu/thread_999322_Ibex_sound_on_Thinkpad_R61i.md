---
title: "Ibex sound on Thinkpad R61i"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by kengla on 2008-12-01
I just switched from Vista to Intrepid Ibex.  This is my first experience with GNU/Linux. I am having issues with the sound.  There is sound, but it is distorted. I have tried searching around the forums for solutions but nothing has altered the sound at all (except some make it worse). Has anyone had this problem and found any solutions?

---

### Post by zzHanks on 2008-12-02
Hi. 

Try this: Type
```
alsamixer
``` in terminal and check the volumes.

---

### Post by Rizareth on 2008-12-02
One of my friends has a problem with random noise from speakers, I don't know if this is the same issue. Try opening the volume control(right-click the sound icon in the toolbar. Hit preferences and add "analog loopback", then go switch that off. Again, this might be a different issue, but here's hoping it works..?

---

### Post by Acegikmo on 2009-02-18
Similar problem on the R61i here.
First off, a fresh install had the problem, then, after changing switches in the hidden section of the volume control panel I fixed it. I've now done something to stuff it up again and I'm not sure what, no combination of the two switches:
IEC958 and IEC958 Default PCM
is fixing the problem.
I don't know anything about sound devices, or what a switch is, but I can describe the distortion as grainy, raspy or like when a speaker is turned up louder than it is supposed to go, although the volume can be adjusted.

If you need me to get more details just tell me how.

---

### Post by Acegikmo on 2009-02-24
Ok so the issue with sound distortion is that the PCM volume is too high, while the master volume is separately controlled.

First, go into your volume control panel and lower the PCM volume till distortion goes away and then increase the master volume to make up for it.

Then, to avoid breaking it again, go into preferences and set applet to control the master volume if it isn't already.

---

