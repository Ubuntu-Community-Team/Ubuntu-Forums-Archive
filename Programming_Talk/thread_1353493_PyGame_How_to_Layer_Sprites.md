---
title: "PyGame: How to Layer Sprites"
date: 2009-12-12
forum: Programming Talk
---

### Post by azurepancake on 2009-12-12
Hello!

I'm working on a small project using PyGame and the number of different sprites in this game are increasing. I've noticed that some sprites are layered over others. For example, in my spaceshooter, if I turn off the collision detection and my ship flies into an enemy ship, it will go behind the enemy sprite, instead of over it. I'm curious as to what governs which sprite is above others.

I tried searching for this answer, but no luck. Anyone got a clue?

Thank you!

---

### Post by sam191 on 2009-12-12
Well, when I was playing around with pygame I noticed that the blitting order had something to do with the layering. So for example, in your main game loop, if your spaceship is the last thing you blit to the screen, then it should be on the topmost layer.


I'm not sure whether this is true or not, but it worked for me. Try it out and let me know what happens.

---

### Post by azurepancake on 2009-12-12
That did it, thank you very much!

---

