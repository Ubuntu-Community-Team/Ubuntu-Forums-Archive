---
title: "Discouraged with Ubuntu Brainstorm"
date: 2009-10-03
forum: Programming Talk
---

### Post by NinjaNumberNine on 2009-10-03
I posted [this on Ubuntu Brainstorm]("http://brainstorm.ubuntu.com/idea/21649/")- not a single positive response. They all seemed to think it is "too hard.."
Maybe it is but I kind of hoped someone would be encouraging. :(
I included a simple game, maybe I left something out, but that's the idea. Having a decent program in 15-20 lines of actual user input with all the hundreds of lines of true code behind the scenes ready to go.
 Can someone tell me what I'm missing? :confused:

---

### Post by phrostbyte on 2009-10-03
Maybe Ubuntu should ship with a programming tutorial. But seriously it's hard to ship all this stuff on a 700 MB CD. :)

Natural language programming is something that has been researched a lot but it's not easy because you need to express things concisely to program,

---

### Post by NinjaNumberNine on 2009-10-03
> **phrostbyte said:**
> Maybe Ubuntu should ship with a programming tutorial. But seriously it's hard to ship all this stuff on a 700 MB CD. :)

Natural language programming is something that has been researched a lot but it's not easy because you need to express things concisely to program,
Thanks for the encouragement! I know this would not be on the LiveCD, but I just wanted it available. And yes, I do know what you mean about the necessary "conciseness".  It would mean that you would need to use very formal English, as "formal English" does not change as fast. Still, anything like this would at least make it easier, Ideally, it would make it almost no work. Just as long as something gets easier for the average noob... Once again, Thank you.

---

### Post by phrostbyte on 2009-10-03
> **NinjaNumberNine said:**
> Thanks for the encouragement! I know this would not be on the LiveCD, but I just wanted it available. And yes, I do know what you mean about the necessary "conciseness".  It would mean that you would need to use very formal English, as "formal English" does not change as fast. Still, anything like this would at least make it easier, Ideally, it would make it almost no work. Just as long as something gets easier for the average noob... Once again, Thank you.

COBOL/FORTRAN is like that, very English like. This is pseudo-COBOL:

ASSIGN 10 TO X
MULTIPLY X BY 20 GIVING Y
ADD 1 TO Y
DISPLAY Y
STOP PROGRAM EXECUTION AND RETURN 0

At some point COBOL was hugely popular. I think a very large amount of the world's financial systems are still run on by programs written in COBOL. :)

---

### Post by NinjaNumberNine on 2009-10-03
> **phrostbyte said:**
> COBOL/FORTRAN is like that, very English like. This is pseudo-COBOL:

ASSIGN 10 TO X
MULTIPLY X BY 20 GIVING Y
ADD 1 TO Y
DISPLAY Y
STOP PROGRAM EXECUTION AND RETURN 0
How can I use that, though? Is it for linux too? Part of the reason I proposed the first idea was to draw more people to Ubuntu. Tell me more! :)

---

### Post by NoaHall on 2009-10-03
I suppose you could make something which translated structured english into a programming language.

---

### Post by NinjaNumberNine on 2009-10-03
If you haven't seen it already, refer to this:


```
Create 2D game engine 

#This is an incomplete simple 2D game 

Resolution: 640x480 
animate /home/halstan/Pictures/Biotux.png, Biotux2.png, Biotux3.png; 
Name the animation "tuxwalkleft". 
animate /home/halstan/Pictures/Biotux4.png, Biotux5.png, Biotux6.png; 
Name the animation "tuxwalkright". 
#(no need to animate because there is only one image:) 
Name /home/halstan/Pictures/Biotuxjump.png "tuxjump" 
Create Background 1; 
Background 1 = "/home/halstan/Pictures/Background.png 
 [[...]]("http://brainstorm.ubuntu.com/idea/21649/") 
   Create physics effect with gravity center at x=1 
Create sprite "Tux" from "tuxwalkleft", "tuxwalkright", "tuxjump". 
Place "Tux" at X=2in. and Y=4in. 
#The keystroke definitions: 
If "up" key is pressed, play "Tux" "tuxjump" and move "Tux" up 3y. 
#(The physics effect will pull him back down) 
If "left" key is pressed, play "Tux" "tuxwalkleft" and move "Tux" left 3x. 
If "right" key is pressed, play "Tux" "tuxwalkright" and move "Tux" right 3x. 
```If you will notice, there is a significant amount of "non-English" in that but it is also simple enough for the beginner to understand. Then you could play around till you got something that worked. 

