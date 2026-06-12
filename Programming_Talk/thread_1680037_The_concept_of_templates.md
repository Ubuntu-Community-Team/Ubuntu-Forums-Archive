---
title: "The concept of templates"
date: 2011-02-01
forum: Programming Talk
---

### Post by worksofcraft on 2011-02-01
I noticed there is a lot of misunderstanding about the value of templates in C++... thought I would write something about it see if anyone wants to offer other perspective!

ATM I'm exploring different graphics formats.
The thing about graphics is that there are lots and lots of pixels in an image so we really do want to optimize on the amount of per-pixel processing.

In any application there are (atleast) 3 different pixel formats:

[LIST=1]
[*]The pixel format used on the display device. In X11 this tends to be RGB_888 i.e. interleaved Red, Green and Blue components with 8 bits each, but other systems have totally different arangements.

[*]The pixel format used by the application. If you continue to use RGB_888 here then you can expect rapidly to get saturation and cumulative rounding problems as you blend and scale different images... those paltry 8 bits don't have much dynamic range!

[*]The pixel format used to store the image. This relates to compression algorithms and the results vary for different types of image. Typically jpeg is good for real photos and png better for artificial pictures.
[/LIST]

As we expect to be converting pixels on the fly from one format to another templates come to our rescue.

How is that? Well simple: Instead of running some kind of conversion selection based on flags at run time, the compiler detects the parameters of the conversion routine and selects the function template that matches those types at compile time.

The compiler can then inline the code for said conversion... typically to do absolutely nothing what-so-ever in the numerous applications where the programmer has elected to use the most appropriate pixel format for the target system.
Even when he/she has not done that, the C++ templates can expand the matched function right there inline, avoiding iterative function calls and parameter stack frames in tight copy loops that could easily get iterated millions of times per image :shock:

Do you think this explanation is informative?

---

### Post by schauerlich on 2011-02-01
You can think of templates as a natural extension of object oriented programming philosophy. An object is essentially a black box containing data with a well defined interface for retrieving and modifying that data (according to the object's rules). Essentially, an object is defined by its interface. Patterns in these interfaces can be described in terms of the methods that the various objects have in common. For instance, anything that can be sorted is likely to have a "less_than" method, and anything that represents button in a graphic interface may have a "draw_self" method. If you're writing a function that deals with a bunch of different objects that all have some usage pattern in common (such as comparisons or drawing), it's handy to only have to write one function for it that can apply to any such object that can do "the same" thing, instead of multiple slightly different functions for each type.

The designers of many different programming languages have noticed this pattern, and made their language accommodate this. Some languages make you explicitly define the attributes that the various objects have in common (such as with interfaces in Java or typeclasses in Haskell), while others are implicit (C++ templates or smalltalk/python-style duck typing).

Perhaps that wasn't the sort of explanation you were looking for, but for a beginner just being introduced to templates it should give some idea of why they're there.

---

### Post by worksofcraft on 2011-02-01
> **schauerlich said:**
> You can think of templates as a natural extension of object oriented programming philosophy. An object is essentially a black box containing data with a well defined interface for retrieving and modifying that data (according to the object's rules). Essentially, an object is defined by its interface. Patterns in these interfaces can be described in terms of the methods that the various objects have in common. For instance, anything that can be sorted is likely to have a "less_than" method, and anything that represents button in a graphic interface may have a "draw_self" method. If you're writing a function that deals with a bunch of different objects that all have some usage pattern in common (such as comparisons or drawing), it's handy to only have to write one function for it that can apply to any such object that can do "the same" thing, instead of multiple slightly different functions for each type.

The designers of many different programming languages have noticed this pattern, and made their language accommodate this. Some languages make you explicitly define the attributes that the various objects have in common (such as with interfaces in Java or typeclasses in Haskell), while others are implicit (C++ templates or smalltalk/python-style duck typing).

Perhaps that wasn't the sort of explanation you were looking for, but for a beginner just being introduced to templates it should give some idea of why they're there.

A limitation I find of object oriented programming is that methods are associated with just one object class. However to my perception, interactions are often between **two** different objects. They are no more "method" of one class than of the other so I think the generalization of my example is that templates bridge that gap by associating code with potentially more than one class while not demanding that you make it a method of either of them :)

---

### Post by schauerlich on 2011-02-02
> **worksofcraft said:**
> A limitation I find of object oriented programming is that methods are associated with just one object class. However to my perception, interactions are often between **two** different objects. They are no more "method" of one class than of the other so I think the generalization of my example is that templates bridge that gap by associating code with potentially more than one class while not demanding that you make it a method of either of them :)

You may want to look into Common Lisp-style multiple dispatch. Since lisp syntax doesn't lend itself naturally to dot notation, they opted to make method calls on objects look like normal function calls using multiple/dynamic dispatch. Essentially, you define generic functions, and then create specializations of that function for each class. That way, you can have method names in the global namespace as global functions, without the disadvantage of naming clashes. 

Whereas in Python you might write something like this:

```
class Foo:
  def shout():
    return "Foo!"

class Bar:
  def shout():
    return "Bar!"

f = Foo()
b = Bar()

f.shout()
b.shout()
```

You would write something like this:

```
; leaving out foo and bar class definitions for brevity
(defgeneric shout (obj))

(defmethod shout ((obj foo))
  "Foo!")

(defmethod shout ((obj bar))
  "Bar!")

(mapcar #'shout (list (make-instance 'foo) (make-instance 'bar)))
```

