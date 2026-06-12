---
title: "I am making a Game Maker"
date: 2007-08-15
forum: Programming Talk
---

### Post by dark joev on 2007-08-15
Hi,
I am thinking of building a game maker for ubuntu I am going to either use C++ or Python I am  not sure so I am developing the maker in both until I can make a decision. It will have support for the usual FPS,RPG,MMO/ORPG,RTS that is what I am going to try to make the maker support if you have any Ideas for freatures or anything or if you think it would even be popular and were would be a good place to host it.

I am about 2 weeks into making it.

---

### Post by Swarms on 2007-08-15
> were would be a good place to host it.
Sourceforge?

I will look forward to it!

---

### Post by kostkon on 2007-08-15
Hi,

You have a very good idea here as there are not any game makers for Linux at the moment. I wish you the best of luck for your project!

I am happy seeing new projects for Linux popping up all the time. It says a lot.

Now, I would like to recommend you to host your project at *Launchpad*. For many reason is a very good service, but I am saying this because from 22nd of August, *you will be able to have your own repository (1GB space) for free*, throught the PPA feature!! Thus, you will be able to give people your repository to install your application and get automatic updates!

Also, you will get automatic builds of your code!!

You will not even need to apply for inclusion of your application to the official Ubuntu repositories, because, as fas I see it, having your own safe and officially recognised by Canonical repository would be sufficient to the success of your project.

---

### Post by dark joev on 2007-08-15
Thanks for the info I have a launchpad account so that is cool

---

### Post by Wybiral on 2007-08-15
I've had some experience with both 2d and 3d object based game engines. I would be glad to pitch in on some areas of code if you ever need an extra hand.

My advice on language... Write the engine in C++ and use Python for the game "script ability" (things that you may want your users to be able to change/script, this would work great since python is so easy to learn).

---

### Post by dark joev on 2007-08-15
That is what I was thinking caues I love C++ coding but I made the switch and everyone was going crazy over python and I look at pygame and that looked like it was easy to use.

but I noticed the lack of game makers for linux so that is when it came to me make your own game maker but windows made me use game makers(Cause I am lazy when on windows) cause game engines take a long time to make and well I was going for quickness of releasing games.


So I have made a page on my webpage look in signature the engine is called Alpha Z3l3

---

### Post by Wybiral on 2007-08-15
Is this going to be 2d or 3d?

---

### Post by dark joev on 2007-08-15
I think I am going to work on 2d then may make it later to be 3d because then I will later beable allow it to be both 3d and 2d so then more users will use it.
Should I use Glade or Qt3

---

### Post by misfitpierce on 2007-08-15
Excellent idea... Sourceforge or i think launchpad has stuff for that. :) look forward to it.

---

### Post by dark joev on 2007-08-15
I am glad I am getting this much feed back.

---

### Post by Wybiral on 2007-08-15
> **dark joev said:**
> I think I am going to work on 2d then may make it later to be 3d because then I will later beable allow it to be both 3d and 2d so then more users will use it.
Should I use Glade or Qt3

You should use SDL and OpenGL (especially if you plan to move it to 3d) but even if you plan 2d as well.

Have you ever written a game engine before?

---

### Post by pmasiar on 2007-08-15
> **dark joev said:**
> Hi,
I am thinking of building a game maker for ubuntu I am going to either use C++ or Python 

Excellent idea, I was suggesting that to many people asking for project idea! Couple suggestions:

1) Make sure you spend some time playing with excellent freeware [Game maker](http://en.wikipedia.org/wiki/Game_maker) so you get a clue how really intuitive it might be.
2) Don't press too hard to make in MMO/RPG at first. Your best bet is to release something usable, so other can use it and help you improving it. I would suggest focusing on platform games only in first version: it has 80% of needed playability with 20% of the complications (no multiuser, no need of AI, etc)
3) Forget about C at first. Do everything in Python, you (or any C gurus) can optimize anything later, if design is sane.
4) Don't over-engineer things. You will likely throw away one or two versions before you will learn how it really should be done.
5) Consider Pygames as your platform, and simplest thing  which possibly can work, for one type of game. Your goal is to "release early, release often" to build community. Look how they build games, build one or two to learn Python and Pygames.
6) Remember, you can automate only something you understand deeply, you need to build 3 different systems by hand to learn how to generalize them.
7) Don't get discouraged, if people will tell you it is hard. Yes it is, it will take months to have something usable. That's why is important to make first version as simple as possible: release pilot version so other can look at it and help you. 

