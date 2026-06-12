---
title: "[SOLVED] Pointers in Python?"
date: 2008-08-20
forum: Programming Talk
---

### Post by Zeotronic on 2008-08-20
Recently I've been trying to learn Python using the documents at [http://docs.python.org/]("http://docs.python.org/") (which is what I *should* be using right?). Presently I'm trying to figure out how to make pointers (like can be found in C++)... or if they even exist in Python. I'd figure they do, but I'm having trouble figuring out how to make them. I suspect that its something thats either right under my nose (in the documentation) or something I've forgotten from the tutorial. I know I saw them mentioned once in the tutorial, but I cant see anything that appears to be related anywhere else on that page (or, probably due to my poor searching abilities, anywhere else in the documents). **How could I make a pointer, or what would be my alternative?**

---

### Post by CptPicard on 2008-08-20
I don't understand what you need a pointer for? Everything is by reference in Python already.

(No, they're not there unless in the C-interfacing stuff for specific reasons)

---

### Post by pmasiar on 2008-08-20
IMHO you are trying to learn how to program C++ using Python syntax. :-) Bad idea.

Try to understand how Python is different from C++ (like references instead of pointers), and how to use native Pythonic approach to solve problems.

---

### Post by Zeotronic on 2008-08-20
> I don't understand what you need a pointer for?
I'm trying to figure out how to store 3D model information. I figure it in my best interests to have the various polygon faces able to use the same vertecies rather than having duplicate vertex data. I would also like the vertecies to be able to refrence their 'master' bones without using duplicate data.

I could sware I had some more difficult needs related to them, but nothing is occurring to me at the moment.

> IMHO you are trying to learn how to program C++ using Python syntax.
Not exactly...

---

### Post by CptPicard on 2008-08-20
```

x = Vertex(0,0,0)
y = x

```

Now x and y point to same Vertex and thus share the vertex data...

---

### Post by nvteighen on 2008-08-20
In a C-ish way, let's say in Python everything is a pointer (passed by reference, is the technical term). :)

To check if an object is the same as another (the same instance), use the 'is' operator, not '=='. ('is' is like comparing pointers and '==' like comparing the values of the dereferenced pointers).

Yes, it was confusing for me too at the beginning... but it's nice.

---

### Post by pmasiar on 2008-08-20
did you considered any 3D graphics module (which would be a wrapper to C library)?

Disclaimer: I don;t do 3D graphics in Python but IIRC some people around do.

---

### Post by days_of_ruin on 2008-08-20
> **pmasiar said:**
> did you considered any 3D graphics module (which would be a wrapper to C library)?

Disclaimer: I don;t do 3D graphics in Python but IIRC some people around do.

+1.The Original Poster should use pyOpenGl.

---

### Post by Zeotronic on 2008-08-20
> Now x and y point to same Vertex and thus share the vertex data... 
I had considered that when you guys started questioning why I would need a pointer, but my test of it (and being that I'm not quite sure what your 'vertex' is this is hardly conclusive):
```
joust=9
biscut=joust
print joust
print biscut
joust=11
print joust
print biscut
```
Yeilded...
> 9
9
11
9
What was that supposed to be a class or something?
> ('is' is like comparing pointers and '==' like comparing the values of the dereferenced pointers)
I had been confused as to the significance of 'is' being separate from '=='... I was wondering if thats what it was (at least after the start of this thread).
> did you considered any 3D graphics module (which would be a wrapper to C library)?
I considered many of them, but ultimately decided against them. I would have went with python-OGRE, but it seems to me there were some problems with using it that I cant quite recall at the moment. Regardless I decided this was a great opportunity to learn.
> +1.The Original Poster should use pyOpenGl.
I am using pyOpenGL... do you mean to say that unlike OpenGL, pyOpenGL has it's own means of storing 3D models with complicated bone/vertex interaction? I haven't really gotten to study pyOpenGL yet so I'm not sure what the differences or the Syntax is.

---

### Post by WW on 2008-08-20
Expanding on CptPicard's post...

The **id** function gives the "identity" of an object, which is effectively the object's memory address, so you can use it to verify what CptPicard said.  For example:
```

>>> p = [1.0,2.5,3.8]
>>> q = p
>>> id(p)
454904
>>> id(q)
454904

```
p and q both refer to the same object.  Assigning a new value to p changes the object to which p refers (but does not change the object to which q refers):
```

>>> p = [-1.0,-2.0,-4.0]
>>> id(p)
8195168
>>> id(q)
454904
>>> q
[1.0, 2.5, 3.7999999999999998]
>>> 

```
By the way, I agree with the gist of the other posters comments: learn how Python variables work; don't try to recreate C/C++.

---

### Post by pmasiar on 2008-08-20
> **Zeotronic said:**
> 
```
joust=9
biscut=joust
joust=11

```


Assignment in Python binds name on left to object in right. Nothing more and nothing less.

joust=11 rebinds to 11, but biscuit stays as it was bound to 9. Try this with objects (any dict will do) and you will see.

Also consider difference between mutable and immutable objects. Numbers constants are immutable :-)

