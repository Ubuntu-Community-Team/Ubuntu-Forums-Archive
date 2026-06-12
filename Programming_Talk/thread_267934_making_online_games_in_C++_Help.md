---
title: "making online games in C++? Help"
date: 2006-09-29
forum: Programming Talk
---

### Post by madsravn on 2006-09-29
Hey.

I'm new to linux and new to C++, but I have some ideas for what I want to do... I have a server here at home, and I would like to do an online game on it. But can C++ some way be accessed from a web-site? I'd like to make a game similar to ogame.org (not the idea, but the programming thingy)... Any ideas?

If this is not possible, what can you recommend for other online programming games? Or other linux c++ games? I'd just like to do some linux c++ programming, if anything else is impossible...

 - madsravn

---

### Post by Ayman on 2006-09-29
It's possible to program online games in C++, I recommend using SDL for graphics and networking.
SDL Home: [http://www.libsdl.org/](http://www.libsdl.org/)
SDL_net: [http://www.libsdl.org/projects/SDL_net/](http://www.libsdl.org/projects/SDL_net/)
Excellent starter: [http://lazyfooproductions.com/SDL_tutorials/index.php](http://lazyfooproductions.com/SDL_tutorials/index.php)

Another possibility for game programming is PyGame, the library is a Python wrapper around SDL, it's very easy and productive at the same time, I highly recommend it if you are into Python.
[http://www.pygame.org/news.html](http://www.pygame.org/news.html)

---

### Post by po0f on 2006-09-29
madsravn,

If you're new to C++ and Linux in general, an online game is not the best first project to start off with.  Follow some online tutorials for C++, [read a couple of books](http://mindview.net/Books/TICPP/ThinkingInCPP2e.html) (these aren't the only ones suggested, but they contain good general C++ knowledge for any programming), and try some very basic projects, just to get started.

A game in general, and a networked one specifically, are kind of advanced.  I would be terrified with such a task.  I'm still a newb when it comes to programming myself, so I hope you don't feel like I'm just telling some newb they can't do it.  I can't do it myself!

I think it's a good thing that you want to code, but have seen many beginners try to start too ambitious of a project and give up when they haven't even started.  Build you skills up until you're confident enough that you can complete a project before you start (wanting to complete a project and being confident that you can complete one are two different things ;) ).

Stick to your guns, and come back here if you need any help!

---

### Post by madsravn on 2006-09-30
Hey,

thanks for your time. Although I didn't mean actual networked games, I liked the links ;) I was talking more about games on a webserver. I know it's a strange idea, but something got me thinking about it. But can I make a web-based game with the core of the game being a C++ programmed file? If the web-server is my own... Keep it coming ;)

---

### Post by Ayman on 2006-09-30
If it's a web-based game then a scripting language like PHP or Python would be much easier and faster, unless this particular web game requires high performance (which I really doubt), using C++ is an overkill.

Even if the game requires some high performance operations, it's recommended to write a PHP or Python module for these operations in C++, instead of writing everything in C++.

---

### Post by po0f on 2006-09-30
madsravn,

Sorry for the assumption, I thought you meant a networked game, not a web-based game.

So you want the client software to be a compatible browser and that's it?  C++ would be good for the backend, but now you need to think about how you present the information to the client/player.  PHP would probably be good for this aspect of the game.

---

### Post by madsravn on 2006-10-01
But how would you make a page which has a C++ thingy as a backend? I'd really like to know how to include some c++ into some web-paging.. Thanks for the links up till now - I like them ;)

---

