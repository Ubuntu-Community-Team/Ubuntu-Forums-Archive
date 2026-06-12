---
title: "C++ &amp; game Development"
date: 2008-06-10
forum: Programming Talk
---

### Post by MechWarrior001 on 2008-06-10
I was wondering if anyone had any links or tutorials to making your own games.

I've tried before, but they all had tutorials or walkthroughs that confused me and I got stuck quite a bit.

Anyone willing to help out a Noob++?

---

### Post by irrdev on 2008-06-10
It depends on the game you want to make; is it 2d or 3d? If you are just starting out, I recommend that you begin with 2d games, and use C++ and the SDL library. A great set of tutorials can be found here -> [http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/gfxsdl/index]("http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/gfxsdl/index") . I realise that the tutorials are aimed at Windows, but the code is completely cross-platform. Simply install the libSDL-dev package from the Ubuntu repository using Synaptic, and then link your program to the "SDL" library. Hope that helps. ;)

---

### Post by Mickeysofine1972 on 2008-06-10
Why not checkout the ubuntu games developer resource wiki? the link is in my signature below

Mike

---

### Post by Sockerdrickan on 2008-06-10
Check here for examples [http://ubuntuforums.org/showthread.php?t=740604](http://ubuntuforums.org/showthread.php?t=740604)

---

### Post by pmasiar on 2008-06-10
Do you try to get into C++ as your first language? That's hard. Python with pygame would be substantially simpler. See stricky FAQ for discussion

---

### Post by seshadri_luminous on 2008-06-10
"Lazy Foo'Productions" has some good tutorials on using SDL...
I'm up to Lesson 6 so far :)

[http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)

They do require some knowledge of C++ :
> Operators (+, -, *, /, ++, --, +=, -=, etc)
Controls (if, else, switch)
Loops (while, for)
Functions
Structs
Arrays
References
Pointers
Classes and Objects
How to use a template.
Bitwise and/or.
to be precise...

---

### Post by MechWarrior001 on 2008-06-10
> **irrdev said:**
> It depends on the game you want to make; is it 2d or 3d? If you are just starting out, I recommend that you begin with 2d games, and use C++ and the SDL library. A great set of tutorials can be found here -> [http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/gfxsdl/index](http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/gfxsdl/index) . I realise that the tutorials are aimed at Windows, but the code is completely cross-platform. Simply install the libSDL-dev package from the Ubuntu repository using Synaptic, and then link your program to the "SDL" library. Hope that helps. ;)

Well I'm also kinda new to Ubuntu and the Whole Synaptic Package System.

I don't want to install the package and have to make all the game code in Notepad or something then run a whole bunch of commands in Terminal in order for it to become usable.

I'm looking for something that has a graphical interface, kinda like MS's Visual Basic 2008 Express.

---

### Post by CptPicard on 2008-06-10
Frankly, if you have such requirements, I don't think you have much of a future in programming, let alone programming games...

Getting comfortable with your tools is the first step. There's no getting around it, so you might just as well bite the bullet early.

---

### Post by JupiterV2 on 2008-06-10
> **CptPicard said:**
> Frankly, if you have such requirements, I don't think you have much of a future in programming, let alone programming games...

Getting comfortable with your tools is the first step. There's no getting around it, so you might just as well bite the bullet early.

Cheers

---

### Post by LoneWolfJack on 2008-06-10
MechWarrior001, please take a very close look at the avatar of CptPicard.

Now imagine every programmer on this planet going exactly like this after reading your last post.

Programming at a professional level is very hard work and can be extremely frustrating and exhausting. Completing a project can be very rewarding, though (and not just on the monetary side). But if you are not willing to get your hands dirty, your only option is to hire a programmer.

---

### Post by MechWarrior001 on 2008-06-10
It's just that I don't know how to notepad code, for example, [I]where do I put the freaking code!?!?
[/I]Do I put it in the parenthesis or outside the parenthesis, or do I put brackets around it or add a # or & or what?
I want something that CLEARLY explains What every symbol and command does and how it works.
For example, some tutorials will be like "ok type in /blah blah blah" and ill be like "Wait, what  does the command do? why are we typing it?

