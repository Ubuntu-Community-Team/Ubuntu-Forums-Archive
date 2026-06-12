---
title: "Easy programming"
date: 2010-05-20
forum: Programming Talk
---

### Post by rhyz on 2010-05-20
Hi

I know there are a few threads like this but. . .

I was wondering what language to go for, I already know javascript, html and css.
I have looked at C++ and that was in the end boring, as it was all command prompt and terminal stuff nothing interesting. When looking at win32 stuff it went from boring to complicated. Also tried python which is very simple and nice to work with cant remember why i stopped that.

I would like to make a game but have no ideas for one i will most likley start off small and work on up as i get the language.

What language should i go for ?
Something similar to what i already know?

Thanks

P.S. Currently on windows as i have no internet connection through ubuntu, but if it comes with installer for ubuntu happy to use it

---

### Post by bapoumba on 2010-05-20
Moved to PT.

---

### Post by eluminBe on 2010-05-20
Python seems to be the best option for you but .. NO! to Python games.

---

### Post by rhyz on 2010-05-20
Sorry for posting in wrong place :oops:

Why no to games in python ?

python supports openGL and pygame but openGL looks a little complicated

---

### Post by KdotJ on 2010-05-20
Java is very portable, and you say you have looked at C++. Java is different to C++ but more similar to C++ than python is.

You say about the C++ you've seen only being command line, but there are tons of GUI toolkits out there for C++ if you are willing to put the effort in to learn.

However in java you can make use of Swing which is its own built in GUI framework which doesn't require any extra packages/libraries to be installed on the machine in order for the GUI to work

---

### Post by eluminBe on 2010-05-20
> **rhyz said:**
> Sorry for posting in wrong place :oops:

Why no to games in python ?

python supports openGL and pygame but openGL looks a little complicated

IMO, you can create a game in PHP and JavaScript, too .. everything depends on what you are planing to achieve.
Ever imagined yourself playing any of the best selling ( I'm not talking about money here - pure quality / entertainment ) games if they would be made in Python ? [COLOR=Gray]Loading ...
[/COLOR]

---

### Post by .:PiXi²:. on 2010-05-20
ActionScript should also be an option. The choice of which language an library's should depend on aspects that your game will need to have. Give us some details about your idea...

---

### Post by rhyz on 2010-05-20
Thanks for replys i have also tried java and would have liked to get on with it but things have never seemed to work for me (using windows). The install never seems to go smooth and once done things dont seem to work properly.

But did you mean it is already available in ubuntu?

Also php and javascript sounds good im already half way their :) examples of games already out there. Tutorials?

---

### Post by Yarui on 2010-05-20
I think the reason eluminBe says no to python for games is because python doesn't compile the code ahead of time, but instead interprets the code during runtime, making code execute more slowly than in many other languages.  You can still make simple games just to learn the methods, but if you want to make a very complex and processor intensive game that requires flawless timing, python probably isn't the best way to go.  Just decide for yourself if python is right for the kind of game you want to make.  In the worst case you would learn a little bit from doing something in python and then decide to start over using something that works better for you.

EDIT: Another disadvantage to making python games is the need to have the python interpreter installed to play them.  If you plan on sharing the games many people would prefer being given an executable program rather than a python file.  Other languages have similar disadvantages, though.  Java requires a java runtime application to be installed (which most people have), while others need to be compiled separately for each operating system, sometimes requiring changes to be made to the code.

As far as C++ being boring to you goes, command prompt programming isn't entirely useless as a learning method.  Almost everything you learn from programming in the command prompt transfers over to graphical applications.  It is good to start with command prompt programming to learn good programming practices without having to deal with all of the extra stuff that graphical programming involves.  If you absolutely can't stand it, though, you are best off finding a good API to program with.  A lot of API programming might be somewhat boring to you too, if all you are interested in is programming games.  Most of what you would make in an API is just the same kinds of things you would make in the command prompt, but you get to map functions to buttons.  If you are mainly just interested in video game programming, I would recommend finding a good book on the subject.

