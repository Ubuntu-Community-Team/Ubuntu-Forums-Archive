---
title: "[SOLVED] Sound trouble"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by esedizzle on 2008-05-03
Amarak gets no sound on my computer despite the fact that i've downloaded flash

---

### Post by macaholic on 2008-05-03
What? Could you elaborate more please? What do you mean amarok gets no sound, when you are trying to play media files? Also, what does flash have to do with that?

---

### Post by esedizzle on 2008-05-03
well i run an nvidia chip amorak can't play music. when the play button is pressed no sound comes despite a progression of time into the song. Well I guess the flash is irrelevant sorry

---

### Post by macaholic on 2008-05-04
> **esedizzle said:**
> well i run an nvidia chip amorak can't play music. when the play button is pressed no sound comes despite a progression of time into the song. Well I guess the flash is irrelevant sorry
No problem, all of us were beginners once, do you ahve any sound working at all? You can test in System > Preferences > Sound. (assuming you are in Gnome)

---

### Post by esedizzle on 2008-05-04
i actually do have sound when i go onto youtube it's just for this specific program that sound will not be made

---

### Post by esedizzle on 2008-05-04
I don't receive sound support when i tested the sound playback and sound capture test

---

### Post by esedizzle on 2008-05-06
everything has tested to make sound in the sound preferences test with CA0106 except for music capture under audio conferencing

---

### Post by marty1011 on 2008-05-06
Are you using Firefox and Amarok at the same time? I also faced the same problem when I ran both programs at the same time (with youtube on firefox). Then I started to use Audacious and it works fine.

---

### Post by esedizzle on 2008-05-06
audacious doesn't work either even though you were correct i am using firefox and amarok

---

### Post by nkri on 2008-05-06
> **esedizzle said:**
> everything has tested to make sound in the sound preferences test with CA0106 except for music capture under audio conferencing

Have you checked the volume control to see if PCM is on?  To do this, right click on the little speaker icon (to the left of the date and time, by default), and click "Open Volume Control."  Are all four bars at their maximum?  If not, try moving them up and see what happens.

---

### Post by marty1011 on 2008-05-07
Try this- 
```
sudo apt-get install libxine-dev libxine1-dbg libxine1-misc-plugins
``` 
and then close firefox and restart computer. Hope this solves the problem.

---

### Post by esedizzle on 2008-05-10
i tried both of these methods and with no luck.  This time when i tried to run amorak it says something called KNotify crashed. Is that why it isn't working?

---

### Post by marty1011 on 2008-05-10
Does it say something like: **KNotify crashed while instantiating KNotify. Do you want to try again or disable aRts sound output? ** If it does then see the following posts: [http://ubuntuforums.org/showthread.php?t=637204](http://ubuntuforums.org/showthread.php?t=637204)
[http://ubuntuforums.org/showthread.php?t=550808](http://ubuntuforums.org/showthread.php?t=550808)

---

