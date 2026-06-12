---
title: "Gtk v. dynamic_cast"
date: 2010-11-05
forum: Programming Talk
---

### Post by worksofcraft on 2010-11-05
[php]
// Gtk callback:
gboolean on_expose_event(
	GtkWidget *widget,
	GdkEventExpose *event,
	gpointer data
) {
	graphplacement *pRoot = dynamic_cast<graphplacement *> (data);
... etcetera
}
[/php]

Not surprisingly guess what that enigmatic gpointer actually is...
```

thedata.cpp:141: error: cannot dynamic_cast &#8216;data&#8217; (of type &#8216;void*&#8217;) to
type &#8216;struct graphplacement*&#8217; (source is not a pointer to class)

```

So the choices I seem to have are:
[LIST=1]
[*]To cast gpointer data unsafely into a graphplacement * and get segmentation fault if I got it wrong.
[*]Have a global graphplacement * that I set before the call back happens.
[*]Unsafely cast to some base class and then do a dynamic_cast to check it's correct
[*]Any other suggestions?
[/LIST]

---

### Post by saulgoode on 2010-11-05
5. Use [GTKMM](http://www.gtkmm.org/en/) when interfacing between GTK and C++.

---

### Post by worksofcraft on 2010-11-05
> **saulgoode said:**
> 5. Use [GTKMM](http://www.gtkmm.org/en/) when interfacing between GTK and C++.

I'm more interested in knowing **how** to do it than having some tool that does it.

p.s. also as I'm trying to explore concepts like [automatic double buffering in GTK+]("http://people.gnome.org/~federico/misc/gtk-drawing-model/index.html#double-buffering") and how to do [threaded animation]("http://cairographics.org/threaded_animation_with_cairo/") I just feel that the Gtkmm wrapper is obfuscating the very mechanisms I'm trying to study.

---

### Post by dwhitney67 on 2010-11-06
Try using static_cast or reinterpret_cast, the latter being closely related to a C-style cast operator.

Read more here: [http://www.cplusplus.com/doc/tutorial/typecasting/](http://www.cplusplus.com/doc/tutorial/typecasting/)

---

### Post by worksofcraft on 2010-11-06
> **dwhitney67 said:**
> Try using static_cast or reinterpret_cast, the latter being closely related to a C-style cast operator.

Read more here: [http://www.cplusplus.com/doc/tutorial/typecasting/](http://www.cplusplus.com/doc/tutorial/typecasting/)

Thanks, that is a very useful article and I shall definitely be making good use of it :)

In particular the const_cast will help when interfacing older libraries in which const'ity was not declared.

reinterpret_cast definitely makes much clearer what one is doing or actually isn't doing in that case: I think I will benefit from only using the original style of type casting where a constructor for the new type is actually being applied.

I expect static cast will help especially where there is multiple inheritance.

Meanwhile of course I realized I don't even have to cast, because the call back functions have to be declared as "C" so that the glade call back module can find them. Thus in the following code I simply tell the compiler that "user_data" is a "graphplacement *" and not a "gpointer" although it's equally unsafe. You can also see I experimented witha  global pointer there. That way **is completely type safe** even if some frown on global data ;)
[php]
// GUI call back functions: must suppress C++ name mangling
// so builder module can find and connect them:
extern "C" {
	GtkWidget *pDrawingArea1; // type checked by compiler

	gboolean on_click(
		GtkWidget *widget,
		GdkEventButton *event,
		graphplacement *user_data // unsafe
	) {
... etc.
[/php]

---

### Post by worksofcraft on 2010-11-06
Meanwhile I'm still struggling with accessing an object as one of it's own base classes which I thought was supposed to be automatic.
e.g. I have a class for placing nodes in a graph. It's a derivative of the base class for edges, but incorporating an affine transform as attribute of said edge:
[php]
struct graphplacement: cs_edge, affine {
	graphplacement(cs_node &rN, const affine & rPos): cs_edge(rN), affine(rPos) {}
};
[/php]

... but when I come to use it as an instance of it's base class "affine", I seemed to need to tell the compiler with a cast :confused: I suspect static_cast would be more appropriate but I don't see why I need to cast at all because it's supposed to already be an instance of affine class isn't it?  
[php]
	graphplacement *pPlace = ... // some iterator expression of cs_edges

	* (affine *) pPlace = affine::rotate(angle_to_rotate_by)) * affine(*pPlace); // transform a rotation
[/php]

---

### Post by dwhitney67 on 2010-11-06
It seems to me that you are neglecting to develop small, standalone, test applications where you can test your theories:
```

#include <iostream>

class A
{
public:
   void doSomethingA() { std::cout << "doSomethingA() called." << std::endl; }
};

class B
{
public:
   void doSomethingB() { std::cout << "doSomethingB() called." << std::endl; }
};

class Foo : public A, public B
{
public:
   void doSomethingFoo() { std::cout << "doSomethingFoo() called." << std::endl; }
};


void function(void* something)
{
   Foo* foo = reinterpret_cast<Foo*>(something);
   foo->doSomethingA();
   foo->doSomethingB();
   foo->doSomethingFoo();
}

int main()
{
   Foo foo;
   function(&foo);
}

```

---

### Post by worksofcraft on 2010-11-06
> **dwhitney67 said:**
> 
...
```

void function(void* something)
{
   A* a = reinterpret_cast<A*>(something);
   a->doSomething();

   B* b = reinterpret_cast<B*>(something);
   b->doSomething();

   Foo* foo = reinterpret_cast<Foo*>(something);
   foo->doSomethingFooish();
}
...

```

OK yeah since I read that article you referenced I got the casting of void *'s sorted... although evidently it wasn't even necessary because gmodule prohibits use of "name mangling" on call back functions. But moving on the static cast in the example above..
[php]
	static_cast<affine> (*pPlace)  = affine::rotate(deg2bfPi(1)) * *pPlace;
[/php]
The compiler already knows that *pPlace derives from class affine, so why does it complain when I take the static_cast out:
```

thedata.cpp:103: error: no match for &#8216;operator=&#8217; in &#8216;* pPlace = 
affine::rotate(((unsigned int)deg2bfPi(1.0e+0))).affine::operator*(((const affine&)((const affine*)(& pPlace->graphplacement::<anonymous>))))&#8217;

``` 
Shouldn't it be able to use the default copy assignment of it's base class affine& affine:: operator=(const affine&) since the equation evaluates to one of those using the defined affine affine:: operator* (affine &) ? :confused:

---

### Post by dwhitney67 on 2010-11-06
I've never seen a static_cast (or any type of cast) used in the left-hand-side of an assignment operator.

What is it that you are attempting to do?  For this statement:
```

  static_cast<affine> (*pPlace)  = affine::rotate(deg2bfPi(1)) * *pPlace;  

```
I would need to know what value type is returned by rotate(), and whether or not you have overloaded the operator*() method is it is a complex object (ie something other an int, float, double, etc).

---

### Post by worksofcraft on 2010-11-06
> **dwhitney67 said:**
> I've never seen a static_cast (or any type of cast) used in the left-hand-side of an assignment operator.

What is it that you are attempting to do?  For this statement:
```

  static_cast<affine> (*pPlace)  = affine::rotate(deg2bfPi(1)) * *pPlace;  

```
I would need to know what value type is returned by rotate(), and whether or not you have overloaded the operator*() method is it is a complex object (ie something other an int, float, double, etc).

[php]
struct affine: coord {
	m2x2 sMatrix;
	// construct matrix for basic transformations
	static affine rotate(unsigned iAngle);
...
	affine operator * (const affine &rIn); // it should be using this one
};

[/php]
It compiles and runs with the static_cast, but not without it. IDK if it makes a difference, but there are no virtual functions in affine or it's base class and the derived graphplacent does not overload operator * either, it's full definition was given earlier... just a constructor and two base classes.

edit... oops no to run correctly it actually needs:
[php]

	* static_cast<affine *> (pRoot)  = affine::rotate(deg2bfPi(-1)) * *pRoot;
[/php]
I suspect static_cast creating a copy when it's not applied to a pointer.

---

