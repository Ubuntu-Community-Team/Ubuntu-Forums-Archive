---
title: "[C++] Pointers and encapsulation concept"
date: 2010-11-28
forum: Programming Talk
---

### Post by dawwin on 2010-11-28
I know, it's bad idea to do something like this
```

class example
{
    int a;
    int b;
    void fnc();
}

```Because it's not okay with encapsulation concept.
But how about this
```

class example
{
  private:
    int a;
    int b;

  public:
    void fnc();
}

void example::fnc()
{
    example2 abc;
    abc.fun(&this->a);
}

```In this example method named fun(), which is part of class example2 can modify private variable of example class. Isn't it in conflict with encapsulation concept?

---

### Post by MadCow108 on 2010-11-28
in this case not really as example request example2 to modify the variable.
This is ok as long as example2 has no side effects which screw up example's state at later time.
As fnc is part of example and it is not const one can expect fnc to change its internal state in the call.

This would be a better example of what one should not do:
```

class A { 
  int a;
  public:
  int * r() { return &a; }
};

```

here one exports a pointer to a private variable to the outside world, which allows it to be modified.
This should not be done as the class can never again rely that its state is consistent.
If one wants to do that one should return pointers to const (and hope the programmers don't const_cast it ;) ).

---

### Post by nvteighen on 2010-11-28
> **dawwin said:**
> I know, it's bad idea to do something like this
```

class example
{
    int a;
    int b;
    void fnc();
}

```Because it's not okay with encapsulation concept.


No, actually, not specifying any access permission makes C++ use "private" as default...

> 
But how about this
```

class example
{
  private:
    int a;
    int b;

  public:
    void fnc();
}

void example::fnc()
{
    example2 abc;
    abc.fun(&this->a);
}

```In this example method named fun(), which is part of class example2 can modify private variable of example class. Isn't it in conflict with encapsulation concept?

My sir, you've encountered a very fishy reality of C++... There's no runtime encapsulation, only compile-time. private/protected only hide a member from compile-time access via the member syntax (example.a) so that the compiler can enforce the class's interface, but as soon as you use an indirection device like a pointer, which is resolved at runtime (a pointer can point to any memory address...), the whole thing is completely unprotected, as you've seen for sure when executing that code.

---

### Post by worksofcraft on 2010-11-28
The question is why you want to make things private/protected in the first place. Just who are you protecting it from?

Some people try to restrict access to everything because they can't see a reason anyone would want to access them. It's what I refer to as the bureaucrat methodology.

Other high level languages like Python seem to get along just fine with hardly any access authorization mechanisms. In my C++ programs I do likewise and only declare things protected/private if there are reasons to do so.

Typically private/protected is useful for things like to prevent accidental copy construction and type conversions or where there is a relationship between different members that must be maintained and so it is best to access them by using the appropriate methods of the class.

---

### Post by nvteighen on 2010-11-29
> **worksofcraft said:**
> 
Some people try to restrict access to everything because they can't see a reason anyone would want to access them. It's what I refer to as the bureaucrat methodology.


Nice name! May I use it in future posts? :D

> 
Other high level languages like Python seem to get along just fine with hardly any access authorization mechanisms. In my C++ programs I do likewise and only declare things protected/private if there are reasons to do so.

Typically private/protected is useful for things like to prevent accidental copy construction and type conversions or where there is a relationship between different members that must be maintained and so it is best to access them by using the appropriate methods of the class.

Yeah, worksofcraft is right: private/protected isn't as needed as they seem at first.

Please understand that 80% of what C++ does is just to give the compiler the ability to enforce the API. In Python you declare everything as public (well, there's that mangling system, but uh... it doesn't work well) and expect the library user to be intelligent enough to read the API docs... but not preventing stupid behaivor, as that could also prevent a smart solution the original developer(s) didn't plan.

It's not that having the compiler enforce the interface is a bad thing; static-typing is the price you have to pay for the execution speed a dynamic environment doesn't have. But that's all about it. As soon as your program is executed, all the computer knows is that there's data in memory, accessable just because the program knows the offsets to apply for accessing it (that's where static-typing comes in: types are actually defined by their size).

Of course, there are situations where forcing the user to do some things in some particular way may be useful and private/protected may be the way to force this in C++ (or Java, for instance).

---

### Post by Arndt on 2010-11-29
> **nvteighen said:**
> No, actually, not specifying any access permission makes C++ use "private" as default...



My sir, you've encountered a very fishy reality of C++... There's no runtime encapsulation, only compile-time. private/protected only hide a member from compile-time access via the member syntax (example.a) so that the compiler can enforce the class's interface, but as soon as you use an indirection device like a pointer, which is resolved at runtime (a pointer can point to any memory address...), the whole thing is completely unprotected, as you've seen for sure when executing that code.

I wouldn't call this fishy. How could it work otherwise? The class's own code, which is allowed to reference all private members, can decide to let a pointer to a private member out, and send it to a function not in the class.

---

### Post by nvteighen on 2010-11-29
> **Arndt said:**
> I wouldn't call this fishy. How could it work otherwise? The class's own code, which is allowed to reference all private members, can decide to let a pointer to a private member out, and send it to a function not in the class.

It isn't fishy if you know how C++ classes work. But a lot of people like the OP really think "private" is something that will prevent any access to data marked as such also at runtime and that they call that to be encapsulation. 

I know the example given by the OP can be considered a kind of "delegation" where the class "allows" an external function to work this way, but if it was production code one could start asking why the data is private.

(Of course, this is much better than using C++ friendship, which makes all private/protected stuff available for a function marked as such, without any further specification)

---

### Post by worksofcraft on 2010-11-29
> **nvteighen said:**
> Nice name! May I use it in future posts? :D


TY, yes you can :)
and specially for those who would like to rubber stamp all appropriately authorized data access... here is a little something to give them nightmares:
[php]
// g++ -Wall -pedantic private.cpp
#include <cstdio>
#include <string>

class bureaucrats_nightmare {
private:
	std::string aPrivate;
public:
	std::string aPublic;
	bureaucrats_nightmare(const char *pBS, const char *pCS = "Closet Skeleton"):
		aPrivate(pCS), aPublic(pBS) {
	}
};

void paperazzo(const bureaucrats_nightmare &rBC) {
	printf("extra... extra... read all about bureaucrat's nightmare:\n");
	printf("behind %s we find %s!!!\n",
		rBC.aPublic.c_str(), (&rBC.aPublic)[-1].c_str()
	);
}

int main() {
	bureaucrats_nightmare sBC("Phoney Public Facade");
	paperazzo(sBC);

	return 0xF0UL;
}
[/php]

... for those who don't want to type ./a.out at a command line... the output is:
```

extra... extra... read all about bureaucrat's nightmare:
behind Phoney Public Facade we find Closet Skeleton!!!

```
... and the [paperazzo]("http://en.wikipedia.org/wiki/Paparazzi") got it all from the public member! :shock:
:D

---

### Post by TheBuzzSaw on 2010-11-29
I am interested in seeing this particular scenario in its original context. It would help better diagnose the design.

There is more to object-oriented programming than making all member variables private and forcing the programmer to work through "obnoxious" member functions. The following class should raise several red flags:

[php]
class MyObject
{
    int mData;

public:
    void setData(int inData) { mData = inData; }
    int getData() { return mData; }
};
[/php]

The object should have a higher level objective (no pun intended). If you find that private member access often "gets in your way", I submit that the class might be poorly designed.

---

### Post by dwhitney67 on 2010-11-29
> **TheBuzzSaw said:**
> If you find that private member access often "gets in your way", I submit that the class might be poorly designed.
Design?  Are you kidding?  This is the Ubuntu Programming Forum; I've yet to see anyone design any of their code prior to implementing it!

If everyone would design their application with care, this forum would be "out of business", except for the newbies who rather learn through the web rather than reading through an ol' fashioned book.

---

### Post by worksofcraft on 2010-12-03
ATM I'm studying the code for anti-grain geometry library and so far it's been real eye opener in programming for me...
However while I let some of it sink in thought I would just share this one:
[php]
template<class Interpolator, class Distortion>
class span_interpolator_adaptor : public Interpolator {
public:
// ... loads of bits elided

	// accessor getting pointer to the distortion object
	const distortion_type& distortion() const {
		return *m_distortion;
	}

	// accessor setting a new distortion member
	void distortion(const distortion_type& dist) {
		m_distortion = dist;
	}
// ... then finally at the very end:
private:
         const distortion_type* m_distortion;
};
[/php]
Declaring it as a class (instead of a struct) and then immediately declaring everything as public also just seems to me like the programmer was being indecisive, but skipping on to the private member:

My view is that this technique of having private members with accessors to get them and another to set them, actually makes very little sense: I do wonder just what purpose this "encapsulation" can serve?
The only reason I can think of atm, is if perhaps there were an expected interface that it must conform to.

... but then I would expect them to be declared as virtual methods of a common base class. That IMO isn't going to be very effective in this case where the base class is a template parameter :shock:

---

### Post by nvteighen on 2010-12-03
> **worksofcraft said:**
> ATM I'm studying the code for anti-grain geometry library and so far it's been real eye opener in programming for me...
However while I let some of it sink in thought I would just share this one:
[php]
template<class Interpolator, class Distortion>
class span_interpolator_adaptor : public Interpolator {
public:
// ... loads of bits elided

	// accessor getting pointer to the distortion object
	const distortion_type& distortion() const {
		return *m_distortion;
	}

	// accessor setting a new distortion member
	void distortion(const distortion_type& dist) {
		m_distortion = dist;
	}
// ... then finally at the very end:
private:
         const distortion_type* m_distortion;
};
[/php]
Declaring it as a class (instead of a struct) and then immediately declaring everything as public also just seems to me like the programmer was being indecisive, but skipping on to the private member:

My view is that this technique of having private members with accessors to get them and another to set them, actually makes very little sense: I do wonder just what purpose this "encapsulation" can serve?
The only reason I can think of atm, is if perhaps there were an expected interface that it must conform to.

... but then I would expect them to be declared as virtual methods of a common base class. That IMO isn't going to be very effective in this case where the base class is a template parameter :shock:

I'd call it bad design, no matter whether there is an interface protocol or not. That member set as private is effectively made public by using getters and setters... The only thing you're doing there is to force a bit more type-safety, but nothing else.

---

### Post by worksofcraft on 2010-12-04
> **nvteighen said:**
> I'd call it bad design, no matter whether there is an interface protocol or not. That member set as private is effectively made public by using getters and setters... The only thing you're doing there is to force a bit more type-safety, but nothing else.

:) people agree with my POV :)

