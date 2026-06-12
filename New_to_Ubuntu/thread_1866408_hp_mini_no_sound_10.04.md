---
title: "hp mini no sound 10.04"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by 40ftcobb on 2011-10-21
ok so i have andhp mini 110
yesterday i installed 10.04 lts and 2 things i noticed 
1 no sound  
nothing muted volumes up just no sound from internal speakers,3.5mm jack works fine
2 cant use my sd reader wont even load the card up
anyone have any ideas how i correct these issues?
thanks in advance

---

### Post by ArgusVision on 2011-10-21
Ok. A couple of thing to check.

In terminal:

**jockey-gtk**

This will scan for drivers. You may get suggestions from jockey, you may not.

Also in terminal:

**alsamixer**

You will get a set of colored bars. Look for any that say 'MM', that means muted. Devices found tend to vary, but mine are

Master, Headphone, PCM, Front, Front_Mi, Mic_Jack, and PC_Beep. 

The only one I have muted is PC_Beep. 

Left and right arrows select the interface. Up and down adjust the volume. 'm' mutes and unmutes. 


Hope this helps. Have fun Ubuntuing :)

---

### Post by 40ftcobb on 2011-10-21
ya none ofthat worked lol

---

### Post by ArgusVision on 2011-10-21
hmmm... Do you have the most recent kernel? I'm trying to remember if there was a separate kernel that worked well for the HP mini's. I'm probably thinking of the Acer Aspire One.

---

