---
title: "effective namespaces?"
date: 2010-12-21
forum: Programming Talk
---

### Post by worksofcraft on 2010-12-21
I notice that namespaces in C++ like std:: and boost:: are simply crammed full of seemingly unrelated goodies, so I'm wondering if there aren't better ways to use this language feature to enhance the structure and intelligibility of code?

Does anyone have any views on the subject please?

---

### Post by dwhitney67 on 2010-12-21
Typically a namespace name is chosen based on the project name.  Of course, one could have a namespace within a project namespace; but hardly no one likes to type anymore.
```

namespace Foo
{
  namespace One
  {
     static const int value = 1;
  }

  namespace Two
  {
     static const int value = 2;
  }
}

#include <cassert>

int main()
{
   assert(Foo::One::value == 1);
   assert(Foo::Two::value == 2);
}

```

---

### Post by PaulM1985 on 2010-12-21
I usually start off with my namespace being the name of the project, like dwhitney said, then have lots of sub namespaces underneath to provide logical groupings, eg:

MyProject.Geometry
MyProject.Ui
MyProject.Characters

etc

This allows for encapsulation since things in different namespaces have different levels of access to the things in the namespace when using protected and default access.

EDIT: I think default access relates more to Java than C++.  Also, you could use "using" in the top of your C++ files to prevent having to type the fully qualified name, provided the class you are using is not in multiple namespaces.

Paul

---

### Post by worksofcraft on 2010-12-21
> **dwhitney67 said:**
> Typically a namespace name is chosen based on the project name.  Of course, one could have a namespace within a project namespace; but hardly no one likes to type anymore.
```

namespace Foo
{
  namespace One
  {
     static const int value = 1;
  }

  namespace Two
  {
     static const int value = 2;
  }
}

#include <cassert>

int main()
{
   assert(Foo::One::value == 1);
   assert(Foo::Two::value == 2);
}

```

I am thinking more about the opposite direction:

I've more or less finished a project of mine now but there is a new project I want to work on and some of the very general bits  from the former will be very useful, while the bulk of it is completely unrelated.

So instead of getting finer control inside that project I want to split it into very general purpose bits that I can reuse and highly specific bits with a dedicated purpose.

That's not too hard to do... but now I get the problem that in my new project I'm using another namespace developed by someone else ("anti grain geometry" package to be precise), while in my old project I'm using Glib and Gtk.

... what I don't want, is to get to a situation where just about every package I work on depends on every other package and drags in all those external dependencies too :confused:

---

### Post by worksofcraft on 2010-12-21
> **PaulM1985 said:**
> I usually start off with my namespace being the name of the project, like dwhitney said, then have lots of sub namespaces underneath to provide logical groupings, eg:

MyProject.Geometry
MyProject.Ui
MyProject.Characters

etc

This allows for encapsulation since things in different namespaces have different levels of access to the things in the namespace when using protected and default access.

EDIT: I think default access relates more to Java than C++.  Also, you could use "using" in the top of your C++ files to prevent having to type the fully qualified name, provided the class you are using is not in multiple namespaces.

Paul

Is it possible to use "inheritance" with name spaces?

In English something like:

MyProject.Geometry uses MyGeneralpurposeProject and uses AGG
MyProject.Ui uses MyGeneralpurposeProject and uses Glib

---

### Post by dwhitney67 on 2010-12-21
I cannot think any way around the issue, other than to "reinvent the wheel".

For example, if you like Glib's ustring, but you don't want to have to deal with importing all other facets of Gtk, well then you are in a tight spot.  Consider swiping (porting) the code for ustring (or whatever it is you need), and place it into your homemade library.  Of course, if you reuse someone else's code, do give them the GPL credit.

---

### Post by PaulM1985 on 2010-12-22
> **worksofcraft said:**
> Is it possible to use "inheritance" with name spaces?

In English something like:

MyProject.Geometry uses MyGeneralpurposeProject and uses AGG
MyProject.Ui uses MyGeneralpurposeProject and uses Glib

I don't think you can create a hierarchy like that, but I think that in the example:

MyProject.Geometry
MyProject.Ui

Both classes in Geometry and in Ui have access to classes in MyProject.  So you would look at namespaces as sets and subsets rather than an inheritance.

In your example, you would have to have "using" declared in the top of each file that uses those namespaces.  I am guessing you where asking that question to see if it is possible to identify a dependency relationship between namespaces.  I don't think it is that easy.  You are probably better to make notes in a readme file in the package if you want that information.

Paul

---

### Post by worksofcraft on 2010-12-23
> **PaulM1985 said:**
> I don't think you can create a hierarchy like that, but I think that in the example:

MyProject.Geometry
MyProject.Ui

Both classes in Geometry and in Ui have access to classes in MyProject.  So you would look at namespaces as sets and subsets rather than an inheritance.

