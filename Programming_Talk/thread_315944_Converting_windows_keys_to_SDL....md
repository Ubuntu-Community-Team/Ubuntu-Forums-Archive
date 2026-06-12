---
title: "Converting windows keys to SDL..."
date: 2006-12-10
forum: Programming Talk
---

### Post by Wybiral on 2006-12-10
Hey, I'm currently porting a windows program to linux and I ran into a roadblock. I need to wrap the windows scankeys into their SDL equivalent. For most of them it is simple, VK_ESCAPE = SDLK_ESCAPE and so forth... But there are a ton of them and I dont know the SDL equivalent for each (I don't even know what half the keys are!).

Alternately, I might just wrap this program over using the SDL keys instead of the scan keys... In this case, how many SDLK keys are there??? My plan is to create an array of them and use their integer value as the index, but I cant find any documentation that shows the integer values for the keys, or how many SDLK keys there even are!

---

### Post by Wybiral on 2006-12-10
Oops... Nevermind, I found them nicely mapped out in the SDL_keysym.h file!

---

