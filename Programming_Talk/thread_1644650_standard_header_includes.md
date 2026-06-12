---
title: "standard header includes"
date: 2010-12-13
forum: Programming Talk
---

### Post by XPeter on 2010-12-13
Hi

In C++, standard headers are allowed to include other standard headers. So using gcc when including <iostream> there is no need to include the <string> header because iostream already includes it.

Trying to write somewhat platform independent code I feel that relying on this is not good because different compilers and different versions of the same compiler can differ.

I was thinking if there exists dummy headers that have no includes and defines exactly what the standard says it should define. Without any real implementation. Then it's possible to compile against these headers instead and see if there is any errors. Of course we don't link the program as there is no implementation. Do anyone know if there exists such headers, or if there is another way to tackle this? I guess it's not too hard to create such header myself but it will take some time, and it's easy to make mistakes so I'm glad if I don't have to ;)

---

### Post by Tony Flury on 2010-12-13
What exactly are you trying to test/prove ?

Why do you need dummy headers ? You say you want header files that don't contain implementation, but i would doubt that any of the standard header files (or any well written header files) provided by anyone else will contain any implementation, they should just contain some declaration of the available classes, methods, functions, and maybe some macros.

When you compile a piece of code, it is not the header file that provides the implementation it is the libraries that the code is linked to.

---

### Post by XPeter on 2010-12-13
I want to prove that my code does not rely on standard headers including other headers.

Well it is not important if it contains implementation but in case of a real implementation it must not include any headers and declare other symbols that is reachable from the source that includes that file.

Templates are required to be implemented in the header, or in a file included by the header because it needs to be in the same compilation unit. It is possible to just use empty functions that doesn't do anything.

---

### Post by trent.josephsen on 2010-12-13
There should be a flag, or set of flags, you can set to turn off the GNU extensions to C++.

