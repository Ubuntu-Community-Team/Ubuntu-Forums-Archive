---
title: "Best way to do this in C++? (re: inheritance and casting)"
date: 2007-07-31
forum: Programming Talk
---

### Post by kpatz on 2007-07-31
I'm in the process of teaching myself C++, and in doing so am writing some basic classes so I can learn better than I would using the class libraries.

Right now I created a simple linked list class:

```
class Chain {
public:
  Chain *prev;
  Chain *next;

  Chain(void);
  virtual ~Chain(void);
  
  virtual Chain *insertBefore(void);
  virtual Chain *insertBefore(Chain *);
  virtual Chain *insertAfter(void);
  virtual Chain *insertAfter(Chain *);
  virtual Chain *add(void);
  virtual Chain *add(Chain *);
};
```

The Chain class simply handles the linked list, but doesn't carry any data.  To carry data, I'm creating derived classes such as this sample that stores a name in each linked list item (String objects):

```
class Mylist: public Chain {
public:
  String *listname;
  Mylist(void): Chain() { 
    listname = NULL;
  };
  Mylist(const Mylist &r): Chain() {
    listname = NULL;
    if (r.listname) listname = new String(*r.listname);
  };
  ~Mylist(void) {
    if (listname) delete listname;
  };
};

```

The problem I'm having is being able to use the Chain methods (that use Chain pointers) on Mylist objects.  In other words:

```

  Mylist *list = new Mylist();
  . . .
  Mylist *item = list->add();  // adds new item to chain

```

  The add() call gets an error because the compiler can't convert Chain* to Mylist*.

I can get around it by type casting and adding functions to Mylist such as:
```

  Mylist *Mylist::add(void) { return dynamic_cast<Mylist *>(Chain::add(new Mylist())); };
  Mylist *Mylist::add(Mylist *p) { return dynamic_cast<Mylist *>(Chain::add(p)); };
  Mylist *Mylist::insertBefore(void) { return dynamic_cast<Mylist *>(Chain::insertBefore(new Mylist())); };
  Mylist *Mylist::insertAfter(void) { return dynamic_cast<Mylist *>(Chain::insertAfter(new Mylist())); };

```

... but is there a better way?  I'd rather not repeat code for every linked-list derived class I create.

TIA,
KJP

---

### Post by LaRoza on 2007-07-31
You might want to look into using Templates.

---

### Post by aks44 on 2007-07-31
CRTP (curiously recurring template pattern) may be one way to achieve it. Covariant return types or factories could also be used.

The catch is that all those methods are (more or less) intrusive.

IMHO the best way is to use a non intrusive wrapper class, and a facade container using iterators to access the elements.
Wait... isn't that how STL does it? ;)

---

### Post by kpatz on 2007-07-31
I had no luck using templates.  I ended up using a macro:

```
#define FUNCS(T) T* add(void) { return dynamic_cast<T *>(Chain::add(new T())); }; \
T* add(T *p) { return dynamic_cast<T *>(Chain::add(p)); }; \
T* insertBefore(void) { return dynamic_cast<T *>(Chain::insertBefore(new T())); }; \
T* insertAfter(void) { return dynamic_cast<T *>(Chain::insertAfter(new T())); };

```

and then in my class:

```

class Mylist: public Chain {
  blah blah blah...
   FUNCS(Mylist)
};

```

There must be a better way, but this way I can create any number of subclasses without copying code over and over (and then having to change it in umpteen places if I find a bug or want to add a feature)...

---

### Post by Wybiral on 2007-08-01
> **kpatz said:**
> I had no luck using templates.  I ended up using a macro

Nooooooo..

---

### Post by aks44 on 2007-08-01
> **kpatz said:**
> I had no luck using templates.  I ended up using a macro:

Oh my...

Please post what you tried to do with templates, so that we can help you fixing it...

BTW I repeat: the template way has to be non intrusive (ie. works with any existing class without requiring any modification).