But using generic functions for simulating OOP is only one use - the type of situation you describe could also be resolved cleanly with generic functions. Generic functions can specialize on any number of parameters, as long as what method you want can be resolved.

---

### Post by CptPicard on 2011-02-02
Bah, schauerlich beat me to the multiple-dispatch post. Single-dispatch is only a limitation of singly-dispatched OO languages; object-orientedness can actually be much broader and general topic than "instances of Java/C++ classes that own method implementations". This is again one of the reasons why other languages than those ones are good for learning, as the idea of "object" is much more malleable there, and once you have learned to "think" of some general problem in certain terms, the solution for a particular, given problem is possibly hackable together in more restricted, rigid languages (and the design patterns you need to get around the crap perhaps make more sense by that time).

---

### Post by worksofcraft on 2011-02-02
> **CptPicard said:**
> Bah, schauerlich beat me to the multiple-dispatch post. Single-dispatch is only a limitation of singly-dispatched OO languages; object-orientedness can actually be much broader and general topic than "instances of Java/C++ classes that own method implementations". This is again one of the reasons why other languages than those ones are good for learning, as the idea of "object" is much more malleable there, and once you have learned to "think" of some general problem in certain terms, the solution for a particular, given problem is possibly hackable together in more restricted, rigid languages (and the design patterns you need to get around the crap perhaps make more sense by that time).

Sure, and in this old thread here I was finding out how to get [double dispatch]("http://ubuntuforums.org/showthread.php?t=1609356") to work using that "more rigid" concept of object oriented inheritance, but as you say, that was restrictive in having to do it in multiple levels. ANy particular dispatch level was limited to subclasses of a base class.

TBH the Python example IMO only shows sequential calling of two different methods of two different classes that happen to have the same name and since I don't know lisp that appears to me to do the same.

OTOH using templates in C++ you have the full flexibility of creating functions (and new classes with yet more methods) that combine any set of classes and I don't quite follow design pattern you would be wishing to ameliorate there :confused:

---

### Post by schauerlich on 2011-02-02
> **worksofcraft said:**
> OTOH using templates in C++ you have the full flexibility of creating functions (and new classes with yet more methods) that combine any set of classes

I'm not quite sure what you mean here.

---

### Post by worksofcraft on 2011-02-02
> **schauerlich said:**
> I'm not quite sure what you mean here.

I mean here is example of a multiple "dispatch" using multiple classes. IDK how one could do that in say Python or Java, but that isn't the point: I'm trying to clear up what programming paradigm is served by templates in C++

[php]
// g++ bar_shout.cpp
#include <iostream>
#include <cmath>

using namespace std;

// traditional methods
struct foo_class {
	int shout() { return 0xF00; }
};

struct empty_class {
	double shout() { return M_PI; }
};

struct bar_class {
	const char * shout() { return "Last orders at the bar!"; }
};

struct pub_class {
	const char * shout() { return "Drinks are on the house!"; }
};

// note: all these classes are totally independent and not sub classes of any
// common base class and their methods don't even return the same type.

// example a "method" that "dispatches" from TWO different classes
// could be done for any number of them
template <class tFooishClass, class tBarishClass> void foo_all_bars(
	tFooishClass &rFoo, tBarishClass &rBar) {

	cout << "the bar shouts \"" << rBar.shout() <<
		"\" and the foo asks for " << rFoo.shout() << endl;
};

	
int main() {
	// four different instances of 4 different classes
	foo_class sWhisperingFool;
	empty_class sHadEnough;
	bar_class sThirsty;
	pub_class sGenerousLandLord;

	// a method "dispatched" according to various combinations of multiple classes
	foo_all_bars(sWhisperingFool, sThirsty);
	foo_all_bars(sHadEnough, sGenerousLandLord);
	foo_all_bars(sWhisperingFool, sGenerousLandLord);
	foo_all_bars(sHadEnough, sThirsty);
	// or even swapping bars for foos
	foo_all_bars(sGenerousLandLord, sHadEnough);
	// etc...

	return 0;
}

[/php]

p.s. edit: the output it generates is:
```

$ ./a.out
the bar shouts "Last orders at the bar!" and the foo asks for 3840
the bar shouts "Drinks are on the house!" and the foo asks for 3.14159
the bar shouts "Drinks are on the house!" and the foo asks for 3840
the bar shouts "Last orders at the bar!" and the foo asks for 3.14159
the bar shouts "3.14159" and the foo asks for Drinks are on the house!

```

---

