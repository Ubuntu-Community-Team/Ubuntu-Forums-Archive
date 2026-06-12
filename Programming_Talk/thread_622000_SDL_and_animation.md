---
title: "SDL and animation"
date: 2007-11-24
forum: Programming Talk
---

### Post by Virion on 2007-11-24
Hi, I am currently making a 2D game with SDL. I've successfully made my character to animate when walking, based on repeating key states (not based on timing) and some noobish techniques... :)
Ok my questions are:

- When I move my cursor during my character is walking, the walking speed increases! How to fix this?

- How to animation my character with timing? Any sample or tutorial?

Demo Video:
[http://www.youtube.com/watch?v=r2svu4X2BnI](http://www.youtube.com/watch?v=r2svu4X2BnI)

As you can see there, I didn't move my cursor lol.

---

### Post by geirha on 2007-11-24
It sounds like you update the position on each redraw. When you move the cursor over the window, the window will be redrawn alot of times to paint over where the cursor was previously painted. Setting the position based on time should fix that.

It was indeed hard to find a good tutorial on timing, though this seems promising: [http://albatross.dnsdojo.net/apache2-default/wiki/index.php/CPP_SDL_Timer_Examples](http://albatross.dnsdojo.net/apache2-default/wiki/index.php/CPP_SDL_Timer_Examples)

---

