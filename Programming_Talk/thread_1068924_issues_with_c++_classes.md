---
title: "issues with c++ classes"
date: 2009-02-13
forum: Programming Talk
---

### Post by cguy on 2009-02-13
I have 3 classes: A,B, and C. Each constructor takes parameters.
The constructors of B and C take integers as parameters.

The constructor of A takes 3 parameters:
A :: A ( B one, B two, C three ) {
...
}

Compiling the test module gives the errors:
 undefined reference to `B::B()'
 undefined reference to `B::B()'
 undefined reference to `C::C()'

but I already provided default constructors.

Solutions?

---

### Post by Zugzwang on 2009-02-13
You are mixing something up. The following code compiles well:

[PHP]
class B {
    B(int a);
};

class C {
    C(int a);
};

class A {
    A( B one, B two, C three );
 
};


A :: A ( B one, B two, C three ) {

}


int main() {
    return 0;
}
[/PHP]

---

### Post by era86 on 2009-02-13
Recheck your constructors and see if you are overloading any of them?  Show us an example of your class implementations.

---

### Post by cguy on 2009-02-13
[PHP]class colored_triangle_surface {
	private:
	coordinates fstPoint , sndPoint , trdPoint ;
	color surface_color ;
	public:
	colored_triangle_surface ( ) ;
	colored_triangle_surface ( coordinates, coordinates, coordinates, color ) ;[/PHP]

[PHP]class coordinates {
	private:
	GLfloat Xcoord, Ycoord, Zcoord ;
	public:
	coordinates ( ) ;
	coordinates ( GLfloat Xc, GLfloat Yc, GLfloat Zc ) { Xcoord = Xc ; Ycoord = Yc ; Zcoord = Zc ; } ;[/PHP]

[PHP]class color {
	private:
	GLfloat R, G, B ;
	protected:
	int validate_color ( GLfloat C ) ;
	public:
	color ( ) ;
	color ( GLfloat RED, GLfloat GREEN, GLfloat BLUE) ;[/PHP]

test.cpp
[PHP]coordinates co1 ( 1.0f, 1.5f, 0.0f ), co2 ( 1.0f, 1.0f, 0.0f ), co3 ( 0.0f, 0.0f, 0.0f ) ;
color col1 (1.0f, 1.0f, 1.0f) ;
colored_triangle_surface Surf1 ( co1, co2, co3, col1 ) ;[/PHP]


[PHP]/tmp/ccvWFQXH.o: In function `colored_triangle_surface::colored_triangle_surface(coordinates, coordinates, coordinates, color)':
test.cpp:(.text+0x4df): undefined reference to `coordinates::coordinates()'
test.cpp:(.text+0x4ed): undefined reference to `coordinates::coordinates()'
test.cpp:(.text+0x4fb): undefined reference to `coordinates::coordinates()'
test.cpp:(.text+0x509): undefined reference to `color::color()'
/tmp/ccvWFQXH.o: In function `colored_triangle_surface::colored_triangle_surface(coordinates, coordinates, coordinates, color)':
test.cpp:(.text+0x6cb): undefined reference to `coordinates::coordinates()'
test.cpp:(.text+0x6d9): undefined reference to `coordinates::coordinates()'
test.cpp:(.text+0x6e7): undefined reference to `coordinates::coordinates()'
test.cpp:(.text+0x6f5): undefined reference to `color::color()'
collect2: ld returned 1 exit status
[/PHP]

---

### Post by cguy on 2009-02-13
Can anyone spot the problem?

Using C++ proves to be a nuisance, so I may go back to C... Should I start rewritingall the code in C? Where is the freakin problem here?

(sorry, I am frustrated)

---

### Post by dwhitney67 on 2009-02-13
You didn't present any of the implementation of your class definitions; thus I am going to assume that either:

1)  You did not implement them, or

2)  You failed to link the modules containing the code with your test.cpp code.

Either way, this is not a C++ issue; the same would occur in all languages!

Btw, a couple of comments... the first constructive, the second not so...

1)  Pass objects by reference whenever possible; since you are already creating local objects (on the stack) in test.cpp, just use these same objects in your class.  If you need distinct objects, then consider allocating the objects rather than declaring them on the stack.

2)  Your coding style is piss-poor.  Consider following this style guide; it will help make your code more readable, and follow typical industry standards.

a)  Start class names with an uppercase letter.
b)  For class member data, affix either an "m_" or "_" to the variable names.  This will help distinguish the local variables from the class variables.
c)  Begin method names with a lowercase letter.
d)  Begin variable names with a lowercase letter.

In the end, stay consistent.  But seriously, your code is difficult to read.  It's no wonder you are having trouble programming.

---

### Post by doojsdad on 2009-02-13
Can you show how you actually implemented the classes, please? Give some context.

---

### Post by dwhitney67 on 2009-02-13
> **Zugzwang said:**
> You are mixing something up. The following code compiles well:

[PHP]
class B {
    B(int a);
};

class C {
    C(int a);
};

class A {
    A( B one, B two, C three );
 
};


A :: A ( B one, B two, C three ) {

}


int main() {
    return 0;
}
[/PHP]

Be careful when posting code in haste!  The code above does not compile because the constructors in each of the classes is private.

Also be aware that for simple classes, it is ok to depend on the compiler to create the copy-constructor, but for more elaborate classes that retain pointers to data, it is best to implement the copy-constructor.

The code above is depending on the compiler-generated copy-constructor.

---

### Post by cguy on 2009-02-13
Here is the whole code I try to compile.

Linked libraries: GL, GLU, glut

---

### Post by SledgeHammer_999 on 2009-02-13
In the prototype of class "colored_triangle_surface" in **colored_triangle_surface.h** in the second constructor you have forgotten to assign a variable(?) to the type; What I mean is this. Your prototype is:
```
colored_triangle_surface ( coordinates, coordinates, coordinates, color ) ;
```

It should be:
```

