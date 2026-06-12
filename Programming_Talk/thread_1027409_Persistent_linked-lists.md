---
title: "Persistent linked-lists"
date: 2009-01-01
forum: Programming Talk
---

### Post by ProgramErgoSum on 2009-01-01
Suppose, I read a file and build a simple linear, one-way linked list. How do I let the built linked-list remain as is after the building is done so that other programs are able to access it ?

[LIST=1]
[*]I have heard of [Serialization in Java]("http://java.sun.com/developer/technicalArticles/Programming/serialization/"). Can this be done in C ?
[*]Is this what is termed as client-server technology ? Namely, server giving a 'connection handle(s)' to clients who then use the server resources based on the access available to them, etc.
[/LIST]

I have searched the fora and the Net. It seems, I am not using the right key words as I am not able to find what I am looking for.

---

### Post by dwhitney67 on 2009-01-01
> **ProgramErgoSum said:**
> Suppose, I read a file and build a simple linear, one-way linked list. How do I let the built linked-list remain as is after the building is done so that other programs are able to access it ?

[LIST=1]
[*]I have heard of [Serialization in Java]("http://java.sun.com/developer/technicalArticles/Programming/serialization/"). Can this be done in C ?
[*]Is this what is termed as client-server technology ? Namely, server giving a 'connection handle(s)' to clients who then use the server resources based on the access available to them, etc.
[/LIST]

I have searched the fora and the Net. It seems, I am not using the right key words as I am not able to find what I am looking for.

Serialization is taking data values, and converting them into either ASCII or binary format to store in a file, or conversely as data that can be sent across a port or other transport device (e.g. a queue).

A simple linked list will have a pointer to the 'next' node; this pointer contains an address.  It would *not* be practical to serialize this address since it would not be usable by another application (the address may very well lie outside the program space of application #2).

Wrt client-server systems, this really falls outside the scope of your original question.  Naturally, a server can serialize data and send it to a client (or vice versa), but once again, as stated above, the pointers to a 'next' node in a linked list would not be part of this data.

Anyhow, to summarize, maintaining a persistent (or non-volatile) linked list is quite a challenge, if not impossible.

---

### Post by Tony Flury on 2009-01-01
if all of your processes are on the same machine - then you could use a memory map to share a common piece of memory between those applications.

if you need the data to be persistent over the restart of programs, then you could memory map the data to a permanent file.

However you may well hit all sorts of interesting address/pointer issues.

There may be better ways to do things : 

1) allow your application to expose an API to other processes (using RPC for instance) that allows the other process to use the data without needing to know it is a linked list

2) Develop a set of methods that allows your application to save your linked list in a standard method (i.e. serialisation) that maintains the relationships between the nodes, without actually saving the pointers themselves. and then another set of methods to read that saved data and reconstructs the list.

---

### Post by pmasiar on 2009-01-01
Serialization is **trivial** in Python - just pickle/unpickle the object.

---

### Post by ProgramErgoSum on 2009-01-01
Thanks ! Let me check them in detail in the AM tomorrow.

---

### Post by Cracauer on 2009-01-01
Today's way of making lists or trees persistent is use a XML interface. Easier to sell to your boss.

If you'd ask me to make a C linked list persistent, and the linked list has the same data type in each element, then I'd just write them one by one into a file (you could say I convert the thing to an array, but I never do it in memory).

---

### Post by ProgramErgoSum on 2009-01-12
Here is one way to use serialization in C : [tpl]("http://tpl.sourceforge.net/"). I am not sure (as yet) if it could be used to serialize a linked-list, etc.

---

