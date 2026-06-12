---
title: "A few questions"
date: 2007-08-20
forum: Programming Talk
---

### Post by mrobert on 2007-08-20
Hello everyone,

I am about to port one of our games to linux (Ubuntu), and decided to ask a few questions, since I am new to coding under linux.

The games uses Direct3D (for 2D graphics), and DirectSound/Music/Input for the rest. The code is pretty clean and simple, so all I need to port, is the above mentioned.

What are my options under Ubuntu for graphics/sound?

Thanks!

---

### Post by Wybiral on 2007-08-20
> **mrobert said:**
> Hello everyone,

I am about to port one of our games to linux (Ubuntu), and decided to ask a few questions, since I am new to coding under linux.

The games uses Direct3D (for 2D graphics), and DirectSound/Music/Input for the rest. The code is pretty clean and simple, so all I need to port, is the above mentioned.

What are my options under Ubuntu for graphics/sound?

Thanks!

I would definitely advise SDL and OpenGL. I'm sure you're aware that OpenGL can be used to replace most of your Direct3D needs (SDL will alone if it's simple enough 2d graphics), and SDL allows for a portable initialization of an OpenGL window as well a ton of other nifty features (events, image loading... etc).

SDL also has a lot of other helper libraries such as SDL_Mixer for sound, SDL_Image for loading lots of image files, and SDL_ttf for text rendering.

What kind of game is it?

---

### Post by mrobert on 2007-08-20
Thanks for the reply.

I am familiar with OpenGL under Win32, so this should be pretty easy.
The game is Hacker Evolution:


[http://www.exosyphen.com/page_hacker-evolution.html]("http://www.exosyphen.com/page_hacker-evolution.html")

---

### Post by Wybiral on 2007-08-20
Cool, sounds like an interesting game. Good luck with the Linux port!

If you run into any bumps, this forum is probably a good place to get answers.

---

### Post by mrobert on 2007-08-20
Thanks a lot!

---

