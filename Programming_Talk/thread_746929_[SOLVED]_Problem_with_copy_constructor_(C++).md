---
title: "[SOLVED] Problem with copy constructor (C++)"
date: 2008-04-06
forum: Programming Talk
---

### Post by Xnyper on 2008-04-06
I am working on a programming assignment and I could really use some help.  I don't want anybody to do this for me, I just need a nudge...

I would like to go back through some previous sections and re-learn templates, because I think that my problem lies with them--but I have only 24 hours to fix this, and tomorrow is a work day :-/

I am asked to write a definition for the copy constructor for the class queueType.  I also need to overload the assignment operator, but once I have the constructor done, that part is cake.

In the book, there is a simmilar class, stackType, with the copy constructor already defined.  I looked at that copy constructor for my inspiration here, and understood it for the most part.  the only part that I didn't understand is the first line, which read:
```
delete [] list;
```
This line does not seem to be causing my problem (outlined below) but I thought I would mention it so that when you see my comments that say "I don't really understand this line" you will see why it is there.  I'd love to understand why it is in there, but that is secondary to my need to finish this program.

The only way that the copy constructor that I referenced above differs from the one that I need to write is in the way it walks through the list.  the one mentioned above directly accessed the array, which I understand, but  the array I need to copy is circular (that is % maxQueueSize) which is where I run into trouble.

The algorithm I am using now was adapted from the one used in the book's test program, testProgFromBook.cpp.  Iit works great for stepping through a queue and printing its contents, but it is either invalid for assigning those contents to a new array, I am running into scope issues, or I have made some sort of template faux pas.


Attatched are 5 files, below are their explanations:

queueADT.h   this file is the header file for the "queue" class.  It was provided to me so that I could #include it, but I do not need to modify it in any way.

queueAsArray.h   this file is the header file for the class that I need to modify.  For the most part it too does not need to be modified.  The last few functions, however, were left empty for me to fill in.  You should notice the difference between my work and the pre-done work.

queueAsArray.h.bak  this is a copy of the header file for the class that I need to modify before I started playing with it--in case you want to see how it was before I messed it up

testProgFromBook.cpp  this was provided by the book to test the book's class, I didn't touch it

testProgIModified.cpp  I edited the above file so that it would test the copy constructor that I needed to define in queueAsArray.h


Now, as far as I can tell, testProgIModified.cpp fails to compile because of one error on line 36

the error on line 36, I think, is caused by an error on line 198 of queueAsArray.h

The compiler tells me:
queueAsArray.h:198: error: passing &#8216;const queueType<int>&#8217; as &#8216;this&#8217; argument of &#8216;void queueType<Type>::deleteQueue() [with Type = int]&#8217; discards qualifiers

testProgFromBook.cpp compiles and runs just fine.  It does not call the constructor in question, but it does include the header file in question--so the problem is not one of syntax.

I am not entirely sure that my constructor is doing its job correctly, but if I could get it to compile I think I would be well on my way to getting it working right.


Thank you very much for anything you can do--I really appreciate it!

---

### Post by Zugzwang on 2008-04-06
> **Xnyper said:**
>  ...  the only part that I didn't understand is the first line, which read:
```
delete [] list;
```
This line does not seem to be causing my problem (outlined below) but I thought I would mention it so that when you see my comments that say "I don't really understand this line" you will see why it is there.  I'd love to understand why it is in there, but that is secondary to my need to finish this program.

The queueType is derived from queueADT (for which you didn't provide an implementation in the file attached to your post). Whenever you create and instance of queueType then the first thing your constructor for queueType does is to call a constructor for  queueADT. And i guess that the list is allocated there but the copy-constructor of the stack allocates the list by itself, so the first thing it does is to free the list. However, doing it this way is not pretty clean, but ok. But this is just a guess. You can use the "valgrind" tool on Linux to check if you are using free/new as needed.


I'll just give you some hint on the rest since it's your homework. ;-)

> **Xnyper said:**
> 
Now, as far as I can tell, testProgIModified.cpp fails to compile because of one error on line 36

the error on line 36, I think, is caused by an error on line 198 of queueAsArray.h

The compiler tells me:
queueAsArray.h:198: error: passing &#8216;const queueType<int>&#8217; as &#8216;this&#8217; argument of &#8216;void queueType<Type>::deleteQueue() [with Type = int]&#8217; discards qualifiers

testProgFromBook.cpp compiles and runs just fine.  It does not call the constructor in question, but it does include the header file in question--so the problem is not one of syntax.


Ok, it is what it is (see [this  comic for details]("http://www.dilbert.com/comics/dilbert/archive/dilbert-20080330.html")). Now, seriously, you try to copy the queue by removing its elements one-by-one. But this would alter the queue you give to the copy constructor, so it doesn't *copy* anymore. You mustn't alter the queue here and instead iterate over its elements and copy it one-by-one or so. The reason that you get this error only when you're actually trying to use the copy constructor is that you're programming a template and it's only really "compiled" when used.

