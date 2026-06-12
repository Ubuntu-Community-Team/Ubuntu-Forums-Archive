---
title: "Template Issues C++"
date: 2010-04-01
forum: Programming Talk
---

### Post by StunnerAlpha on 2010-04-01
Ey fellas, I am getting an error message and have spend a good amount of time googling and trying different things but I just can't seem to figure out how to resolve it. This is what I have:
```

template <class T>
stack<T> Stack = new stack<T>();//error given for this line

```
And here is the error I get(right below the assignment line-I am using Xcode):
```

error: template declaration of 'stack<T> Stack'

```
Here is the code for my classes:
```

//stack.h
#ifndef stack_h
#define stack_h

#include <iostream>
#include <list>
#include "stackNode.h"

using namespace std;

template <class T>
class stack{
private:
	list< stackNode<T> > stackList;
public:
	stack();
	void addVar(string var, T val);
	//void print();
}; //class filePos

template <class T>
stack<T>::stack(){
	
}

template <class T>
void stack<T>::addVar(string var, T val){
//	stackNode<T> newStackNode;
//	newStackNode = new stackNode<T>(var, val)
	stackList.push_front(new stackNode<T>(var, val));
}

template <class T>
void stack<T>::print(){
	list<T>::iterator itr;
	itr = stackList.begin();
	for (; itr!=stackList.end(); ++itr)
		cout << " " << *itr;
	cout << endl;

}

#endif

```
```

//stackNode.h
#ifndef stackNode_h
#define stackNode_h

#include <string>

using namespace std;


template <class T>
class stackNode{
private:
	string variable;
	T value;
public:
	stackNode(string var, T val);
	string getVariable();
	T getValue();
	void setValue(T val);
}; //class stackNode

template <class T>
stackNode<T>::stackNode(string var, T val){
	variable = var;
	value = val;
}//stackNode constructor

template <class T>
string stackNode<T>::getVariable(){
	return variable;
}

template <class T>
T stackNode<T>::getValue(){
	return value;
}

template <class T>
void stackNode<T>::setValue(T val){
	value = val;
}//setValue

#endif

```

Any help appreciated. Thanks in advance!

---

### Post by Cracauer on 2010-04-01
It has no way of knowing what type you want for T at that particular time.

ETA: you also put the new()-ish object into a non-pointer place.

---

### Post by StunnerAlpha on 2010-04-01
Wait, so is this even possible? and what do you mean by "you also put the new()-ish object into a non-pointer place."?

---

### Post by Cracauer on 2010-04-01
> **StunnerAlpha said:**
> Wait, so is this even possible? and what do you mean by "you also put the new()-ish object into a non-pointer place."?

I'm not clear on what you are trying to do with that particular statement.

Presumably you need something like 
```

Foo<int> *myfoo = new Foo<int>();
or
Foo<int> myfoo;

```

---

### Post by dwhitney67 on 2010-04-01
StunnerAlpha:

Rather than present your code, could you please present your requirements?

Whereas I believe that using contraptions that contradict the order of the universe may solve what you have presented, perhaps there is a simpleton solution that a brain-dead kid in nursery could solve if you merely state what you are trying to accomplish.

---

### Post by StunnerAlpha on 2010-04-01
> **dwhitney67 said:**
> StunnerAlpha:

Rather than present your code, could you please present your requirements?

Whereas I believe that using contraptions that contradict the order of the universe may solve what you have presented, perhaps there is a simpleton solution that a brain-dead kid in nursery could solve if you merely state what you are trying to accomplish.

Yeah I was building up to present my requirements rather than going into a lengthy description and waste my time if it turns out to be just a stupid syntactical issue. Then my efforts of describing my larger picture turn out to be moot, right? The second comment I posted very briefly before I stepped out so I refrained from going into more depth. I understand on forums like this you get a lot of these types of posts that can fluster you and I understand. Point is, all of us asking for help aren't braindead numbskulls and some of us do have some etiquette even though it may not seem so at first. But thanks for suggesting I post my requirements.

Anyways... back on topic. So I am attempting to implement a "simple" programming language. It is actually not as simple as it sounds as I plan on eventually adding functions and classes and whatnot(very inspired by python). Anyways, as of now it functions as a C++ program which takes in an ordinary text file, parses the data in there(syntax checking and whatnot) and spits out errors for improper syntax.

