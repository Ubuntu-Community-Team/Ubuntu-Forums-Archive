---
title: "gtkpod/volume/suspend &amp; hibernate problems"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by abraxas_swa on 2008-06-03
Hi guys, thanks for taking a moment to read this. Any advice is greatly appreciated.

I recently installed Hardy on my Compaq Presario C300 laptop. It's been a largely positive experience, and any issues I've had I've been able to resolve either playing around with the machine or looking through the forum archives. I have three remaining problems though, and I hope you can help me with them.

1 - I can use gtkpod to view my iPod's track listings and can play the music through Rythmbox, however I am unable to save any changes in gtkpod. It's a Windows formatted 80GB video model. I can connect and mount it without any problems but am unable to transfer tracks to it, delete tracks from it or change information such as song titles, artist names etc. I go through the steps, select "save changes" and nothing happens.

2 - The volume on the machine is stuck at 100%. I can use the volume control buttons on the keyboard or use the graphical slider on the desktop panel, however the volume remains at full level, even when set to mute. I CAN change the volume within an application such as Movie Player or Rythmbox, however I'd prefer to be able to set this through the main volume control

3 - If I attempt to sleep, hibernate or close the lid of the laptop, I can't wake it up! I need to power off and restart the machine. This is very inconvenient and any help would be greatly appreciated.

Thanks in advance for your help!

---

### Post by _sphinx_ on 2008-06-03
Hello,

For main volume control you can use the command:
alsamixer 
and see if this works. I don't know why the volume control at panel is not working.
And about the sleep and hibernate, I am suffering from the same problem but its not all the time that it doesnot wake up, like, it sometimes wakes and sometime I have to suspend the laptop again wake it up, it helped me though.

---

### Post by sayakb on 2008-06-03
1. Banshee media player (as well as Rhythmbox) has native support for iPOD. You may also try Exaile, which has a good iPOD plugin.

2. Open a terminal and type:
```
alsamixer
```
Also, check that you set your device to ALSA (and not Pulseaudio) from the Volume (Mixer) applet.

3. Seems to be a problem on some laptops.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203253](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203253)
Though someone might have a solution.

---