Well here is some more:
[php]
// these are dumb IMO
    //-----------------------------------------------------------------is_stop
    inline bool is_stop(unsigned c)
    { 
        return c == path_cmd_stop;
    }

    //--------------------------------------------------------------is_move_to
    inline bool is_move_to(unsigned c)
    {
        return c == path_cmd_move_to;
    }

    //--------------------------------------------------------------is_line_to
    inline bool is_line_to(unsigned c)
    {
        return c == path_cmd_line_to;
    }

    //----------------------------------------------------------------is_curve
    inline bool is_curve(unsigned c)
    {
        return c == path_cmd_curve3 || c == path_cmd_curve4;
    }

    //---------------------------------------------------------------is_curve3
    inline bool is_curve3(unsigned c)
    {
        return c == path_cmd_curve3;
    }

    //---------------------------------------------------------------is_curve4
    inline bool is_curve4(unsigned c)
    {
        return c == path_cmd_curve4;
    }
[/php]
What in cyber-space motivates someone to write code like that I wonder? Do they think others can program a simple comparison for equality?
... and the comments... do they actually explain anything we couldn't learn from the code? It's just the sort of thing one forgets to update :shock:

---

### Post by CptPicard on 2010-12-04
> **nvteighen said:**
> I'd call it bad design, no matter whether there is an interface protocol or not. That member set as private is effectively made public by using getters and setters... The only thing you're doing there is to force a bit more type-safety, but nothing else.

