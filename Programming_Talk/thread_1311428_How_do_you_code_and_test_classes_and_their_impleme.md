---
title: "How do you code and test classes and their implementations?"
date: 2009-11-02
forum: Programming Talk
---

### Post by s1300045 on 2009-11-02
If I have multiple classes to implement and test, and they all sort of interdependent on each other, do I make a test driver file for each of them? I am very tempted to do it but some how afraid of all that redundancy and messiness.  What should I do?

---

### Post by dwhitney67 on 2009-11-02
> **s1300045 said:**
> ... multiple classes... all sort of interdependent on each other....  What should I do?

Consider posting your design.  Perhaps it can be refined.  It's odd that multiple classes would be interdependent on each other.

---

### Post by MadCow108 on 2009-11-02
there are tons of testing frameworks for practically every language:
[http://en.wikipedia.org/wiki/List_of_unit_testing_frameworks](http://en.wikipedia.org/wiki/List_of_unit_testing_frameworks)
these may be helpful in your task

---

### Post by s1300045 on 2009-11-02
> **dwhitney67 said:**
> Consider posting your design.  Perhaps it can be refined.  It's odd that multiple classes would be interdependent on each other.

Okay, I have to say I am very amateur and there are probably millions of ways to do this. Please let me know if I am doing something stupid! This is a game I just started working on. Supposedly I have a image class handling all the basic functions, and I have a sprite class and a map class built on top of that. The game class oversees both those classes but also uses the image class to do the interface. I have all those header and implementation files residing in one folder, and they are growing out of control! What should I do?

---

### Post by korvirlol on 2009-11-02
im assuming c++, so disregard this if you arent using c++.

A very strong testing application is CPPUnit. You can create "test runners" to create instances of your class objects and test them. Using cron, you can automate the tests and record the output of the tests, and then you can review the logs and find out if and what broke. 

in my opinion, definitely an integral tooling in large scale development projects - ESPECIALLY if there are multiple programmers

---

### Post by dwhitney67 on 2009-11-03
> **s1300045 said:**
> Okay, I have to say I am very amateur and there are probably millions of ways to do this. Please let me know if I am doing something stupid! This is a game I just started working on. Supposedly I have a image class handling all the basic functions, and I have a sprite class and a map class built on top of that. The game class oversees both those classes but also uses the image class to do the interface. I have all those header and implementation files residing in one folder, and they are growing out of control! What should I do?

Sorry for the late reply;  I'm not much of a game developer, but from what I can assume, the Sprite class should not need awareness of the Game class, nor of the Map or the Image class. Similarly, the Map class should not need awareness of the Sprite.

User interfaces, inclusive of games, should attempt to follow the MVC (Model-Viewer-Controller) paradigm as a design.

The term Model, albeit not intuitive, refers to the "state" of the GUI/Game/etc.  Viewer, as the name implies, relates to the graphical component of the system.  As for the Controller, it manages the collection of user input, and as needed, interfaces with the Model and the Viewer.

Your Game, or perhaps the Game Controller, should manage what is displayed using your Image class.  The Image class should provide an interface so that it can render an image, at a given location.

The Map class retains an image, but nothing else.  Similar for the Sprite, although perhaps dimensions are a necessary attribute as well.  (It seems like these objects could share a base-class).

The Game Controller will tell the Image class to draw the Map and the Sprites.  Note that the Image class should not care whether it is drawing a Map or a Sprite; from its perspective, both are merely images.

If your design is more coupled than described above, then you should re-factor it.  Perhaps familiarizing yourself a bit with Object Oriented Design would be helpful.

Once the class(es) are simplified, then testing should be a breeze.  You can employ some of the testing ideas presented in this thread, or have an a friend play the game to find out if there are any bugs.

---

