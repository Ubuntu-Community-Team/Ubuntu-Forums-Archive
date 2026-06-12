---
title: "[C++] Class-key error"
date: 2009-07-21
forum: Programming Talk
---

### Post by wbest on 2009-07-21
Riddle me this, my brethren!

g++ gives me the error

error: a class-key must be used when declaring a friend

So I go to the line it refers to

```
class __XAuto; 
 
  typedef XSingleton<TYPE>            __singleton; 
 ** friend typename __singleton::__XAuto;**
```

I've read it needs to have "class" jammed in there.  So I do that.

```
  friend class typename __singleton::__XAuto;
```

Then I get this from g++

error: expected identifier before ‘typename’
error: multiple types in one declaration
error: friend declaration does not name a class or function

Okay, so maybe I put it in the wrong place.

>   class friend typename __singleton::__XAuto;

error: expected identifier before ‘friend’
error: multiple types in one declaration
error: friend declaration does not name a class or function


Huh...the same error.  And apparently the friend declaration does not name a class.
But I've already been told I need a class key with a friend.

What do I do?  WHAT DO I DO!?

---

### Post by Habbit on 2009-07-21
I _think_ that the "class" keyword makes the "typename" declaration unnecessary.

---

### Post by dribeas on 2009-07-22
A little more context would be appropriate. Some things you may want to know:

You cannot define argument-dependent types friends in a template declaration:

```

template <typename T>
struct X {
   friend class T; // error
   typedef typename T::internal_type other_type;
   friend class other_type; // error
};

```

Typename shall only be used in template declarations and definitions (C++2003, 14.6 par 5). In a template parameter declaration, there is no semantic difference between class and typename.

```

template <typename T> struct X; // equivalent to template <class T> ...
template <typename T> typename T::value_type f( typename T::value_type const & arg) // correct
{
   typedef typename T::value_type value_type;
   typename T::value_type tmp(arg); // correct and required
   return tmp;
};

```

Then again, the comeau compiler (closest thing to an executable version of the standard) does allow some other uses, so I might have misinterpreted the standard in this last limitation.

---

### Post by wbest on 2009-07-22
Yeah, I replaced the "typename" with "class" and it worked.
Thanks.
 
Also, yes, it was in a template.

---

