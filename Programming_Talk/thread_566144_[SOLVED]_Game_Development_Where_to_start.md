---
title: "[SOLVED] Game Development: Where to start?"
date: 2007-10-03
forum: Programming Talk
---

### Post by Circus-Killer on 2007-10-03
Hi there.

I'm a web developer straight out of college. I've only got basic programming skills. Can make decent standard applications, but that's about it. What I want to do is try my hands at more hectic programming, more specifically, gaming.

I was wondering if anyone could point me in the right direction of where to start. What languages should I learn? Are there tools to make game development easier? I have no doubt that once i get started, it will build up like an avalanche. the problem is the getting started. I have no idea where to start. Suggestions?

---

### Post by Wybiral on 2007-10-03
PyGame is good for beginners. It's basically a Python wrapping for SDL and OpenGL but it makes developing small games really easy. Since it uses the SDL+OpenGL combination, you can also do 2d or 3d.

[http://pygame.org/news.html](http://pygame.org/news.html)

---

### Post by Soybean on 2007-10-03
Depending on what you've got in mind, it may also help to have a basic undestanding of C and C++ code. There are lots of examples out there in those languages, so it might help the learning process if you can follow them.

But like Wybiral says, Python and PyGame are likely the best starting point for doing your own game development. :)

---

### Post by pmasiar on 2007-10-03
Learn python first - see wiki in my sig. Start with command-line programs, then solve puzzles on pythonchallenge website. Then you will be ready for Pygame. They have plenty of games with source code, you can learn from that.

I have one project in mind to make creating games even simpler than Pygame, if you are interested (and after done with pythonchallenge), contact me.

---

### Post by YoG%*@ on 2007-10-03
hi there,

> **Circus-Killer said:**
> Hi there.

I was wondering if anyone could point me in the right direction of where to start. What languages should I learn? Are there tools to make game development easier? I have no doubt that once i get started, it will build up like an avalanche. the problem is the getting started. I have no idea where to start. Suggestions?


as the others already suggested, you might want to consider learning c++, as it is probably best suited for developing games/graphic engines/etc...

the nehe tutorials are an awesome resource for everything game programming related:
[http://nehe.gamedev.net/](http://nehe.gamedev.net/)

hth, have fun programming!
mux

---

### Post by hockey97 on 2007-10-03
I suggest to learn, c-script and c++, their are lot's of people that can help you their, since it's a popular lang.  
once you got a good grip on c++ then I suggest to learn more of gaming concepts, like using direct x or open gl , I also suggest to learn graphic programming, which is what direct x and opengl is really.
that's my opinion,  becuse you then can have much control on the overall of the game, otherwise you won't have control on the graphics,
of the game.

basically to make a game, you need to know programming and programming concepts, like AI, artificial intelligences,  and also graphics, you don't have to learn graphics, but I recommend it if you plan on selling games, it will let you have more control of how the game looks.

now if you planning just to make a application game learn c++, if you plan on making web games, then I would say try to learn flash or java, or python, I mostly think python would be great,

I am not fully sure if python can make web games, put I think it can, since I have a plug-in for apache web server to use python scripts.

it depends on what you really want to do, when you first are starting off you have to have goals.

what do you plan to do, make a game and try to sell it or just food for thought.

if you want to be able to sell games, you have a long way's to go ,
lot's to learn,   

also if you plan to make games by yourself from ground up and try to sell it , you would need to know how to 3d model, need artistic skills, programming skills, and musician skills and sound engineering.

what I mean is if you want to sell the game, you need to make every aspect of the game yourself or you can pay some people to make sound effects and music, but to me I think it's pricey. 

so if your goal is to make a commercial game and sell it,

I would first start out learning programming, c-script, then in c++

once you got a good handle on it, then start making simple 3d models, I use blender a 3d modeling software thats free.
then with the simple 3d models just try to practice  coding a small game, get a good handle on putting a menu and a game concept 
together, and make  small game, use some free sound effects from the internet, try doing simple Ai

once you done that and make your first complete, game then I suggest, to learn graphics programming, and try to make your own 3d game engine, trust me if you learn that you can then be god, lol 
like your imagination is your limitation...  because direct x and opengl
is really graphics programming but it's done already for you, you just plug, in functions from those api

graphics programming is hard lot's of math, like also caulk and trig.

that is the only way to master game making, otherwise you rely on programs, which can be a weakness in the game.

that's if you plan after learning lot's of stuff about games, you want to be able to produce a game to sell.

otherwise if you don't want to sell games, but just want to see what game making is all about,  then just learn c-script and c++,
and some 3d modeling, and some game concepts like ai,
sprites.

you can make games in c-script, but heard that c++ gives you more control over the game.

if you don't want to code the game yourself like make the game from bottom to top,  then use game engines, 
pygame is a game engine for python,  you use python  to script your game using pygame's functions, which all graphics's sound, animation,inputs devices ect, is done for you, you just have to plug-in the functions to you script.

so start by learning c-script.


hope this helps, in some way.

---

### Post by pmasiar on 2007-10-03
> **hockey97 said:**
> I am not fully sure if python can make web games, put I think it can, since I have a plug-in for apache web server to use pythong scripts.

It does, of course: twisted is one of frameworks to create sophisticated web apps, including games. Eve Online and GalCon are examples of online games created in Python.

In Python, you can any time write C libraries for stuff you need to happen fast - there is just no reason to write EVERYTHING in C if you can write in C only 5% of code which you PROFILED and TESTED and know positively it needs the speed. Why to write AI in C, if you can do it 20 times faster and simpler in Python?

---

### Post by Wybiral on 2007-10-03
> **hockey97 said:**
> I suggest to learn, c-script and c++, their are lot's of people that can help you their, since it's a popular lang.

You have to learn two new languages just to write some simple games? C-Script?

> **hockey97 said:**
> once you got a good grip on c++ then I suggest to learn more of gaming concepts, like using direct x or open gl , I also suggest to learn graphic programming, which is what direct x and opengl is really.

I wouldn't bother with Direct3d (it's MS specific and doesn't really offer anything over OpenGL, aside from being locked into the Windows platform).

> **hockey97 said:**
> I am not fully sure if python can make web games, put I think it can, since I have a plug-in for apache web server to use pythong scripts.

Browsers do not have Python built-in, so it can't be used for a game. It would be cool... But so far I don't think it's ever been done (browser embedded Python). Unless you mean "online" games as-in "networked/multi player". Then yeah, Python has a number of libraries for that (but I'm not sure what Apache has to do with it).

> **hockey97 said:**
> once you got a good handle on it, then start making simple 3d models, I use blender a 3d modeling software thats free.
then with the siimple 3d models just try to pratics codeing a small game, get a good handle on putting a menu and a game concept 
together, and make  small game, use some free sound effects from the internet, try doing simple Ai

That's a lot to do at once. I would start with some simple 2d games, AI isn't a big deal for basic games (you may want to learn A* and basic state machines, but write a simple game before worrying about all this). Start with pong, then space invaders.

> **hockey97 said:**
> once you done that and make your first complete, game then I suggest, to learn graphics programming, and try to make your own 3d game engine, trust me if you learn that you can then be god, lol 
like your imagination is your limitation...  becuse direct x and opengl
is really graphics programming but it's done already for you, you just plug, in functions from those 3d engines.

