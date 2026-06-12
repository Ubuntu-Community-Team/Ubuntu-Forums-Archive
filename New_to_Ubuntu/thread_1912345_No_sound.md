---
title: "No sound???"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by BanterThorpin on 2012-01-20
Hello I have just installed ubuntu studio on my desktop yesterday and all went well. Everything booted up I adjusted all my colors and appearance to how I like played with the many settings connected to the Internet and so on. It all seemed great then I wanted to check out all the audio programs that studio comes with to find I have no sound at all anywhere. I try to run the linux audio configuration tool but I get an error 
"JACK can only be configured with a loaded and stopped studio. Please create a new studio or load and stop an existing one."
  I am new to linux and I do not understand. I can not find how to install proper drivers for my sound card. My computer has on board audio ALC883 a realtek hd audio card on a MSI mainboard with an AMD 64x2 4400+ with on board Nvidia gpu.
I found a thread that instructed me to find the most similar card from alist and add the name to the end of  ("ALSA"???) I followed those instructions but it did not help. The only info I can find on my card and linux is all about laptops but I am on a desktop???
:confused:
I would really like to fix this as it was the audio production that I wanted to use as I am a big reason fan and will be hooking up my axiom 61. will I have any issues with the keyboard once I get my sound problem soved? 
I am new to linux but can follow detailed instructions.
Thank you

I put in the code:  aplay -l 
and I get this 
banter@BanterThorpin:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
banter@BanterThorpin:~$

---

### Post by Buntumatic on 2012-01-20
It looks like the driver is installed. Did you check mixer levels with amixer? Can you play anything when using ALSA directly, bypassing JACK?

ALSA provides low level sound driver, JACK is sound server, middleman between ALSA and your application.

---

### Post by BanterThorpin on 2012-01-20
Got it Thanks. The mixer was fine and all the volumes were set right, but for some reason the speaker out was in a different spot on the back of the pc from where they were plugged in before? 
All set for now, until ?:D
Thanks

---

