---
title: "How Long does it take?"
date: 2007-05-30
forum: Programming Talk
---

### Post by TreeFinger on 2007-05-30
I am finally buckling down and really learning a computer language, Python. I have dabbled with other computer languages like C++ but I have never really sat down for long periods of time thinking about programming. Right now I don't think I could write any useful program but that is part of my question. 

I stumbled upon [this tutorial]("http://www.developer.com/lang/other/article.php/625901") by Richard Baldwin and I really like it. I am not finished yet but I don't think it even gets into if statements! This is the first tutorial I have ever read that is like that. From the tutorial I know a lot about indexes and tuples, I understand them greatly so far which I could not say for any language I have tried to learn. Even C++ (which I had a semester in college to learn) I never understood arrays.

Back to the reason for my post.. I am wondering when will I actually be able to write a program or a script I could use? I know I won't be able to until I learn more about if and while statements, but what else is there to learn after that? I have a feeling there is a lot :p

Also where do you programmers come up with the ideas for your programs? I always think of what the first program I make will be..

---

### Post by Omnios on 2007-05-30
Hi there is a library thread with lots of tutorials here

 [http://ubuntuforums.org/showthread.php?t=255970&highlight=Library](http://ubuntuforums.org/showthread.php?t=255970&highlight=Library)

---

### Post by LaRoza on 2007-05-30
> 
Back to the reason for my post.. I am wondering when will I actually be able to write a program or a script I could use? I know I won't be able to until I learn more about if and while statements, but what else is there to learn after that? I have a feeling there is a lot

Also where do you programmers come up with the ideas for your programs? I always think of what the first program I make will be..

Usually, one can write useful, if short, programs as soon as the basic syntax is learned. Useful could be something very simple, the most useful program I wrote, that was not Web based, was a batch script for my sister. 

Here is a quote from this forum that I copied for my own reference, but I can not remember where it is exactly:

> 
here's a simple rundown for ANY language (note that it is vague, also assuming a declarative language like C)
----------------
0. ability to describe what you are going to be doing in the program (and the idea behind it) (teaches good documentation)
1. a hello world - print a message on the screen (teaches a simple function call and ability to get a simple program going)
2. create a variable, assign some value to it, then print it (teaches binding of variables to values)
3. use ALL looping contructs (without being clever) and display each value (a counting program) (teaches loops)

by now, your skills are turing complete

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

Also, if you post questions, we will help (make sure to title your thread with language name and the type of thing you are working with and/or having problems with,...

As to ideas for programs, the first motivating factor is need, and the other seems to be boredom.

---

### Post by pmasiar on 2007-05-30
> **TreeFinger said:**
> I am wondering when will I actually be able to write a program or a script I could use? I know I won't be able to until I learn more about if and while statements, but what else is there to learn after that? I have a feeling there is a lot :p

Also where do you programmers come up with the ideas for your programs? 

Yup, there is a lot to learn: data structures to model objects in PC, and it is not easy or obvious. Programming is much more than just corect syntax.

Check wiki in my sig, it has ideas to program: simple games, which you can show your friends to amuse them. And links to data structure lectures...

But with Python, learning is less sweat and more fun! Good luck!

---

### Post by ankursethi on 2007-05-31
Take a look at Dive into Python at diveintopython.org after you have completed that Baldwin tutorial. That will take you into advaced topics.

Need is the mother of all invention. Just look at what's missing, what could make your life easier and better and then start coding that piece of software. Otherwise just write a simple game (look at PyGame located at pygame.org).

---

