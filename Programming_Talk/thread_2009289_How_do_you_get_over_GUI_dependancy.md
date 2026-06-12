---
title: "How do you get over GUI dependancy?"
date: 2012-06-24
forum: Programming Talk
---

### Post by J-E-N-O-V-A on 2012-06-24
I'm starting to learn to program in C++ and I can't really do more than one for loop without making a small GUI within the program to help me. I suppose the obvious thing is to just stop doing it so I guess I'm asking whether you think it's okay to do this? Or am I limiting my programs? I find it difficult to visualise the program after a while and get completely lost when I get out of a few scopes.

For example I'm writing a program that counts the number of occurances of one string within another string. I'm using a number of for loops and if conditions to do this, but the output is crap. I can match a char within a string but not a string within a string. I've decided to start creating a table within the program and produce a purely graphical output and then remove the GUI part of the program when I have the code that I need. I feel as though I'm cheating somehow.

---

### Post by hyper2hottie on 2012-06-24
Alk you are doing with the gui is crwating a concrete visualization for yourself.  When you need to di something you can not visualize in you head you need to try drawing it out. 

With you example, draw several test strings. One that has a sequence in it once, one with it twice, and one without it. Figure out how you might do it mentally and make that be code. Whenever you wriye the code try think how it would work with your tests. This always helps me.  And remember you can prototype your code. If you are not sure how one part works then make small parts and expand upon it to get the final result. You can test your results without a gui. Just output to command line.

---

### Post by ofnuts on 2012-06-24
> **J-E-N-O-V-A said:**
> I'm starting to learn to program in C++ and I can't really do more than one for loop without making a small GUI within the program to help me. I suppose the obvious thing is to just stop doing it so I guess I'm asking whether you think it's okay to do this? Or am I limiting my programs? I find it difficult to visualise the program after a while and get completely lost when I get out of a few scopes.

For example I'm writing a program that counts the number of occurances of one string within another string. I'm using a number of for loops and if conditions to do this, but the output is crap. I can match a char within a string but not a string within a string. I've decided to start creating a table within the program and produce a purely graphical output and then remove the GUI part of the program when I have the code that I need. I feel as though I'm cheating somehow.
Adding print statements all over the code to figure out what it does is legitimate (even if using a debugger may avoid most of this)(*). Writing a full GUI is a bit overboard, though.

(*) If the code is a server, this transforms into logging, which is one the ways to figure out why the server didn't behave correctly.

---

