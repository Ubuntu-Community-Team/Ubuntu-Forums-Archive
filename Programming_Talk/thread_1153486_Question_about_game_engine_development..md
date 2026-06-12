---
title: "Question about game engine development."
date: 2009-05-08
forum: Programming Talk
---

### Post by hockey97 on 2009-05-08
Hi, I am thinking in the near future to create 2 things one a game engine and another is a OS. 

this OS is small nothing like windows. More like a embedded OS. 

I currently am learning. I don't plan to do this overnight or anytime soon.

So I am asking here where I should start. I know c++ and also object oriented programming. 

I have looked at open source game engines. I even bought books on 3d game engine but those books are outdate. They teach how to make a fake 3d game.

the one from the old days where like for example your a  race car so your on a  tract the closer you get to another car that is in front of you the bigger the rescaling the size of that cars image becomes to make it seem as if your behind him and your getting closer to him.

a guy that worked at Microsoft and nasa as a software engineer.

He told me the best way to learn and be comfortable with game engines is to go and grab open source game engines and read their code and try to understand the code.

so I ask here:  what do you think I should look into in order to make game engines and OS.

I did looked at tutorials on easyO'S and Assembly code.

just woundering if any can give me any good advice on going abouts making such a thing.

Like for example what math would I exactly need to know to do such a thing.

I am interested to going to the libary picking up some math books to learn over the summer.

So I just am looking for advice. My long term goal is to make a game engine and an OS. 

the OS won't be as big as windows. It's more like a OS of a eletronic device like a dvd type device. I do know windows is complex cause it needs to handly many things. Where as a dvd player just needs to read a dvd and then proccess that data and then render the data onto the screen (tv).

Thanks for your time. I am currently in the middel of learning assembally.

---

### Post by iblis on 2009-05-08
> **hockey97 said:**
> Hi, I am thinking in the near future to create 2 things one a game engine and another is a OS. 

I don't mean to discourage you, but for either, I hope you have a lot of time on your hands.

> 
So I am asking here where I should start. I know c++ and also object oriented programming. 

I have looked at open source game engines. I even bought books on 3d game engine but those books are outdate. They teach how to make a fake 3d game.

the one from the old days where like for example your a  race car so your on a  tract the closer you get to another car that is in front of you the bigger the rescaling the size of that cars image becomes to make it seem as if your behind him and your getting closer to him.

a guy that worked at Microsoft and nasa as a software engineer.

He told me the best way to learn and be comfortable with game engines is to go and grab open source game engines and read their code and try to understand the code.

so I ask here:  what do you think I should look into in order to make game engines and OS.

_[Open source engines](http://en.wikipedia.org/wiki/List_of_game_engines#Open-source_engines)_.

I suggest taking a peek at OGRE, if you haven't already. Also, Panda3d.

Delta3d doesn't look half bad, though I haven't browsed the source.

You might want to start out with mastering using an engine first - make a game with it, I mean - and then worry about writing your own. Believe me, after doing so, you'll have plenty of first hand experience on what you might do differently. 

Hope this helps.

---

### Post by noerrorsfound on 2009-05-08
> **hockey97 said:**
> So I am asking here where I should start. I know c++ and also object oriented programming.
Have you already created many C++ projects? I'm a beginner, and I know that before doing any serious games, one has to be comfortable with the language itself. (Meaning, for example, creating a text-based card game before a graphical one that uses additional libraries, to ensure that I know the fundamentals.)

---

### Post by hockey97 on 2009-05-09
well, I do have experience with c++. 

I have played around with some free 3d game engine. I also used a A 3d game engine. 

I done labs made mini games. Nothing too complex. 

The problem is that even working with a game engine the game engine done most of the math for the game. Like allI had to do was use their function to render a 3d model on the screen. I mean you can make modifications but I never went in grade detail about it.

I was told that the best way to learn is to read open source. I know c++. I know some python. I always heard python is the way to go. I also heard python runs slower then c++ apps. So I never had interest in python and never went full out on it.

the software engineer knew I know c++ and programming baics good enough thtat I can read other peoples code. 

he told me to read a open source engine and also learn more math.

He said todays graphics has alot of math involved to calculate every drawn frame that shows on screen.

So I just wanted some more input.

---

### Post by Reiger on 2009-05-09
Creating a 3d physics engine (which is by all means a core component of a game engine that wants to simulate 3d worlds) begins with an unholy amount of Math practice. Are you familiar with calculating a 60 degree rotation over the Z-axis of an object by using matrix multiplication yet? :P

---

### Post by hockey97 on 2009-05-09
I am familiar with matrix multiplication. I never had heavy pratice with it.

I learned basics of it in high school. so to answer your question no.

That is why I plan to learn the math I will need. This summer I plan to go to the library and check out math books that I need.

I do own a fake 3d game engine not really 3d but 2d graphics that acts like 3d environment. 

So this is what I want to rack up. Is their any website or a big list that shows what type of math I would need to learn. 

Do you think it would be in the game developer website. 

I am more interested in the math. cause I think what I mostly need is to look at open source 3d game engine. and also the math to understand what a game engine is.

I know a game engine is nothing but code that uses direct x or opengl.

I always wandered how direct x and open gl was created.

I was told  they are created by some assembly code but mostly either c or c++. 

I am not sure myself but I am trying to get on  a right path to be able to make a game engine .

what I was told is that a game engine is nothing but classes that have reusable code.

I was explained that you need to know about programming games. 

So you can understand what game makers need.

A game engine is usally for programmers to not focus on working on hardware and talking to the OS directly.

So the game makers just focus on making the games using your code .

So I have to at least know graphics programming and graphics math.

also physicas and audio and media playback.  all that to make a game engine to produce a game.

the OS is another area. It's nothing but code to make a device run.

I plan to make an OS that is not like a windows os or anything like that.

I plan on making a small os for a device that reads a cd image and other stuff but nothing as heavy as a Full blown OS.

So from what I see I just need to learn the math. Then I need to see how the math gets used. I got to see some engines that are open. 

Once I understand everything a 3d game engine has  then I can start on one.

Now My goal is not to make a professioanl game engine just one that works.

Once I finish that I can then work on making it professional.

I heard that most game engines are not made from scratch.

They usally copy and past all code that already takes care of old graphics and other old problems.

They said when your focused on making a game engine you should only focus on creating new stuff not reinventing the wheel but you still have to know what the old stuff is and was.

---

