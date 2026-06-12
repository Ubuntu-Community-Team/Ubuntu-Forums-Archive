---
title: "Volume control not working"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by browny254 on 2008-11-01
Hi, I just did a new install of Kubuntu 8.10 but my volume control isnt working. My laptop is a Toshiba Satellite A200/K00 and it has a volume control dial on the front of it. When I turn this the volume display pops up on my screen but it doesnt change, it just displays the current volume no matter what direction the dial is scrolled. How can I fix this?

---

### Post by m_l17 on 2008-11-01
Do you have sound using the volume control on the desktop?

If not try this:

```
$ alsamixer
```

When the screen comes up raise the levels one at a time. Until you get sound.

---

### Post by browny254 on 2008-11-01
The volume works fine - I have KMix though because I have Kubuntu. But its just this dial I have isnt working properly. I also have media buttons above my keyboard that arent working 100% either, the Play/Pause button causes Amarok to restart the currently playing track like the Previous button should, and the previous and next buttons arent working.

If I have Amarok displayed though I am able to change the volume down using the dial, although the Kmix volume display that pops up does not change. 

I have tried setting the shortcuts both in Amarok and in the System Settings and have had no luck so far.

---

### Post by browny254 on 2008-11-01
Ok I have found that the volume dial is only controlling pcm (whatever that is) no matter what channel i select as the master. The reason why the display doesnt change when I have selected the correct channel (Front) is that it is still adjusting the PCM but displaying the current master channel's volume.

Anyone know how to fix this now?

---

### Post by Odur on 2008-11-18
Did you find a solution? I got a similar problem. The volume buttons work, but the popup volume bar only shows 0% no matter what. The slider inside Kmix moves though.

---