### Post by schauerlich on 2011-02-02
That isn't multiple dispatch. With multiple dispatch, you can call two completely different functions based on the type of the argument. While the C++ compiler does create a bunch of different "foo_all_bars" functions behind the scenes, you're really only doing a search-and-replace of types combined with a singly dispatched call to "shout". Take [this](http://paste.lisp.org/display/119319) for example. 

```
schauerlich@inara:~$ sbcl --script foo.lisp
Two foos? Who wants two foos?
That's more like it.
Now that's just weird.

```
You can see that, based on the types of the argument handed into "hello", something completely different is called - not just the same function with differently typed parameters.

More on multiple dispatch: [http://en.wikipedia.org/wiki/Multiple_dispatch](http://en.wikipedia.org/wiki/Multiple_dispatch)

---

### Post by worksofcraft on 2011-02-02
> **schauerlich said:**
> That isn't multiple dispatch. With multiple dispatch, you can call two completely different functions based on the type of the argument. While the C++ compiler does create a bunch of different "foo_all_bars" functions behind the scenes, you're really only doing a search-and-replace of types combined with a singly dispatched call to "shout". Take [this](http://paste.lisp.org/display/119319) for example. 

```
$ sbcl --script foo.lisp
Two foos? Who wants two foos?
That's more like it.
Now that's just weird.

```
You can see that, based on the types of the argument handed into "hello", something completely different is called - not just the same function with differently typed parameters.

More on multiple dispatch: [http://en.wikipedia.org/wiki/Multiple_dispatch](http://en.wikipedia.org/wiki/Multiple_dispatch)

lol well you don't need templates or anything to do that, it's simply called overloading and in C++...
[php]
// g++ bar_shout2.cpp
#include <iostream>
#include <cmath>

using namespace std;

// traditional methods
struct foo_class {
	int shout() { return 0xF00; }
};

struct empty_class {
	double shout() { return M_PI; }
};

struct bar_class {
	const char * shout() { return "Last orders at the bar!"; }
};

struct pub_class {
	const char * shout() { return "Drinks are on the house!"; }
};

// note: all these classes are totally independent and not sub classes of any
// common base class and their methods don't even return the same type.

// WTF ok then different methods for different classes if that wut U want but
// it's hardly "rocket science" and doesn't even need templates or polymorphism!

void foo_all_bars(foo_class & sF, bar_class & sB) {
	cout << sF.shout() << " overloaded1 " << sB.shout() << endl;
}
void foo_all_bars(empty_class & sF, bar_class & sB) {
	cout << sF.shout() << " overloaded2 " << sB.shout() << endl;
}
void foo_all_bars(foo_class & sF, pub_class & sB) {
	cout << sF.shout() << " overloaded3 " << sB.shout() << endl;
}
void foo_all_bars(empty_class & sF, pub_class & sB) {
	cout << sF.shout() << " overloaded4 " << sB.shout() << endl;
}
void foo_all_bars(pub_class & sB, empty_class & sF) {
	cout << sF.shout() << " overloaded5 " << sB.shout() << endl;
}



int main() {
	// four different instances of 4 different classes
	foo_class sWhisperingFool;
	empty_class sHadEnough;
	bar_class sThirsty;
	pub_class sGenerousLandLord;

	// a method "dispatched" according to various combinations of multiple classes
	foo_all_bars(sWhisperingFool, sThirsty);
	foo_all_bars(sHadEnough, sGenerousLandLord);
	foo_all_bars(sWhisperingFool, sGenerousLandLord);
	foo_all_bars(sHadEnough, sThirsty);
	// or even swapping bars for foos
	foo_all_bars(sGenerousLandLord, sHadEnough);
	// etc...

	return 0;
}
[/php]

---

### Post by schauerlich on 2011-02-03
> **worksofcraft said:**
> lol well you don't need templates or anything to do that, it's simply called overloading and in C++...


Right. There's definitely a conceptual overlap there, as it says [on the wikipedia page](http://en.wikipedia.org/wiki/Multiple_dispatch#Data_types). It's largely a matter of compile time vs run time and the conveniences associated with each method.

```
#include <cstdlib>
#include <iostream>

using namespace std;

struct foo {
  foo() {}
};

struct bar {
  bar() {}
};


bool some_runtime_condition() {
  return (rand() % 100) <= 50;
}

void *try_something(void) {
  if (some_runtime_condition()) {
    return new foo();
  }
  else {
    return new bar();
  }
}

void use_it(foo *f) {
  cout << "foo" << endl;
}
void use_it(bar *b) {
  cout << "bar" << endl;
}

int main(void) {
  void *foo_or_bar = try_something();
  use_it(foo_or_bar); // which method will be called?

  return 0;
}

```

```
(defclass foo () ())
(defclass bar () ())

(defun some-runtime-condition ()
  (<= (random 100) 50))

(defun try-something ()
  (if (some-runtime-condition)
      (make-instance 'foo)
      (make-instance 'bar)))

(defgeneric use-it (obj))

(defmethod use-it ((obj foo))
  (format t "foo~%"))
(defmethod use-it ((obj bar))
  (format t "bar~%"))

(defun main ()
  (let ((foo-or-bar (try-something)))
    (use-it foo-or-bar))) ; no ambiguity because of runtime type checking

```

---

### Post by nvteighen on 2011-02-03
We're mixing discussions about the object and the pragmatics of that said object. Being a physicist doesn't make you an engineer...

C++ templates are just a patch to create generic functions on top of a static compiled language. That's all they are.

Of course, C++ templates are one way to go for creating anything that resembles multiple dispatch, but that's an application of that linguistic feature. It's like when in English you can choose between a passive and an active sentence to express the same thing. This is very well shown by worksofcraft's example of "multiple dispatch" using a "procedural" design (aka C-like OOP) with overloaded functions.

So, if I were to compare C++ templates to something in Lisp, I'd do it with Lisp macros. Not unreasonable at all, as the Common Lisp Object System (CLOS) is actually implemented with macros. The situation is then more-or-less the same: you've got a metaprogramming facility being used to create a generic function system.

Now. CLOS's dispatch is actually completely different to C++'s dispatch because the former is dynamic and the latter, static. No matter what you use, C++ does everything at compile-time (heck, even dynamic_cast<>() is actually a compile-time operator!). And this is the key point that makes CLOS multiple dispatching much better than any C++ implementation for multiple dispatch.

The difference is that in CL there's no need for dispatching. 1) You can write functions that take arguments without checking any type, just resolving stuff by requesting behaivor. 2) There's no explicit distinction between classes and non-classes. So, using regular non-generic defun's also constitutes OOP programming in CL, because everything is some kind of object derived from STANDARD-CLASS. What I mean with this is that OOP programming in CLOS can be done without ever dispatching anything for any type.

defgeneric, IMO, is about setting selective dispatching by "class" in a similar way to how overloaded non-class functions work in C++. And similarly, this can be used for multiple dispatching. There are occasions where you want a certain combination of classes to work in a specific way and another in a different one. Look at my Common Chess project and take a look on how I use defgeneric: I only use it when using a defun would imply to write a huge conditional block testing for the class of the arguments... You could, of course: use the class-of standard procedure, test for the target class and redirect to some procedure.

That's my take.

---

### Post by worksofcraft on 2011-02-03
> **nvteighen said:**
> We're mixing discussions about the object and the pragmatics of that said object. Being a physicist doesn't make you an engineer...

C++ templates are just a patch to create generic functions on top of a static compiled language. That's all they are.

Of course, C++ templates are one way to go for creating anything that resembles multiple dispatch, but that's an application of that linguistic feature. It's like when in English you can choose between a passive and an active sentence to express the same thing. This is very well shown by worksofcraft's example of "multiple dispatch" using a "procedural" design (aka C-like OOP) with overloaded functions.

So, if I were to compare C++ templates to something in Lisp, I'd do it with Lisp macros. Not unreasonable at all, as the Common Lisp Object System (CLOS) is actually implemented with macros. The situation is then more-or-less the same: you've got a metaprogramming facility being used to create a generic function system.

Now. CLOS's dispatch is actually completely different to C++'s dispatch because the former is dynamic and the latter, static. No matter what you use, C++ does everything at compile-time (heck, even dynamic_cast<>() is actually a compile-time operator!). And this is the key point that makes CLOS multiple dispatching much better than any C++ implementation for multiple dispatch.

The difference is that in CL there's no need for dispatching. 1) You can write functions that take arguments without checking any type, just resolving stuff by requesting behaivor. 2) There's no explicit distinction between classes and non-classes. So, using regular non-generic defun's also constitutes OOP programming in CL, because everything is some kind of object derived from STANDARD-CLASS. What I mean with this is that OOP programming in CLOS can be done without ever dispatching anything for any type.

defgeneric, IMO, is about setting selective dispatching by "class" in a similar way to how overloaded non-class functions work in C++. And similarly, this can be used for multiple dispatching. There are occasions where you want a certain combination of classes to work in a specific way and another in a different one. Look at my Common Chess project and take a look on how I use defgeneric: I only use it when using a defun would imply to write a huge conditional block testing for the class of the arguments... You could, of course: use the class-of standard procedure, test for the target class and redirect to some procedure.

That's my take.

Hum... well since Common Lisp is an interpreted language I suspect it doesn't ever resolve anything at compile time :confused:

One thing is certain and that is that both for compiled and for  interpreted languages you can't get away from having to write the code for each combination that you plan to support. So it's just an issue of how the selection is done.

Run time dynamic dispatch is achieved with virtual methods in compiled languages like C++ and in rare cases where multiple parameter types cannot be resolved until run time then with the technique illustrated in that thread I referred to earlier (about double dispatch), you still NEVER have to code a "huge conditional block testing for the class of the arguments".

Note: If you really were concerned about what goes on behind the scenes there, then in a nutshell, it first dispatches through one v-table and then through another v-table... thus working like a multi dimensional v-table. IDK how the lisp interpreter goes about it but it will have to do some kind of multi dimensional look up at run time before it can know what to do.

p.s. anyway this thread isn't meant to be about which language is the better it is about what concepts are being served by templates.

---

### Post by CptPicard on 2011-02-03
Actually, I'll clarify a bit; my comment was specifically targeted at the idea of "this"-based method dispatch, that is, when the implementation is chosen based on the type of the object whose method gets called.

Lisp-style dispatch is built on the idea that objects and functions are always decoupled because in the end that just makes more sense. When one just throws out the method-call (method strictly being "member of class" here) idea and works with standalone functions, C++ does actually come pretty close to multiply-dispatched multimethods (especially when template specializations are thrown into the mix). Close enough actually that it took me the writing of the whole post to come up with a counter-example, see below...

Of course, Common Lisp is able to dispatch on *anything*, not just types, and has before/around/after methods and so on but this was about multiple-dispatch...


> **nvteighen said:**
> 
So, if I were to compare C++ templates to something in Lisp, I'd do it with Lisp macros.

C++ templates are actually Turing-complete in their own right, but hmm... Lisp macros are a full front-end compiler of the language, that you can write in that language itself...


> **worksofcraft said:**
> Hum... well since Common Lisp is an interpreted language I suspect it doesn't ever resolve anything at compile time :confused:

The most robust CL implementation of today:

[http://en.wikipedia.org/wiki/Steel_Bank_Common_Lisp](http://en.wikipedia.org/wiki/Steel_Bank_Common_Lisp)

Well, a CL implementation *can* be interpreted, but SBCL has a compiler where you can type-annotate and write in imperative terms the speed-critical stuff to your heart's content and it produces very efficient assembly... the best part of the picture is that as you know, it's sufficient to optimize only the true bottlenecks of the code...  and the macro facility and so on allows for still retaining a high level of abstraction while compiling down, especially when combined with type inference (which unfortunately in a non-pure-functional language is necessarily somewhat limited), with rather few type-annotations (that is, not needed all over the place).

> Run time dynamic dispatch is achieved with virtual methods in compiled languages like C++

Yeah, and the vtable-based dispatch is the dispatch-based-on-single-object problematic stuff I didn't like above.

> thus working like a multi dimensional v-table. IDK how the lisp interpreter goes about it but it will have to do some kind of multi dimensional look up at run time before it can know what to do.

You know, I guess the counter-example of "multiple dispatch C++ can't do but CLOS can" indeed has something to do with something that would look like "multi-dimensional vtables" in C++. Like if X is superclass of Y and A is superclass of B, then f(X,A) would always dispatch to an implementation of impl(Y,B), if those are the actual types of the parameters. Overriding in C++ won't do as that is resolved statically. Templates won't do either, as the template parameter types would be those at the location of its instantiation.

When it comes to the SBCL compiler, I suspect it is quite able to compile everything down that it can, and what needs to be resolved at runtime, is left as is. It is very good at making use of compile time type information when it exists.

---

### Post by nvteighen on 2011-02-03
> **worksofcraft said:**
> Hum... well since Common Lisp is an interpreted language I suspect it doesn't ever resolve anything at compile time :confused:

Well, it's byte-compiled... And the major implementations use a compiler for the interpreter. Also, you can optionally turn CL into a static typed language for optimization using some special declaration forms.

> 
One thing is certain and that is that both for compiled and for  interpreted languages you can't get away from having to write the code for each combination that you plan to support. So it's just an issue of how the selection is done.

Run time dynamic dispatch is achieved with virtual methods in compiled languages like C++ and in rare cases where multiple parameter types cannot be resolved until run time then with the technique illustrated in that thread I referred to earlier (about double dispatch), you still NEVER have to code a "huge conditional block testing for the class of the arguments".

Note: If you really were concerned about what goes on behind the scenes there, then in a nutshell, it first dispatches through one v-table and then through another v-table... thus working like a multi dimensional v-table. IDK how the lisp interpreter goes about it but it will have to do some kind of multi dimensional look up at run time before it can know what to do.

p.s. anyway this thread isn't meant to be about which language is the better it is about what concepts are being served by templates.

Ok, maybe my post was a bit messy because I wrote it too early in the morning... and my coffee hadn't made any effect yet.

My point was just that templates are a metaprogramming construct but that language features can be used in different ways... So I agree with you. And then I started a comparison on how C++ and CL do this because CL was brought earlier in the thread to show what multiple dispatch usually means.

So now specifically and exclusively about C++ templates.

Templates work by creating a metafunction that accepts a parameter, usually but not exclusively (you can pass variables to a template...), a type and substitutes it into the body of the function or class returned.

It's a quite simplistic and limited approach to generic programming. But it's a consequence of C++'s own design principles. If you design a language where every type has to be known at compile-time and also want it to support generic programming, you have to implement some overloading support. But, in order to avoid the usage of multiply overloaded functions where the difference between all cases are only one or a few types, templates where created in order to abstract that overloading by the means of a metaprogramming facility that "generates" all versions.

But think about it. If your language (even if low-level) doesn't have to know all types at compile-time, you gain a lot of genericity just with normal "monomorphic" functions. The limit will be set by the behaivor of each element in play. Of course, if you add operator overloading and OOP polymorphism, you have Python.

Ok, but back to C++. IMO, the reason and the way templates were implemented in C++ makes them quite limited for generic programming. As soon as you want to create a templated object from runtime information, you're lost. E.g.: I ask the user to create either a set of objects of class A or one of objects of class B, where A and B aren't in the same class hierarchy; I can't do this:

```

/* Doesn't compile */

#include <iostream>
#include <cctype> // tolower()

class A
{
public:
    A() {}
};

class B
{
public:
    B() {}
};

char prompt_user()
{
    char choice;

    while(1)
    {
        std::cout << "Create object of type A or B?" << std::endl;
    
        std::cin >> choice;
        choice = tolower(choice);

        if((choice != 'a') && (choice != 'b'))
        {
            std::cout << "Error!" << std::endl;
            continue;
        }
        else
            break;
    }

    return choice;
}

template <typename T>
T make_object(char choice)
{
    if(choice == 'a')
        return A();
    else if(choice == 'b')
        return B();
}

int main()
{
    char choice  = prompt_user();
    UNKNOWN_CLASS object = make_object<UNKNOWN_CLASS>(choice); // <- !!!
    
    /* ... */

    return 0;
}

```

Even though the concept for templates, as defined, and with its pretension to be the C++ way to support genericity, this doesn't even compile.

To solve the above, you have to artificially create a parent class Parent that englobes A and B, so that I can "know" that at compile-time that no matter what I choose, it will a Parent object regardless whether it's also an A or a B...

```

#include <iostream>
#include <cctype> // tolower()

class Parent
{
public:
    Parent() {}
};

class A : public Parent
{
public:
    A() {}
};

class B : public Parent
{
public:
    B() {}
};

char prompt_user()
{
    char choice = 0;

    while(1)
    {
        std::cout << "Create object of type A or B?" << std::endl;
    
        std::cin >> choice;
        choice = tolower(choice);

        if((choice != 'a') && (choice != 'b'))
        {
            std::cout << "Error!" << std::endl;
            continue;
        }
        else
            break;
    }

    return choice;
}

Parent make_object(char choice)
{
    Parent result;

    if(choice == 'a')
        result = A();
    else if(choice == 'b')
        result = B();
    
    return result;
}

int main()
{
    char choice  = prompt_user();
    Parent object = make_object(choice);
    
    /* ... */

    return 0;
}

```

But this is "fake". What I'm doing there is to adapt my model to the language's typing system and force two objects to be classified as the same at compile-time.

In other words, C++ templates do add genericity to the language, but they fail to support some pretty simple situations... Situations that end up solved by some counter-intuitive "design pattern". Please be aware that in my code above, the childhood of A and B may be motivated just because I needed to code this snippet and be the case that A and B actually didn't share any feature in common (i.e. that Parent is no more than an empty class). So, they add genericity in cases where no runtime information is needed.

I hope this stated my point in a more ordered fashion.

---

### Post by CptPicard on 2011-02-03
> **nvteighen said:**
> Well, it's byte-compiled... 

Umm... the SBCL compiler produces native code...

---

### Post by nvteighen on 2011-02-03
> **CptPicard said:**
> Umm... the SBCL compiler produces native code...

Mea culpa, mea culpa, mea magna culpa...

---

### Post by Reiger on 2011-02-03
> **CptPicard said:**
> You know, I guess the counter-example of "multiple dispatch C++ can't do but CLOS can" indeed has something to do with something that would look like "multi-dimensional vtables" in C++. Like if X is superclass of Y and A is superclass of B, then f(X,A) would always dispatch to an implementation of impl(Y,B), if those are the actual types of the parameters. Overriding in C++ won't do as that is resolved statically. Templates won't do either, as the template parameter types would be those at the location of its instantiation.

When it comes to the SBCL compiler, I suspect it is quite able to compile everything down that it can, and what needs to be resolved at runtime, is left as is. It is very good at making use of compile time type information when it exists.

I think a nice example here is the diamond pattern. In languages which do objects similar to C++ your basic object looks like:
```

object {
  parent_objects;
  vtable;
  data_members;
}

```

So inheriting methods from a superclass is little more than:

```

dispatch “on” object: 

if method in vtable -> call method
else try to dispatch “on” parents

```

So if you have the hierarchy B inherits from A, C inherits from A, D inherits from both B and C, you get a structure whereby an object of type D (d) has two distinct ancestors of type A, one through a parent B and another through a parent C.

So in C++ and co. multiple inheritance is theoretically possible, but fundamentally broken. In languages such as Lisp where methods (functions) are distinct from data types (arguments/data/objects), you can inherit from as many classes as you care to and not run into any such problem.

In languages where you keep functions/methods distinct from data, a compiler/interpreter merely needs to do two things:
(a) Track classes. (And of course functions outside of classes)
(b) Per class, track implementations. 

The latter is simple because this can be done when a source module is analyzed (before any code is run or compiled): the class & function definitions are always explicitly declared.

---

### Post by worksofcraft on 2011-02-03
> **nvteighen said:**
> ...
But this is "fake". What I'm doing there is to adapt my model to the language's typing system and force two objects to be classified as the same at compile-time...


Yeah thanks for that explanation and I think I understand that you want a totally generic syntax for deferring the identification of object types to whatever point in the program that you need to know.

However from another perspective, every OOP implementation needs some kind of mechanism for determining what type an object is. Many implicitly derive ALL classes from a single root "object" class even if none is stated in your program. In that light C++ allows multiple object hierarchy roots. Thus templates serve to select *which root* you are going to be working from. Then compile time binding mechanisms propagate that through your code for you.

Just to get back to my pixel example that I started with... the technical advantage of templates is their zero overhead at run time. Thus it's not trying to identify my pixel format on every pixel, millions of times per image.

Instead the template and compile time type binding has enabled the compiler to determine exactly which class hierarchy my pixel formats are in and inserts exactly the right code. It's much better than having to code void* pointer casts explicitly and at the other extreme I seriously would **not** want to be doing some kind of fancy behind the scenes dynamic dispatch mechanism there :shock:

TL;DR version: template serves to select which "object class hierarchy root" to use.

---

### Post by psusi on 2011-02-03
> **CptPicard said:**
> Umm... the SBCL compiler produces native code...

Are you sure it doesn't just build an executable that is the byte code interpreter with the byte code built in?  That has long been a trick to "compile" languages that are inherently interpreted.

> **Reiger said:**
> I think a nice example here is the diamond pattern. In languages which do objects similar to C++ your basic object looks like:
```

object {
  parent_objects;
  vtable;
  data_members;
}

```


The vtable pointer is always the first member of the object, then the chain of parent objects follow.

> **Reiger said:**
> So inheriting methods from a superclass is little more than:

```

dispatch “on” object: 

if method in vtable -> call method
else try to dispatch “on” parents

```


No, it just looks like object.vtable->function().  The compiler figures out which function pointer to put in the vtable at compile time.  There is always a pointer to SOME function there.

---

### Post by Reiger on 2011-02-03
@psusi: I was merely sketching out how this logic works -- not the result code/implementation. The dispatch logic is done at compile time for C++ but the example merely serves to show *how* the method to dispatch is chosen where it concerns object inheritance.

In other words: essentially the source analyzers figure out whether or not a method is defined inside the scope of the class/object type and if not defer to parents. But that is completely different from the analyzer of a language (implementation) such as Haskell where you start with a collection of functions/methods under the same name and try to match one with input data (object).

---

### Post by CptPicard on 2011-02-04
> **psusi said:**
> Are you sure it doesn't just build an executable that is the byte code interpreter with the byte code built in?  That has long been a trick to "compile" languages that are inherently interpreted.

Yes, I'm sure. You can try it yourself; set up SBCL and disassemble some compiled functions. It's actually quite charming to observe how the compiler's output changes when you alter the code by adding type annotations, more imperative constructs and so on, allowing the compiler to "compile down" instead of delegating to some runtime service routines. In the end you can write almost "C" and recognize in the assembly what is going on.

---

### Post by worksofcraft on 2011-02-04
> **CptPicard said:**
> Yes, I'm sure. You can try it yourself; set up SBCL and disassemble some compiled functions. It's actually quite charming to observe how the compiler's output changes when you alter the code by adding type annotations, more imperative constructs and so on, allowing the compiler to "compile down" instead of delegating to some runtime service routines. In the end you can write almost "C" and recognize in the assembly what is going on.

Well that's all well and good but AFIK lisp does not actually support the concept of templates.

So say I have a base class called "pixel" and derived classes "monochrome" and "rgb" then using templates I can make each of those domains be their own root to a class hierarchy and thus avoid any need to incorporate virtual table pointers in each and every pixel object on my computer screen.

That is the reason why when it comes to performance level programming, IMO C++ pwns and SBCL doesn't.

IMO there is no "superior" computer language because they each offer different advantages. C++ is good for teaching because it seems to support **ALL** the concepts... even if you personally don't think it does a particularly good job of any of them :P

---

### Post by CptPicard on 2011-02-05
> **worksofcraft said:**
> Well that's all well and good but AFIK lisp does not actually support the concept of templates.

Or perhaps templates as they appear in C++ are a thing of the C++ type system, and that in Lisp, because it's not C++, won't have C++ templates?

Anyway, it's trivial to write a macro in Lisp if you want a replaceable type definition. The compiler type-inferencer takes care of the rest.

> That is the reason why when it comes to performance level programming, IMO C++ pwns and SBCL doesn't.

After hearing you happily proclaim Lisp "interpreted" I'm not going to take your statements regarding supposed Lisp implementations of some things at face value before trying myself :p I do have a 

But as you know, I am more interested in the ideas involved in a programming language's / program's design than tuning for raw speed.

> 
IMO there is no "superior" computer language because they each offer different advantages. C++ is good for teaching because it seems to support **ALL** the concepts...

[http://www.haskell.org/haskellwiki/Higher_order_function](http://www.haskell.org/haskellwiki/Higher_order_function) (no, function pointers or functors are not first-class functions)

[http://en.wikipedia.org/wiki/Homoiconicity](http://en.wikipedia.org/wiki/Homoiconicity) 

(most importantly)
[http://en.wikipedia.org/wiki/Closure_%28computer_programming%29](http://en.wikipedia.org/wiki/Closure_%28computer_programming%29)

Different languages may offer different advantages and there probably is no One Language To Rule Them All in every situation, but some languages are closer to offering all the advantages than others. I've told you at length how I feel about C++'s "signal-to-noise ratio" and ability to convey important concepts in a smallish, coherent package to a learner, so let's not go there again...

---

### Post by nvteighen on 2011-02-05
> **worksofcraft said:**
> Well that's all well and good but AFIK lisp does not actually support the concept of templates.

So say I have a base class called "pixel" and derived classes "monochrome" and "rgb" then using templates I can make each of those domains be their own root to a class hierarchy and thus avoid any need to incorporate virtual table pointers in each and every pixel object on my computer screen.


No, it doesn't work that way.

1) Lisp macros are its templates and they are way more powerful than you think. They can change the Lisp syntax completely... you could write macros to make Lisp look like C++ if you wanted. This is made possible because Lisp expressions are syntax trees and because Lisp is homoiconic (i.e. Lisp code is Lisp data and viceversa). As there's no difference between code and data and, also, the syntax requires almost no parsing, it's extremely easy to create a macro system that's able to create new constructs. Apart from this, there are also "reader macros" that affect the way the reader/parses reads the code (this can be used to create infixed operators, as opposed to the usual prefix Lisp syntax).

2) The Lisp concept works the other way around. You don't add a vtable to any object, but rather to the methods... Ok, that's not a technical description, but it's the concept. The way this is done is by declaring a generic procedure to which you assign several versions ("methods") based on dispatching. This avoids having duplicated vtables.

Remember that Lisp doesn't anything similar to the object.method() notation. In Lisp everything is (procedure args ...), so there's actually no special OOP *syntax* in it, but the concepts are there.

> 
That is the reason why when it comes to performance level programming, IMO C++ pwns and SBCL doesn't.


The reason why C++ is faster is because Common Lisp needs a middle layer in our preferred platforms. But in a Lisp Machine, it'd be the other way around because the interpreted language would be C++. Anyway, SBCL is amazingly fast as a VM.

> 
IMO there is no "superior" computer language because they each offer different advantages.


+1

> 
C++ is good for teaching because it seems to support **ALL** the concepts... even if you personally don't think it does a particularly good job of any of them :P

All Turing-complete languages support all computable concepts. Even ASM does.

The problem with C++ is that it supports all concepts via aggregation, not abstraction. It took C and started to add stuff to it. The result is a mix of different things, OOP based on typing and not on what the objects are (Java is static-typed too and does this... :/), a metaprogramming facility that's quite limited just because someone wanted to ensure type-safety... but type-safety limits C++ classes a lot, making them no more than polymorphic, inheritable C structs with dot notation for methods.

About OOP and performance, well, there's a certain contradiction there. Well, true OOP, based on objects as we consider them in the real world, is quite a high-level thing. So I would expect OOP code to perform worse than a pure procedural solution (if there is such a thing)... And there you have it: no matter how optimizable C++ code is because of its C heritage, the vtable bottleneck is impossible to solve.

And for teaching what you need is something that's consistent and clear. For your information, OOP is usually taught using Java. Maybe not the optimal solution to my taste, but it works because it's cleaner. Why? Well, because they offered an abstracted solution to performance-aware OOP. Be aware that Java's main bottleneck is the JVM startup (the same goes for SBCL).

I won't deny that C++ can be useful, but you have to know a lot of things in order to write good C++ code. In summary, you have to know what low-level programming means, what high-level programming means and, finally, what are the consequences of mixing both levels to what extent. I wouldn't expect someone who hasn't written the Python "Hello world" to be able to do that.

---

### Post by worksofcraft on 2011-02-05
> **CptPicard said:**
> Or perhaps templates as they appear in C++ are a thing of the C++ type system, and that in Lisp, because it's not C++, won't have C++ templates?

Anyway, it's trivial to write a macro in Lisp if you want a replaceable type definition. The compiler type-inferencer takes care of the rest...

This is a thread about the concept of "templates". Templates are not the same thing as macros, because macros are identified by name only and not by their parameter types.

I still don't see the relevance of lisp in this discussion and even if someone has made a compiler for it, it still isn't the kind of language I would choose to implement something like say an mpeg decoder.

---

### Post by worksofcraft on 2011-02-05
> **nvteighen said:**
> 
The reason why C++ is faster is because Common Lisp needs a middle layer in our preferred platforms. But in a Lisp Machine, it'd be the other way around because the interpreted language would be C++.

...
The problem with C++ is that it supports all concepts via aggregation, not abstraction. It took C and started to add stuff to it.


... as you say, C++ evolved from C which in turn evolved from assembler and so they reflect the very fundamental basis on which digital computers still operate today.

> 
And for teaching what you need is something that's consistent and clear. For your information, OOP is usually taught using Java.

IMO OOP isn't really the holy grail of all programming paradigms and it's hardly surprising students fail to grasp simple concepts, like pointers and macros and pass by value and memory management when they are being taught with languages from which these have been deleted :shock:

---

### Post by CptPicard on 2011-02-05
> **worksofcraft said:**
> This is a thread about the concept of "templates". Templates are not the same thing as macros, because macros are identified by name only and not by their parameter types.

As I said, it should be easy to write a Lisp macro to generify types for this kind of a situation. It's not a C++ template, because it's not C++; but it doesn't mean that the C++ template would be somehow conceptually unheard of elsewhere or that the same things wouldn't be achieved in other ways...

> I still don't see the relevance of lisp in this discussion and even if someone has made a compiler for it

Hmm. At least to me it seems like there's a perfectly reasonable chain of exchanges explaining why Lisp was brought up. Care to enlighten me where you're losing track?

> it still isn't the kind of language I would choose to implement something like say an mpeg decoder.

Horses for courses, but as we generally try to keep this particular discussion on a general level, special pleading for application X won't do :)

> it's hardly surprising students fail to grasp simple concepts, like pointers and macros and pass by value and memory management when they are being taught with languages from which these have been deleted :shock:

Maybe they have been deleted because they're not all that relevant to the task at hand; that is, writing programs?

---

### Post by worksofcraft on 2011-02-05
> **CptPicard said:**
> As I said, it should be easy to write a Lisp macro to generify types for this kind of a situation. It's not a C++ template, because it's not C++; but it doesn't mean that the C++ template would be somehow conceptually unheard of elsewhere or that the same things wouldn't be achieved in other ways...



Hmm. At least to me it seems like there's a perfectly reasonable chain of exchanges explaining why Lisp was brought up. Care to enlighten me where you're losing track?



Horses for courses, but as we generally try to keep this particular discussion on a general level, special pleading for application X won't do :)



Maybe they have been deleted because they're not all that relevant to the task at hand; that is, writing programs?

If you look carefully at the opening post of this thread you might notice it is about the benefits of templates to do an efficient compile time method dispatch.

Selecting appropriate conversion for pixel formats I give as example of something that might need that. It is what one might find in an mpeg decoder as it renders movies to your computer screen and writing this kind of program is in fact the task at hand.

p.s. anyway I just thought others might want to know what use templates can be, but for those who are not interested in writing generic data structures and algorithms that produce *zero run-time overhead* then they aren't much use at all.

---

### Post by Reiger on 2011-02-05
Lisp macros are more that just the C ones. They do more than &#8220;(take some parameters and) output some source code&#8221;.

For the best analogy consider a XSLT template:

```

<xsl:template name="other_name">
  <xsl:comment>
    <xsl:copy-of select="."/>
  </xsl:comment>
</xsl:template>
<xsl:template match="pattern_1|pattern_2">
  <xsl:value-of select="'hello world'"/> 
  <xsl:call-template name="other_name"/>
</xsl:template>

```

Essentially whatever matches pattern_1 or pattern_2 are now new programming symbols. They have semantic meaning.

You can inspect the source hierarchy inside the the templates, modify template behaviour accordingly. You are essentially programming the XSLT processor to interpret a particular XML dialect you just defined through templates. The source code is not the XSLT here, it is the XML data it operates on; the XSLT is merely macro's to interpret the XML...

C macro's or C++ templates have no meaning they're just 'clever' shorthands for automating bits of code. Search & replace, a tiny bit more.

---

