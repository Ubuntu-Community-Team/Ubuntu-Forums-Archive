---
title: "C++ Inheritance Question"
date: 2010-05-10
forum: Programming Talk
---

### Post by mjobrien on 2010-05-10
Hi everyone,

First of all, I am fairly new to this forum, so if this question is out of line (since it is not Ubuntu related), I apologize, and just let me know ;o)  My C++ skills are foggy, so I was wondering if anybody would be willing to offer advice in the following situation.  I have 4 classes:  class B extends class A, class beta extends class alpha, and alpha is a member of A, beta is (supposed to be) a member of B.  So, the code I am considering looks like:

```

class alpha{
/* stuff */
}

class beta : public alpha {
/* stuff */
}

class A{
alpha alpha_obj;
/* stuff */
}

class B : public A {
beta beta_obj;
/* stuff */
}

```

So, the question is:  is there a better way to do this?  This form seems dumb because class B will have a copy of alpha and beta, which is not really what I want.  Is a better approach to use some sort of virtual data?  This seems like a straight forward thing that probably happens often, I'm just not very experienced with c++, so any advice would be very appreciable!  

Thanks in advance!
Mike

---

### Post by dwhitney67 on 2010-05-10
edited: code doesn't work.

---

### Post by nvteighen on 2010-05-10
> **mjobrien said:**
> Hi everyone,

First of all, I am fairly new to this forum, so if this question is out of line (since it is not Ubuntu related), I apologize, and just let me know ;o)

On the contrary! Here everyone's programming issues are welcome!

> 
```

class alpha{
/* stuff */
}

class beta : public alpha {
/* stuff */
}

class A{
alpha alpha_obj;
/* stuff */
}

class B : public A {
beta beta_obj;
/* stuff */
}

```


IMO, it depends on what you're doing. This very abstract example has nothing I can complain about, as there's no relationship between alpha and beta besides the fact that a beta and an alpha object are part of every B instance... 

Something different would be if you want B not have an alpha on it... Well, then I just don't get what you want to do.

---

### Post by mjobrien on 2010-05-10
Yes, sorry I meant to write that.  At this point, B has an instance of alpha in it, and this is wasteful.  B does not need alpha, it needs beta.  So yes, I am trying to eliminate this.  My current thought is to try and do it with pointers.  i.e. don't even include a beta object in B, and just use the alpha object pointer to point to a beta object:


```

class alpha{
/* stuff */
}

class beta : public alpha {
/* stuff */
}

class A{
alpha * alpha_obj;

A(alpha * aa) : alpha_obj(aa) {};

/* stuff */

}

class B : public A {

B(beta * bb) : A(bb) {};

/* stuff */
}

```