---

### Post by thornmastr on 2008-06-10
> **MechWarrior001 said:**
> It's just that I don't know how to notepad code, for example, [I]where do I put the freaking code!?!?
[/I]Do I put it in the parenthesis or outside the parenthesis, or do I put brackets around it or add a # or & or what?
I want something that CLEARLY explains What every symbol and command does and how it works.
For example, some tutorials will be like "ok type in /blah blah blah" and ill be like "Wait, what  does the command do? why are we typing it?

It's fairly obvious you do not know C, or Python, or C++, or Java, or Lisp. Have you done any game programming at all producing a game at least of the same Complexity of Hangman? 

Your attitude....."I want....." rather than "I would like to learn the basics" indicates a person with neither the drive nor the maturity necessary to become a good programmer; whether producing games, business applications, scientific programs, or just someone who wants to learn programming for the sake of learning.

You might do well to (1) Read the Wiki's of both LaRoza and the posts of pmasiar especially his arguments for using Python as a first language. Then, immerse yourself in some serious studying via a good old fashoned book...the kind you have to spend money to acquire...and start working through the problems.  If you need help, people here will help you provided you can show them you have attempted a solution on your own.

I wish you well in your studies  as does almost everyone in this group.

Robert

---

### Post by cmay on 2008-06-10
here is the first c++ program.
explained as in most tutorials.
```

// these '/'  are comments they dont mean anything for the program
#include <iostream>
 // is a library need to include to write something on screen
using namespace std;
// saves you the typing of std:: in front of everything
int main(){
// is the main program all starts here
cout<<"hello world"";
// is the very first program all c++ starts here
return 0;
// renember this as itmeans no errors in program 
}
// thelast } is the end of main

```
google for the c and c++ made easy tutorials.
they are fun and easy but you dont get to know the c++ language fully 
its just to get you started. the first games i created was whit a basic game creator called gamecreator. 
it comes whit visual studio express in a c++ version and you dont have to know any code at all.
 thats the program that got me started to think about how to create your own programs and then i followed 
every tutorial on the internet i could find for the past 3 years. that is c++
pascal basic perl and now i am only started to understand the book i bourght 3 years ago about c that much that i over the last monht have learned the syntaxt of the  language c which is the language the pro game industry uses besides c++.  
as far as i know there are not any alternative to gamecreator or any programmering tools for linux that assumes the user dont know how to handcode. 
 you have to start at the  hello world in c++ how to in the sticky tread . otherwise you cant learn gamecoding. 
as it as you found out already to code games you need to know
 ```
Operators (+, -, *, /, ++, --, +=, -=, etc)
Controls (if, else, switch)
Loops (while, for)
Functions
Structs
Arrays
References
Pointers
Classes and Objects
How to use a template.
Bitwise and/or.
```

if you dont wanna learn all this then run windows and use the gamecreator.
its fun and you can modifie your programs a lot too.
good luck .

by the way
i am still just a beginner for fun.
i dont wanna make games and nerver did.
the gamecreator just made me work whit sound effects and as a musician
that was kind of cool to have a easy drag and drop program to use for makin
something that i could create sounds for.
i wanna learn in time to code something whit sound if i ever get competent.
programmering is hard.
but if you do it for fun and only becouse you like doing it when you do it at the level where you are its not that hard . then its just fun.

---

### Post by mike_g on 2008-06-10
> It's just that I don't know how to notepad code, for example, where do I put the freaking code!?!?
Do I put it in the parenthesis or outside the parenthesis, or do I put brackets around it or add a # or & or what?
I want something that CLEARLY explains What every symbol and command does and how it works.
For example, some tutorials will be like "ok type in /blah blah blah" and ill be like "Wait, what does the command do? why are we typing it?
You wont have the patience for C++ then. You're going to have to go through a lot of mundane crap with it before you will be able to create anything that even remotely resembles a game. If you try jump in at the deep end you will quickly become confused and bored.

