---
title: "c++ help"
date: 2007-08-13
forum: Programming Talk
---

### Post by zerobinary on 2007-08-13
```
double x;
vector<double> homewrok;
while (cin>>x)
homework.push_back(x);

```
I don't get the line homework.push_back(x);
plz help

---

### Post by Mirrorball on 2007-08-13
It inserts x as the last element of the vector homework.

---

### Post by Wybiral on 2007-08-13
A vector (in this case) is a container from C++'s STL. It's a variation of a linked list (dynamically sizable array).

---

### Post by zerobinary on 2007-08-13
> It inserts x as the last element of the vector homework.
what do u mean by last element
u mean homework is written in the value of x by using push_back(x)

---

### Post by era86 on 2007-08-13
push_back is built in through STL in the vector.  It simply takes the element x and "pushes" it into the "back" of the vector.  Since element x is taken from cin, it will be inputed from somewhere (or something... im rusty).

---

### Post by zerobinary on 2007-08-13
> "pushes" it into the "back" of the vector. Since element x is taken from cin, it will be inputed from somewhere (or something... im rusty).
what does that mean by pushes back into vector ???????
sorry i need ur help again plz come back and help

---

### Post by slavik on 2007-08-13
you have a line of 10 people, when a new person enters the line at the back, it is what the function does (creates space for another thing at the end of the line and adds it to the end).

---

### Post by era86 on 2007-08-13
> **zerobinary said:**
> what does that mean by pushes back into vector ???????
sorry i need ur help again plz come back and help

Think of a vector as a list of something.  It can be anything.  Now let's make a vector of blocks and call it blocks.  We know all vectors have a function called push_back(element).  So we can add an element to our block vector using it!

blocks before push_back(): [empty]

blocks.push_back(block1);

Now blocks is not empty.  This is what we have:

blocks after push_back(block1): [block1]

Let's do it again!

blocks.push_back(block2)

Now we have:

blocks after push_back(block2): [block1, block2]

And so on...

---

### Post by zerobinary on 2007-08-13
k so it is like entering a a group of value 
when enter new value new value is at the back of the line

---

### Post by CptPicard on 2007-08-13
Guys, don't do people's homework when they obviously haven't been paying attention in class and deserve to flunk.. ;)

---

### Post by zerobinary on 2007-08-13
> Guys, don't do people's homework when they obviously haven't been paying attention in class and deserve to flunk.
school is over is out for summer, so no school.
Most importantly no class. LoL
U almost scared me to death by say that

---

### Post by zerobinary on 2007-08-13
k so it is like entering a a group of value
when enter new value new value is at the back of the line
plz answer that

---

### Post by zerobinary on 2007-08-13
ur voice is important to me. A little hand plz

---

### Post by Wybiral on 2007-08-13
Read at least one tutorial on abstract data types. I already mentioned it was a form of linked list, so: [http://en.wikipedia.org/wiki/Linked_list](http://en.wikipedia.org/wiki/Linked_list)

"push_back" is appending an element to the linked list. If you do not understand this concept, I suggest you do some googling on: stacks, queues, linked lists, and binary trees.

---

### Post by zerobinary on 2007-08-14
I got it is like a stack. Push back is poping one plate on top of on another. Covering one after one. Pops remove the pop plate
yeah thx guys

---

