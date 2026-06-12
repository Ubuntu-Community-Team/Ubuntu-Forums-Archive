---
title: "Front Audio Panel Not Working"
date: 2015-01-21
forum: New to Ubuntu
---

### Post by Xshaedx on 2015-01-21
Hi. I recently switched over to Ubuntu 14.10, and to Linux in general, from Windows and OSX for python development. I'm having trouble getting audio output from the front panel of my desktop. On Windows 8.1, I have no problem getting audio output from the front panel. The only audio outputs that are listed for me in Ubuntu are HDMI output, Digital output, and Analog output (my on-board back panel outputs, as I understand). I usually don't ask questions on forums, but this is a problem that I've spent several hours trying to solve with no results. I've tried setting snd_hda_intel model to auto in the alsa conf, with no results. I'm not sure what the problem is. If you need me to post some terminal output, please let me know. Many thanks to any help provided.

---

### Post by Derrick_Katula on 2015-01-23
You probably have the wrong module model loaded for your sound card
also activating system sounds

---

