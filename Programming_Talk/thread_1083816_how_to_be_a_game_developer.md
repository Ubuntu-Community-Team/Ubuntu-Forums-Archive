---
title: "how to be a game developer?"
date: 2009-03-01
forum: Programming Talk
---

### Post by Shady3D on 2009-03-01
hi all, i am a computer science student and i was thinking about working as a Game Developer after i graduate (i'm in term 6).

1. what should i learn to be game developer ?
2. the resources for learning ?
3. and the tools that i can use from programming ?
4. can use Linux only for development, or in other way should i use windows to have a job as game developer ?

---

### Post by PythonPower on 2009-03-01
Well, what type of game? :P

Almost always you'll be using C++ mainly and in Linux, [OpenGL]("http://en.wikipedia.org/wiki/OpenGL") and toolkits like [SDL]("http://en.wikipedia.org/wiki/Simple_DirectMedia_Layer") are popular.

---

### Post by tneva82 on 2009-03-01
> **Shady3D said:**
> hi all, i am a computer science student and i was thinking about working as a Game Developer after i graduate (i'm in term 6).

1. what should i learn to be game developer ?
2. the resources for learning ?
3. and the tools that i can use from programming ?
4. can use Linux only for development, or in other way should i use windows to have a job as game developer ?

1) Math, math, math and some more math is going to be pretty darned handy(as I have found out several times. Got to go borrow some math books and refresh myself on them again). Obviously programming language(C/C++ probably for game programming though might be wrong).
2) gamedev.net might be worth looking. [http://nehe.gamedev.net/](http://nehe.gamedev.net/) is also handy for openGL(which is where I started openGL programming). And of course lots of coding. Code, code, code.
4) If you plan to use openGL linux is workable. Also generic programming solutions can be done. However if you plan to be professional game programmer I'm affraid windows is way to go since most of games are released there. Though windows or linux internal workings are pretty similar. It's mainly hardware where things change. Especially with 3d graphics. However with openGL and SDL you could probably get both covered with little enough modifications(atleast that's my hope as well. I'm definetly trying to avoid platform specific solutions).

---

### Post by jimi_hendrix on 2009-03-01
learn that you are dispensible!

game developement is hard because it involves so many different programming fields, and if you dont make the cut, the geek next to you is ready to take your place!

i am not discouraging you but telling you it is competative

also if you have a windows computer availible i recommend C# (if you know java C# is pretty much java, but with a few other (more?) features) and XNA, Gamedev in it is simple, so you can spend more time focusing on logic and theory than segfaults

---

