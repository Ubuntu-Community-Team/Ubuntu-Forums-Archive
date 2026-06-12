---
title: "No sound in chromium -Ubuntu 11.10"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by Baja2001 on 2011-11-30
Hello Everyone
I will be extremely thankful if someone helps my with my problem. For last 2 or 3 days I haven't been able to get any sound in Chromium browser. It happened after I plugged my computer to a TV via hdmi cable. Now after switching back to my monitor and speakers I am able to receive sound in Firefox and all other applications seem to be working fine, just not the chromium. I tried both flash and html 5 and in both cases it's silence. Reinstalling the browser doesn't help neither. 

But when the other user logs on (my wife) she is able to get the sound in the chromium browser in her user account.

Please help
Bartek

---

### Post by Lisiano on 2011-11-30
I have a feeling either pulseaudio or chromium is remembering that you tried using HDMI audio and is staying on it. I would suggest downloading [pavucontrol]("apt://pavucontrol") by either just clicking the name or typing this in a terminal
```
sudo apt-get install pavucontrol
```
After it installed, just run it using either Alt+F2 or a terminal and just type ```
pavucontrol
```
Now open up chromium and find wherever you can't hear sound and tell chromium using pavucontrol to use your speakers or whatever you use.

---

### Post by ask_ on 2011-11-30
> **Lisiano said:**
> I have a feeling either pulseaudio or chromium is remembering that you tried using HDMI audio and is staying on it. I would suggest downloading [pavucontrol]("apt://pavucontrol") by either just clicking the name or typing this in a terminal
```
sudo apt-get install pavucontrol
```
After it installed, just run it using either Alt+F2 or a terminal and just type ```
pavucontrol
```
Now open up chromium and find wherever you can't hear sound and tell chromium using pavucontrol to use your speakers or whatever you use.

Hey, thanks for this amazing tip, I was struggling with the same issue on a Lubuntu machine.([http://ubuntuforums.org/showpost.php?p=11501755&postcount=10](http://ubuntuforums.org/showpost.php?p=11501755&postcount=10))

My Lubuntu machine used to play flash, vlc properly earlier, but suddenly one day, sound went off. I was able to get back vlc sound by changing default audio input to ALSA, but couldn't do so in flash.I don't even know how to configure flash.


Then I read a lot of documentation on ALSA and Pulse audio, but I couldn't sift out the information that my particular problem needed.

I guess , since I am a beginner to Linux what I needed was a GUI in this case.

I tried out what you suggested and now my chromium is playing flash sound as it did previously.

Thanks !!:popcorn:

---

### Post by Baja2001 on 2011-11-30
It solved my problem. Thank you x 10000...

:)

---

### Post by Lisiano on 2011-11-30
Glad it worked. If there are any problems, don't hesitate to ask in the forums.

---

### Post by Liam1027 on 2013-04-08
+1

this just saved me what would have been a headache for sure.

---

### Post by oldos2er on 2013-04-08
Old thread closed.

---

