---
title: "Members of a class - Stack or Heap?"
date: 2009-06-17
forum: Programming Talk
---

### Post by jacensolo on 2009-06-17
I'm developing a game and never thought about this before, are class members stored on the stack or heap? The reason I want to know is because I am going to have a lot of  members so it probably wouldn't want to store it on the stack.

Edit: Well the answer hit me right after I posted this. It is stored on the stack and is cleaned up automatically by the destructor.

---

### Post by TheBuzzSaw on 2009-06-17
It depends on how you use the class.

```
myClass myObject;
```
That will end up on the stack.

```
myClass* myObject = new myClass();
```
That will end up on the heap.

---

### Post by jacensolo on 2009-06-17
> **TheBuzzSaw said:**
> It depends on how you use the class.

```
myClass myObject;
```
That will end up on the stack.

```
myClass* myObject = new myClass();
```
That will end up on the heap.

Oh yes, I know that. That is a bit funny, though. If I declare a member in the class on the stack (or not if the class is declared dynamically) like :
```
class A
{
protected:
  int A;
}
```

It ends up on the heap. but the destructor still know to clean it up even if the class is declared dynamically as opposed to: ```
class A
{
protected:
  int* A = new int;
}
```

The destructor needs to be told to delete A in that case. I guess I don't understand the internals of class memory management.

---

### Post by jacensolo on 2009-06-17
I am going to hijack my thread here because I don't think this is new thread worthy at this time of night. Does mono support unmanaged c++? I'm creating a game under windows and I really do not want to write a few makefiles to get it working under Linux until I'm finished. It would be really nice to be able to open  up my project's solution (after transferring the files) and start.

---

### Post by Tony Flury on 2009-06-17
The problem with hijacking a thread about a complete different topic - and with a title that is irrelevant to your problem - is that some of the people who might be able to solve your problem wont read your question, and also you are making it tougher for the OP to get a useful answer to his question.

Also - you comment about "this time of night" - remember the world works on a 24 hour clock, and there are forums members active all through the day - it might be night time for you - but it is almost certainly day time for someone else, and they might just be able to answer your question.

---

### Post by CptPicard on 2009-06-17
Think of it this way -- the memory that pointers point to is *never* automatically released. That is, for a "new" there is never an automatic, implicit "delete".

Primitive datatype members that you have in your class (ints, floats, pointers...) form a block of memory that either

a) sits on the stack and can be automatically reclaimed when it comes out of scope

or

b) is allocated on the heap and pointed-to by some pointer somewhere, that eventually gets delete'd.

Now, destructor gets run at both cases when object needs to be cleaned up. The memory allocated for the block *primitive* members gets reclaimed either by the "going out of scope" or the initial call to delete without the destructor doing anything, but the destructor needs to specifically release all memory pointed to by the pointer members in the class.

---

### Post by directhex on 2009-06-17
> **jacensolo said:**
> I am going to hijack my thread here because I don't think this is new thread worthy at this time of night. Does mono support unmanaged c++? I'm creating a game under windows and I really do not want to write a few makefiles to get it working under Linux until I'm finished. It would be really nice to be able to open  up my project's solution (after transferring the files) and start.

Mono does not support Managed C++ or C++/CLI, except on Windows. You can P/Invoke into pure unmanaged libraries the same as on Windows though - meaning that pure g++-compiled C++ libraries would need C wrappers.

---

### Post by dwhitney67 on 2009-06-17
Here's some code that demonstrates that a 'delete' is not always necessary after allocating memory from the heap.

```

#include <memory>

class Foo
{
public:
   Foo() : m_data(new int(5)) {}
private:
   std::auto_ptr<int> m_data;
};

int main()
{
   Foo foo;
}

```

There are other types of smart pointers, such as the shared or the scoped.

Wrt the question concerning Mono, what is the problem with developing a Makefile?  For small projects, they are a cake to develop, and typically once you have a Makefile, it can be used again and again for other projects, with only slight modifications.

Here's a basic Makefile:
```

APP      = MyApp

APPFLAGS = -O3
INCPATH  = -I./
LDFLAGS  = -L./
LIBS     = -lpthread

# Rarely should anything ever have to be changed below
#
SRCS     = $(wildcard *.cpp)
OBJS     = $(SRCS:.cpp=.o)

CXXFLAGS = -Wall -pedantic -ansi

.PHONY: all clean distclean

all: $(APP)

$(APP): $(OBJS)
        $(CXX) $^ $(LDFLAGS) $(LIBS) -o $@

.cpp.o:
        $(CXX) $(CXXFLAGS) $(INCPATH) $(APPFLAGS) -c $<

clean:
        $(RM) $(OBJS)

distclean: clean
        $(RM) $(APP)

```

---

### Post by CptPicard on 2009-06-17
> **dwhitney67 said:**
> Here's some code that demonstrates that a 'delete' is not always necessary after allocating memory from the heap.


Well, the smart pointer's destructor does contain the delete.. :p

---

### Post by jacensolo on 2009-06-17
This project is going to expand quite a bit (hopefully) and includes multiple static libraries, so I thogught making a makefile would be difficult. I'll look into it.

> **CptPicard said:**
> Think of it this way -- the memory that pointers point to is *never* automatically released. That is, for a "new" there is never an automatic, implicit "delete".

Primitive datatype members that you have in your class (ints, floats, pointers...) form a block of memory that either

a) sits on the stack and can be automatically reclaimed when it comes out of scope

or

b) is allocated on the heap and pointed-to by some pointer somewhere, that eventually gets delete'd.

Now, destructor gets run at both cases when object needs to be cleaned up. The memory allocated for the block *primitive* members gets reclaimed either by the "going out of scope" or the initial call to delete without the destructor doing anything, but the destructor needs to specifically release all memory pointed to by the pointer members in the class.

Thanks. Although I knew most of that, it's good to have a refresher once in a while.

---

### Post by dwhitney67 on 2009-06-17
> **jacensolo said:**
> This project is going to expand quite a bit (hopefully) and includes multiple static libraries, so I thogught making a makefile would be difficult. I'll look into it.

Funny you mention this; I just finished updating a Makefile that I use to build a static library.  Here it is...
```

LIB      = libLDS.a

OBJDIR   = objects
SRCS     = $(wildcard *.cpp)
OBJS     = $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))
DEPS     = $(patsubst %.cpp,$(OBJDIR)/%.d,$(SRCS))

INCLUDES =
CXXFLAGS = $(INCLUDES) -Wall -pedantic -ansi -c

ifeq ($(DEBUG), 1)
CXXFLAGS += -g3 -DDEBUG
endif

.PHONY: all clean distclean

all: $(LIB)

$(LIB): buildrepo $(OBJS)
	@echo "---> Archiving $@"
	@$(AR) r $@ `find $(OBJDIR) -name \*.o`

buildrepo:
	@mkdir -p $(OBJDIR)

$(OBJDIR)/%.o: %.cpp
	@$(call make-depend,$<,$@,$(subst .o,.d,$@))
	@echo "---> Compiling $<"
	@$(CXX) $(CXXFLAGS) $< -o $@

clean:
	@echo "---> Removing object files"
	@$(RM) $(OBJS)

distclean: clean
	@echo "---> Removing library"
	@$(RM) -r $(OBJDIR)
	@$(RM) $(LIB)

ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif

# usage: $(call make-depend,source-file,object-file,depend-file)
define make-depend
  $(CXX) -MM            \
         -MF $3         \
         -MP            \
         -MT $2         \
         $(CXXFLAGS)    \
         $1
endef

```

---