Pardon if I don't quite get the context of this issue, I spent all of 30 seconds looking at the situation, but the getter/setter pattern with actual data being private is a very common pattern. For example in Java you rarely, if ever, see actual data members of an object being set directly; I suppose C++ has similar best-practices.

Ruby takes this to the extreme; all data access is through responding to get/set messages (think Smalltalk-ish OOP).

The idea is of course that the getters and setters work as the interface to whatever actually implements the storage. The getter/setter can also easily include other code without requiring changes to the callers.

---

### Post by nvteighen on 2010-12-04
> **CptPicard said:**
> Pardon if I don't quite get the context of this issue, I spent all of 30 seconds looking at the situation, but the getter/setter pattern with actual data being private is a very common pattern. For example in Java you rarely, if ever, see actual data members of an object being set directly; I suppose C++ has similar best-practices.

Ruby takes this to the extreme; all data access is through responding to get/set messages (think Smalltalk-ish OOP).

The idea is of course that the getters and setters work as the interface to whatever actually implements the storage. The getter/setter can also easily include other code without requiring changes to the callers.

I meant it was bad design when setting and getting is as trivial as assigning a value or getting it, like in worksofcraft's example. If memory allocation, computations or anything else is needed to do this correctly, then the setters/getters would be necessary... (in CLOS, a :before method could me used :P)

