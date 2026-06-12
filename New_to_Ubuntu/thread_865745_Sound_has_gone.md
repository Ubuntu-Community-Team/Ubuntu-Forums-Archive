---
title: "Sound has gone"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by caoimhe23 on 2008-07-20
Hey guys, had ubuntu for a few months, have been loving it, until today my sound no longer works (got update 2 days ago not been working since)

Gone through everything i can think of, nothing is on mute. I have searched on the forums and done what others have suggested but it just isn't working.

I have an acer laptop if that helps

---

### Post by iaculallad on 2008-07-20
> **caoimhe23 said:**
> Hey guys, had ubuntu for a few months, have been loving it, until today my sound no longer works (got update 2 days ago not been working since)

Gone through everything i can think of, nothing is on mute. I have searched on the forums and done what others have suggested but it just isn't working.

I have an acer laptop if that helps

Install the linux-generic header file:

```
sudo aptitude install linux-generic
```

---

### Post by caoimhe23 on 2008-07-20
that means nothing to me, can you put a few steps in as to how i can get this header file??

cheers

---

### Post by sydbat on 2008-07-21
Applications > Accessories > Terminal...copy and paste the code above...it will ask your password, type it (it will not show)...the rest is automatic.

---

### Post by caoimhe23 on 2008-07-21
cheers for that, it worked but still no sound coming through

---

### Post by Squid Tamer on 2008-07-21
This sounds REALLY STUPID, but it happened to me and I was able to help another guy who had the same problem.

Make sure your speakers are plugged in/in the right port. I doubt that's what happened to you, but just in case.

---

### Post by caoimhe23 on 2008-07-21
my speakers are built into the laptop so unfortunately that is not the problem, if only it was that simple. All the boxes under preferences in the sound are ticked and none are muted, but nothing is coming through, i had perfect sound, until last night i noticed on pidgin that they sounds weren't coming through, and i had just done an update of the system the day before. So i am a bit inexperienced in this sort of area.

---

### Post by iaculallad on 2008-07-21
> **caoimhe23 said:**
> cheers for that, it worked but still no sound coming through

Had you tried to logout of your account then log back in? Then try to retest your audio.

---

### Post by fuzzyk.k on 2008-07-21
try changing the sound driver on your music player to an alternate one

---

### Post by caoimhe23 on 2008-07-21
restarting my computer worked, dont know why but it did, cheers for all your guys help :)

---

