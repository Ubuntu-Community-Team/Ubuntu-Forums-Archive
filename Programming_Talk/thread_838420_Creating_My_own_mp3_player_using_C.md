---
title: "Creating My own mp3 player using C"
date: 2008-06-23
forum: Programming Talk
---

### Post by rraj.be on 2008-06-23
I am a beginner c-software developer with good knowledge in c-programming.

This is my first project that i have undertaken.

I wish to create a very simple  mp3 player which could just play the mp3 from specific location's.

I have no idea about where to start this as i haven't yet developed some applications like this.I use to program for my study experiments alone.

I wish to learn programing Applications like this.

Can any one guide me where could i start,please.

---

### Post by Kadrus on 2008-06-23
I assume you want to make a graphical program out of it..so you will be using GTK+..
There is a member on the forum that is already creating such a project if I am not mistaken
[Link]("http://morganize.sourceforge.net/")
[GTK+ Programming]("http://library.gnome.org/devel/gtk-tutorial/stable/")
Once you learn well how to program with C-GTK+ you will be able to develop sort of apps.

---

### Post by NormR2 on 2008-06-23
Sounds like an interesting project.
Reading bytes from some source (an mp3 file) and making sounds from them will require lots of research. Or is this just a front-end for an existing mp3 player?
Good luck.

---

### Post by LaRoza on 2008-06-23
> **rraj.be said:**
> I am a beginner c-software developer with good knowledge in c-programming.

This is my first project that i have undertaken.

I wish to create a very simple  mp3 player which could just play the mp3 from specific location's.

I have no idea about where to start this as i haven't yet developed some applications like this.I use to program for my study experiments alone.

I wish to learn programing Applications like this.

Can any one guide me where could i start,please.

All you need is an audio library capable of playing that format (I would suggest a free format, instead of mp3 though).

How you play it depends on your preferences. You don't need a GUI (mplayer just just fine without one).

---

### Post by henchman on 2008-06-23
here's a useful [SDL]("http://de.wikipedia.org/wiki/Simple_DirectMedia_Layer") tutorial for your music part of it:

[http://kekkai.org/roger/sdl/mixer/index.html](http://kekkai.org/roger/sdl/mixer/index.html)

---

### Post by rraj.be on 2008-06-23
Thanks a lot for all your help.


As your opinion i am too thinking of just reading the data from an mp3 file and i want to convert it to sound.

At first i just want to design the software and i can introduce GUI later  because being a beginner i just want to make it simple at first .

What is the first step to be taken.

What are the basic modules that i should code?

Should i code my codec of my own for this?

---

### Post by LaRoza on 2008-06-23
> **rraj.be said:**
> Thanks a lot for all your help.

As your opinion i am too thinking of just reading the data from an mp3 file and i want to convert it to sound.

At first i just want to design the software and i can introduce GUI later  because being a beginner i just want to make it simple at first .

What is the first step to be taken.

What are the basic modules that i should code?

Should i code my codec of my own for this?

I just coded an example "MP3 Player" a few seconds ago (not using C, but Python and PyGame (which uses SDL)), it isn't that hard. If you are wanting to write your own codec, that is a little harder (alright, a lot harder).

If you want to make it simple, you are doing everything you can to make it hard ;) GUI's are easier to write than codecs...

I suggest checking out SDL and its modules for playing sound, and use that as the basis for this project.

---

### Post by rraj.be on 2008-06-23
> **LaRoza said:**
> I just coded an example "MP3 Player" a few seconds ago (not using C, but Python and PyGame (which uses SDL)), it isn't that hard. If you are wanting to write your own codec, that is a little harder (alright, a lot harder).



I am unknown about using already existing codecs and where to get them.

Thus i asked whether should i code codec of my own.

> 
If you want to make it simple, you are doing everything you can to make it hard ;) GUI's are easier to write than codecs...

I suggest checking out SDL and its modules for playing sound, and use that as the basis for this project.

Could you give me an example mp3 player at the most simplest level thus i can get an idea.

---

### Post by StOoZ on 2008-06-23
> **rraj.be said:**
> I am unknown about using already existing codecs and where to get them.

Thus i asked whether should i code codec of my own.



Could you give me an example mp3 player at the most simplest level thus i can get an idea.


type in the terminal : man mplayer
a player with no GUI (or a version of this player with no GUI)

---

### Post by nvteighen on 2008-06-23
Couldn't writing your MP3 **codec** be potentially illegal?

---

### Post by LaRoza on 2008-06-23
> **rraj.be said:**
> I am unknown about using already existing codecs and where to get them.

