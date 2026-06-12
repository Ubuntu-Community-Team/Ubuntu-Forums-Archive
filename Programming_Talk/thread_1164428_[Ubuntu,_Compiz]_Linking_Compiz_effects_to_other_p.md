---
title: "[Ubuntu, Compiz] Linking Compiz effects to other programs"
date: 2009-05-19
forum: Programming Talk
---

### Post by shivkrish22 on 2009-05-19
I just had this idea, and am not sure if its been done or not. Would it be possible to link the Compiz effects like the water ripples or fire effect to other programs,maybe like a visualization for audio where they are fired up to the beat of the music. I'm not very experienced with programming on linux but would like to give something like this a try. Im not sure where to start though.

---

### Post by nvteighen on 2009-05-19
> **shivkrish22 said:**
> I just had this idea, and am not sure if its been done or not. Would it be possible to link the Compiz effects like the water ripples or fire effect to other programs,maybe like a visualization for audio where they are fired up to the beat of the music. I'm not very experienced with programming on linux but would like to give something like this a try. Im not sure where to start though.
What do you mean by linking? If you mean to take an effect and apply it inside a different program for something else... well, it's quite probable that you'll have to code it by yourself: Compiz is a window manager and it's code is meant for that job... It's not actually a general graphics framework as SDL...

---

### Post by shivkrish22 on 2009-05-19
well what i meant was something like this: (found that thread just after i posted here) 
[http://forum.compiz-fusion.org/showthread.php?t=2191](http://forum.compiz-fusion.org/showthread.php?t=2191)

but instead as a plugin(e.g for a media player). a way for the applications to "talk" to compiz and trigger events based on the output from the application. hope i'm a bit more coherant now. I'm just looking for a starting point to try something like this.

---

### Post by nvteighen on 2009-05-20
Ah, I see... Isn't there an Compiz API you can use?

---

### Post by shivkrish22 on 2009-05-21
I assumed there would be. But haven't managed to find any documentation on it yet.

---

