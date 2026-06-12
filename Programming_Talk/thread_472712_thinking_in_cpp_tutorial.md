---
title: "thinking in cpp tutorial"
date: 2007-06-13
forum: Programming Talk
---

### Post by mills on 2007-06-13
ok, need a little nudge in the right direction here

i've downloaded the [thinking in c++]("http://mindview.net/Books/TICPP/ThinkingInCPP2e.html") sourcecode and cd'd to the directory and did "make gcc" everything went well (i think) but what do i do now, i was expecting some kind of interactive tutorial  but nothing seems to have happened, iam not sure whats supposed to happen either, am i missing something really obvious

any ideas?

---

### Post by HackingYodel on 2007-06-13
Hi mills,

I just checked it out and think I know what happened.  Bruce Eckel had set up a master makefile that you ran when you ran **make gcc**.  This master was set up so that each subdirectory was dropped into and its makefile ran.

If you check the subdirectories, now, you'll see that the *.cpp files have been compiled for you.  Chapter 3 from ***Thinking in CPP vol. 1 2nd edition*** has a section about **make**, or a quick google for **make** tutorials should clear everything up for you.

Hope that helps!

***edit***
I just noticed that you have a link to the awesome Rute in your sig.  Section 22.4 of that guide is about makefiles.  Yeah, it really does have everything.

---

### Post by mills on 2007-06-13
i tried making it again but this time i noticed errors ( i didnt really check for errors last time)

```
cd C02; make -f gcc.makefile
make[1]: Entering directory `/home/alex/untitled/C02'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/alex/untitled/C02'
cd C03; make -f gcc.makefile
make[1]: Entering directory `/home/alex/untitled/C03'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/alex/untitled/C03'
cd C04; make -f gcc.makefile
make[1]: Entering directory `/home/alex/untitled/C04'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/alex/untitled/C04'
cd C05; make -f gcc.makefile
make[1]: Entering directory `/home/alex/untitled/C05'
g++  -c NestFriend.cpp
NestFriend.cpp:18: error: a class-key must be used when declaring a friend
NestFriend.cpp:18: error: friend declaration does not name a class or function
make[1]: *** [NestFriend.o] Error 1
make[1]: Leaving directory `/home/alex/untitled/C05'
make: *** [gcc] Error 2
```

i looked at line 18 for the friend declaration to see if i could fix it but quickly realized i don't really know what a class or function actually is (surprise surprise) is there a simple fix for this like a ';' or something? or should i just find another tutorial to learn from

```
//: C05:NestFriend.cpp

// From Thinking in C++, 2nd Edition

// Available at http://www.BruceEckel.com

// (c) Bruce Eckel 2000

// Copyright notice in Copyright.txt

// Nested friends

#include <iostream>

#include <cstring> // memset()

using namespace std;

const int sz = 20;



struct Holder {

private:

  int a[sz];

public:

  void initialize();

  struct Pointer;

  **friend Pointer;**

  struct Pointer {

  private:

    Holder* h;

    int* p;

  public:

    void initialize(Holder* h);

    // Move around in the array:

    void next();

    void previous();

    void top();

    void end();

    // Access values:

    int read();

    void set(int i);

  };

};



void Holder::initialize() {

  memset(a, 0, sz * sizeof(int));

}



void Holder::Pointer::initialize(Holder* rv) {

  h = rv;

  p = rv->a;

}



void Holder::Pointer::next() {

  if(p < &(h->a[sz - 1])) p++;

}



void Holder::Pointer::previous() {

  if(p > &(h->a[0])) p--;

}



void Holder::Pointer::top() {

  p = &(h->a[0]);

}



void Holder::Pointer::end() {

  p = &(h->a[sz - 1]);

}



int Holder::Pointer::read() {

  return *p;

}



void Holder::Pointer::set(int i) {

  *p = i;

}



int main() {

  Holder h;

  Holder::Pointer hp, hp2;

  int i;



  h.initialize();

  hp.initialize(&h);

  hp2.initialize(&h);

  for(i = 0; i < sz; i++) {

    hp.set(i);

    hp.next();

  }

  hp.top();

  hp2.end();

  for(i = 0; i < sz; i++) {

    cout << "hp = " << hp.read()

         << ", hp2 = " << hp2.read() << endl;

    hp.next();

    hp2.previous();

  }

} ///:~

```

ok i just looked at the friends bit of code and apparently its incomplete!!!

*// Declaration (incomplete type specification):* Line 8 in code below

why would a tutorial expect a beginner to be able to solve this?

```
//: C05:Friend.cpp

// From Thinking in C++, 2nd Edition

// Available at http://www.BruceEckel.com

// (c) Bruce Eckel 2000

// Copyright notice in Copyright.txt

// Friend allows special access



**// Declaration (incomplete type specification):**

struct X;



struct Y {

  void f(X*);

};



struct X { // Definition

private:

  int i;

public:

  void initialize();

  friend void g(X*, int); // Global friend

  friend void Y::f(X*);  // Struct member friend

  friend struct Z; // Entire struct is a friend

  friend void h();

};



void X::initialize() { 

  i = 0; 

}



void g(X* x, int i) { 

  x->i = i; 

}



void Y::f(X* x) { 

  x->i = 47; 

}



struct Z {

private:

  int j;

public:

  void initialize();

  void g(X* x);

};



void Z::initialize() { 

  j = 99;

}



void Z::g(X* x) { 

  x->i += j; 

}



void h() {

  X x;

  x.i = 100; // Direct data manipulation

}



int main() {

  X x;

  Z z;

  z.g(&x);

} ///:~


```

so iam guessing the question i need to ask now is how do i complete the type specification?

---

### Post by HackingYodel on 2007-06-13
> **mills said:**
> 
i looked at line 18 for the friend declaration to see if i could fix it but quickly realized i don't really know what a class or function actually is (surprise surprise) is there a simple fix for this like a ';' or something? or should i just find another tutorial to learn from

....

so iam guessing the question i need to ask now is how do i complete the type specification?

Not to be rude, but you are getting way ahead of yourself here.

Start at the beginning of the book and work your way up to chapter 5 and the problem.  By the time you get there and understand things like functions, pointers, struct, class, and the rest of the basics, you'll have no problem fixing the code sample.  Broken code often teaches much more than code that "just works".  Relax.  By the time you get to this code in the book, you'll understand why it does what and how to make it your own.

---

### Post by mills on 2007-06-13
but how do i look at chapter 1 if its all broken?

the screenshot shows what's inside the chapter 1 directory, the "gcc make" command doesn't seem to to have made anything, it looks exactly as it did when i first downloaded it. which is why i thought the nestfriend error needed to be fixed b4 i could use the tutorial

did you get any errors relating to friend.cpp or nestfriend.cpp in C05 like i did when you compiled it?

---

### Post by harun on 2007-06-13
> **mills said:**
> but how do i look at chapter 1 if its all broken?


Looking at chapter 1 != building the source.

If you want to read the book:

[http://www.briceg.com/eckel/one/](http://www.briceg.com/eckel/one/)

---

### Post by lesda03 on 2008-04-04
...
    struct Pointer;
   friend struct Pointer; // correct - tells compiler friend is a struct
   //friend Pointer;   // the code actually in online text of TiCppV1 Chpt 5
                            // this results in error: a class-key must be used when  
                                                          declaring a friend
                            // i guess a typo that made it into the book
                            // the compiler just needs to know the type of object 
                            //   you are trying to make friends with
    struct Pointer {
    ...

---