colored_triangle_surface ( coordinates C1, coordinates C2, coordinates C3, color Co) ;
```

NOTE: I didn't compile your code so I don't know if this is actually the problem.

Another "problem" that I see is that you implement the class in the "header" right after the declaration of the prototype. In the header leave the class prototype and move the ACTUAL implementation in a .cpp file(#including the header there too)

---

### Post by dwhitney67 on 2009-02-13
Do you see this header file (coordinates.h)?
```

#ifndef _COORDINATES_H_
#define _COORDINATES_H_

#ifndef _GL_H_
#define _GL_H_
        #include <GL/gl.h>
        #include <GL/glu.h>
        #include <GL/glut.h>
#endif

class coordinates {
        private:
        GLfloat Xcoord, Ycoord, Zcoord ;
        public:
        coordinates ( ) ;
        coordinates ( GLfloat Xc, GLfloat Yc, GLfloat Zc ) { Xcoord = Xc ; Ycoord = Yc ; Zcoord = Zc ; } ;
//      ~coordinates ( ) { }
        void setX ( GLfloat Xc ) { Xcoord = Xc ; } ;
        void setY ( GLfloat Yc ) { Ycoord = Yc ; } ;
        void setZ ( GLfloat Zc ) { Zcoord = Zc ; } ;
        GLfloat X ( void ) { return Xcoord ; } ;
        GLfloat Y ( void ) { return Ycoord ; } ;
        GLfloat Z ( void ) { return Zcoord ; } ;
} ;

#endif

```
Please tell me (and everyone for that matter), where you have implemented the default no-arg constructor.  Notice that you declare it, but you never implement it!

As I mentioned earlier, I would recommend that you change the constructor signature of colored_triangle_surface() to be:
```

class colored_triangle_surface {
private:
        coordinates& fstPoint;
        coordinates& sndPoint;
        coordinates& trdPoint ;
        color&       surface_color ;

public:
    colored_triangle_surface(coordinates&, coordinates&, coordinates&, color&);

    ...

```

The constructor would then be implemented as:
```

colored_triangle_surface :: colored_triangle_surface ( coordinates& C1, coordinates& C2, coordinates& C3, color& Co )
: fstPoint(C1),
  sndPoint(C2),
  trdPoint(C3),
  surface_color(Co)
{
}

```
This would have obviated the need for to have a no-arg constructor for coordinates.  In your original code, before you ever initialized the private member data of colored_triangle_surface with the input parameters, an attempt was made to construct the member data using their respective no-arg constructors... which you hadn't defined!

P.S.  An alternative is to declare colored_triangle_surface's constructor as:
```

class colored_triangle_surface {
private:
        coordinates* fstPoint;
        coordinates* sndPoint;
        coordinates* trdPoint ;
        color*       surface_color ;

public:
    colored_triangle_surface(coordinates*, coordinates*, coordinates*, color*);
    ...

```
In this case, the addresses of the parameters would be provided; this is helpful if you want to create the objects on the heap, and pass ownership to colored_triangle_surface.  Don't forget to implement the destructor if you plan to have this class destroy these objects!

---

### Post by dwhitney67 on 2009-02-13
> **SledgeHammer_999 said:**
> In the prototype of class "colored_triangle_surface" in **colored_triangle_surface.h** in the second constructor you have forgotten to assign a variable(?) to the type; What I mean is this. Your prototype is:
```
colored_triangle_surface ( coordinates, coordinates, coordinates, color ) ;
```

It should be:
```

colored_triangle_surface ( coordinates C1, coordinates C2, coordinates C3, color Co) ;
```

NOTE: I didn't compile your code so I don't know if this is actually the problem.

Another "problem" that I see is that you implement the class in the "header" right after the declaration of the prototype. In the header leave the class prototype and move the ACTUAL implementation in a .cpp file(#including the header there too)

When _defining_ constructors or other methods, providing variable names for the parameter list is optional.  In fact, it is generally done only so those reading the code will have a better understanding of what the constructor/method accepts as parameters.  For instance, for the object described above, it would be helpful to know which coordinate relates to the x-axis, which to the y-, and which to the z-axis.

Concerning splitting the definition (in the .h file) and the implementation (in a .cpp) file, this is the general accepted practice, and I too, agree with this principal.

Based on the OP's programming experience, perhaps he does not know how to linked together multiple .cpp files?

---

### Post by cguy on 2009-02-14
> **dwhitney67 said:**
> 
Concerning splitting the definition (in the .h file) and the implementation (in a .cpp) file, this is the general accepted practice, and I too, agree with this principal.

Based on the OP's programming experience, perhaps he does not know how to linked together multiple .cpp files?

You are right. How do I compile without getting undefined references errors when I split the class declaration from it's implementation?

---

### Post by Zugzwang on 2009-02-14
> **cguy said:**
> You are right. How do I compile without getting undefined references errors when I split the class declaration from it's implementation?

Most simple method: Tell the compiler to compile and link all the .cpp files at once. Example:
```

g++ -o myExecutable one.cpp two.cpp three.cpp

```

---

### Post by cguy on 2009-02-14
Already tried that and it spouts a thousand errors of types not being declared and "coordinates" & "color" not naming a type.
Yes, I did include the corresponding .h files (yep, between ""); I also tried including the files already included inside the headers into the corresponding .cpp-s, but to no effect.

I know this kind of separating worked in VC++ back when I had Windows, but not in g++.

When I wrote some similar files a few days ago I got the same kind of errors and searching on Google returned a result from cplusplus.com where some guy said that g++ does not support this kind of separating.


So, does g++ really support this? If so, what kind of magic to do to make it work?

--

Thanks dwhitney67 for the help!

---

### Post by dwhitney67 on 2009-02-14
> **cguy said:**
> ...

 some guy said that g++ does not support this kind of separating.
...

This guy is full of dudu.

You're welcome for the help.

Here's an example that you can play with to further your GCC education.  Copy the code and place into the files with the names given.

ClassOne.h:
```

#ifndef CLASS_ONE_H
#define CLASS_ONE_H

class ClassOne
{
  public:
    ClassOne();
    ~ClassOne();

