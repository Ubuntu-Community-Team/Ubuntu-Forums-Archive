---
title: "I Want To Start Developing An RPG, Need Advice"
date: 2008-01-09
forum: Programming Talk
---

### Post by jlacroix on 2008-01-09
I've been wanting to develop platform-independent games for quite some time.

Right now, I develop RPG's with Game Maker, which runs on Windows. (The only two things I use Windows for is Game Maker, and Oblivion, the latter of which I can't get to work with wine or cedega, but that's another topic).

My RPG's aren't all that great (I'm trying), however I've started to really dislike the community surrounding Game Maker. For example, you could create the best game in the world with Game Maker, however if the game is over 5MB, everyone will hate you for it and flame you. If you use some of the programming tricks that some people don't like, you'll get flamed for it. If you use an included sprite, you'll be flamed for it.

What's worse than the community, is that there are currently no plans for a Linux version of Game Maker to ever be developed. They are porting it to Mac, though.

So, that means that if I continue with Game Maker, I'll have to deal with an annoying community and stick with proprietary operating systems. No thanks. I bought a C++ book and I'm going to try to learn to develop games that will compile on any platform, which leads me to assume I'll probably need to learn OpenGL at some point as well.

Sorry for the long post. I like to make shooting games and classic styled Scifi RPG's, similar to Star Ocean or Xenogears. I want to start developing 2D games, and then move my way up to 3D.

Any advice to a newbie that's very fond of C++, Ubuntu, and Role Playing Games? After I finish reading the C++ book I just bought (C++ Primer Plus 5th Edition) what book should I move on to?

---

### Post by Zugzwang on 2008-01-09
You probably want to have a look at [SDL]("http://www.libsdl.org/"), which is a set of libraries you can use for graphics & sound. They are cross-platform and quite easy to use and are therefore the de-facto standard for games.

In case you move on to 3D, OpenGL also integrates into this framework.

As you wrote that you know the language C++ quite well, you might want to look at some tutorials for SDL (with C or C++). You should also choose some nice IDE for developing. You'll find some threads about that in the forums.

---

### Post by pmasiar on 2008-01-09
I liked Game Maker, never bothered with community. 


> 
is that there are currently no plans for a Linux version of Game Maker to ever be developed.
That's why I started Game Baker , inspired by Game Maker, but based on Python and Pygame. We are not there yet, but certainly we do try! :-)

If you like to join, see link in my sig, or just msg me!

---

### Post by Lster on 2008-01-09
[QUOTE=pmasiar]That's why I started Game Baker , inspired by Game Maker, but based on Python and Pygame. We are not there yet, but certainly we do try! 

If you like to join, see link in my sig, or just msg me! [/QUOTE]

I hadn't seen that in your signature before, pmasiar. That looks really polished - I will have to check it out! :)

---

### Post by FriedChips on 2008-01-09
I would suggest joining an existing project. The problem with most FOSS games is that they tend to fizzle out when they are near completion. The original developers that wrote the code just decide 3 years is quite enough and bail. People don't like to pick up where someone left on a project like that cuz it can take quite a bit to understand just what the last dev did, but this is essential for these projects to keep making headway. Check out the planeshift game for example. This game's been in development for quite some time. They are asking for coders for the game engine and some other positions that they need the seats filled in to continue active development on the project. If these seats are not filled development will eventually stop as current developers bail as well.

I am not trying to say that you can't do it. I know that this is quite possible. Just saying that starting with or joining an existing project would get you off the ground MUCH faster, and would most likely result in a more polished RPG. I know planeshift may not be what you're looking for as it is MMO, but take a look around sourceforge at all the RPG projects there. You may just find that one of them is similar to what you are wanting to make and will require much less work than starting from scratch.

---

### Post by pmasiar on 2008-01-09
> **Lster said:**
> I hadn't seen that in your signature before, pmasiar. That looks really polished - I will have to check it out! :)

Please do, and we welcome any feedback.

I just GameBaker to my sig couple days ago.

Code is not mine but eavymetal's - I am just advisor/cheerleader. No time to code, wasting too much time on forums ;-)

Big part of it is, Python is such a productive language.

---

### Post by jlacroix on 2008-01-09
I'll probably want to start with something small like a shooter first. I would probably want to use an already coded C++ engine, is that possible? Would that make it easier?

---

### Post by FriedChips on 2008-01-09
Yes that is what I would recommend, like I said sourceforge would be a great place to start looking for a functional game engine. Using an existing game engine would take a lot of the hardest work out of the development. Writing a game engine from scratch would be quite a learning experience ( maybe even more than you're in for ;) ) and time consuming. You may even find a good project that you would feel comfortable polishing to your liking or just joining in on development for at your own pace, to get some experience before you dive into your own project head first.

---

### Post by boban on 2008-01-09
OpenGl is one option for working with 3D. But I would recommend using [OGRE]("http://ogre3d.org/") for that. Having some experience in OpenGl (& DirectX on Windows) and then moving to OGRE I think that I won't ever go back to the former.

(Maybe I will be redundant with this, but I will write it anyway) 
If you want to make a game - I think you should start with something simpler then RPG. It is very complex gender (GUI/AI/GFX/scripts/story/etc). I know that writing a tetris or mario bros clone isn't as satisfying as writing Oblivion 2 ;-), but even writing those should teach you some important skills and how game programming is different to application programming (and I'm guessing that your c++ book will teach you that). 

Another option is joining some existing project - FriedChips is right about that. 

Some links I would recommend for beginning: 
[LIST=1]
[*][GameDev.net]("http://www.gamedev.net/") - read some excelent articles from there.
[*][Nehe Open Gl Tutorials]("http://nehe.gamedev.net/") - IMHO those are the best on-line tutorials to start with opengl (if you decide to learn it anyway) 
[*][OGRE]("http://ogre3d.org/") - go to ogre's wiki from there - see the section with tutorials for beginners.
[/LIST]

---

### Post by FriedChips on 2008-01-10
[http://sourceforge.net/projects/g3d-cpp](http://sourceforge.net/projects/g3d-cpp)
check that out, looks like maybe that would be a good starting point.

---

