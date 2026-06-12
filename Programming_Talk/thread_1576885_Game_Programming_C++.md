---
title: "Game Programming C++"
date: 2010-09-18
forum: Programming Talk
---

### Post by YourMomsASmurph on 2010-09-18
This summer I plan on applying for a co-op position at bioware. One of the that they say will increase the chances of getting the job is to have developed and programmed some sort of game outside of my basic school courses (preferably in C++/C#) 

I have a basic understanding of the language and have even created a blackjack game (fully functional [can choose to play with 5,8,or 10 decks // allows for insurance bets etc.] -- though for an experienced programmer this probably wouldn't be that hard to do.)

I am hoping to get done a few of the following things before I apply for the job in 8 months. 

1) Apply a UI to the blackjack program so that it is not just text based but an actual game.
2) Create a tetris-like game (one of the easier games to program.) 
3) If I have time, Create a side scroller game or a simple multiplayer/battle version of my tetris-like game.

The question that I need to get answered is, is there any reading that someone can recommend that will help me find out what the process of designing a game like this would be. // How to apply a user interface to a program that has already been written. (I've been told that I may have to rewrite the whole program. But would like to confirm.)

---

### Post by shadylookin on 2010-09-18
I googled c++ tetris and got these

[http://www.gamedev.net/community/forums/topic.asp?topic_id=192483](http://www.gamedev.net/community/forums/topic.asp?topic_id=192483)
[http://gametuto.com/tetris-tutorial-in-c-render-independent/](http://gametuto.com/tetris-tutorial-in-c-render-independent/)

The biggest factor in whether you'll need to rewrite a lot will depend on just how well you separated out your game logic from the input and output process. Though it's such a small undertaking, redoing it from scratch might be easiest if you didn't abstract your logic enough.

---

### Post by mainerror on 2010-09-18
> **shadylookin said:**
> The biggest factor in whether you'll need to rewrite a lot will depend on just how well you separated out your game logic from the input and output process. Though it's such a small undertaking, redoing it from scratch might be easiest if you didn't abstract your logic enough.

This.

---

### Post by simeon87 on 2010-09-18
I don't know your programming skills but I would raise the bar if I were you. Familiarize yourself with an existing game engine and build a small game using that. It doesn't have to be much but it's a lot more impressive to an employer like Bioware than Tetris and Blackjack.

Read a bit about game engines, find one in your favorite programming language, read its documentation and create something small that actually works. You'll learn a lot about a game loop, user input, maybe some interaction in a 3D world if you're up for it. Creating a game engine is quite complex but understanding an existing one is very well possible in 8 months time.

---

### Post by YourMomsASmurph on 2010-09-18
> **simeon87 said:**
> I don't know your programming skills but I would raise the bar if I were you. Familiarize yourself with an existing game engine and build a small game using that. It doesn't have to be much but it's a lot more impressive to an employer like Bioware than Tetris and Blackjack.

Read a bit about game engines, find one in your favorite programming language, read its documentation and create something small that actually works. You'll learn a lot about a game loop, user input, maybe some interaction in a 3D world if you're up for it. Creating a game engine is quite complex but understanding an existing one is very well possible in 8 months time.

Great advice -- My only problem is coming up with a game idea :P
But will give it a try

Thx all

---

