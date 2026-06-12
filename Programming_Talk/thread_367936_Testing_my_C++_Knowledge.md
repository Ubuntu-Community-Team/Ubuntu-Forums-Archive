---
title: "Testing my C++ Knowledge"
date: 2007-02-22
forum: Programming Talk
---

### Post by rekahsoft on 2007-02-22
Hi all, i have been learning C++ for some time and am about to start learning about template programming but i am not sure that i am totally ready. So i decided i would come to the forums and ask if somebody would give me a very small task that i can complete with my knowledge...the   task should make sure i have a concrete understanding of object oriented programming in C++, and know the main part of the standard library. Thanks for the help and input :D

---

### Post by hod139 on 2007-02-22
> **rekahsoft said:**
> Hi all, i have been learning C++ for some time and am about to start learning about template programming but i am not sure that i am totally ready. So i decided i would come to the forums and ask if somebody would give me a very small task that i can complete with my knowledge...the   task should make sure i have a concrete understanding of object oriented programming in C++, and know the main part of the standard library. Thanks for the help and input :D

There are many cases when Object-Oriented design and generic program conflict.  For example, think of many of the STL functions on containers.  You don't do containter.foo(), it's usually a global function that takes the containter, like foo(container).

For a good first example, you could write a linked list class that uses a generic type for the nodes data.

---

### Post by rekahsoft on 2007-02-22
ok...i am just looking for a simple exercise to do that will test my knowledge of the C++ standard lib and design in C++.

---

### Post by rekahsoft on 2007-02-22
Now back to what i would like: I would like an exercise that will test my knowledge of the C++ standard lib and C++ design.

---

### Post by Tenicus on 2007-02-22
I am on Ubuntu 6.10
It says so next to my name actually.

That is fine.

---

### Post by Wybiral on 2007-02-22
I agree with hod139, a linked list is a good start... It will make sure you understand pointers and generally recursion (although they can be done without).

A binary tree might even be a good task to see how well you understand pointers/recursion/dynamic memory/classes.

And... Since you mentioned templates, once you implement the linked list/binary tree you can use templates to make it a generic linked list or binary tree.

These kinds of abstract data are really good task's for someone looking to ensure their knowledge of C++ and they are a great excuse to bring templates into it.

My vote, linked list, or if you want a little challenge where you almost have to use recursion... Binary tree.

Make a nice class to handle either of these... Then templatize it.

---

### Post by rekahsoft on 2007-02-22
What do you mean by "Binary Tree"...i have never heard this before.

---

### Post by Wybiral on 2007-02-22
It's an abstract data type... They're a pretty effective way to create an organized structure to store and lookup things with. It's basically a linked list, but every node has two children (you can see how this creates a "tree" starting at the "root" node)

Usually you start with a structure like this...
```

struct BTNode
{
   int key;
   BTNode* min;
   BTNode* max;
}

```

When you insert a value into the tree, you start at the root... If the root is empty, place that value there. If the root is not empty... Check to see if the value is greater than the key in the root, if so... Move on to the max node, otherwise move to the min... You keep doing this until you get to an empty node (thus the labels min and max... Some might use low/high or even left/right)

You should do some research...

