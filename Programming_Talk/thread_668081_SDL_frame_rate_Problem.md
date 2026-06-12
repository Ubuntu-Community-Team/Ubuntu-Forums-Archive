---
title: "SDL frame rate Problem"
date: 2008-01-15
forum: Programming Talk
---

### Post by Decinoge on 2008-01-15
Hi Ubuntu forums, my name is Telmo Rocha but you can call me Deci as many of my friend do. I'm from Portugal.
I'm a kinda fresh Ubuntu user, and very happy till now.

So the situation is this:
I'm making a video game as part of my master degree's final project. The video game is supposed to be for Playstation Portable (a little homebrew) but i want more, and i want it cross platform.
For that purpose I've decided to program my game in C++ (which I had to learn but I'm coming out fine), using the SDL libraries for the media work.
Everything is going a bit slow, but still stable. I was developing in Windows till much recently, but when I grabbed Ubuntu I found out that I wanted to develop under this system. Specially because i was using Linux based tools on windows to make my work (Dev-C++ and Cygwin for PSP SDK).

However, when i got to Ubuntu, i run to a problem that i didn't had on Windows. I've been sniffing around the internet, and this seemed to be the best place were to ask for help. I saw many active members supporting and discussing about SDL on these threads.
My frame rate is fluctuating and low comparing to what i supposedly want it to be. I've learned there is no Hardware Acceleration on SDL under Ubuntu. But still that shouldn't be the problem since it is a simple 2D game, and my machine is more than enough for this kind of work.

Yet i have no idea if the problem is with the code, or my nVidia drivers configuration. The thing is that i want a 60 frame per second rate (which i was able to get on windows and on my PSP) but on Ubuntu i get frame rates of 42 to 58, constantly changing.

I've made my code available [[COLOR="Red"]here[/COLOR]]("http://redwater.sonance.net/proll/pr.tar.gz") so that anyone can watch it.
_[silly edit] Stupid me... on the services.cpp file, on the line 240 (inside the DisplayService::fps() function) you have to uncomment that line with SDL_Delay. Otherwise there wont be frame rate control. sorry for the sillyness._
I'm using Code::Blocks, so I am sorry for not having a makefile for the compilation (and I've never even made one... that's how n00b I am).
If you want to compile, this application uses SDL, SDL_image, and SDL_mixer. It also needs a -D_noPSP_ tag so it won't compile for PSP.

I hope i get some help in here, as this subject became a great disappointment.
I'm also having problems setting my PSPSDK right, but that's probably a subject for some other thread on some other forum.

Anyway, I feel like in this first post i should thank the Ubuntu team/s for all their hard work, and everyone that might spend some or their time reading this.

---

### Post by hod139 on 2008-01-15
It looks like you found a solution to your problem, but I'll also add this: [sdl_gfx]("http://www.ferzkopp.net/joomla/content/view/19/14/") gives you more framerate control than just plain SDL.

---

### Post by Decinoge on 2008-01-15
No, i haven't find the solution. The problem is with with that SDL_Delay, that using the same way it is used on the "lazy foo" tutorials, i get fluctuating frame rates. Too much fluctuating. For example:

I have a int that on the beginning of the program i have an int called FRAME_INTERVAL that is assigned as 1000 / FRAME_PER_SECOND, being the FRAME_PER_SECOND a pre processor #define as 60. 
FRAME_INTERVAL gets as being 16 (truncating from int division).
Then of course, with SDL_GetTicks() at the beginning and end of a frame i calculate the processing time in milliseconds, and do the obvious math to define the waiting time in milliseconds.

The result is however very unstable. This same code used to give me some rock steady 60fps with some slight fluctuation to a possible 62fps that passed without notice.

I'm starting to believe this is not a code related problem, because i've been trying different sets of flags on the SDL_SetVideoMode().
with this set:
SDL_SWSURFACE | SDL_ASYNCBLIT | SDL_DOUBLEBUF | SDL_ANYFORMAT | SDL_SRCALPHA
and no frame delay i get around 500fps. however, every 1.5 seconds the game freezes for about 1 second.

SDL_gfx might be a possible solution but i would like to leave it as a last resort since i wouldn't want to add it to my PSP version. Also, it shouldn't be needed since this code _does_ it's business... i just don's know why it is not working under linux.

Anyway, thanks for your help, it is much appreciated.

---

