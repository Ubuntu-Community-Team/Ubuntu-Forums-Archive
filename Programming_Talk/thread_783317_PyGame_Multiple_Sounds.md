---
title: "PyGame: Multiple Sounds?"
date: 2008-05-05
forum: Programming Talk
---

### Post by sekinto on 2008-05-05
Is it possible to play multiple sounds and have them overlap eachother?

```
pygame.mixer.music.load('noise')
pygame.mixer.music.play()
```

That is what I have, but if I try to load and play another sound it will stop the previous one.

---

### Post by WW on 2008-05-05
According to [this page](http://www.pygame.org/docs/ref/music.html),
> 
The mixer system only supports a single music stream at once.

Apparently you can play multiple *sounds* with the mixer, but only one music stream.  For example, the two sounds played here will play simultaneously:
```

# Initialize the mixer
pygame.mixer.init()
# Load two sounds
snd1 = pygame.mixer.Sound('sounds/bang.wav')
snd2 = pygame.mixer.Sound('sounds/zoom.wav')
# Play the sounds; these will play simultaneously
snd1.play()
snd2.play()

```

---

### Post by sekinto on 2008-05-05
-_-
That really sucks. I'm almost done with my noise dail generator and now I find out I can only play one sound at a time. I guess it will have to do.

Edit:

Wait, if you were to do:
snd1.play()
time.sleep(2)
snd2.play()

Would that 'hack' still work?

---

### Post by WW on 2008-05-05
> **sekinto said:**
> -_-
That really sucks. I'm almost done with my noise dail generator and now I find out I can only play one sound at a time. I guess it will have to do.

To be safe, I'll stick with the pygame terminology.  You *can* play more than one *sound* at a time.  But you can only have one *music stream* at a time. (*Disclaimer*: I haven't used a music stream; that last statement is based on reading the link above.)

> **sekinto said:**
> 
Edit:

Wait, if you were to do:
snd1.play()
time.sleep(2)
snd2.play()

Would that 'hack' still work?
That will start snd1 playing, and then two seconds later, start snd2.  If snd1 lasts more than two seconds, the sounds will overlap and play at the same time.

---

### Post by sekinto on 2008-05-05
Great, it works now.

---

