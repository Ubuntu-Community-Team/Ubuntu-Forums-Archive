---
title: "Overloading operator&lt;&lt; to output based on derived classes"
date: 2011-11-17
forum: Programming Talk
---

### Post by akand074 on 2011-11-17
Hey, I've been having a lot of trouble trying to do this. Basically I want to have something like this:

```

class A {
   //
public:
   ostream& operator<<(ostream& out, const A& a);
};

class B {
   //
public:
   ostream& operator<<(ostream& out, const A& b);
}

class C {
   //
 public:
    ostream& operator<<(ostream& out, const A& c);
}

```and then doing something like this:

```

A obj = B();
A obj2 = C();
std::cout << obj; //prints content of B type class
std::cout << obj2; //prints content of C type class
```I would basically just use a dynamic_cast to down-cast A to the derived class types but the operator functions don't seem to work like normal functions. When I make A's operator<< function virtual, I get a "too many parameters" error, if I make the operator<< function non-virtual (and make all three friend ofcourse) I get a linking error in C saying the operator is already defined in B or something.

Does anyone have any idea what the best way of doing this is? (While still using the << operator).

---

### Post by Blackbug on 2011-11-18
Its an interesting problem and I tried to work on abit to find a solution but couldnt..
then i googled but only some workaround are available
probably you might have read them already
[http://www.velocityreviews.com/forums/t282211-how-to-make-operator-a-virtual-function.html](http://www.velocityreviews.com/forums/t282211-how-to-make-operator-a-virtual-function.html)
 
It cannot be made virtual since its a friend function and for a virtual method it must be class member function..not very sure about how operator overloading should work in this context.
 
I hope will get some fruitful answers here

---

### Post by akand074 on 2011-11-18
> **Blackbug said:**
> Its an interesting problem and I tried to work on abit to find a solution but couldnt..
then i googled but only some workaround are available
probably you might have read them already
[http://www.velocityreviews.com/forums/t282211-how-to-make-operator-a-virtual-function.html](http://www.velocityreviews.com/forums/t282211-how-to-make-operator-a-virtual-function.html)
 
It cannot be made virtual since its a friend function and for a virtual method it must be class member function..not very sure about how operator overloading should work in this context.
 
I hope will get some fruitful answers here

No that actually might be a good idea (from that page). I tried something similar but not quite the same and ran into issues. Basically if I just have a virtual function "write" in the base class and then override it in the derived classes and then have an overloaded << operator only in base and have it call write, write would be called based on the runtime type wouldn't it?

---

### Post by gateway67 on 2011-11-19
> **akand074 said:**
> 
Does anyone have any idea what the best way of doing this is? (While still using the << operator).
In the future, please post real code, not a "something like" attempt at gibberish that is replete with syntax errors galore.  That way, someone like me doesn't have to re-create an entire program to demonstrate a suggestive course of action to resolve your query.

Anyhow, what you need to do is create a helper-function for each class; I would suggest that you declare it as virtual.  As for your overloaded operator << function, these will need to be declared as a 'friend'.

For example:
```

#include <iostream>
using namespace std;

class A {
public:
   friend ostream& operator<<(ostream& out, const A& a) { a.printInfo(out); return out; }
private:
   virtual void printInfo(ostream& out) const { out << "I'm A."; }
};

class B : public A {
public:
   friend ostream& operator<<(ostream& out, const B& b) { b.printInfo(out); return out; }
private:
   virtual void printInfo(ostream& out) const { out << "I'm B."; }
};

class C : public A {
public:
   friend ostream& operator<<(ostream& out, const C& c) { c.printInfo(out); return out; }
private:
   virtual void printInfo(ostream& out) const { out << "I'm C."; }
};

int main()
{
   A* obj  = new B;
   A* obj2 = new C;

   cout << *obj  << endl;
   cout << *obj2 << endl;
}

```

---