I will restate the goal a little:

There will be a list of common words with their code equivalents, and that list will be available to the general public. In other words, you cannot type "sentences" in english and expect it to translate it. Rather, you refer to the list and create your sentences using only the GIVEN words. Here's a list of some of the words you could use: ( In this example I am using the general subclass "Games" which means that in the beginning of the program there would be something that asked "what kind of program do you wish to create?" and you would choose "Games" which would tell the program to use the built-in list of expressions specially built for designing games.)
IF
AND
GRAVITY
PHYSICS
SPRITE
MAKE 
THEN
BE
PLAY
SHOW
VIEW
CREATE
BACKGROUND
SAVE
NEW
LOAD
ANIMATE
A
GET
THE
USE
LEVEL
MAP
OPENGL
RASTER
3D
2D
RESOLUTION
COORDINATE
X AXIS
Y AXIS
X
Y
HEIGHT
WIDTH
DEPTH
PARTICLE
IMAGE
IMAGES
GAME
MENU
FONT
TEXT
BLOCK
ENEMY


In those 40 or so words you could program most 2D games like SuperTux or even Mario. 
Neat, huh?

---

### Post by NoaHall on 2009-10-03
Get language making then.

---

### Post by tubasoldier on 2009-10-03
The reason it failed in the Brainstorm is because it isn't something a distribution should do. There seems to be a growing sense that a distribution should take care of all things in and of itself. But a distribution is merely a central distribution of software and not a major player in the creation of said software. It isn't the distribution's goal to make software but to merely make a distribution of that software. 

To me this sounds like an entirely separate project to be later included in a distributions CONTRIB repository.

---

### Post by NinjaNumberNine on 2009-10-03
> **NoaHall said:**
> Get language making then.
I'm taking a crash course to learning c right now, but its gonna take a while before I can donate. :)

---

### Post by grayrainbow on 2009-10-03
Don't wanna discourage you but...there's something called bash :) I guess you want something more.
Natural language processing is pretty big deal in AI research(couse there is its place) and it doesn't seems that will be use for standard programming(after all nobody write mathematics formulas with plain words, right ;) ). But for that what you want, I get it as mainly child oriented game for first encounter with computer, you may try to get emacs from repository, then - M-x(that mean alt+x) and type "doctor" :)

---

### Post by fiddler616 on 2009-10-03
First of all, tubasoldier's right: This isn't Ubuntu's problem. And in the event that it did get built, it would be a package for other distros too.

Second of all, if you make it proprietary, and try to peddle it to Linux-only folk, you'll get lynched.

Third of all, I just don't think it's a very good idea.

There's quite a few GUI-centric game makers (PT regular pmasiar (who might be banned, although I think it got lifted...although I haven't seen him for a while) made an app called "GameBaker", IIRC, which would do everything your proposed language can do, and be easier.

I think that there's still the possibility of ambiguity with your proposed syntax.

Even moderately fun programs would still be huge in terms of line length.

I saw no way to error-catch--people could make Tux move outrageous places. And they could spam the up key, and make him fly. And if you fix that exploit, someone with either more brains or more time than myself will find a new one.

