---
title: "[SOLVED] Realtek AL60 &amp;amp; ICH6 Intel HDA"
date: 2008-07-07
forum: Philippine Team
---

### Post by Recursion_1209 on 2008-07-07
I'm using Ubuntu 8.04 on my MSI 12" laptop and was happy with the results. I didn't have much problems with the drivers. Now, I'm totally an Ubuntu convert.

I have another 14" laptop (Flextra) bought in Megamall two years ago and installed Ubuntu 8.04. However, I am having problems with the sound. It has Realtek ALC260 and ICH6 Intel HDA.

I have tried all the tutorials/how to's/fixes from a lot of forums (even here in Ubuntu forums), nothing worked. I've tried OSS4 and what I got was no speaker sound but you can hear something from the headphone jack and the sound volume was very very low.

Can someone please help me with this? I would be very willing to do another fresh install and try out new sugestions. Actually, I am too frustrated with this laptop that I am planning to reinstall Windows XP again if I cannot fix the sound volume soon.

TIA!!!

---

### Post by rjmdomingo2003 on 2008-07-07
> **Recursion_1209 said:**
> I'm using Ubuntu 8.04 on my MSI 12" laptop and was happy with the results. I didn't have much problems with the drivers. Now, I'm totally an Ubuntu convert.

I have another 14" laptop (Flextra) bought in Megamall two years ago and installed Ubuntu 8.04. However, I am having problems with the sound. It has Realtek ALC260 and ICH6 Intel HDA.

I have tried all the tutorials/how to's/fixes from a lot of forums (even here in Ubuntu forums), nothing worked. I've tried OSS4 and what I got was no speaker sound but you can hear something from the headphone jack and the sound volume was very very low.

Can someone please help me with this? I would be very willing to do another fresh install and try out new sugestions. Actually, I am too frustrated with this laptop that I am planning to reinstall Windows XP again if I cannot fix the sound volume soon.

TIA!!!
Try installing linux-386 using synaptic then reboot.

Good luck.

---

### Post by Recursion_1209 on 2008-07-07
Actually, I've tried that before. Saw it from one of the forums also. But, I didn't do it after a fresh install. I'll try to do a fresh install and install linux-386 kernel.

Thanks!

---

### Post by Recursion_1209 on 2008-07-08
Did a fresh install and installed linux-386. Still no sound. Can anyone suggest any other things that I should try?

---

### Post by rjmdomingo2003 on 2008-07-09
Maybe you can check this thread out: [http://ubuntuforums.org/showthread.php?t=205449&highlight=toshiba+A200+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=toshiba+A200+sound)

Good luck!

---

### Post by Recursion_1209 on 2008-07-09
Tried that already. Same result, no sound. I might be doing something wrong. Maybe, my other laptop is not suited for Ubuntu.

---

### Post by Recursion_1209 on 2008-07-16
Finally fixed my sound issues. Here is what I did:

1. Clean install of Ubuntu Hardy.
2. Download latest driver from realtek website (HD Audio Codec - July 11 2008).
3. Run install script. This will compile the latest driver - 1.0.16 (5.05 I think this is the version# of the driver).
4. Experimented will all the available models and worked with the below option in /etc/modprobe.d/alsa-base file.
  options snd-hda-intel model=will probe_mask=1

   I had to restart a lot of times for each model.

---

### Post by king leoric on 2008-07-16
thank you for sharing. This might help others soon

---

### Post by rjmdomingo2003 on 2008-07-16
You can mark this as SOLVED. Cheers!

---

