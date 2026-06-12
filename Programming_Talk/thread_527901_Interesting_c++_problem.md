---
title: "Interesting c++ problem"
date: 2007-08-17
forum: Programming Talk
---

### Post by aquavitae on 2007-08-17
Hi all

I'm attempting to write a class that basically does the following:
```

template<typename T>
class my_class {
   T m_val;
public:
   void set(T value) {
      m_val = val;
   }
};

```There's more to it, but thats the part I'm stuck on.  What I want to do is to allow the class that owns an instance of my_class to intervene in the set() function and permit the change.  For example, only allow the value to be set if a certain external condition is met.  Basically, I want to do this:
```

void my_class::set(T value) {
   m_value = request_change(value, m_value);
}

class owner_class {
   my_class<int> a;
   my_class<char> b;

   int request_change_a(int, int) {
      ...
   }
};

```Obviously the code I wrote won't work as I want because request_change_a cannot be seen from within my_class, and even if it could it would't know which instance to work with.  

Two options I thought of are to either use boost::signals or to put a pointer to request_change as a template argument of my_class.

The problem with boost::signals is that it will allow any number of request_change functions to be used on one instance of my_class (I only want one), and it will also allow any function that can see the instance of my_class access to it (I want it to be accessible only from owner_class).  

The problem with a template argument is that I don't think its syntactically possible to use a function pointer as a template argument.

Does anyone have any other ideas, or know how to use a function pointer as a template argument?

---

### Post by -Rick- on 2007-08-17
I made a little test program which I think does what you want, see attachment. (Renamed to .txt because .cpp isn't allowed)

---

### Post by aquavitae on 2007-08-17
Thanks for your reply.

That's almost what I'm after, but the problem is that the return value of request_change() could depend on other variables (some private) within the Owner class, e.g.
```

class Owner {
   bool state;
public:
   int request_change(int val, int newval) {
      if (state)
         return val;
      else
         return newval;
   }
};
```
But I can't use a pointer to a member function.

---

### Post by -Rick- on 2007-08-17
> **aquavitae said:**
> Thanks for your reply.

That's almost what I'm after, but the problem is that the return value of request_change() could depend on other variables (some private) within the Owner class, e.g.
```

class Owner {
   bool state;
public:
   int request_change(int val, int newval) {
      if (state)
         return val;
      else
         return newval;
   }
};
```
But I can't use a pointer to a member function.

You can use a pointer to member function in C++, with a little extra work:

```

#include <iostream>

template <typename T, typename C> class my_class
{
    T var;
    C *request_change_class;
    
    typedef T (C::*func_type)(T, T);
    func_type request_change_func;
    
public:
    my_class(C *c, func_type f) : request_change_class(c), request_change_func(f) {}
    
    void set(const T newvar)
    {
        var = (request_change_class->*request_change_func)(var, newvar);
    }
    T get(void) { return var; }
};


// Demo class, chowing various ways
class TheOwner
{
    bool flag;
    
public:
    TheOwner(void) : flag(true)
    {
        my_class<int, TheOwner> c(this, &TheOwner::OwnChecker);
        c.set(5);
        std::cout << c.get() << '\n';
    }
    
    int OwnChecker(int var, int newvar) { return (flag) ? newvar : var; }
};

int main()
{
    TheOwner owner;
    return 0;
}

```

---

### Post by aquavitae on 2007-08-17
Great! I didn't know you could do that - useful. Thanks for the help!

---

### Post by the_unforgiven on 2007-08-17
This is a very very good read:
[http://www.newty.de/jakubik/callback.html](http://www.newty.de/jakubik/callback.html)

It explains the various design patterns of callbacks in C++.

HTH ;)

---

### Post by aks44 on 2007-08-17
This article relies on dirty but clever hacks, you may want to have a look at it: [http://www.codeproject.com/cpp/FastDelegate.asp](http://www.codeproject.com/cpp/FastDelegate.asp)

The author was able to implement generic delegates that are both efficient and portable, at the expense of bypassing the standard.

> Because it relies on behavior that is not defined by the standard, I've been careful to test the code on many compilers. Ironically, it's more portable than a lot of 'standard' code, because most compilers don't fully conform to the standard. It has also become safer through being widely known. The major compiler vendors and several members of the C++ Standards commitee know about the techniques presented here (in many cases, the lead compiler developers have contacted me about the article). There is negligible risk that vendors will make a change that would irreparably break the code.


Kinda the same spirit as boost IMHO.

---

