---
title: "USB Audio"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by hifen on 2008-06-09
I've just switched over to ubuntu from windows, and have finally gotten everything up and running, however due to a broken headphone jack, the only way to get sound from my computer is with a usb audio device.  After switching everything to usb in the prefrence> sound tab, i still can't get audio, (with the exception of movie player).  What else do i have to do to make it so that usb is the primary and only audio output for everything (vcl, firefox, mplayer ect.)    i've also tried switching dev/dsp to dev/dsp1 in vcl, but that didn't work,   any advice would be great, since it sucks having a computer with no sound.    Oh, and i just want to say, that i know pretty much nothing about linux...

---

### Post by SunnyRabbiera on 2008-06-09
make and model of the audio device?

---

### Post by hifen on 2008-06-09
Since usb is the only way for me to get sound i do switch through a few which wasn't a problem on windows, at the moment i have altec lansing xt2 speakers and C-Media USB Headphones, i've been trying to replace everything with a 3d sound hy552 adaptor so i can just start using normal speakers.

---

### Post by SunnyRabbiera on 2008-06-09
Yes though linux is not windws.
Did you try a restart?
I cannot be all too helpful to you as I dont use a device like you do, but I at least can try to get you started.

---

### Post by hifen on 2008-06-09
yeah, i tried restarting it before, the headset works in the sound "testing" in preferences but not on firefox, or some media players (mplayer, vcl), and the adapter doesn't seem to work at all.

---

### Post by Xiong Chiamiov on 2008-06-09
Take a follow through [this guide]("http://ubuntuforums.org/showthread.php?t=205449"), then tell us where you have problems.

---

### Post by Faud on 2008-06-11
I have the same exact problem. usb headset. Sound works on the test and thru mplayer but no where else. If you get it figured out let me know. Would love to have sound on my ubuntu =)

---

### Post by hifen on 2008-06-12
i believe me sound card is an ICH6, i checked the  alsa home page as the guide said to and it was present, when i ran 

sudo modprobe snd- [tab],

        and i don't think i saw my sound card listed there, however wouldn't i most likely have a detected sound card if i was getting sound in a couple aps, such as rythm box,  and mplayer?  my usb card is a c-media, also accepted by alsa.  Again i don't know if i saw it on the list.  

   Also i don't know if this matters (since i know nothing of this), but the problems arise in vcl, tuxguitar, and firefox, so perhaps its a java problem?

---

### Post by PAFin on 2008-06-14
I am having the same problem as well.  Alsa sees both my sound card and my usb audio device.  I tried to set my usb audio device to the primary but it always defaults back to my sound card.  I have tried quite a few things but always seems to circle back to usb audio isn't very reliable.  I wish someone had a usb audio 101.

---

### Post by Modax42 on 2008-09-25
I am also having this same problem.  Is there no solution?

I have a logitech USB headset+mic and it plays sound through the headphones in everything but firefox.

Actually, firefox has sound, but it always plays through the laptop speakers when I'd rather it play through the headset.  Also, if I connect earphones through the speaker jack, I get sound through firefox there, just not USB.

---

### Post by tjk on 2008-09-29
I also have a Logitech usb headset (headphones & mic), but can't get it to work.  I've searched the web for answers but found none.  So if anyone knows how to get this working I sure would like to hear from them.

---

### Post by markbuntu on 2008-09-29
I have just added a new usb headset section to my guide here. just scroll on down to it:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

