---
title: "2D side-scroller game"
date: 2007-12-30
forum: Programming Talk
---

### Post by chips24 on 2007-12-30
i want to make my own side scroller game, i need the code and detailed instructionon how to put the game together. its going to have 16 bit images for the graphics, so can you help?

btw, the code can be for any windows or linux.:confused:

---

### Post by Steveway on 2007-12-30
[http://pygame.org/news.html](http://pygame.org/news.html)
That should be good for a beginner.

---

### Post by chips24 on 2007-12-30
i found that site a bit confusing, i dont want to download any software, i want to put the game together with bitmap images and .txt documents:confused:

---

### Post by chips24 on 2008-01-01
i need help still

---

### Post by Kitsun on 2008-01-01
AFAIK Ubuntu comes with Python installed, just type python in the terminal to get a CLI interpreter, its also possible to get this program to run text files, I can't remember how, wasn't too difficult.

I think Pygame is installable from the repos, if its not installed by default.

---

### Post by chips24 on 2008-01-02
ummm, no internet

---

### Post by chips24 on 2008-01-02
i have the 32x32 tiles ready, now i just want to make it a game. but i dont know anything with game making. need eastist possible instructions.ive done extensive research for weeks and i couldnt find anything

---

### Post by chips24 on 2008-01-03
i want to mmake my own 2d sidescrolling game, i have 32x32 tiles,but i need windows software, because im making it on windows.

---

### Post by chips24 on 2008-01-03
help?

---

### Post by Mike'sHardLinux on 2008-01-03
Hi.

I am not sure what you are asking.

Do you already know how to program? If not, you can take a look at [Python.]("http://python.org/") It is available for Linux and windows, so you could use it for what you want. It is supposed to be pretty easy to learn. I am learning it in Linux right now. I don't have any more specific information unless I know exactly what you wanting to know.

Good luck.

---

### Post by chips24 on 2008-01-03
i wanna make a 2d side-scroller platformer., i think that should be fairly simple?

---

### Post by Rhubarb on 2008-01-03
If you decide to use Python to make your game, you could use the pygame library (which works in windows and linux fine)
[http://www.pygame.org](http://www.pygame.org)

Also have a look here at some already implemented python side scrolling games:
[http://www.pygame.org/tags/platformer](http://www.pygame.org/tags/platformer)

---

### Post by mister_k81 on 2008-01-03
I realize that you are looking for Windows apps, but there are a few basic 2D game making programs out there for linux. Though I don't know how well any of these work... 

Novashell: [http://www.rtsoft.com/novashell/](http://www.rtsoft.com/novashell/) 

2D Game Editor: [http://game-editor.com/2d-game-maker.html](http://game-editor.com/2d-game-maker.html)

and Mokoi: [http://mokoi.sourceforge.net/:](http://mokoi.sourceforge.net/:)

...And of course there is [Game Maker](http://www.yoyogames.com/) for Windows.

---

### Post by chips24 on 2008-01-03
game maker... ill try this... hopfully i can add my own images into it

---

### Post by chips24 on 2008-01-03
thankyou so much

---

### Post by Sockerdrickan on 2008-01-03
I would still recommend Python

---

### Post by sub2007 on 2008-01-06
> **chips24 said:**
> i wanna make a 2d side-scroller platformer., i think that should be fairly simple?

Do you really want to make an "original" game, or just a game with your graphics in? If you just want your graphics, you can modify an existing side-scroller (such as Supertux or Secret Maryo Chronicles), replace the sprites and make new levels and call it a new game. Open source give this flexibility. I don't see any need to code a new game when suitable engines already exist.

P.S. 32x32 images will look really ugly if the game is to run at any decent resolution. :)

---

### Post by Seraed on 2008-01-06
[http://www.gamedev.net](http://www.gamedev.net)

I highly recommend you visit GameDev.net and look through their tutorials. Also take a look at their forums.

There is much to do when making a game. Even the simplest game requires a great deal of programming knowledge.

Try simple games like pong clones, then work your way up to tetris clones. Once you have mastered concepts in those games, you can begin to tackle more advanced topics, such as side scrolling, sprite animation, AI, etc.

---

### Post by chips24 on 2008-01-08
> **sub2007 said:**
> Do you really want to make an "original" game, or just a game with your graphics in? If you just want your graphics, you can modify an existing side-scroller (such as Supertux or Secret Maryo Chronicles), replace the sprites and make new levels and call it a new game. Open source give this flexibility. I don't see any need to code a new game when suitable engines already exist.

P.S. 32x32 images will look really ugly if the game is to run at any decent resolution. :)

whats a good tile size than?

---

### Post by chips24 on 2008-01-08
i think i will just take somthing like supertux and change the images(sprites), thanks for the idea. i think the best way for me to learn the code is by looking at the scripts first hand because i am very visual. most scrips like metacity are very easy, which why i say use bitmap images and txt documents, oh yeah, how come some code is different colours, toes the colour of the code have any function?

plus im not on the internet that often on ubuntu, so i better do some studying.

---

### Post by chips24 on 2008-01-10
how do you get to the supertux datafile?
i want to change the sprites.

---

### Post by sub2007 on 2008-01-13
> **chips24 said:**
> how do you get to the supertux datafile?
i want to change the sprites.

I don't really know Supertux, but I can heavily recommend Secret Maryo Chronicles. All images are stored in /usr/share/smc/pixmaps . All sprite data (scaling information, rotation, collision information...) is stored in easily modifiable XML .settings files. The game auto scans for new images each start. It's very flexible for modding. More info on sprites in the wiki: [http://secretmaryo.org/wiki/index.php?title=SMC:Sprites](http://secretmaryo.org/wiki/index.php?title=SMC:Sprites) or discuss it on the forum: [http://secretmaryo.org/phpBB2](http://secretmaryo.org/phpBB2) :D

You can get the latest version from getdeb: [http://www.getdeb.net/release.php?id=1906](http://www.getdeb.net/release.php?id=1906)

---

### Post by charlieg on 2008-01-15
A better place to post this might be the [FreeGameDev forums]("http://forums.freegamedev.net/") which, as the name suggests, are a community based on developing Free Software games.

There's much more to the FGD place than just the forums though.  There's a [game dev wiki]("http://wiki.freegamedev.net/") (although it's a bit sparse atm but information is coming) and [freeartsearch]("http://artsearch.freegamedev.net/") (which is just amazing).

---

### Post by chips24 on 2008-02-04
i have been dieing to write programs, ind im a very visual person so reading a stupid tutorial is useless for me !!!!!!! i want to recreate a second generation side scroller game, and pygame might help, but i know no code, not one single letter, so can you give me some advice?

im also very annoyed with blender, how do you put and image overlay over youre object you created, than add shading, im too lazy to search the web.

---

### Post by LaRoza on 2008-02-04
Try Python with PyGame, see my wiki and the stickies.

(Moving thread)

---

### Post by chips24 on 2008-02-04
gee, you are popular!!

---

### Post by chips24 on 2008-02-04
this stuff is so confusing at first!!!

really all i see is blah blah blah blah blah

sorry, this will take me a while

---

### Post by chips24 on 2008-02-04
python is c++ right?

---

### Post by CptPicard on 2008-02-04
> **chips24 said:**
> ...  reading a stupid tutorial is useless for me !!!!!!! ... i know no code ...im too lazy to search the web.... this stuff is so confusing at first!!! blah blah blah ... python is c++ right?

[IMG]http://wasteddomain.com/gallery/d/568-1/picard-sigh.jpg[/IMG]

Coding is all about being able to first read code. You will have to think in terms of abstractions which are, in practical terms, expressed and manipulated in terms of a formal language. When you learn to code you will learn to "visualize" things after a fashion, but *reading those "stupid" tutorials* (which for Python are excellent) is a mandatory first step.

There's no way someone is going to be able to draw you pretty pictures to give you an understanding of what you're dealing with.

Also, Google Is Your Friend. If you're too lazy to use it, don't expect others to use it for you.

No, Python is not C++. Whole different languages.

*(sorry, couldn't resist the picture.. )*

---

### Post by chips24 on 2008-02-04
ok, im done venting, I just want to make a 2d sidescrolling platformer, like Sonic The Hedgehog or mario

---

### Post by CptPicard on 2008-02-04
Well, then you just need to hit the tutorials and learn the language. You need to have the basics down well first before you can take on a project like that. And you definitely are better off starting with Python (and not C++), considering you are a total beginner.

They say the PyGame library is good for writing smallish games in Python, you should take a look at it.

---

### Post by LaRoza on 2008-02-04
You have already posted a thread, you marked it solved, and you got a lot of advice.

Threads are merged.

---

### Post by pmasiar on 2008-02-04
To write game like that you are looking into couple years of learning different areas of programming: graphics, data structures, beyond basic syntax. So it would be smart to set some simpler goals as milestones, like simple text games/programs.

But from your post I doubt you have patience and drive to do it even in simple and beginner-friendly system like Python/Pygame, not even mentioning real C++. If you are really dedicated, you can learn it all - see stickies and wiki in my sig for links. But you need to be more self-driven to get there - it is fun, but not easy.

Another option might be Game Maker - freeware for windows, which is much more visual, and you have many sample games to learn from. But there is a lot of "boring" reading too. To become a programmer you need certain mindset and a lot of patience, from your post it seems you lack both. But don't get discouraged, I would love you prove me wrong: start learning, and don't give up.

Good luck! And remember: Google is your friend and already knows the answer! :-)

---

### Post by Sockerdrickan on 2008-02-04
This thread made me :lolflag:

It sounds like he wants everyone else to learn programming and transfer the knowledge to his brain.

---

### Post by chips24 on 2008-02-04
okeday , whatever...

i will do some tutorials, ummmmm... 
 
ohhh, oh

well ok

fine.                     :lolflag:

i just realized how stupid ive been, its a good thing i dont take things to personally... i think, sorry for being stupid and thanks for youre help

---

### Post by pmasiar on 2008-02-04
> **chips24 said:**
> i just realized how stupid ive been, its a good thing i dont take things to personally... i think, sorry for being stupid and thanks for youre help

Don't worry about asking stupid questions. Do ask questions, even if it might seem like a stupid question, you will get the answer.

But do worry about not doing your homework: if someone gives you a link, do read it, and try to learn. In my experience, you can start learning in any area by reading what wikipedia has to say about it. If that is too hard to comprehend, try [http://simple.wikipedia.org/](http://simple.wikipedia.org/)

Like [Python](http://simple.wikipedia.org/wiki/Python_(programming_language)) and [Programming language](http://simple.wikipedia.org/wiki/Programming_language) and [Computer science](http://simple.wikipedia.org/wiki/Computer_science)

Stupid is not the person who ask: stupid is the one who never learns. :-) To learn asking question right way, see link in my sig. Here on ubuntu forums we are friendly with beginners. Other forums are substantially less friendly, trust me on that.

Now go and read, and have fun learning :-)

---

### Post by chips24 on 2008-02-04
i dont think stupid is usually used in the correct context, like other words that are not appropriate for this forum, stubid to me is just another way of saying i messed up, not that i cant learn, and i do agree with you, these forums rock!

---

### Post by chips24 on 2008-02-04
another reason why im so stubborn is bucause im frusterated that i dont have internet on ubuntu, the software im using is damaged or somthing, and interferes with other software. Im using vista right now.

---

### Post by dismal_denizen on 2008-02-04
OK, you have 3 options.

1. Learn a programming language and make a game from scratch
2. Replace the graphics in an existing game
3. Use a program like Game Maker or The Game Factory to make the game (since you use Windows...), which don't require any coding

Option 3 sounds like the best for you.

---

### Post by CptPicard on 2008-02-04
4. Fix the net on the Linux side so you can actually get to all the information you need. The net is your friend here. :)

---

### Post by dismal_denizen on 2008-02-04
I like option 4.

---

### Post by chips24 on 2008-02-04
> **CptPicard said:**
> 4. Fix the net on the Linux side so you can actually get to all the information you need. The net is your friend here. :)

thats the thing, i dont know how to fix it, ive tried every possible thing i can think of! but nothing works!!!
i always flip flop between windows and linux so that mkes everything complicated.

---

### Post by LaRoza on 2008-02-04
> **chips24 said:**
> thats the thing, i dont know how to fix it, ive tried every possible thing i can think of! but nothing works!!!
i always flip flop between windows and linux so that mkes everything complicated.

Then use Python, it works in both fine. See my wiki for downloads for Windows, use Synaptic in Ubuntu for downloading PyGame, if it is there.

---

### Post by chips24 on 2008-02-04
okeyday

---

### Post by NinjaNumberNine on 2009-10-14
NovaShell is the best! :)

---

### Post by jessiebrownjr on 2009-10-14
> **NinjaNumberNine said:**
> NovaShell is the best! :)
 
Congratulations on bumping an almost two year old post :-) lol.
 
I would like to comment to anybody thats bored enough to read this, that I wish I had the patience to be as nice as some of these fellas were in their responses...

---

### Post by jeffery12109 on 2010-02-08
> **chips24 said:**
> help?
2 things
first one... can I borrow the earth image.....
tooo lazy to make my own...
second thing...
you can most likely make your images like this:
if x >= 300:
        stageHorizontal += 1
        x = 299
         
        
if stageHorizontal == 1:
    PUT IMAGES
    pygame.display.update()

---

### Post by jeffery12109 on 2010-02-15
> **pmasiar said:**
> Don't worry about asking stupid questions. Do ask questions, even if it might seem like a stupid question, you will get the answer.

But do worry about not doing your homework: if someone gives you a link, do read it, and try to learn. In my experience, you can start learning in any area by reading what wikipedia has to say about it. If that is too hard to comprehend, try [http://simple.wikipedia.org/](http://simple.wikipedia.org/)

Like [Python](http://simple.wikipedia.org/wiki/Python_(programming_language)) and [Programming language](http://simple.wikipedia.org/wiki/Programming_language) and [Computer science](http://simple.wikipedia.org/wiki/Computer_science)

Stupid is not the person who ask: stupid is the one who never learns. :-) To learn asking question right way, see link in my sig. Here on ubuntu forums we are friendly with beginners. Other forums are substantially less friendly, trust me on that.

Now go and read, and have fun learning :-)

I agree with him, and you should try python with pygame.... it simple enough.... You should try to do the basic functions with the python alone...



just a suggestion

---

### Post by heamaster on 2010-02-15
> **chips24 said:**
> i found that site a bit confusing, i dont want to download any software, i want to put the game together with bitmap images and .txt documents:confused:

Put together a game with .txt-files? :popcorn:

---

