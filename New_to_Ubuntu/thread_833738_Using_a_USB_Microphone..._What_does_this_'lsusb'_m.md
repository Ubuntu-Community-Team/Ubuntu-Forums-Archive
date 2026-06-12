---
title: "Using a USB Microphone... What does this 'lsusb' mean?"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by OKnotOK on 2008-06-18
My "lsusb" says:
 
> 

Bus 002 Device 007: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 002 Device 002: ID 0461:4d16 Primax Electronics, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 058f:6377 Alcor Micro Corp. 
Bus 001 Device 001: ID 0000:0000

With "Asahi Kasei Microsystems Co., Ltd" being what shows up for my USB mic. 

Shouldn't it say Logitech since it's a logitech mic?

Also, in alsamixer, should I have the input source as 

Mic
Front Mic
Line
Aux

or would I need something else?

---

### Post by z0mbie on 2008-06-18
Usually companies brand other products with their popular brand name. Like DLink with Realtek hardware. I have the same USB mic, it'll be under AK5370 (Alsa mixer). If you have issues with recording on it in Audacity, you'll need to select **1 (Mono)** channel in the with **ALSA:AK5370** as the device.

---

### Post by OKnotOK on 2008-06-18
> **z0mbie said:**
> Usually companies brand other products with their popular brand name. Like DLink with Realtek hardware. I have the same USB mic, it'll be under AK5370 (Alsa mixer). If you have issues with recording on it in Audacity, you'll need to select **1 (Mono)** channel in the with **ALSA:AK5370** as the device.

Okay, I've set AK 5370 as the device using my volume control-thingie (forgive me for not knowing the proper terms all the time)... 

I'm just trying to use the mic with the sound recorder, cheese, etc.

---

### Post by z0mbie on 2008-06-18
OK, by default it is muted, so you'll have to make sure it's not muted.

---

### Post by OKnotOK on 2008-06-18
> **z0mbie said:**
> OK, by default it is muted, so you'll have to make sure it's not muted.

Did that. It still isn't working. I also changed to AK5370 in system>preferences>sound

---

### Post by z0mbie on 2008-06-18
Are you using Audacity?

---

### Post by OKnotOK on 2008-06-18
No, just trying to use the 

applications> sound & video> sound recorder

I'm just trying to make the mic work -- the goal is for it to work in Cheese.

But I just downloaded Audacity. It says 

> Error while opening sound device. Please check the input device settings and the project sample rate.

---

### Post by OKnotOK on 2008-06-18
Okay I think I have it in mono recording, but I've clicked on every little thing and can't find any way to change the device to AK5370.... Either way how will Audacity work for me? I am trying to use this with my webcam in Cheese...

---

### Post by z0mbie on 2008-06-18
> **OKnotOK said:**
> No, just trying to use the 

applications> sound & video> sound recorder

I'm just trying to make the mic work -- the goal is for it to work in Cheese.

But I just downloaded Audacity. It says

Honestly, I've had issues with Sound Recorder. For Audacity make sure your settings in Edit > Preferences look like this:

[CENTER][IMG]http://img205.imageshack.us/img205/1925/audacityhh2.png[/IMG][/CENTER]

I haven't tried Cheese but, I'll look into it for you. There must be away to get different audio input source other than the webcam in Cheese.

---

### Post by OKnotOK on 2008-06-18
Still nothing. Although Audacity allows me to make a recording, there's no audio there. (It's all four-letter words by now, lol!)

When I was using a mic that had a head-phone-style jack, it worked in Cheese, but the mic cheap and sounded very crackly. So I returned it and got this. 

I appreciate you trying to help. I've been trying to get the webcam I bought to work 11 days now.](*,)

---

### Post by OKnotOK on 2008-06-19
Test Call on Skype also doesn't work. 

Please can someone help? 

You know, I've spent hour searching all over the internet for the answer to this, and it seems that this (microphones, recording, etc) is a pretty common issue for people to get ZERO response on... Its so strange.

---

