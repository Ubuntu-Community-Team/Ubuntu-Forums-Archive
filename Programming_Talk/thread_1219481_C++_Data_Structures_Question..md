---
title: "C++ Data Structures Question."
date: 2009-07-21
forum: Programming Talk
---

### Post by pepperphd on 2009-07-21
I'm teaching myself to program, so forgive me if this question is one of the first answered in a relevant class on the subject.   The standard library seems to make data structures defined by me frivolous. Once I learned how to use vector, I couldn't (and still haven't been able to) find a reason to ever use new and delete again. Should I just do it for the practice, or maybe there are more abstract structures that vector just doesn't cut it for?

---

### Post by c0mput3r_n3rD on 2009-07-21
New and delete are keywords for pointers for your own memory allocation and are used A LOT in C++.

---

### Post by pepperphd on 2009-07-21
> **c0mput3r_n3rD said:**
> New and delete are keywords for pointers for your own memory allocation and are used A LOT in C++.

 Why should I ever define a fickle data structure to test extensively when vectors seem so much more workable?

---

### Post by Mirge on 2009-07-21
There will be times where you need to define your own data types, or use data types others have created (IE: Qt4)... you'll want to be familiar with memory management, imo.

---

### Post by issih on 2009-07-21
I admit I am confused by this thread.

Vectors are for storing lots of something, they are a clever array, nothing more or less.

How is that equivalent to a data structure?

If your data structure is nothing but a collection of one type, e.g. three integers or something like that, then a simple array, and therefore a vector, would cut it. However for anything more complicated, say a bookmark storing the book and the page number, you want a data structure because you have a string and an int.

Obviously this is just a tiny example, and in reality data structures only really come into their own for something a bit more serious, like a teelvision program say...strings(name of program, description, channel name) integers(date and time broadcast, number in series), booleans(HD, 5.1 sound, etc)

Thats a lot of data about one thing....and they are not all the same type...so a vector is no use.

Of course in reality you'd make a full blown class, and implement some methods to do useful things, like say record(), alert() or whatever you wanted.

Just do not see how a vector is equivalent to a data structure or a class at all...

---

### Post by TheStatsMan on 2009-07-21
> **issih said:**
> I admit I am confused by this thread.

Vectors are for storing lots of something, they are a clever array, nothing more or less.

How is that equivalent to a data structure?

If your data structure is nothing but a collection of one type, e.g. three integers or something like that, then a simple array, and therefore a vector, would cut it. However for anything more complicated, say a bookmark storing the book and the page number, you want a data structure because you have a string and an int.

Obviously this is just a tiny example, and in reality data structures only really come into their own for something a bit more serious, like a teelvision program say...strings(name of program, description, channel name) integers(date and time broadcast, number in series), booleans(HD, 5.1 sound, etc)

Thats a lot of data about one thing....and they are not all the same type...so a vector is no use.

Of course in reality you'd make a full blown class, and implement some methods to do useful things, like say record(), alert() or whatever you wanted.

Just do not see how a vector is equivalent to a data structure or a class at all...

I think the OP is talking about the use of new and delete internally in a class rather than vector being the only data structure. Obviously you could create a class to do everything in your example without using new and delete.

I find I use new and delete when creating basic heavily used containers (just to clarify I mean new and delete inside the container implementation). For example internal storage in a matrix class or a sparse matrix class I find it slightly more convenient and I think more sensible to use a C style array for internal storage. If you look at the source for eigen and blitz they do the same thing.

---

### Post by issih on 2009-07-22
I also see in no way how a vector removes the need for new and delete....

vectors are arrays for storage, that have all the implicit limitations of any other scoped variable (unless you create a vector on the heap with new).

new and delete allow the use of custom memory management, that is their purpose, how is that related to data structures as such?

The OP's question does not (to me at least) make any sense

---

### Post by MindSz on 2009-07-22
new and delete are just ways of allocating/deallocating memory. It can be used with any data type (user defined or otherwise) and for most simple programs they are not needed.

If you think you don't need to manually allocate/deallocate memory, then don't worry about it.

---

### Post by nvteighen on 2009-07-22
The existence of a good data structure doesn't mean you won't ever use anything else :)

---