---

### Post by Zeotronic on 2008-08-20
> By the way, I agree with the gist of the other posters comments: learn how Python variables work; don't try to recreate C/C++. 
Now I feel I must go onto the offensive, so with all due respect: *I **am** trying to figure out how Python works.* I just have nothing to go on (relative to programming) besides my knowledge of C++. So by stating this without giving me a source to learn it you are being *less than helpful.* (specifically: frustrating)

---

### Post by WW on 2008-08-20
> **Zeotronic said:**
> Now I feel I must go onto the offensive, so with all due respect: *I **am** trying to figure out how Python works.* I just have nothing to go on (relative to programming) besides my knowledge of C++. So by stating this without giving me a source to learn it you are being *less than helpful.* (specifically: frustrating)
You know, when I wrote that I thought "I hope this doesn't sound harsh...", especially since "learning how Python variables work" is exactly what you are doing in this thread! :)  So, *mea culpa*.

---

### Post by CptPicard on 2008-08-20
> **WW said:**
> Assigning a new value to p changes the object to which p refers (but does not change the object to which q refers)

:-k live and learn... this would have bit me sometime, bad. +1

---

### Post by Zeotronic on 2008-08-20
> Try this with objects (any dict will do) and you will see.
I just did a test and it worked the way its 'supposed to'. It still seems kind of weird, but I think I'm starting to get it.

---

### Post by pmasiar on 2008-08-20
> **Zeotronic said:**
> I just did a test and it worked the way its 'supposed to'. It still seems kind of weird, but I think I'm starting to get it.

Because you do not 'assign to' immutable object. System will create another instance of immutable object with different value (strings, tuples).

Name X is bound to object A, then rebound to another object B. Why would different name Y bound to A care what happened to X?

---

### Post by CptPicard on 2008-08-20
> **Zeotronic said:**
> I just did a test and it worked the way its 'supposed to'. It still seems kind of weird, but I think I'm starting to get it.

Pass by value vs. pass by reference is a pretty broad fundamental concept, and essentially in all high-level languages you're passing by reference *by default* (that is, in even more high-level terms, you have "bindings").

The value itself on the stack is rare, but if you get to pure-functional languages, you may need to re-acquaintance yourself to the concept as by definition you will not be able to effect side-effects through the "implicit pointer" you are handling everything through.

So yeah, you really are trying to recreate C/C++ in Python. It's just a recognition of a mindset/assumption issue from your part, not an insult.

---

### Post by muffluphagus on 2008-09-16
Hi I know this thread is listed as solved, but i had a (semi)pertinent question.
 I was wondering if ever I would need to dereference a pointer in python, and if so how i would do it.
it seems as easy as x = CLASS_INSTANCE()
                    x = None
