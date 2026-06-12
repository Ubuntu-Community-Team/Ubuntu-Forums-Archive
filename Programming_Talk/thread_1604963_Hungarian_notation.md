---
title: "Hungarian notation"
date: 2010-10-24
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-24
Recently found my self learning several large software libraries and it gets quite confusing keeping track of various concepts.

For instance XDefaultScreenOfDisplay(Display *display) returns a **pointer to a data structure** of type "Screen" but XDefaultScreen(Display *display) returns an **integer identifier** for a screen.

In sample code both of these might be assigned to a variable by the name "screen" which might be a member of some other data structure. Add to this the complexity that some of these things need an explicit XFree call to dispose of them once no longer needed while others might need to be freed from some other library or from the general heap and it is easy to make mistakes :(

From more general perspective, in C++ sometimes things are actual class instances, sometimes they are pointers sometimes they references and sometimes simple data types and any of them might need dynamic memory management.

Thus I was wondering about potential of adopting a naming convention to help me keep track. However researching it I find that even Microsoft have moved away from that kind of idea and quoting Linus Torvalds:

"Encoding the type of a function into the name (so-called Hungarian notation) is brain damaged&#8212;the compiler knows the types anyway and can check those, and it only confuses the programmer."


:shock:... no! I'm looking for a way to **avoid** confusion... not create even more confusion :confused: Anyone got any ideas?

---

### Post by worseisworser on 2010-10-24
> **worksofcraft said:**
> Recently found my self learning several large software libraries and it gets quite confusing keeping track of various concepts.

For instance XDefaultScreenOfDisplay(Display *display) returns a **pointer to a data structure** of type "Screen" but XDefaultScreen(Display *display) returns an **integer identifier** for a screen.

In sample code both of these might be assigned to a variable by the name "screen" which might be a member of some other data structure. Add to this the complexity that some of these things need an explicit XFree call to dispose of them once no longer needed while others might need to be freed from some other library or from the general heap and it is easy to make mistakes :(

From more general perspective, in C++ sometimes things are actual class instances, sometimes they are pointers sometimes they references and sometimes simple data types and any of them might need dynamic memory management.

Thus I was wondering about potential of adopting a naming convention to help me keep track. However researching it I find that even Microsoft have moved away from that kind of idea and quoting Linus Torvalds:

"Encoding the type of a function into the name (so-called Hungarian notation) is brain damaged&#8212;the compiler knows the types anyway and can check those, and it only confuses the programmer."


:shock:... no! I'm looking for a way to **avoid** confusion... not create even more confusion :confused: Anyone got any ideas?

Supposedly of course; perhaps actually improving the XLib API would be a better solution than switching to Hungarian notation; it would solve the same problem, only better.

---

### Post by NovaAesa on 2010-10-24
Use good abstraction layers use scoping rules properly - that way you aren't playing with other people's data and your use of a variable will always be (relatively) close to where where it is declared.

Using abstraction layers is extremely important. Other modules/classes/etc should not know about the internal structure of other modules/classes/etc. The api for each module/class/etc should be as clean as possible.

---

### Post by lisati on 2010-10-24
> **NovaAesa said:**
> Use good abstraction layers use scoping rules properly - that way you aren't playing with other people's data and your use of a variable will always be (relatively) close to where where it is declared.

Using abstraction layers is extremely important. **Other modules/classes/etc should not know about the internal structure of other modules/classes/etc. The api for each module/class/etc should be as clean as possible.**

Agreed. For ordinairy use, we shouldn't need to know too much (if anything) about the internals of functions/classes/whatever that we use beyond how to use them correctly and what results to expect.

---

### Post by worksofcraft on 2010-10-24
> **worseisworser said:**
> Supposedly of course; perhaps actually improving the XLib API would be a better solution than switching to Hungarian notation; it would solve the same problem, only better.

Indeed and so I'm playing about with a bunch of ideas. One of them is C++ wrapper for X11, but I also want a more consistent approach to error handling.

Here is very simple wrapper for opening a connection to an X11 "display".
[php]

// g++ xopen.cpp -lX11
#include <stdio.h>
#include <X11/Xlib.h>
#include <stdarg.h> // for exit with error message: "fatal"
#include <stdlib.h> // exit

// print error message then exit: beware, destructors don't get called
void fatal(const char *pFmt, ...) {
	va_list L;
	va_start(L, pFmt);
	vfprintf(stderr, pFmt, L);
	va_end(L);
	exit(EXIT_FAILURE);
//	throw (pFmt); // IDK what to throw atm
}

struct x11display {
	Display *pDpy;
	// NULL name will open the one identified by environment variable DISPLAY
	// hostname:number.defaultscreen
	x11display(char *aName = NULL) {
		pDpy = XOpenDisplay(aName);
		if (!pDpy) fatal(
			"Failed to open display %s\n",
			aName? aName: "NULL"
		);
	}
	~x11display() {
printf("destructor called\n");
		if (pDpy) XCloseDisplay(pDpy); // disconnect from X server
	}
};

int main(int iAc, char *pAv[] ) {
	char *pDisplayName = NULL;
	if (iAc > 1) pDisplayName = *++pAv;
	x11display sX11(pDisplayName);
	return !printf("exits normally\n");
}
[/php]

I try opening my own display with full name. It fails in the constructor (not sure why yet).
At the base level aborting the program with a fatal error message will do, but at some stage I can envisage make a super class that pops up some kind of user dialog. However I want to keep the base class as simple as can be.

However I digress. It's not just about X11, there is similar in other libraries e.g. glib: functions return things using a  gpointer and you have to remember to use g_free when done with them.
Oh well, just interested in any suggestions atm how other people might approach these issues :)

---

### Post by dwhitney67 on 2010-10-24
It works for me, but of course I used the version below.
```

#include <X11/Xlib.h>

#include <cstdarg>
#include <cstdlib>
#include <cstdio>
#include <iostream>


// print error message then exit: beware, destructors don't get called
void fatal(const char *format, ...)
{
   va_list args;
   va_start(args, format);
   vfprintf(stderr, format, args);
   va_end(args);
   exit(EXIT_FAILURE);
}


namespace Wrapper
{
class Display
{
public:
   // NULL name will open the one identified by environment variable DISPLAY
   // hostname:number.defaultscreen
   Display(const char* displayName = NULL)
      :display(XOpenDisplay(displayName))
   {
      if (!display)
      {
         fatal("Failed to open display %s\n", displayName ? displayName : "NULL");
      }

      std::cout << "constructor successful." << std::endl;
   }

   ~Display()
   {
      std::cout << "destructor called." << std::endl;

      if (display)
      {
         XCloseDisplay(display);
      }
   }

private:
    ::Display* display;
};
}  // end namespace


int main(int argc, char** argv)
{
   const char* displayName = (argc > 1 ? argv[1] : NULL);

   Wrapper::Display display(displayName);

   return 0; // superfluous, but used to silence the lambs.
}

```
Note that I also avoid Hungarian Notation, and instead attempt to use descriptive names for my variables.  Of course, I couldn't think of a nifty name for the namespace.

---

### Post by worksofcraft on 2010-10-24
> **dwhitney67 said:**
> It works for me, but of course I used the version below.
```

// Nice tidy up :), but I won't duplicate it just to cut down on message size

```
Note that I also avoid Hungarian Notation, and instead attempt to use descriptive names for my variables.  Of course, I couldn't think of a nifty name for the namespace.

You mean you managed to open the display by explicit name? I'm hoping to experiment with connecting to X servers on virtual hosts but even after editing /etc/gdm/gdm.schemas I can't get beyond localhost:0.0 Anything else says "no protocol specified" :(

As for the restructuring, yes, name spaces are a good idea but I'm still a bit concerned about all the confusion with the same identifiers such as "Display" and "display" and Wrapper::display appearing and they might be class names or pointers to instances or numeric identifiers :confused: that's what I want to get away from.

p.s. oh... btw ever since I learned about internationalization, cout is out and formats are back in :)

---

### Post by dwhitney67 on 2010-10-25
> **worksofcraft said:**
> You mean you managed to open the display by explicit name? I'm hoping to experiment with connecting to X servers on virtual hosts but even after editing /etc/gdm/gdm.schemas I can't get beyond localhost:0.0 Anything else says "no protocol specified" :(

I did not bother to try opening a display other than one I currently *own*.

> **worksofcraft said:**
> 
... I'm still a bit concerned about all the confusion with the same identifiers such as "Display" and "display" and Wrapper::display appearing and they might be class names or pointers to instances or numeric identifiers :confused: that's what I want to get away from.

When I develop C++ (or Java or C) s/w, I see a clear distinction between *Display* and *display*.  The former represents a class/struct; the latter a mere variable.

If you are indeed interested in developing a wrapper around the X library, then the user's of this library extension should in theory never have to know anything about the details of Xlib's Display (actually _XDisplay); the user should only be aware of the interface that *you* present.

> **worksofcraft said:**
> 
p.s. oh... btw ever since I learned about internationalization, cout is out and formats are back in :)
No comment.

---

### Post by worksofcraft on 2010-10-25
> **dwhitney67 said:**
> 
When I develop C++ (or Java or C) s/w, I see a clear distinction between *Display* and *display*.  The former represents a class/struct; the latter a mere variable.

If you are indeed interested in developing a wrapper around the X library, then the user's of this library extension should in theory never have to know anything about the details of Xlib's Display (actually _XDisplay); the user should only be aware of the interface that *you* present.


Hum... well I have no desire to use Java and when I started programming I learnt Prolog. There names of all my variables start with a capital letter and all the clauses have lower case and that is compulsory and built into the language... (z0mg if only other languages could be so consistent and sensible).

Later when I learnt C there were ints and chars and floats and none of those types start in a capital letter. When programming with stuff like X library and glib that were written in 1980's, adopting a standard that relies on much more recent fashions in camel case and capitalization is going to fail where the original work does not conform.

Xlib uses names like Display and Screen, but these might be struct, or they might be pointers to structs or they might even just be an integer type used as identifiers for things known to the "server".

The "users" of my wrapper class, well "they" is "me" and the biggest problem I have is not how to use what I've done, but how to make sense of the bits I'm working on next :shock:

so anyway I decided I'm going to start all my variable names with a capital but just to please people who don't like that I'm going to stick a lowercase character on the front as follows

[LIST]
[*]p a pointer
[*]r a reference
[*]s a structure or class
[*]a an aggregate or array
[*]i a simple type (int/long/float/...)
[*]g a global/static variable
[*]z something that is dynamically allocated
[*]c a constant known at compile time
[/LIST]
and unlike the Hungarian I'm not going to combine them but just apply one depending on what I happen to think is most relevant ;)

---

### Post by dwhitney67 on 2010-10-25
> **worksofcraft said:**
> ...
so anyway I decided I'm going to start all my variable names with a capital but just to please people who don't like that I'm going to stick a lowercase character on the front as follows

[LIST]
[*]p a pointer
[*]r a reference
[*]s a structure or class
[*]a an aggregate or array
[*]i a simple type (int/long/float/...)
[*]g a global/static variable
[*]z something that is dynamically allocated
[*]c a constant known at compile time
[/LIST]
and unlike the Hungarian I'm not going to combine them but just apply one depending on what I happen to think is most relevant ;)

Bad idea!... but that is merely my opinion (and one that is shared by countless other individuals and organizations).  But do as you please.

---

### Post by worksofcraft on 2010-10-25
> **dwhitney67 said:**
> Bad idea!... but that is merely my opinion (and one that is shared by countless other individuals and organizations).  But do as you please.

Yes I will :)
When Hungarian became fashionable I thought it was just about the dumbest idea on the planet, however never "knock" something till you tried it they say and I never tried this... 