I am really excited that someone is taking on this one, feel free ask more help here or PM me anytime. 

Hosting: Sourceforge was good choice long time ago, but not anymore. Google code is faster (more responsive) and much simpler, I have no first-hand experience with Launchpad but it could be good choice too, because of the easy reach to all Ubuntu users (to build community fast).

Good luck, and keep us posted!

---

### Post by dark joev on 2007-08-15
I have built a engine before but it used DirectX and it was in its early stages and it wasn't that great so I have some experience I was looking at using OpenGL as I have hardly used SDL Before. I am going to start working on some early versions of it. I was thinking of starting with something simple like a platform game.

---

### Post by Wybiral on 2007-08-15
> **dark joev said:**
> I have built a engine before but it used DirectX and it was in its early stages and it wasn't that great so I have some experience I was looking at using OpenGL as I have hardly used SDL Before. I am going to start working on some early versions of it. I was thinking of starting with something simple like a platform game.

SDL can be used in combination with SDL... I HIGHLY recommend this as it gives you lots of portability in the C side of things.

But... I agree with pmasiar to an extent. My experience with game engines suggests that it's VERY difficult to write a fast enough (full featured) engine in a high level language like python. BUT... Python is perfect for everything but the core of the engine. Do all of the rendering and detail code in C/C++ but handle all of the organization and game code in Python.

I can help with this in case you've never interfaced the two (it's pretty easy).

The advantage is that you get the core speed of your compiled language for the CPU intense stuff. But you also get the magic of not having to recompile the engine every time just to do the user interface/scripting stuff.

And when it comes to writing a script engine for your game maker... STOP... No need, python is there :)

---