I am not sure if this even allowed (we'll see when I get to compile stage), but it seems like a reasonable soln to me, at this point.

Thanks again for the advice from everyone!

---

### Post by Tony Flury on 2010-05-10
> **mjobrien said:**
> Yes, sorry I meant to write that.  At this point, B has an instance of alpha in it, and this is wasteful.  B does not need alpha, it needs beta.

The way i understand what you are saying and how you have your definitions, then the only way to prevents getting alpha in B is not to derive beta from Alpha. Since Beta is derived from Alpha - then every instance of beta is an instance of alpha with extensions (attributes methods etc) - that is was inheritance means.
When you declare an instance of beta as a member of B, you don't get a "copy" of alpha - you get an instance of beta - which contains all the attributes of beta (including those inherited from Alpha).

Each instance you create of B will create a new instance of every member object including beta.

---

### Post by trent.josephsen on 2010-05-10
Please, allow me.  <cracks knuckles>

You have four classes:

A Programmer (B) is an Employee (A).
A Program (beta) is a Task (alpha).
An Employee has a Task.
A Programmer has a Program.

You want to avoid redundancy, so you don't want a Programmer to have both a Task and a Program -- the Program is the programmer's Task.  Am I following so far?

So, an Employee has a member myTask.  When you create an Employee, you will set employee.myTask = new Task("Empty garbage").  When you create a Programmer, you will set programmer.myTask = new Program("Tile windows").  Since every Program is a Task, you can store a Program object into a Task member variable.  What's more, you can call methods of Task on the Program object without caring whether it is a Program or a generic Task -- this is known as polymorphism.

It looks something like this in suspiciously Pythonesque pseudocode:

```

class Task:
    Task(self, description): # this is a constructor
        self.description = description

class Program (Task):
    Program(self, description):
        super(description) # call the parent constructor

class Employee:
    Employee(self, task):
        self.task = task

class Programmer (Employee):
    Programmer(self, program):
        super(program)

```

I don't know how clear I have made myself, but I don't know if I can do any better at the moment.  If you are still having trouble, please go for some more specific code and tell us what the problem is exactly.

---

### Post by nvteighen on 2010-05-11
> **trent.josephsen said:**
> Please, allow me.  <cracks knuckles>

You have four classes:

A Programmer (B) is an Employee (A).
A Program (beta) is a Task (alpha).
An Employee has a Task.
A Programmer has a Program.

[...]


A nice way to put it, but it demonstrates that one can solve this issue by knowing what's the code **meant** to do.

So, @OP:
Could you please tell us what are you trying to do? I mean, what's you code all about?

Because from the information given, what I'd do is something like this:
```

class alpha
{
    // stuff
};

class beta : public alpha
{
    // stuff
};

class base_for_A_and_B
{
    // stuff common to A and B
};

class A : public base_for_A_and_B
{
    alpha myAlpha;
    // more stuff specific to A
};

class B : public base_for_A_and_B
{
    beta myBeta;
    // more stuff specific to B
};

```

---

### Post by mjobrien on 2010-05-12
> **nvteighen said:**
> 
```

class alpha
{
    // stuff
};

class beta : public alpha
{
    // stuff
};

class base_for_A_and_B
{
    // stuff common to A and B
};

class A : public base_for_A_and_B
{
    alpha myAlpha;
    // more stuff specific to A
};

class B : public base_for_A_and_B
{
    beta myBeta;
    // more stuff specific to B
};

```

Thanks!  This is something I had not thought of doing, and I like this approach.  Using this approach, however, my classes A and alpha would essentially be empty as I use all of alpha in beta, and I use all of A in B.  That's why I was hoping for a simpler extension solution--but this would definitely work.  What I had tried that did not work is using a pointer as in:

```

#include <iostream>

using namespace std;

class alpha{
public:
  int a;
  alpha(int aa) : a(aa) {};
};

class beta : public alpha {
public:
  int b;
  beta(int aa, int bb):alpha(aa), b(bb){};
};

class A{
public:
  alpha * obj;  // to store either alpha or beta pointer
  void f() {cout << "alpha->a = " << obj->a << endl;};
  A(alpha * aa): obj(aa) {};
};

class B : public A {
public:
  void g() {cout << "beta->a = " << obj->a << ", beta->b = " << obj->b << endl;};
  B(beta * bb): A(bb) {};
};

int main(){
  int x = 1;
  int y = 2;
  beta * bb = new beta(x, y);
  B obj_B(bb);
  obj_B.f();
  obj_B.g();
  return 0;
}

```

This simple code will (almost) compile, and complain that alpha has no member b.  (Commenting out the call to obj->b, everything compiles and runs.)  So, it appears that pointers are not the solution.  Thanks for all the help, and if I don't hear back, I will use the shared base class solution (thanks!)

---

### Post by mjobrien on 2010-05-12
Ok, this is a solution that seems to be working.  Any input would be appreciated, as I don't know if this is bad coding style, a complete and non-standard hack =)  But it seems to be doing what I want.

```

#include <iostream>

using namespace std;

class alpha{
public:
  int a;
  alpha(int aa) : a(aa) {};
};

class beta : public alpha {
public:
  int b;
  beta(int aa, int bb):alpha(aa), b(bb){};
};

class A{
public:
  alpha * _obj;  // to store either alpha or beta pointer
  virtual alpha* obj();
  void f() {cout << "alpha->a = " << obj()->a << endl;};
  A(alpha * aa): _obj(aa) {};
};

class B : public A {
public:
  virtual beta* obj();
  void g() {cout << "beta->a = " << obj()->a << ", beta->b = " << obj()->b << endl;};
  B(beta * bb): A(bb) {};
};

alpha* A::obj(){
  return (alpha*) _obj;
}

beta* B::obj(){
  return (beta*) _obj;
}

int main(){
  int x = 1;
  int y = 2;
  beta * bb = new beta(x, y);
  B obj_B(bb);
  obj_B.f();
  obj_B.g();
  return 0;
}

```

Thanks everyone for the input on this problem!

-Mike

---

### Post by dwhitney67 on 2010-05-12
The use of the virtual methods is the proper way to go.  Of course, with your example, you should consider providing more encapsulation for your data.

In an effort to demonstrate that the code in your previous post could be used to some degree, I threw the following together.  It is somewhat similar to your latest attempt in that it uses virtual methods.

```

#include <iostream>

class Alpha
{
public:
   Alpha(const int aval) : my_aval(aval) {}

   inline int  aval() const         { return my_aval; }
   inline void aval(const int aval) { my_aval = aval; }

   friend std::ostream& operator<<(std::ostream& os, const Alpha& a);

protected:
   int my_aval;
};


class Beta : public Alpha
{
public:
   Beta(const int aval, const int bval) : Alpha(aval), my_bval(bval) {}

   inline int  bval() const         { return my_bval; }
   inline void bval(const int bval) { my_bval = bval; }

   friend std::ostream& operator<<(std::ostream& os, const Beta& b);

private:
   int my_bval;
};


std::ostream& operator<<(std::ostream& os, const Alpha& a)
{
   os << "my_aval = " << a.my_aval;
   return os;
}


std::ostream& operator<<(std::ostream& os, const Beta& b)
{
   os << "my_aval = " << b.my_aval << "\n"
      << "my_bval = " << b.my_bval;
   return os;
}


class A
{
public:
   A(Alpha* obj) : my_obj(obj) {}

   virtual ~A() { delete my_obj; }

   friend std::ostream& operator<<(std::ostream& os, const A& a)
   {
      os << *(a.my_obj);
      return os;
   }

protected:
   Alpha* my_obj;
};


class B : public A
{
public:
   B(Beta* obj) : A(obj) {}

   virtual ~B() {}

   friend std::ostream& operator<<(std::ostream& os, const B& b)
   {
      os << *(static_cast<Beta*>(b.my_obj));
      return os;
   }
};


int main()
{
   B b(new Beta(10, 20));

   std::cout << b << std::endl;
}

```

---

### Post by trent.josephsen on 2010-05-13
Gah, the abstraction, it is strangling me... ;)

