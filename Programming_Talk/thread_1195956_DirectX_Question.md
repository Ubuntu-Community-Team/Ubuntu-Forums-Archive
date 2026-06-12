---
title: "DirectX Question"
date: 2009-06-24
forum: Programming Talk
---

### Post by Swenghk on 2009-06-24
I need to know how I can use DirectX in Linux.

I use OpenGL to make the graphics for a game, but I need access to different DirectX things too, such as DirectInput or DirectSound...

Thank-you

---

### Post by milton1 on 2009-06-24
Can't. You need to find equivalent functions that are linux-native.

---

### Post by Swenghk on 2009-06-24
I can't...I NEED DirectX

Well...looks like I'm off to Windows again

---

### Post by milton1 on 2009-06-24
> **Swenghk said:**
> I can't...I NEED DirectX

why?

---

### Post by jinksys on 2009-06-24
> **Swenghk said:**
>  I need access to different DirectX things too, such as DirectInput or DirectSound...

You can't access DirectX on linux as it is a set of Windows APIs.  If you need a cross-platform way to access input, sound, and video, take a look at SDL. 

[http://www.libsdl.org/](http://www.libsdl.org/)

Also, if you come to the forum for *help*, and then we give you straight answers, don't hit us up with guilt trip. "Looks like it's back to windows."

---

### Post by shadylookin on 2009-06-24
You should consider SDL for event handling and SDL_mixer for sound. It's cross platform and integrates with opengl

in the repos their libsdl1.2-dev and libsdl-mixer1.2-dev

---

### Post by decoherence on 2009-06-24
OP had an honest question and gave an honest response. I wouldn't read too much in to it. Or do I detect a little drawing library envy? ;)

Anyway, just to confirm, MS hasn't released DX for any other systems, so if you NEED it then you need Windows. 

You could try doing whatever it is you want to do in Cedega. At least then you can use Linux for most things and use Windows for your DX stuff. That might be more trouble than it's worth for you, though. Depends on how desperate you are to get away from Windows.

---

### Post by Swenghk on 2009-06-25
I wasn't trying to send you on a guilt trip

I was saying that in a depressed way..I just came back from Windows when I figured I could learn OpenGL in my favorite OS :]

And thanks for the suggestion to SDL *happy* Looks like I'm sticking with Linux!

But...is SDL a cross-platform API?
(Well, I know its cross-platform...but do you have to change the code for another OS)

---

### Post by Zugzwang on 2009-06-25
> **Swenghk said:**
> But...is SDL a cross-platform API?
(Well, I know its cross-platform...but do you have to change the code for another OS)

SDL is no API, but rather a library that encapsulates the local native APIs into a unified, cross-platform way of accessing them.

This means that the code does not need to be changed, provided that you programmed correctly. As always with C or C++, you might make critical programming mistakes that will not have an effect on every machine. To give a SDL example, not every platform will "forget" some surfaces. So if you program on these platforms, the code might not work correctly on platforms that do sometimes forget surfaces (like Windows) if you do not do the handling correctly (or forget it).

---

### Post by Swenghk on 2009-06-25
> 
You should consider SDL for event handling and SDL_mixer for sound. It's cross platform and integrates with opengl

in the repos their libsdl1.2-dev and libsdl-mixer1.2-dev

I tried to install them, but it won't let me. I tried to install SDL before from another guide and it didn't work. Is there any way to start over?

---

### Post by shadylookin on 2009-06-25
> **Swenghk said:**
> I tried to install them, but it won't let me. I tried to install SDL before from another guide and it didn't work. Is there any way to start over?

What do you mean by it won't let you? Does it give some sort of error when you try and download them from synaptic?

Sounds like you tried to manually install them and messed up your package management. 

You might need to ask in another forum where they'll be able to help you better since I'm not really sure how to fix synaptic. when you search for libsdl1.2-dev and libsdl-mixer1.2-dev  it should look like in the picture

then once you get it you include it in your source code with

#include <SDL/SDL.h>
#include <SDL/SDL_mixer.h>

then when you go to compile and link(assuming your naming it program and the source is program.c)

gcc -oprogram program.c -lSDL -lSDL_mixer

---

