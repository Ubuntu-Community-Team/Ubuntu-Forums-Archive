---
title: "Quik inheritance question (C++)"
date: 2010-01-30
forum: Programming Talk
---

### Post by Saxcore on 2010-01-30
Hi there. I've got a pretty straight forward question, however I seem to be struggling to find anything on the internet about it (although I'm probably searching for the wrong terms!)

Basically, must a derived class be a *direct* "descendant" of a base class in order to be used as a parameter to functions designed to take in the base class. I think I can elaborate without posting up any real code; say our "hierarchy" looks something like this:

```
**base_class**  -->  **derived_class_1**  -->  **derived_class_2**
```

..where derived_class_2 is derived from derived_class_1, which is derived from base_class. Somewhere in our code there is a function, that has a definition along these lines:

```
void foo(base_class)
```

Seeing as derived_class_1 could be passed as an argument to this function, I would have thought that derived_class_2 could, too. But, according to an application I'm writing, apparently not! Is the only way around this problem to derive derived_class_2 from base_class?

Cheers, Sam.

---

### Post by Queue29 on 2010-01-30
It depends on the type of inheritance you are using public, protected, or private. If you don't explicitly state something other than private, it defaults to private, in which case you cannot access anything but the public members of your base class.

---

### Post by Saxcore on 2010-01-30
Ah yeah, sorry for leaving that out, it's been a long day.

I'm using public inheritance in both instances, so all methods and attributes should be in the right places, seeing as there is nothing set as private.

Cheers, Sam.

---

### Post by dribeas on 2010-01-30
Any derived class, no matter how deep in the hierarchy (as long as it is accessible).

---

### Post by dwhitney67 on 2010-01-30
> **Saxcore said:**
> 
Seeing as derived_class_1 could be passed as an argument to this function, I would have thought that derived_class_2 could, too. But, according to an application I'm writing, apparently not!

Since you are using public inheritance, I then find your conclusions hard to fathom.

Here's the stupidest example I could come up while waiting to depart to collect a pizza I just ordered, and at the same time, under the influence of my avatar.  Play with it in your spare time.
```

#include <iostream>

class Base
{
public:
   Base() {}

   void doSomething() { std::cout << "doing something from Base" << std::endl; }

   void foo(const Base& b) { std::cout << "foo is doing nothing with the parameter; such a waste!" << std::endl; }
};

class SubclassA : public Base
{
public:
   SubclassA() : Base() {}
};

class SubclassB : public SubclassA
{
public:
   SubclassB() : SubclassA() {}
};

int main()
{
   SubclassB scb;

   scb.doSomething();

   scb.foo(scb);
}

```

---

### Post by Saxcore on 2010-01-30
Hey, thanks for your time guys. 

> Since you are using public inheritance, I then find your conclusions hard to fathom.

..Hmm, must be related to something else then. Something to do with virtual functions, perhaps? I have more of those than I feel comfortable with, at the moment.

..I'll look in to it now.

Cheers, Sam.

---

### Post by dwhitney67 on 2010-01-30
> **Saxcore said:**
> Something to do with virtual functions, perhaps?
Nope!

The application will perform only the actions that you, the programmer, has coded it to do.  The application will not develop a conscience of its own and start taking over the world.

---

### Post by Zugzwang on 2010-02-01
> **Saxcore said:**
> Seeing as derived_class_1 could be passed as an argument to this function, I would have thought that derived_class_2 could, too. But, according to an application I'm writing, apparently not! Is the only way around this problem to derive derived_class_2 from base_class?


Can you show us the compiler error you are getting? As already mentioned by dwhitney67, it doesn't matter for this question whether the functions are virtual or not.

---