However I change the z to q just to keep all my pointer types together. In any case now all my instance identifiers willbe identified by names that start with a lower case letter and so they should  hence forth be fitting in the grand scheme of nonsensical standards that nobody knows where they come from but of which everybody fears to question the sense and sensibility too :shock:

---

### Post by dwhitney67 on 2010-10-25
I know exactly where programming "standards" come from... they come from s/w organizations that employ tens, hundreds, if not thousands, of s/w weenies, and they want each and every weenie to program in the same style.

Organizations may themselves have differing notions of standards, but one thing that obviously has stood out in the last decade, is that more and more of these organizations are abandoning the Hungarian Notation.  I believe it was M$ that brought this HN style to the limelight, and then after realizing their error, abandoned it too.  I guess they took the clue from the rest of the industry.

If you want to develop MFC-style code with the X library, do as you please.  But don't stare and wonder if other s/w developers shake their head when they see your code.

---

### Post by shakey on 2010-10-25
putting the variable type in the variable name is useless, you know that type it is already. Howver, if you use Hungarian notation as discussed [here]("http://blogs.msdn.com/b/ericlippert/archive/2003/09/12/52989.aspx"), then it becomes very useful.

---

### Post by worksofcraft on 2010-10-25
> **shakey said:**
> putting the variable type in the variable name is useless, you know that type it is already. Howver, if you use Hungarian notation as discussed [here]("http://blogs.msdn.com/b/ericlippert/archive/2003/09/12/52989.aspx"), then it becomes very useful.

