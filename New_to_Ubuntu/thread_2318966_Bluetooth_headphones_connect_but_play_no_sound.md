---
title: "Bluetooth headphones connect but play no sound"
date: 2016-03-30
forum: New to Ubuntu
---

### Post by jdkcarlson on 2016-03-30
I'm running Ubuntu 14.04 on a Acer Aspire R5-471T. 

I try to connect my Bluetooth headphones to my computer. When I do, they make the noise that says they're connected, but after that, won't play sound. The Bluetooth icon in the upper right appears with a little lock under it. In the sound options, the dials that would let me adjust left and grey balance are grayed out. When I try to play something with Google Play Music, say, the play button doesn't respond and become a pause button, and similarly with YouTube. When I disconnect the headphones, the videos or audio tracks start playing.

These headphones work for my phone, so it doesn't seem to be a problem with them. 

How do I make them play sound?

Thanks!

---

### Post by jeremy31 on 2016-03-31
Check ```
pactl list short | grep bluetooth
```

You are likely missing module-bluetooth-discover

---

### Post by Geoffrey_Arndt on 2016-03-31
_Just in case you haven't tried this already_, but you also have to select the new device (or in this case, change it from PC speaker to the device).   If using Unity, this is done via the sound settings option (click on the Sound Widget in the top-right panel) . . you should see your devices - - choose the right one.

---

### Post by jdkcarlson on 2016-04-01
> **jeremy31 said:**
> Check ```
pactl list short | grep bluetooth
```

I get

```
7	module-bluetooth-policy		
8	module-bluetooth-discover
```

Does this mean I *do* have the discover module? It *claims* to connect in any event.

---

### Post by jdkcarlson on 2016-04-01
> **Geoffrey_Arndt said:**
> _Just in case you haven't tried this already_, but you also have to select the new device (or in this case, change it from PC speaker to the device).   If using Unity, this is done via the sound settings option (click on the Sound Widget in the top-right panel) . . you should see your devices - - choose the right one.

Yep, I did try this; that's how I realized the options for adjusting balance, volume, etc. are grayed out. **WAIT**

I just randomly adjusted "Mode" in this panel from "telephony duplex (HSP/HFP)" to "high fidelity playback (A2DP)" and now for some reason it's fine! So I guess I'll mark this one solved too, but any idea what just happened?

---

### Post by jdkcarlson on 2016-04-02
Another question: is there a way to make these the default so I don't have to change these two settings manually every time I connect these headphones?

---

