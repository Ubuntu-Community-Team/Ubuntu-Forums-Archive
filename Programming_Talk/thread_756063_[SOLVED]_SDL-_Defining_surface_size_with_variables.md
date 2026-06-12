---
title: "[SOLVED] SDL- Defining surface size with variables?"
date: 2008-04-15
forum: Programming Talk
---

### Post by Zeotronic on 2008-04-15
C++: I have been working on a game for several months now... I wouln't get too much into it, but at one point I use SDL_CreateRGBSurface to create a surface, and then later apply that surface to the screen, however when I do this it crashes... one thing I have noticed is that when I use variables to define it's width and height it crashes, however, when I just put in some numbers myself, it works fine. (though admittedly, it appears black, and my code should have put some text on it as far as I can tell)

Specifically, I create a surface, create another surface, apply the new surface onto the old surface, and then apply the old surface onto the screen... but as I said, it crashes when I use variables to define the dimensions of the old surface.

Does anyone know if I shouldn't use variables to declare the dimensions of the surface? I don't change the variables during the lifetime of the surface mind you.

---

