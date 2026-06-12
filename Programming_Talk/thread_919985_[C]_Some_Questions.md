---
title: "[C] Some Questions"
date: 2008-09-14
forum: Programming Talk
---

### Post by loganwm on 2008-09-14
I'm working on a program for a learning experience that essentially interprets text into crude commands for a bigger project I'm working on.

Essentially this is how it works:

User input: "What is X?" ->

Translate into crude command: "?x" ->
*//question mark at beginning means "query" so the program handles that command as a query for the value of "x"*
Process command: return "x" ->
Await next command or exit.

So here comes my questions.

1) When a user enters the user input "x is 5" the command ":x=5" is sent to the program and the program sets the quasi-variable value for "x" is 5.

When storing and loading values saved by the program (it'll persistently remember certain variables in a file) I was thinking of using a linked list like the following:

struct node {
 name = "x";
 value  = 5;
 node *next;
}; 

Is this efficient for sorting, setting, and retrieving my quasi-variables or no? If not, is there a preferable way?

2) Hypothetically, could I have the main process of the program and the front end as separate programs?

The main processing program runs as a "daemon" for lack of a better term.
The front end is separate and sends and receives signals to and from (respectively) the daemon.

If so, can you put me on the right track?

3) Unrelated: (but out of curiosity) What is the stigma about using "goto" commands, is it inefficient, cause too much recursion, etc?

This is all in a planning phase still (with a little bit of basic linguistic processing capability in demo form) and I'm curious on how to do this effectively?

---

### Post by LaRoza on 2008-09-14
> **loganwm said:**
> 
3) Unrelated: (but out of curiosity) What is the stigma about using "goto" commands, is it inefficient, cause too much recursion, etc?


It leads to sloppy code and leads to more bugs. There are some cases it when it can be used, but you'll know those times when you know them.

goto itself is very efficient (learn assembly, you'll be goto'ing a lot).

---

### Post by cabalas on 2008-09-14
Linked lists are not the most efficient way for searching for the variables, you would probably want some form a binary search tree ([http://en.wikipedia.org/wiki/Binary_Search_Tree](http://en.wikipedia.org/wiki/Binary_Search_Tree)) some form of balancing tree would be a good idea.

As for goto commands they can be very helpful when used right. However in most cases they result messy unreadable code which is usually better known as spaghetti code ([http://en.wikipedia.org/wiki/Spaghetti_code](http://en.wikipedia.org/wiki/Spaghetti_code))

---

### Post by loganwm on 2008-09-14
> **cabalas said:**
> Linked lists are not the most efficient way for searching for the variables, you would probably want some form a binary search tree ([http://en.wikipedia.org/wiki/Binary_Search_Tree](http://en.wikipedia.org/wiki/Binary_Search_Tree)) some form of balancing tree would be a good idea.

As for goto commands they can be very helpful when used right. However in most cases they result messy unreadable code which is usually better known as spaghetti code ([http://en.wikipedia.org/wiki/Spaghetti_code](http://en.wikipedia.org/wiki/Spaghetti_code))

Ah, much appreciated, about the binary tree: it makes if quicker finding a member, correct? And is the structure of my node for data storage reasonable?

---

### Post by dwhitney67 on 2008-09-14
Your structure looks fine.  Insert into the binary tree based on 'name'.

You should look at the open-source code for the application 'bc'.

---

### Post by loganwm on 2008-09-14
> **dwhitney67 said:**
> Your structure looks fine.  Insert into the binary tree based on 'name'.

You should look at the open-source code for the application 'bc'.

[http://www.numbertheory.org/gnubc/](http://www.numbertheory.org/gnubc/)

Is this it?

---

### Post by dwhitney67 on 2008-09-14
yes, I believe that is it.

You probably already have 'bc' installed on your system.  Just invoke it from the command line.  Pass a '-l' (dash-ell) argument if you want higher precision with your computations.

I've only used 'bc' for basic operations.  But you can set variables equal to a value, then later recall these variables in your formulas.

For instance:
```
$ bc -l
x=10
y=3
d=x/y
d
```

---

### Post by loganwm on 2008-09-14
> **dwhitney67 said:**
> yes, I believe that is it.

You probably already have 'bc' installed on your system.  Just invoke it from the command line.  Pass a '-l' (dash-ell) argument if you want higher precision with your computations.

I've only used 'bc' for basic operations.  But you can set variables equal to a value, then later recall these variables in your formulas.

For instance:
```
$ bc -l
x=10
y=3
d=x/y
d
```

The data that I'll be working with in the memories of the program [the binary tree] will be pretty multi-purpose, things like addresses, names, special information, etc, although some numerical values will be stored as well.

Thank you for the reference, I'll look into it.


Any idea on how I could perhaps sort the tree by the name field? Should I just total the values of each char in the name, or another way?

---

### Post by dwhitney67 on 2008-09-14
> **loganwm said:**
> ...
Any idea on how I could perhaps sort the tree by the name field? Should I just total the values of each char in the name, or another way?

Sort them in lexicographical order ([http://en.wikipedia.org/wiki/Lexicographical_order](http://en.wikipedia.org/wiki/Lexicographical_order))

P.S.  Since you are writing code in C, use either strcmp() or strncmp().

---

### Post by loganwm on 2008-09-14
> **dwhitney67 said:**
> Sort them in lexicographical order ([http://en.wikipedia.org/wiki/Lexicographical_order](http://en.wikipedia.org/wiki/Lexicographical_order))

P.S.  Since you are writing code in C, use either strcmp() or strncmp().

I can't believe that I let alphabetic order slip my mind completely.

I'll see if I can get some demo code up and running in the next few days, I'd like some criticism on my coding, it always seems to help :)

---