-std=c++98 -pedantic maybe? ([source](http://gcc.gnu.org/onlinedocs/gcc/Standards.html))

---

### Post by MadCow108 on 2010-12-13
Not really because say a function in iostream has string in the declaration of a function its public interface and you use that function.

You now replace iostream with a dummy header which does not include string so you can see if your code needs string but does not include it.
This means you have to provide a dummy string class in the dummy iostream (with all operators iostream or you are using!) or else it will stop in iostream before reaching your code.
But now your code does not need string anymore either and you gain nothing!
In the best case (problem in iostream can be fixed by forward declaration) you get some other cryptic error which is different in each file...

Missing standard includes are the easiest to fix errors, don't bother writing a tool to detect it, just fix the bugs as they come in.

Btw. you can minimize the number of bugs by _always_ including standard headers last.

---

### Post by dwhitney67 on 2010-12-13
> **XPeter said:**
> I want to prove that my code does not rely on standard headers including other headers.


Then remove any "using namespace std" statements from your code, and replace them with specific "using" statements as to what you actually require.

For example:
```

#include <iostream>

using std::cout;
using std::endl;

int main()
{
   string message = "Hello World";

   cout << message << endl;
}

```
You will be enlightened almost immediately as to what is missing in the code above after attempting to compile it.

---

### Post by dwhitney67 on 2010-12-13
> **MadCow108 said:**
> 
Btw. you can minimize the number of bugs by _always_ including standard headers last.

The best advice in the world; too bad lots of C and C++ programmers just don't understand the benefit of doing this.

---

### Post by worksofcraft on 2010-12-14
> **dwhitney67 said:**
> The best advice in the world; too bad lots of C and C++ programmers just don't understand the benefit of doing this.

It's all very well in theory, but say I have a really elementary base class in my own header file that needs to return a string...

[php]
struct base {
    std::string identify() { return "I'm base"; }
};
[/php]

I suspect one way or the other I'll have to #include <string> **before** I can use it :confused:

---

### Post by dwhitney67 on 2010-12-14
> **worksofcraft said:**
> It's all very well in theory, but say I have a really elementary base class in my own header file that needs to return a string...

[php]
struct base {
    std::string identify() { return "I'm base"; }
};
[/php]

I suspect one way or the other I'll have to #include <string> **before** I can use it :confused:

Duh!  What's your point?

---

### Post by Arndt on 2010-12-14
> **worksofcraft said:**
> It's all very well in theory, but say I have a really elementary base class in my own header file that needs to return a string...

[php]
struct base {
    std::string identify() { return "I'm base"; }
};
[/php]

I suspect one way or the other I'll have to #include <string> **before** I can use it :confused:

Of course each source file should include header files for what it is using directly itself. What dwhitney probably meant was the order in which one file includes those header files, when some are system ones and some are project-local.

---

### Post by XPeter on 2010-12-14
> **trent.josephsen said:**
> -std=c++98 -pedantic maybe?
These plags can be a good idea but they have nothing to do with my question.

> **trent.josephsen said:**
> You now replace iostream with a dummy header which does not include string so you can see if your code needs string but does not include it.
This means you have to provide a dummy string class in the dummy iostream (with all operators iostream or you are using!) or else it will stop in iostream before reaching your code.
But now your code does not need string anymore either and you gain nothing!
In the best case (problem in iostream can be fixed by forward declaration) you get some other cryptic error which is different in each file...
Types should use forward declaration whenever possible in the headers. I think that is enough. 

> **trent.josephsen said:**
> Missing standard includes are the easiest to fix errors, don't bother writing a tool to detect it, just fix the bugs as they come in.
Yes, I am more concerned about other people that might try to compile it. If a beginner gets thousands of errors when he tries to compile he will likely just give up, and it's not easy to solve if you don't know how to solve it.

> **dwhitney67 said:**
> Then remove any "using namespace std" statements from your code, and replace them with specific "using" statements as to what you actually require.
I never use the using keyword. So this is already not a problem.

> **dwhitney67 said:**
> [QUOTE=MadCow108;10234991]Btw. you can minimize the number of bugs by _always_ including standard headers last.The best advice in the world; too bad lots of C and C++ programmers just don't understand the benefit of doing this.[/QUOTE]
I actually heard about this a few days ago so I have started to do this. It helps ensuring my headers are independent and not needs another header included before this header is included. But it still does not do anything about that we rely on that headers we include include other headers. I am more concerned about the standard headers because they can change. If my own headers have a long chain of includes it's not much of a problem because it will always be consistent regardless of platform, compiler version etc.

---

### Post by dwhitney67 on 2010-12-14
> **XPeter said:**
> I am more concerned about the standard headers because they can change.

You worry too much. If the header files change, then everyone will have to adapt to it.  It would not be the first time.

---

### Post by trent.josephsen on 2010-12-14
> **XPeter said:**
> These plags can be a good idea but they have nothing to do with my question.
What I was trying to get at is, if #include <iostream> is **required by the standard** to #include <string>, then you have nothing to worry about; your code is standards-compliant whether it depends on the behavior or not.  If it does so just for convenience in a certain implementation, then forcing compliance to a particular standard should warn you about it.  (If not, that is either a bug in <iostream>, or an oversight on the part of the standards committee.  Try to get it fixed.)

None of the other things you quoted were from me.  Please edit your post to credit the original authors.

---

### Post by worksofcraft on 2010-12-14
I think this thread is interesting because I'm struggling with the following problem:

I have a project with lots of files and right at the very top I have a little header where I try to do all the project wide configuration options.

One of these is whether I use either std::string or Glib::ustring for my strings.

[php]
// select the class to use for strings
#define STRING std::string
// #define STRING Glib::ustring
[/php]

that works just fine, and I don't have to include either std::string or Glib::ustring header files, where I don't use them :)

However as we all know, macros don't obey C++ scope rules, so I was told it is** bad practice** to do this and that I should use a *typedef*... but then I would have to include those header files in my configuration header which goes in everything! :shock:... so now I don't know what to do :(

---

### Post by nvteighen on 2010-12-15
> **worksofcraft said:**
> 
However as we all know, macros don't obey C++ scope rules, so I was told it is** bad practice** to do this and that I should use a *typedef*... but then I would have to include those header files in my configuration header which goes in everything! :shock:... so now I don't know what to do :(

Well, you can use conditional macros that choose between two typedef's :)

```

#ifdef USE_STD_STRING
typedef String std::string;
#else
typedef String Glib::ustring;
#endif

```

Now more seriously, I don't understand what's your exact problem. Could you elaborate a bit on it? (Or maybe I did solve it with my joke... :P)

---

### Post by worksofcraft on 2010-12-15
> **nvteighen said:**
> Well, you can use conditional macros 
Now more seriously, I don't understand what's your exact problem. Could you elaborate a bit on it? (Or maybe I did solve it with my joke... :P)

Actually your joke explains it very well indeed :)

At issue are header include file dependencies. Clearly without including #include <glibmm/ustring.h>, a typedef like:
[php]
typedef Glib::ustring string_type;
[/php]
... results in:
```

def.cpp:10: error: ‘Glib’ has not been declared
def.cpp:10: error: expected initializer before ‘string_type’

```

So in order to keep all my configurations in one header file I would have to include said glibmm/ustring.h and add `pkg-config --cflags --libs gtkmm-2.4` to every compile command of every module regardless if it uses a string... not a good solution IMO :(

Now your suggestion DOES solve that problem:
By defining an otherwise useless intermediate macro USE_STD_STRING I can avoid defining macro STRING "simply" by creating a **conditionally compiled typedef in every single module** that does use strings... also not a good solution IMO :(

I was hoping to keep all the configuration related stuff in one header file that can be included everywhere without dragging in all sorts of other headers weather they are need or not. So I was  wondering how other people solve this :popcorn:

---

### Post by Arndt on 2010-12-15
> **worksofcraft said:**
> Actually your joke explains it very well indeed :)

At issue are header include file dependencies. Clearly without including #include <glibmm/ustring.h>, a typedef like:
[php]
typedef Glib::ustring string_type;
[/php]
... results in:
```

def.cpp:10: error: ‘Glib’ has not been declared
def.cpp:10: error: expected initializer before ‘string_type’

```

So in order to keep all my configurations in one header file I would have to include said glibmm/ustring.h and add `pkg-config --cflags --libs gtkmm-2.4` to every compile command of every module regardless if it uses a string... not a good solution IMO :(

Now your suggestion DOES solve that problem:
By defining an otherwise useless intermediate macro USE_STD_STRING I can avoid defining macro STRING "simply" by creating a **conditionally compiled typedef in every single module** that does use strings... also not a good solution IMO :(

I was hoping to keep all the configuration related stuff in one header file that can be included everywhere without dragging in all sorts of other headers weather they are need or not. So I was  wondering how other people solve this :popcorn:

autoconf?

---

### Post by worksofcraft on 2010-12-15
> **Arndt said:**
> autoconf?

How do you make it tell the modules that use strings which class of strings you want to use?

---

### Post by dwhitney67 on 2010-12-16
> **worksofcraft said:**
> 
I was hoping to keep all the configuration related stuff in one header file that can be included everywhere without dragging in all sorts of other headers weather they are need or not.

Well, that's right.  One header file should suffice.  This header file should be included in all modules that require it.

Now, the trick is to instruct the build process which "technology" to use: either STL or gtkmm.  You could easily pass a flag to the "make" command to tell it which you prefer.

Examine these files...

common.h
```

#ifdef USE_GTKMM

   #include <gtkmm.h>
   typedef Glib::ustring String;

#else

   #include <string>
   typedef std::string String;

#endif

```

main.cpp:
```

#include "common.h"
#include <iostream>

int main()
{
   String str = "Hello World";
   std::cout << str << std::endl;
}

```

Makefile:
```

APP      = myapp

OBJDIR   = .srcobjs

SRCS    := $(shell find . -name '*.cpp')
SRCDIRS := $(shell find . -name '*.cpp' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))
DEPS    := $(patsubst %.cpp,$(OBJDIR)/%.d,$(SRCS))

[B]ifeq "$(GTKMM)" "1"
CXXFLAGS = -DUSE_GTKMM
INCLUDES = `pkg-config --cflags gtkmm-2.4`
LDFLAGS  = `pkg-config --libs gtkmm-2.4`
endif[/B]

INCLUDES +=
DEBUG     = -g
CXXFLAGS += $(DEBUG) -Wall -pedantic -ansi $(INCLUDES)
LDFLAGS  +=

SHELL     = /bin/bash

.PHONY: all app clean distclean

all: app

app : buildrepo $(APP)

$(APP) : $(OBJS)
	$(CXX) $^ $(LDFLAGS) -o $@

$(OBJDIR)/%.o: %.cpp
	$(CXX) $(CXXFLAGS) -MT $@ -MD -MP -MF $(subst .o,.d,$@) -c $< -o $@

clean:
	$(RM) -r $(OBJDIR)

distclean: clean
	$(RM) $(APP)

buildrepo:
	@$(call make-repo)

define make-repo
   for dir in $(SRCDIRS); \
   do \
	mkdir -p $(OBJDIR)/$$dir; \
   done
endef


# usage: $(call make-depend, SourceFile, ObjectFile, DependFile)
define make-depend
  $(CXX) -MM -MF $3 -MP -MT $2 $(CXXFLAGS) $1
endef

ifneq "$(MAKECMDGOALS)" "distclean"
ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif
endif

```
To build with gtkmm:
```

make GTKMM=1

```
otherwise:
```

make

```


Btw, as far as gtkmm/ustring.h, where are you referencing this file???  It is not on my system; I use gtkmm-2.4.

---

### Post by worksofcraft on 2010-12-16
> **dwhitney67 said:**
> Well, that's right.  One header file should suffice.  This header file should be included in all modules that require it.

Now, the trick is to instruct the build process which "technology" to use: either STL or gtkmm.  You could easily pass a flag to the "make" command to tell it which you prefer.

Examine these files...

common.h
```

#ifdef USE_GTKMM

   #include <gtkmm.h>
   typedef Glib::ustring String;

#else

   #include <string>
   typedef std::string String;

#endif

```

main.cpp:
```

#include "common.h"
#include <iostream>

int main()
{
   String str = "Hello World";
   std::cout << str << std::endl;
}

```

Makefile:
```

APP      = myapp

OBJDIR   = .srcobjs

SRCS    := $(shell find . -name '*.cpp')
SRCDIRS := $(shell find . -name '*.cpp' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))
DEPS    := $(patsubst %.cpp,$(OBJDIR)/%.d,$(SRCS))

[B]ifeq "$(GTKMM)" "1"
CXXFLAGS = -DUSE_GTKMM
INCLUDES = `pkg-config --cflags gtkmm-2.4`
LDFLAGS  = `pkg-config --libs gtkmm-2.4`
endif[/B]

INCLUDES +=
DEBUG     = -g
CXXFLAGS += $(DEBUG) -Wall -pedantic -ansi $(INCLUDES)
LDFLAGS  +=

SHELL     = /bin/bash

.PHONY: all app clean distclean

all: app

app : buildrepo $(APP)

$(APP) : $(OBJS)
	$(CXX) $^ $(LDFLAGS) -o $@

$(OBJDIR)/%.o: %.cpp
	$(CXX) $(CXXFLAGS) -MT $@ -MD -MP -MF $(subst .o,.d,$@) -c $< -o $@

clean:
	$(RM) -r $(OBJDIR)

distclean: clean
	$(RM) $(APP)

buildrepo:
	@$(call make-repo)

define make-repo
   for dir in $(SRCDIRS); \
   do \
	mkdir -p $(OBJDIR)/$$dir; \
   done
endef


# usage: $(call make-depend, SourceFile, ObjectFile, DependFile)
define make-depend
  $(CXX) -MM -MF $3 -MP -MT $2 $(CXXFLAGS) $1
endef

ifneq "$(MAKECMDGOALS)" "distclean"
ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif
endif

```
To build with gtkmm:
```

make GTKMM=1

```
otherwise:
```

make

```


Btw, as far as gtkmm/ustring.h, where are you referencing this file???  It is not on my system; I use gtkmm-2.4.

Yes, that does work thanks :)

It does however still make the compile take oodles longer by
including either <string> or <gtkmm.h> in every single module it compiles...

I split my library code into many tiny modules so that it would only link in the ones that actually get used and it also helped me make it much more intelligible by remove identifying unnecessary coupling. However that does mean that #including unnecessary files in hundreds of modules instead of in the one or two where they are actually needed makes a big difference.

Btw, the gtkmm path seems to be a symbolic link in my includes folder that points to gtkmm-2.4 folder. I presume it is something that gets setup when you install it. Thus changing version means only to change the symbolic link I suspect, but haven't tried that.

---

### Post by trent.josephsen on 2010-12-16
If you are significantly slowed by including the declaration of your String type in every module (which sounds fishy to start with; including headers is usually a tiny tiny fraction of compile time), then you should make your own "whateverString.h" header file and #include it only in the files where you use your String type.  There's nothing to be gained by putting *everything* in one header file.

---

### Post by dwhitney67 on 2010-12-16
> **worksofcraft said:**
> 
It does however still make the compile take oodles longer by
including either <string> or <gtkmm.h> in every single module it compiles...

Instead of calling the common header file "common.h", consider calling it "String.h", and then only include it where necessary (similar to what you would have done if you merely stuck to using either the STL <string> or <gtkmm.h>).


> **worksofcraft said:**
> 
Btw, the gtkmm path seems to be a symbolic link in my includes folder that points to gtkmm-2.4 folder. I presume it is something that gets setup when you install it.
No, it does not get setup.  It is probably something that you did manually.  The whole point of the pkg-config command is that you don't need to worry so much where the package header files reside.  Of course it blows that one must specify the version number of the gtkmm package.

---