---

### Post by CptPicard on 2010-12-04
> **nvteighen said:**
> I meant it was bad design when setting and getting is as trivial as assigning a value or getting it, like in worksofcraft's example.

How can you tell that in the future it is not a trivial assignment? At least in Java directly accessing members is considered just plain bad style; in C++ I've carried over the habit so you'd see me doing exactly what is in the example...

---

### Post by SledgeHammer_999 on 2010-12-04
I just want to add to this, that Gtk/glib(and maybe gstreamer) for at least a year now, have been introducing setters/getters to the API and deprecating old methods by fordiding direct access to variables from the public API(they use the G_SEAL macro to enforce this).

I don't know if this is good or bad practice, I just wanted to post it.

---

### Post by TheBuzzSaw on 2010-12-04
> **CptPicard said:**
> How can you tell that in the future it is not a trivial assignment? At least in Java directly accessing members is considered just plain bad style; in C++ I've carried over the habit so you'd see me doing exactly what is in the example...

Generally, you are correct. I believe the point nvteighen was making is that lots of programmers use that kind of pattern inappropriately. If you foresee the set/get being made more complicated later on, it makes a lot of sense to have a setter/getter anyway. It's just that, in many cases, people have the belief that the raw data being shielded by nothing but a logic-free pass-thru setter/getter constitutes "object-oriented programming".

---

### Post by worksofcraft on 2010-12-04
> **CptPicard said:**
> 
The idea is of course that the getters and setters work as the interface to whatever actually implements the storage. The getter/setter can also easily include other code without requiring changes to the callers.

In some situations that makes perfect sense and in others it is not.

Say you have an object that has an "is_visible: flag. You turn the flag on with an accessor and that not only turns on the flag but also causes the item to be drawn: It isn't just an accessor.

OTOH say you have a class that represents a vertex and it contains an x coordinate and a y coordinate... would you really want to use a "get_x()", "set_x()", get_y()" and "set_y()" accessor?

However back to the case mentioned.
It is a template class contained in it's own header file of 87 lines of code.
The **ONLY** thing it does, besides having constructors and accessors for said pointer to a distortion class instance is...
[php]
	// the important bit: converts to distorted coordinate system
	void coordinates(int* x, int* y) const {
		// get the interpolated coordinates
		base_type::coordinates(x, y);
		// distort them
		m_distortion->calculate(x, y);
	}
[/php]
Note: This code is mostly uncommented and there is no documentation to tell me what span_interpolator_adaptors are supposed to do, or how to use them, so the comments you see there are from what I'm trying to work out.

Now I do suspect they used a template instead of making coordinates() as a virtual method of the Interpolator base class because they don't want the overhead of a virtual method indirection through the v-tables on each access to coordinates of vertices.

