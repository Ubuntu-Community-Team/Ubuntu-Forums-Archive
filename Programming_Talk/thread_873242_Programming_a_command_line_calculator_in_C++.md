---
title: "Programming a command line calculator in C++ ?"
date: 2008-07-28
forum: Programming Talk
---

### Post by Chake99 on 2008-07-28
Alright so although I do know some Java my C++ is quite (extremely) lacking as is my knowledge of programming in linux and I decided to try and brush up on both. 

To that end I've decided to make a small command line calculator that can be used by typing something like  "calc (3 + (4 ^ 3)) / 2" into the command line

Things which I'm unsure of --

-- where would I put such a program to be able to access it like other Linux utilities? (Are they bash scripts or something, and can I use c++?)

-- what is the standard format for writing these system utilities? (really where source code would be would answer this, so its most likely the same as the question before)

-- How does one use common data structures like binary trees while in C++? There's nothing provided in the way there is in Java, correct? Does linux/kubuntu have libraries I would reference if I wanted a linked list/stack/queue or would I program these structures myself?

---

### Post by mssever on 2008-07-28
> **Chake99 said:**
> -- where would I put such a program to be able to access it like other Linux utilities? (Are they bash scripts or something, and can I use c++?)
Put it in your $PATH. The Filesystem Hierarchy Standard recommends /usr/local/bin for this. Utilities are written in a variety of languages, but C is probably the most common.

---

### Post by slavik on 2008-07-28
I suggest looking into bc and dc

---

### Post by ceclauson on 2008-07-28
C++ has containers in its standard library, which are similar to collections in Java. As it turns out, there's a stack.

I googled C++ stack, and found a page that could help:
[http://www.cppreference.com/cppstack/index.html](http://www.cppreference.com/cppstack/index.html)

---

### Post by dribeas on 2008-07-29
> **Chake99 said:**
> "calc (3 + (4 ^ 3)) / 2"

-- what is the standard format for writing these system utilities? (really where source code would be would answer this, so its most likely the same as the question before)

-- How does one use common data structures like binary trees while in C++? There's nothing provided in the way there is in Java, correct? Does linux/kubuntu have libraries I would reference if I wanted a linked list/stack/queue or would I program these structures myself?

I would recommend you to use just one argument (quote the operation) or else directly use stdin for operation input, as this will simplify lots of boiler plate that won't teach you much.

C++ STL does not have binary trees, but it does have stacks/lists (doubly linked)/vectors/deque, you should start with some of the recommended beginner books (Standard C++, C++ Primer, Accelerated C++, ...) or tutorials.

   David

---

### Post by Reiger on 2008-07-29
I would avoid commandline arguments also. Use the shunting yard algorithm and you can make do with stacks for simple calculations; it's basically how a pocket calculator works as well. 

The shunting yard alogrithm 'parses' a convoluted expression by using built-in operator 'definitions'.

---

### Post by kknd on 2008-07-29
You will need to build an interpeter if you are planning to use accept expressions like
5+(9/(6*7)), taking care of the precedence and etc. 

If you want an example, I can send you by email (I will not post it here to don't mess with the topic).

---

### Post by dwhitney67 on 2008-07-29
Someone on this forum recently had a similar exercise.

The best approach is to convert the equation in infix notation into postfix notation.  (Btw, this step requires a little thought!)

Once you have the postfix equation, then use a stack to store the values/operands. Then just pop from the stack to compute the result.  (This is the easy part!)

The calculator problem is a typical exercise problem given in many school programming courses, not just C++.

P.S.  Infix to postfix... read about it here:  [http://scriptasylum.com/tutorials/infix_postfix/algorithms/infix-postfix/index.htm](http://scriptasylum.com/tutorials/infix_postfix/algorithms/infix-postfix/index.htm)

---

### Post by kknd on 2008-07-29
I've pasted [here]("http://pastebin.com/mba9a55") a simple math interpreter that I did some time ago. It supports things like:

x=10 
y=(10+x*(5+(6)))
y-x

---

### Post by Chake99 on 2008-07-30
Thanks everyone. The C++ STL seems to be what I was looking for. 'Tis a pity that it doesn't have trees though== I've already implemented a similar calculator in java with stacks and queues (with infix/postfix) and was hoping to try and also learn more about working with trees. Simply build a tree using proper priority rules and then if I'm not mistaken a preorder readthrough would give me the postfix expression

I guess I may make my own tree code then :).

I've been doing some C++ tutorials and thanks for the book suggestions, Dribeas.

Slavik, Can I ask what bc and dc are?

kknd, the link is appreciated.

---

### Post by dribeas on 2008-07-30
> **Chake99 said:**
> 
Slavik, Can I ask what bc and dc are?


I am not Slavik, but anyway... they are text calculators. You start them in the command line and type in whatever you want to compute. bc is an infix calculator and dc, if I recall correctly, is a reverse polish notation calculator (postfix notation). They have much more functionality than what you were aiming at.

You can always implement trees on your own. Building a simple data structure can be a good exercise on some of your C++ knowledge, moreover if you to generalize it through templates, work on strong exception safety...

   David

---

