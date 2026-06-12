---
title: "2D Programming in Python 3"
date: 2012-05-11
forum: Programming Talk
---

### Post by Carpentr on 2012-05-11
Hi everyone,

I am doing some research for a project I would like to complete over the summer. I have chosen to use Python because I feel I will be able to get the most accomplished within the next few months.

My problem is, that I have chosen Python 3 and not Python 2 as my language of choice. I found 'Pygame' for 2D programming, but not all features are supported for Python 3. Do any of you have any viable options to suggest in regards to Python 3 Game Development in 2D? I'm not looking to do anything too complicated. I am looking to create a very simple platformer. 

If all else fails, I am thinking of using C++, as I have several books from college lying around. But, I would really prefer to use Python 3 if I could. I am exploring my options for the next few days before I get started.

Thank you for taking the time to read this.

---

### Post by memilanuk on 2012-05-11
Its entirely possible to use (most of) the coding styles from Python 3.x while using Python 2.6 or 2.7.  That way you will be able to use more libraries that are available to you in 2.x, but have fairly little code to re-write for Python 3 down the road.

---

### Post by gnuman on 2012-05-11
> **Carpentr said:**
> ....My problem is, that I have chosen Python 3 and not Python 2 as my language of choice....

Oh my--some would say you summed it all up right there  :-$:shock:=;


Seriously, you can install more than one Python version with little problems.  You can launch a particular version by attaching the version number to the command.

According to this, though, Pygame is almost ready for Python 3:  

[http://www.pygame.org/wiki/FrequentlyAskedQuestions#Does%20Pygame%20work%20with%20Python%203?]("http://www.pygame.org/wiki/FrequentlyAskedQuestions#Does%20Pygame%20work%20with%20Python%203?")

---

### Post by juancarlospaco on 2012-05-11
> **Carpentr said:**
> 
Do any of you have any viable options to suggest in regards to Python 3 Game Development in 2D?

Blender ( [http://www.blender.org](http://www.blender.org) )
Pilas-Engine ( [http://pilas-engine.com.ar](http://pilas-engine.com.ar) )

---

### Post by Carpentr on 2012-05-11
Thank you all for the suggestions. I will read into them all. It is appreciated!

---

### Post by LemursDontExist on 2012-05-11
Check out [cairo]("http://cairographics.org/pycairo/").

It's not exactly focused on game development, but is an excellent 2D graphics library use extensively alongside gtk, and it has python 3 bindings.  I would discourage you from using PyGame, for serious projects you'll run into technical limitations, and for simple projects, it's honestly not that easy to learn.  I would instead choose separate graphics and audio libraries and go from there.

---

### Post by forrestcupp on 2012-05-11
> **Carpentr said:**
> 
If all else fails, I am thinking of using C++, as I have several books from college lying around. But, I would really prefer to use Python 3 if I could. I am exploring my options for the next few days before I get started.

If you end up going with C++, check out [SFML](http://www.sfml-dev.org/). It's very powerful, hardware accelerated, and very simple to use. It also has built in libraries for audio, input, and networking.

---

### Post by Carpentr on 2012-05-12
Great suggestions. Cairo seems promising, as does SMFL. The libraries for networking could come in handy. Maybe I could add simple multiplayer functionality if I work really hard in the coming months. 

I've leaning toward C++ now. I've heard it is used in the industry a lot and a lot of the internships at my college are looking for C++ and .Net developers. I have a reasonable amount of experience with VB.Net, so working in C++ wouldn't hurt (experience wise). I suppose a good amount of the C++ experience I learn from this project could be applied to VS C++ .Net when my internship comes.

If anyone has any more suggestions for Python or C++ 2D programming, I'd be glad to hear them!

Thanks for all the tips!

Edit: Oh, it seems SFML is also usable in VB.net. This project could also benefit me if I ever need to work with SFML in VB. That could be useful!

---

### Post by forrestcupp on 2012-05-12
> **Carpentr said:**
> 
Edit: Oh, it seems SFML is also usable in VB.net. This project could also benefit me if I ever need to work with SFML in VB. That could be useful!

I've used SFML, and if you can learn either C++ or a language that it has bindings for, then you definitely won't be disappointed. It's extremely easy to use, and it can do a lot. 

I would suggest learning C++, though, because it's quick, powerful, and it would be useful for a lot of things. C++ will get you a lot farther in the programming world than Python will. There's really no need at all to learn the winAPI side of Visual C++. It's a pain in the backside, unportable, and you don't really need it. Just learn the basic C++ syntax, and you'll be fine to go ahead and start learning the API for SFML, wxWidgets, or anything else that uses C++. [Here's a good web site](http://www.cplusplus.com/doc/tutorial/) that teaches C++ syntax, if you're interested.

---

### Post by gnuman on 2012-05-13
[Pyglet]("http://www.pyglet.org/") is pretty nice.

---

### Post by Carpentr on 2012-05-14
> **forrestcupp said:**
> I've used SFML, and if you can learn either C++ or a language that it has bindings for, then you definitely won't be disappointed. It's extremely easy to use, and it can do a lot. 

I would suggest learning C++, though, because it's quick, powerful, and it would be useful for a lot of things. C++ will get you a lot farther in the programming world than Python will. There's really no need at all to learn the winAPI side of Visual C++. It's a pain in the backside, unportable, and you don't really need it. Just learn the basic C++ syntax, and you'll be fine to go ahead and start learning the API for SFML, wxWidgets, or anything else that uses C++. [Here's a good web site](http://www.cplusplus.com/doc/tutorial/) that teaches C++ syntax, if you're interested.

I have decided to use SFML and C++. I've been reading up  the tutorials and whatnot. I really like how easy it is to create a window and add images, sprites, etc. Luckily, I have taken a semester of C++ this year and have a reasonable understanding of the basics. We left off at pointers (I think?). I still have my book though, and I've started reading the parts we did not cover. Thanks for the link, it will be a good refresher at the very least.

---

