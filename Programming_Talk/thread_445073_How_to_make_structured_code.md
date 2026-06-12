---
title: "How to make structured code?"
date: 2007-05-15
forum: Programming Talk
---

### Post by petok on 2007-05-15
I have learned myself Java the past year. I made an attempt to develop a poker game, which was more complex than I realized at the beginning. I came really far, but right now it is a complete mess. For example there is a method right now in the GuiBuilder class of the poker game called EvaluateHand. I do not feel like writing the entire application from scratch again. I have read Head First Java totally and I think I have a good basic Java knowledge.
Right now I want to make a new application, it does not have to be very useful, just for learning purposes and gaining more experience.
So my question is, how can I make structured code, that stays structured even after > 500 lines?
And does anyone have suggestions for applications or games (preferably the first) to develop next?

---

### Post by Ramses de Norre on 2007-05-15
Make good, well named methods and variables... I try to keep methods about one property or feature in the same area. Also, refactor enough, methods shouldn't be too big.

But a source file gets messy very quick anyway... I use eclipse's outline view a lot to retrieve methods in my sources, I'm not able to retrieve the correct method in a 1500+ lines class neither.

---

### Post by petok on 2007-05-15
> **Ramses de Norre said:**
> Make good, well named methods and variables... I try to keep methods about one property or feature in the same area. Also, refactor enough, methods shouldn't be too big.

But a source file gets messy very quick anyway... I use eclipse's outline view a lot to retrieve methods in my sources, I'm not able to retrieve the correct method in a 1500+ lines class neither.

I use eclipse as well. I heard something about UML diagrams...Is it possible to make such a diagram and load it into eclipse?

---

### Post by Tomosaur on 2007-05-15
Break everything down as far as is logically possible (within reason!). Java is heavily slanted towards this idea. Create a new class for pretty much anything which has some unique processes assosciated with it. Without thinking about it too much, I'd suggest the following different objects:

Card
Hand
Player
AIPlayer (if applicable, of course)
MoneyPot (referring to the pile of money / whatever which players place their wager into).

And, last but not least:
Game

People often overlook the fact that most programs are essentially just big loops. Create a 'game' object to initialise and control everything - there's no point confusing yourself by putting all of the game logic inside, say, the Player class. The player is a part of the game, thus the game itself is an object.

Methods shouldn't really stretch for longer than one 'page' of your text editor (ie, it shouldn't extend beyond the currently visible lines of code). Of course, this one is hard to stick to depending on which editor you're using, screen resolution, etc etc. Just try to break everything down as far as they can go. Keep your methods relevant to the object. For example - your EvaluateHand method should be part of your AIPlayer object, not the 'Card' object or the 'Game' object. Just use common sense, really. Use seperate files for each class, try not to nest too many loops / conditionals.

If you find yourself writing similar code in different methods, then chances are you can just create a new method and cut out the superfluous code.

---

### Post by pmasiar on 2007-05-15
Some tasks good for beginner programmers (and not only for python) are at wiki in my sig

---

### Post by qebab on 2007-05-17
[quote=Tomosaur]
Methods shouldn't really stretch for longer than one 'page' of your text editor (ie, it shouldn't extend beyond the currently visible lines of code). Of course, this one is hard to stick to depending on which editor you're using, screen resolution, etc etc. Just try to break everything down as far as they can go. Keep your methods relevant to the object. For example - your EvaluateHand method should be part of your AIPlayer object, not the 'Card' object or the 'Game' object. Just use common sense, really. Use seperate files for each class, try not to nest too many loops / conditionals.[/quote]

This is a very good tip. I don't know about Java, but when I use python I tend to break up methods and functions if they span more than 10 lines (as a rule of thumb, there are exceptions). Separate logically different things with empty lines if that helps you (for instance, if you assign some variables or do some calculations, and have logical statements ('if's, 'else's) or loops, separate these by a blank line). Break things up as much as possible, and put what logically belongs together in the same module / class. 

Not only does this make it more readable, but I think that it could often save people from having to do rewrites, as it is much, much more easy to avoid a complete rewrite when you've breaken things up sufficiently. It's easier to take out parts of your program and still have usable bits left of it.

---

### Post by Levander on 2007-05-18
petok, you're asking a very advanced question that can't be answered in a few lines on a message board.  What you're asking how to do, a lot of people are making very nice livings doing professionally.  Typically, I'd want someone with at least five years of professional experience to make these decisions really well like what you're wanting.  

It'd be good if you had other peoples code to work on, starting with fixing bugs, moving up to extending it in functionality.  Maybe volunteering to work on an open source project written in Java would be a good way to learn.  I don't consider it necessary to become a good programmers, but you could also get a computer science degree at some college.  

But, as for what you're asking now.  The best advice I can give you is to read Craig Larman's GRASP patterns.  His GRASP patterns form what he claims to be the underlying idea of all more complex design patterns.  They are the simplest building blocks of other design patterns.  Unfortunately, his documentation is split out into 2 chapters of a very much larger book called Applying UML and Patterns.

But, really I think the easiest way to learn this is to work on someone else's code that has implemented good design.  My guess is for you to try to find a open source project written in Java that has a reputation for being well designed.

---

### Post by rplantz on 2007-05-19
I worked in industry for a decade then taught computer science (university) for two decades. I second Levander's comments. It comes from experience seeing lots to bad code, both yours and others'.

Be willing to throw something away and start over. One of the best projects I worked on was a CAT scanner. The company got a contract to build one for another company that included development costs. That allowed us to start over, knowing lots of mistakes that existed in our current design.

To state this another way:

Q: What's the secret of wisdom?
A: Good judgment.

Q: What's the secret of good judgment?
A: Experience.

Q: And how do you get experience?
A: Bad judgment.

---

### Post by Levander on 2007-05-19
No idea if you're reading this still petok.  But, I would consider it important for you to get on a project that is well designed.  There are a lot of open source projects out there that are junk.  Considering your lack of experience, it is probably hard to determine which has that reputation as being well written.  One open source project I know of, that I've seen the source code to, and know is really well written is JPOX.  Just head to jpox.org and see if they are looking for volunteers.  If not, I can't imagine the head programmer, I believe his name is Andy, wouldn't recommend another project for you.  He is very active in the open source / java community.

---

