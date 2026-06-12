---
title: "class factory"
date: 2010-11-03
forum: Programming Talk
---

### Post by worksofcraft on 2010-11-03
Still trying to persuade C++ compilers to do what I want and not what I say... if only I knew how to say it :confused:
[php]
#include <cstdio>

struct base {
	int iD[1];

	static base factory() {
		base sThat;
		printf("constructing base at %p\n", &sThat);
		sThat.iD[0] = 0xBAD;
		return sThat;
	}
};

struct derived: base {
	// How do I get the base class factory to initialize the base of this class
	// directly instead of using a copy constructor ?
	derived(const base &rB): base(rB) {
		printf("constructed derived @%p\n", this);
	}
};

int main() {
	derived sD(base::factory());
	printf("&sD=%p, sizeof(sD)=%lx\n", (base *) &sD, sizeof(sD));
	return !printf("exits normally\n");
}
[/php]
... wrong again :(
```

$> g++ basefactory.cc
$> ./a.out
constructing base at 0x7fff84c24d10
constructed derived @0x7fff84c24d40
&sD=0x7fff84c24d40, sizeof(sD)=4
exits normally

```

---

### Post by nvteighen on 2010-11-04
Er... what is what you mean by "factory"? Just for you to know, my I understand that a class "factory" is one that dynamically creates an instance of something from somewhere else... usually a plugin handler or similar...

In Python (this is code from PycTacToe... GPLv3, (C) 2008-2010 Contributors):
```

class GameFactory(object):
    """Class to encapsulate game modules into an object."""
    
    def __init__(self, game_type):
        """Initiates a Game class. If it fails, it raises ImportError."""
        
        self.result = False

        module_name = "PTTGame_%s" % game_type
        exec "from pttgames.%s.%s import %s" % (game_type, game_type,
                                                module_name)
        exec "self.result = %s()" % module_name

```

I may be mistaken, of course... and using a name to mean something else than what you do.

---

### Post by worksofcraft on 2010-11-04
> **nvteighen said:**
> Er... what is what you mean by "factory"? Just for you to know, my I understand that a class "factory" is one that dynamically creates an instance of something from somewhere else... usually a plugin handler or similar...

In Python (this is code from PycTacToe... GPLv3, (C) 2008-2010 Contributors):
```

class GameFactory(object):
    """Class to encapsulate game modules into an object."""
    
    def __init__(self, game_type):
        """Initiates a Game class. If it fails, it raises ImportError."""
        
        self.result = False

        module_name = "PTTGame_%s" % game_type
        exec "from pttgames.%s.%s import %s" % (game_type, game_type,
                                                module_name)
        exec "self.result = %s()" % module_name

```

I may be mistaken, of course... and using a name to mean something else than what you do.

Hum... I thought you responded something about not changing the language the original poster is using... quite recently...

However that is exactly what my "factory" is supposed to do: it creates a new instance of the base class.... just I made it very simple in this case. I think I'll post the real thing in a moment so you can see whether or not it makes more sense then.

Not that long ago I posted about how [return by value can be used to initialize a new instance]("http://ubuntuforums.org/showthread.php?t=1589812") without having to run a copy constructor... so now I want my factory to initialize the base class component of my derived class in the same way.

---

### Post by worksofcraft on 2010-11-04
[php]
// 2D geometric transformation = 2x2 matrix + displacement
struct affine: coord {
	m2x2 sMatrix;
	// construct basic geometric transformations
	static affine rotate(double iAngle);
	static affine scale(double iScale); // enlarge
	static affine translate(double iX, double iY); // move

    // transform a coordinate pair
	coord operator * (const coord &rIn);
    // combine two transformations into one
	affine operator * (const affine &rIn);
}

// relying on return by value optimization you can use these to
// construct new affine instances without copying:
affine sShrinkMe = scale(0.3);
// or even...
affine sShrinkTwistAndMove = scale(0.3) * rotate(Pi/4.0) * translate(2.0, 7.5);
[/php]

OTOH if I made constructors that take a double then it is ambiguous if I want to make a rotation or a scaling.

Then the next step is I have classes that derive from affine and I want to initialize their affine component in the same way :popcorn:

---

### Post by dwhitney67 on 2010-11-04
> **worksofcraft said:**
> Hum... I thought you responded something about not changing the language the original poster is using... quite recently...

Agreed; if C++ is being discussed, it should be used in examples, unless pseudocode is used.

> **worksofcraft said:**
> 
However that is exactly what my "factory" is supposed to do: it creates a new instance of the base class.... just I made it very simple in this case. I think I'll post the real thing in a moment so you can see whether or not it makes more sense then.

If a factory is only supposed to produce one type of object, then one might ask what is the point of developing this factory.

If you require the factory to produce distinct objects (perhaps all sharing a common base class), then you will need to supply more information to the factory() method.

> **worksofcraft said:**
> 
Not that long ago I posted about how [return by value can be used to initialize a new instance]("http://ubuntuforums.org/showthread.php?t=1589812") without having to run a copy constructor... so now I want my factory to initialize the base class component of my derived class in the same way.
What of it?

Rather than let the compiler create a default constructor, a copy constructor, and an overloaded assignment method for you, why don't you start practicing developing these yourself.  Those that you do not want to be used can be declared as private, and of course you can choose whether to implement them or not. 

For example:
```

class Foo
{
public:
   Foo() {}

private:
   // declared, but not implemented.
   Foo(const Foo& other);
   Foo& operator=(const Foo& rhs);
};

```


P.S.  Please don't open a thread with one question, only to later back up, and change the question to something else in the thread.  Did you resolve the factory issue?

---

### Post by dwhitney67 on 2010-11-04
> **worksofcraft said:**
> 
Not that long ago I posted about how [return by value can be used to initialize a new instance]("http://ubuntuforums.org/showthread.php?t=1589812") without having to run a copy constructor... so now I want my factory to initialize the base class component of my derived class in the same way.

Testing a little further, I found that although the copy-constructor is not called, the compiler requires it to be available and publicly accessible.  So regardless of the fact that it is not called, it must be present.  Of course, as you are so fond of doing, you never declare, much less implement, a copy-constructor.

Look at this example; because the copy-constructor is declared private, the code will not compile.
```

#include <iostream>

class Foo
{
private:
   // this is never called, but must be made public!
   Foo(const Foo& other) : x(other.x) { std::cout << "Foo copy constructor called." << std::endl; }

public:
   static Foo factory()
   {
      Foo local;     // calls default constructor
      local.x = 5;
      return local;
   }

private:
   Foo() { std::cout << "Foo constructor called." << std::endl; }

   // declared, but not implemented.
   Foo& operator=(const Foo& other);

   int x;
};

int main()
{
   Foo f = Foo::factory();
}

```

---

### Post by nvteighen on 2010-11-04
> **worksofcraft said:**
> Hum... I thought you responded something about not changing the language the original poster is using... quite recently...


Yes, certainly my mistake and I apologize. I grabbed the first thing I found lying around... I can be quite stupid sometimes :D 

Ok, so, we're talking about the same thing, then.

I agree with dwhitney67 in that I don't quite see the point of a factory here if all you want is to construct a new instance of the same factory class. My Python example (ok, Python is dynamic and allows for some interesting tricks there) that allows the loading of any class whose name is "PTTGame_%s" (%s = whatever string). Ok, the dynamic name lookup is not what you want, but the ability of my class to return instances of different classes by retaining a base class somehow (which unifies the interface for ever possible returnable class).

So, all you need, at first is to write the "product-constructors" (IIRC, that's the name that's used) by respecting the factory-constructor's interface. It looks a lot to what you do in some "non-OOP" Lisp dialects such as Scheme, where you use a closure... well... you make your class to be an anonymous dispatch function that returns different data structures depending on what the arguments are, but as it is the same function, the interface is obviously respected... (Again, it seems I've been using these patterns for ages without knowing how they're called). Anyway, I've found this webpage that may clarify a bit what's the essence of a factory class (in C++ ;)): [http://sourcemaking.com/design_patterns/factory_method/cpp/1](http://sourcemaking.com/design_patterns/factory_method/cpp/1)

---

### Post by worksofcraft on 2010-11-04
> **dwhitney67 said:**
> 
If a factory is only supposed to produce one type of object, then one might ask what is the point of developing this factory.


I can't make two different constructors of the same class that take the same parameter(s) but produce different results but I can make two different static functions and assign their result.
[php]
    static affine rotate(double iAngle);
    static affine scale(double iScale); // enlarge
[/php]


> **dwhitney67 said:**
> 
Rather than let the compiler create a default constructor, a copy constructor, and an overloaded assignment method for you, why don't you start practicing developing these yourself.


... cuz in this case I can see nothing wrong with the default copy and assignment. Overloading this default behavior to do unusual things is likely to cause confusion for people who are used to the standard copy construction and assignment actions.

> **dwhitney67 said:**
> 
P.S.  Please don't open a thread with one question, only to later back up, and change the question to something else in the thread.  Did you resolve the factory issue?

If you look at my first post you should see that the factory issue is the same thing: Return by value from the "factory". In this case, instead of initializing a new instance of the same class I want it to initialize the base class component of a derived class.

It's a good thing I referred to that thread because it reminded me that I have to disguise my call to printf with a volatile function pointer, or the compiler won't do the optimization :shock:

anyway I better go read that link that nvteighen gave ...

---

### Post by dwhitney67 on 2010-11-04
Get this book; it discusses the Factory Design Pattern in depth.
[http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612](http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612)


A quote from the book itself...
> 
[A factory method] defines an interface for creating an object, but lets subclasses decide which class to instantiate.  Factory Method lets a class defer instantiation to subclasses.


Before I ever knew about the "Factory Method", I employed something similar to the following on a project which I supported over 10 years ago...
```

enum ProductID { SPROCKET, SCREW, NUT };

class Factory
{
public:
   static Product* create(ProductID id)
   {
      switch (id)
      {
         case SPROCKET: return new Sprocket;
         case SCREW:    return new Screw;
         case NUT:      return new Nut;
      }

      return 0;
   }
};

int main()
{
   Sprocket* sprocket = dynamic_cast<Sprocket*>(Factory::create(SPROCKET));
   Screw*    screw    = dynamic_cast<Screw*>(Factory::create(SCREW));
   Nut*      nut      = dynamic_cast<Nut*>(Factory::create(NUT));
   ...
}

```

Another approach is to templatize the factory such that specific instances of the factory can be defined.  For example:
```

template <class TheProduct>
class SpecificFactory
{
public:
   Product* create()
   {
      return new TheProduct;
   }
};

SpecificFactory<Sprocket> theSprocketFactory;
SpecificFactory<Screw>    theScrewFactory;
SpecificFactory<Nut>      theNutFactory;

int main()
{
   Sprocket* sprocket = dynamic_cast<Sprocket*>(theSprocketFactory.create());
   Screw*    screw    = dynamic_cast<Screw*>(theScrewFactory.create());
   Nut*      nut      = dynamic_cast<Nut*>(theNutFactory.create());
   ...
}

```


P.S.  For the examples above, the remaining code:
```

#include <cassert>

class Product
{
protected:
   Product() {}
   virtual ~Product() {}
};

class Sprocket : public Product
{
public:
   Sprocket() {}
};

class Screw : public Product
{
public:
   Screw() {}
};

class Nut : public Product
{
public:
   Nut() {}
};

```

---

### Post by worksofcraft on 2010-11-04
> **dwhitney67 said:**
> 
...


Thanks for that example code :)
It has made clear how to use it with polymorph objects and how to avoid having to add options to the factory
by using templates.

