---
title: "connecting my comp to my HDTV - sound issue"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by Toronto11 on 2012-02-22
Good evening,

I am using Ubuntu 10.04 and am trying to connect my comp to my Samsung  Series 503 HDTV but can only thus far get the sound out of the computer  speakers.  

I'm on the verge of entering a command into the  etc/modprob.d/alsa-base.conf file but wanted to make sure I don't  totally mess things up.

In the alsa-base.conf file I was going to enter the following:
options snd-hda-realtek model=auto =enable=1 index=0

where realtek is the sound card maker, or would I put alc1200 as the sound card manufacturer?

I have an Asus M3A78-EM motherboard and am using an HDMI to HDMI connection.

Thanks for any and all assistance.

---

### Post by grahammechanical on 2012-02-22
Are you sure that the signal coming out of the video card HDMI socket also includes an audio signal?

I have a Samsung T200HD that I connect to my Nvidia Geforce GT 220 by DVI-D and to get sound coming out of the TV/monitor screen speakers I use the line-out port of the motherboard's built in audio card. The motherboard is an Asus P5B deluxe.

The cable goes into the HDMI/DVI-D AUDIO IN port on the back of the TV/monitor. Otherwise no sound as I do not have computer case speakers.

Regards.

---

### Post by Toronto11 on 2012-02-22
No, I'm not too sure.  How would I check that?

---

### Post by philmacdonald2 on 2012-02-24
Most HDMI outs from computers only carry video. You may need to get an HDMI to Component AV cable and then get a 3.5mm to Red and White sound leads. Unless your TV has a HDMI with a DVI port. Then just plug a 3.5mm to 3.5mm audio cable into the DVI and the HDMI in as well. My Samsung TV has a DVI on HDMI 1, check the back of your tv. This would allow you to get audio too pretty easily. As for checking to see if the HDMI outputs sound, visit the manufacturors website and see if it tells you there.

---

### Post by gordintoronto on 2012-02-24
Tell us more about your computer? (Are you using the onboard video?) On my laptop, I have to change the sound device in Sound Preferences to get sound on the TV via HDMI.

My desktop computer has a cable which connects the motherboard sound to my video card, so the HDMI out includes sound from the motherboard. I suspect most system builders don't bother with this cable...

By the way, every release of Ubuntu over the past couple of years has improved the support for sound devices. Running 11.10 might fix your problem all by itself.

---

### Post by audiomick on 2012-02-24
> **philmacdonald2 said:**
> ... 3.5mm to Red and White sound leads..

With "red and white", I expect you mean RCA connectors.
[http://en.wikipedia.org/wiki/RCA_connector](http://en.wikipedia.org/wiki/RCA_connector)
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/9/91/Composite-cables.jpg/800px-Composite-cables.jpg[/IMG]

---

### Post by LowSky on 2012-02-24
go to the sound settings in Ubuntu you should have an option to use HDMI sound, Under the hardware tab make sure HDMI is on, then under output choose hdmi.

---

### Post by philmacdonald2 on 2012-02-25
> **audiomick said:**
> With "red and white", I expect you mean RCA connectors.
[http://en.wikipedia.org/wiki/RCA_connector](http://en.wikipedia.org/wiki/RCA_connector)
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/9/91/Composite-cables.jpg/800px-Composite-cables.jpg[/IMG]
Yeah, but a 3.5mm jack to just the red and white leads. Can easily get them from eBay.

---