We could give you a more accurate solution if you would tell us what problem you are *actually* trying to solve.  A and B, alpha and beta tell us nothing.

---

### Post by nvteighen on 2010-05-13
> **trent.josephsen said:**
> Gah, the abstraction, it is strangling me... ;)

We could give you a more accurate solution if you would tell us what problem you are *actually* trying to solve.  A and B, alpha and beta tell us nothing.

That's why I went for the "base class that is inherited by two children classes" approach... it's the generic way to solve this issue...

@dwhitney67: 
I still don't get where you're trying to head to :p It makes sense, but I feel my idea is just rather... well... the obvious... Could you please elaborate it?

---

### Post by mjobrien on 2010-05-13
The argument against a shared base class, in this case, would be that I want to extend this hierarchy more:

(base_class -> derived_class)
A -> B -> C -> ...

alpha -> beta -> gamma -> ...

And then have alpha a member of A, beta a member of B, gamma a member of C, and so on.  Though, this problem is easily solved, I think, by just putting in pointers to alpha, beta and gamma rather than the actual class.  Then, whenever a function from A is called, it will use only 'alpha-piece of gamma', but when a function from B is called, it will use the 'beta-piece of gamma', and so on.  The code to do this is:

```

#include <iostream>

using namespace std;

class alpha{
public:
  int a;
  alpha(int aa) : a(aa) {};
};

class beta : public alpha {
public:
  int b;
  beta(int aa, int bb):alpha(aa), b(bb){};
};

class A{
public:
  alpha * obj;  // to store either alpha or beta pointer
  void f() {cout << "alpha->a = " << obj->a << endl;};
  A(alpha * aa): obj(aa) {};
};

class B : public A {
public:
  beta * obj; // to store beta pointer
  void g() {cout << "beta->a = " << obj->a << ", beta->b = " << obj->b << endl;};
  B(beta * bb): A(bb), obj(bb) {};
};

int main(){
  int x = 1;
  int y = 2;
  beta bb(x,y);
  B obj_B(&bb);
  obj_B.f();
  obj_B.g();
  return 0;
}

```


