---
title: "c++ terminal loading line"
date: 2007-11-06
forum: Programming Talk
---

### Post by joebanana on 2007-11-06
Hi. I need some kind of indicator that computer is working something. I want to make a simple rotating line with stages: -- , \ , | , /  .How should I implement this (I process large files and it would look nice)

---

### Post by hod139 on 2007-11-06
[http://wooledge.org/mywiki/BashFAQ](http://wooledge.org/mywiki/BashFAQ)

FAQ 34

EDIT: I'm a moron, I thought this was a bash question, not a C++ question. 
The bash example can show you how to do it in C++ as well though, create a string of the spinner states, and iterator over the string.

---

### Post by Angry on 2007-11-06
you could try this:

std::cout << "\r" << the_current_character;

along with whatever you have in place to change the character, fired whenever you want to change the state of the line.  The \r will perform a carriage return without a new line, which will in effect overwrite the last character, giving the perception of animation.

The devil, of course, is in the implementation details.  I mean, if you control the loading process, you can fire that event off in there.  Else if you just want it spinning while the file loads, you'll have to get into threading or some such to handle the two processes.

---

