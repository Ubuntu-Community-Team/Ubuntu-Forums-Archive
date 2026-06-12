---
title: "DVD playback"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by mcgarry83 on 2008-11-02
Im having a bit of an issue with DVD playback. I have all the proper codecs installed. The problem is, when I try to play a DVD it starts but it skips every couple of seconds. It completely unwatchable. I have tried several DVD's and media players. It happens in Totem VLC and GXINE. I did not have this problem in Hardy either. I dont know what else to try.

---

### Post by shae on 2008-11-02
What CPU/video card do you have?

---

### Post by mcgarry83 on 2008-11-02
Its a compaq presario 2140us with and AMD xp 2200+ and the video card is a ATI MOBILITY RADEON 4X AGP 3D architecture. But that shouldnt really have an effect, after all it played DVD's fine when I had Windoz XP, and played fine with Ubuntu from Dapper all the way to Hardy. I upgrade to Intrepid, and all of a sudden I get this problem, which by the way, is really the only problem I have in 8.10. Other than that, its a great OS!

---

### Post by mcgarry83 on 2008-11-03
I've been messing with some settings and DVD playback has improved but Im still getting some skipping every few seconds. I opened gstreamer-properties and changed it to "x window system (x11/xshm/xv)" and for device I used ATI Radeon video overlay. I also made VLC use x11 for video output. VLC is also using about 50-60% of my processor. Is that normal? It seems a little high. I only have a 1.8 gig processor, but like I said, I never had DVD playback issues before 8.10.

edit: No matter which video player I use, my CPU is getting absolutely rapped. I even tried a last ditch effort and used Xfce with the same jerky video. How can I make video use less processing power?

---

### Post by jtdelasalas on 2008-11-11
I'm actually forum surfing trying to find a solution to this exact problem.  Is this just some huge bug from 8.10 that enough people haven't encountered yet?

---

### Post by kansasnoob on 2008-11-11
Go to Synaptic and search for libdvdcss2

Things are changing with Medibuntu and I don't have it figured out yet!

I'm having trouble getting libdvdcss2!

---

### Post by johnjb on 2008-11-11
I had the same problem found after searching the forums it is a compiz issue there advice was to install Conpiz Fusion to enable switching between different visual effects for use for 3D and DVD go to 
System> Preferences> Appearance> Visual Effects> select None 
Hope this works for you it worked for me

---

### Post by fogelfink on 2008-11-18
I have the same issue with skipping video, but your solution, johnjb, seems to suggest that we have to turn compiz off completely, or am I getting this wrong?
My widget layer is gone when selecting the No Visual effects option, plus I now have the annoying effect that new windows open behind the currently top layer window.  Do I have to re-enable compiz now to get some of the desktop/window management finctionality back, or would that mean to bring the trouble back.  BECAUSE the trick seems to work - the DVD I just tested did not play choppy video.  
One more thing that I am wondering about is if that video problem is related to an audio glitches problem, I am experiencing in 8.10.  Amarok skips and distorts playback as soon as I plug a USB stick in i.e.  This also does not seem solved by the no effects setting, so it might be unrelated, I was just wondering if anyone else had such problems with video & sound.

---