However the distortion member type is a template parameter. Consequently you can't simply change one distorter instance for another: They have to be the very same type. In my own test program the coordinates method of my distorter didn't even need an instance as it's function was fully determined by it's type.

A different kind of distortion would expand to a different class of span_interpolator_adaptor and it's internal distortion object pointer shouldn't ever need to be accessed from outside the class.

As a side note: IMO simply using the two lines...
[php]
		base_type::coordinates(x, y);
		m_distortion->calculate(x, y);
[/php]

... would have produced far more intelligible code than we get from including the 87 lines of encapsulating adaptor template with member accessors.

---

### Post by saulgoode on 2010-12-05
> **worksofcraft said:**
> OTOH say you have a class that represents a vertex and it contains an x coordinate and a y coordinate... would you really want to use a "get_x()", "set_x()", get_y()" and "set_y()" accessor?
If you are writing a library then, yes, one might really want to use proper functions instead of direct access to fields in data structures. This makes writing language bindings much simpler, more portable, and less susceptible to compile options. To this end, even macros are a bad idea.

---

### Post by worksofcraft on 2010-12-05
> **saulgoode said:**
> If you are writing a library then, yes, one might really want to use proper functions instead of direct access to fields in data structures. This makes writing language bindings much simpler, more portable, and less susceptible to compile options. To this end, even macros are a bad idea.

Computer programming has the concepts of "data" and of "algorithms". One contains values and the other represents sequences of instructions.

Also in object oriented programming your objects still have data fields to hold values and methods to perform algorithms. I don't think disguising your data with accessor methods is actually that clever.

As for encapsulation, the point is to hide implementation details that you don't need to be concerned with so providing methods to hack at the values of these internals is a sure sign of a failed design IMO.

---

### Post by saulgoode on 2010-12-05
> **worksofcraft said:**
> Also in object oriented programming your objects still have data fields to hold values and methods to perform algorithms. I don't think disguising your data with accessor methods is actually that clever.

As for encapsulation, the point is to hide implementation details that you don't need to be concerned with so providing methods to hack at the values of these internals is a sure sign of a failed design IMO.

Say I've written a library which maintains and employs the following data structure:

```
extern struct {
  int x, y;
  short width, height;
  double thickness;
  struct *pattern;
} path;

```

Since I don't wish to seem unclever, I don't provide any accessor functions to the fields. It is ever so obvious that the value of '*width*' is '*path.width*' -- it would be dumb to provide a '*set_width*' function, or a '*get_width*'. 

Your mission (should you choose to accept it) is to write a program in Python... or Lisp, or Perl, or whatever ... which interfaces with my library; retrieving the value of *path*'s *width*, incrementing it, and then setting it to the new value.

---

### Post by nvteighen on 2010-12-05
> **CptPicard said:**
> How can you tell that in the future it is not a trivial assignment? At least in Java directly accessing members is considered just plain bad style; in C++ I've carried over the habit so you'd see me doing exactly what is in the example...

Good point. It's about API stability in languages where member access is done in a different way than method execution... languages like Common Lisp or Smalltalk-like won't suffer any of this because they unify everything into a single access way, be it CLOS methods or Smalltalk-like messages.

I think I've learned something from you again :)

---

### Post by CptPicard on 2010-12-05
> **worksofcraft said:**
> Computer programming has the concepts of "data" and of "algorithms". One contains values and the other represents sequences of instructions.

I need to point out that things can get interesting when one tries to do away with the distinction. After all, even our instructions are just bits in memory; and Lisp is all about "code being data" on a higher level; program execution is data structure evaluation.

> 
Also in object oriented programming your objects still have data fields to hold values and methods to perform algorithms. I don't think disguising your data with accessor methods is actually that clever.

In "pure" OOP, everything happens just through "objects responding to messages". I personally have a soft spot for such consistency and minimalism of ideas; it does not really matter to the caller where the response to a message comes from; internally there may be a data field. Or there may not.

