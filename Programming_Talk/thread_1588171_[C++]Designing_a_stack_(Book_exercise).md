---
title: "[C++]Designing a stack (Book exercise)"
date: 2010-10-04
forum: Programming Talk
---

### Post by xnerdx on 2010-10-04
I'm reading the book Practical C++ Programming and it's currently stepping into discussing simple classes. To convey the idea it's describing how to create a simple stack using structures and later it will discuss preforming the same action with classes. I understand both classes and structures but I'm curious about whether this code is writen correctly. The following code is quoted from the book, I don't own any of the following code:
**Structure declaration**
```

const int STACK_SIZE = 100;     // Maximum size of a stack 

// The stack itself 
struct stack { 
   int count;                   // Number of items in the stack 
   int data[STACK_SIZE];        // The items themselves 
};

```
**Pop function**
```

inline int stack_pop(struct stack& the_stack) 
{ 
    // Stack goes down by one 
    --the_stack.count;

    assert((the_stack.count >= 0) && 
           (the_stack.count <
                  sizeof(the_stack.data)/sizeof(the_stack.data[0])));
    // Then we return the top value 
    return (the_stack.data[the_stack.count]); 
}

```
I haven't tested it but my assumption is that using the stack_pop function will return the 2nd vaule in the stack, not the first; seeing as the stack count is decremented by one prior to determining the top most item. Is my assumption correct or am I looking at this the wrong way...

EDIT: I figured it out... I feel stupid now. The "top-most" data member (the member at count prior to decrementing the count by one) is not set to anything yet. The push function allocates a new, empty data spot after it's called. Therefore, the top-most (existing) data member is at [count-1]. I apologize for posting without thinking :'(. Hopefully someone can benifit...

---

### Post by schauerlich on 2010-10-04
the_stack.count is the number of items in the stack. Therefore, used as an index, it will point to one *past* the last item in the array when stack_pop() is entered. It's decremented to what the count will be *after* the pop, and is then used as an index for the item at the end of the array/top of the stack.

---

### Post by dwhitney67 on 2010-10-04
I sure hope the book you are reading (Practical C++ Programming) indicates somewhere in the text that structs and classes are identical in every way, with the exception that by default, member data and methods that are declared within a class are considered private.  In a struct, they would be public.

Thus, this would be legal C++:
```

struct stack {
   // data members
   int count;                   // Number of items in the stack 
   int data[STACK_SIZE];        // The items themselves

   // constructor
   stack();

   // method(s)
   void push(int value);
   int pop();
};

...

stack::stack()
   : count(0)
{
}

void stack::push(int value)
{
   // ...
}

int stack::pop()
{
   if (count == 0)
   {
      // handle error; use assert() or throw an exception
   }

   return data[--count];
}

```

---

### Post by xnerdx on 2010-10-13
> **dwhitney67 said:**
> I sure hope the book you are reading (Practical C++ Programming) indicates somewhere in the text that structs and classes are identical in every way, with the exception that by default, member data and methods that are declared within a class are considered private.  In a struct, they would be public.

Thus, this would be legal C++:
```

struct stack {
   // data members
   int count;                   // Number of items in the stack 
   int data[STACK_SIZE];        // The items themselves

   // constructor
   stack();

   // method(s)
   void push(int value);
   int pop();
};

...

stack::stack()
   : count(0)
{
}

void stack::push(int value)
{
   // ...
}

int stack::pop()
{
   if (count == 0)
   {
      // handle error; use assert() or throw an exception
   }

   return data[--count];
}

```

As already mentioned I figured out my own stupidity but I'd like to mention that the book does indeed elaborate on the fact that structures and classes are relatively the same thing accept for the access permissions.

---