What I am trying to implement now is the so-called "stack" which holds the variables and their respective values. It may sound stupid to some but I am not very concerned with speed, at least for the time being, and am implementing this stack as a linked list(Stack) for flexibilty. This linked list contains nodes of type stackNode which holds variable names as a sting, and their values(tricky part) of any type. So a value could essentially be an array, or a long, or char, or anything, that's the idea. This is why I am fudging up with the templates syntax.

So that's basically it. If any of you have any work-arounds for how I am implementing it, or even a better way please let me know. And thanks for all your time and help!

---

### Post by Cracauer on 2010-04-01
I don't think you have told us anything about what that global variable is supposed to do.

Are you implementing an interpreter for some language and you want a stack that can hold any of that language objects? Then you instantiate the template with void* or MyLanguageObject*.

But you can't mix compile time generic computing and run-time type dispatch computing with the same containers.

---

### Post by falconindy on 2010-04-01
A vector in this case isn't necessary. Rather, your stack nodes should contain a pointer to the next node in the stack. Then you can code up some methods

```
class StackNode {
  void *data;
  StackNode *next;
};
```
And then you can code up some public methods for push, pop, and top. Methods which modify the stack should return a StackNode which represents the current top of the stack.

---

### Post by falconindy on 2010-04-01
But all this sort of ignores the fact that C++ has a built in stack ADT (shows how much I know/care about C++).

I would have edited, but Chromium has decided that it loathes these forums and segfaults when I click edit.

---

### Post by StunnerAlpha on 2010-04-01
> **Cracauer said:**
> I don't think you have told us anything about what that global variable is supposed to do.

Oh the global variable "Stack"? That is just supposed to be a way for me to access the stack from any of my functions.

> **Cracauer said:**
> 
Are you implementing an interpreter for some language and you want a stack that can hold any of that language objects?

Yep

> **Cracauer said:**
> 
Then you instantiate the template with void* or MyLanguageObject*.


Would it be possible for you to give me an example of this please?

> **Cracauer said:**
> 
But you can't mix compile time generic computing and run-time type dispatch computing with the same containers.

So in other words the class needs to be known before runtime so that the compiler knows how much memory to allocate for an instance of the class?

---

### Post by StunnerAlpha on 2010-04-01
> **falconindy said:**
> A vector in this case isn't necessary. 

Do you mean list?

> **falconindy said:**
> 
Rather, your stack nodes should contain a pointer to the next node in the stack. Then you can code up some methods

```
class StackNode {
  void *data;
  StackNode *next;
};
```
And then you can code up some public methods for push, pop, and top. Methods which modify the stack should return a StackNode which represents the current top of the stack.

Even though its called "Stack" it doesn't mean I want it to resemble a typical stack. I am using the linked list for flexibility's sake. I will modify it later if need be. And all my functions that handle stuff with the linked list are going to be taken care of in the "stack" class, so the calling functions will just call things like addVar(a) and checkIfVarExists(a) and not have to worry about how everything is done. Encapsulation for the win. ;)

---

### Post by Cracauer on 2010-04-01
> **StunnerAlpha said:**
> Would it be possible for you to give me an example of this please?



The self-grown stack probably isn't what you want but anyway.

What you normally do when implementing a simple interpreter is that all objects of all types are held in something like this:

```

struct MyUniversalObject {
  enum type;
  union {
     int incaseiamaninterger;
     float incaseIamafloat;
  };
};

```

Then, to hold these things in a C or C++ data structure you point to it with
struct MyUniversalObject **objects;

or in C++
MyCollectionClass<MyUniversalobject> myglobalstorage.


I'm still no sure what purpose the non-associative stack has in your interpreter, though.

 > **StunnerAlpha said:**
> 

So in other words the class needs to be known before runtime so that the compiler knows how much memory to allocate for an instance of the class?

In C++ the templates are compile-time expansions to types you know you will use. The code will be duplicated at compile time for each type.

In almost all other languages you have the code once and it holds pointers, not objects, and with some kind of type identification (user as in Java or dynamically as in Python).

Of course you can do that in C++, too, if you are willing to make your collection class instance take void* and then cast everything in and out. But C++ isn't GCed either, so ownership will be a headache on top of miscasting.

---

### Post by StunnerAlpha on 2010-04-01
Thanks for the example. I am going to have to refresh myself on= enum and union. So everything within that union block are the different types the variable could possibly be, right?

I need to create this so called "Stack" so that I have a list of variables that I can check/read/write from, so if the user declares A twice I can complain about it. Or if the user is adding A and B to determine C, I can look up their values in the stack.

