---
title: "C++ Undefined Reference"
date: 2008-05-07
forum: Programming Talk
---

### Post by markoklacar on 2008-05-07
Hi all,

I'm doing a school assigment and I just can't figure this one out. I know it's probably as easy as a,b,c but I'm pretty new to 
C++.

I've got a couple of classes but the error I get reads like this:
```

Session.o(.text+0x118): In function `main':
D:/cpp/inlupp/Session.cpp:33: undefined reference to `Button::Button(int, int, int, int, std::string)'

```

This is the Button class and it's header:
```

#ifndef BUTTON_H_
#define BUTTON_H_
#include <String>
#include "Component.h"

using namespace std;

class Button : public Component {
public:
	Button(int sx, int sy, int ex, int ey, string caption);
	void show() const;
	bool handle_event(Event eve) const;
	void set_text(string cap);
	string get_text();

private:
	string caption;
};

#endif /*BUTTON_H_*/

```

```

#include <iostream>
#include <cctype>
#include <string>
#include "Button.h"

using namespace std;

Button::Button(int sx, int sy, int ex, int ey, string caption) :
	Component::Component(sx, sy, ex, ey), caption(caption) {
}

bool Button::handle_event(Event eve) const {
        return true;
}

void Button::show() const {
}

void Button::set_text(string cap) {
}

string Button::get_text() {
	return caption;
}

```

And here is the Session.

```

#include <cctype>
#include <cstring>
#include <String>
#include "Button.h"

using namespace std;
using namespace terminal_star85;

int main() {
	Button* b= new Button::Button(0,0,10,10,"Marko");
	b->show();
}

```

Ths thing is I want to call even more things from the Session but they give me the 'undefined referece' error.

Any ideas?:confused:

Thank you in advance

---

### Post by supirman on 2008-05-07
How are you compiling them?  See [http://en.allexperts.com/q/C-1040/Undefined-reference-linking.htm](http://en.allexperts.com/q/C-1040/Undefined-reference-linking.htm) for a bit of info regarding undefined references and the building process.  

I don't know how big your project is, but if it was just 3 files, Component.cpp, Button.cpp, and Session.cpp, to form your executable you'll need something similar to:
g++ -o myapp Component.cpp Button.cpp Session.cpp

---

### Post by markoklacar on 2008-05-07
Hi,

It's bigger then 3 files. I'll start by looking at the link you gave me.

Thanks for now, but keep your eyes open :)

---

### Post by issih on 2008-05-07
Casting a quick eye over it, I don't think your include directives are working correctly....

You include the Button header from the Button class (.cc, whatever you want to call it) file.

However you then include the header file in the Session, not the class file. The session therefore has the header information, but because the header file never includes the class file, the actual method definitions are never passed to the compiler...

You can either include the class file rather than the header in the session, or start messing around with proper build systems like make, something I keep meaning to do, but never get around to. Note that if you start including the class file rather than the header, you should really have inclusion guard preprocessor directives in that file too.

Hope that helps sort it out

---

### Post by markoklacar on 2008-05-07
Hi,

I already tried including the .cpp file of button. BUT I didn't use guards for this. 

How should I write the guards?
How do guards for .cpp files look?

Thanks

---

### Post by issih on 2008-05-07
You used an inclusion guard in the code you posted for the Button header file, its the ifndef, define and endif statements wrapping all the other code. They act so that if multiple external files include this one, the compiler only sees it once.

Having another look as you have tried the most obvious error, I can't see anything glaringly wrong, but I wonder if it might (and this is a guess) be to do with your string libraries and literals.

Currently you have lots of different libraries being referenced..

Firstly I don't know why you are including c style strings and c++ ones, generally stick to one, it'll save you a lot of frustration. I use c++ and the conversion method (.c_str() if I remember correctly) if I have to pass a c style null terminated array to another function.

Nonetheless you should get away with it, as long as the different string libraries pass enough to the compiler that it can know how to convert from one type to another.

My biggest worry is that currently you include <String> in your header and in Session, but <string> in the cpp file. I admit I don't actually know if these are referencing the same library, but as a general rule, case matters in programming...a lot.

---

### Post by supirman on 2008-05-07
How are you compiling the code?  Post your makefile, or the command you're using, and we can help resolve the issue for you.  

