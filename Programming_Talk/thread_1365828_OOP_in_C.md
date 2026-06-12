---
title: "OOP in C"
date: 2009-12-27
forum: Programming Talk
---

### Post by nmccrina on 2009-12-27
Sorry for bringing this subject up yet again (I don't want to start a flame war, honest!), but I'm having a bit of trouble choosing between learning C or C++. So far I've had about 2-3 semesters worth of C++, and 1 semester of C, so I'm trying to decide which I want to focus on and really become proficient in.

Basically it comes down to this: I like the OOP paradigm, but I prefer coding in C. So I'm wondering how feasible it is to do OOP in C. I know that one can use the Gnome/glib framework to kind of approximate it, but after doing some coding with it I think C++ would actually end up being a cleaner OOP solution. Are there any alternatives? Would you recommend not using OOP, or at least waiting until I become more of a C guru and can roll my own framework?

Also, my main interest is in systems programming, with games coming in a more or less distant second, which would seem to be another factor in favor of C. 

Does anyone have any thoughts/ideas/suggestions?

---

### Post by CptPicard on 2009-12-27
Objective-C? It is a different, and IMO, nicer take on the "C with classes" idea. It really takes C and adds *just* OOP, with a different method dispatch idea than C++.

That said, doing object-oriented code in C is perfectly feasible. I tend to find that all of my C ends up with some sort of object-structure... what you do is that you have structs as objects (you can even do "inheritance" by nesting structures, extending like that), and then you just have a set of functions that take an "opaque pointer" (of some "top-level class-struct" for example) into them as first parameter, and internally "know" what kind of a struct* to expect. You can even stick function pointers into the structure so that the correct function gets carried around...

Something I have recently started doing is actually code my C as Python extensions. Python gives you high-level object management and program structure, individual pieces of code can be written specifically in C... but I guess this is a bit advanced :)

---

### Post by nmccrina on 2009-12-27
> **CptPicard said:**
> Objective-C? It is a different, and IMO, nicer take on the "C with classes" idea. It really takes C and adds *just* OOP, with a different method dispatch idea than C++.

That said, doing object-oriented code in C is perfectly feasible. I tend to find that all of my C ends up with some sort of object-structure... what you do is that you have structs as objects (you can even do "inheritance" by nesting structures, extending like that), and then you just have a set of functions that take an "opaque pointer" (of some "top-level class-struct" for example) into them as first parameter, and internally "know" what kind of a struct* to expect. You can even stick function pointers into the structure so that the correct function gets carried around...

Something I have recently started doing is actually code my C as Python extensions. Python gives you high-level object management and program structure, individual pieces of code can be written specifically in C... but I guess this is a bit advanced :)

Thanks for your help! Objective-C sounds interesting; I'll have to look into that.

Actually, I have sort of been spiraling towards the idea of using Python (or Ruby) for the stuff where OOP would be a good fit (especially GUI's), and using C for the lower level stuff. I feel the most comfortable with C-style languages, though.

---

### Post by Can+~ on 2009-12-27
[PHP]//Standard Headers
#include <stdio.h>
#include <string.h>


typedef struct
{
	int id;
	char name[100];
}parent;

typedef struct
{
	int id;
	char name[100];
	
	char childname[100];
}child;

void parent_print(parent *p)
{
	printf("id: %d\nname: %s\n", p->id, p->name);
}

int main(int argc, char **argv)
{
	child x;
	
	x.id = 5;
	strncpy(x.name, "This is my name", 16);
	strncpy(x.name, "This is my child name", 23);
	
	parent_print((parent*)&x);
	
	return 0;
}
[/PHP]

Kinda fishy, but it's a certain degree of polymorphism. Though, notice that is is purely a memory issue, if you exchange the order of the structs, for instance:

[PHP]typedef struct
{
	char name[100];
	int id;
}parent;[/PHP]

It breaks, because C casting is pretty much "let's assume that the thing is here, and in the same order".

Also, to achieve a more "elegant" quasi-class in C, try having different files containing specialized functions for the struct, for instance:

[LIST]
[*]list.c contains:
[LIST]
[*]struct list : struct that represents the list base
[*]struct node : a node of the list
[*]list_insert : insert something on a list
[*]list_delete : ...
[*]list_<name> : ...
[/LIST]
[*]heap.c contains:
[LIST]
[*]struct heapdata
[*]heap_heapifyup : ...
[*]heap_heapifydown : ...
[*]heap_<name> : ...
[/LIST]
[/LIST]

---

### Post by nmccrina on 2009-12-27
I think C + High Level Interpreted Language For OOP When Necessary is what I'll do. It will probably end up being Ruby, simply because I already have a book on that. Thanks for your input, guys!

:popcorn:

Then, eventually, Lisp!

---

### Post by mmix on 2009-12-28
glib and vala is oop

---

### Post by nvteighen on 2009-12-28
While Can+~'s example is also OOP, it doesn't bring up any access security, making everything public.

What usually is done is what CptPicard said: the opaque pointer technique, which relies on the fact that the compiler compiles each module separately and only afterwards links everything up, thus giving you compile-time encapsulation (not runtime though... a pointer to a private member will crack the whole thing).

The drawback of this is that it forces you to use dynamic memory allocation even for members you know how big they are at compile-time... otherwise you'll get a dangling pointer. This is because, as you're referring to stuff defined in another module, you just don't know how big it is in the main module.

---

### Post by nrs on 2009-12-28
You can ***approximate ***it. id did this up until about Doom III I think before they just gave up and switched to C++. Do you think you can make it work better than John Carmack? :P

If you insist on this, I think you're better off writing C-style code w/ a C++ compiler. Just  pick and choose which parts you want to use or don't want to use. You don't have to play with templates, etc. if you don't want to. For the longest time I didn't even know how to write them or when to use them.

---

### Post by MadCow108 on 2009-12-28
you can also have a look at gobject and vala
vala adds syntax for gobject which is a C object system

---

### Post by jpkotta on 2009-12-28
> **nrs said:**
> You can ***approximate ***it. 

OOP has nothing to do with the language.  It's all about how the code is organized.  Of course, the language can certainly help in this regard.

BTW, this guide is pretty well written: [www.planetpdf.com/codecuts/pdfs/ooc.pdf](www.planetpdf.com/codecuts/pdfs/ooc.pdf)

---

### Post by phrostbyte on 2009-12-28
Using structs and the "union" keyword you can do some pretty powerful OOP in C to the point where I doubt there is any OOP pattern you can not implement in pure C. Of course OOP languages themselves tend to have nicer OOP syntax.

Of course you can also use gobject, which provides C programmers with a very powerful and modern object model with all the typical "buzzwords" that come along with it. :)