OpenGL and Direct3d (DirectX and OpenGL aren't even on the same page, I assume you mean Direct3d) are just 3d api's, not engines. There are tons of good free engines out there. If you plan on making a 3d game, use one of those... Writing engines is for engine writers, not game makers.

> **hockey97 said:**
> graphics programming is hard lot's of math, like also calk and trig.

I looked up the definition of "calk" and got:
> A pointed extension on the toe or heels of a horseshoe, designed to prevent slipping.
I don't see how that will help the OP with writing games. If you mean "calculus" and "trigonometry" then you should know that you actually don't need to know much about either to write a game. You do to write a game ENGINE, but those are two different areas of programming. Game writer != game engine programmer.

> **hockey97 said:**
> that is the only way to master game making, otherwise you rely on programs, which can be a weakness in the game.

Even professional game developers use premade engines. They usually buy them (or buy the rights to use them). Like I said, there is a difference between games, engines, and graphics... It's not all the same.

> **hockey97 said:**
> if you don't want to code the game yourself like make the game from bottom to top,  then use game engines, 
pygame is a game engine for pythong,  you use python  to script your game using pygame's functions, which all grapic's sound, animation,inputs devices ect, is done for you, you just have to plug-in the functions to you script.

so start by learning c-script.


1. PyGame is not a game engine. It's a graphics/multimedia API.
2. WTF is pythong and grapic's?
3. If pythong is so easy and fully functional, why start by learning c-script? Why not start with pythong? (Or better yet, try Python instead).

---

### Post by kknd on 2007-10-03
Choose a programming language and learn it very well. Master data structures, and them pick a game framework.

The ones that I recommend:

- Pygame, if you like Python;
- Ogre, if you like C++ (have other bindings too);
- jMonkeyEngine, if you like Java;

I'm using now jMonkeyEngine, and I like it.

---

### Post by Vox754 on 2007-10-04
> **hockey97 said:**
> 
hope this helps, in some way.

It does help. It is very funny. (pythong!)

And, Wybiral, don't be so hard. Let it be. Else I'll ask you to comment on every single grammatical error in pmasiar's posts.

---

### Post by Wybiral on 2007-10-04
> **Vox754 said:**
> It does help. It is very funny. (pythong!)

And, Wybiral, don't be so hard. Let it be. Else I'll ask you to comment on every single grammatic error in pmasiar's posts.

I was just teasing about the spelling errors, there was actually a point to the rest. I don't think I'm THAT mean, it's just my sense of humor :)

I would especially understand if they don't natively speak English, but if they do... Then I don't think I was being hard enough, lol. Spell check is a mighty tool when you're trying to actually make a point. If people are going to have trouble reading it, don't bother writing it. It wastes everyones time. But maybe they aren't a native English speaker, in that case I would understand completely.

But most of it needed to be said anyway as parts of the post were inaccurate.

As an added note: Is everyone around here aware of Firefox's "spell check this field" option?

---

### Post by jasonbrisbane on 2007-10-04
HI,

I got a book from my local library in Australia called Game Programming All in One 3rd ed (blue cover).
You can look it up on Amazon.

It covers Allegro 2D programming for games.
Its a blast.
The examples are all FREE (GPL) and the source code is directly portable between Windows and Linux (a few changes for MAC if you are interested).

I'd recommend having a look at that.
Try: [www.allegro.cc](www.allegro.cc)

---

### Post by LeChuck on 2007-10-04
As already told, learn a programming language - Python and C++ - and become a good programmer. Learn how to use a multimedia/gamedev API like PyGame, SDL, Allegro, or ClanLib - these are the game programmer tools to make life easier. Get familiar with game programming by creating simple old school arcade games like Pong, Space Invaders, Tetris.

---

### Post by LaRoza on 2007-10-04
> **Vox754 said:**
> 
And, Wybiral, don't be so hard. Let it be. Else I'll ask you to comment on every single grammatic error in pmasiar's posts.

It should be "grammatical" :D.

---

### Post by Engnome on 2007-10-04
[http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/)

---

### Post by Vox754 on 2007-10-04
> **LaRoza said:**
> It should be "grammatical" :D.
Oh noes!

Wait, I never said that. Wybiral and LaRoza are misquoting me!
This is not really a thread we want to hijack, do we?
(Sorry about not saying a thing in the other post but Wybiral just made me laugh.)

Just to contribute, I'll say this: follow Wybiral's and LaRoza's comments on the topic, and head to the Gaming forum, but you already know that.

I believe it is great if you can contribute to an existing project. But it is very important to keep an open mind if you are asking questions in a Linux forum.
Look at the responses someone got [when he wanted to keep his project a secret]("http://ubuntuforums.org/showthread.php?t=481076").

---

### Post by hockey97 on 2007-10-04
what i was saying before, was a long term thing, if he wanted to go pro.

and if you think you can be called a pro by using someone else's, game engine that's not being a pro, a pro game maker,  has to understand what a 3d game engine is and how it's made, in order to compete in the  real world.

I suggested c-script and c++ because  their is lot's of support and tools, c++ have been around longer than python and is mostly used in the industry.

I never said you have to learn c-script and c++ to make simple games,  If you actually  read the whole post from top to bottom, it was if his goal at the end was  to make games good enough to sell.

I suggested c-script becuse you need to learn that in order to adjust easier to c++.

opengl and direct x are api

---

### Post by CptPicard on 2007-10-04
> **hockey97 said:**
> 
and if you think you can be called a pro by using someone else's, game engine that's not being a pro, a pro game maker, 

Pros do that all the time. Most of the games on the market make use of a smaller number of engines that are coded elsewhere.

I understand your point though to a degree, I've got an old skool CS degree and am quite happy with it exactly for the reason that I understand a lot of stuff on a deeper level and am not just a code monkey... then again, if you want to be a game maker, you definitely don't need to be able to write the engine, and you can gain an appreciation of what it *does* without being able to write it from scratch.


> I suggested c-script becuse you need to learn that in order to adjust easier to c++

What the heck *is* "c-script"? :)

If you just mean C... you're better of going straight to C++, there will be less bad habits to unlearn, and going downwards to C is still fairly trivial.

---

### Post by Rupertronco on 2007-10-04
> **Wybiral said:**
> I was just teasing about the spelling errors, there was actually a point to the rest. I don't think I'm THAT mean, it's just my sense of humor :)

I would especially understand if they don't natively speak English, but if they do... Then I don't think I was bein""g hard enough, lol. Spell check is a mighty tool when you're trying to actually make a point. If people are going to have trouble reading it, don't bother writing it. It wastes everyones time. But maybe they aren't a native English speaker, in that case I would understand completely.

But most of it needed to be said anyway as parts of the post were inaccurate.

As an added note: Is everyone around here aware of Firefox's "spell check this field" option?

I love your attitude. 

Also, to those who don't speak native English, it's no surprise your grammar is not flawless, but it is sad that your grammar is usually much, much better than native speakers of the language.

---

### Post by LeChuck on 2007-10-04
> and if you think you can be called a pro by using someone else's, game engine that's not being a pro, a pro game maker, has to understand what a 3d game engine is and how it's made, in order to compete in the real world.
I don't agree with you. In the pro world it is all a question of budget. The development of an engine is usually more expensive than licensing an existing one. Engine development is a separate thing. It is definitely not wrong to develop skills as engine developer, but it's not necessary, especially not for beginners, homebrew & indie game developers - that's my opinion.

---

### Post by Rupertronco on 2007-10-04
> **hockey97 said:**
> what i was saying before, was a long term thing, if he wanted to go pro.

and if you think you can be called a pro by using someone else's, game engine that's not being a pro, a pro game maker,  has to understand what a 3d game engine is and how it's made, in order to compete in the  real world.

I suggested c-script and c++ because  their is lot's of support and tools, c++ have been around longer than python and is mostly used in the industry.

I never said you have to learn c-script and c++ to make simple games,  If you actually  read the whole post from top to bottom, it was if his goal at the end was  to make games good enough to sell.

I suggested c-script becuse you need to learn that in order to adjust easier to c++.

opengl and direct x are api

Huh? Go pro? Is he an athlete? Didn't think so.

I hope you don't honestly think the majority of professional game programmers understand physics engines, because they sure don't. Physics engines are one of the primary functioning/governing engines in most new games. Does that mean a programmer needs to understand the kinematics behind the engine? Nope. 

I don't like to be harsh on this forum, as it is very friendly, I find it unacceptable for people like you, who really have no clue what they're talking about, doling out advice. If you noticed the original post, he said he's just finished college, he's not looking for advice from kids. You're constantly editing your posts, regurgitating information that you've been corrected on "opengl and direct x are api" at the end of your post serves no purpose whatsoever, other than it's just a repetition of you being corrected. 

Please don't offer any more programming advice.

