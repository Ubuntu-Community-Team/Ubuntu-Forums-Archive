---
title: "sleep() one process and allow others? (c++)"
date: 2010-02-11
forum: Programming Talk
---

### Post by daweefolk on 2010-02-11
I'm planning a small game along the lines of a text-based warcraft/starcraft type game and i'm wondering... for building/training units would the sleep() function be best to designate the training time? and if so how could i make it so other functions could be done (like interacting with other "buildings")?

---

### Post by Zugzwang on 2010-02-11
No, in games you normally have a "main game loop" in which you constantly update the entities in your game. Stick to this idea and simply check in each loop cycle whether you are done with building.

---

### Post by daweefolk on 2010-02-11
I suppose a text-based rts game is probably a very hard, if not nearly impossible, thing to produce, huh? It's almost like i'd need "background" tasks running to update the game while the user answered prompts about what they want to do.

---

### Post by Zugzwang on 2010-02-12
> **daweefolk said:**
> I suppose a text-based rts game is probably a very hard, if not nearly impossible, thing to produce, huh? It's almost like i'd need "background" tasks running to update the game while the user answered prompts about what they want to do.

No, that's no problem! But I strongly suppose using only two threads: one for the user input and one for updating the game. In any case, you might want to look into multi-threading (unless you use non-blocking input or a event-driven GUI engine).

---

