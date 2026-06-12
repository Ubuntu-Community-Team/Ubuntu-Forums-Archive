---
title: "[C++] Initiating a pointer var to be a copy of another pointer var"
date: 2008-08-21
forum: Programming Talk
---

### Post by NovaAesa on 2008-08-21
Hi,

say I have a variable declared as follows:
```
myType* var1 = new myType(50);
```

I want to create another pointer that will point to a copy of what var1 is pointing to. So far, the only way I have found of doing this is:
```
myType* var2 = new myType();
*var2 = *var1
```

I'm wanting to know if there is a more efficient or "better" way of doing it. How I have it at the moment doesn't seem that great, because a new object is being created (just for the sake of allocating memory) and then being overwritten straight away. This seems a bit wasteful to me. Does anyone know a better way?

I have already tried doing:
```
myType* var2;
*var2 = *var1
```
but of course this results in a seg fault.

---

### Post by loganwm on 2008-08-21
I'm on my pocket pc currently so I can't test your code, but have you tried using an address operator [&]?

---

### Post by Npl on 2008-08-21
the most sensible operation would be to use the Copy-Constructor. This allows you to initialise more efficiently.```
myType* var2 = new myType(*var1);
```

---

### Post by NovaAesa on 2008-08-21
A copy constructor sounds like a good idea. I would just have to loop around with everything in there are copy in manually. I can even reuse the code from my overloaded assignment opperator. Thanks for the tip =]

---

### Post by Npl on 2008-08-22
If you already manually overloaded the assignment operator, then you should overload the Copy-Constructor for the same reasons. But you do know that both assignment and copy-constructer have a default (to copy all member variables) - ie. you dont have to define them to use them ?

---

### Post by NovaAesa on 2008-08-22
I didn't realise that, I'll keep that in mind for next weeks lessons (I'm learning C++ at uni).

---

### Post by hod139 on 2008-08-22
> **NovaAesa said:**
> Hi,

say I have a variable declared as follows:
```
myType* var1 = new myType(50);
```I want to create another pointer that will point to a copy of what var1 is pointing to. 

I'm not sure what you are asking.  If you want to create a copy of what the pointer is pointing too, then NPL's solution will work.  If you just want to have a copy of the pointer, then that's not what you have done.


Here is some example code that creates a copy of the pointer, and a copy of what the pointer points too.  Since the only data in the myType class is a primitive, I did not need to write a copy constructor, assignment operator, nor destructor.
[php]
#include <iostream>

struct myType{
  explicit myType(int data_) : data(data_) {}
  int data;
};

int main(){
   myType* var1 = new myType(50);
   myType* p_var1(var1);
   myType* copy_var1 = new myType(*var1);

   std::cout << "var1->data = " << var1->data << "\n";
   std::cout << "p_var1->data = " << p_var1->data << "\n";
   std::cout << "copy_var1->data = " << copy_var1->data << "\n\n";

   delete var1; // invalidates p_var1
   
   std::cout << "p_var1->data = " << p_var1->data << "\n";
   std::cout << "copy_var1->data = " << copy_var1->data << "\n";
   
   delete copy_var1; // memory management

   return 0;
}
[/php]

---

### Post by kpatz on 2008-08-22
To the original poster: one thing that isn't clear to me:  Are you looking to point to another copy of the data, or do you want two pointers pointing to the SAME copy of the data?

If you want two copies of the object, you will have to allocate 2 copies (like you do in your first example).  Use a copy constructor, then you can do this:

```

myType* var1 = new myType(50);
myType* var2 = new myType(*var1);

```

Now you'll have two instances of myType with the same data in them, but are independent (overwriting one won't affect the other).

If you want to have two pointers to the same instance of the object, like your 2nd example (the one that segfaults), do it like this:

```

myType* var1 = new myType(50);
myType* var2 = var1;  // note no *s

```

Yours segfaulted because you were dereferencing var2 without initializing it.  Here, we're just copying the pointer, not the object, so var1 and var2 point to the same copy of the data.

---

