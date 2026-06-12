---
title: "[SOLVED] Sounds gone!"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-30
OK i had sound maybe 30min ago i leave to go get dinner come back and there's no sound! my speakers are connected the sound icon isn't on mute all the volume controls on the applications are up my speakers are turned on!

Please help:lolflag:

---

### Post by littletinman on 2008-05-30
try restarting. Did your computer go to sleep or anything like that?

---

### Post by Bakon Jarser on 2008-05-30
Have you already tried rebooting?  If you have and still don't have sound then try going to System > Preferences > Sound.  Set it to pulse audio and hit the test button and see if you hear any sound.  The test sound is a long continuous beep.  If not then try alsa and oss. Oh, and let's not foreget the obvious, make sure somebody didn't trip over a wire and disconnect your speakers.  Check all of your connections, including power.

---

### Post by kamitsukai on 2008-05-30
> **littletinman said:**
> try restarting. Did your computer go to sleep or anything like that?

I've rebooted 3 times everything is connected as i said above tried system -->preferences-->sound and then tested it, all i hear is a like a static noise but no sound

---

### Post by kamitsukai on 2008-05-30
Speakers are working fine on my xp partition

---

### Post by littletinman on 2008-05-30
hmmmm, this is wierd. Did you recently update?

---

### Post by kamitsukai on 2008-05-30
Ok figures it out but i still dont know what caused this to happen i went to the terminal and typed:
```
alsamixer
```

and discovered that the "PCM" was set to nil! why would this happen randomly with no interfering from me?

---

### Post by WRDN on 2008-05-30
Have a look in the /proc folder for one called /asound. Pray to God is exists.

Also, look in your System Log to see if there are any errors (System > Administration > System Log).

---

### Post by kattman on 2008-05-30
Try this , Click " system > preferances > sound Than under the default mixer track Click Master!   

It worked for me

---

### Post by kamitsukai on 2008-05-30
> **kattman said:**
> Try this , Click " system > preferances > sound Than under the default mixer track Click Master!   

It worked for me

it's fixed now, and the master is just like using the sound slider from the top taskbar...


but thanks anyway:KS

***Edit***
Hell yer! 600 hundred posts :P

---

