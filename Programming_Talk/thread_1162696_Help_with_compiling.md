---
title: "Help with compiling"
date: 2009-05-18
forum: Programming Talk
---

### Post by L473ncy on 2009-05-18
I'll be upfront. This is homework related but it's just compiling issues I'm having.

OK... So usually I'd use emacs + g++ to write and compile my programs. BUT since my Ubuntu install died on me (and I don't have the time to fix it until mid-June) I have to compile and run my programs with Visual Studio 08 (although in my final handin of the project the source has to be able to compile and run on a Unix machine using g++).

I'm totally new to VS08. I actually got it a while back but never bothered to actually use it since I would just boot up on my Ubuntu partition and write + compile with emacs.

SO can anyone with experience in VS08 please help me? (Yeah yeah I know this is a Linux forum but you never know, we're all geeks so there has to be at least one person that knows the in's and out's of VS08.

Specifically I'm looking for how to compile and make an exe so that I can run and test my program. It looks from my googling that I should be able to press C-F5 and it should "start without debugging" whatever that means (it's grayed out in the menu BTW). Also there is an option in the test menu >> run >> test but those options are also grayed out. So what am I doing wrong here???

PS: I am using files with .cc extensions. I don't think it should really make a difference though but should I have made the extension .cpp??? To me it's all the same but it might make a difference in VS08.

---

### Post by thelamb on 2009-05-18
Did you create a project? Or are you opening a single file n trying to compile it?

If you create a project and add the files the commands in the menu should be enabled

---

### Post by L473ncy on 2009-05-18
EDIT [RESOLVED] I was being stupid and the prototype didn't match the actual function call....

---

### Post by geirha on 2009-05-18
Have you ever used cygwin? It installs a linux-like environment in windows, where you can install emacs and g++ amongst a lot of other common linux packages. If it compiles in cygwin with g++, it should compile on most unix plattforms with g++ as well.

[http://cygwin.org](http://cygwin.org)

---

### Post by L473ncy on 2009-05-19
Well thanks for the tip I'll have to try it out but for now I don't want to be messing around since I have "mission critical" timelines to be met and can't have an unstable machine or one that's out of commission.

Also I'm getting a weird problem with my exe, it's just the way I'm writing it though. It gets stuck in an infinite loop and I can't for the love of god find where it's looping infinitely.

The function I'm supposed to be doing is recursive and as such has a base case (when "y ==10"). It also calls itself in the "else" case. So those two are pretty standard for all recursive functions but is there anything else I'm missing? The way I have it setup might be a bit weird though since I'm basically doing:

if (...) // Base case
(...)
else if (...) //Alternative
(...)
else //If neither of above true default to this
(...)

Should I be able to do that in a recursive function? Logically to me it seems like a yes, and why shouldn't it be? But I've been looking at it for a while and haven't seen where it's wrong. I've even been going through it logically, writing it out on paper and making little drawings but nothing.

I know how much you guys don't like people asking for help on homework (it's actually against the rules of this section) but I'm not asking directly for help just some pointers and conceptual ideas. I really want to learn and figure this out myself but some tips would be really appreciated. I don't think I'll post my code here just because of the stigma that would be attached, (that I'm a noob who can't do their comp sci homework).

Basically I have to traverse a maze with a "robot". The map is read in from a file (testfile.dat) and it contains a bunch of ints (I open the file, read in, and input the datastream into a 2D integer array). From there I have to start from any position at the top, traverse only to squares that are 1 greater or 1 less than the current square the robot is on. From there I output the number of paths that the robot can take to get to the end ("bottom" of the maze).

I have the following functions:

findpaths, getvalue, and move

The move function I made the recursive function (so it will call itself 3 times within each function call, a move left, move down, and move right) at each step it will try to get a value from the current square and if it's +/- 1 then it will update it's current position to reflect that then repeat. If it can't then it will exit the function and return (backtrack to the above function call) to go to the next possible path to test if it's valid and can get to the bottom of the maze.

The question is, is there anything I'm missing, or obviously wrong with the way I'm working it out?

---