    void doSomething();
};

#endif

```

ClassOne.cpp:
```

#include "ClassOne.h"
#include <iostream>

ClassOne::ClassOne()
{
}

ClassOne::~ClassOne()
{
}

void ClassOne::doSomething()
{
  std::cout << "ClassOne is doing something!" << std::endl;
}

```

Main.cpp:
```

#include "ClassOne.h"

int main()
{
  ClassOne c1;
  c1.doSomething();
}

```

To compile/link, and then to run:
```

g++ Main.cpp ClassOne.cpp
./a.out

```
If you have another class, then follow the "cookie" pattern for defining/implementing classes, and add that file to your g++ statement.  If you find yourself with 3 or more files, I would recommend that you consider developing a Makefile.

---

### Post by mb1 on 2009-03-03
Hi dwhitney67,
I am having a similar problem with c++ code. In my code the class is declared in a .h file, the same class is defined in a .cpp file and then the main function is defined in a .cpp file which is creating an object of the previously defined class. 

The code is correct as I copied it from a textbook, but I get the same 

fig06_05.cpp:(.text+0x194): undefined reference to `Time::Time()'

message when I do g++ fig06_05.cpp

But I compile the code using the command you gave ( g++ fig06_05.cpp time1.cpp ), and it creates the a.out as expected...

Out of curiousity, why do you think the first command errored? Shouldnt g++ know to look in to the main file and know where to find the class definition & declaration?

Thanks for posting your reply, that has reduced my initial pain :)

---

### Post by dwhitney67 on 2009-03-04
> **mb1 said:**
> ...
But I compile the code using the command you gave ( g++ fig06_05.cpp time1.cpp ), and it creates the a.out as expected...

Out of curiousity, why do you think the first command errored? Shouldnt g++ know to look in to the main file and know where to find the class definition & declaration?

Thanks for posting your reply, that has reduced my initial pain :)

Concerning your question related to compiling/linking fig06_05.cpp as a standalone module, you indicate that it could not reference Time::Time().  Was this constructor implemented elsewhere?  Sometimes when a constructor does nothing, and accepts no parameters, developers will implement the constructor in the header file.  Please recheck your book and/or your code.

I'm also surprised that when you compiled/linked fig06_05.cpp as a standalone module, that you did not get an undefined reference to main().

Anyhow, "undefined references" are errors that are spit out by the GCC ('gcc' and 'g++') linker when a function can not be found.  If you develop an application using multiple modules, you will need to link each and every module to form the executable image.

So to answer your other question, the answer is "no"... GCC will not look at any modules other than the ones you specify.  Note that the module name Main.cpp was arbitrarily chosen as an indicator that the main() function is implemented there.  One could easily define their main() in a module called Foo.cpp.

---

### Post by mb1 on 2009-03-04
Yes, the constructor was implemented in another file.
time.h (has the class declaration)
time.cpp (has the member function & constructor definitions for the class)
fig05_06.cpp (has the main() function)

"If you find yourself with 3 or more files, I would recommend that you consider developing a Makefile."
I will have to create a makefile going forward...
Thanks again.

---