I think this does what I want, and it is simple.  I don't even need to employ virtual functions (aside from the ones I'm already planning to use.)


Thanks again to everyone!

---

### Post by trent.josephsen on 2010-05-13
Okay, now I just want to know:  why are you using inheritance in the first place?  You don't (in this code) use polymorphism or any kind of dynamic binding.  You don't appear to want to use the members of the base class in the derived class.  You seem to want to avoid writing virtual functions.  Your "is-a" relationships look suspiciously like "has-a" relationships.  In a nutshell, there is probably an object oriented way to approach this problem, but you haven't taken it and none of us understand the problem well enough to suggest it.

---

### Post by mjobrien on 2010-05-13
> **trent.josephsen said:**
> Okay, now I just want to know:  why are you using inheritance in the first place?  You don't (in this code) use polymorphism or any kind of dynamic binding.  You don't appear to want to use the members of the base class in the derived class.  You seem to want to avoid writing virtual functions.  Your "is-a" relationships look suspiciously like "has-a" relationships.  In a nutshell, there is probably an object oriented way to approach this problem, but you haven't taken it and none of us understand the problem well enough to suggest it.



Well, really my classes are much more complicated than this example.  This was just cooked up to get the general structure across to everyone, so that people could see what I was trying to do, and also so that I could debug the structure and see what potential downfalls there would be, w/o anything else getting in the way ;o)  To actually post real code would take pages....so I thought this example would be a better way to go.  In essense, at every step along my A->B->C->... chain, I am using all the components in A through B.  And all the components of B through C.  And same w/ the alpha->beta->gamma->... chain.  The reason I build it up like this is because my first "experiment" uses only A and alpha.  My second uses B and beta, and my third will use C and gamma, and so on.  Each experiment is just adding more complicated functionality to the previous....but I still need to demonstrate the previous experiment.  For ease of use, for myself and others, I don't want people to have to look at things like c_obj.b_obj.a_obj.member, so I chose this approach so that one only ever has to consider the classes C and gamma, if they are doing a type C experiment.  I hope this answers your question.  Maybe I'm still doing it in a dumb way, but I'm learning =)

---

### Post by DrMelon on 2010-05-13
> **trent.josephsen said:**
> Please, allow me.  <cracks knuckles>

You have four classes:

A Programmer (B) is an Employee (A).
A Program (beta) is a Task (alpha).
An Employee has a Task.
A Programmer has a Program.

[etc]

While this didn't seem to be chosen as the solution, this has helped me to understand polymorphism immensely. Thankyou!

---

### Post by nvteighen on 2010-05-13
> **mjobrien said:**
> Well, really my classes are much more complicated than this example.  This was just cooked up to get the general structure across to everyone, so that people could see what I was trying to do, and also so that I could debug the structure and see what potential downfalls there would be, w/o anything else getting in the way ;o)  To actually post real code would take pages....so I thought this example would be a better way to go.  In essense, at every step along my A->B->C->... chain, I am using all the components in A through B.  And all the components of B through C.  And same w/ the alpha->beta->gamma->... chain.  The reason I build it up like this is because my first "experiment" uses only A and alpha.  My second uses B and beta, and my third will use C and gamma, and so on.  Each experiment is just adding more complicated functionality to the previous....but I still need to demonstrate the previous experiment.  For ease of use, for myself and others, I don't want people to have to look at things like c_obj.b_obj.a_obj.member, so I chose this approach so that one only ever has to consider the classes C and gamma, if they are doing a type C experiment.  I hope this answers your question.  Maybe I'm still doing it in a dumb way, but I'm learning =)