In your example, you would have to have "using" declared in the top of each file that uses those namespaces.  I am guessing you where asking that question to see if it is possible to identify a dependency relationship between namespaces.  I don't think it is that easy.  You are probably better to make notes in a readme file in the package if you want that information.

Paul

Thanks for that insight Paul :)
Ok I think I've got the solution now...
[LIST=1]
[*]I put all the common generic classes in the top level namespace (and I keep it's name short to cut down on reading and writing)
[*]Within that I make namespaces that are related to a topic but otherwise are self contained.
[*]Then finally I split out the modules that are dependent on other packages with their own namespace
[/LIST]

So like, say my generic namespace is cs:: (my initials) Within that I have namespace cs::conform:: which deals with container formatting and cs::draw:: which deals with drawing. cs::draw:: is dependent on outside package agg:: but cs::conform:: is not.

Then in cs::conform:: is just this one module that is dependent on gtk so probably I should split that out into it's own name space... Then when I write an application I can just choose which parts I want to be using and am made aware of when I want to drag some other set of components in :)

OTOH I could just go back to sticking cs_ on the front of all my class names and forget about namespaces... but since they've been implemented I might as well try and use them to good effect :popcorn:

---

### Post by worksofcraft on 2010-12-23
Just checking if I'm doing this right:

For each section that resides in cs::conform I have to write:
```

namespace cs {
    namespace conform {
    ...
    } // end cs:: conform
} end cs

```

or can I do it more succinctly?
How would you personally handle indentation... like indent everything to level 3 before you start within the nested section?

---

### Post by PaulM1985 on 2010-12-24
Ah, I thought you would have been able to use 
```

namespace Some::Space {

```

but it seems like this is not the case.

This article on stack overflow seems to have some suggestions: [http://stackoverflow.com/questions/713698/c-namespaces-advice](http://stackoverflow.com/questions/713698/c-namespaces-advice)

I know it is a bit horrible to look at but maybe you could have:

```


// Namespace Some::Space::Thing
namespace Some { namespace Space { namespace Thing {

    //Single tab things in
    ...
    ...

} } }

```

Paul

This link also is pretty interesting: [http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?id=1043284351&answer=1046398336](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?id=1043284351&answer=1046398336)

---

### Post by worksofcraft on 2010-12-24
> **PaulM1985 said:**
> Ah, I thought you would have been able to use 
```

namespace Some::Space {

```

but it seems like this is not the case.

This article on stack overflow seems to have some suggestions: [http://stackoverflow.com/questions/713698/c-namespaces-advice](http://stackoverflow.com/questions/713698/c-namespaces-advice)

I know it is a bit horrible to look at but maybe you could have:

```


// Namespace Some::Space::Thing
namespace Some { namespace Space { namespace Thing {

    //Single tab things in
    ...
    ...

} } }

```

Paul

This link also is pretty interesting: [http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?id=1043284351&answer=1046398336](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?id=1043284351&answer=1046398336)

Sroustrup explains amongst others as follows (C.10.3)

[LIST=1]
[*]ideally a class would just be a namespace with a few extra facilities
[*]a namespace is open (i.e you can keep adding to it) while a class is closed (you have to define it all in one place)
[*]namespaces should be preferred over classes when all that is needed is encapsulation of names.
[/LIST]

Somehow they seem to have stopped just short of taking it through to it's logical conclusion: an open struct with no instance. IMO the same idea as nested namespaces could have been expressed more elegantly as a form of inheritance:
```

name_space common_space {
	// common structs and type defs used in loads of other namespaces
}

// a name space that shares access to the common one
namespace my_space: common_space {
	// yep we I wanna use all those common ones in here
}
// a different name space that also has implicit access of  the common one
namespace your_space: common_space {
	// me too, I wanna use them
	// but we don't wanna clash anything else
}

```

Quite a few times I've come across other people's code using classes that have no need to ever be instantiated, e.g. where they control aspects of a template. I wouldn't be surprised if one could thus find good uses even for constructs like template namespaces:
```

template<typename tType> namespace special_space {
	struct special_pair_type {
		tType myThingy1, myThingy2
	};
}

```

OTOH lumping everything together like they do in namespace std:: and that horrible syntax for nesting seems a bit of a disappointment wrt the concept of "encapsulation".

---

### Post by worksofcraft on 2010-12-24
I forgot to mention... you can crash the C++ compiler with this one:
[php]

#include <cstdio>
namespace common {
	int x = 7;
}

namespace common { namespace derived {
	int y = 6;
}}

namespace other = common::derived;

namespace other {
	int x = 5;
}

int main(int argc, char *argv[], char *envp[]) {
	printf("x=%x, y=%x\n", other::x, other::y );
	return !printf("exits normally\n");
}
[/php]

so I think I'll just stick with a flat name space hierarchy.

---