Thus i asked whether should i code codec of my own.

Could you give me an example mp3 player at the most simplest level thus i can get an idea.

[php]
#!/usr/bin/python
import pygame #uses SDL

pygame.mixer.init()
pygame.mixer.music.load(raw_input())
pygame.mixer.music.play()
[/php]

> **nvteighen said:**
> Couldn't writing your MP3 **codec** be potentially illegal?

Yes (although I just read up on it, and there are some other things involved)

---

### Post by rraj.be on 2008-06-23
> **LaRoza said:**
> [php]
#!/usr/bin/python
import pygame #uses SDL
pygame.mixer.init()
pygame.mixer.music.load(raw_input())
pygame.mixer.music.play()
[/php]


Kindly forgive me.

I have no idea about python programing.

But i hope SDL could help me to do this.

Just seeing what is SDL and how its loading sound and how can  use it in my c program.

Any opinion regarding this may too helpful.

Is it better to use SDL?

---

### Post by LaRoza on 2008-06-23
> **rraj.be said:**
> Kindly forgive me.

I have no idea about python programing.

But i hope SDL could help me to do this.

Just seeing what is SDL and how its loading sound and how can  use it in my c program.

Any opinion regarding this may too helpful.

Is it better to use SDL?

I know, it was just the example you asked for ;)

I suggest you read the documentation provided earlier (pygame uses SDL).

My wiki has links to resources on SDL and what it is.

---

### Post by sq377 on 2008-06-23
[http://www.gstreamer.net/](http://www.gstreamer.net/)
> GStreamer is a library for constructing of graphs of media-handling components. The use cases it covers range from simple Ogg/Vorbis playback, audio/video streaming to complex audio (mixing) and video (non-linear editing) processing.

Applications can take advantage of advances in codec and filter technology transparently. Developers can add new codecs and filters by writing a simple plugin with a clean, generic interface. Read more ... 

I think this is more what you are looking for.  I created a gui mp3 player a few weeks ago in c using this and gtk.  It is a bit confusing to start with, but read the documentation.

---

### Post by imdano on 2008-06-23
I was going to suggest gstreamer as well.  Thats what [Exaile](www.exaile.org) uses for its backend, and I think its of the backends Amarok supports (along with xine and a few others).

---

### Post by 3ain_2eyy on 2008-06-24
I assume that you have no business in this!
Indeed, me, I, is a representetive of teh Boss who have agreed to:
You have been BANNED to use ubuntu, linux and all it's products.
hopefully yours
admin

---

### Post by rraj.be on 2008-06-26
Ok.Now i gathered a bit idea about SDL and i decided to use SDL.

Now where should i start at first.

I think i should design my algorithm correctly?Am i right?Can any one help me with this.Please.

Beside the project i should learn something about how to create a software.

Please help me.

---

### Post by Zugzwang on 2008-06-26
> **rraj.be said:**
> 
I think i should design my algorithm correctly?

The answer to this question is quite obvious - What do you really mean by that?

I would also strongly advise against trying to write your own MP3 decoder - This will likely take a couple of months even if you are a very experienced programmer/developer *and* have the necessary scientific background. On the other hand, there's nothing wrong with using GStreamer or other suitable libraries.

Where to start? Well, if you want to stick with SDL, look at [http://icculus.org/SDL_sound/]("http://icculus.org/SDL_sound/") that page. You will find links to example applications using the SDL library for loading various file formats (including MP3). Then look at tutorials for SDL and play around with it yourself.

EDIT: [http://www.gmdsoft.de/haumann/classes/Sound/]("http://www.gmdsoft.de/haumann/classes/Sound/") here is a C++ wrapper for the library *and* a MP3 playing example.

---

### Post by nvteighen on 2008-06-26
> **Zugzwang said:**
> 
I would also strongly advise against trying to write your own MP3 decoder - This will likely take a couple of months even if you are a very experienced programmer/developer *and* have the necessary scientific background. On the other hand, there's nothing wrong with using GStreamer or other suitable libraries.


Moreover, it is highly recommended to learn how to use third-party libraries, get used to read APIs, etc. And also know what tools there are out there.

Unless you want to learn something specific from the very inside, you should not be reinventing the wheel when creating a "utility" application. For example, I'm currently reimplementing some data structures in C, for the sake of improving my knowledge on how to organize data. So, I **need** to reinvent the wheel... (because I want to build a wheel :p).

You, instead, want to open a MP3 file, play it and close it... In other works, to manage input & output without caring on the format itself. You want to build a bike, so you don't need to know how wheels are created; you just need two wheels and learn how to place them :)

---

