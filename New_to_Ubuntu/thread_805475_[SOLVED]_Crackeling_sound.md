---
title: "[SOLVED] Crackeling sound"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-05-24
When ever I try to listen to streaming audio in vlc or realplayer the audio has a lot of static.  When I listen to mpg3's in Rythembox I also get very bad static.  I am running a Sound Blaster Live sound card.  In 7.10 it worked fine with these programs.  What's Up?????

---

### Post by iaculallad on 2008-05-24
> **alienexplorers said:**
> When ever I try to listen to streaming audio in vlc or realplayer the audio has a lot of static.  When I listen to mpg3's in Rythembox I also get very bad static.  I am running a Sound Blaster Live sound card.  In 7.10 it worked fine with these programs.  What's Up?????

Just a suggestion: Did you try changing all the "AutoDetect" to "ALSA" under the Sound Preferences? (From Sound Events, Music and Movies, and Audio Conferencing)

---

### Post by alienexplorers on 2008-05-24
Yes I already have them set to ALSA.

---

### Post by FuturePilot on 2008-05-24
Looks like it might be this bug
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/190754]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/190754")
Some have reported that upgrading to the -17 kernel in Hardy Proposed fixed or at least greatly reduced the problem.

---

### Post by oldsoundguy on 2008-05-24
I had the same issues using a 5.1 surround Live Drive in Gutsy ... crackling and drop out.  Blamed everything .. but the CORD.  It WAS the cord.

---

### Post by whitethorn on 2008-05-24
I had a similar problem my sound skipped whenever I was browsing online or doing pretty much anything.  

 sudo /etc/init.d/alsa-utils reset

This did it for me

---

### Post by alienexplorers on 2008-05-24
Yes this does sound like the bug I have.  Really don't want to mess with updating the kernel in the event I screw something up.  I really do not want to reload everything again.  Once was enough.....

---

### Post by jfelpel on 2008-05-25
I was having a similar issue. All sound was very distorted or had lots of static. But after running WhiteThorn's SUDO command (sudo /etc/init.d/alsa-utils reset) everything cleared up. Sooo... thanks WhiteThorn.

hardware.
athlon x2 4400+
2 Gigs of ram
onboard Nvidia nForce3 sound
ATI X850pro vid card

:)

---

### Post by oldsoundguy on 2008-05-25
wonder if that command would restore the volume control?  That is my current issue with my 5.1 .. no volume control on the digital out feed to the amplifier.  I can control it with the amp remote, so that has not been a serious issue.

---

### Post by kattman on 2008-05-25
old sound guy?

did you try to click the master in the sound editor box, Just highlight it and close

---

### Post by oldsoundguy on 2008-05-25
nope, still no control of volume from the desktop.  No matter the feed into the mixer.

---

