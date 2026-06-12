---
title: "How to test C knowledge"
date: 2011-12-24
forum: Programming Talk
---

### Post by biggiee on 2011-12-24
I have been reading a book on C aswell as coding along with the problems in the book a while. I am looking for somewhere to test my knowledge of the language, or possibly find/move on to another book.
In addition, I have been thinking about which language i should move onto next. C++ seems like the logical choice, but languages such as Python and Ruby have also caught my eye.

Any input would be greatly appreciated.
thanks,
~biggiee

probably no one has heared of the book but it is:
Applied C: An introduction and More
by Alice E. Fischer, David W. Eggert, Stephen M. Ross

---

### Post by Frak on 2011-12-24
Alright, I'll give you a test. If you can do it, I'll assume that you have at least a beginners understanding:

Write me a program that acts as a change calculator. You will prompt the user with a menu. You will take the response as a number (1. add, 2. subtract, etc.). Display an error if an incorrect option is given, and then return them to the menu. The program should be able to add numbers, subtract numbers, multiply numbers, and divide numbers. The numbers are real (floats). After a successful option is entered, prompt the user for a real number on a new line, beginning with your countries money symbol (ex. $, €, £). Assume the user will only enter a valid real number (i.e. not a sentence). When the operation is done, print the answer and return them to the menu. If an answer cannot be reached, display an error and return to the menu.

Do that and you should have proficient beginners knowledge IMHO.

---

### Post by trent.josephsen on 2011-12-24
Well, this is only my personal opinion, but if you've only read through one book, you shouldn't even be considering moving on to another language.  Stick with C, *maybe* get another book (K&R being the one everybody suggests), read a lot of code, write some of your own, and learn to use C like a native speaker.  You won't get that from books alone, but you will get it from hacking on other people's code.  If you learn to write C *well*, you won't have so many bad habits to unlearn when you eventually move on to another language -- it's easy to learn a new syntax, but good programming habits transcend languages.

You might want to peruse the code of a program you regularly use, like a game -- NetHack is pretty cool (both in C, albeit a slightly old C, and an awesome game if you've never played).

Edit:  Oh yeah, there are some commonly used libraries you could also look into to enhance your C-fu -- pthreads, ncurses, and gtk come to mind.

---

### Post by fdrake on 2011-12-24
> **biggiee said:**
> I have been reading a book on C aswell as coding along with the problems in the book a while. I am looking for somewhere to test my knowledge of the language, or possibly find/move on to another book.
In addition, I have been thinking about which language i should move onto next. C++ seems like the logical choice, but languages such as Python and Ruby have also caught my eye.

Any input would be greatly appreciated.
thanks,
~biggiee

probably no one has heared of the book but it is:
Applied C: An introduction and More
by Alice E. Fischer, David W. Eggert, Stephen M. Ross
 
why don't you join the c#/c++ forum.(i am in there too and I knwo some other Ubu/fedora users are there as well   cprogramming.com) i am studying C too and in there you can test your skills by solving different isssue that users encounter: 

"practice makes perfect".

if you thing you have mastered something challenge yourself to do what others have failed in to.

---

### Post by Frak on 2011-12-24
I would also like to add that you'll learn a lot more about programming from experimenting than you will reading source code. If you don't have first hand experience in working with these tools, it's hard to get a full grasp on the concepts themselves. Your brain will fool you into thinking you know what you're doing when you don't. When you encounter this roadblock, work through it, and if you don't know how ***ask, ask, ask questions!*** Never be afraid to ask for help. The way a book, or I explain something isn't necessarily enough for *you* to understand it.

---

### Post by trent.josephsen on 2011-12-24
> **Frak said:**
> I would also like to add that you'll learn a lot more about programming from experimenting than you will reading source code. If you don't have first hand experience in working with these tools, it's hard to get a full grasp on the concepts themselves. Your brain will fool you into thinking you know what you're doing when you don't. When you encounter this roadblock, work through it, and if you don't know how ***ask, ask, ask questions!*** Never be afraid to ask for help. The way a book, or I explain something isn't necessarily enough for *you* to understand it.
I would like to respectfully disagree with part of your post.  While first hand experience is important, it's absolutely essential to read and follow code written by others, to understand how people have solved problems before you.  Code written for production, mind you, not education.  (Reading others' code will also give you sympathy for the poor maintenance programmer who has to poke through your code in 6 months or so, and may encourage you to write cleaner and better documented code.)  While experimenting solo may be fun, it also tends to lead to a *lot* of dead ends -- which can be really frustrating and lead to burnout (this happened to me the first time I tried to learn C).

Naturally, the best approach lies somewhere between pure experimentation and pure research, and is probably different for everybody.

OP, one place you might keep an eye on is the newsgroup comp.lang.c -- there are quite a few skilled programmers in there worth learning from, if you can avoid the mountains of spam and learn to filter out the trolls.

---

### Post by Frak on 2011-12-24
> **trent.josephsen said:**
> I would like to respectfully disagree with part of your post.  While first hand experience is important, it's absolutely essential to read and follow code written by others, to understand how people have solved problems before you.  Code written for production, mind you, not education.  (Reading others' code will also give you sympathy for the poor maintenance programmer who has to poke through your code in 6 months or so, and may encourage you to write cleaner and better documented code.)  While experimenting solo may be fun, it also tends to lead to a *lot* of dead ends -- which can be really frustrating and lead to burnout (this happened to me the first time I tried to learn C).

Naturally, the best approach lies somewhere between pure experimentation and pure research, and is probably different for everybody.

OP, one place you might keep an eye on is the newsgroup comp.lang.c -- there are quite a few skilled programmers in there worth learning from, if you can avoid the mountains of spam and learn to filter out the trolls.
I respectfully have to correct you. Nowhere did I say reading code is worthless. You have to expand somewhere, but don't overload yourself. You've essentially agreed with me, but I wasn't going to give him that information up front until he needed it (I didn't want him jumping too quickly into reading code he doesn't understand). Once you become comfortable with the basic tools, you can expand into more productive avenues.

If you've never used a measure, it's hard to build a house.

---

### Post by trent.josephsen on 2011-12-24
I'm glad we're all being so respectful :)

---

### Post by Frak on 2011-12-24
> **trent.josephsen said:**
> I'm glad we're all being so respectful :)
With respect, I do see that your respect is quite respectful.

---

### Post by fdrake on 2011-12-24
wow.... hohohh enogh respect ok? I am feel sick already :D

---

### Post by JDShu on 2011-12-25
IMO the best way is to think of a (realistic) project that really excites you and then program away. You'll make a ton of mistakes, but you'll get very familiar with the language, and programming in general while doing something you love.

---