### Post by Gordon Bennett on 2009-03-01
> **Shady3D said:**
> hi all, i am a computer science student and i was thinking about working as a Game Developer after i graduate (i'm in term 6).

*1. what should i learn to be game developer ?*
  *****See below
  Beginner:  C, C++, 3D/2D, Audio, input processing.
  Advanced:  GPU programming, video processing, audio processing, hardware and electronics.

*2. the resources for learning ?*
  [Gamedev]("http://www.gamedev.net/") and similar websites, books on your chosen field.

*3. and the tools that i can use from programming ?*
  Any IDE that you feel comfortable with of the big heavyweights - Microsoft, Codewarrior, Eclipse, CodeBlocks etc.

*4. can use Linux only for development, or in other way should i use windows to have a job as game developer ?*
  You can use Linux - bear in mind that most commercial games are developed in DirectX - it's not as elegant as OpenGL but historically it has offered better performance, hence its widespread use.

Generally there are two types of games companies: the huge studios where you'll disappear into programming oblivion with a relatively easy job, and the smaller studios where the more skilled usually reside, with a tougher job to do.

*****In the games industry, there's usually specialists in a particular field - the hot GPU programmer, or the talented audio engineer and so on.  Some are good writing tools for Maya plugins etc.  Take your pick!

Have a look at what you would like to do and follow it on from there.

---

### Post by Can+~ on 2009-03-01
There are two key differences while making a game:

1. When you have a [working engine]("http://en.wikipedia.org/wiki/Game_engine").
2. When you don't.

There are working engines [(Unreal Engine (Unreal Tournament, Gears of War 1, 2 ....), Source (Half-Life, Portals, Team Fortress 2), Open Sourced engines, etc.]("http://en.wikipedia.org/wiki/List_of_game_engines") All this are huge pieces of code that have world physics, audio and many other details already implemented, and it's just about tweaking to make a different game from them. When working with a engine you got 90% of the work done. So the knowledge you need is all around understanding how the engine is configured and improved (usually reading it's own documentation)

If you intend to build a full fledged game from the ground-up, you'll first have to make an engine, which requires not only knowledge of a programming language, but also a Graphic Library ([OpenGL (3D Open Source)]("http://en.wikipedia.org/wiki/OpenGL"), [Direct3d (3D Microsoft)]("http://en.wikipedia.org/wiki/Direct3D"), [SDL (2D Open Source)]("http://en.wikipedia.org/wiki/Simple_DirectMedia_Layer"), ...), and most importantly, MATH.

About resources, it depends on what do you want. If you have an engine, learn the language in which it's written (probably C++) and read it's documentation. If you don't, learn a programming language and later how to use it with a graphic library.

As python is a good starter language, you should check it and the library [pygame]("http://www.pygame.org/news.html").

---

### Post by jimi_hendrix on 2009-03-01
> **Can+~ said:**
> There are two key differences while making a game:

1. When you have a working engine.
2. When you don't.

There are working engines (Unreal Engine (Unreal Tournament, Gears of War 1, 2 ....), Source (Half-Life, Portals, Team Fortress 2), Open Sourced engines, etc. All this are huge pieces of code that have world physics, audio and many other details already implemented, and it's just about tweaking to make a different game from them. When working with a engine you got 90% of the work done. So the knowledge you need is all around understanding how the engine is configured and improved (usually reading it's own documentation)

valve is still using the source engine...they just released left 4 dead, which is basically a masked over half-life as far as i can tell.

if i recall, there is an implementation of the quake engine in java, free to use

> 
If you intend to build a full fledged game from the ground-up, you'll first have to make an engine, which requires not only knowledge of a programming language, but also a Graphic Library (OpenGL, DirectX, SDL, ...), and most importantly, MATH.

i prefer doing it this way...challanging and rewarding (and frustrating!)

you will also need to learn gimp and/or blender...or hire a local artist for your homemade games...i normally just use circles or sprites ripped from other games until it is developed enough to where i can say "ok, i need an artist, i have a good game, anyone willing to draw some sprites?"

---

### Post by Shady3D on 2009-03-01
so is there any recommended book to get me started.

---

### Post by Can+~ on 2009-03-01
> **Shady3D said:**
> so is there any recommended book to get me started.

Learn a programming language first. You can't go wrong with [python]("http://www.python.org/doc/"), but, in the end, it all boils down on what you want to do.

Check the pinned threads.

---

### Post by Shady3D on 2009-03-01
well i've learned C/C++, C# & Java, and i am learning openGL this term in C++

---

### Post by simeon87 on 2009-03-01
> **jimi_hendrix said:**
> you will also need to learn gimp and/or blender...or hire a local artist for your homemade games...i normally just use circles or sprites ripped from other games until it is developed enough to where i can say "ok, i need an artist, i have a good game, anyone willing to draw some sprites?"

Learning Gimp and Blender is not worthwhile if you want to be a game programmer. In the game business, you need to specialize to develop the required skills for the job. The content, like models, textures, are created by artists so if you want to do that, follow that track, but you're not expected to be both a programmer and an artist.

---

### Post by simeon87 on 2009-03-01
> **Can+~ said:**
> Learn a programming language first. You can't go wrong with [python]("http://www.python.org/doc/"), but, in the end, it all boils down on what you want to do.

Check the pinned threads.

Python is not the language of choice for mainstream game development so it's probably better to invest in C/C++ and to work on personal or existing projects so you can show that you have experience.

---

### Post by Can+~ on 2009-03-01
> **simeon87 said:**
> Python is not the language of choice for mainstream game development so it's probably better to invest in C/C++ and to work on personal or existing projects so you can show that you have experience.

Again, it all boils down on what the OP wants to do:

-Make a game by himself => better use a simple language.
-Be a professional developer => Learn the project's language (C++ likely).

---

### Post by Shady3D on 2009-03-01
and if i told u i already explored Photoshop and Maya

---

### Post by jimi_hendrix on 2009-03-01
also check out some games on sourceforge or browse for people looking for game developers on sourceforge

---

### Post by jimi_hendrix on 2009-03-01
> **Shady3D said:**
> and if i told u i already explored Photoshop and Maya

that beats me!

i know gimp and the basics of blender

so now can you draw up a few starship fighters for me? xD

---

### Post by simeon87 on 2009-03-01
> **Shady3D said:**
> and if i told u i already explored Photoshop and Maya

Well, every bit of knowledge helps I guess :)

