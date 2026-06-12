---
title: "A simple C++ question"
date: 2008-01-20
forum: Programming Talk
---

### Post by breaking on 2008-01-20
I have a "board" class that is instantiated once.. I need my gameBoard to contain 5 "ship"s. The problem is, if I just put them in my board constructor, they're temporary, and even if I mark them static, I can't do
```
gameBoard.shipName.whatever
```
Because the ships aren't technically members of the gameBoard.. 

I tried creating a member array of ship pointers and pointing that to the ships in the constructor, then marking them static, but it was fairly messy and I have to be missing something here because a concept this simple can't be this difficult to pull off!

If I put the ships' declaration in the header file and give it constructor arguments, it will run its constructor like normal, right? But that would be defining it and isn't that something you're not supposed to do inside class definitions? What's the "correct" way to do it?.. some weird combination of extern and new?

---

### Post by SledgeHammer_999 on 2008-01-20
maybe if you define in your gameboard class as members five different names of members of type shipname. And then you define shipname as another class type.

But I don't know if a class can have as members other classes.

---

### Post by breaking on 2008-01-20
I tried that, but I had unrelated problems.. I tried this instead and am having even stranger problems:

In my board header:
```
ship shipsArray[5];
```

In my board constructor:
```
	ship shipsArray[5] = { ship(4,"shipname1"), ship(3,"shipname2"), ship(3,"shipname3"),ship(2,"shipname4"), ship(2,"shipname5") };
```

Now this is a very strange problem.. it initializes all of the ships with the default constructor (length and name both 0) when it reaches the class definition in the header, and then when it reaches the actual array declaration, it goes through each ship, takes the parameters properly, plugs them into the member variables in the ship object, and goes onto the next ship. 

The whole time I'm looking at my Watches panel, and my shipsArray *never* actually changes. It's fully 0 0 0 0 0 0 0 0 0 0 0 0 0 etc even while I see the member variables being changed by the ship constructor! What's going on there?

---

### Post by aks44 on 2008-01-20
You may want to read [this post]("http://ubuntuforums.org/showpost.php?p=3981541&postcount=5") about constructors and initializer lists.

Although it is not absolutely on topic WRT your question, it will probably help you understand how C++ objects are constructed under the hood. Anyway it will give you enough hints so that you can do some research on the subject on your own.

That's the best I can do right now since I don't have enough time to explain object construction in a detailed way (this would require quite a lengthy explanation in order to be complete).

I'll do that later if the post I linked isn't enough to get you started, and if someone doesn't explain it before.

---

### Post by breaking on 2008-01-20
OK I went back to just putting their declarations in the board class definition and declaring the ships in the board constructor.. you're right, it was just a misunderstanding of how things are constructed because I didn't have a default constructor at all before. Still didn't work but after I realized that it was actually *my sloppy debugging code* that was segfaulting it, I got it to work!!

I'm still curious though.. why couldn't it change that array? Do I need to use dynamic allocation if I want to do that declare-in-class-definition, define-in-constructor array thing?

---

### Post by SledgeHammer_999 on 2008-01-20
if you had declared two "ship shipsArray[5]" one **inside** the boardgame class definition and one **outside** of that then these are two different instances of shipsArray[5].

sorry if I didn't understand what you were talking about.

---