Original Poster: I'm sure you can get some decent information from people in this forum, but I'm not sure it's the best avenue to pursue. I'd check out some developer sites, specifically game developer sites. Also, see if you can get in touch with some open source game developers maybe some of the guys who worked on the Quake2/3 based games. The open source community (as far as games go) will likely provide you with much more information and advice, it's just in their nature.

---

### Post by Acglaphotis on 2007-10-04
I would recommend you to read "Python for absolute begginers", it teaches python via text games, later developing to 2d games and such. You can find on Barnes & Nobles or Usenet ; ).

---

### Post by pmasiar on 2007-10-04
> **Vox754 said:**
>  I'll ask you to comment on every single grammatical error in pmasiar's posts.

Sorry, but English is not my first language, or even second. Actually, it is my forth language, not counting programming languages :-)

---

### Post by Rupertronco on 2007-10-04
> **pmasiar said:**
> Sorry, but English is not my first language, or even second. Actually, it is my forth language, not counting programming languages :-)

That's impressive. What's even more impressive is that you have better skills in the language than the majority of its native (at least American) speakers. It's quite the poor reflection on the country. I would be shocked if hockey97 wasn't American.

---

### Post by CptPicard on 2007-10-04
Huh? What's wrong with pmasiar's English? IMO it's excellent, and I really can't tell he's not native (although I am not either)... if you're going to put him under some sort of special spelling/grammar-nazi surveillance, I want to volunteer for this special treatment too, out of solidarity.. :)

---

### Post by Wybiral on 2007-10-04
> **pmasiar said:**
> Sorry, but English is not my first language, or even second. Actually, it is my forth language, not counting programming languages :-)

So excluding programming languages you're quad-lingual! That's crazy. English is the only language I can understand more then a few words of. I do plan on learning more though (it's a valuable skill to have).

---

### Post by Vox754 on 2007-10-04
> **pmasiar said:**
> Sorry, but English is not my first language, or even second. Actually, it is my **forth** language, not counting programming languages :-)

```
forth != fourth
```

Sorry! I couldn't help myself!