---

### Post by Can+~ on 2009-03-01
> **Shady3D said:**
> and if i told u i already explored Photoshop and Maya

"Explored" could be anything.

And, no, you could do a project on your own, but it should be rather simple, otherwise you'll drive yourself crazy trying to build a game engine, models, animation, textures, sound, basic networking...

You're not a superhuman, remember that. Try to focus on doing something that works, not a mess of half-done stuff.

---

### Post by tneva82 on 2009-03-01
> **Can+~ said:**
> "Explored" could be anything.

And, no, you could do a project on your own, but it should be rather simple, otherwise you'll drive yourself crazy trying to build a game engine, models, animation, textures, sound, basic networking...

You're not a superhuman, remember that. Try to focus on doing something that works, not a mess of half-done stuff.

Yeah. Myself I won't even dream of getting my project ever "done". Atleast not without outside help. If nothing else models, animation and textures are something I'll never be able to get past mock-up(VERY simple mockups at that). But that's allright. I'm coding more of just for fun and to see what sort of development issues I run into.

---

### Post by jimi_hendrix on 2009-03-01
or....you could always impress possible employers by making a rogue clone...and having twice the features of nethack

---

### Post by jimi_hendrix on 2009-03-01
> **tneva82 said:**
> Yeah. Myself I won't even dream of getting my project ever "done". Atleast not without outside help. If nothing else models, animation and textures are something I'll never be able to get past mock-up(VERY simple mockups at that). But that's allright. I'm coding more of just for fun and to see what sort of development issues I run into.

same here...presidents day weekend in C# i wrote a mario clone, that would take a string and turn it into a level...took about 5 or 6 hours work (maybe less)...but i didnt do anything passed movement, level making, and goomba logic because it wouldnt be worth the time.

---

### Post by Gordon Bennett on 2009-03-01
I'll add in a few tips from my experiences as a games programmer:

If you want to go solo and make your own game, the world is your oyster: there's some excellent suggestions already mentioned in this thread.  You will end up learning more than if you started at a games company, but you won't have the 'deep end' reference that can give you.  You can use any tool that you want and learn at your own pace.

Most games companies are cut-throat - small development studios fare better in human terms :)  The advantage is that you get to use high-end, industry-standard apps with big budgets.  Disadvantages can be punishing 'crunch' times (usually pre-gaming-expo) and creativity that is usually put under the boot in favour of milestones.  But this is what you get paid for :P

As Can +~ mentioned, math is important for any of the two paths above: whether you are making your own game or for someone else, a problem will be presented to you like 'how do I detect the collision between this rectangle and this circle?' or 'how do I best represent my idea as a 2d or 3d scene with the tools I have?', 'how do I do Doppler sound?' and so on.

I must stress that to make a great game yourself (or with friends) you do not need millions of euros - a good, strong idea mixed in with dedication and care is enough - there are plenty of games out there which do that, a great example and a favourite of mine is the award-winning [Kiki the Nanobot]("http://kiki.sourceforge.net/"), a simple idea executed brilliantly.

By the way, if you want to keep your audience as wide as possible in terms of your own game (be it 2d/3d or whatever!), use OpenGL; for sound, use OpenAL or SDL.

---

### Post by jimi_hendrix on 2009-03-01
@Gordon

did you work for a company or just as a hobbyiest (curious)

---

### Post by Gordon Bennett on 2009-03-01
> **jimi_hendrix said:**
> @Gordon

did you work for a company or just as a hobbyiest (curious)

I worked for three companies - my first ever games job happened because I wrote my own 3D engine (before the days of consumer hardware-accelerated 3D) and the company saw it and hired me.  So at the start I was a hobbyist!