The link that nveighten gave is also very good but I do get concerned about the use of "new" especially where it suggests reusing existing ones.

It's going to be tricky to manage their allocation and dispose of them where I want to just put them in an expression. e.g. I apply a scale to a rotation to make a new "shrink and twist" transform. (The operation is just a 2x2 matrix multipliction producing a new 2x2 matrix).

Somehow my needs still seems different:

For instance, while my screen placement does derive from the base class affine transform, it doesn't change the way that base class operates in any way shape or form: It simply adds some extra things like color that I need for plotting shapes on the screen.

I think 'll have to experiment a bit more because I'm not so sure what I need now :confused:

---

### Post by dwhitney67 on 2010-11-04
> **worksofcraft said:**
> 
For instance, while my screen placement does derive from the base class affine transform, it doesn't change the way that base class operates in any way shape or form: It simply adds some extra things like color that I need for plotting shapes on the screen.

Well, that's generally the gist of inheritance.  A base class offers some functionality, and subclasses offer more.  If a subclass did not offer any additional functionality, then there really would be no point in defining it.

---

### Post by worksofcraft on 2010-11-04
> **dwhitney67 said:**
> Well, that's generally the gist of inheritance.  A base class offers some functionality, and subclasses offer more.  If a subclass did not offer any additional functionality, then there really would be no point in defining it.