Macros are the worst you could do :(

---

### Post by kpatz on 2007-08-01
I tried umpteen different things, but here's a sample I cobbled together to show the gist of the problem:

```

#include <stdio.h>

// Note - I left out Chain's implementation for brevity, to show my template problem
class Chain {
protected:
  Chain *prev;
  Chain *next;

public:
  Chain(void);
  virtual ~Chain(void);
  
  virtual Chain *insertBefore(void);
  virtual Chain *insertBefore(Chain *);
  virtual Chain *insertAfter(void);
  virtual Chain *insertAfter(Chain *);
  virtual Chain *add(void);
  virtual Chain *add(Chain *);
  virtual Chain *getNext(void);
  virtual Chain *getPrev(void);
};

template <class T>
class Mylist: public Chain {
public:
  long iFlags;
  char *pattern;
  Mylist(void): Chain() { 
    pattern = NULL;
  };
  Mylist(const Mylist &p): Chain() {
    if (p.pattern)
      pattern = p.pattern; // don't mind this, I stripped out some custom code
    else
      pattern = NULL;
  };
  ~Mylist(void) {
    if (pattern) delete pattern;  // don't mind this, I stripped out some custom code
   };
   T* add(void) { return dynamic_cast<T *>(Chain::add(new T())); }; \
   T* add(T *p) { return dynamic_cast<T *>(Chain::add(p)); }; \
   T* insertBefore(void) { return dynamic_cast<T *>(Chain::insertBefore(new T())); }; \
   T* insertAfter(void) { return dynamic_cast<T *>(Chain::insertAfter(new T())); }; \
   T* getPrev(void) { return dynamic_cast<T *>(Chain::getPrev()); }; \
   T* getNext(void) { return dynamic_cast<T *>(Chain::getNext()); };
};

int main()
{
  Mylist<Mylist> x;   // get compile error here
  return 0;
}

```

Compiling this gets me:

template.cxx: In function âint main()â:
template.cxx:50: error: type/value mismatch at argument 1 in template parameter list for âtemplate<class T> class Mylistâ
template.cxx:50: error:   expected a type, got âMylistâ
template.cxx:50: error: invalid type in declaration before â;â token

The gist of it is, the type doesn't exist outside the template, so I can't instantiate the class of its own type.

As for what I'm trying to accomplish, imagine that I'm creating several "Mylist"-like classes (all derived from Chain) carrying different data (Mylist shows a single string being carried, but the classes in reality may carry several items like a struct would).  The idea being, of course, that the linked-list handling is dealt with in the parent class and the derived classes just deal with the actual data being kept in the list.    I don't want to have to repeat the add(), insertBefore() code in every class to cast to the new class's type.  I'd like to have them exist in one place and then have them work in every class.  If I can do it with templates, great.  If I have to use macros, hey, if the shoe fits...

---

### Post by aks44 on 2007-08-01
Seeing how you started it, you're headed for CRTP...

Your problem is that it must be Chain that is a template, not MyList.
And MyList will be public Chain<MyList>

In your current implementation of Chain, just make it template<class T> and replace all occurrences of Chain* / new Chain(...) with T* / new T(...).

Then discard the now useless **virtual** keyword in front of your list functions.

This should do the trick.

Now you won't need to rewrite the list functions in any Chain<T> descendant.

---

### Post by rjfioravanti on 2007-08-01
> **kpatz said:**
> I'm in the process of teaching myself C++, and in doing so am writing some basic classes so I can learn better than I would using the class libraries.

Right now I created a simple linked list class:

```
class Chain {
public:
  Chain *prev;
  Chain *next;

  Chain(void);
  virtual ~Chain(void);
  
  virtual Chain *insertBefore(void);
  virtual Chain *insertBefore(Chain *);
  virtual Chain *insertAfter(void);
  virtual Chain *insertAfter(Chain *);
  virtual Chain *add(void);
  virtual Chain *add(Chain *);
};
```

The Chain class simply handles the linked list, but doesn't carry any data.  To carry data, I'm creating derived classes such as this sample that stores a name in each linked list item (String objects):

```
class Mylist: public Chain {
public:
  String *listname;
  Mylist(void): Chain() { 
    listname = NULL;
  };
  Mylist(const Mylist &r): Chain() {
    listname = NULL;
    if (r.listname) listname = new String(*r.listname);
  };
  ~Mylist(void) {
    if (listname) delete listname;
  };
};

```

The problem I'm having is being able to use the Chain methods (that use Chain pointers) on Mylist objects.  In other words:

```

  Mylist *list = new Mylist();
  . . .
  Mylist *item = list->add();  // adds new item to chain

```

  The add() call gets an error because the compiler can't convert Chain* to Mylist*.


Since you have a concrete MyList class inheriting properties from a Chain class, you should instantiate a Chain class with the MyList constructor

example

```

Chain *list = (Chain*)new Mylist();
  . . .
  Chain *item = list->add();  // adds new item to chain

```

A good way to do this is have a static method in Chain class that returns a list instance of it, so you can do something like this

```

Chain * list = Chain :: createMyList();

```

But you may not want the Chain class to know about MyList so if you are going to use a static creation method you might want to put it somewhere else in some kind of factory

---

### Post by brooksbp on 2007-08-01
Why not store your data in the Chain class?? Keep It Simple Stupid (KISS)?

---

### Post by aks44 on 2007-08-01
> **brooksbp said:**
> Why not store your data in the Chain class?? Keep It Simple Stupid (KISS)?

Because (s)he wants the list routines to be reuseable? :p

---

### Post by brooksbp on 2007-08-01
You can still store the data in the Chain class, but use a template so it's reusable...

---

### Post by rjfioravanti on 2007-08-01
> **brooksbp said:**
> You can still store the data in the Chain class, but use a template so it's reusable...

But that data that he is using here will not apply to each implementation that uses Chain

---

### Post by kpatz on 2007-08-01
> **brooksbp said:**
> Why not store your data in the Chain class?? Keep It Simple Stupid (KISS)?Because I may want to store different types of data in different linked lists.  For example, one list might be strings, another might carry an int, a char*, and a couple longs in each item, another might carry apples, another oranges, etc.

I'm basically trying to encapsulate the maintenance of the linked list in Chain, and then using subclasses of Chain to carry whatever data elements need to be stored in the list.

And also because I'm a C++ noob and want to learn how to properly use  OO techniques in C++. :)

---

### Post by aks44 on 2007-08-01
So, what are the results of moving the template<class T> out of MyList into Chain? :p

---

### Post by brooksbp on 2007-08-01
> **kpatz said:**
> Because I may want to store different types of data in different linked lists.  For example, one list might be strings, another might carry an int, a char*, and a couple longs in each item, another might carry apples, another oranges, etc.

I'm basically trying to encapsulate the maintenance of the linked list in Chain, and then using subclasses of Chain to carry whatever data elements need to be stored in the list.

And also because I'm a C++ noob and want to learn how to properly use  OO techniques in C++. :)

duck typing :)

