---
title: "Need help with data structure in C/C++"
date: 2007-05-28
forum: Programming Talk
---

### Post by La Hechizera on 2007-05-28
hello,

my problem is:

for example if I have a pair of number {3,5} that means that program has to return 2, because the number of numbers in {} is 2. then if I add another pair, for example, {6,3}, that means that the program has to add it to the first pair, so sum them together, it means {3,5,6} and program has to return 3. in case if the next pair is {7,8} the program doesn't add it. etc

uff, I hope the description was good more or less.. So what I don't have a clue about is how to make this confusing thing to work using data structures (not using templates) in C or C++ or in some similar language. I'd be very grateful if someone could help me with this, even more grateful I'd be if someone could help me with the source, cuz I want to make some complicated program, but without this part it will never work :( please help me..

---

### Post by nitro_n2o on 2007-05-28
It looks like your implementing a Set! for c++ it's already implemented in the STL (Standard Template Library) this is a good resource about the STL [http://www.cs.brown.edu/people/jak/proglang/cpp/stltut/tut.html](http://www.cs.brown.edu/people/jak/proglang/cpp/stltut/tut.html)  
In java you can also use the "HashSet" class in java.util in both cases you can use the method size() to know the current size of the Set

---

### Post by La Hechizera on 2007-05-28
thank you, nitro_n2o, I really want to implement a set :)  but using data structures :( that is no templates and no STL :( I cannot figure out how to how to solve it

---

### Post by badactress on 2007-05-28
Hi,

I think reading up on linked lists is going to help you. I did a quick google & out of 3 or 4 sites, this one seems to be a pretty good explanation: [http://www.functionx.com/cpp/articles/linkedlist.htm]("http://www.functionx.com/cpp/articles/linkedlist.htm")

But is there a reason why you don't want to use templates? What you're doing in creating a linked list, is pretty much re-writing the 'vector' class of the STL.. Vectors are VERY easy to use! I mean so simple I laughed when I first looked into them & have never had to waste time creating linked lists since!

Hope this helps!

---

### Post by La Hechizera on 2007-05-28
thank you, badactress! I don't want to use a template because I want to understand how things work without templates :)

---

### Post by neo.patrix on 2007-05-28
I think it is pretty simple , create a class which has expandable ArrayList (I have been working with java for long enough), but with C/C++ u can play arround with pure good old pointers to make Array expandable,

When size of set is queried return the size of member array.
also, you need to implement certain important set operations like union and intersection, with C++ u can use operator overloading but that won't be advisable. B'cuz in set theory '+' and '-' operations have different meaning than union and intersection opreations.

I think you could easily get library class like 'Array' with dynamic memory or some similar data structure representation a class, use object of that class to create data member of your Set Class
to store set.

Then you certain algorithms for union and intersection, size operation won't be a big deal to implement. may be following link is helpful

[http://www.cphstl.dk/Report/SetAlgs/cphstl-report-2001-8.ps](http://www.cphstl.dk/Report/SetAlgs/cphstl-report-2001-8.ps)

It is template based , but if you need you can extract algorithms.

---

### Post by La Hechizera on 2007-05-28
thank you, neo.patrix :)

---