And you shouldn't be including actual cpp files in others, only the headers.  The key is to make sure all files in your project are available when the application gets linked.

---

### Post by dempl_dempl on 2008-05-07
> **markoklacar said:**
> Hi all,

I'm doing a school assigment and I just can't figure this one out. I know it's probably as easy as a,b,c but I'm pretty new to 
C++.

I've got a couple of classes but the error I get reads like this:
```

Session.o(.text+0x118): In function `main':
D:/cpp/inlupp/Session.cpp:33: undefined reference to `Button::Button(int, int, int, int, std::string)'

```

This is the Button class and it's header:
```

#ifndef BUTTON_H_
#define BUTTON_H_
#include <String>
#include "Component.h"

using namespace std;

class Button : public Component {
public:
	Button(int sx, int sy, int ex, int ey, string caption);
	void show() const;
	bool handle_event(Event eve) const;
	void set_text(string cap);
	string get_text();

private:
	string caption;
};

#endif /*BUTTON_H_*/

```

```

#include <iostream>
#include <cctype>
#include <string>
#include "Button.h"

using namespace std;

Button::Button(int sx, int sy, int ex, int ey, string caption) :
	Component::Component(sx, sy, ex, ey), caption(caption) {
}

bool Button::handle_event(Event eve) const {
        return true;
}

void Button::show() const {
}

void Button::set_text(string cap) {
}

string Button::get_text() {
	return caption;
}

```

And here is the Session.

```

#include <cctype>
#include <cstring>
#include <String>
#include "Button.h"

using namespace std;
using namespace terminal_star85;

int main() {
	Button* b= new Button::Button(0,0,10,10,"Marko");
	b->show();
}

```

Ths thing is I want to call even more things from the Session but they give me the 'undefined referece' error.

Any ideas?:confused:

Thank you in advance


Hi!

If you use C++ some IDE ( like Visual Studio , Kdevelop, ANjuta , C++ Builder , etc. )  , you should always add files with  
"Add file to project" , and it'll all be just fine :)   .





---------

> **supirman said:**
> How are you compiling the code?  Post your makefile, or the command you're using, and we can help resolve the issue for you.  

And you shouldn't be including actual cpp files in others, only the headers.  The key is to make sure all files in your project are available when the application gets linked.

He's a beginner. Beginners don't make their own Makefiles :)  .

---

### Post by issih on 2008-05-07
Ok I had a little fiddle:

Button.h:
```
#ifndef BUTTON_H_
#define BUTTON_H_
#include <string>

using namespace std;

class Button{
public:
	Button(int sx, int sy, int ex, int ey, string caption);
	void show() const;
	void set_text(string cap);
	string get_text();

private:
	int anSX;
	int anSY;
	int anEX;
	int anEY;
	string caption;
};

#endif /*BUTTON_H_*/
```

Button.cpp
```
#ifndef BUTTON_C_
#define BUTTON_C_

#include <iostream>
#include <string>
#include "Button.h"

using namespace std;

Button::Button(int sx, int sy, int ex, int ey, string caption) :
anSX(sx),
anSY(sy),
anEX(ex),
anEY(ey),
caption(caption)
{}

void Button::show() const{
	cout<<caption<<endl;
}

void Button::set_text(string cap) {
	caption = cap;
}

string Button::get_text() {
	return caption;
}

#endif
```

Session.cpp
```
#include <string>
#include "Button.cc"

using namespace std;

int main() {
	Button* b= new Button(0,0,10,10,"Marko");
	b->show();
}
```

That compiles and does what it should with the simple line:
```
g++ Session.cpp
```

Obviously I had to simplify things slightly as I don't have the rest of your classes, but it should translate easily.

I fully admit that supirman is correct, you should really (following good pratice) only include header files in cpp files. You then need to use the command ```
g++ -c <list of all cpp files>
``` to produce .o object files from each .cpp file. These .o files should then be linked together into the final executable in a second step using ```
g++ <list of all .o files>
```

build utilities such as make and things built into various IDEs are all about automating this process.

Nonetheless, what I have done above is valid c++. I am just compiling and linking in one single step, and I am using the include directives so that the compiler effectively sees one large text file defining the whole program. Its quick, its dirty, and you shouldn't really do it, but I admit that I do more often than I should

---