Maybe start out with a high level language and game development lib. Something like python+pygame, at least with that you should make more progress. And if you really cant stand writing stuff yourself then you could always make a mod for an existing game.

---

### Post by cmay on 2008-06-10
[http://darkbasic.thegamecreators.com/](http://darkbasic.thegamecreators.com/)

this is the link for the page where gamecreator is found.
it will cost you something though.
i cant renmber how much i paid for it back then.
and i forgot to adwise you againts the microsoft visual studio tools.
it may look as if it easy becouse you can just drag and drop some things and 
hoop de doo you have a window. but the truth is that most beginners that wanna learn programmering download this and find out the hard way that it is tools for proffesionals that knows what all the code that is generated means. i had the express c++ edition and i have nerver found out how to create a simple hello world program whit it. go for this above link if you want something that is free from any coding at all .
or as someone else suggested find out how to modifie an existing game.

there is also the gamemaker program but i nerver have tried that so i wont recommend it as i dont know what it is . 
point is whit the intension of nerver write any code at all you cant write a game your selve on linux as of this moment.

i hope this has helped you :)

---

### Post by MechWarrior001 on 2008-06-10
> **cmay said:**
> [http://darkbasic.thegamecreators.com/](http://darkbasic.thegamecreators.com/)

this is the link for the page where gamecreator is found.
it will cost you something though.
i cant renmber how much i paid for it back then.
and i forgot to adwise you againts the microsoft visual studio tools.
it may look as if it easy becouse you can just drag and drop some things and 
hoop de doo you have a window. but the truth is that most beginners that wanna learn programmering download this and find out the hard way that it is tools for proffesionals that knows what all the code that is generated means. i had the express c++ edition and i have nerver found out how to create a simple hello world program whit it. go for this above link if you want something that is free from any coding at all .
or as someone else suggested find out how to modifie an existing game.

there is also the gamemaker program but i nerver have tried that so i wont recommend it as i dont know what it is . 
point is whit the intension of nerver write any code at all you cant write a game your selve on linux as of this moment.

i hope this has helped you :)

I don't mean to be rude but would you please re-phrase that last couple of lines? The grammar made it hard for me to understand.

> It's fairly obvious you do not know C, or Python, or C++, or Java, or Lisp. Have you done any game programming at all producing a game at least of the same Complexity of Hangman? 

Your attitude....."I want....." rather than "I would like to learn the basics" indicates a person with neither the drive nor the maturity necessary to become a good programmer; whether producing games, business applications, scientific programs, or just someone who wants to learn programming for the sake of learning.

You might do well to (1) Read the Wiki's of both LaRoza and the posts of pmasiar especially his arguments for using Python as a first language. Then, immerse yourself in some serious studying via a good old fashoned book...the kind you have to spend money to acquire...and start working through the problems. If you need help, people here will help you provided you can show them you have attempted a solution on your own.

I wish you well in your studies  as does almost everyone in this group.

Robert

And yeah, I agree with you. It hard being the "Most Mature Teenager I've ever seen" at 14 years old.

---

### Post by Can+~ on 2008-06-10
This threads are so common.

-Someone, after years/months of gaming, thinks about their own game.
-Wants to learn code and start making games.
-Realize that what must be learnt is a lot, lot more than before.

Now the path splits in three:
a) Follows it's dream and makes games. (chance: 5%)
b) Quits (chance: 80%)
c) Realizes that gaming is not something really doable just by one person, or that making games is not as much fun as it sounded, but it's too late, programming looks appealing now, and instead of following the dream of becoming a game dev, decides to be just a programmer (that may or may not end up working as a game dev anyway). Bites the bullet, and jump into code. (chance 15%)

(chances pulled from my butt).

