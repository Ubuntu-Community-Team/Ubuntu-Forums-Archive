---
title: "HOWTO: Animating Sprites using SDL"
date: 2006-11-25
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2006-11-25
Hi all

You be pleased to know that these a new HOWTO on the The Ubuntu Game Developers Resource.

Here the link:
[http://ubuntu-gamedev.pbwiki.com/](http://ubuntu-gamedev.pbwiki.com/)

Mike

---

### Post by Choad on 2006-11-25
sweet

---

### Post by Choad on 2006-11-25
ok i know this isnt c++ tutorials but what the hell, i'll ask anyway

you made an animation.h file for the animation class, but then you put all of its function definitions in the main file.

why is this?

because it would be alot tidier **if** you could stick em all together in the animation.h file

---

### Post by Mickeysofine1972 on 2006-11-25
Actually it would be even tidier if the class methods where put in thier own cpp file and the anumation.cpp on contained the main program functions :-D

As it is, the .h is for definitions of classed and other stuff like that and the cpp is for code. So, I cheated a bit and put all my code in one file for simplicity of compiling.

As a test of you metal you might like to try and implement the separate cpp for the class and compile and link it. That will give you and idea of why I did it the way I did. ;-)

Mike

---

### Post by Choad on 2006-11-25
hmmm could be worth a shot! would certainly teach me alot

i do have to get some food at some point today else i'll be going hungry tonight. stupid lack of parents to do stuff for me

---

### Post by Mickeysofine1972 on 2006-11-25
This will be a seminal moment for you then - learn to make more complex programs and fend for yourself LOL

Mike

---

### Post by VDM on 2006-11-26
The animation uses a delay to wait to go to the next frame.
If you want to use a lot of animations, you will find out that works pretty anoying since your game will be spending all the time waiting for the animations. You can edit the example pretty easly and use Timers. You simply check on the current time vs the time your frame started. when it exceeds 5 secons you call nextframe and reset the timer to start with the current time.

Another tip would be to start with a random frame. This way, when you create 10 animations or so, they wont act like complete mirrors from one another. For example, when you create 10 wind mills (sue me, i'm Dutch) that each have 4 frames, you could start each mill with a random frame between 0 and 3. Lets assume a mill has 4 blades. 
Ofcause these 4 frames will only represent the first 90 degrees on the wheel because after that it simply repeats. (Unless your blades looks different ofcause, then yould need 16 frames).

The nice thing about using timers is that you can easly adjust the time between animations. Some mills can rotate faster then others.

The result would be very smooth looking, rotating mills that do not all act exactly the same.

I hope this helps giving your game a little more 'cool' factor. ;)

---

### Post by Mickeysofine1972 on 2006-11-26
I agree and we will be making a HOWTO to explain the use of timers and such in the near future

So keep your eyes peeled! ;-)

Mike

---

### Post by VDM on 2006-11-26
hehe, yeah it might be a nice thing for a part 2 article :mrgreen:

---

### Post by Mickeysofine1972 on 2006-11-26
Update: weekends are a bit of an inconvenience when it comes to developing a series of HOWTOs for SDL.

The reason is that I have 'responsibilities' yes you've guessed it I'm ad husband and farther and I must on occasion step into the realms of what women call 'real life', ( i just know the politically correct ploice will get me for saying that but its true. 

Well, rest assured that when the weekend is over I will return to plowing though the articles about SDL.

We have had a great response and we have also formed a of me, Seethru and VDM we are all working in a collaborative way to generate some REALLY top notch games programming articles.

If you would like to contribute you are very welcome as feel that the more support from the Ubuntu/Linux community the better.

So if your using ubuntu or just linux or you use windows but can compile SDL we can use anything you would like to contribute HOW EVER SMALL.

Don't be afraid we will only praise you for you help.

New HOWTO due in the next week include timers, tiled/platform background rendering and much much more!

Mike

---

