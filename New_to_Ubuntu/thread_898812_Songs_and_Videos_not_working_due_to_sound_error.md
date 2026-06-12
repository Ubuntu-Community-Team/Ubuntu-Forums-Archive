---
title: "Songs and Videos not working due to sound error"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Ketson on 2008-08-23
All of a sudden my music and videos wont play due to a sound error i believe i have ran totem through the terminal and this is the response i get.

> ketson@ketson-laptop:~$ totem
** Message: Error: Failed to connect stream: Invalid argument
pulsesink.c(411): gst_pulsesink_prepare (): /play/abin/audiosinkbin/audio-sink/bin6/autoaudiosink1/autoaudiosink1-actual-sink-pulse


---

### Post by nitro_n2o on 2008-08-23
did you remove alsa or something by mistake.. like when you update the system it might say "those package will be REMOVED" you should watch out for these 

check that you still have alsmixer by typing 
alsamixer 
in the terminal 

also to see if the sound working and it is not a "totem" problem type 
speaker-test 
in the terminal, you should hear some noise

---

### Post by Ketson on 2008-08-23
both of these are coming up with positive results the sound test came up with white noise and alsamixer had 100/100 for Master and PCM and 0/100 for the other 3 im assuming that that is correct. I have reinstalled both totem and rhythmbox with no change. Any other suggestions?

---

### Post by Ketson on 2008-08-23
have just found that videos are working with VLC player with sound but are running fast the same with mplayer, although mplayer is giving an error warning at the start. is there anyone that has had this problem or knows what to do?

---

### Post by tipiglen on 2008-08-29
I'm having the same problem, but only with sound.  Videos seem OK, though one particular mpeg (from an email attachment) is frame-by-frame slow...

I'll get back here if I find a fix

Salaam/Shalom/Shanthi/Dorood/Peace
   Namaste  -ed

---

### Post by tipiglen on 2008-08-29
The problem disappears if I reboot into the previous version of the kernel

See this thread:
[http://ubuntuforums.org/showthread.php?t=865253&highlight=invalid+argument+sound](http://ubuntuforums.org/showthread.php?t=865253&highlight=invalid+argument+sound)

Good luck
ed

---