This make sense? Is there a better way about going about this?

---

### Post by Cracauer on 2010-04-02
> **StunnerAlpha said:**
> Thanks for the example. I am going to have to refresh myself on= enum and union. So everything within that union block are the different types the variable could possibly be, right?



Right, you stuff strings and whatever else in there, too.


> **StunnerAlpha said:**
> 

I need to create this so called "Stack" so that I have a list of variables that I can check/read/write from, so if the user declares A twice I can complain about it. Or if the user is adding A and B to determine C, I can look up their values in the stack.

This make sense? Is there a better way about going about this?

Unless I miss something your stack doesn't actually provide a
key->value relationship, no? In any case, the linear search required
to find things in your stack, whether it has the values or not, will
be prohibitive performance-wise.

Simple interpreters usually use a top-level hashtable to hold symbols, or
multiple hashtables if the language has multiple namespaces.

Actual interpretation will then try to convert a file's source
code so that the location of a variable's name is known throughout the
execution so that you don't actually do hash lookup at runtime. But for a simple enough interpreter brute-forcing it until it becomes a problem would work if the backing is a hashtable that is reasonably collision-free.

---

### Post by StunnerAlpha on 2010-04-02
> **Cracauer said:**
> 
Unless I miss something your stack doesn't actually provide a
key->value relationship, no? 

Actually, I believe it does. The "key" is the variable name stored as a string, and the value is the value of that variable. (See stackNode.h-1st post)
> **Cracauer said:**
> 
In any case, the linear search required
to find things in your stack, whether it has the values or not, will
be prohibitive performance-wise.

Simple interpreters usually use a top-level hashtable to hold symbols, or
multiple hashtables if the language has multiple namespaces.

Actual interpretation will then try to convert a file's source
code so that the location of a variable's name is known throughout the
execution so that you don't actually do hash lookup at runtime. But for a simple enough interpreter brute-forcing it until it becomes a problem would work if the backing is a hashtable that is reasonably collision-free.

Hmm, I may end up implementing it with a hash table but for now I am going to try to get it working with a linked list and see how it goes as the city simulator portion of my project is memory intensive as is and I wouldn't mind sacrificing a bit of speed for memory. But who knows, it may run slower than I envision and will then alter it to a hash table. Thanks for all the help/comments! I am not going to mark this thread as solved just yet as I may be back with some more questions...

---

### Post by StunnerAlpha on 2010-04-18
Ey man, finally back to working on this project. Anyways, this is what I have:
```

struct universalType{
	enum type;
	union{
		int ifInt;
		char ifChar;
	};//union
};

```
And it is giving me an "error: use of enum 'type' without previous declaration" error. Should I change that enum line to:
```

enum type{};

```
? Or was there something else you had in mind?

---

### Post by StunnerAlpha on 2010-04-18
Oh, and another thing... I got caught up in all the restructuring that I removed the template implementation from stack and stackNode. That is not what I should have done huh? I should have merely just created the struct and used that declaration you gave me, right?

---

### Post by StunnerAlpha on 2010-04-19
So I have this bit of code:
```

Stack->addVar(actualLineWOWS.at(wowsPos-1),integer); //ERROR AT THIS LINE

```
```

//stack.h
#ifndef stack_h
#define stack_h

#include <iostream>
#include <list>
#include "stackNode.h"

using namespace std;

template <class T>
class stack{
private:
	list< stackNode<T> > stackList;
public:
	stack();
	void addVar(string var, T val);
}; //class filePos

template <class T>
stack<T>::stack(){
	
}

template <class T>
void stack<T>::addVar(string var, T val){
	stackList.push_front(new stackNode<T>(var, val));
}

```
And I am getting this error:
```

error: no matching function for call to 'stack<universalType>::addVar(std::basic_string<char, std::char_traits<char>, std::allocator<char> >&, int&)'

```
So... what exactly is it that I am doing wrong? I am passing in a string and then an int. I think there may be a problem with universalType. Here is its declaration:
```

struct universalType{
	enum type{};
	union{
		int ifInt;
		char ifChar;
	};//union
};

```
Thanks in advance!

---

### Post by Some Penguin on 2010-04-19
Integers aren't interchangeable with unions.

---

### Post by StunnerAlpha on 2010-04-19
Thanks, fixed the problem by doing this:
```

universalType uT;
uT.ifInt = integer;
Stack->addVar(actualLineWOWS.at(wowsPos-1),uT);

```

---

