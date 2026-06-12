---
title: "HDMI audio not working after upgrade to Precise"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by RadagastII on 2012-04-30
Just before I upgraded to 12.04 I had gotten the audio to work through the HDMI connection to my TV, but after the upgrade it stopped working.  I am using the onboard video and audio on my Gigabyte GA-E350N-USB3 motherboard, and I would like to have both go through the HDMI cable instead of getting a seperate cable for the audio.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
```
rm -rf ~/.pulse
```
log out and back in and see if it is working
i manged to screw up my hdmi audio after installing 12.04 and that fixed it
once you do that open up your sound settings and try to get it working

---

### Post by Mathor on 2012-04-30
This may or may not work for you, but after installing the most recent kernel, 3.4rc4, my HDMI sound is working for the first time in a while. It usually has to do with missing audio drivers.

---

### Post by RadagastII on 2012-05-01
Alright, I'll give both of those a shot.  Thanks for the assistance.

---

