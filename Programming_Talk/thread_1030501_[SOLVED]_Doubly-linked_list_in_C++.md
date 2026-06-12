---
title: "[SOLVED] Doubly-linked list in C++"
date: 2009-01-04
forum: Programming Talk
---

### Post by Zorgoth on 2009-01-04
I am teaching myself programming and am trying to implement a class of doubly-linked list of integers.  I know what the structure is, but actually programming it is quite annoyingly difficult.

My first idea is to create a class of nodes containing an integer and the two relevant pointers.  First, can a class contain a pointer to the same kind of object?  Second, how do you write a destructor for the list when the nodes are made like this?  And third, does this make any sense or is there a better way to do it?

The basic idea looks like this:

```

class intnode
	{
	public:
	//Loads of functions
	private:
	int data;
	intnode * forward;
	intnode * backward; //Are these pointers kosher?
	};
class doublelist
	{
	public:
	//More functions
	private:
	intnode firstnode; //The first node in the list
	intnode currentnode; //The node we are currently accessing
	};

```

---

### Post by nvteighen on 2009-01-04
Ok, I'll repeat the topic: if you are a programming beginner, C++ is a bad choice as it is a fairly complicated language... you'll be much better using Python.

But, it's also true that Python already has lists built-in, so if you're interested on implementing them, maybe using C instead of C++ might be simpler: you wouldn't be troubled using OOP, but just using a data structure (struct)... Well, you also can do that in C++, but it would be plain C anyway :)

Anyway, the pointers are correct, IMO.

---

### Post by hundredwatt on 2009-01-04
IMO, C++ is a great language to start out with. I found that learning all the formalities of and low-level details in C++ gave me a great introduction to programming and made picking up other languages much easier.

First off all, I would change your class intnode to struct intnode:
```
struct intnode {
    int data;
    intnode *forward;
    intnode *backward;
};
```

I believe that most compiliers treat structs the same as classes. However, by convention, people use structs when they only want them to contain data and no functions, which is what I would recommend here. Put all your functions in the doublelist class.

As for your class, your private values need to be pointers (ie intnode * firstnode). I would also add an intnode * lastnode, but it would be possibly to go without this.

As far as a destructor that deletes the entire list try something like this:
```
intnode *first = <Class object>.firstnode;
intnode *current;
intnode *temp;
do {
  temp = new intnode; //make a copy of 
  *temp = *current; //current in temp

  delete current; //delete the node current
  current = *temp.forward; //assign current to be the next node
  delete temp; //clears the temp variable
} while(*current.forward != NULL);
delete current; //Deletes the last element
```

I didn't actually try this code, so it may not work, but the idea is their. Feel free to PM me with any other questions.

---

### Post by Martin Witte on 2009-01-04
> **hundredwatt said:**
> 
I believe that most compiliers treat structs the same as classes. However, by convention, people use structs when they only want them to contain data and no functions, which is what I would recommend here.
The [difference]("http://en.wikipedia.org/wiki/C%2B%2B_structures_and_classes#Differences_between_structures_and_classes") between structs and classes is that in structs all members are public by default, in classes members are private by default

---

### Post by dwhitney67 on 2009-01-04
That destructor could be made easier.  See below...

Here's an example where the struct Node is declared outside the LinkedList class:
[php]
#ifndef LINKED_LIST_H
#define LINKED_LIST_H

struct Node
{
  Node(int val)
    : value(val),
      next(0),
      prev(0)
  {
  }

  int   value;
  Node* next;
  Node* prev;
};

class LinkedList
{
  public:
    LinkedList()
      : m_head(0)
    {
    }

    ~LinkedList()
    {
      while (m_head != 0)
      {
        Node* next = m_head->next;
        delete m_head;
        m_head = next;
      }
    }

    void insert(Node* node)
    {
      if (m_head == 0)
      {
        m_head = node;
      }
      else
      {
        // this is left as an exercise for the OP
      }
    }

  private:
    Node* m_head;
};

#endif
[/php]

---

### Post by kjohansen on 2009-01-04
this is fine as an exercise, but if you are actually going to use a doubly linked list you will probably be best suited to use the list in the STL.

---

### Post by dwhitney67 on 2009-01-04
> **kjohansen said:**
> this is fine as an exercise, but if you are actually going to use a doubly linked list you will probably be best suited to use the list in the STL.

The use of a home-made linked list is not always relegated to classroom exercises.  There are cases in the real-world where one must use something other than an STL container.

Read more about it here... [Embedded-C++]("http://www.caravan.net/ec2plus/rationale.html")

Note that template object are not permitted with Embedded-C++; it adds to code-bloat which is not desirable in certain embedded systems.

Btw, here is an example embedded system that utilized Embedded-C++ on a RAD (radiation hardened) PowerPC 750:  [AEHF Satellite]("http://www.lockheedmartin.com/products/AdvancedExtremelyHighFrequencyEHF/index.html")

---

### Post by efexD on 2009-01-04
> **nvteighen said:**
> Ok, I'll repeat the topic: if you are a programming beginner, C++ is a bad choice as it is a fairly complicated language... you'll be much better using Python.

But, it's also true that Python already has lists built-in, so if you're interested on implementing them, maybe using C instead of C++ might be simpler: you wouldn't be troubled using OOP, but just using a data structure (struct)... Well, you also can do that in C++, but it would be plain C anyway :)

Anyway, the pointers are correct, IMO.

Why not? C++ Will teach you more then any other languages or just as much. Theres no point in starting small when you can just start with C++ and have good practices and become good at it. If you catch my drift..

---

### Post by monkeyking on 2009-01-04
He asks a specific programming question in c++, and are told to use python or atleast stl's.

If you got the brains for it, stick with c++.

This will give you a better general background in programming.
Than just being able to call already built routines.

Btw, I wouldn't implement it with classes but with structs.

something like

[PHP]
typedef {
  int data;
  struct iNode* prev;
  struct iNode* next;
}iNode;

iNode* myAlloc(int i){
  iNode *retNode =malloc(sizeof(iNode));
  retNode->data = i;
  retNode->prev=NULL;
  retNode->next=NULL; 
  return retNode;
}

[/PHP]

I havn't checked the code, but it should give you an idea

---

### Post by dwhitney67 on 2009-01-04
> **monkeyking said:**
> ...

Btw, I wouldn't implement it with classes but with structs.

...
Huh??  You propose that the OP use C++, then you turn around and indicate that he/she implement a non-OO solution.  :confused:

Btw, the only difference between a class and a struct, besides the spelling, is that with the latter, all declarations (whether member data or methods) are by default publicly accessible.  With a class they are by default private.

For all intents and purposes, the following are identical:
[php]
struct Foo
{
  Foo(int val) : value(val) {}

  int getValue() const { return value; }

  private:
    int value;
};
[/php]
[php]
class Foo
{
  int value;

  public:
    Foo(int val) : value(val) {}

    int getValue() const { return value; }
};
[/php]

---

### Post by Zorgoth on 2009-01-04
Thanks everyone!  I think I understand these things better now.

---

### Post by nvteighen on 2009-01-05
> **efeXor said:**
> Why not? C++ Will teach you more then any other languages or just as much. Theres no point in starting small when you can just start with C++ and have good practices and become good at it. If you catch my drift..

The reason is because low-level programming puts a lot of "computer controlling" that is not what programming is actually about. Those are just side-effects caused by the fact that you use a computer to simulate something you expressed in some formalized language... high-level languages hide that and just let you express what you want without caring for controlling how the computer parts should work (of course, if you need to, stick with C and C++).

---