Now, why this happens?
-Game developing is serious business, there are tons of engines (and lots of open source ones) going on, and each one of them takes a different approach, trying to learn both the language and the tools without any understanding of how things move beneath the surface, will lead (in most cases) to poor design choices.
-Developing an engine is a hell of a task.
-Developing a game, even when knowing the engine AND the language, will take loads of time.
-Even if you manage to make a game, it will lack sounds, plot, graphics and probably, fun. You need a bigger team of more experienced people in this areas before doing it. (Except if you're nintendo, then you can just copy paste the same franchise again, I'm also looking at you EA!).

If you want to learn programming, strip any idea of making games first, learn the language fully. When you are a better and more mature programmer, you'll ask yourself if you still want to make a game... Or maybe use one of those sandbox programs like gamemaker.

Now that I read it again, it sounds pretty blunt, but it's true. Why do I now this? Some coders start like that, including me. That trip put me in the path of flash, lot of jumping around between new languages, and eventually ended up in python and C. And I wrote this specially, because of the age of the OP.

---

### Post by cmay on 2008-06-10
> 

there is also the gamemaker program but i nerver have tried that so i wont recommend it as i dont know what it is .
point is whit the intension of nerver write any code at all you cant write a game your selve on linux as of this moment.

```

i hope this has helped you
I don't mean to be rude but would you please re-phrase that last couple of lines? The grammar made it hard for me to understand.

```

yes of course i will re-phase that. i clicked submit too early sorry and no offense taken.
there is a lot of programs for windows that can be used to create games whit out  coding at all. but the most popular is a program called gamemaker. and you can google wikipedia to find it.
 
there is a other program i can see if i can find it again that is actually an old game engine made gpl by cedega as far as i renember.

i will look for it tonight and post if i find 
anything that you maybe could use. 

and just look in this tread once in a while 
and see if the pops something up:)

---

### Post by CptPicard on 2008-06-10
14... now, you're not in a hurry. :) But you do need to start from the bottom, like all of us did. I was doing 3D cube rotations in C at about your age on top of DOS. Writing the quaternion math in inline ASM was interesting... I never got into texture mapping though (mind you, most kids these days do their texture maps using OpenGL, I would have had to do it by hand).

It's a good test of whether you like programming and hacking at all really... just get yourself to the point where you can actually do stuff, because trust me, there is a lot of syntax to be learned, and command-line commands are just the first, very minor, part of it...

---