---

### Post by eluminBe on 2010-05-20
> **rhyz said:**
> 
Also php and javascript sounds good im already half way their :) examples of games already out there. Tutorials?

[LostWorlds]("http://www.lostworlds.lv/"), [Ikariam]("http://us.ikariam.com/"), etc. - tons of other / similar examples available .. use Google ( *browser based games* ).

---

### Post by rhyz on 2010-05-20
Well c++ command prompt got boring as i had already input and output data and that seemed to be it i think i even made a guessing game.

The reason i have learned html javascript and css is because everything you type happens.

Any one could tell me what is going to happen here
```

<input type="button" value="MY BUTTON" onclick="document.getElementById('mybox').style.visibility='hidden';">

```

Its so simple easy to read and in one line of text you have a button with text, that can change a <div> from visible to hidden.

After messing around with C++ for a evening i was a bit boared as it didnt really ammount to anything it made me feel good but you show it to a family member and they think so what.

What exsactly is a API?
I dont have any ideas for games really i think im looking for something that will allow me to start simple and then allow me to get more complex and to be able to make something people may want to play, but really it would only be a hobby. Getting other people interested would be a bonus.

---

### Post by rhyz on 2010-05-20
> 
LostWorlds, Ikariam, etc. - tons of other / similar examples available .. use Google ( browser based games ).


Ahh i see :) i remember playing neopets when i was little spent hours on it :)

---

### Post by Yarui on 2010-05-20
> **rhyz said:**
> Well c++ command prompt got boring as i had already input and output data and that seemed to be it i think i even made a guessing game.

The reason i have learned html javascript and css is because everything you type happens.

This is understandable,  I probably would have never done much more than that had I not taken a class to program with C++, it can be hard to come up with ideas for programs that seem interesting.  When you are learning to program, though, sometimes you can't make something that will impress your friends and family right away.  You may be ecstatic to make your first "Hello World" program, but few others will really understand that excitement.  If you enjoy it, though, don't worry about impressing your family, just enjoy it for yourself.  I'm not pushing C++, I'm just speaking of programming in general.

I also know what you mean when you say you like how simple it is to read and understand higher level languages.  I started with C++ and when I later learned to write javascript and python I was extremely satisfied with the results almost immediately.  They are fun languages to use, but it is always good to learn other languages so that you don't get stuck using a single one.

API is short for application programming interface.  It is a set of tools that makes it easier to write programs.  They normally have tools that make graphical programming much easier.  Visual Studio is the microsft API, but there are countless others.  I have heard good things about eclipse for web development.  If you want to make applications in windows that have some data entry fields and buttons and other such things, those buttons and data fields are referred to as widgets.  If you read a bit about widgets you will probably come by a good API for widget-based development.  There are probably APIs that are specialized for game making, too.  If you ask around in some game making communities you could probably get some recommendations for good game making APIs.

---

### Post by Yarui on 2010-05-20
If you really want to learn about making video games and get some quick insight into how things work, there are also tons of video game making tools available online.  I have spent a little time working with Multimedia Fusion 2.  If memory serves me correctly it was free.  There isn't any plain text programming involved, but you do create procedures through a point and click interface that are very similar to the kinds of procedures you would create in plain text programming.  Using a tool like this could take out the more difficult aspects of getting started with programming video games, and they are used by many successful indie video game makers.  After getting some experience with these kinds of tools you could decide to take the plunge into coding your own videogames from scratch, or you could decide that you like them enough to continue using them.

---