would that accomplish anything?
For example if CLASS_INSTANCE was a particularly large object, of which there were many, would I improve the performance/resource requirements of my code through the above assignment of the variable to 'None'?
thanks alot for your time

---

### Post by fifth on 2008-09-16
Some more knowledgeable in Python than me i'm sure will properly answer, but imo you should concentrate more on your program structure and allow the object to be collected when its out of scope. Then you will have less need to worry about dereferencing objects.

---

### Post by CptPicard on 2008-09-16
> **muffluphagus said:**
> 
 I was wondering if ever I would need to dereference a pointer in python, and if so how i would do it.

You're using the term "dereference" wrong... to dereference is essentially to do "*p" in c terms to a pointer p.

> 
For example if CLASS_INSTANCE was a particularly large object, of which there were many, would I improve the performance/resource requirements of my code through the above assignment of the variable to 'None'?
thanks alot for your time

Usually you can just leave it to the gc. If you have huge objects hanging around you aren't using and need to do this None trick, then there's something wrong with your design...

---

### Post by pp. on 2008-09-16
> **CptPicard said:**
> Usually you can just leave it to the gc. If you have huge objects hanging around you aren't using and need to do this None trick, then there's something wrong with your design...

There are some kinds of programs which keep on creating new objects within ever-growing structures (linked lists or collections). Unless you prune or otherwise clean those growing structures, you will - at some time - have gobbled all of your memory. 

Hence, releasing memory by ceasing to refer to objects which are no longer needed can indeed become necessary. 

Once an object is no longer referred to, you mostly leave things to te garbage collector as you suggested.

However, there are structures where all references are present in two directions (i.e. A refers to B and B refers to A). That kind of structure might need a bit help in getting rid of objects that are no longer useful.

That's presumably one of the reasons why Python provides object destructors.

---

### Post by CptPicard on 2008-09-16
> **pp. said:**
> There are some kinds of programs which keep on creating new objects within ever-growing structures (linked lists or collections). Unless you prune or otherwise clean those growing structures, you will - at some time - have gobbled all of your memory. 

Hence, releasing memory by ceasing to refer to objects which are no longer needed can indeed become necessary. 

IMO what you're talking about is just normal, correct operation of a program/data structure, not the kind of explicit "nulling" of references the question was about :)

> 
However, there are structures where all references are present in two directions (i.e. A refers to B and B refers to A). That kind of structure might need a bit help in getting rid of objects that are no longer useful.

Yes, a naive reference-counting gc can have issues with circular structures... but I recall this has been resolved in modern implementations of Python?

---

### Post by Denestria on 2008-09-16
I only just started reading it myself so I don't know if it's in depth enough for you, but have tried [Byte of Python?]("http://www.swaroopch.com/notes/Python")

---

### Post by starfyredragon on 2010-06-17
As a note, I'm trying to figure out how to do pointers in python as well. However, for me, it's for a very specific reason, and that is large file support. I need to point to a portion of a file without opening the whole thing, because opening the whole thing (working with file sizes that can come near half a terabyte) would crash the system. I want to use python, but I need to access direct memory addresses, and I can't see a way to do that in python yet, being without pointers.

---

### Post by StephenF on 2010-06-17
> **starfyredragon said:**
> As a note, I'm trying to figure out how to do pointers in python as well. However, for me, it's for a very specific reason, and that is large file support. I need to point to a portion of a file without opening the whole thing, because opening the whole thing (working with file sizes that can come near half a terabyte) would crash the system. I want to use python, but I need to access direct memory addresses, and I can't see a way to do that in python yet, being without pointers.
Why not try before assuming it won't work.

Also: import mmap and was it really necessary to dredge up a two year old thread?

---

### Post by schauerlich on 2010-06-18
Python doesn't read the entire file when you open it, it just makes a file object which refers to a file on disk. you have to explicitly read in the data, and you can specify how many bytes at a time it comes in.

[http://docs.python.org/library/stdtypes.html#file-objects](http://docs.python.org/library/stdtypes.html#file-objects)

---