I mean there are no virtual methods. It inherits teh functionality but never is there any need to use it in a polymorph context.

---

### Post by nvteighen on 2010-11-05
> **worksofcraft said:**
> 
The link that nveighten gave is also very good but I do get concerned about the use of "new" especially where it suggests reusing existing ones.


The link I gave you was to show the concept rather than a particular implementation. I'm pretty aware that the way they show it there is not the best way to do it. I really prefer the template-based way or, if this were Lisp (or C++0x?), a closure-based one.

The way I see this is that this kind of patterns is conceptual, not implementational. What you want is a "factory" that creates several "products"... that's what the Factory Pattern is... Now, there are several ways to achieve that effect.

So, yes, the implementation shown there may be suboptimal, but I think it shows the concept in a very clear fashion.

> 
Somehow my needs still seems different:

For instance, while my screen placement does derive from the base class affine transform, it doesn't change the way that base class operates in any way shape or form: It simply adds some extra things like color that I need for plotting shapes on the screen.

Hm... I'd like to see your most updated code. From what you've shown us, I tend to think a simple class that internally updates the matrix would seem simpler and more effective. But I do recongnize I'm getting half (or even less) of what you want to do, so I may be wrong.

---

### Post by worksofcraft on 2010-11-05
> **nvteighen said:**
> 
Hm... I'd like to see your most updated code. From what you've shown us, I tend to think a simple class that internally updates the matrix would seem simpler and more effective. But I do recongnize I'm getting half (or even less) of what you want to do, so I may be wrong.

