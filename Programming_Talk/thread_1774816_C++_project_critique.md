---
title: "C++ project critique"
date: 2011-06-03
forum: Programming Talk
---

### Post by Ghostmn on 2011-06-03
Hello Ubuntu forums! I was wondering if anyone with the knowledge of C++ could critique my project. It can be found at
[http://code.google.com/p/midnight-cloud/downloads/list](http://code.google.com/p/midnight-cloud/downloads/list)

I'm new to C++ and would like some advice. Thanks!

---

### Post by Ghostmn on 2011-06-03
I forgot to include a file with a list of controls.

w,a,s,d-movement
q-quit game
j-open journal
h-heal

---

### Post by simeon87 on 2011-06-03
Let me start off by saying that it's actually a nicely designed game, reminiscent of the retro games of the good old days.
Regarding the code, it's clear that you've made an effort to familiarize yourself with concepts such as class, functions, header files etc, which is a good thing.

Although you are rather consistent with your coding style, it's unlike most C++ code I've seen (in particular the way the code is indented and lowercase names for classes).
You are also using global variables which is discouraged by many. This makes it hard to test the software and to reuse pieces of code.

I'm also a bit curious about how you made the player class. The player is a good choice for an object and you can use it to represent various information, such as health, inventory, items, etc. But you have chosen to put player_health as a global, which seems a bit odd. It would make more sense to have it in the player class and then to access it with player->health.

I also wouldn't put Loadgame and Savegame in the player class because they're more part of the game itself, not part of the player object. These can just be separate functions. Or, you can create a Level class with load() and save(), which seems like a justifiable choice.

I think it's a good start and if you're willing to get into game development, C++ is certainly a good language choice.

---

### Post by rpmp on 2011-06-03
dude how u do this.im learning C++ to program games too though im a newbie.can you give me a few tips on how to do games in C++?

---

### Post by cgroza on 2011-06-03
> **rpmp said:**
> dude how u do this.im learning C++ to program games too though im a newbie.can you give me a few tips on how to do games in C++?
Take a look at SDL. It provides you the graphic, sound, input and many others.

---

### Post by Ghostmn on 2011-06-03
I understand what's wrong with Globals. I've been reading up on pointers and references and i'm starting to include them more.

I'm not interested in game development to be honest. I'm just making a game because they include a lot of programming concepts? maybe?

I really want to get into kernel development or software development.

---

### Post by rpmp on 2011-06-03
okay but at least tell me where you learn to make the game.

---

### Post by Ghostmn on 2011-06-03
> **rpmp said:**
> okay but at least tell me where you learn to make the game.

I just learned C++.

---

### Post by ThatCoolGuy220 on 2011-06-04
LOL is very addictive I wish there were more levels....
it reminds me the zelda-like games.

Good job bro, I'm studying C++ too, this is a very good reference for my future job.

PD: I use Code Google too.

---

### Post by DangerOnTheRanger on 2011-06-04
It's triple reply time! :D

> **Ghostmn said:**
> I understand what's wrong with Globals. I've been reading up on pointers and references and i'm starting to include them more.

I'm not interested in game development to be honest. I'm just making a game because they include a lot of programming concepts? maybe?

I really want to get into kernel development or software development.

Kernel development? If you mean the Linux kernel, you should study C, not C++, as C is used in the Linux kernel (as well as practically every other OS out there: Windows, OSX, BSD...) It's true, the languages have a lot in common (a C++ compiler, for example, can compile C programs), but there are some differences, including:

[LIST]
[*]Agile/OO design being favored for C++, compared to structured design in C
[*]The lowest level of granularity in design for C++ is the class, compared to the function for C
[*]Emphasis on classes that provide their own algorithms in C++, compared to non-interactive data structures that are modified by functions in C
[/LIST]
So there are a lot of differences in C and C++. Learning one will give you a head start in the other, but there's a minor paradigm gap between the two languages.

Also, what do you mean by *software development*? That's a somewhat ambiguous term. Could you clarify, please?

> **rpmp said:**
> dude how u do this.im learning C++ to program games  too though im a newbie.can you give me a few tips on how to do games in  C++?

**** BEGIN DYNAMIC LANGUAGE RANT ****

If you're just starting out in programming, and you'd like to do game development, I'd recommend Python (my personal choice) or Lua, instead of C++.

The main reasons are:

[LIST]
[*]Even if you're developing on a Linux system, as long as the game engine you use is also written in Python or Lua (or is cross-platform), porting your game to Windows requires little to no effort on your part. You don't even *need* to have Windows!
[*]Python (or Lua) is much nicer on the eyes compared to C++. Syntactic sugar (look up that term on Wikipedia) may seem insignificant, but 25,000 lines of code down the road, you'll be thankful. Especially if there aren't too many comments.
[*]Python already has many features you'd have to code yourself in C++. For example, Python has a built-in dictionary data type, which is like a C/C++ array, but you can use arbitrary objects (a floating-point number, a string, even a regular class) as indices. This is near impossible to implement in C++.
[/LIST]
**** END DYNAMIC LANGUAGE RANT ****

> **simeon87 said:**
> Let me start off by saying that it's actually a  nicely designed game, reminiscent of the retro games of the good old  days.
Regarding the code, it's clear that you've made an effort to familiarize  yourself with concepts such as class, functions, header files etc,  which is a good thing.

Although you are rather consistent with your coding style, it's unlike  most C++ code I've seen (in particular the way the code is indented and  lowercase names for classes).
You are also using global variables which is discouraged by many. This  makes it hard to test the software and to reuse pieces of code.

I'm also a bit curious about how you made the player class. The player  is a good choice for an object and you can use it to represent various  information, such as health, inventory, items, etc. But you have chosen  to put player_health as a global, which seems a bit odd. It would make  more sense to have it in the player class and then to access it with  player->health.

I also wouldn't put Loadgame and Savegame in the player class because  they're more part of the game itself, not part of the player object.  These can just be separate functions. Or, you can create a Level class  with load() and save(), which seems like a justifiable choice.

I think it's a good start and if you're willing to get into game  development, C++ is certainly a good language choice.

I'd stick Loadgame and Savegame into a completely separate class altogether, as it'll make the code easier. Look up the Strategy Design Pattern.

---

### Post by unknownPoster on 2011-06-04
> **DangerOnTheRanger said:**
> 

I'd stick Loadgame and Savegame into a completely separate class altogether, as it'll make the code easier. Look up the Strategy Design Pattern.

While Design Patterns are great, I feel that in this situation using the Strategy pattern is overkill.

Using Design Patterns just for the sake of using them is much worse than not using them at all (Other than educational purposes).I've always felt that it's possible to over-engineer a problem.

---

### Post by Ghostmn on 2011-06-04
> **ThatCoolGuy220 said:**
> LOL is very addictive I wish there were more levels....
it reminds me the zelda-like games.

Good job bro, I'm studying C++ too, this is a very good reference for my future job.

PD: I use Code Google too.

Thanks! It's nowhere near complete. I still need to add a few more enemies, bosses, levels etc.

---

### Post by Ghostmn on 2011-06-04
> **DangerOnTheRanger said:**
> It's triple reply time! :D

Kernel development? If you mean the Linux kernel, you should study C, not C++, as C is used in the Linux kernel (as well as practically every other OS out there: Windows, OSX, BSD...) It's true, the languages have a lot in common (a C++ compiler, for example, can compile C programs), but there are some differences, including:

[LIST]
[*]Agile/OO design being favored for C++, compared to structured design in C
[*]The lowest level of granularity in design for C++ is the class, compared to the function for C
[*]Emphasis on classes that provide their own algorithms in C++, compared to non-interactive data structures that are modified by functions in C
[/LIST]

  
I'm studying both C and C++ concurrently. EDIT Also by software development I mean software development. I would like to make software.

---

### Post by ThatCoolGuy220 on 2011-06-04
hahaha ok just dont forget to tell me when its done 

=D

---

### Post by nvteighen on 2011-06-04
It looks pretty good, though I suggest you to take a look at ncurses. That's a library that gives a very handy API for text-based interfaces, for instance, it solves the "backlog" issue, i.e. old screens getting accumulated in the terminal (just scroll the terminal up...).

But you've written a well-designed game: maps are loaded from file, you've written a Makefile, you're using threads, etc., those are essential skills for a beginner to learn. Ok, there may be some annoying global variables, but in general it looks even better than anything I'd write :P

I'll take some more time looking at the source and tell you if I find something noteworthy.

---

### Post by Ghostmn on 2011-06-04
> **nvteighen said:**
> It looks pretty good, though I suggest you to take a look at ncurses. That's a library that gives a very handy API for text-based interfaces, for instance, it solves the "backlog" issue, i.e. old screens getting accumulated in the terminal (just scroll the terminal up...).

But you've written a well-designed game: maps are loaded from file, you've written a Makefile, you're using threads, etc., those are essential skills for a beginner to learn. Ok, there may be some annoying global variables, but in general it looks even better than anything I'd write :P

I'll take some more time looking at the source and tell you if I find something noteworthy.

Well thanks! I noticed the "backlog" issue a month ago. I am not interested in learning a new API just yet. I want to understand the standard one first.

 Thank you everyone for the input! More is welcome!

---

### Post by djohnson3278 on 2011-06-04
In C, global variables aren't really all that evil...espeically if your whole application is designed as a state machine.  You could go shead and say: "But, you can use the static storage class inside a function", but then I counter with the need to store many globals in a header file.  Anything having to do with threading is of course separate from the globals...but I really don't see how they are that evil.

From an assembly programmer's standpoint, initialized globals are data section objects...locals are stack objects.  I have plenty of room in my initialized data, but not so much in my stack.  :p

---

### Post by DangerOnTheRanger on 2011-06-04
> **unknownPoster said:**
> While Design Patterns are great, I feel that in this situation using the Strategy pattern is overkill.

Using Design Patterns just for the sake of using them is much worse than not using them at all (Other than educational purposes).I've always felt that it's possible to over-engineer a problem.

It's applicable in this case because if a Level class knew both how to store/load a level, that would mean the Level class would be not only handling business rules (number of tiles, where which tile is, etc...), it would handle level loading. This means it'll change more often than necessary. So I'd recommend adding a separate class, that just knows how to load/save a level. That way, only said class would have to change when you add a new sort of tile, or a new monster.

---

### Post by Ghostmn on 2011-06-04
> **djohnson3278 said:**
> In C, global variables aren't really all that evil...espeically if your whole application is designed as a state machine.  You could go shead and say: "But, you can use the static storage class inside a function", but then I counter with the need to store many globals in a header file.  Anything having to do with threading is of course separate from the globals...but I really don't see how they are that evil.

From an assembly programmer's standpoint, initialized globals are data section objects...locals are stack objects.  I have plenty of room in my initialized data, but not so much in my stack.  :p

One day I hope to have as much knowledge as you in programming.

I'm experimenting with everything and seeing how they work with each other, hence the random thread to globals. 

PS. I only understood maybe 1/2 of what you said :popcorn:

---

### Post by unknownPoster on 2011-06-05
> **DangerOnTheRanger said:**
> It's applicable in this case because if a Level class knew both how to store/load a level, that would mean the Level class would be not only handling business rules (number of tiles, where which tile is, etc...), it would handle level loading. This means it'll change more often than necessary. So I'd recommend adding a separate class, that just knows how to load/save a level. That way, only said class would have to change when you add a new sort of tile, or a new monster.

I believe your understanding of the strategy pattern is a bit wrong.

The strategy pattern allows for algorithms/functions to be determined at runtime rather than compile time. If a class is just told to call save or load when appropriate this is not an implementation of the strategy pattern.

[http://en.wikipedia.org/wiki/Strategy_pattern](http://en.wikipedia.org/wiki/Strategy_pattern)

---

### Post by Ghostmn on 2011-06-05
Regarding the two functions loadgame/savegame. Would it be best to take them out of the player class and put them into their own file?

---

### Post by NovaAesa on 2011-06-05
Do you have the movement controls defined in more than one place? I'm using Dvorak and want to change the controls. I changed them in file Ascii.cpp and that was fine for moving the character around, but it didn't change the controls for the menus.

---

### Post by cgroza on 2011-06-05
> **NovaAesa said:**
> Do you have the movement controls defined in more than one place? I'm using Dvorak and want to change the controls. I changed them in file Ascii.cpp and that was fine for moving the character around, but it didn't change the controls for the menus.
Glad to see I am not the only one using it!:D

---

### Post by Ghostmn on 2011-06-05
> **NovaAesa said:**
> Do you have the movement controls defined in more than one place? I'm using Dvorak and want to change the controls. I changed them in file Ascii.cpp and that was fine for moving the character around, but it didn't change the controls for the menus.

Sorry for the inconvenience! My keyboard is qwerty so i programmed for it.

I have them defined in ascii, mainmenu, and player I believe.

---

### Post by NovaAesa on 2011-06-06
Thanks, I just changed all the values and had a bit of a play. Nice work! As nvteighen said though, it could be a good idea to look into ncurses.

---

### Post by slavik on 2011-06-06
> **DangerOnTheRanger said:**
> It's triple reply time! :D



Kernel development? If you mean the Linux kernel, you should study C, not C++, as C is used in the Linux kernel (as well as practically every other OS out there: Windows, OSX, BSD...) It's true, the languages have a lot in common (a C++ compiler, for example, can compile C programs), but there are some differences, including:

[LIST]
[*]Agile/OO design being favored for C++, compared to structured design in C
[*]The lowest level of granularity in design for C++ is the class, compared to the function for C
[*]Emphasis on classes that provide their own algorithms in C++, compared to non-interactive data structures that are modified by functions in C
[/LIST]
So there are a lot of differences in C and C++. Learning one will give you a head start in the other, but there's a minor paradigm gap between the two languages.

Also, what do you mean by *software development*? That's a somewhat ambiguous term. Could you clarify, please?



**** BEGIN DYNAMIC LANGUAGE RANT ****

If you're just starting out in programming, and you'd like to do game development, I'd recommend Python (my personal choice) or Lua, instead of C++.

The main reasons are:

[LIST]
[*]Even if you're developing on a Linux system, as long as the game engine you use is also written in Python or Lua (or is cross-platform), porting your game to Windows requires little to no effort on your part. You don't even *need* to have Windows!
[*]Python (or Lua) is much nicer on the eyes compared to C++. Syntactic sugar (look up that term on Wikipedia) may seem insignificant, but 25,000 lines of code down the road, you'll be thankful. Especially if there aren't too many comments.
[*]Python already has many features you'd have to code yourself in C++. For example, Python has a built-in dictionary data type, which is like a C/C++ array, but you can use arbitrary objects (a floating-point number, a string, even a regular class) as indices. This is near impossible to implement in C++.
[/LIST]
**** END DYNAMIC LANGUAGE RANT ****



I'd stick Loadgame and Savegame into a completely separate class altogether, as it'll make the code easier. Look up the Strategy Design Pattern.

Oh, wow ... where to begin?

[LIST=1]
[*]You are aware that C++ has something called a Map, right?
[*]Are you aware that Python is slow when using OpenGL? (take a guess why)
[*]Lua was designed in place of Tcl (which itself was targeted at being embeded)
[*]Lowest level of design in C++ is a function ... it's called backwards compatibility with C
[*]C++ allows you to put functions inside structures to make management easier. There are algorithmic functions in C++ that are outside of any class, simple example is sort.
[*]Last but not least, the OP is not asking you to recommend/compare languages.
[/LIST]

---

### Post by Ghostmn on 2011-06-06
> **slavik said:**
> Oh, wow ... where to begin?

[LIST=1]
[*]You are aware that C++ has something called a Map, right?
[*]Are you aware that Python is slow when using OpenGL? (take a guess why)
[*]Lua was designed in place of Tcl (which itself was targeted at being embeded)
[*]Lowest level of design in C++ is a function ... it's called backwards compatibility with C
[*]C++ allows you to put functions inside structures to make management easier. There are algorithmic functions in C++ that are outside of any class, simple example is sort.
[*]Last but not least, the OP is not asking you to recommend/compare languages.
[/LIST]


Nicely said. I didn't bother to read all of his post to be honest.

---

### Post by Ghostmn on 2011-06-06
> **NovaAesa said:**
> Thanks, I just changed all the values and had a bit of a play. Nice work! As nvteighen said though, it could be a good idea to look into ncurses.

I will probably begin using non-standard API's once i'm familiar with the standard API. I'd rather not have dependencies as a new programmer. It's more convenient when asking for help as anyone willing to help can dive into the source without installing another library.  

I might use ncurses once 0.1 comes out though :P

---

### Post by SledgeHammer_999 on 2011-06-07
ncurses is widely used IMO.(never used it though)

Are you open for contributions? I am a hobbyist C++ programmer and your project seems simple enough for me to get involved...

---

### Post by Ghostmn on 2011-06-07
> **SledgeHammer_999 said:**
> ncurses is widely used IMO.(never used it though)

Are you open for contributions? I am a hobbyist C++ programmer and your project seems simple enough for me to get involved...

The project was a learning experience. I really don't have much plans for it. I also don't think such a simple game can handle any intermediate concepts which i'm starting to get into.

If you want to contribute to it, feel free. I just need a gmail account so I can add you to the contributors list.

---

### Post by slavik on 2011-06-07
or you can accept patches ;)

---

### Post by Ghostmn on 2011-06-07
> **slavik said:**
> or you can accept patches ;)

True. I will accept patches.

---

