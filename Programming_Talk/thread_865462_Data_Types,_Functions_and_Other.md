---
title: "Data Types, Functions and Other"
date: 2008-07-20
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-07-20
In programming i find implementing data types and functions most interesting.
could you list some interesting/unique data types or functions and a link to a description.
If you designed it then you can describe it but otherwise a post should look like this
> 
Vector - [Wikipedia]("http://wikipedia.org")

the goal it to have a quick list to go through
nothing basic like vector or bubble sort please, complexity is the fun part.

---

### Post by Can+~ on 2008-07-20
Wikipedia did it already:
[http://en.wikipedia.org/wiki/List_of_data_structures](http://en.wikipedia.org/wiki/List_of_data_structures)

Anyway, a short list:

Array - [Wikipedia]("http://en.wikipedia.org/wiki/Array")
List - [Wikipedia]("http://en.wikipedia.org/wiki/Linked_list")
Stack - [Wikipedia]("http://en.wikipedia.org/wiki/Stack_(data_structure)")
Queue - [Wikipedia]("http://en.wikipedia.org/wiki/Queue_(data_structure)")
Hash - [Wikipedia]("http://en.wikipedia.org/wiki/Hash_function")
Tree - [Wikipedia]("http://en.wikipedia.org/wiki/Tree_data_structure")

---

### Post by Wybiral on 2008-07-20
Hashtables, binary trees (balanced binary trees, red-black trees), heaps, "trie"s...

There are lots of useful datastructures, google around.

---

### Post by tinny on 2008-07-20
WeakHashMap

[http://java.sun.com/j2se/1.5.0/docs/api/java/util/WeakHashMap.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/WeakHashMap.html)

Weak hash maps are interesting. It is a little known fact that it is possible to get memory leaks in Java (sort of). If you store a key value pair in an ordinary HashMap and lose all external references to that key you in theory can have unused objects in memory (in the hash map) that will not be garbage collected (unless you manually iterate through the collections keys).

In a weak hash map this key value pair will be removed from the collection when all external references to that key are lost. However most of the time a standard HashMap will do just fine...

If you are interested here is some further reading on this topic.

[http://www.ibm.com/developerworks/java/library/j-jtp11225/index.html](http://www.ibm.com/developerworks/java/library/j-jtp11225/index.html)

---

### Post by tinny on 2008-07-20
Also...

AVLTree - [http://en.wikipedia.org/wiki/AVL_tree](http://en.wikipedia.org/wiki/AVL_tree)
B-Tree - [http://en.wikipedia.org/wiki/Btree](http://en.wikipedia.org/wiki/Btree)

---

### Post by stevescripts on 2008-07-21
Take a look here too, the Dictionary of Algorithms and Data Structures: [http://www.nist.gov/dads/]("http://www.nist.gov/dads/")

The NIST provides a lot of other useful info regarding programming besides
this one too.

Steve

As an afterthought - some of the folks who are always looking for something to 
code, can do their own implementations (in whatever language floats their boat) of many of the algorithms and data structures ...

---

### Post by moma on 2008-07-21
**[COLOR="Red"]Red[/COLOR]-Black** balanced (binary search) tree - [Wikipedia]("http://en.wikipedia.org/wiki/Red-black_tree")
An example implementation [here...]("http://www.futuredesktop.org/adt/"), unpack adt-0.1.tar.gz and read the README file.

[[img]http://bildr.no/thumb/230074.jpeg[/img]](http://bildr.no/view/230074)

---

### Post by dribeas on 2008-07-21
> **Mr.Macdonald said:**
> In programming i find implementing data types and functions most interesting.

There's not much more than data types and functions to programming... or I guess you meant algorithms. I would recommend some algorithm book ([Introduction to algorithms]("http://www.amazon.com/Introduction-Algorithms-Thomas-H-Cormen/dp/0262032937/ref=pd_bbs_2?ie=UTF8&s=books&qid=1216631636&sr=8-2") for example).

If you just code for fun, then I can recommend [ACM-International Collegiate Programming Contest]("http://cii-judge.baylor.edu/") problem database. There you can find problems that require the use of algorithms and data structures to find a solution. I believe they still validate solutions, I have not checked for some years now.

   David

P.S. For me design is the most important part of programming and while data structures and algorithms are fun (and useful bricks) you won't learn how to design from them.

---

### Post by nvteighen on 2008-07-21
> **stevescripts said:**
> 
As an afterthought - some of the folks who are always looking for something to 
code, can do their own implementations (in whatever language floats their boat) of many of the algorithms and data structures ...

Yes, it's a great idea, but anyone who takes this approach should always also research on what existing libraries there are that implement that data type or algorithm, so you know what tools exist in case you need them.

---