This is starting to sound to the CLOS-like approach of combined methods in Common Lisp or maybe I'm just that confused that my brain is trying to grasp an analogy in order to understand this somehow... :P

Let me see if I got what you want...

For instance, you have a two parallel hierarchies: A->B->... and alpha->beta->... whose relation is that A has an alpha member, B has a beta member, etc. Then, you want, for example, that a D object that has a delta member acted as an A with alpha, as a B with beta, as a C with gamma and as a D with delta, right? So, the idea would be that if I do myD.something(), this method gets applied first using myD as an A, then as a B, then as a C and then, finally, as a D, "incrementally"? The same for the alpha->beta->... "line".

The other requirement you want is that A's members be specific to A and B specific to B while methods still be used interchangeably... I have an issue with this, but first tell me if I got the idea.

If that's what you want, you'll be trying to reimplement half of Common Lisp's object system in C++... You better try using Common Lisp or change your design. You can use virtual methods, but you'll get into a weird typecasting hell to make it work.

---

### Post by mjobrien on 2010-05-13
> **nvteighen said:**
> This is starting to sound to the CLOS-like approach of combined methods in Common Lisp or maybe I'm just that confused that my brain is trying to grasp an analogy in order to understand this somehow... :P

Let me see if I got what you want...

For instance, you have a two parallel hierarchies: A->B->... and alpha->beta->... whose relation is that A has an alpha member, B has a beta member, etc. Then, you want, for example, that a D object that has a delta member acted as an A with alpha, as a B with beta, as a C with gamma and as a D with delta, right? So, the idea would be that if I do myD.something(), this method gets applied first using myD as an A, then as a B, then as a C and then, finally, as a D, "incrementally"? The same for the alpha->beta->... "line".

The other requirement you want is that A's members be specific to A and B specific to B while methods still be used interchangeably... I have an issue with this, but first tell me if I got the idea.

If that's what you want, you'll be trying to reimplement half of Common Lisp's object system in C++... You better try using Common Lisp or change your design. You can use virtual methods, but you'll get into a weird typecasting hell to make it work.



Yeah, I think that's the right idea.  I am not sure what you mean by "methods used interchangeably", but if that means that I want A's methods accessible by B, then yes.  One of my earlier ideas used weird type casting, so you are right ;o)  My current version seems to be working (though, I won't know for sure until I'm done w/ the debugging).  I haven't yet progressed to tier C yet, so maybe that will make things harder.  But so far, so good.

---

### Post by nvteighen on 2010-05-13
> **mjobrien said:**
> Yeah, I think that's the right idea.  I am not sure what you mean by "methods used interchangeably", but if that means that I want A's methods accessible by B, then yes.  One of my earlier ideas used weird type casting, so you are right ;o)  My current version seems to be working (though, I won't know for sure until I'm done w/ the debugging).  I haven't yet progressed to tier C yet, so maybe that will make things harder.  But so far, so good.

Ok, so then:

1) Use virtual functions, as they might suit you much better... Though, you'll have to use type casting for making the code know what implementation (or better the implementation associated with which class) to use when. Pointers won't help too much here...
2) Look at this. I haven't coded anything for the alpha->beta->... line, but it'd work exactly the same.