[http://en.wikipedia.org/wiki/Binary_tree](http://en.wikipedia.org/wiki/Binary_tree)

Linked list's are also a pretty common ADT that you learn for C/C++

Naturally, you can use the STL containers, but sometimes you'll want to implement your own. They'll especially good for practicing things like: pointers, structures, classes, recursion... And later, instead of using "int" for the key's... You can templatize it to accommodate other data types.

---

### Post by hod139 on 2007-02-23
> **Wybiral said:**
> 
Usually you start with a structure like this...
```

struct BTNode
{
   int key;
   BTNode* min;
   BTNode* max;
}

```
Wybiral, I've never seen the children in a tree referred to as min and max before.  I usually see them called left and right respectively.  I understand why you chose those names, but I think the convention is left/right.  Also, calling the data field "key" might be a poor name, since key mean something else, like in a hash table.  Just calling it data or element is clearer.

Aside, in a Binary Tree the element (what Wybiral called key) must be comparable (i.e. you can use the < operator on it).  As Wybiral mentioned, you can generify this struct as (I'm going to use my left/right names for the pointers and element for the data since that is what I am used to):
```

template <typename Comparable>
struct BinaryNode
{
   Comparable element;
   BinaryNode* left;
   BinaryNode* right;
}

```Note, calling the generic type Comparable doesn't mean C++ will enforce anything; the name is only to supply meaning to the programmer.  Future versions of C++ will eventually support this type of checking through so called "concept checking" (Boost has a preliminary version), which will allow you to assign high level properties such as comparable to the generic types.

---

### Post by Wybiral on 2007-02-23
> **hod139 said:**
> Wybiral, I've never seen the children in a tree referred to as min and max before.  I usually see them called left and right respectively.  I understand why you chose those names, but I think the convention is left/right.  Also, calling the data field "key" might be a poor name, since key mean something else, like in a hash table.  Just calling it data or element is clearer.

Aside, in a Binary Tree the element (what Wybiral called key) must be comparable (i.e. you can use the < operator on it).  As Wybiral mentioned, you can generify this struct as (I'm going to use my left/right names for the pointers and element for the data since that is what I am used to):


The min/max are just what I use (high/low makes more sense IMO... I don't know why I usually use min/max). Usually I see the value as either key/value/data.

But, these aren't really important... The concept is important.

Then, once you make a binary tree, try to make an evenly distributed binary tree (a "balanced" tree) where you rearrange the nodes so that each branch is of equal length. This makes operations quicker since unbalanced trees can develop in unwanted formations (like a straight line of nodes, essentially a linked list which defeats the purpose of using a binary tree)

Say your tree develops like this:
[code]
__2______
___3_____
____5____
__4__7___
____6_8__
[code]
(the 4 is on the left of the 5 btw)

Which begins to look more like a linked list if that trend keeps occurring. It happened because we added the "2" first (which means that everything other than 1 will go on the right side)
But you can write a balancing function to rearrange it to look like this:

[code]
____5____
__3___7__
_2_4_6_8_
_________
_________
[code]

---

### Post by g3k0 on 2007-02-23
ugh I hate BSTs.  If you really want to shoot yourself do an optimal binary search tree with frequencies

---

### Post by rekahsoft on 2007-02-23
ok...i need an exercise that does not require the knowledge of template programming...before i move onto reading and learning about it inmy book i want to make sure i know the previous material.

---

### Post by rekahsoft on 2007-02-23
> **g3k0 said:**
> ugh I hate BSTs.  If you really want to shoot yourself do an optimal binary search tree with frequencies

I don't want to shoot my self ;) and i need a exercise that won't take me a very long time to complete...something short and sweet so i can move onto more learning :D

---

### Post by Wybiral on 2007-02-23
A simple linked list or binary tree class is very easy (no foot shooting involved) and shouldn't take too long to type out. Also... You don't HAVE to use templates, you can use integers or something for the data. The point was that you can extend them with templates so accommodate other data types, but this is AFTER you understand them without templates.

However... Templates are actually very simple, consider this:

```

#include <iostream>
#include <string>

using namespace std;

template <typename T>
T doubleMe(T input)
{
   return input + input;
}

int main()
{
   int intValue = 5;
   float fltValue = 10.234;
   string strValue = "Ha ";

   cout << doubleMe(intValue) << endl;
   cout << doubleMe(fltValue) << endl;
   cout << doubleMe(strValue) << endl;
}

```

The function "doubleMe" takes any type that can use the "+" operator and returns "input + input" as the type of "input" (T represents any type of data)

That's really all templates do... Nothing complex really, they are just a placeholder for some data type allowing for functions/classes to use compile-time decided data types.

---

### Post by rekahsoft on 2007-02-23
I will start learning template programming tonight then :D

---

### Post by RedSquirrel on 2007-02-24
> **rekahsoft said:**
> Hi all, i have been learning C++ for some time and am about to start learning about template programming but i am not sure that i am totally ready. So i decided i would come to the forums and ask if somebody would give me a very small task that i can complete with my knowledge...the   task should make sure i have a concrete understanding of object oriented programming in C++, and know the main part of the standard library. Thanks for the help and input :D

Just some thoughts off the top of my head...

Data structures in general are a good start. Linked lists, trees, and so on. Knowing how to write statements (and classes) in C++ is one thing, but you'll find out pretty quickly if you know what you're doing once you start to design & code your own data structures. Translating a design in pseudo-code and diagrams to C++ is sometimes (often?) nontrivial.

And it wouldn't hurt if you learned (at some point) how to decide which data structure is best for a given set of circumstances.

When I was first learning C++, we had three very short assignments: a linked-list using an array, then a circular linked-list using an array, then a linked-list using pointers. Later, we did doubly-linked lists and on and on and on...

---

### Post by wedge2k on 2007-04-10
I've been messing with templates as well in school projects.  However, i havnt been able to compile any program that uses templates.  I get:

```
undefined reference to `my template statement`
```

I get that error for any type of template code i write.  This one happens to be a template function.  I've also had the problem with templated classes.  I have all the g++ standard libraries installed.  Any thoughts? Thanks

---

### Post by WW on 2007-04-10
It might be better to start a new thread. Also, include the code in your post.

---

### Post by slavik on 2007-04-10
create a class person
create a class student that inherits from person and has some additional field, like classes taken or school
create a class teacher that inherits from person that adds years teaching and classes taught

stick a bunch of teachers and students into 1 'collection' (array, list, etc) and sort them by various things. :)

make sure to have a toString() method in all of them that prints all their info in some kind of formatting ...

---

