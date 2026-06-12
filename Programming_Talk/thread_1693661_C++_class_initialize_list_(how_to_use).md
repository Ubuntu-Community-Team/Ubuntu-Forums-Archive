---
title: "C++ class initialize list? (how to use?)"
date: 2011-02-23
forum: Programming Talk
---

### Post by cthulhu_54 on 2011-02-23
Hi!
I have a problem, that I think can be solved by using a initialize list but I don't know how to implement it. 

_What I want to do:_ I have a class (MyClass) that has member functions who need a lot of random numbers. So I want to initialize a random number generator with a seed in the constructor of MyClass, and then have this accessible to all member functions to MyClass.   

Naively, my code for MyClass would look like this:

```
#include "ran.h"     //Random number generator from numerical recipes 3 ed.

class MyClass{
private:
  Ran random(double);       //accessible to all members of MyClass

public:
  MyClass(double seed){
    random(seed);           //initialize the random number generator
  }

  double getRandom(void){
    return random.doub();   //this is how I get a new random number
  }
  
  //+other functions that use "random.doub()" to get random numbers

};
```

The Ran class needs to be initialized with a seed, and I want it to be accessible to all members of MyClass. I've read through the first 2 pages of Google hits for "C++ Initialization lists" but can't get it right. This is my best attempt:


```
class MyClass{
private:
  Ran random(double);

public:
  MyClass(double seed): random(seed){
  }

  double getRandom(void){
    return random.doub();
  }
};

```

But i get this error:
```
nrtest.cpp: In constructor ‘MyClass::MyClass(double)’:
nrtest.cpp:14: error: class ‘MyClass’ does not have any field named ‘random’
nrtest.cpp: In member function ‘double MyClass::getRandom()’:
nrtest.cpp:18: error: ‘((MyClass*)this)->MyClass::random’ does not have class type
```

Any suggestions would be greatly appreciated.

---

### Post by Zugzwang on 2011-02-23
I'm trying to fix your syntax below:

```
#include "ran.h" 

class MyClass{
private:
  [COLOR="Red"]Ran random[/COLOR];       //accessible to all members of MyClass

public:
  [COLOR="Red"]MyClass(double seed) : random(seed)[/COLOR] {
  }

  double getRandom(void){
    return random.doub();   //this is how I get a new random number
  }
  
};
```

For the member element "random", the parameters are not given in the declaration, but during initialization.

---

### Post by cthulhu_54 on 2011-02-23
Ah! Yes, I actually mistyped in the post, what I meant was:
```
#include "ran.h" 

class MyClass{
private:
 [COLOR="Red"] Ran random[/COLOR][COLOR="Lime"](double)[/COLOR];       //accessible to all members of MyClass

public:
  [COLOR="Red"]MyClass(double seed) : random(seed)[/COLOR] {
  }

  double getRandom(void){
    return random.doub();   //this is how I get a new random number
  }
};

```
The included error message is for this version (with Ran random[COLOR="Lime"](double)[/COLOR]).

---

### Post by Zugzwang on 2011-02-23
So leave out the "(double)" in the declaration of the member element "random" and it should be fine, unless "random" is a template, which it probably isn't.

---

### Post by cthulhu_54 on 2011-02-23
AH!
OK, I'm (almost) dyslectic, my last post was pointless, as I misunderstood your reply (and then misread my original post). 

Yes, it compiles fine now, without any errors, a million thanks!

---

### Post by cthulhu_54 on 2011-02-23
It does not show up as "Solved" on the "Programming Talk", even though I put my first post as "SOLVED".

---