Thanks for that link Shakey :)

That is indeed a useful way to use said notation and it shows how large scale adoption of standards without understanding of their intent has turned a good idea into a useless mess.

I was not looking for that level of detail. Just considering general operators like -> or . or [] and in particular to keep track items that must be memory managed i.e. disposed of in some way when no longer needed.

One problem I haven't really resolved is an indication where parameters passed by reference to a function are used to return results. In C++ the syntax can be indistinguishable from pass by value! Yet being able to see at a glance which ones are output parameters (without having to refer back to method declarations all the time) makes following the program logic much easier.

p.s. in X11 they seem to have adopted a convention of adding the suffix "_return" on the name, but evidently that only works inside the function and not in the code one is reading that uses those results.

---

### Post by worksofcraft on 2010-10-25
> **dwhitney67 said:**
> 
If you want to develop MFC-style code with the X library, do as you please.  But don't stare and wonder if other s/w developers shake their head when they see your code.

edit..

whatever, the real topic is: what is worth communicating.
Do I need to distinguish class names from variable identifiers and distinguish those from method and function names by some kind of capitalization convention?

I can tell which are which from the context... like functions have brackets on them and class names appear in declarations. e.g.
[php]
person Person = _person((person) people);
[/php]
even without a convention I can tell who is who ;)

---