---

### Post by matthew.ball on 2009-12-28
I remember reading something about the Linux kernel requiring code submitted in an object-oriented structure.

Though, it didn't say how this was done.

---

### Post by jpkotta on 2009-12-29
> **matthew.ball said:**
> I remember reading something about the Linux kernel requiring code submitted in an object-oriented structure.

Though, it didn't say how this was done.

The kernel has its own object system, kobject.  Plus other parts of it are somewhat OO even if they don't use kobject.  Read about it in [LDD3]("http://lwn.net/Kernel/LDD3/") (Ch. 14).

---

### Post by nrs on 2009-12-29
> **jpkotta said:**
> OOP has nothing to do with the language.  It's all about how the code is organized.  Of course, the language can certainly help in this regard.

BTW, this guide is pretty well written: [www.planetpdf.com/codecuts/pdfs/ooc.pdf]("http://www.planetpdf.com/codecuts/pdfs/ooc.pdf")
This is obviously technically true, after all, C++ didn't just magically pop into existence. But unless you're insane and going around writing what may as be another compiler/language all you're going to get is an approximation of the stuff you're capable of doing C++.

---

### Post by kahumba on 2009-12-29
Since you care more about system programming then C should be your choice.
But for 3D games and GUI programming I'd suggest C++.
I myself moved from C to C++ for (Gtk) GUIs cause:
(1) C is too verbose,
typical Gtk C code:
```
gtk_window_set_title(GTK_WINDOW(window), "title");
```
typical Gtk C++ code:
```
window->set_title("title");
```
(2) C has no clue about inheritance which for one makes your code littered with (ugly, upper-case) macros and yet more code.
(3) Extending a component in C is a nightmare (the straw that broke the camel's back for me)
(4) (I still mean non-system programming) the overhead of C++ over C is not meaningful, it's not like Mono or Java compared to C!

---

### Post by napsy on 2009-12-29
I would advice you to first rethink if you really need object orientation. There are other paradigms that are much better then object-orientation.

Take for example the new language from Google, Go. It has no classes  but has interfaces that enable you to do abstraction.

---

### Post by CptPicard on 2009-12-29
> **napsy said:**
> I would advice you to first rethink if you really need object orientation.

Object-orientation really needs to be understood quite broadly, it has many incarnations and a lot of languages are, in some way, object-oriented. What kind of things the language has built-in to support it varies.

In C for example, I do find that my structs more often than not really behave as kinds of objects, "methods" for which need to be resolved manually or perhaps by some ad hoc dispatching mechanism.

 >  There are other paradigms that are much better then object-orientation.

Well... even your typical functional programming languages have their data items as "objects" that you then call functions on. Functions themselves also tend to be objects that can be passed to other functions and so on...

> It has no classes  but has interfaces that enable you to do abstraction.

Classes are a type system thing, although objects in an object system often have a datatype that is a member of some class hierarchy. The interfaces issue is a really good example of a variant of an OOP implementation that recognizes that inheriting implementation is often a bad thing -- it tends to result in "fragile base classes" and other problems...

---

### Post by iharrold on 2010-01-05
You can sort of overload C functionality via changing function pointers.  I.e.

```

struct 
{
   void (*myfunct) (int);
} myClass;

void foo1(int)
{
   /* do something */
};

void foo2(int)
{
   /* do something else */
};

void main (void)
{
  struct myClass mc1;

  mc1.myfunct = foo1;  // has does something
  mc1.myfunct = foo2;  // now does something else

  mc1.myfunct(1);  /* do something else */


}

```

So you can have the struct do different things depending up type by changing the the function is pointed too.  But there still is not desctructor/constructor option which is very much needed for oop.

Note:  I didn't compile this, I just wrote free hand so it may have compile error.s

---

### Post by WitchCraft on 2010-01-05
You can use C++ and try to only use C code, except for the object orientation/function overloading.

But I'd actually recommend you this:

If you want to program operating systems/computer graphics/video, continue learning C.

If you want to go into the industry and write web and database (using) applications, learn C#.

---

