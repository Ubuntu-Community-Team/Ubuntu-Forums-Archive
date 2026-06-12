---
title: "Looking for a better way to run c++ console apps"
date: 2011-11-10
forum: Packaging and Compiling Programs
---

### Post by fabiosn on 2011-11-10
Hi, everyone (:

I start playing around with C++ and Code::Blocks for about two weeks now and everything is fine except for the fact that I can only run my programs on the IDE itself or by "cd'ing" to the directory it is located and using ./program

I've also tried the "run in terminal" option I'm given after double-clicking the executable in the project's bin folder, but all I get is a blank terminal for about a second, and the usual prompt after that.

Is there any easier way? 

Thanks in advance.

ps: I'm only developing console applications for now, so I guess that rules out any GUI related problems.

---

### Post by podmod101 on 2011-11-12
those are the only ways to run any code unless you add the directory for your console apps to the PATH...

try this (be careful, research PATH environmental variables first!)
PATH=$PATH:/your/directory/here

then you should be able to run any programs in the root of the directory specified above without the ./ or "cd-ing"

---

