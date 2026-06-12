---
title: "Understanding structure of projects"
date: 2009-01-09
forum: Programming Talk
---

### Post by psycovic23 on 2009-01-09
Hey,

I've been trying to move from the simple programming to actually doing something, so I'm trying to just read/understand the code of crack-attack, but am completely lost.  I generated the Makefile from configure and tried to look for essentially the int main() of the program, but I don't really know where to look.  

Could someone give a quick rundown of how to read open source project code to see how it's organized and where I should start reading from?

Link to the source code: [http://aluminumangel.org/attack/dl_ii_linux.html](http://aluminumangel.org/attack/dl_ii_linux.html)

---

### Post by nvteighen on 2009-01-09
> **psycovic23 said:**
> Hey,

I've been trying to move from the simple programming to actually doing something, so I'm trying to just read/understand the code of crack-attack, but am completely lost.  I generated the Makefile from configure and tried to look for essentially the int main() of the program, but I don't really know where to look.  

Could someone give a quick rundown of how to read open source project code to see how it's organized and where I should start reading from?

Link to the source code: [http://aluminumangel.org/attack/dl_ii_linux.html](http://aluminumangel.org/attack/dl_ii_linux.html)
There's no way to know what a project's structure is until you read their code :p

This is FOSS: anyone does whatever he/she believes to be better. So criteria will often differ. Anyway, contacting the developers wouldn't hurt, I guess ;)

---

### Post by CptPicard on 2009-01-09
Anything from autotools is meant just for machine consumption -- don't try to read generated Makefiles or anything. Just hit the source as it is...

---

### Post by pmasiar on 2009-01-09
There is no way to tech you this. 

The only way for you is to become more competent programmer. After simple homework tasks, complete some more complicated training tasks, see wiki in my sig.

Learn more languages, so you will learn to see patterns in the code. There is no replacement for patience, perseverance and endurance.

See also [http://en.wiktionary.org/wiki/Sitzfleisch](http://en.wiktionary.org/wiki/Sitzfleisch) - train also your gluteus muscles :-)

---

### Post by pp. on 2009-01-09
The answers so far are correct if a bit one-sided.

If you want to understand the structure of a project, you have to know about structures. Sorry if that sounds self-evident, but there's a difference between understanding just the code and understanding the overall pattern of elements made out of that code.

To use an analog case (which is, of course, very rarely done in this forum) would be knowing about brick walls (code) vs understanding the static properties of a high rise or bridge.

Hence, once you have gained some knowledge and experience in larger-scale software structures, you won't have to actually read much of the code to gain a good understanding of the overall structure.

---

### Post by psycovic23 on 2009-01-09
> **pp. said:**
> The answers so far are correct if a bit one-sided.

If you want to understand the structure of a project, you have to know about structures. Sorry if that sounds self-evident, but there's a difference between understanding just the code and understanding the overall pattern of elements made out of that code.

To use an analog case (which is, of course, very rarely done in this forum) would be knowing about brick walls (code) vs understanding the static properties of a high rise or bridge.

Hence, once you have gained some knowledge and experience in larger-scale software structures, you won't have to actually read much of the code to gain a good understanding of the overall structure.

Well said.  I guess in response, how would I go about getting experience in larger-scale software structures?

I guess the problem I have now is...I can write code, but I can't program. I can do projecteuler stuff. I have an introductory grasp of data structures, and would be able to learn about more of them if I  needed. I can build "weekend project" web apps from the ground up, most recent being something like billshare or billmonk. But now what? I'd love to help out with other projects, but staring at their source code trumps me.  

Also, I'm an EE, so my next semester's work will only lead me away from this stuff (although I might be able to jump into a "intro to game devel" class).  

Any suggestions?

---

### Post by pp. on 2009-01-09
I can not offer a definite recipe for learning to do software structures. However, most engineering disciplines tend towards grouping the constituents of their constructs into sub-assemblies. EE is in that respect not all that different from software engineering (such as it is).

Most nontrivial software projects have the core of their functions organized into a 'model layer'. If the software has a GUI, expect some kind of MVC architecture: Model, View and Controller. Also expect some kind of vetting layer which is supposed to validate the input which reaches the different layers of the application. Expect some technical support or infrastructure for handling the database, mapping the entities of your model layer onto the data storage model, transaction logging and other persistence related stuff. On the other hand, expect multiple undo functions, a help system and so forth. More layers are bound to exist, I'm doing this from off the top of my head and on the spur of the moment.

Basically, most software systems which are operated by the end user tend to solve more or less the same architectural questions. Hence, after a while you kind of know what sorts of functions to expect in a project (besides those which are intrinsic to the problem the project is meant to solve). You also have some sort of idea how those parts of the architectures are bound to interact and, hence, how the code might be organized.

In fact, there might be considerable similarity in the structures of projects which are developed for the same purpose. Let's take, for example, Bulletin Boards or Wikis written in PHP and storing their data in one of the more popular database systems. I'd rather expect those to exhibit more or less the same overall structures.

However, some projects might structure their code along other than functional lines: by source language, by author, by release date or other even less obvious criteria. However, that would be like sorting the books in a library by the colors of their bindings or by the size of the volumes.

---

### Post by Cracauer on 2009-01-09
A good classes/functions/variable browser for C/C++ will help.

I wonder what people use for a klickable hierachy/caller browser on Ubuntu these days? I usually use emacs tags, but something more interactive would be nice.

---

### Post by monkeyking on 2009-01-10
If you want to get a overview of some larger project,
I can recommend doxygen.

It generates a nice html site with callgraphs, sourcecode viewer etc.
But nice thing is that you can click your way around the files,
it even has a builtin search engine if you have php

---

### Post by Cracauer on 2009-01-10
> **monkeyking said:**
> If you want to get a overview of some larger project,
I can recommend doxygen.

It generates a nice html site with callgraphs, sourcecode viewer etc.
But nice thing is that you can click your way around the files,
it even has a builtin search engine if you have php

Is it sufficiently powerful to cut through templates and preprocessor use?

---

### Post by WW on 2009-01-10
> **psycovic23 said:**
> Hey,

I've been trying to move from the simple programming to actually doing something, so I'm trying to just read/understand the code of crack-attack, but am completely lost.

crack-attack is written in C++.  Do you know C++?
> **psycovic23 said:**
> 
  I generated the Makefile from configure and tried to look for essentially the int main() of the program, but I don't really know where to look.

The C++ code is in the src subdirectory; this is a common convention for source code distributed in a tar file.

The src subdirectory does not have a file called main.cxx, so you could try using grep to find it:
```

$ grep "main" *.cxx
Attack.cxx:int main ( int argc, char **argv )
Game.cxx:int Game::remaining_time;
Game.cxx:  remaining_time = 0;
Game.cxx:  remaining_time = 0;
Game.cxx:    remaining_time += time - previous_time;
Game.cxx:    if (remaining_time < GC_TIME_STEP_PERIOD) break;
Game.cxx:    remaining_time -= GC_TIME_STEP_PERIOD;
Game.cxx:    if (remaining_time < GC_TIME_STEP_PERIOD)
Game.cxx:    remaining_time += time - previous_time;
Game.cxx:    if (remaining_time < GC_TIME_STEP_PERIOD) break;
Game.cxx:    remaining_time -= GC_TIME_STEP_PERIOD;
Game.cxx:    if (remaining_time < GC_TIME_STEP_PERIOD)
GarbageFlavorImage.cxx:  // check to see if we already have a copy of it in our main list
$ 

```
So main() is in the file Attack.cxx.

---