### Post by Can+~ on 2010-05-20
> **eluminBe said:**
> IMO, you can create a game in PHP and JavaScript, too .. everything depends on what you are planing to achieve.
Ever imagined yourself playing any of the best selling ( I'm not talking about money here - pure quality / entertainment ) games if they would be made in Python ? [COLOR=Gray]Loading ...
[/COLOR]

Let me guess how this conversation goes: "C++ is for games, so if you want to develop a game, do it in C++". Or, "My favorite language is X, so I recommend you X".

Yes, I know C/C++ whatever/language is faster than python, and thus, commercial games are done with it/your game is done with it, but it doesn't matter when you're a newbie. Choosing speed over ease of use for a newbie programmer, is like handing a motorcycle to a kid that all that needed was a bike, clearly irresponsible parenting.

Back to the OP, the easiest path I can think of having immediate visual feedback, is programs like Flash (unfortunately, paid), or game-specific engines, like the Source Engine, Warcraft Engine. Yes, sounds weird, but the easiest path, is the one where all graphical/sound problems have been solved and wrapped around a cute editor, games which offer Map-building facilities and a form of scripting language (UScript, Warcraft command-based instructions) are seriously the easiest ways to go.

I feel that you're still pretty young, as code alone doesn't do it for you, and your eagerness to jump around languages without "majoring" any of them.

If you still want to go for a full-featured language; I would recommend Python and Pygame for learning purposes, Python is pretty much all rounded corners and pygame is a very simplistic abstraction of SDL.

---

### Post by Yarui on 2010-05-20
> **Can+~ said:**
> 
Yes, I know C/C++ whatever/language is faster than python, and thus, commercial games are done with it/your game is done with it, but it doesn't matter when you're a newbie. Choosing speed over ease of use for a newbie programmer, is like handing a motorcycle to a kid that all that needed was a bike

Back to the OP, the easiest path I can think of having immediate visual feedback, is programs like Flash or game-specific engines

If you still want to go for a full-featured language; I would recommend Python and Pygame for learning purposes, Python is pretty much all rounded corners and pygame is a very simplistic abstraction of SDL.

I fully agree with this.  Like I said before, game creation kits like multimedia fusion can be good.  Can+~ makes a good point, though, using commercial game engines is another good way of getting started.

I have looked at pygame a bit and they have a great tutorials page:

[http://www.pygame.org/wiki/tutorials](http://www.pygame.org/wiki/tutorials)

I especially like the following tutorial:

[http://eli.thegreenplace.net/category/programming/python/pygame-tutorial/](http://eli.thegreenplace.net/category/programming/python/pygame-tutorial/)

but I suppose that is just personal preference.

---

### Post by eluminBe on 2010-05-20
> **Can+~ said:**
> Let me guess how this conversation goes: "C++ is for games, so if you want to develop a game, do it in C++". Or, "My favorite language is X, so I recommend you X".

Yes, I know C/C++ whatever/language is faster than python, and thus, commercial games are done with it/your game is done with it, but it doesn't matter when you're a newbie. Choosing speed over ease of use for a newbie programmer, is like handing a motorcycle to a kid that all that needed was a bike, clearly irresponsible parenting.


C isn't for games, C++ isn't for games, neither Python is .. I didn't meant to say that it's wrong to use what you have access to - as previously stated, everything depends on what you are trying to achieve .. a game which just works or a game which you can extend and understand the roots of it, not just how to tell the user to click here or there.

---

### Post by Yarui on 2010-05-20
> **eluminBe said:**
> C isn't for games, C++ isn't for games, neither Python is .. I didn't meant to say that it's wrong to use what you have access to - as previously stated, everything depends on what you are trying to achieve .. a game which just works or a game which you can extend and understand the roots of it, not just how to tell the user to click here or there.

Well, I would argue that few languages are "for games".  The languages are for manipulating the computer to do what you would like it to, and making games just happens to be what the programmer wants to do with it.  There are some specialty languages that are just for games, but I don't hear anyone recommending any of those anyway.  Like you say, it basically comes down to what you know how to use and weighing the pros and cons of each language.  However I don't agree that any of the other suggested methods are simply telling the user to click here and there.  Using game development kits can give huge insight into the inner workings of video games.  If that is where the user feels most comfortable starting, that is again a personal choice.

---

### Post by ja660k on 2010-05-20
You all know that EVE online is written in python?
and runescape written in Java

It all depends on what kind of game you want to make, 
mobile, browser, console/pc.

---

### Post by lisati on 2010-05-20
> **ja660k said:**
> You all know that EVE online is written in python?
and runescape written in Java

It all depends on what kind of game you want to make, 
mobile, browser, console/pc.

That reminds me: I've seen versions of the original "[Colossal Cave]("http://www.rickadams.org/adventure/")" text-based adventure game written in Fortran. I wouldn't recommend trying something like that to a beginner (text stuff in Fortran), because it could result in them ending up in a twisty maze of passageways, all alike...

---

### Post by Rususeruru on 2010-05-20
C++ is a great language if you plan on making a career out of development, but I wouldn't recommend it if you're looking to jump straight into GUI programs.  Microsoft Visual C++ is good for toying around with GUI's in C++. I'm not aware of any free open source software that offers such an easy to use toybox.

I find Java syntactically is very similar to C++ so if you want to play with GUI stuff and think you'd like to get into desktop development, go ahead and jump into Java using Swing.  Be warned that a Swing GUI will not run as fast as a C++ GUI implementation (though things are getting better) since Java is an interpreted language not native code like C++.  I've done a couple of projects in Java using Netbeans, but I find that Netbeans causes a mess when you're dealing with many graphical elements so perhaps the community could offer a better IDE, I haven't played with Eclipse enough to familiarize myself.

Since you already know markup languages Python may be the way to go since it's easier to read, if performance isn't a major concern and you're looking for some quick gratification.  I'm actually just diving into python myself coming from a Java/C++ background.

---

### Post by .:PiXi²:. on 2010-05-22
> **Rususeruru said:**
> C++ is a great language if you plan on making a career out of development, but I wouldn't recommend it if you're looking to jump straight into GUI programs.  Microsoft Visual C++ is good for toying around with GUI's in C++. I'm not aware of any free open source software that offers such an easy to use toybox.
...

Have you ever tried [Qt]("http://qt.nokia.com/")? Just give it a try, you will be impressed.

---

### Post by simeon87 on 2010-05-22
I'm not sure what the topic starter is looking for.. languages for game programming or simply an easy ride? If you quickly get bored by writing code that doesn't quickly give results on the screen, you'll likely give up after moving some sprites around. Games in 3D are out of the question and even in 2D there's a lot going on in a sufficiently advanced game.

Building something like a client/server architecture can be quite fun but it'll take a while before you can play something decent with your friends. Consider the following: if you always do easy things, you'll never grow as a programmer.

---

### Post by .:PiXi²:. on 2010-05-22
Making a game in ActionScript using Flash Professional and Flash Builder should not be too hard. The software is not free, but there are open source alternatives.

---

### Post by rhyz on 2010-05-23
Wow Thankyou everyone for your input i didnt expect all these replys :)

I have always wanted to try flash but of course dont want to pay for it, i know there is a trial but thats also a fat download so ... What are the alternatives to flash (programs)?

I think i might give PHP + Javascript a go but i need to sort out wireless connection for that, but maybe i should have another look at c++ but i would like to know how i can make a window and add images ect a simple tutorial?

Difference of C and C++ ?

Finally i think im pointing to c++ more as you can start off just in console and work your way up like i did with html etc

start on text based html page and make it better, i was quite happy with my final results :) so hopefully it will work with c++

---

### Post by KdotJ on 2010-05-23
> **rhyz said:**
> 

Finally i think im pointing to c++ more as you can start off just in console and work your way up like i did with html etc

start on text based html page and make it better, i was quite happy with my final results :) so hopefully it will work with c++

Good thinking, C++ is great. And working with console I think is better to start with while you're actually learning how to program. Then when you go for GUI programs, I would recommend Qt to use with C++, it's very nice and clean

---