And if people want to go a step above a GUI environment...what about Gloss (which is much more powerful, too)? [http://www.tuxradar.com/content/make-python-game-minutes-gloss](http://www.tuxradar.com/content/make-python-game-minutes-gloss) (Added bonus: it teaches real programming).

---

### Post by NinjaNumberNine on 2009-10-13
> **fiddler616 said:**
> 
And if people want to go a step above a GUI environment...what about Gloss (which is much more powerful, too)? [http://www.tuxradar.com/content/make-python-game-minutes-gloss](http://www.tuxradar.com/content/make-python-game-minutes-gloss) (Added bonus: it teaches real programming).
Sounds a lot like NovaShell.
[http://www.rtsoft.com/novashell/](http://www.rtsoft.com/novashell/)

---

### Post by fiddler616 on 2009-10-13
> **NinjaNumberNine said:**
> Sounds a lot like NovaShell.
[http://www.rtsoft.com/novashell/](http://www.rtsoft.com/novashell/)

Maybe I'm misreading documentation, but as far as I can tell, NovaShell looks a lot more visual. Gloss is just a particularly easy to use Python module (that's a library for the rest of you).

---

### Post by MadMan2k on 2009-10-13
[http://www.pegasus-project.org/en/Welcome.html](http://www.pegasus-project.org/en/Welcome.html) - here you go. It already exists... and it sucks badly ;)

---

### Post by benj1 on 2009-10-13
i think its a good idea, to a point but you are underestimating the problem
your example:
```

Create 2D game engine 

#This is an incomplete simple 2D game 

Resolution: 640x480 
animate /home/halstan/Pictures/Biotux.png, Biotux2.png, Biotux3.png; 
Name the animation "tuxwalkleft". 
animate /home/halstan/Pictures/Biotux4.png, Biotux5.png, Biotux6.png; 
Name the animation "tuxwalkright". 
#(no need to animate because there is only one image:) 
Name /home/halstan/Pictures/Biotuxjump.png "tuxjump" 
Create Background 1; 
Background 1 = "/home/halstan/Pictures/Background.png 
 [...] 
   Create physics effect with gravity center at x=1 
Create sprite "Tux" from "tuxwalkleft", "tuxwalkright", "tuxjump". 
Place "Tux" at X=2in. and Y=4in. 
#The keystroke definitions: 
If "up" key is pressed, play "Tux" "tuxjump" and move "Tux" up 3y. 
#(The physics effect will pull him back down) 
If "left" key is pressed, play "Tux" "tuxwalkleft" and move "Tux" left 3x. 
If "right" key is pressed, play "Tux" "tuxwalkright" and move "Tux" right 3x.

```
ok the direction syntax is fine but 
```
#(The physics effect will pull him back down)
```
is very specific.
say you wanted to make a top down game? this would only be so easy to read for 2d platform games, programming languages need to do more than that.
i think python is probably the closest you will get to natural language
for x in y:
if y in x:
etc etc
yes it can be improved in many other areas but you will never get a true natural language programming language because natural languages are so imprecise, its all context and body language and everthing that a computer has no conception of.

---

### Post by NinjaNumberNine on 2009-10-13
> **fiddler616 said:**
> Maybe I'm misreading documentation, but as far as I can tell, NovaShell looks a lot more visual. Gloss is just a particularly easy to use Python module (that's a library for the rest of you).
NovaShell is awesome for what it does- But all it does is makes 2d games...:cry: Right now I'm writing a game called BioTux, meant as a sort of "continued" version of SuperTux... But that's another story. (I'm fixing to make a post for contributions to BioTux in the form of art and SoundFX, I'll add a link here when I do)
Also NovaShell uses ClanLib, and that's what SuperTux is written in, too.
Excellent quality and super fast, too. And it's platform independent with no extra packages needed! :)

[URL="http://www.youtube.com/watch?v=l3y4WWmKUBs&feature=player_embedded"]
A Preview[/URL]

---

### Post by NinjaNumberNine on 2009-10-13
> **benj1 said:**
> i think its a good idea, to a point but you are underestimating the problem
your example:
```

Create 2D game engine 

#This is an incomplete simple 2D game 

Resolution: 640x480 
animate /home/halstan/Pictures/Biotux.png, Biotux2.png, Biotux3.png; 
Name the animation "tuxwalkleft". 
animate /home/halstan/Pictures/Biotux4.png, Biotux5.png, Biotux6.png; 
Name the animation "tuxwalkright". 
#(no need to animate because there is only one image:) 
Name /home/halstan/Pictures/Biotuxjump.png "tuxjump" 
Create Background 1; 
Background 1 = "/home/halstan/Pictures/Background.png 
 [...] 
   Create physics effect with gravity center at x=1 
Create sprite "Tux" from "tuxwalkleft", "tuxwalkright", "tuxjump". 
Place "Tux" at X=2in. and Y=4in. 
#The keystroke definitions: 
If "up" key is pressed, play "Tux" "tuxjump" and move "Tux" up 3y. 
#(The physics effect will pull him back down) 
If "left" key is pressed, play "Tux" "tuxwalkleft" and move "Tux" left 3x. 
If "right" key is pressed, play "Tux" "tuxwalkright" and move "Tux" right 3x.

```ok the direction syntax is fine but 
```
#(The physics effect will pull him back down)
```is very specific.
say you wanted to make a top down game? this would only be so easy to read for 2d platform games, programming languages need to do more than that.
i think python is probably the closest you will get to natural language
for x in y:
if y in x:
etc etc
yes it can be improved in many other areas but you will never get a true natural language programming language because natural languages are so imprecise, its all context and body language and everthing that a computer has no conception of.
```
#(The physics effect will pull him back down)
```
You will notice that I used Linux syntax for "ignore this line" in the form of "#". That was to describe to the reader what "physics effect" would do.

---

### Post by benj1 on 2009-10-13
@NinjaNumberNine
i know, my point is its a very large part of a game to just explain away with a comment.

i could write breakout as
```

blocks(x=0,y=0,h=10,w=100,colour=xyz);paddle(x=100,y=50,h=2,w=5,speed=5,colour=xyz);ball(size=5,speed=5,colour=xyz);
background(xyz)
```
but it wont be generally usable for anything else.

---

### Post by NinjaNumberNine on 2009-10-13
Igotcha benj1. BTW here's the link to the BioTux thread I mentioned earlier:
[http://ubuntuforums.org/showthread.php?t=1290670](http://ubuntuforums.org/showthread.php?t=1290670)

---

### Post by fiddler616 on 2009-10-13
benj1 brings up a very good point that was floating around ethereally in the back of my brain for a while: ease of use is paid for with extensibility.
Python and C are prime examples: Python is very easy to use, C is more powerful.
Your proposed language would be very easy to use--but only works for simple platform games. It can't even do Pong, as I see it.

---

### Post by benj1 on 2009-10-13
> **fiddler616 said:**
> benj1 brings up a very good point that was floating around ethereally in the back of my brain for a while: ease of use is paid for with extensibility.
Python and C are prime examples: Python is very easy to use, C is more powerful.
Your proposed language would be very easy to use--but only works for simple platform games. It can't even do Pong, as I see it.

i dont think its a straight trade off you can do alot of things with python, but its a bigger language in terms of functions etc compared to C, you could have a language where you could type 
```
pong()
```
but it would be a monstrously large language.

i suppose design comes into play here, its the difference between 'big and featureful' and 'big and unwieldy', python hides its size very well, or at least manages the complexity of it well.

---

### Post by fiddler616 on 2009-10-14
> **benj1 said:**
> i dont think its a straight trade off you can do alot of things with python, but its a bigger language in terms of functions etc compared to C, you could have a language where you could type 
```
pong()
```
but it would be a monstrously large language.

i suppose design comes into play here, its the difference between 'big and featureful' and 'big and unwieldy', python hides its size very well, or at least manages the complexity of it well.
I definitely would've pressed your thank button, if I could have.

---