### Post by supirman on 2008-05-07
> **dempl_dempl said:**
> He's a beginner. Beginners don't make their own Makefiles :)  .

Really?  Just about the first thing we did in my first "introduction to programming" type of class was learn to write (simple) makefiles for our class projects.  Professors won't accept your assignments unless they were accompanied by an appropriate makefile.

---

### Post by dwhitney67 on 2008-05-07
markoklacar -

Here are some suggestions...

First, remove the #ifndef/#define/#endif from the implementation file for Button.cpp.  These are not needed.

Second, and this is merely a suggestion based on good programming practices, always include system header files (e.g. iostream, string, etc.) _after_ you have included your project header files.

Lastly, take supirman's original advice and verify that you are not only compiling each of your .cpp modules, but that you are linking them all together to form the executable program.  Supirman's comments were similar to:

```
$ g++ -o myApp Session.cpp Button.cpp Component.cpp
```

If you have additional .cpp modules, then add them to the end of the g++ statement.  Alternatively, massage this Makefile to suit your needs:
```
SRCS      := $(wildcard *.cpp)
OBJS      := $(SRCS:.cpp=.o)
CXXFLAGS  := -g
INCPATH   := -I./
LIBPATH   :=
LIBS      :=
APP       := myApp

.PHONY: clean distclean


# link object files together to form executable application
$(APP): $(OBJS)
        $(CXX) $(LIBPATH) $(LIBS) $(OBJS) -o $@

# compile source code to generate object files
.cpp.o:
        $(CXX) $(CXXFLAGS) $(INCPATH) -c $< -o $@

# delete object files
clean:
        $(RM) $(OBJS)

# delete object files and executable application
distclean: clean
        $(RM) $(APP)
```

---

### Post by markoklacar on 2008-05-08
Hi guys,

Thank you all for your help. In the end I made a makefile and it solved the problem.

Cheers guys!!!

---

### Post by Arwen on 2009-10-08
Hello to everyone!

It's a similar problem so I don't think it's worth creating a new thread.
I have 3 files : foo.h,foo.cpp that includes foo.h and goo.cpp which contains the main function. When I add a new function as public member of a class in foo.h > class hello {
                        int x;
                        public:
                               void change(int y);
                                   };

and define it as > void hello::change(int y)
                        {    x=y; } 
in foo.cpp,
 g++ gives : "error: no 'void hello::change(int)' member function declared in class 'hello'.
I include foo.h in both foo.cpp and goo.cpp.
All files aren't created by me but I have to change them,so the very first change I made is to add a new function as class member.
Any ideas about this problem?

I use Debian 5 and g++ (I run g++ -g foo.cpp goo.cpp).

Thanx for any help!

---

### Post by MadCow108 on 2009-10-08
according to your description it should work
you must be doing some other mistake

---

### Post by Arwen on 2009-10-08
I've run out of ideas right now, the weird thing is that in foo.h there's sth like this > enum Vehicles{cars,trucks}; and I just added 'buses' in it and it gives "foo.cpp:error: 'buses' was not declared in this scope" . Why cars and trucks are declared and buses aren't? (I can't imagine how ridiculous this question sounds :-P)

---

### Post by dwhitney67 on 2009-10-08
Arwen

You need to provide more information, regarding the g++ compiler errors, and better snippets of code.  Preferably all of the code would be nice.

Nevertheless, something as you described in your OP should work.

Foo.h:
```

#ifndef FOO_H
#define FOO_H

class Hello
{
public:
   enum Vehicle { CAR, BUS, TRAIN, AIRPLANE };

   void change(int y);
private:
   int x;
};

#endif

```
Foo.cpp:
```

#include "Foo.h"

void Hello::change(int y)
{
   x = y;
}

```
Goo.cpp:
```

#include "Foo.h"
#include <iostream>

int main()
{
   Foo foo;
   foo.change(5);

   // here, scope operator needed to access enum CAR
   //
   std::cout << Foo::CAR << std::endl;
}

```

P.S.  To build app:
```

g++ Foo.cpp Goo.cpp -o mygoo

```

---

### Post by Arwen on 2009-10-08
Thank you for your time, my problem is solved.Rather supernaturally..I made all the changes I wanted using gedit and not kate.Now everything is defined and declared.Why would the editor make such a difference?

Anyway,thanx a lot!

---

