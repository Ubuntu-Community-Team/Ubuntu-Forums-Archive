---
title: "What are Arrays and how do I use them?"
date: 2011-08-10
forum: Programming Talk
---

### Post by MasterNetra on 2011-08-10
Even from earliest introduction to the programming enviroment via Dragonspeak from Furcadia, I've encountered Arrays, but for the life of me I've been unable to understand what they are and how to use them. I am the type of person that works visually and if I can't see how something works with a visual model in my mind then I don't understand it.

If someone can explain this in a simple way that paints a simple visual image of the concept that would be appreciated.

---

### Post by dwhitney67 on 2011-08-10
Think of the "array" of mail boxes at the post office.

---

### Post by MasterNetra on 2011-08-10
> **dwhitney67 said:**
> Think of the "array" of mail boxes at the post office.

I am not familiar with the processes of a post office enough to make the connection.

---

### Post by CptPicard on 2011-08-10
```

x = [ a | b | c ]
      0   1   2

means

x[0] = a
x[1] = b
x[2] = c

```

---

### Post by nmaster on 2011-08-10
not sure if this is a serious question, but here goes... ... ...

i have no idea what Dragonspeak is, but perhaps this book might help a little bit with understanding how to program: [http://www.cs.berkeley.edu/~bh/ss-toc2.html](http://www.cs.berkeley.edu/~bh/ss-toc2.html)

rather than using arrays, it introduces you to sentences (which are exactly what they sound like) and then lists (also should be a familiar concept).  these are not the same as arrays, but i think it might be easier for you to understand sentences and lists.  once you understand how to use these data structures, perhaps arrays will make more sense.

---

### Post by MasterNetra on 2011-08-10
> **CptPicard said:**
> ```

x = [ a | b | c ]
      0   1   2

means

x[0] = a
x[1] = b
x[2] = c

```

So essentially its like a variable in that its a storehouse, except unlike a variable it stores more then one value?

---

### Post by nmaster on 2011-08-10
> **MasterNetra said:**
> So essentially its like a variable in that its a storehouse, except unlike a variable it stores more then one value?

yes. in fact, this is very similar to the explanation given on wikipedia :
> In [computer science]("http://en.wikipedia.org/wiki/Computer_science"), an **array data structure** or simply **array** is a [data structure]("http://en.wikipedia.org/wiki/Data_structure") consisting of a collection of elements ([values]("http://en.wikipedia.org/wiki/Value_%28computer_science%29") or [variables]("http://en.wikipedia.org/wiki/Variable_%28programming%29")), each identified by at least one [index]("http://en.wikipedia.org/wiki/Index_%28information_technology%29").
[http://en.wikipedia.org/wiki/Array_data_structure](http://en.wikipedia.org/wiki/Array_data_structure)

---

### Post by schauerlich on 2011-08-10
In C, you can think of variables as boxes laid in a row next to each other. When you declare an array, you just designate a segment of boxes next to each other as being part of the array, and hang on to a reference to the first box. If you know where the first box is, you can find the rest of the elements using an offset. ie, if you know that the number 5 is in the 12 box to the right after the first, you can locate it if you know where the first box is. That's all the numbers in brackets are, the offset from the first element.

```
int foo[20]; /* 20 boxes that are big enough to hold ints */
foo[12] = 42; /* find the first box in foo. Move over to the right 12 boxes, and put 42 in the box you find there. */
```

---

### Post by zkissane on 2011-08-10
Think of an array as a row of boxes on the floor, numbered sequentially starting at 0 (in most languages).  You can put one thing in each box (and frequently, you can only put one kind of thing into the boxes).  The boxes are also attached to each other, so you can pick up the whole group of boxes and hand it to someone else who wants it.

---

### Post by schauerlich on 2011-08-10
> **zkissane said:**
> The boxes are also attached to each other, so you can pick up the whole group of boxes and hand it to someone else who wants it.

Incorrect. You can pass around a reference to the first element, without moving the boxes. There's no way to "pick up" the boxes - although you can copy the contents of the boxes and put them in other boxes, somewhere else in the row.

---

### Post by MasterNetra on 2011-08-10
> **nmaster said:**
> yes. in fact, this is very similar to the explanation given on wikipedia :

[http://en.wikipedia.org/wiki/Array_data_structure](http://en.wikipedia.org/wiki/Array_data_structure)

I guess I can see how it would be used. Starting to learn PHP now, something I should of done years ago but didn't, but meh.

---

### Post by zkissane on 2011-08-10
> **schauerlich said:**
> Incorrect. You can pass around a reference to the first element, without moving the boxes. There's no way to "pick up" the boxes - although you can copy the contents of the boxes and put them in other boxes, somewhere else in the row.

I meant it to be much more metaphorical than you took it.  Some "people" (functions) expect to be "given" (passed) arrays.  Clearly the passing semantics (reference vs value) are another can of worms but are probably too overwhelming right now for someone struggling with the bare concept of arrays.  I haven't touched C in a long time, but in Java, for example, you do pass an array as a complete entity, not as the first element.  The compiler may ultimately reduce it down to the first element with offsets and all but that's way beyond the scope of what he was asking.

---

### Post by dwhitney67 on 2011-08-10
> **MasterNetra said:**
> I am not familiar with the processes of a post office enough to make the connection.

](*,)

---

### Post by ofnuts on 2011-08-10
> **dwhitney67 said:**
> ](*,)This is the picture of a mixed array of char/int/float:D

---

### Post by MasterNetra on 2011-08-10
> **dwhitney67 said:**
> ](*,)

lol the post office near me isn't like that.

---

### Post by MasterNetra on 2011-08-10
I may not have a 100% idea of how to fully utilize a array but I got a good enough of idea of it to where I think I can figure out the rest for myself. Thanks for helping. :)

---

