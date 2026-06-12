---
title: "idea for a simple program"
date: 2007-05-04
forum: Programming Talk
---

### Post by DrPppr242 on 2007-05-04
well everyone says the only way to learn programming is to write  some programs, so this thread is for giving ideas for simple programs that could be written by some with only basic knowledge could write.

---

### Post by raja on 2007-05-04
I guess it is difficult for anyone to suggest something unless we know how much programming you know now, what language you are learning (or intend to learn, etc).

---

### Post by DrPppr242 on 2007-05-04
I was hoping for an pretty much any idea that could be done as a command line program in multiple languages, I personally mostly know c++.

---

### Post by seamless on 2007-05-04
A good project is to write your own versions of command like cp, mv, ls and so on. Also if you have a lot of pictures or music write something that will give you the meta info out of them and or help you to organize them. You could also try your hand at some client server programming. An echo server and client isn't all that hard. If you're just looking to learn then just look at what has already been done and make your own version of it.

---

### Post by slavik on 2007-05-05
here's a simple rundown for ANY language (note that it is vague, also assuming a declarative language like C)
----------------
0. ability to describe what you are going to be doing in the program (and the idea behind it) (teaches good documentation)
1. a hello world - print a message on the screen (teaches a simple function call and ability to get a simple program going)
2. create a variable, assign some value to it, then print it (teaches binding of variables to values)
3. use ALL looping contructs (without being clever) and display each value (a counting program) (teaches loops)

by now, your skills are turing complete ;)

4. comparison statement (if, unless, ...)
5. nested loops and/or comparison statements
6. use pointers/references to alter data inside functions so that the change carries back to the calling function
7. learn about classes/structures (C and C++ structures are not exactly the same)
8. dynamic memory allocation. allocate memory, put stuff in, print it, free the memory (if you can)

8b. learn about linear/bubble sort and about binary search

=== here is the fun stuff begins ===

9. understand what Stack and List are.
10. write a stack library and make use of it by using it to add two numbers (postfix notation, if you get a number, push it on stack, if an operator, pop top 2 items and perform the operation. only concerned with +*/- at this point) (a cut down version of 'dc')
11. write a queue library and use it (stuff can print in turn or something)
12. write a list and use it (list of names, allow to view the list, remove and add items to the list and allow user to specify the place)
13. learn about binary trees and implement one with preorder traversal, inorder traversal, post order traversal (use a tree to sort numbers)
14. write a sorted list library (mod of the list/queue) and put stuff in, then take it out and print it

Basics about LIST and BINARY TREE:
LIST: Allows you to put stuff in where you want (start, end, middle)
QUEUE: Allows you to only put things into the end and remove stuff from the beginning (like a checkout line)
STACK: allows you to put stuff in only at the end, same for removal (only at the end)

BINARY TREE: VERY IMPORTANT!!!
an empty tree is a tree with no nodes.
a single node is a tree.
each node may have upto 2 children (sub trees), usually called LEFT and RIGHT (when I was taught, may call them A and B or TOP and BOTTOM, or even YOUGER and OLDER, your choice, I suggest LEFT and RIGHT)

reason for the layout: done in short time and quickly, reason for pointers/references and structures before the fun stuff is because it is the basis of the fun stuff.

Also, if you post questions, we will help (make sure to title your thread with language name and the type of thing you are working with and/or having problems with, because I will not read Python threads since I am not familiar with it, expect me on C, C++, Perl, Java, maybe Scheme, Prolog, Ruby).

---

### Post by kevinlyfellow on 2007-05-23
I need ideas too so I can learn, but here are some things I've done:

Make a "tower of hanoi" program.

Simulate the Monty Hall problem (there's a neat little subtlety in this one ;-)) [http://en.wikipedia.org/wiki/Monty_Hall_problem](http://en.wikipedia.org/wiki/Monty_Hall_problem)

Using a Monty Carlo method, estimate the value of pi

Write a tea cooker program

---

### Post by pmasiar on 2007-05-24
> **DrPppr242 said:**
> well everyone says the only way to learn programming is to write  some programs, so this thread is for giving ideas for simple programs that could be written by some with only basic knowledge could write.

See wiki in my sig - simple tasks for beginners

---

### Post by smartbei on 2007-05-24
Well, I am having a lot of fun doing the challenges in projecteuler.net - not all of them are for beginners, but they have are generally arranged by skill level.

---

### Post by DucentiVigintiDuo on 2007-05-24
> **smartbei said:**
> Well, I am having a lot of fun doing the challenges in projecteuler.net - not all of them are for beginners, but they have are generally arranged by skill level.

Thanks for that link; it seems really interesting. 
Unfortunately I can't do any of these challenges for another two weeks (exams) but I'll definitely start solving them soon enough :D

---

### Post by raja on 2007-05-24
Project Euler is more of numerical challenges. Another interesting set of challenges specific for python is at [www.pythonchallenge.com](www.pythonchallenge.com). Very addictive.

---

### Post by DucentiVigintiDuo on 2007-05-24
Still, it's a mathematical challenge that involves programming...doesn't get any better than this imo. I haven't tried Python yet, but if I do I'm definitely checking this challenge.

---

### Post by kevinlyfellow on 2007-05-24
> **smartbei said:**
> Well, I am having a lot of fun doing the challenges in projecteuler.net - not all of them are for beginners, but they have are generally arranged by skill level.

I've just signed up :-)  I'm liking this.  I'm on the third problem now

---

### Post by FuriousLettuce on 2007-05-26
Thanks for introducing me to projecteuler.net, it really is a good way to challenge yourself and get your numerical skills up. It's interesting finding the different ways (other than brute forcing) that you can achieve each post!

---

### Post by Mathiasdm on 2007-05-27
Damnit, why did you tell me about Project Euler?

I'm addicted :p 6 down, 150 to go!

---

### Post by kevinlyfellow on 2007-05-27
> **Mathiasdm said:**
> Damnit, why did you tell me about Project Euler?

I'm addicted :p 6 down, 150 to go!

I'm addicted too, I've done 13 and I'm stuck!  What's humbling about this site is that whenever I have a solution, I look in the forums and there is always someone who did it with a few lines of code and its significantly faster than my code.  But its been a great learning tool thus far!

---

### Post by Mathiasdm on 2007-05-27
Yep, I entirely agree.
It's a great way to improve your skills.

Look at those people doing the challenges in Assembly, it's crazy :o

I seem to have a bug in my solution for the 7th problem (10001th prime number), but I think I'll study for my exam, before continuing my quest for the right solution :p :popcorn:

**Also, note that only 15 members have solved 100% of the problems!**

---