A lot of developers get into the industry this way - Portal, for example: the original game developers of [Narbacular Drop]("https://www.digipen.edu/fileadmin/website_data/gallery/game_websites/NarbacularDrop/") were hired by Valve to make it into Portal.

---

### Post by jimi_hendrix on 2009-03-01
@gordon, may i ask what company (i am a big gamer)

---

### Post by Gordon Bennett on 2009-03-01
> **jimi_hendrix said:**
> @gordon, may i ask what company (i am a big gamer)

It was long ago, see if you remember this one:

The best one I worked for was DiD (Digital Image Design), well-known for its flight simulators (F29 Retaliator, EF2000, etc and the occasional non-sims such as Robocop 3) - it was small team, completely mad and loads of fun!

This will give you an idea of how far back it was - we wrote everything in assembler to squeeze blood from humble 8Mhz CPU's with no graphics acceleration hardware... 

The other companies I am too embarassed to mention - in fact, one of them I got fired from by telling the company director that the games being produced were a pile of sh*t and it was ripping people off :P

---

### Post by jimi_hendrix on 2009-03-01
> **Gordon Bennett said:**
> It was long ago, see if you remember this one:

The other companies I am too embarassed to mention - in fact, one of them I got fired from - by telling the company director that the games being produced were a pile of sh*t and it was ripping people off :P

like 90% of the wii games out there

---

### Post by Gordon Bennett on 2009-03-01
> **jimi_hendrix said:**
> like 90% of the wii games out there

Actually, that brings me round to a little something I found out while working at the company I was fired from (for speaking my mind about their gaming sewage):
All that company did was produce endless licenses (from TV shows etc) for the NES.  It was due to the size of the market - the company was guaranteed at least 90,000 British Pounds from any trash they released.  So, even the most diabolical worst-rated game ever was assured that amount of money.

This is why sometimes the game market is saturated with crap - because of pure numbers the developers get a guaranteed return if the review sites miss the release.  Console licenses encourage this - if Sony/M$/Nintendo allow your game to be distributed on the console, the return investment is pretty much guaranteed, since more people will buy the game because of strangled release coverage - it's like restricting a supermarket shelf to only stock three types of cereal instead of ten - the three cereal producers will get a bigger share of the customer's money that way; the cereal producers/developers get the impression that they are 'special' to be allowed there, thus giving the supermarket/distributor more power over them.  Win/win for the console manufacturer.

However, in the past years there has been a resurgence of small software houses producing great games.  And independent developers too like people here ;)

---

### Post by Shady3D on 2009-03-02
thank u all for advice.

---

### Post by Can+~ on 2009-03-02
> **Gordon Bennett said:**
> This is why sometimes the game market is saturated with crap - because of pure numbers the developers get a guaranteed return if the review sites miss the release.  Console licenses encourage this - if Sony/M$/Nintendo allow your game to be distributed on the console, the return investment is pretty much guaranteed, since more people will buy the game because of strangled release coverage - it's like restricting a supermarket shelf to only stock three types of cereal instead of ten - the three cereal producers will get a bigger share of the customer's money that way; the cereal producers/developers get the impression that they are 'special' to be allowed there, thus giving the supermarket/distributor more power over them.  Win/win for the console manufacturer.

That's why the wii is getting all the crap, it's the cheapest console, the most accessible, and recently adopted the "for everyone" instead for the classical "hardcore" market. I've seen bad titles for every console, but Wii eats the biggest share from it, bunch of broken party games for casual gamers.

---

### Post by Dread Knight on 2009-03-03
I haven't really gone though all the thread's posts, but if you wish to gain some experience as game developer, i've founded a NPO a while ago and i have a small team + support from community.

Personally i'm an open source fanatic, so i use linux (kubuntu/ubuntu), blender, gimp, inkscape etc.


We're working on 2 open source game projects atm, mainly using blender 3d and it's internal game engine (logic bricks + python for programming stuff).

[www.FreezingMoon.org/forums](www.FreezingMoon.org/forums)
you can find gallery there as well as wips posted on the forums and the design documentation for both projects.

We hang on irc, mainly on Freedone server, channel #AncientBeast

Also my email is [email]dk.vali@gmail.com[/email] and i have IM contact info in my profile.


Cheers!

---

