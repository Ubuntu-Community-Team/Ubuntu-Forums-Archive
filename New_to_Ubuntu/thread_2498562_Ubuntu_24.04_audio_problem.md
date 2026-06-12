---
title: "Ubuntu 24.04 audio problem"
date: 2024-06-19
forum: New to Ubuntu
---

### Post by emred12 on 2024-06-19
I'm using a Monster Huma H4 V3.2 laptop. I've installed Ubuntu 24.04 on my PC. Wifi, Bluetooth, and everything else is working fine. However, when I join an online meeting (like Zoom, Skype, etc.), my voice comes through very crackly on the other end. When I lower the volume, the crackling stops but my voice also becomes quieter. I've tried various options like Alsamixer and PulseAudio, but none of them fixed the issue.

I contacted customer support, and they said Monster laptops are only compatible with Windows and suggested I find and install a Realtek driver for Linux. I couldn't find a Realtek audio driver version 6.0.8757.1 on the internet. How can I solve this problem?

I hope someone has encountered a similar situation before. I would greatly appreciate your help.

PS: For additional drivers, the option 'nvidia driver metapackage from nvidia-driver-535 (proprietary - tested)' is selected. 

Also I tried to remove Pulseaudio and install pipewire, also I purged 535 nvidia driver and install 555. But unfortunately I still have the same problem. I joined an online meeting, and still my voice goes very crackly and dirty. :(

---

### Post by currentshaft on 2024-06-19
Laptop microphones are notoriously terrible. Even if you get it working perfectly, it will still sound awful. Recommend investing into a USB microphone if you're going to be in online meetings, they can be quite cheap and people will thank you for using it.

---

### Post by emred12 on 2024-06-19
Thanks a lot for your recommendation. I wonder your idea, should I use usb microphone or bluetooth microphone would be fine ?

---

### Post by Autodave on 2024-06-19
USB is a LOT easier to set up.

---

### Post by anntuio on 2024-06-24
I have to agree with you, but there are some great [COLOR=#333333][FONT=&quot][speakerless audio system]("https://audiolab360.com/driving-the-electric-vehicle-ev-revolution-forward-with-superior-audio-technology/") that work well but connected to the laptop[/FONT][/COLOR]

---

### Post by him610 on 2024-06-24
Recommendation: Plantronics Blackwire C310 USB headset [https://www.amazon.com/Plantronics-85618-02-Blackwire-C310/dp/B00EU8U8RI/ref=sr_1_5?crid=SFY3VI1ZC2G3&dib=eyJ2IjoiMSJ9.O4B977jseYDnBfx4ozjFMltbT2k32gNV7-AZES30h2Fc_0HGuE5CFSNUQoU6WLAvvuJhB9mUFwMOrqpLqKh5ntaZ7l6-Cr14MTS2NVqv7X9YwrArs5WMwXD1mUnQKFaF-CwDDpIigdgJSRJBVfWNQSq5aMSxIMF5ttaK-RmYZm0cyFrqNT50txmUDKSsSKkjQi1AO5l0jxWs0bnz2Ej2u6FLjaAA1uwXirWZNBoOv2umjSjr5PLR_kalNxEsujsBkb21brNAu3jZvopw9Br0mqSP-fek8vS3QanSL_32zts.5AbKChvAlxp4OEH6fOFNV2LIBIgktC3gmC6afCNla3Q&dib_tag=se&keywords=Plantronics+Blackwire+C310+headset&qid=1719274010&sprefix=plantronics+blackwire+c310+headset%2Caps%2C622&sr=8-5]("https://www.amazon.com/Plantronics-85618-02-Blackwire-C310/dp/B00EU8U8RI/ref=sr_1_5?crid=SFY3VI1ZC2G3&dib=eyJ2IjoiMSJ9.O4B977jseYDnBfx4ozjFMltbT2k32gNV7-AZES30h2Fc_0HGuE5CFSNUQoU6WLAvvuJhB9mUFwMOrqpLqKh5ntaZ7l6-Cr14MTS2NVqv7X9YwrArs5WMwXD1mUnQKFaF-CwDDpIigdgJSRJBVfWNQSq5aMSxIMF5ttaK-RmYZm0cyFrqNT50txmUDKSsSKkjQi1AO5l0jxWs0bnz2Ej2u6FLjaAA1uwXirWZNBoOv2umjSjr5PLR_kalNxEsujsBkb21brNAu3jZvopw9Br0mqSP-fek8vS3QanSL_32zts.5AbKChvAlxp4OEH6fOFNV2LIBIgktC3gmC6afCNla3Q&dib_tag=se&keywords=Plantronics+Blackwire+C310+headset&qid=1719274010&sprefix=plantronics+blackwire+c310+headset%2Caps%2C622&sr=8-5")

Been using a Plantronics Blackwire C310 headset for over 10 years now with both laptops and desktops.

---