The fact that you are a [Forth](http://en.wikipedia.org/wiki/Forth_%28programming_language%29) hacker makes this sentence even funnier!

CptPicard, don't worry, I wasn't trying to mock pmasiar. Everybody in here knows he is a real hacker.
I was just joking about it because it would take Wybiral several months to correct every single one of pmasiar's 2000+ posts. Congratulations, by the way.
If you want the pmasiar's special, you need to raise your post count to 1200 within three months.

If you can take constructive criticism, the errors pmasiar has made in the last weeks are:
[LIST=1]
[*]The use of the word "what" instead of "that" or "which" in "[Relative clauses](http://en.wikipedia.org/wiki/Relative_clause)". For instance, *"he is using a language what is not useful"* is wrong; the correct sentence is *"he is using a language that is not useful."*
[*]The order of words in "Indirect Speech". For instance, using *"I don't know what is he doing."* is wrong; the correct sentence is *"I don't know what he is doing."*
[*]The redundant use of the past form of verbs that happen with the auxiliary "did". For example, *"Did you used the function?*"; the correct sentence is *"Did you use the function?*".
[/LIST]

Those are not pmasiar quotes, they are examples.
pmasiar's English is good, he just happens to get excited in some threads that his grammar starts failing.

I cannot apologize enough for hijacking this thread.
------------------------------------------------------------------------

> **Wybiral said:**
> So excluding programming languages you're quad-lingual! That's crazy. English is the only language I can understand more **then** a few words of. I do plan on learning more though (it's a valuable skill to have).

It is not **then**, it is **[than](http://en.wikipedia.org/wiki/Than)**!
I wonder if this is specific to the Ohio area.

---

### Post by Wybiral on 2007-10-04
> **Vox754 said:**
> It is not **then**, it is **[than](http://en.wikipedia.org/wiki/Than)**!
I wonder if this is specific to the Ohio area.

Damn, you got me, lol. In my defense, the "a" and the "e" are pretty close on the keyboard and either would pass a spell checker.

---

### Post by CptPicard on 2007-10-04
It's totally OT, but just to note something about the language skills of non-native speakers and native speakers...

You have to realize that non-native English speakers have been taught the language from scratch by a teacher. Make a mistake, and you get marked down. Those who speak English natively have manners of speech intruding their writing way more easily than us who started with schoolbooks that had "how to use a London taxicab" examples and exercises in. So mother tongue English education spends its time eradicating these colloquialisms, which don't ever exist in our speech.

Also, I would bet that most of us Europeans who are good at English get most of our English from books. This means we get a lot of exposure to the correct written forms of English words, so our spelling is automatically better than that of natives'. I have read a LOT of English material ever since I was like 12 and was able to start fighting my way through one of Eddings' fantasy novels. That's about the time after which I was always ahead of the class, and could essentially have dropped regular English classes for some language I didn't already know. Unfortunately it was not possible, so I sat through useless classes until graduation from school, at which point I lost one (1) point in the English matriculation exam. I'm still bitter for not knowing where I screwed up. :)

Then there is the simple fact that in Europe you're close to other people who speak other languages, so that naturally evolves your linguistic capacity... I am fluent in Finnish and English, could get Swedish fluent with some real-world exposure, can read books in German and can get the idea of a newspaper article in French.

So there. :)

---

### Post by Rupertronco on 2007-10-04
> **CptPicard said:**
> Huh? What's wrong with pmasiar's English? IMO it's excellent, and I really can't tell he's not native (although I am not either)... if you're going to put him under some sort of special spelling/grammar-nazi surveillance, I want to volunteer for this special treatment too, out of solidarity.. :)

I wasn't being sarcastic. I'm thoroughly impressed. I'm always impressed by people that can master multiple languages, I never could. I can read and understand 3, but I can't speak them worth a darn.

I think you misunderstood me.

---

### Post by CptPicard on 2007-10-05
It was Vox who made the initial comment on fixing pmasiar's posts. :) Yes, I do understand it was tongue in cheek, just wanted some clarification on why exactly it was him who was being singled out :)

---

### Post by hockey97 on 2007-10-05
wow, ok, whatever you think, you said that pro game makers meaning programmers don't know physics engine thats somewhat true, but at EA games they have programmers that know that crap.

all I am saying it would give him an edge.

that's all .

I don't get why so many people keep twisting my words, I never said he was an athlete. ...  read my post or if you can't read I suggest taking a English class....

I do know programming, I bet if you made a game and made a business out of it you would lose your shirt, you know why because you depend on 3dgame engines instead of learning how 3d game engines are made. and ya I made a mistake I meant api but put 3d engines,  3d engines uses,  I corrected the post because I didn't want people to get confused,  I was not covering up my mistakes. I use c++ myself, don't really like python much, and I know it's faster and easier, but I am just used to c++, I first learned c-script  since it was recommended to me to start their before learning c++, which I did, I  learned html when I was in 6th grade, by using the internet.

so I do knot programming, just because I made a term mistake doesn't mean I don't know anything about programming.

what is your backround????  since you have to power to say who can or cannot post messages on the forum.

I was seriously trying to help him. but then you guy's showed, you didn't really help him by making fun of me..

I bet you don't know what api's are..???

[quote]

Huh? Go pro? Is he an athlete? Didn't think so.

I hope you don't honestly think the majority of professional game programmers understand physics engines, because they sure don't. Physics engines are one of the primary functioning/governing engines in most new games. Does that mean a programmer needs to understand the kinematics behind the engine? Nope.

I don't like to be harsh on this forum, as it is very friendly, I find it unacceptable for people like you, who really have no clue what they're talking about, doling out advice. If you noticed the original post, he said he's just finished college, he's not looking for advice from kids. You're constantly editing your posts, regurgitating information that you've been corrected on "opengl and direct x are api" at the end of your post serves no purpose whatsoever, other than it's just a repetition of you being corrected.

Please don't offer any more programming advice.

Original Poster: I'm sure you can get some decent information from people in this forum, but I'm not sure it's the best avenue to pursue. I'd check out some developer sites, specifically game developer sites. Also, see if you can get in touch with some open source game developers maybe some of the guys who worked on the Quake2/3 based games. The open source community (as far as games go) will likely provide you with much more information and advice, it's just in their nature.[quote]

get this through your head....  I  am not saying he has to know everything about the 3d game engines in order to make games but in order to compete with other's it would be a good idea.

you really need an English class really when I said pro, umm hmmm wow were talking about programmers and game makers, I don't get where athlete comes into play???

well I am no longer going to post on this post, any further since it's a waste of time, since you guy's would keep making fun of my post instead of helping the guy that started the post asking for help ,, in stead of helping your making fun of mean,  and also become the English police, acting that if anyone makes English mistakes  they must leave the internet....

I have seen stores spell cool as kool, I don't see why people would have to go in the store and yell at the store owner "learn some proper English"

so let me get this straight, I tried helping him, and you helped by making fun of me and turning the guy's post into an English post, if I am correct that's called being off topic,  that's part of English, and if you didn't know that then take an English class and just don't don't make fun of others English, I get calls from India at 12:00am and hear  a person speaking worst English than Americans I never go out and blown up saying omg wow he didn't know English, he sound's be aloud to call America because he has trouble with English.

so I advise you to just give your advice and let it be, don't go and lol at other peoples advice, that just shows stupidity and shows your not open minded.

---

### Post by Circus-Killer on 2007-10-05
okay, thanks for all the responses guys, even the rather heated ones. :popcorn:

but lets keep calm, i'm just looking to start making games as a hobby on the side, in my spare time.

looks like i've got an idea of where i need to start. i do appreciate all the advice. thanks everyone, and if you have more to add, feel free to. ;)

---

### Post by Wybiral on 2007-10-05
> **hockey97 said:**
> I have seen stores spell cool as kool, I don't see why people would have to go in the store and yell at the store owner "learn some proper English"

so let me get this straight, I tried helping him, and you helped by making fun of me and turning the guy's post into an English post, if I am correct that's called being off topic,  that's part of English, and if you didn't know that then take an English class and just don't don't make fun of others English, I get calls from India at 12:00am and hear  a person speaking worst English than Americans I never go out and blown up saying omg wow he didn't know English, he sound's be aloud to call America because he has trouble with English.

so I advise you to just give your advice and let it be, don't go and lol at other peoples advice, that just shows stupidity and shows your not open minded.

No, I didn't just make fun of your English for no reason. The only reason I responded to you was because you're offering terrible advice. If you don't know enough about game development to really help the OP, then don't "help" by offering such bad advice. And if you do "help" by offering bad advice, be prepared to be called out on it. I was mostly kidding with the English comments, but seriously, there's nothing wrong with a spell checker (Firefox has one built-in).

In reality, commercial game developers usually _buy_ engines (and they often go for thousands of dollars too). Most hobby game developers will use something like [Soya3d]("http://home.gna.org/oomadness/en/soya3d/index.html"), [Irrlicht]("http://irrlicht.sourceforge.net/"), [Ogre]("http://www.ogre3d.org/"), [Crystal Space]("http://www.crystalspace3d.org/main/Main_Page"), [G3D]("http://g3d-cpp.sourceforge.net/"), and [many others]("http://www.devmaster.net/engines/"). And this is _if_ the OP even wants to get into 3D game development. If all you want to do is make pac-man or a small single-player RPG, there's absolutely no need to invest the time it takes to learn the ins and outs of 3D game engine development.

On a side note, there's absolutely no reason not to make an effort to try and make your posts readable. That includes punctuation, capitalization, and using a spell checker if you have to. Even if people can understand you (which is difficult) they aren't going to take you seriously.

---

### Post by hockey97 on 2007-10-05
well first off I didn't know what his goals were, until now so he wants to do it on the side, start with python it's eaisier, Irrlicht is a 3d engine not a game engine and is only for c++ or .net programming lang. I use  Irrlicht , and they do have an online classes and functions list that explain what each function does.

just do searches on 3d game engines on google you will find out many of the their are alot free ones and from their determine what programming language you will learn, becuse  it really depends on what engine you use,  it  should tell you on their website.


also Wybiral , I know how to make games, gosh ,  the problem I was having was what his goals were,  which he now just stated,  I was giving advice based on if he wanted to run with the big boy's  I did that becuse even if he didn't want to sell games with the big boy's it was just my way of showing what's involve.

I know beyond game making, I know how to make a computer, and even code the whole thing still struggling with the OS just know theory of OS .

my advice was  about  if he wanted to sell games that are good enough to  run with the big boy's  and if he had to make the game by himself then that's what you had to do.

but it's true you can run with the big boy's with great game engine's which you will pay big $$$  if you using commercial game engines  and have the companies you running agains get to see what your using and see's the game engine, how it was made then they make their own game engine that's better than any commerical game engine on the market, then you got clambered..

I was just advising him what he needs to know in order to really run against the  big boy's, that was it , and was not bad advise just maybe won't help him much since he just said he was doing on the side, as a hobby.

if that was the case then use a free 3d engine and learn a programming language that is used in that 3d engine.

and use google to search for script examples,   and here is a good site in learning C++ if you want to learn c++.
[http://www.cplusplus.com/doc/tutorial/]("http://www.cplusplus.com/doc/tutorial/")

Good luck circus-killer

---

### Post by hod139 on 2007-10-05
Ignoring everything else you've said, I'll chime in with this post of yours:
> **hockey97 said:**
>  Irrlicht is a 3d engine not a game engine and is only for c++ or .net programming lang. 

What's the difference between a 3D engine and a game engine?  You draw a distinction, but don't say why.  As far as I'm concerned, they mean basically the same thing, and in practice are used interchangeably.  

> 
just do searches on 3d game engines on google you will find out many of the their are alot free ones and from their determine what programming language you will learn, becuse  it really depends on what engine you use,  it  should tell you on their website.
Wybrial already mentioned a good list of engines in a previous post, no need to randomly search google.  I will add to his list though (I hope he doesn't mind).  I'm more interested in physics simulation (opposed to how many game engines strive for believability over reality), and some of the better engines are [ODE]("http://www.ode.org/") and [Bullet]("http://www.bulletphysics.com/Bullet/").  Or, there is [mine]("http://robotics.cs.rpi.edu/dvc/"), but at the moment it is only for 2D and 2.5D (another grad student is working on extending it to 3D).  I don't say this to brag, only to add credibility to post.

> 
also Wybiral , I know how to make games, gosh ,  the problem I was having was what his goals were,  which he now just stated,  I was giving advice based on if he wanted to run with the big boy's  I did that becuse even if he didn't want to sell games with the big boy's it was just my way of showing what's involve.
I've seen some of Wybrial's work, I haven't seen anything you've done.  For these reasons I trust Wybrial's judgment over yours; you make lots of claims, but do not back them up.

> 
I know beyond game making, I know how to make a computer, and even code the whole thing still struggling with the OS just know theory of OS .
Why should we believe you?  Nothing in your post history suggests these claims you make.  Again, you make these unqualified claims, followed by statements that seem counter to these claims.  Also, knowing how to make a computer has little to do with developing games, so I'm not sure I follow your appeal.

> 
my advice was  about  if he wanted to sell games that are good enough to  run with the big boy's  and if he had to make the game by himself then that's what you had to do.
What about the girls?

> 
and use google to search for script examples,   and here is a good site in learning C++ if you want to learn c++.
[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)
It's much better to not use google to search for random code on the web.  The link you provided is a decent C++ reference.  I highly suggest using books and peer reviewed sites for learning.  For graphics the nehe site is very good.  For openGL books, I suggested a list not too long ago on another thread.  The red and blue book are standard, the Hearn and Baker book is also very good.

---

### Post by slavik on 2007-10-05
C and OpenGL. Get a book on graphics, get comfortable. Then start coding :)

---

### Post by hockey97 on 2007-10-05
their is  a difference in a 3d engine and a 3d game engine.

a  3d engine is only to create a 3d world, were as a 3d game engine is engine to make games and was designed to make games or more suitable for games.

some of what he named are 3d engines it will help only to make a 3d world, and also some of those engines do have plug-ins like  a sound class of functions ect.

I don't care if you believe me or not, I am just asking to stop making fun of me, I don't get where I said anything about to believe that I make games.

if you want proof then wait in a couple of years or so, you will hear about me.

but until then i guess you go by him.

but I can care less.

the point was that I was trying to help and what I get in return is being made fun off and you guys' telling people about that I ain't a programming just someone giving bad advice because I enjoy seeing people get bad advice.

you don't even know me.

I don't see how you have a right to tell people that I ain't a programmer and just a bad person who loves to see people go down in flames.

that's all I am saying.

I am not the one that started this you guys did, by making fun of me and saying I don't know anything about computers or even programming.

where is your proof??? prove everyone that I don't know anything about computer and that in high school I had electronics , and during the summers I do learn programming from the Internet.

I wasn't here to start any fights or anything, was just giving my advice.

but just for the record a 3d engine is meant only for making Gui's or 3d worlds like objects ect, it can't be used to make AI or use those functions for game play codes.

3d game engines like A6 ect are nothing but scripts that handle most of the aspects of a game, like sprites, 3d animation, your input devices ect, lot's of functions that you would use in games, it's more specified for games, and does handle 3d graphics also but more to it and the 3d graphics was designed for games..

a 3d engine just handles the graphics of a game or a program, hint 3d engine is used in any program even games,  doesn't have to be a game,
3d game engines are made and designed just for games, and was really meant for games, those are the differences between them.

I won't be replying any more here since, it's not welcomed.

just wanted to know that I never give advice if I didn't know, and if I did I would of said something saying I am not sure of but I would think....

---

### Post by Wybiral on 2007-10-05
> **hockey97 said:**
> [COLOR="Red"]their[/COLOR] is  a difference in a 3d engine and a 3d game engine.

a  3d engine is only to create a 3d world, [COLOR="Red"]were[/COLOR] as a 3d game engine is engine to make games and was designed to make games or more suitable for games.

some of what he named are 3d engines it will help only to make a 3d world, and also some of those engines do have plug-ins like  a sound class of functions ect.

I don't care if you [COLOR="Red"]bealive[/COLOR] me or not, I am just asking to stop making fun of me, I don't get where I said anything about to [COLOR="Red"]bealive[/COLOR] that I make games.

if you want proof then wait in a couple of years or so, you will hear about me.

but until then i guess you go by him.

but I can care less.

the point was that I was trying to help and what I get in [COLOR="Red"]retune[/COLOR] is being made fun off and you guys' telling people about that I ain't a programming just someone giving bad advice [COLOR="Red"]becuse[/COLOR] I enjoy seeing people get bad advice.

you don't even know me.

I don't see how you have a right to tell people that I [COLOR="Red"]aint[/COLOR] a programmer and just a bad person who loves to see people go down in flames.

that's all I am saying.

I am not the one that started this you guys did, by making fun of me and saying I don't know anything about computers or even programming.

where is your proof??? prove everyone that I don't know anything [COLOR="Red"]aobut[/COLOR] computer and that in highschool I had [COLOR="Red"]eletronics[/COLOR] , and during the summers I do learn programming from the internet.

I wasn't here to start any [COLOR="Red"]fight's[/COLOR] or anything, was just giving my advice.

but just for the record a 3d engine is meant only for making gui's or 3d worlds like [COLOR="Red"]ojbects[/COLOR] ect, it can't be used to make AI or use those functions for game play codes.

3d game engines like A6 ect are nothing but scripts that [COLOR="Red"]handel[/COLOR] most of the aspects of a game, like sprites, 3d animation, your input devices ect.

a 3d engine just [COLOR="Red"]handels[/COLOR] the graphics of a game or a program,  [COLOR="Red"]dosen't[/COLOR] have to be a game.

In no professional circle will you ever be taken seriously if you don't _try_ to write properly. Spell check is not going to kill you.

There isn't much formal definition between 3d engine and 3d game engine. Check [this]("http://en.wikipedia.org/wiki/List_of_game_engines") list out (I actually never called them GAME engines either, just engines).

The main problem with the game developer making their own engine is productivity. A tested and debugged engine large enough to support most modern video games takes years to develop. Commercial game developers just don't waste that kind of time. They find the most suitable engine and work from that (often the license can be bought to give them the source allowing them to further extend the engine if they need to).

I personally never said anything about your lack of computer science know-how. I just wanted to correct some things you said about "pro" game development because it was inaccurate. Nothing personal. But I'm also compelled to complain about your spelling and punctuation because you are here wasting the time of professionals. Try to make it more readable.

---

### Post by hod139 on 2007-10-06
> **hockey97 said:**
> 
I don't care if you believe me or not, I am just asking to stop making fun of me, I don't get where I said anything about to believe that I make games.

Nowhere did I make fun of you, if you feel that way re-read what I wrote.  All I stated is that you need to learn to back up your claims.

> 
if you want proof then wait in a couple of years or so, you will hear about me.
I hope that is true.


> 
the point was that I was trying to help and what I get in return is being made fun off and you guys' telling people about that I ain't a programming just someone giving bad advice because I enjoy seeing people get bad advice.

you don't even know me.
I appreciate your willingness to help, but misinformation helps no one.  You are absolutely correct that I don't know you, but all I have judged is what you have written, not you.  

> 
I don't see how you have a right to tell people that I ain't a programmer and just a bad person who loves to see people go down in flames.
Where did I say this?  All I asked is for you to back up what you have written.  Again, I made no personal comments about you, I have only commented on what you have written.

> 
where is your proof??? prove everyone that I don't know anything about computer and that in high school I had electronics , and during the summers I do learn programming from the Internet.
Where is my proof of what?  I definitely didn't say you didn't know anything.

> 
I wasn't here to start any fights or anything, was just giving my advice.
You are free to offer any advice you want, but you must be prepared to defend it against knowledgeable people.

> 
I won't be replying any more here since, it's not welcomed.
You are more than welcome to reply and post here.

---

### Post by hockey97 on 2007-10-06
well ya their is a difference,  if you buy any how to make a 3d/game engine books, it tells the difference.

a 3d engine is made to cover all areas in programs meaning, games,
and other type of software, it was not made just for games.

a 3d game engine, or just game engines,  are made just for games, from everything  a game needs, like graphics, it would make sprites, 
and other stuff,  and handle animation, it would also handle physics.

so their is a big difference on what it does.

but I only use a 3d engine just to speed up the time in making my gui's and 3d worlds.

here is another website I think is good on learning just game concepts.

[http://www.devmaster.net/engines/]("http://www.devmaster.net/engines/")

I never misinformed the guy.

I didn't know what his goals were, 

so  what I said was if he wanted to play with the big boys.

EA games they make their own game engines, and if you think you can beat them or just even compete with them, by using someone else's 3d game engine then you will find out the hard way.

I never said he has to do what I was saying, i  just suggested if it was me, and wanted to go pro after learning every single thing about game making and wanted to make a business out of it, that's what
I would do.

I don't get where I misinformed him???

---

### Post by LeChuck on 2007-10-07
Game programming is much more than graphics programming, and game development is not engine development.

---

### Post by hockey97 on 2007-10-10
> **LeChuck said:**
> Game programming is much more than graphics programming, and game development is not engine development.

I know that game programming is more than graphics.

what do you think an engine does???

I never said you had to make a engine in order to make games,

I am just saying that I advise you to know what goes on in the background of the game engine, and would give you more strength, in building a game, more professional look.

I am just saying if you were to make a game better than EA games how could you if  you don't know anything about what goes behind the scenes.

EA games if you ever read their script's from their games they make their own game engine, from scratch, depends on which games,

maxis I read some of their simcity ones, and some are similar, like you can tell they add on code to existing game engine they made until they start to work on a whole new look for a whole new game well dosen't have to be a new game just when they want the game to look and have better graphics ect and artwork, ect.

I never told him that he need's to learn how to make a game engine  in order to make simple games or any games, just was saying if he

wanted in a long-term goal was to sell games and try to beat EA games or some company, just saying what you should know.

you can alway's get a person that know's how to make a 3d game engine.


The thing I didn't know his goal, a short term or long term.

if he wanted to make games as good or better than EA games it's a long term goal, and my advice fit that goal if it was his goal.

but later told that he wanted to do it on the side as a hobby.

in that case he dosen't need to know the game engine.

---

### Post by Wybiral on 2007-10-10
> **hockey97 said:**
> I am just saying if you were to make a game better than EA games how could you if  you don't know anything about what goes behind the scenes.

You use a really good game engine, there are thousands out there.

> **hockey97 said:**
> EA games if you ever read their script's from their games they make their own game engine, from scratch, depends on which games,

They may have at some point, but I highly doubt they do frequently. Do you have some kind of reliable resource that explains which engines they've written ground-up? Like I said before, it takes years to develop, test, and debug a functional game engine. They aren't going to waste that development time when there are other options available.

It's likely that you might want to tweak something at some point, but you make it sound like you have to write game engines to be a professional game developer and that just isn't so.

As an example, John Carmack wrote the original doom/quake first person shooter engine a long time ago. The only reason he did so is because he was one of the first. Now almost all first person shooters use a derivative of that engine. Not nearly as many write their own. It's just not productive.

If you've written your own engines before and can confirm the fact that it was useful for you to get into game development, by all means, let us know.

---

### Post by LeChuck on 2007-10-11
If you aim is to beat EA, then you need a multi million dollar budget, and a fully staffed devteam of specialists. It's very unlikely to find someone funding the development of a game in addition with an engine, maybe unless you're John Carmack.

---

### Post by hockey97 on 2007-10-11
no, i didn't mean that to be a pro game maker, you have to make game engines,  I am just saying if you plan to go in business as a pro.

I have read scripts with the simcity line up, simcity 4 I think uses simular game engine as the sims2, EA games has their own people making the game engines, usally it's just adding onto it.

you don't really need multi-million dollars to start such a company.

unless you plan on hiring top notch people and a big development team.

you can make games just like EA games and could make it by yourself but takes time, the more people you have on the team to develop the engine and game would take less time than compared by doing it yourself.

I know how to make a game engine thanks to a book, 3d game engine art...

great, book, shows all the guts of the game, lot's of math, and programming.

lol


I am sorry if I sounded like I was saying pro game makers that are pros has to know about the game engine.

I really mean if you were to make a game and want to sell it and start a business and want to make a game as good as EA or some
big company.

my advices was based on that goal.

I advised know the 3d game engine, for that goal, becuse that's really learning the main gut's of games really.
graphics,sound,api,gui,usser input, ect

but it could not alway's hurt to learn what goes on in the backround 
it would just make you stronger in game development ect.

He said that he wanted to make games as a hobby on the side,

so I suggested python as a start.

however with my experience I thought learning c-script and then learning c++ and going on programming board fourms helped me

to learn overall game develop.

I can't really find anything ti really prove to you that Ea games make their own game enigne.

[http://www.jobs.ea.com/how_ea_makes_games.html]("http://www.jobs.ea.com/how_ea_makes_games.html")


but I have read simcity 3000 scripts and saw their own game engine in the game codes, connections and links ect, also heard about it on the modding fourms, they only use it for their games they don't sell the game engine.
the engines are only made for a few games not all the games.
console games they use other game engines.
currently I think EA signed with unreal game engine 3.
and said they will start making games for ps3 .

the next simcity series is simcity societies, I think the game looks like crap, lol simcity 4 looks better, it comes out in dec.

I don't know if they used their own game engine, for this game, but hearing some rumors , and they also will put global warming in this new game.
lol

---

### Post by g4m3b0y on 2007-10-11
This post has been very amusing to me :) In my personal and short lived (due to relocating -- california is too expensive to live in) professional experience making games for the PS2 and PSP (worked for LTI Gray Matter), I recommend learning C++.  C++ is the dominant language used in the industry. The game engines used a majority of the time are created by someone else. I worked in a development house and the license to the game engine was owned by Crave Entertainment. It was their game engine. I wrote higher level code (logic, AI and HUD). Unfortunately the IDE used was M$ VisualStudio.Net with the Platform SDK and any serious gamer uses windoze when making pc games.  Its a shame but that's how the world works.  I recently just started using python for development (trying to use it with blender) and I have to say that python made me fall back in love with programming. If this is just a hobby, learn pygame or cheat using blender with python and an export script (if you're trying to make money). But if you're serious, learn C++ (you can even use python for AI) and OpenGL. Don't try to tie yourself down to one platform by learning DirectX. I live on the East Coast now :( and have to do web to survive (because that's what people want here) but I can choose what platform I develop on since the web is supposedly neutral (to an extent).  Either way, you should learn python anyway because you can be much more productive. Python for prototyping (speed of development) and C++ for speed of implementation or both (C++ for lower-level operations and python for logic)

---

### Post by CptPicard on 2007-10-11
> **hockey97 said:**
> 
I have read scripts with the simcity line up, simcity 4 I think uses simular game engine as the sims2, EA games has their own people making the game engines, usally it's just adding onto it.

It really does not add to your credibility that you insist on speaking of "scripting" and "c-script" (which does not exist) when in particular the engine part of a game tend to be always compiled binaries (and I don't see you acknowledging this anywhere despite advocating engine programming). A quick googling doesn't even reveal much of a public scripting interface for either SimCity 4 or Sims 2, and the internal interfaces are probably very different.

You aren't reading and comparing the binaries are you? ;)

> 
you don't really need multi-million dollars to start such a company.

unless you plan on hiring top notch people and a big development team.


Yeah, these days you pretty much do. Game development is getting very expensive even without writing your own engine.

> 
I know how to make a game engine thanks to a book, 3d game engine art...


I know how to make a game engine on a very high level too, not that I would actually attempt it because the devil is in the details and the work would be enormous. There's a difference between reading a book on it and actually being able to do it.

That said, a general understanding on that level is pretty much all you need to make games unless you're an engine developer yourself.

> 
no, i didn't mean that to be a pro game maker, you have to make game engines,  I am just saying if you plan to go in business as a pro.
..
I am sorry if I sounded like I was saying pro game makers that are pros has to know about the game engine.

Uh... I really wonder what exactly it is you mean here.

> I advised know the 3d game engine, for that goal, becuse that's really learning the main gut's of games really.

Of course you need to know the API you're using. And when you're using a 3D engine for example, you're pretty lost if you don't know the fundamentals of 3D graphics... you do need to know what you want your engine to do for you. But that's still far away from writing your own engine.

> however with my experience I thought learning c-script and then learning c++ and going on programming board fourms helped me

What the heck is this c-script language you keep on talking about? :)

---

### Post by Wybiral on 2007-10-11
> **CptPicard said:**
> What the heck is this c-script language you keep on talking about? :)

lol, I've been wondering the same thing. I assume he/she means C? I've never heard anyone refer to it as c-script though (considering it isn't a scripting language).

---

### Post by CptPicard on 2007-10-11
> **Wybiral said:**
> lol, I've been wondering the same thing. I assume he/she means C? I've never heard anyone refer to it as c-script though (considering it isn't a scripting language).

I suspect he's under the impression that C is to C++ as Javascript is to Java... which isn't even correct on the Java side, of course...

---

### Post by hockey97 on 2007-10-11
no, i just read the game scripts , a modder maid a program to read lot's of the scripts, they even talked on the board fourms about it.
the modde claims he got to go at EA games head quarters and got permission to look at the game engine, and also they unlocked all the 3d models of the game, to him so he could make some neat models.

I can't prove, just saying what I know, and don't really have a full time to show all places where the proof is, just saying .

and I know that every script/code you make, you have to compile it, gosh I ain't going to explain or point out every single detail of the programming process, every programmer should know that a complier  just  converts the code language like c++ or any language into binary,
or you can also call it machine code... 

and ya I know  the compliers are made specified like c++ complier deals with c++ scripts or code....

I know looking on the internet would  not show all simcity 4 code.
 
even if you have the game you need s program to read the specified script/code,  
and their are lot's of areas locked like most of the 3d models are.

I didn't read the game engines, but read the game scripts.

and ya C-script does exist...

[http://freshmeat.net/projects/csl/]("http://freshmeat.net/projects/csl/")

---

### Post by Wybiral on 2007-10-11
> **hockey97 said:**
> [COLOR="Red"]n[/COLOR]o,[COLOR="Red"] i[/COLOR] just read the game scripts , a modder [COLOR="Red"]maid[/COLOR] a program to read[COLOR="Red"] lot's[/COLOR] of the scripts, they even talked on the board[COLOR="Red"] fourms[/COLOR] about it.
[COLOR="Red"]t[/COLOR]he [COLOR="Red"]modde[/COLOR] claims he got to go at EA games [COLOR="Red"]head quarters[/COLOR] and got permission to look at the game engine, and also they unlocked all the 3d models of the game, to him so he could make some neat models.

I can't prove, just saying what I know, and don't really have a full time to show all places where the proof is, just saying .

[COLOR="Red"]a[/COLOR]nd I know that every script/code you make, you have to compile it, gosh I ain't going to explain or point out every single detail of the programming process, every programmer should know that a complier  just  converts the code language like c++ or any language into binary,
or you can also call it machine code... 

[COLOR="Red"]a[/COLOR]nd ya I know  the compliers are made specified like c++ complier deals with c++ scripts or code....

I know looking on the internet would  not show all simcity 4 code.
 
[COLOR="Red"]e[/COLOR]ven if you have the game you need [COLOR="Red"]s[/COLOR] program to read the specified script/code,  
and [COLOR="Red"]their[/COLOR] are [COLOR="Red"]lot's[/COLOR] of areas locked like most of the 3d models are.

I didn't read the game engines, but read the game scripts.

[COLOR="Red"]a[/COLOR]nd ya C-script does exist...

[http://freshmeat.net/projects/csl/]("http://freshmeat.net/projects/csl/")

[SIZE="7"][COLOR="Red"]D-[/COLOR][/SIZE]

Scripts don't get compiled. [http://en.wikipedia.org/wiki/Scripting_language](http://en.wikipedia.org/wiki/Scripting_language)

As far as C-script... Wow, it actually exists. But it looks on the site like it hasn't been touched since 2002. What makes it a good language to start with? As I recall, you recommend C-script then C++? Why not just C?

---

### Post by aks44 on 2007-10-11
> **Wybiral said:**
> [SIZE="7"][COLOR="Red"]D-[/COLOR][/SIZE]
[SIZE="7"][COLOR="Red"]C++[/COLOR][/SIZE]? (Sorry I couldn't help :p)

> **Wybiral said:**
> As far as C-script... Wow, it actually exists. But it looks on the site like it hasn't been touched since 2002. What makes it a good language to start with?

FWIW C hasn't been touched since 1999. :twisted: (ok, I'm playing the devil's advocate, I'll stop here ;))


</troll>

---

### Post by hockey97 on 2007-10-11
the reason, I  I suggested c-script, was that their are alot of tutorials, and also game engines uses it like in A6 game engine.
The reason I suggested was that lot's of newcomers use c-script I even done it that's where I started, I first tried learning c++ too hard for me at that time, I was frustrated, and a person suggested c-script , I goggled it and found tutorials and learned alot taking it a step at a time.

I soon got good enough that I make simple 2d games. after playing around with it making programs small ones, I then jumped into c++

and then c++ became readable lol 

if c-script doesn't get complied, then how come their are many of compilers out their, for c-script??? in the game engine A6 the script you have to compile the script the c-script.

compilers job is to  first know the laws of the language,  and next is reading the script or code and then converting it to binary.

so for every language their are compilers, and their could be a compiler that can be used for more than one language, but haven't seen one, yet doesn't mean it's not possible.

I don't get why your grading me?? 
since it look's like you  think you know everything, 
first you tell me I ain't a programmer,  then you now are grading, me
I don't recall you being a teacher???

My point is I was trying to help, and ya I do know programming, 
and how games are made.

I was just helping the guy out.

but then you come and give your suggestions, 

and then make fun of me,
and then say I ain't a programmer,
and then grade me.

I don't get it.

how come I know of c-script and you didn't ???
so your telling me and everyone that I am not a programmer and yet
I know of c-script and you don't

that just show's that you don't know anything about me.
and  what you said that  I don't know programming and should stop giving advice on stuff I don't know.

if that's true then the same goes with you.

if you didn't know of c-script then why give advice to this guy.
I mean if I  am right that I understood that you said before that I shouldn't give advice becuse  of  what I suggested to him.
and I feel that you think you  know everything about programing,well enough to tell if a stranger is a programmer or not and yet you never heard of c-script and I have.
that's the only thing I can prove I know programming.

even thought that's not fully strong evidence, but at least shows, 
my point.

what your telling me that I should have every detail explained about programming like compiling, I don't think even professionals would explain a high detail of programming on a board fourm , unless it was important or needed.

since the guy said he has some experance in programming for the web .
I assumed he knows what a compiler is since php or  any high end web language even in tutorials, they would say your almost finish just complies the script or code.. and then run it.  

but on here I at least showed some what proof that I know programming, which was that c++ website tutorial page, and saying and clarifying c-script that it does exist.

and you said it didn't you guy's made fun of me, saying I  was thinking like javascript and java,  I know those are 2 different stuff.

my point is why pick on me???

I was trying to help, not trying to show everyone my work and prove I am a programmer.

I am also not saying that I am perfect or that I am the best programmer,  I am just saying I was trying to help.

that was it.

I should really make fun of you laughing at me about c-script . 

but I didn't because we are not perfect, and it's stupid to make fun of others, even when you yourself is not perfect.

me myself I  would  welcome people to give advice even if they them self are wrong or made some mistakes, so at least others could correct him, so he wont make the same mistake nor give the same advice to people.

The reason I don't care if you do be alive that I can program, is because it won't matter,  I would have to spend time  to convince you and at the end if you be alive me then what did I get??
nothing it's not worth spending the time.

I didn't say he had to make a game engine to make games or to be a professional game maker.
but I said that if he wanted to start a business and plan in long terms what he needs to know in order to beat or run with Ea or another game company.

ya I haven't made a game engine but I know how to build one ,I read the book.

but I didn't say that I made one. and ya it's alot of work lot's of math, 
trig, geo, calk, and ya calk in my terms means calculous, ok. 

I know I am not the best nor bragging anything.

I was just helping.

and don't understand why I am being treated this way.

and don't care, assuming you are not open minded type, since it sounds like you don't allow others to make mistakes if they do they should be made fun off instead of helping to correct them.
I mean correcting the person without making fun of the person for making such mistakes.

that's just my point and why I am somewhat frustrated on some of the comments based on my postings.

I just was giving my advice, and if you disagreed then you could respond in a polite manner, saying I don't agree what that because....
but you didn't you, without any evidence posted saying that I don't know programming and should not give bad advice on something that you don't know. 

right now I could of made fun of you not knowing c-script exist.

because you just misinformed the board by those posting.

but I didn't .

then you fired back at me saying scripts don't get compiled.
and that I said that script does get compiled.

and I never said that I was just commenting on the last post,
that talked about compiling.

but on that subject, I know c-script has compilers around google them if you want proof.

and since you don't know c-script I don't get why you made that post.
and the A6 game engine is built on c-script , they have a plug-in where you can write code in c++.

that's all I know about the topic on c-script if it get compiled or not.
that's all I know about that.

---

### Post by hockey97 on 2007-10-11
> **Wybiral said:**
> [SIZE="7"][COLOR="Red"]D-[/COLOR][/SIZE]

Scripts don't get compiled. [http://en.wikipedia.org/wiki/Scripting_language](http://en.wikipedia.org/wiki/Scripting_language)

As far as C-script... Wow, it actually exists. But it looks on the site like it hasn't been touched since 2002. What makes it a good language to start with? As I recall, you recommend C-script then C++? Why not just C? 

oh and ya they do read that whole thing.

Scripting languages can also be compiled, but because interpreters are simpler to write than compilers, they are interpreted more often than they are compiled.

I took that part from the webpage you provided.

so you just misinformed us again, saying that script's can't be compiled , even thought that sorce you gave us say's it can but it's mostly interpreted.

c-script is compiled, and I know it since I see lot's of compilers on the internet.

this should prove people that I was right, and should not be made fun of.

since were are humans, can we can make error's , and also shows that programming is large, their are lot's of info on it.
so it doesn't mean if I didn't know specific terms in computer since, doesn't prove or mean I don't know programming.

that's why I  replied, saying that you can't prove that I don't know programming.

so just settle down and advise the guy that had the question about game development on where to begin, to not listen to me because
what ever your reasoning on why you think my advice is bad and he shouldn't listen to me. 

that's all you had to do, instead of posting that I am not a programmer and I should even give suggestions on stuff I don't know.

---

### Post by Wybiral on 2007-10-11
ROFLOL

*** Recovers ***

No, I said that SCRIPTS don't get compiled. I say this because you mentioned C++ scripts and they don't exist. C++ isn't a scripting languages. Scripts and programs are not synonyms. Script source usually gets interpreted, not compiled. Look, I'm not trying to single you out or make fun of you. I kid about the grammar / spelling. But when you offer advice that you aren't sure about, it's probably going to come back and bite you (like this thread). If you don't have good proof, expect to get questioned about it. And you're right, I had no idea what C-script is. And I don't think I'm the only one, it doesn't seem to be a very popular language. I guess that makes you a better programmer than me. Maybe I should write a giant, misspelled, one sentence rant about it?

EDIT:

Also, in case it wasn't clear, the D- was for grammar, not content (and it was a joke).

---

### Post by Lster on 2007-10-11
This isn't really constructive or useful anymore. I would just give up your arguing...

PS: Nice Halloween avatar, Wybiral :). I should make a pumpkin-box for my cat - he'd love that...

---

### Post by Wybiral on 2007-10-11
> **Lster said:**
> This isn't really constructive or useful anymore. I would just give up your arguing...

Yeah, I'm bad at ignoring threads like this though. But you're right, we've completely demolished this thread (sorry OP).

> **Lster said:**
> PS: Nice Halloween avatar, Wybiral :). I should make a pumpkin-box for my cat - he'd love that...

lol, thanks. That picture was from last year (my signature has more of those pictures). She really likes pumpkins for some reason.

---

### Post by hockey97 on 2007-10-12
I don't understand you man.

Why do I need to prove my suggestions???

suggestions are based on your opinion that you think will help the person.

I didn't know that we had to prove with huge amounts of evidents that are suggestions are 100% right, I mean this is a board fourm not college,
gosh.

and ya your making fun of me.
you keep on striking back, I am just defending, myself that's why I respond.

and scripts can be compiled but usally they are interperted, becuse it's faster.

c++ does get compiled.

I really don't understand how I would prove and why would I spend hours proving my suggestions.

I don't see you proving yours...

what I am saying you don't need to prove your suggestions, becuse this is a board fourm not college, or a company where you have to as a job.

have c-script is popular, I see lot's of book out about it.

and also websites that teach c-script and c++.

their are lot's of compilers and also game engines that use c-script.

I never said I was the best programmer,  what I was saying you act like you know everything,  becuse your telling me that I have to prove every post of mine to proof it with high details and lot's of information which takes time.
and I am not wasting my time to prove to you anything... and yet you don't have to prove yourself.

---

### Post by LeChuck on 2007-10-12
It's just because you give weird advice. Anyway, I just googled myself for c-script and the a6 game engine you mentioned, and found a commercial game development package for Windows. Well, now I have a clue what you are talking about.

---

### Post by xStylezx on 2007-10-12
Thought id just chime in,scripts can and do get compiled all the time.Not that it matters,but that is fact.Ok,let the flaming continue....

---

### Post by pmasiar on 2007-10-12
> **hockey97 said:**
> Why do I need to prove my suggestions???

Some of us strive to give CORRECT and VALID suggestions based on FACTS, EXPERIENCE and best practices, not mere opinions. And many of us are ready to support suggestions we give with relevant info, when requested, to prove that it is not just a WAD == Wild A55 Guess.

Obviously, this concept seems foreign and strange for you. Well, I guess this is your peculiar way to enliven the discussion :-)

---

### Post by hockey97 on 2007-10-12
no, I am not saying that you should give a random suggestion.

ya I understand that you have to prove your reasoning,  but in this question it's asking where to start with game development.

I wanted to know what his goal was.

they reason I suggested what I posted, was that if he wanted to start a business and wanted to run against or make as good of games as like EA.

and I assumed it was one person.

most people ask where to start, and some of those people expect what you suggest after they go through that they expect to make good games just like what you see on the xbox ect.

Key word SOME!!! 

I wanted to show him if his goal was to make good games as EA or even better,  how much work and what you should learn base on what I have seen, read, learned, from books, news, watching other game company's. 

I wanted to show what he has to go threw to reach his goal.

and I was giving advice based on what I thought his goal was.

he then later stated it was for just on the side hobby, which then I suggested him to use python, and pygame.

what I don't understand is what you need to prove that my suggestion was just to help him, and not give him belony.

like if he wanted to make a business and make great games and wanted to run against EA.

your suggestions would kill him,  seriously he would of learned python and pygame and then learn some ai game concepts then compete.

it's like telling him go into a boxing ring with minimal skill and  you will win against the opponent that has 20 years of experience and has more skill then him.
and you tell him oh wait  put on these magic gloves, and out of nowhere he might have a chance to win but still that's just a maybe 
going from no way to a maybe.

basic you advise him to learn programming python, or c++ what ever you told which one to take, and then pick up a free 3d game engine, so when he makes his games he won't know the true stuff behind his game.

he will only know the code he put in, and use other's functions to make his game.

I was giving advice based on what his goal might be,  that is why I asked what his goal was.

and I just gave a quick advice based on if he wants to make great game in  the long run, what is the over all picture.

so that after 2 years of practice and  reading, he wont be disappointed. 

I don't see how that is weird advice???

and I don't get how I could prove this???

what should I do google stuff??

that advice then soon changed when he state his goal or what he planned to do.

the advice you gave, some new comers would think that omg that's how games are made, they would think that within a year they will make good games as EA and when they spend that 1 or 2 years and find out their not even near them they get disappointed.

that was the reason I gave my suggestion, and then changed it after he state his goal.

I don't understand why I have to prove my post's and stuff and everyone else doesn't????  

where's your proof???

I am not the one fighting or started this, i  am just defending  myself,

and some of you guy's keep after me, you just wont let it slide, 
like right now about c-script , some of you were wrong saying it dosen't exist.

and you were after me, making fun of me, even with C-script  and even their are other post supporting the c-script post I made, you still are after me.

where was your proof???

you just shouted out your opinion about me.
some of you even think you know all about me, saying I am not a programmer.

that's why I don't understand what you mean by back up your statement's how is it That I  am the only one that needs to back up
my post.

but others can speak their minds??

my main point is why do you care???

I gave my suggestions.

if you disagree with it then say so, and tell the person that started this post, why you think that I am wrong.

and that's it,  I won't mind it.

I mind it when you start pointing fingers and  and say about me that I am not a programmer because I said so....

wow that's some good proof that I am not a programmer, wow

you should read all my post and read it step by step.

and you will find out I was not fighting or started the fight.

I was just defending my self.

and basically saying why you care so much??

and why am I the only one that needs to prove myself????

that's what your saying that I need to back myself up.

and yet  you don't have to.

that's where I am confused.:confused:

oh and  when I said earlier, 2 years,  I was giving an example so do be up all over my face saying that  it dosen't take 2 years it takes more or what ever.

---

### Post by Perfect Storm on 2007-10-14
Thread closed on the request of the OP.

---