---

### Post by Xnyper on 2008-04-06
I'm at work, so i can't get too far into this, but I'm going to take a careful look when I get home.  BTW I really appreciate the help.

about the implimentation file, its code is included in the header file.  I know it's bad practice, and I prefer it the other way, but thats how the files were given to me, and my teacher freaks out if I don't submit *exactly* the files she expected

So your saying that when I work my way through the list--in the copy constructor--I'm modifying the original (which was declared const) and thats the problem?  Like... do I need to come up with a new way to run through the queue?  Any suggestions? [I know its my hw... and I'm sorry if it seems like I'm trying to get it done for me, but the due time (midnight) approaches and I'm kind of freaking out].

---

### Post by Zugzwang on 2008-04-06
> **Xnyper said:**
> I'm at work, so i can't get too far into this, but I'm going to take a careful look when I get home.  BTW I really appreciate the help.

about the implimentation file, its code is included in the header file.  I know it's bad practice, and I prefer it the other way, but thats how the files were given to me, and my teacher freaks out if I don't submit *exactly* the files she expected

Oh, sorry, I missed the point that the methods in queueADT.h are virtual and abstract. Ok, so forget about the called constructors then. But then starting the copy constructor with "delete[] list" is definitely wrong if I see it correctly.

> **Xnyper said:**
> 
So your saying that when I work my way through the list--in the copy constructor--I'm modifying the original (which was declared const) and thats the problem?  Like... do I need to come up with a new way to run through the queue?  Any suggestions? [I know its my hw... and I'm sorry if it seems like I'm trying to get it done for me, but the due time (midnight) approaches and I'm kind of freaking out].

Here's a hint. Make a complete program out of it and don't forget to allocate the list accordingly.
```

    int copyPtr = other.queueFront;
    while(copyPtr != other.queueRear)				
    {
	addQueue(other.list[copyPtr]);					
	copyPtr = (copyPtr + 1) % maxQueueSize;								
    }
    addQueue(other.list[copyPtr]);

```

---

### Post by dwhitney67 on 2008-04-06
The first statement in the copy-constructor method, the "delete []list" is not necessary.  The author of your book probably made a typo, or thought that the statement would be necessary to clean-up an object before potentially introducing a memory leak.

One should assume that a virgin object has not yet had any memory allocated to it, thus the clean-up in the copy-constructor is not necessary.  And since a constructor (or copy-constructor) is only called _once per object_, this adds further weight to this argument.

An easier way to test the copy-constructor would be to do something like:
[PHP]queueType< int > q1;
...
queueType< int > q2( q1 );[/PHP]

Concerning the code posted by Zugzwang, heed the suggestion, paying careful attention to copy all attributes of the source-object to the new (destination) object, and allocating the queue of the new object, _before_ attempting to copy the elements from the source.

---

### Post by dwhitney67 on 2008-04-06
> **Xnyper said:**
> about the implimentation file, its code is included in the header file.  I know it's bad practice, and I prefer it the other way, but thats how the files were given to me, and my teacher freaks out if I don't submit *exactly* the files she expected

When dealing with template-objects, the implementation code "must" be included in the same file as the template definition.  I placed the word 'must' in quotes because I have not dealt with every compiler that exists to man!

This being said, you have two choices... continue with your approach, or alternatively place the implementation in a separate file, and then '#include' it into the header file.

For example, for queueAsArray.h:
[PHP]#ifndef H_QueueAsArray
#define H_QueueAsArray
...
template <class Type>
class queueType : public queueADT<Type>
{
...
};

#include "queueAsArrayImpl.cpp"   // implementation file for template

#endif [/PHP]

This practice shown above is quite common, and keeps things "clean".  However, I can't predict what your professor will say, much less whether he/she will embrace this style.

---

### Post by Xnyper on 2008-04-06
You guys are awesome.  I was looking over my code on break and scribbled some pseudocode that looks remarkably simmlar to Zugzwang's hint, how fortuitous.  If I hit any snags I may post again, but even though I'm a few miles away from the assignment, it's looking clearer now than it ever has.

Thanks for clearing up that delete [] mess too... I think i get it.


----arrived home

GOT IT!

I ended up copying everything member-wise, like I had earlier, and then re-vamped my iteration routine.  I kept ending up with: 
"5 9 16 4 2 0 0 0 0 0" instead of
"5 9 16 4 2"

I continued to work on my iteration algorithm, I seriously came up with five ways to do it, but to no avail.  Then I realized that I needed to reset count to zero, not other.count, and blamo--perfect results.  Thanks again, you guys are awesome.

---