```

(defclass A ()
  ((alpha :initarg :alpha
          :accessor alpha)))

(defclass B (A)
  ((beta :initarg :beta
         :accessor beta)))

(defclass C (B)
  ((gamma :initarg :gamma
          :accessor gamma)))

(defclass D (C)
  ((delta :initarg :delta
          :accessor delta)))

(defgeneric print-whatever (object))

;; This could be replaced by a powerful macro that writes this repetitive code
;; automatically, but it's not the idea behind this. I just want to show how
;; CLOS seems to be what the OP wants to do in C++.
(defmethod print-whatever ((myobj t)) ; Default case. Does nothing.
  nil)

(defmethod print-whatever ((myobj A))
  (format t "alpha: ~a~%" (alpha myobj))
  (call-next-method))

(defmethod print-whatever ((myobj B))
  (format t "beta: ~a~%" (beta myobj))
  (call-next-method))

(defmethod print-whatever ((myobj C))
  (format t "gamma: ~a~%" (gamma myobj))
  (call-next-method))

(defmethod print-whatever ((myobj D))
  (format t "delta: ~a~%" (delta myobj))
  (call-next-method))

```

Run on Slime/SBCL:
```

CL-USER> (defparameter Dobject (make-instance 'D :alpha 0 :beta "s" :gamma -1 :delta "hello!"))
DOBJECT
CL-USER> (print-whatever Dobject)
delta: hello!
gamma: -1
beta: s
alpha: 0
NIL
CL-USER> 

```

One can change the order of combination, but I'm not that quite good at that yet ;) Don't worry for the last NIL there... it's just for correctness.

The issue is that you want to avoid access of data because of "redundancy" where there's no redundancy at all. If you insist in the idea of B "being" an A, then it's perfect to have B being able to access the alpha in A... and it may be even needed if your "combined methods" (using Common Lisp-lingo) become more complex. In C++ you can use privacy (both accessing permissions and inheritance type) to make this...

---

### Post by dwhitney67 on 2010-05-13
> **nvteighen said:**
> 
@dwhitney67: 
I still don't get where you're trying to head to :p It makes sense, but I feel my idea is just rather... well... the obvious... Could you please elaborate it?

The code I posted met the original requirements the OP originally laid out.  However, now that we have been provided additional details of his project, I believe the OP is on the wrong track.

From what I understand, there is a flaw in his design if the OP plans to have a hierarchy such as A <- B <- C <- D <- etc, where B is a subclass of A, and C a subclass of B, etc.  I cannot think any such thing on Earth that could fit this model.

What the OP probably should do is define each of his classes independently of each other, which each having their respective flavor of member data.  Each of these classes should however subclass from an interface (abstract) base-class that defines the common operations that he wishes each object to perform.

The abstract base-class merely declares the interface, but it is up to each sub-class to actually implement the methods.

If the OP requires that his class objects be operated on in a polymorphic fashion, then maintaining a handle to the interface class would suffice.

In summary:
```

#include <iostream>


class Abstract
{
public:
   virtual void doSomethingUnique() = 0;

   // other abstract methods

protected:
   Abstract() {}
};


class A : public Abstract
{
public:
   A(int val) : myVal(val) {}

   void doSomethingUnique()
   {
      std::cout << "class A is doing something." << std::endl;
   }

   inline int  val() const { return myVal; }
   inline void val(int v)  { myVal = v; }

private:
   int myVal;
};


class B : public Abstract
{
public:
   B(int val) : myVal(val) {}

   void doSomethingUnique()
   {
      std::cout << "class B is doing something." << std::endl;
   }

   inline int  val() const { return myVal; }
   inline void val(int v)  { myVal = v; }

private:
   int myVal;
};


int main()
{
   Abstract* a1 = new A(10);
   Abstract* a2 = new B(20);

   a1->doSomethingUnique();
   a2->doSomethingUnique();
}

```

The other possibility is to have class B contain an object of class A, and class C contain an object of class B, etc.  But even this design seems a bit hokey.

```

class A
{
   ...
};

class B
{
public:
   B(A* a) : myA(a) {}

private:
   A* myA;
};

class C
{
public:
   C(B* b) : myB(b) {}

private:
   B* myB;
};

int main()
{
   C c(new B(new A));
   ...
}

```

---

