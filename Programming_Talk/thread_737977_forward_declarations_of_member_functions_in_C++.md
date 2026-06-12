---
title: "forward declarations of member functions in C++?"
date: 2008-03-28
forum: Programming Talk
---

### Post by schmendrick on 2008-03-28
hi guys,

i am a bit at loss here. maybe somebody can help me out:
i know that i can make a forward declaration of a class and then use it like:



> 
class A;

class Base
{
friend class A;
public:
	Base();
private:
	int x;
};

class A : public Base
{
	void Foo();		//Foo is using x
}


ok thats cool. But am i also able to make a forward declaration of a class member function?
something like:

> 
class A;
void A::Foo();

class Base
{
friend void A::Foo();
public:
	Base();
private:
	int x;
};

class A : public Base
{
	void Foo();	//Foo is using x
}

which does not compile, i do not know if or how i can make a forward declaration of a member function. 

the reasion i want this:
i have a base class lets call it "Base" and 3 classes derived from Base, lets call them "A", "B" and "C".
i know this sounds somewhat wicked, but is this possible in any way?
but only class "A", and not all member functions of A should be able to access the private members of "Base".

so is it possible to forward declare member functions ? i didnt find anything on the net.

---

### Post by tpg on 2008-03-28
Try this at the top instead

```

class A {
  void Foo();
}

```

although I'm not sure whether or not you can persuade the 'friend' keyword only to apply to a few members of a class and not all of them.

---

### Post by schmendrick on 2008-03-28
yes, you can declare member functions to be friends, allthough it surprises me that most people dont know it. plus it is rarely used.

unfortunately your suggestion cannot work, because i would **define ** A. when the compiler then gets to the real code of class A he will throw the error that the class is redefined. 

> ( error: redefinition of &#8216;class A&#8217; ) 

any other ideas?

---

### Post by tpg on 2008-03-28
OK, typing in your code and trying to compile, the error messages suggest that the Foo() method of class A must be defined before you can apply the friend keyword to it.

I was thinking that maybe putting each class into a separate header file with inclusion guards, and including the other header, might work, but I don't think it will.

I'm not sure if this is going to be possible, is there another way of designing this to avoid the circular problem?

---

### Post by pedro_orange on 2008-03-28
I'm slightly confused as to what you are trying to achieve.

But can you not do this with inheritance? 

```
class Base{
//...
};

class A : public Base{
//...
};

```

A member of a derived class can use public & protected members of its base class as if it were part of it's own class. (But ofc not the base classes private names)
But then to get around that you can write a public fn in Base to allow access to those private members.

---

### Post by schmendrick on 2008-03-31
whoohooow, weekend was nice, back to the problem ^^.
thanks for the comments so far.

> I'm slightly confused as to what you are trying to achieve.

But can you not do this with inheritance?

this is all about inheritance. Base  IS the base class of A,B,C.   


> OK, typing in your code and trying to compile, the error messages suggest that the Foo() method of class A must be defined before you can apply the friend keyword to it.

unfortunately correct.

> 
I was thinking that maybe putting each class into a separate header file with inclusion guards, and including the other header, might work, but I don't think it will.


unfortunately correct again

> 
I'm not sure if this is going to be possible, is there another way of designing this to avoid the circular problem?

i also dont see a way how this is possible. but i also do not see another way how to avoid this problem. plus: i couldnt change the architecture that easy anyway: it is a quite huge project at work that i dont work on alone and i am quite stuck with that architecture. 

Maybe i need to explain the situation:

Base is an abstract class. A,B,C are all classes whose instances can be included in one big tree. the root of this tree is an instance of A. all nodes of this tree are derived from Base.
all 3 (A,B,C) need to be derived from Base because Base provides navigation methods, memory things etc. Base also has a protected member childlist containing pointers to other Base classes. Base provids navigation-methods for navigating to the correct child of a tree-hirarchy.

a normal - examplehirarchy that would be created would have the following instances/would look somewhat like this


A--> B
_--> B ---> C
_____ ---> C
_____ ---> C
_--> B ---> C
_____ ---> C



meaning: a instance of class A has n instances of B in its childlist (in this example 3). 
an instance of B can have n instances of C in its childlist. in this case the second B has 3 instances of C in its childlist, the third B has 2 instances of C in its childlist.

from the APIs point of view, i want the programmer only to be able to invoke some Base's inherited methods if he is invoking it from A, but he must not do so from instances of B or C. 
this is for example very important for locking, because this structure has to be thread-safe. 

i guess i will have to stick to making A friend of base and writing very harsh comments in the doxygen documentation not to use other private members of base that are not designed to be used from A. 
i was just astonished that this is not possible. in C# i could easily do something like that but it really seems that C++ can't cope with this situation.

anybody seeing anything i missed? if not, thanks anyway guys!

---

