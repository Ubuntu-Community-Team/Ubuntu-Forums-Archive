---
title: "Music playback stops working"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by t0p on 2008-07-16
I installed Hardy yesterday, and I've discovered an unusual problem.  When my computer has been on for a few hours, I can't play any music - rhythmbox and totem both won't play music files. It's not a case of playback being silent, the apps just refuse to play the music (though there isn't any error message, they just don't play).  But if I restart the computer, the apps will then play okay.

What's going on??  And how can I fix it??

---

### Post by affouneh on 2008-07-16
Yeah I have the same problem !
could anyone tell us what to do please?

---

### Post by pedro_orange on 2008-07-16
I would imagine you are opening multiple applications that are trying to access the sound card/driver and it's not being shared correctly. 
Resulting in a process locking the sound card as it were.

I think PulseAudio is supposed to address this, but when I'm using Rhythmbox & I want to play a flash video I still have to close RB to free up the sound.

I apologize if I misunderstood your question.

---

### Post by t0p on 2008-07-16
> **pedro_orange said:**
> I would imagine you are opening multiple applications that are trying to access the sound card/driver and it's not being shared correctly. 
Resulting in a process locking the sound card as it were.


Hmmm... that *may* be what's going on... I'll have to pay attention next time it happens, to see if it is down to multiple apps not sharing the sound card properly.

---

