---
title: "No hardwar sound ubuntu"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by pqku on 2012-01-31
Hi ,


I have ubuntu 11.10
I try to set up alsa because i had skype problem with pusle audio. So i unistalled pulse audio.
When i go to alsamixer i can see and even change the speaker volume.

But when i go setting->sound->no hardwar
 But my micro and webcam work.

What sould i do ? My speaker doesnt work .

Help Please

Thank you

---

### Post by pqku on 2012-01-31
Here is

aplay -l

                                 **** List of PLAYBACK Hardware Devices ****  
 card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]  
   Subdevices: 1/1  
   Subdevice #0: subdevice #0  
 card 1: SB [HDA ATI SB], device 0: ALC269VB Analog [ALC269VB Analog]  
   Subdevices: 1/1  
   Subdevice #0: subdevice #0
  


aplay -L

 null  
     Discard all samples (playback) or generate zero samples (capture)  
 hdmi:CARD=Generic,DEV=0  
     HD-Audio Generic, HDMI 0  
     HDMI Audio Output  
 dmix:CARD=Generic,DEV=3  
     HD-Audio Generic, HDMI 0  
     Direct sample mixing device  
 dsnoop:CARD=Generic,DEV=3  
     HD-Audio Generic, HDMI 0  
     Direct sample snooping device  
 hw:CARD=Generic,DEV=3  
     HD-Audio Generic, HDMI 0  
     Direct hardware device without any conversions  
 plughw:CARD=Generic,DEV=3  
     HD-Audio Generic, HDMI 0  
     Hardware device with all software conversions  
 default:CARD=SB  
     HDA ATI SB, ALC269VB Analog  
     Default Audio Device  
 front:CARD=SB,DEV=0  
     HDA ATI SB, ALC269VB Analog  
     Front speakers  
 surround40:CARD=SB,DEV=0  
     HDA ATI SB, ALC269VB Analog  
     4.0 Surround output to Front and Rear speakers  
 surround41:CARD=SB,DEV=0  
     HDA ATI SB, ALC269VB Analog  
     4.1 Surround output to Front, Rear and Subwoofer speakers  
 surround50:CARD=SB,DEV=0  
     HDA ATI SB, ALC269VB Analog  
     5.0 Surround output to Front, Center and Rear speakers  
 surround51:CARD=SB,DEV=0  
     HDA ATI SB, ALC269VB Analog  
     5.1 Surround output to Front, Center, Rear and Subwoofer speakers  
 surround71:CARD=SB,DEV=0  
     HDA ATI SB, ALC269VB Analog  
     7.1 Surround output to Front, Center, Side, Rear and Woofer speakers  
 dmix:CARD=SB,DEV=0  
     HDA ATI SB, ALC269VB Analog  
     Direct sample mixing device  
 dsnoop:CARD=SB,DEV=0  
     HDA ATI SB, ALC269VB Analog  
     Direct sample snooping device  
 hw:CARD=SB,DEV=0  
     HDA ATI SB, ALC269VB Analog  
     Direct hardware device without any conversions  
 plughw:CARD=SB,DEV=0  
     HDA ATI SB, ALC269VB Analog  
     Hardware device with all software conversions

---

### Post by rgreener25 on 2012-01-31
Try opening sound then output then make sure the right output is selected

---

### Post by pqku on 2012-01-31
i dont have anything in output. nothing at all

---

### Post by rgreener25 on 2012-01-31
maybe your soundcard didn't configure correctly during install

---

### Post by pqku on 2012-01-31
what should i do then ?

---