### Post by cmay on 2008-06-10
[http://en.wikipedia.org/wiki/Adventure_Game_Studio](http://en.wikipedia.org/wiki/Adventure_Game_Studio)

here it is. i have installed it once and maybe this something you can use.
the wikipeia has lots of freeware gameengines .
just check it out and see if you get something usefull out of it.

hope it helps.
i cant find more things as of right now.
but you should be able to spend some time looking trough this.

---

### Post by LoneWolfJack on 2008-06-10
> "Lisp's beauty is not in dragging and dropping, but in making a human thought become a computer's." -- LaRoza

((And) (I)) (((thought ((it's) (about))) (trapping) ((elephants) (in) (brackets)))

---

### Post by CptPicard on 2008-06-10
> **LoneWolfJack said:**
> ((And) (I)) (((thought ((it's) (about))) (trapping) ((elephants) (in) (brackets)))

The secret is... *there is no elephant*.

---

### Post by MechWarrior001 on 2008-06-10
What about making 3D Screen savers? I know they are programs and they use OpenGL, so would that be a good start?

---

### Post by Can+~ on 2008-06-10
Make console applications to start (if you want to keep in the programming path). Sounds boring, but it isn't.

Also, if you're using ubuntu, you already have python installed, so you could give it a try.

---

### Post by cmay on 2008-06-10
if you want to make screensavers you need to learn pascal.
google for free pascal.org and there you will find a nice tutorial and a sample / template for making screensavers. and thats not easy .
pascal however is pretty easy to learn.
and you can also start coding games whit lazarus 
that are in linux / ubuntu repos .
pascal looks like this.
```
program hello_world;
begin
writeln('hello world ');
readln;
end.
 
```
if you start now and really stick whit it id say in a matter of six month or so you can maybe write a screensaver.:)
but the free pascal has so many cool things to offer and you will pretty quick begin doing something funny whit it.
and thats the most important thing when you start.

did you find anything in my links above ?

---

### Post by CptPicard on 2008-06-10
> **cmay said:**
> if you want to make screensavers you need to learn pascal.

No, *you do not have to learn Pascal to make screensavers.*

Please refer to my avatar for further impressions.

---

### Post by cmay on 2008-06-10
```

if you want to make screensavers you need to learn pascal.
No, you do not have to learn Pascal to make screensavers.

Please refer to my avatar for further impressions.
```

i too agree .
but from games to screensavers why not also jump from no coding required
to pascal as a good some required coding language for a 14 year old kid.
might as well try keep open all options .

---

### Post by Wybiral on 2008-06-10
> **cmay said:**
> i too agree .
but from games to screensavers why not also jump from no coding required
to pascal as a good some required coding language for a 14 year old kid.
might as well try keep open all options .

Why not a more high-level/versatile language like Python or Lisp then?

---

### Post by MechWarrior001 on 2008-06-10
I don't know if this is supposed to be like this but I installed basically everything in the Programming subsection of the Add/Remove applications menu and now I'm trying to find the Python interpreter and I can't find it. ([Here]("http://www.python.org/doc/current/tut/node4.html") is the tutorial I am using.)

---

### Post by Can+~ on 2008-06-10
> **MechWarrior001 said:**
> I don't know if this is supposed to be like this but I installed basically everything in the Programming subsection of the Add/Remove applications menu and now I'm trying to find the Python interpreter and I can't find it. ([Here]("http://www.python.org/doc/current/tut/node4.html") is the tutorial I am using.)

[IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot2-1.png[/IMG]

---

### Post by cmay on 2008-06-10
> 
Why not a more high-level/versatile language like Python or Lisp then?
simply becouse there is apparently in other countries some schools that teach 
programmering and some of them is pascal some is c++ or java but not the dangerus parts of these -> c++ java. in case he is from one of these countries and have to learn anyway then it would be a good time to start.
pascal is also a good beginners language as well. at least i think so.
maybe they are already starting to use python in school too.
then its the right choice from this point of wiev.

---

### Post by cmay on 2008-06-10
```

i too agree .
but from games to screensavers why not also jump from no coding required
to pascal as a good some required coding language for a 14 year old kid.
might as well try keep open all options .
Why not a more high-level/versatile language like Python or Lisp then?
```
ohh and in order too follow the only "how to make a screensaver" tutorial i know of then he needs to learn pascal .
that is also a really fine reason dont you think?

---

### Post by Wybiral on 2008-06-10
> **cmay said:**
> ohh and in order too follow the only "how to make a screensaver" tutorial i know of then he needs to learn pascal .
that is also a really fine reason dont you think?

You're suggesting that he learn a less powerful language just because you don't have a tutorial to write screensavers with it?

---

### Post by cmay on 2008-06-10
> that is also a really fine reason dont you think?
You're suggesting that he learn a less powerful language just because you don't have a tutorial to write screensavers with it?

if i had any other links ready i would suggest them.
i have tried to give him all the options that i have.
however the joke should be clear. 
also it touches the deep understanding one must have that you only can relate  to what you already know.
i dont know python . 
i have slight problems whit my eyes from time to time and this language has something whit use of whitespaces i cant handle.
so i would  of course never suggest anything i dont know of.
i would not suggest otherwise either.
from the begining he wated to make games whitout coding at all.
i gave him links for that.
 then he wanted to make screensavers finding the the links i suplied not usable.
so i am fresh out ideas.
now all of you can take over from here since he is starting python

---

### Post by pmasiar on 2008-06-10
OP: If you want really simple game programming with GUI (no code), try GameMaker. If that is too hard for you, you are NOT ready to become programmer. Programmer has to be VERY detail-oriented, without that you cannot get anywhere at all. If you cannot learn some trivial commands (and cannot figure how to automate those), same thing. You can be graphic designer or something, with more immediate feedback.  

For non-programmers, programming is like dance to call rain - you have to learn it by observing others to dance. One small mistake, there is no rain - and you have to try again. But if you are good - rain! magic!

---

### Post by MechWarrior001 on 2008-06-10
> **pmasiar said:**
> OP: If you want really simple game programming with GUI (no code), try GameMaker. If that is too hard for you, you are NOT ready to become programmer. Programmer has to be VERY detail-oriented, without that you cannot get anywhere at all. If you cannot learn some trivial commands (and cannot figure how to automate those), same thing. You can be graphic designer or something, with more immediate feedback.  

For non-programmers, programming is like dance to call rain - you have to learn it by observing others to dance. One small mistake, there is no rain - and you have to try again. But if you are good - rain! magic!

That reminds me of the (Fictional) Civilization of the D'ni. They could write books to other "Ages". If you altered the books coding, it became a Prison Book. Maybe, If I keep at It, I could make my own Age, Savvy?

---

### Post by CptPicard on 2008-06-10
> **MechWarrior001 said:**
> Maybe, If I keep at It, I could make my own Age, Savvy?

Yes... but you still have to start at the bottom to really get it :)

---

### Post by Mickeysofine1972 on 2008-06-11
As I agree with most of the post that have been put in this thread in some regards I feel that you have been met with a LOT of negativity in relation to wanting to try something more than just the run of the mill. I feel sad that you have been given a negative "your not in the know so dont bother, go do something less hard".

Having come from the "I dont know how just yet but I can and will" type of software development perspective I think you should start this journey and I will be happy to personally help you.

I personally recommend Code::Blocks as Your IDE and it makes live a little easier when making C++ projects,(games and what ever you like).

Set yourself a goal of a game you would like to have a go at making, (something simple), and I will help you start to learn.

Never let it be said that the Ubuntuforums are full of nay sayers, we are what we are because of who we are, it just we need to remeber that sometimes.

Mike

---

### Post by mike_g on 2008-06-11
> I feel sad that you have been given a negative "your not in the know so dont bother, go do something less hard".
Its not so much "your not in the know so dont bother, go do something less hard", but "you can't be bothered so don't bother" 

C++ is not an easy language to make games in. I would not recommend it to any beginner that wants to make a game and see results fast.

---

### Post by pmasiar on 2008-06-11
> **Mickeysofine1972 said:**
> Never let it be said that the Ubuntuforums are full of nay sayers, we are what we are because of who we are, it just we need to remeber that sometimes.


Good advice, and putting things in perspective, might help OP to better understand how formidable challenge s/he attempts. The "feel good" advice ("try your best, and go down swinging") given in schools to teenagers may help to build self-appreciation but is less than useless when solving real world problems, as you soon realize in real life. If you are banging head against the wall, **wrong** advice is to try harder: good advice is look around, maybe there are doors somewhere.

No amount of hard trying will make hard task easier, but change of perspective might.

---

### Post by Mickeysofine1972 on 2008-06-12
Well maybe two heads banging on a wall might just break it :-D

Mike

---

### Post by pmasiar on 2008-06-12
> **Mickeysofine1972 said:**
> Well maybe two heads banging on a wall might just break it :-D

yes. Breaking the head is always a possibility :-)

---

### Post by MechWarrior001 on 2008-06-13
Ok I've been looking at this Python tutorial but I dont understand this part:

```
 Strings can be subscripted (indexed); like in C, the first character of a string has subscript (index) 0.  There is no separate character type; a character is simply a string of size one.  Like in Icon, substrings can be specified with the *slice notation*: two indices separated by a colon.  
 
>>> word[4]
'A'
>>> word[0:2]
'He'
>>> word[2:4]
'lp'

   Slice indices have useful defaults; an omitted first index defaults to zero, an omitted second index defaults to the size of the string being sliced.  
 
>>> word[:2]    # The first two characters
'He'
>>> word[2:]    # Everything except the first two characters
'lpA'

   Unlike a C string, Python strings cannot be changed.  Assigning to an  indexed position in the string results in an error:  
 
>>> word[0] = 'x'
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
TypeError: object doesn't support item assignment
>>> word[:1] = 'Splat'
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
TypeError: object doesn't support slice assignment

  
```

---

### Post by cmay on 2008-06-13
i am no python programmer but it seems that it works like 

```
<< 'a' 'string' 'and' 'a' string' 'become' 'one' 'string'

```
press return and the output will be

```
<< astringansastringwillbeonestring
```

there will probely be somebody that knows this for sure 

but i think  its great you are started to write code by hand .
keep up the good work.
and good luck

---

### Post by MacAnthony on 2008-06-13
Each character in a string can be referred too by it's numerical index in the string starting from 0. So in HelpA it iwould be:
```

HelpA
01234

```

The colon works as between marker. So [0:2] would be from index 0 to index 2 not including 2. If no number is present, it goes to either the end or beginning of the string. [:2] would be the same as [0:2].

These indexes can only be used for referrence though and you can't assign different text by using those indexes like some other languages (C is the example they use).

If there is a specific part you don't understand, I'm sure we could try and explain it to make it more clear.

---

### Post by MechWarrior001 on 2008-06-13
So are you saying that if I put a colon, it assigns a numeral Identifier to the text based on linear organization?

In otherwords:

hi
12

1 = h
2 = i

---

### Post by Can+~ on 2008-06-14
> **MechWarrior001 said:**
> So are you saying that if I put a colon, it assigns a numeral Identifier to the text based on linear organization

Semicolon acts as a splitter.

```
a = "Hello"

a[0] # Is "H"
a[1] # IS "e"

a[0:3] # "Hel"

a[1:3] # "el"
a[2:-1] # "ll"
```

Strings in python (and in most languages (including C/C++)) start with a zero.

```
Example
0123456
```

But also, as negative numbers.

```

 E  x  a  m  p  l  e
-7 -6 -5 -4 -3 -2 -1
```


There are various fancy things you can do with strings, refer to the [string methods]("http://docs.python.org/lib/string-methods.html") to check them. Mixing them with splitting and other techniques:

```
filename = "info.txt"
filename.split(".") # Returns ["info", "txt"]
filename.split(".")[-1] # Returns "txt"
```

---

### Post by CptPicard on 2008-06-14
I guess the easiest way to deal with understanding indexing is to first of all forget about the colon altogether. It's a more advanced Python concept.

In many, many languages, the brackets [] are used to index into an array or an array-like structure such as a string. An "array" is just something that stores stuff sequentially and numbered... if you have an array called x, x[0] is the first item, x[1] is the second item, x[2] is third and so on.

In general, in arrays you can also put things into these numbered locations by assignment. So to set your first item to, say, the number 2, you say x[0] = 2. After this, x[0] will be interpreted as 2 when seen.

Now, a string can be seen as an array of characters, so in s = "Hello", s[0] produces H and so on. What it means that it doesn't "support assignment" is that you are not allowed to change the contents of the string by saying something like x[0] = 'J' to get x of "Jello". In C you could, for example, but can't in Python because Python's strings are immutable (non-changeable).

Now, the colon is something that works on most sequential types... it just lets you to get a subsequence from some index to some other index. But that's specific to Python really.

---

### Post by Wybiral on 2008-06-14
In Python, strings are objects, and they are hashable objects. This is the exact reason you can't modify the strings, because you can't modify hashable objects. This is also why lists and dicts, for instance, aren't hashable... It wouldn't make sense to have a mutable hashable object.

(this is a response to the index part, not the slices)

---