There is quite a lot of code now. Like...
[php]
// Two dimensional (2D) coordinate
// note: I'm avoiding the word "vector" to avoid confusion with said
// STL container template, but consider "coord" as synonymous with 2D vector.
struct coord {
	vnum x, y; // vector coordinates
	coord(vnum X, vnum Y): x(X), y(Y) {}

	// coordinate addition
	coord & operator += (const coord &rIn) { x += rIn.x; y += rIn.y; return *this; }
	coord & operator -= (const coord &rIn) { x -= rIn.x; y -= rIn.y; return *this; }
	// coordinate magnitude.
	vnum abs() {
		// uses rounding when type is integer
		// note: float would lose precision as int and float are same size
		return m2v(sqrt(x*double(x) + y*double(y)) );
	}
	int angle() { return rad2bfPi(atan2((double) y, (double) x)); }
};

// 2x2 matrix
struct m2x2 {
	mnum xx, xy, yx, yy;

	m2x2(mnum iXX, mnum iXY, mnum iYX, mnum iYY): xx(iXX), xy(iXY), yx(iYX), yy(iYY) {}
	// to be useable on self, must use a copy, hence return by value!
	m2x2 operator*(const m2x2 &);
	// transform a coordinate
	coord operator*(const coord &);
	// area
	mnum det() const { return xx * yy - xy * yx; }
	// inverse matrix
	m2x2 inv();
};

// 2D geometric transformation = 2x2 matrix + displacement
struct affine: coord {
	m2x2 sMatrix;
	// construct matrix for basic transformations
	static affine rotate(unsigned iAngle); // Binary fractions of Pi
	static affine scale(mnum iScale); // enlarge
	static affine translate(vnum iX, vnum iY);

	affine(mnum iXX, mnum iXY, mnum iYX, mnum iYY, vnum X = 0, vnum Y = 0):
		coord(X, Y), sMatrix(iXX, iXY, iYX, iYY) {
	}
	affine(const m2x2 &rIn, vnum X = 0, vnum Y = 0):
		coord(X, Y), sMatrix(rIn) {
	}

	coord operator * (const coord &rIn);
	affine operator * (const affine &rIn);
	affine operator + (const coord &rIn);

	// for diagnostics, display my parameters
	void show(const char *) const;
};
[/php]

and that's just the header file for the 2D stuff.
Note vnum and mnum can be typedef'ed to be double or float or int on my Amd quad core double is best.
Anyway then I go on to use it:
[php]


// the screen placement of a shape consists of an affine transform
// to convert the shape's coordinates to screen coordinates.
// These are used by the iterator that does the drawing
struct screenplacement: cs_link, affine {
	//TODO: default place center of window and make y go up instead of down
	screenplacement(graphplacement *pEdge, const affine &rAf = translate(200, 150)):
		cs_link(*pEdge), affine(rAf) {
	} 
	// double vtable dispatch: each cs_graph defines it's own method of
	// "visiting" and each shape has it's own methods for such visits
	virtual bool visit() {
		shape *pShape = CAST(shape, &rEdge.rNode);
		assert(pShape);
		return pShape->draw_me(*this);
	}
};
[/php]
The above ones are calculated by combining relative transforms of shapes within shapes and then an optional dynamic relative movement. That way when actually generating the drawing it only has one transformation to do for each point.

There are other affine class derivatives to place things relative to each other and I need to change movement because erasing the whole thing then redrawing it makes the image strobe...

p.s. I just realized the best way to do movement is to "[double buffer]("http://en.wikipedia.org/wiki/Multiple_buffering")" the image :)
i.e. you toggle between two off-screen images: one being painted and the other being transferred to the screen. (Thus it will have no effect on the affine transformation classes)

---

### Post by worksofcraft on 2010-11-05
Thanks for the input Guys :)
I think I got this one solved for now... may need to revisit it when I add capability to [read the actual data structure from XML]("http://ubuntuforums.org/showthread.php?t=1613894") definition... but as you can see, that is already another thread.

So I also decided my target application will be a schematic capture system for which I just created a project google code named [schematrix]("http://code.google.com/p/schematrix/")
but it's only in it's infancy and I'm working on other things too :popcorn:

---

