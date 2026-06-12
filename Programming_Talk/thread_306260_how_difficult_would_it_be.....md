---
title: "how difficult would it be...."
date: 2006-11-24
forum: Programming Talk
---

### Post by Choad on 2006-11-24
to make something similar to game maker for linux

[www.gamemaker.nl](www.gamemaker.nl)

i always loved that thing, its what got me in to programming. 

i was thinking about it, and i reckon something similar altho at the same time very different wouldnt be too hard to make.

im thinking c++ code, none of this interpreted ****, and the program creates the template of a graphical program in c++ (basically a game engine) with the ability to add objects, and a built in framework for various "events" such as a tick event for every step, and creation/ destruction event and a draw event. the program then compiles this in to a c++ project, generates a makefile and boom, you're good to go. the program just slaps in some generic code for handling of these basic events, that would be useful for any game, be it 2d or 3d

none of the handling of resources, no "paths" or even rooms or any of that crap, just plenty of built in functions to let the user do their own thing and load in resources easily. probably based on SDL/openGL

this would be alot LOT more low level than game maker, but also alot more flexible. for example, you could add in any module you liked manually, you could do anything at all.



my skills are not up to this, i couldnt even make a game, let alone a game maker, but im thinking if someone wrote a generic enough engine, its really just a matter of cutting and pasting bits of code together to create the final product, and all this program does is manage the fragments of code, possibly with a nice inteli-sense auto complete thing.

these are just my ramblings tho lol

any comments?

reading through my post, this kinda comes down to a "game engine meets IDE" type scenario

---

### Post by po0f on 2006-11-24
Choad,

I don't know if it's really what you're looking for, but there is [something similar](http://roguelike-eng.sourceforge.net/) for Java.

---

### Post by Choad on 2006-11-24
> **po0f said:**
> Choad,

I don't know if it's really what you're looking for, but there is [something similar](http://roguelike-eng.sourceforge.net/) for Java.
ew java

not a fan tbh

interesting tho

---