---

### Post by kpatz on 2007-08-01
> **aks44 said:**
> So, what are the results of moving the template<class T> out of MyList into Chain? :pI got it to work!  Thanks...

Here's a snippet of how I did it:

```
#include <stdio.h>

// Note - I left out Chain's implementation for brevity
template <class T>
class Chain {
protected:
  T *prev;
  T *next;

public:
  Chain(void);
  virtual ~Chain(void);  // needs to be virtual since I dynamic cast below
  
  T *insertBefore(void);
  T *insertBefore(T *);
  T *insertAfter(void);
  T *insertAfter(T *);
  T *add(void);
  T *add(T *);
  T *getNext(void);
  T *getPrev(void);
};

// here's one of Chain's methods, to show how I did it
template <class T>
T *Chain<T>::insertBefore(T *link)
{
  if (prev) prev->next = link;
  link->next = dynamic_cast<T *>(this);
  link->prev = prev;
  prev = link;
  return link;
}

// Here's a class derived from Chain, to show how I use derived classes
// to carry data in the linked list maintained by the Chain class
class Mylist: public Chain<Mylist> {
public:
  long iFlags;
  char *pattern;
  // Mylist constructor
  Mylist(void): Chain<Mylist>() { 
    iFlags = 0;
    pattern = NULL;
  };
  // Mylist copy constructor
  Mylist(const Mylist &p): Chain<Mylist>() {
    if (p.pattern)
      pattern = p.pattern; // don't mind this, I stripped out some custom code
    else
      pattern = NULL;
   iFlags = p.iFlags;
  };
  // Mylist destructor
  ~Mylist(void) {
    //if (pattern) delete pattern;  // don't mind this, I stripped out some custom code
   };
};

```

---

### Post by aks44 on 2007-08-02
Just a few comments:

- prev and next in Chain need not be protected, they should be private.
- You don't need a **dynamic_cast**, a **static_cast** will be more efficient. However you may want to keep your Chain destructor virtual so that you can destroy derived objects through a base class pointer.
- You don't need to test for a pointer to be non-null before deleting it, the **delete** keyword already takes care of that for you.

---

### Post by DavidBell on 2007-08-02
As others have said, and you have found, templates are the way to go. I can offer two hints for future

1. An easy way to do them is just get the class working with int or string, all in an .h file, then just search and replace 'int' with 'T'. It's remarkable how close this will get you to a working template ... probably only problm will be with undefined operators in member functions.

2. The other neat trick in templates is to declare 'pure virtual' functions (ie =0) in the template, and use 

```

template <class T>
class Chain 
{/// blah blah
  void PureFunction (T*) =0;
}

class MyChain : public Chain<MyClass>  
{// You must define implementaion of PureFunction here
     void PureFunction (MyClass*)
       {//etc
       }

} something;
```

instead of just

```
 MyChain<MyClass> something; 
```

It gives an extra level of flexibility, because to use the template, you are forced to define 'PureFunction'. An example would be if you have a generic Sort function in your Chain class, it in turn may call a "bool IsGreater(T*)" function. Simple ">" operator may not be appropriate for all classes, so by making IsGreater pure virtual in the template the user is forced to define an appropriate function for classes using the template.. MS ATL helper classes use this extensively and it's a pretty powerful concept I think.

DB

---

