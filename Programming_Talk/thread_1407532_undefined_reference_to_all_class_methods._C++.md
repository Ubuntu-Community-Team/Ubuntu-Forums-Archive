---
title: "undefined reference to all class methods. C++"
date: 2010-02-15
forum: Programming Talk
---

### Post by tbastian on 2010-02-15
I'm writing a c++ data structure and I declared my class in a header file, my declaration in  a .cpp file and I'm trying to use the class in a test file. The compiler gives me the error:

undefined reference to `ElasticArray<float>::ElasticArray(int)'

and similar errors for every other method I try to use, including the destructor which I don't explicitly call (I assume it is called by default at the end of a program...). I found an FAQ [HERE]("http://gcc.gnu.org/faq.html#vtables"), which looks like my problem, but I didn't declare anything as virtual!

any ideas?

I'm using Eclipse which compiles with g++.

---

### Post by Zugzwang on 2010-02-15
Definitions of templated functions should reside in header files and not in ".cpp"-files. Try moving it there.

Reason: Code for concrete instantiations of templated classes is generated upon use.

---

### Post by tbastian on 2010-02-15
is there any way around that? such as declaring them as inline?

---

### Post by Zugzwang on 2010-02-15
> **tbastian said:**
> is there any way around that? such as declaring them as inline?

No. The compiler doesn't remember for which template parameters it still has to generate code for. However, you could add some function to your .cpp file containing a function which is not called later that instantiates a object of your template class for all template parameters used. But that's a not-so-nice hack. Non-working example:

```

#include "myTemplate.hpp"

template void MyTemplate<typename T>::myFunction() {
   // foo
}

// ... other functions ...

// Helping function
void my_helper_function() {
  MyTemplate<int> t;
  MyTemplate<char> t2;
}

```

---

### Post by dwhitney67 on 2010-02-15
> **tbastian said:**
> is there any way around that? such as declaring them as inline?

Only two ways I know of... the way Zugzwang suggested, or adding the methods to a separate file... which is not compiled directly, but is included within the header file.

You're using an IDE; so I do not know if it tolerates 'tricks' such as I suggested.  But in a nutshell:

MyTemplate.h:
```

#ifndef MYTEMPLATE_H
#define MYTEMPLATE_H

...

template <typename T>
class MyTemplate
{
public:
   ...

   void ElasticArray(int val);

   ...
};

// here you include the implementation of the template's methods
#include "MyTemplate.impl"

#endif

```

MyTemplate.impl
```

template <typename T>
void
MyTemplate<T>::ElasticArray(int val)
{
   ...
}

```

P.S.  I do not work with templates every waking minute of the day; forgive me if there is a syntax error above.

---

### Post by tbastian on 2010-02-15
> **dwhitney67 said:**
> Only two ways I know of... the way Zugzwang suggested, or adding the methods to a separate file... which is not compiled directly, but is included within the header file.

You're using an IDE; so I do not know if it tolerates 'tricks' such as I suggested.  But in a nutshell:

MyTemplate.h:
```

#ifndef MYTEMPLATE_H
#define MYTEMPLATE_H

...

template <typename T>
class MyTemplate
{
public:
   ...

   void ElasticArray(int val);

   ...
};

// here you include the implementation of the template's methods
#include "MyTemplate.impl"

#endif

```

MyTemplate.impl
```

template <typename T>
void
MyTemplate<T>::ElasticArray(int val)
{
   ...
}

```

P.S.  I do not work with templates every waking minute of the day; forgive me if there is a syntax error above.


Thanks, but I get an error saying that all my methods have already been defined. If I remove them from the class file it complains that they aren't class methods!

The way Zugzwang suggested works (I think, I have different errors now which I'm working through...). Thank-you for your replies!

---

### Post by dwhitney67 on 2010-02-15
> **tbastian said:**
> Thanks, but I get an error saying that all my methods have already been defined. If I remove them from the class file it complains that they aren't class methods!

The way Zugzwang suggested works (I think, I have different errors now which I'm working through...). Thank-you for your replies!

You probably had a typo or something related.  It seems that you do not quite have a full understanding of templates.  If you wish to proceed and simply ignore the cause of the errors you had, then so be it.

---

### Post by tbastian on 2010-02-16
> **dwhitney67 said:**
> You probably had a typo or something related.  It seems that you do not quite have a full understanding of templates.  If you wish to proceed and simply ignore the cause of the errors you had, then so be it.

I got it to work now. Thank you.

---