### Post by dark joev on 2007-08-15
Yea I have been playing with python and I think I will use it as the engines scripting language as for interfacing the together I haven't done that before but one of my friends said he would do it but I think I would like to know caues he isn't the best at actually doing it.(By That I mean actually getting around to working with the engine and integrating them together.

I have only began using python and am making a game in python it is pretty easy.

I will look into SDL

---

### Post by Mickeysofine1972 on 2007-08-16
You could save yourself a lot of coding by using the gamepower 2d library that DARKGuy created for the iTeam project.

Maybe Wybiral could help you make a Python interface for it. Its very easy to use and has most of the stuff you will need in terms of displaying and manipulation.

Also, my ubuntu gamedev wiki,([http://ubuntu-gamedev.wikispaces.com](http://ubuntu-gamedev.wikispaces.com)), has info about making tiled game worlds which will get you well on your way to a platform game.

I'm currently tied up with the iTeam project at the moment but I would be happy to help out later when I'm not blowing up little sprites and stuff.

Mike

---

### Post by batrick on 2007-08-16
You should consider Lua for the scripting language. It's pretty standard in games. It's stupid fast, flexible, and powerful.

---

### Post by vexorian on 2007-08-16
> I am thinking of building a game maker for ubuntu I am going to either use C++ or Python I am not sure so I am developing the maker in both until I can make a decision sorry but that's just a terrible idea, you should decide before coding, no need to double development time by 2. It is a common mistake to start coding too soon, for example I made it, I released a game that had terrible code design, it still costs me development time it shouldn't.

opinion: You should just make the engine in C(++) and let it have bindings to python and many other languages...

---

### Post by pmasiar on 2007-08-16
> **vexorian said:**
> opinion: You should just make the engine in C(++) and let it have bindings to python and many other languages...

Let me disagree. There are at least half a dozen engines, what is direly needed (like Windows has) is simpler intuitive GUI to create games, - Game Maker from my first response (#12).

But looks like OP is not interested in doing what is missing, creating yet another half-finished engine to be abandoned later. oh well... :-(

---

### Post by CptPicard on 2007-08-16
The problem is that games made by game makers mostly suck... it would be better if people with competence in programming concentrated on making games. :)

---

### Post by Wybiral on 2007-08-16
> **CptPicard said:**
> The problem is that games made by game makers mostly suck... it would be better if people with competence in programming concentrated on making games. :)

I don't think that's the point... Game makers let non-programmers make their own game. Sucky or not, it's a creative outlet that non-programmers would otherwise not have.

---

### Post by Steveway on 2007-08-16
Yes, that is a nice and interesting project.
Keep on going I'm gonna look if I can help, I don't have much programming experience but I can help with translations and a little bit with artwork.
Have you considered something like the RPGmakers, I liked them back in my windows days.

---

### Post by CptPicard on 2007-08-16
> **Wybiral said:**
> I don't think that's the point... Game makers let non-programmers make their own game. Sucky or not, it's a creative outlet that non-programmers would otherwise not have.

But you're still very much limited by whatever the engine allows you to do, and there is no such thing as a "generalized game maker" that lets you make any game. Whenever you're implementing your own functionality, you're almost by definition approaching programming.

---

### Post by Wybiral on 2007-08-16
> **CptPicard said:**
> But you're still very much limited by whatever the engine allows you to do, and there is no such thing as a "generalized game maker" that lets you make any game. Whenever you're implementing your own functionality, you're almost by definition approaching programming.

Most people using game makers just want to implement their own storyline and have the joy of making their game come to life.

And... Since most game makers will require some minor scripting in parts where they need more control, it's a good way for non-programmers to get a taste of programming.

That's why I say that the scripting language should be Python. It's easy to learn, and the users will be learning to program in Python whenever they write scripts for their games.

I see nothing bad about game makers at all... As I said, if nothing, it's just another creative outlet for people who haven't invested the time to learn programming far enough to program their own game.

---

### Post by pmasiar on 2007-08-16
> **CptPicard said:**
> there is no such thing as a "generalized game maker" that lets you make any game. Whenever you're implementing your own functionality, you're almost by definition approaching programming.

I strongly disagree, I am on the side of Wybiral. Programming a game does not have to involve OOP, compiling, C++/Java debugging. It has to be fun and within possibilities and grasp of a kid - and it is possible.

Free Game Maker for Windows allows you to write wide selection of game styles, and is so intuitive (using LEGO-style GUI to manipulate programming "blocks") that 10 years old can create playable game. I mean, platform game like million other platform games, but all is done by the kid: graphics, events, objects, interaction. No text files, no syntax, no editors. You need to try it to understand - but obviously hardly anyone bothered to try [Game Maker](http://en.wikipedia.org/wiki/Game_maker) to understand what state-of-the-art is.

---

### Post by AlexThomson_NZ on 2007-08-16
I recall an old program on the Amiga called AMOS, which was was basically a very high level programming language similar to BASIC, but very much geared toward 2d game development.  This was very popular back then, and still has a cult following even now.

Is it something along these lines you are thinking of?

---

### Post by slavik on 2007-08-16
while I think creating a game maker for many types of games is tough (you have to make lots of assumptions and predict the future), it gives the person some understanding of the difficulty certain projects involve.

I tried implementing my own huffman coding program (bzip2 does this) and the first timearound (looking at the code now), I am disgusted by some of the things I did (backwards and not nice), but now, after seeing many others' code and how some people do things, I have realised better ways to do things.

I am also trying to write OO C code. :)

---

### Post by dark joev on 2007-08-17
In my windows days I used DarkBasic, Realm Crafter, Game Maker Pro, Tried Torque, Genesis 3D, Source SDK(Half-life 2 engine =Crashing 100% of the time) 
and the reason I want to make this game maker is beacues if Ubuntu's community is serious about getting the market we need to have more and better programs and we also need to give the windows (Non-Programmer) a easy to use environment (Less terminal needed). Ok back on topic we need to have game engine designed for both Programmers(Which We Have) and Non-Programmers (We might have but few of them are good).

---

### Post by Mickeysofine1972 on 2007-08-17
Actually, I used DarkBASIC a while back and found it very easy to use. I'd like to see that sort of program happen whether it basic or python I don't care, but you could still generate a template wizard driven code generator for those guys who just want to create games based on a set of menu options.

Sounds great! I'm getting excited about it already!

Mike

---

### Post by ssam on 2007-08-17
you might want to post about it in the [http://happypenguin.org/](http://happypenguin.org/) forums. you might find some more people interested in helping.

---

### Post by pmasiar on 2007-08-17
> **dark joev said:**
> In my windows days I used ... Game Maker Pro

Game Maker written by Mark Overmars? So **you know** what I am talking about!

> if Ubuntu's community is serious ... we need to have game engine designed for both Programmers (Which We Have) and Non-Programmers (We might have but few of them are good).

Get them while they are young! 

We already have many game engines for programmers.  Why I am so excited about Mark Overmars Game Maker is, 10 years old kids can use it, because it does not require reading and editing huge amounts of text.

BTW my guess is, if your code will be usable, it could be wild success with $100 laptop folks.

I can help you with design if you want me to, msg me.

---

### Post by dark joev on 2007-08-17
I made a forum for the Game maker at [http://alphaz3l3.freeforums.org/]("http://alphaz3l3.freeforums.org/")
and I will be updating the look of the forum and I haven't ran forums ever so I am learning.

---

### Post by slavik on 2007-08-17
> **dark joev said:**
> ...  a easy to use environment (Less terminal needed).

"Right tool for the job" many say.

---

### Post by dark joev on 2007-08-18
yea but windows users don't have to ever open the command prompt ever to get a program installed and we need to have it so that a windows user can easly make the switch so maybe a program to automate some of the terminal commands I mean I am use to the Terminal

---

### Post by slavik on 2007-08-18
> **dark joev said:**
> yea but windows users don't have to ever open the command prompt ever to get a program installed and we need to have it so that a windows user can easly make the switch so maybe a program to automate some of the terminal commands I mean I am use to the Terminal
synaptic ...

cat logfile.log | grep errorcode | less

gives you a list of error lines with the specific errorcode and allows you to compare the time on all of them.

---

### Post by dark joev on 2007-08-18
Yea but if you listen to all the windows users that bash Linux could develop a easy to use program to make it so no terminal use is need and all you need to do is use this program (Insert name) and it will compile the source and/or install it and put a Icon on the desktop or in the Applications section so then it shows up and the user dosen't have to do the compile by them selves then I think it would be a lot better this may be another project I will start to work on while I am working on the Game Maker which I am going to get help from some of my friends to maybe speed up some development time. I will be keeping everyone posted I will most likely have it so that there will be a Dev team set up to handle the modifications to the engine and/or maker and from there decide whether or not to include it into a official release of the engine kinda like how ubuntu does it and also allow people to just download the engine.

---

### Post by dark joev on 2007-08-20
sadly I am about to go back to school so my freetime will be less and I will just be able to work on the project when I get the Time to so please be patent

---

### Post by Note360 on 2007-08-20
I would suggest doing something like this.

Write the core code in C++ (the stuff that needs to be fast) write the GUI in either C++ or python and have all scripting in python via Python bindings to your C++ stuff.

---

### Post by cmat on 2007-08-20
A 3d engine with support for free 3d formats and collision detection would be really great. Excellent to see someone taking initiative to support the open source community.

---

### Post by Fonon on 2007-08-20
This will be a great idea!  I used to use Game Maker in my Windows days, and I have a friend who creates really good games with GM.  I'd help with this project if I could, but I'm a newbie at programming, and so, I couldn't offer anything useful.  SOrry :(

---

### Post by Stamat on 2008-12-04
"I am making a Game Maker" is a serious statement to make. As the Pmasiar said, the project needs to be well done so you can get kids addicted while they are still young... Like myself,i always wanted to be biologist and make an artificial being but than i started a game in game maker 2.0 when i was a bit older kid, about 13 years old and since then i am a programmer. I discovered a world of where can you express your creativity with no limitations other than your intelligence and dedicated myself to develop a good AI. Developed my work over 8 years almost, and did some fancy stuff no one in this whole dump of a country called Serbia ever dreamed of (not much to be proud of, but anyway ;))... that is how its like when you become a programmer whit your soul not with the mind... cause most people do not consider programming like this but i consider it as an art...

I went to a forum the topic creator posted, and by the looks of the logo i can see why this project never made it... 
Well if anyone still tries to make it, it better not be like "Multi media factory" or how it is called cause an "IDE" if i can call it like that makes what visual basic makes of an student who is about to start his venture to a world of programming...

Game Maker is a powerful tool, indeed which explains OOP very well to starters. I used it to explain the classes and object manifestations to a programming classes i held...

Well, as i was saying... if anyone still tries to make it, please post links,demos, something... i will be glad to be a part of it and help as much as i can... if not, the next free space (if there will ever be free space) for a project will be filled with this topic and developed by iVar.

Until than we w8 :popcorn:

---

