---
title: "C++ Inheritance/object memory/pointer casting question"
date: 2010-03-27
forum: Programming Talk
---

### Post by PanP5 on 2010-03-27
I've been playing with some code to better understand how inheritance works, and ran into an issue that has stumped me.

I have a method, output(), that is defined in my base class and overridden in my derived class.

The base class' output() outputs the string "base".
The derived class' output() outputs the string "level1".

In my code, I declare an object of the base class type. I also declare a pointer of the level1 type.

I have the level1 pointer point to the instance of the base class object using the & operator in front of the instance name and casting the address of type "level1":

```
p1 = (level1*)&b; //the level1 pointer is pointing to a base class object
```

Doing this, the code p1->output() outputs the string "level1".


How is this possible?? I understand that the pointer type usually determines which version of a method to run, but in this case, the object in question (the instance of the base class object) shouldn't have access to level1 implementation of output()! **How does the compiler memory allocation work in this case?**

Below is the the code, below that is the output:

```
#include <iostream>
using namespace std;

class base{
   public:
   void output(){cout << "base \n";}
};

class level1 : public base{
   public:
   void output(){cout << "level1 \n";}
};

int main()
{
   base b, *p = 0;
   level1 l1, *p1 = 0;

// using the base pointer
   p = &b;
   p->output();

   p = &l1;
   p->output();

   cout << "End Base Pointer\n";

// using the level1 pointer
   p1 = (level1*)&b; //the level1 pointer is pointing to a base class object
   p1->output(); //shouldn't this output "base"?
   
   p1 = &l1;
   p1->output();


   cout << "End L1 pointer\n";

   return 0;
}

```

Output:

base 
base 
End Base Pointer
level1 
level1 
End L1 pointer

---

### Post by WillFerrellLuva on 2010-03-27
I'm no expert but if you want to be able to correctly use p1 to point to different data types shouldnt you make p1 a void pointer?

---

### Post by MadCow108 on 2010-03-27
functions usually lie in some global static memory accessible from everything in the process (on machine code level)
So you can call any function at any time and from any context. Machine code has no concept of objects.

So by that cast you tell the compiler that the pointer p1 points to a level1 object and thus it will call the function associated to level1.

This is of course wrong and only works because level1 also has a function with that name, but the compiler just assumes the programmer knows what he's doing in most cases.

if you would add a virtual to the function definitions you would tell the compiler to check the type of the object at runtime and call the member function of the type it really is.

---

### Post by PanP5 on 2010-03-27
> **WillFerrellLuva said:**
> I'm no expert but if you want to be able to correctly use p1 to point to different data types shouldnt you make p1 a void pointer?

I'm not trying to accomplish anything with the code; I'm just trying to really strengthen my understanding of C++. (I'm on a job search right now, and the screening tests have a LOT of curveballs).

That said, I just tried:

void *vp = &b;
vp->output();

It didn't compile. The compiler complained about that second line: "error: ‘void*’ is not a pointer-to-object type"

---

### Post by PanP5 on 2010-03-27
Thanks **MadCow**!

---

### Post by PanP5 on 2010-03-27
> **MadCow108 said:**
> So by that cast you tell the compiler that the pointer p1 points to a level1 object and thus it will call the function associated to level1.

This is of course wrong and only works because level1 also has a function with that name, but the compiler just assumes the programmer knows what he's doing in most cases.

I just tried adding a method unique to level1, and called it using a level1 pointer pointing to the base class object. It worked. I guess, casting in that manner, whatever object is *actually* pointed to is almost irrelevant. (I imagine I'd run into an error if I tried updating a variable unique to level1, though).

I rewrote the code using dynamic_cast. It compiled, with a warning and, when run, seg faulted right at the bit of code I was asking about.

In this case, what bit of memory was the code trying to access to cause this fault?

---

### Post by WillFerrellLuva on 2010-03-27
think I misunderstood what you were doing there.

You can use a void pointer to point to both though, just have to cast it into the correct type before you deference it:

```

#include <iostream>
using namespace std;

class base{
   public:
   void output(){cout << "base \n";}
};

class level1 : public base{
   public:
   void output(){cout << "level1 \n";}
};

int main()
{
   base b;
   level1 l1;
   void* vp;

   vp = &b;
   static_cast<base*>(vp)->output();

   vp = &l1;
   static_cast<level1*>(vp)->output();

   return 0;
}

```

Ill be quite now.

---

### Post by PanP5 on 2010-03-27
> **PanP5 said:**
> I rewrote the code using dynamic_cast. It compiled, with a warning and, when run, seg faulted right at the bit of code I was asking about.

In this case, what bit of memory was the code trying to access to cause this fault?

Figured it out. I just remembered that dynamic_cast, when it fails, sets the pointer value to 0 and throws an exception. I didn't bother catching the exception, nor did I check the pointer value, so I was trying to interact with memory address "0", causing the seg fault :)

> **WillFerrellLuva said:**
> think I misunderstood what you were doing there.

You can use a void pointer to point to both though, just have to cast it into the correct type before you deference it

Thanks for the input!

---

### Post by dwhitney67 on 2010-03-27
> **PanP5 said:**
> I just remembered that dynamic_cast, when it fails, ... throws an exception.

That's news to me.  Can you show me how you got it to throw an exception?

---

### Post by MadCow108 on 2010-03-27
note that this behavior may be implementation dependent. I don't think the standard dictates to handle this situation like that

A compiler could place virtual function call tables in or near the objects even when the object is not polymorphic or use some other object <-> member function relation which could resolve this kind of thing or even figure out the the programmer made an mistake in the first place.

@ dwhitney
dynamic cast throws bad_cast when dealing with references:
[http://www.cplusplus.com/reference/std/typeinfo/bad_cast/](http://www.cplusplus.com/reference/std/typeinfo/bad_cast/)
with pointers it just sets them to NULL

---

### Post by dwhitney67 on 2010-03-27
> **MadCow108 said:**
> 
@ dwhitney
dynamic cast throws bad_cast when dealing with references:
[http://www.cplusplus.com/reference/std/typeinfo/bad_cast/](http://www.cplusplus.com/reference/std/typeinfo/bad_cast/)
with pointers it just sets them to NULL
Thanks, but I knew this.  I was wondering how did the OP got the dynamic cast to throw an exception when he was assigning to a pointer.  I guess he merely misstated something.

---

