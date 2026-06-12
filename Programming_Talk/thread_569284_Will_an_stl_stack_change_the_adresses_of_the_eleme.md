---
title: "Will an stl stack change the adresses of the elements put in it?"
date: 2007-10-06
forum: Programming Talk
---

### Post by Hospadar on 2007-10-06
I'm working on a little c++ project and I have some objects that keep track of others by reference.  But the objects referenced are external, (declared normally and then referenced by pointer as opposed to using "new" to allocate memory) so there's no deep copy or anything.  

I'm wondering if it's safe to reference items in a stack this way, or will the stl stack ever change the adresses of an object once it's in the stack.

If stack isn't the right container for this, would a list work better?

Thanks,
Luke

---

### Post by slavik on 2007-10-06
stack and list work in different ways on the theoretical level.

so you are storing references/pointers in a stack. once memory is allocated the object does not move, unless you move it or it's somehow moved by whatever manages it (an array inside of an object could possibly move when a bigger array is needed).

if you are referencing items INSIDE the stack, it defeats the purpose of the stack (or the list) unless you write your own stack/list.

My question would be: Are you storing references on the stack or are you referencing items in the stack?

Seems to me like you want to peek at items on the stacks (as often done with queues in Operating Systems or event queues)

---

### Post by Hospadar on 2007-10-07
well I'm actually thinking that I'll be using a list, and I do want to reference things inside the list.  It's a little klunky of a solution but it's a project to demonstrate a different point so it's no biggie.  

I'm just wondering now if list will ever change the adress of any of it internals (like a vector would when you grow it) I know in theory lists don't do that but i'm not totally sure if their are no exceptions.

---

### Post by slavik on 2007-10-07
list shouldn't since it's node based, whereas vector is array based.

if you want to access things inside the list, use a list<T>::iterator :)

---

### Post by cwaldbieser on 2007-10-07
> **Hospadar said:**
> well I'm actually thinking that I'll be using a list, and I do want to reference things inside the list.  It's a little klunky of a solution but it's a project to demonstrate a different point so it's no biggie.  

I'm just wondering now if list will ever change the adress of any of it internals (like a vector would when you grow it) I know in theory lists don't do that but i'm not totally sure if their are no exceptions.

An STL list has the following properties:
+ Insertion and splicing do not invalidate iterators to list elements.
+ Deletion invalidates only iterators that point to elements actually deleted.

Note that these guaruntees are for iterators, not pointers.  A list iterator may be implemented as a pointer, but then again, it may not, especially if you are using a debug library.

---

### Post by slavik on 2007-10-07
I think the stl list iterators are reference based.

---

