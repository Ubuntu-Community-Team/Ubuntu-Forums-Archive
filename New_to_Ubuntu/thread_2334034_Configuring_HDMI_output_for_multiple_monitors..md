---
title: "Configuring HDMI output for multiple monitors."
date: 2016-08-15
forum: New to Ubuntu
---

### Post by crecord on 2016-08-15
I am totally new to linux and I am using ubuntu 16.04. I have 4 monitors attached to my pc via HDMI. I have the the GTX 1070 graphics card. I am having an issue where the audio will only output to one of the HDMI devices rather than all 4 :(

I have tried to configure simultaneous output via pulseAudio Preferences, but it didn't work. It still just plays from the one hdmi output. When I look in the system settings under sound and test each hdmi output it still just plays from the one monitor. I've used aplay -L to see what is connected and here is some of the output: 

hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 1
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 2
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 3
    HDMI Audio Output


Any advice on how to switch between the hdmi devices as audio outputs or to create an aggregate device would be much appreciated!!

---

