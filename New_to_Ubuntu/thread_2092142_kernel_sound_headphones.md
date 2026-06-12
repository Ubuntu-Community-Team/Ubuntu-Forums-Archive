---
title: "kernel sound headphones"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-12-06
The worst thing about linux are the sound problems. I am quickly loosing credibility among my friends after I recommend linux and they run into problems. I've had numerous problems myself and here's my latest one.

The headphones give very low sound, almost impossible to hear. I had the problem before and fixed it with 
sudo leafpad /usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones.conf

 [General]
-priority = 100
-name = analog-output-speaker
+priority = 90
+name = analog-output-headphones
+
+[Jack_InputDevice]
+code = Headphone
 [Element Hardware Master]
 switch = mute
Where lines with ‘-’ in front should be removed and lines with ‘+’ should be added.
Then reboot.

Somehow, not chosen by me, the kernel updated itself. Now instead of 
3.0.0-22-generic-pa
I have
3.0.0-28-generic-pae

So I tried
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
but there was nothing for my kernel. The ppa seems to stop at 
3.0.0-20 generic-pae

In alsamixer the sound on the headphones is as loud as you can put it but this doesn't solve the problem.

Any help would be appreciated.

---

### Post by Kevin McCready on 2012-12-06
I just tried
1
sudo apt-get purge pulseaudio pavucontrol
2
rm -rf ~/.pulse 
3
sudo apt-get install pulseaudio pavucontrol

Reboot

But it didn't work either.

---

### Post by Kevin McCready on 2012-12-07
bump

---