> 
As for encapsulation, the point is to hide implementation details that you don't need to be concerned with so providing methods to hack at the values of these internals is a sure sign of a failed design IMO.

Turn it around and think of it this way: What you can call on an object represents its external interface. If for some given X you want to get and set it and that is part of what you want to do with that object, then fine; the internal implementation of X can be just a field if that suffices.

However, you shouldn't just expose every data item through accessors; if X itself is an implementation detail of some other functionality of the object, then exposing X directly for manipulation is probably wrong design and the getters and setters should not be in the interface.

---

### Post by TheBuzzSaw on 2010-12-05
Well, I think the discussion has moved a bit too far into abstract territory. Frankly, certain data structures have no choice but to essentially expose all of its private components (such as a matrix or 3D vector) because all the programmer cares about *is* the private data. My matrix class, for example, has so much exposed to the point where I am considering switching to the paradigm others use: simply having a 16-element array (it's a fixed 4x4 matrix) and switching all the member functions to external 'helper' functions. One could argue that it was never meant to be an object in the first place; I felt it should be.

Meanwhile, in other "ideally designed" objects, you generally don't know (or care) what private member variables exist (barring the fact that you were the one that created it). All you care about is that the object does its job. The STL is a good example. The string's length member function is a getter, but there is no setter for it. That would be silly! Does that function return a variable's value? Or does it do a fresh count? It doesn't really "matter". The user of the object just wants the length of the string.

Again, if you have an omnipowerful setter and getter for a private member variable, there had better be a good reason...

---

### Post by CptPicard on 2010-12-05
> **TheBuzzSaw said:**
> 
Again, if you have an omnipowerful setter and getter for a private member variable, there had better be a good reason...

How do you feel about the view that the getter and setter are what the object does; the private member variable just is the implementation, if that suffices?

---

### Post by TheBuzzSaw on 2010-12-05
> **CptPicard said:**
> How do you feel about the view that the getter and setter are what the object does; the private member variable just is the implementation, if that suffices?

Well, that's the whole dilemma right there. In the case of my matrix class, the private data essentially *is* the object. If anything, the class is more of a wrapper than the design for an actual distinct object. However, with other kinds of objects, you have to ask *why* you have almost unrestricted access to the data.

Perhaps give me an example of what you are describing.

---

### Post by worksofcraft on 2010-12-05
> **saulgoode said:**
> Say I've written a library which maintains and employs the following data structure:

```
extern struct {
  int x, y;
  short width, height;
  double thickness;
  struct *pattern;
} path;

```

Since I don't wish to seem unclever, I don't provide any accessor functions to the fields. It is ever so obvious that the value of '*width*' is '*path.width*' -- it would be dumb to provide a '*set_width*' function, or a '*get_width*'. 

Your mission (should you choose to accept it) is to write a program in Python... or Lisp, or Perl, or whatever ... which interfaces with my library; retrieving the value of *path*'s *width*, incrementing it, and then setting it to the new value.

In the past I've had absolutely **no problems** interfacing Borland **Prolog** with Borland C++ and even with Microsoft visual C. The linker was quite happy linking things defined in one language with ones defined in the other as long as I suppressed the name mangling that assists type safety at link time.

Your problem would appear to be not with C++ but with your interpreted language and I'm sure each and every one of those has it's own idiosyncrasies and guide lines for interfacing code written in other languages... probably platform dependent too.

From what you write it suggests you are dealing with one that is unable to recognize raw data items and needs mediation from genuine (not inline) function calls to get, or set them.

Instead of lumping all this baggage into your neat, intelligible  and efficient library base classes you should consider creating a separate interface that is appropriate to your target language. You might even consider inheritance:

[php]
struct path_glue: path {
	int get_x() { return x; }
	void set_x(int new_x) { x = new_x; }

	int get_y() { return y; } 
	//... etcetera
};
[/php]

Then you can use your interface when you need to interface to your interpreted language... and you won't seem "unclever" at all.

OTOH attempting to make universal classes that support every conceivable facility built in at the base level produces what is commonly known as "code bloat" and often not very easy to follow or maintain.

---

