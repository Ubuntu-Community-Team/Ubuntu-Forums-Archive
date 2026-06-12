---
title: "Question about exception handling in functions returning values."
date: 2009-08-10
forum: Programming Talk
---

### Post by pepperphd on 2009-08-10
While writing my own container class (for learning purposes) I came across a problem that caused a segmentation fault.  Misusing [] easily crashed the program, so I decided to create an exception to handle these cases, instead of crashing the program.  I'm wondering if this is common practice, or if I should just let it crash the program. Below is the exception. It returns a junk reference.

[php]
typedef unsigned long long ull;
       class LTYPE & operator [] (ull index) const
            {
                try
                {
                    if(index > size() || empty()) throw OVERRUN;
                    const List_element<LTYPE>*current = lcc(head);
                    for(; index; index--) current = lcc(current)->get_next();
                    return current->data;
                }
                catch(int i)
                {
                    static class LTYPE junk;
                    if(i == OVERRUN) cout << "overrun []. use +=. returning to caller with junk reference" << endl;
                    return junk;
                }
            }[/php]

---

### Post by dwhitney67 on 2009-08-10
Checking an index boundary, and throwing an exception if it is out of bounds is not uncommon.  What is unusual is for the function to catch this type of exception; it shouldn't.  Let the exception propagate back to the caller (of the function).

(Btw, it is also uncommon for one to use the keyword 'class', other than when declaring one.)

The other thing you should check before you begin indexing your list is that there is indeed a valid pointer through which to navigate to the next list item.  But perhaps you feel safe that if you have an N number of elements, then you must also have an N number of pointers to objects.

What type of container is it that you are attempting to create?  Is it a list?


P.S.
```

SomeType& MyClass::operator[](const unsigned long long& index) const
{
   if (index >= MaxElements)
   {
      throw OutOfRangeException("Index is out of range.");
   }

   // ...

   return element;
}

```

---

### Post by schmendrick on 2009-08-10
i'd say this depends on your approach and philosophy to programming, plus on the purpose of your code. (in embedded projects or apps that need to be quick you will normally avoid exceptions because of speed). 
additionally many c++ programmers detest exceptions. i think this is mostly because most of them come from the c side.
on the other hand i have observed people having learned java or another managed language as their first programming language do have a certain affection to exceptions :)


i'd say letting the program crashing is surely not a good idea. 



but i personally wouldnt use your approach: 


let the caller handle the exception (meaning i wouldnt catch the exception myself but let the caller catch it). catching it yourself and returning "junk" is the worst of two worlds: 
first you are much slower than you need to be:
you are using "slow" exceptions plus the caller needs to check if returned stuff is junk or valid (which he may forget). plus you need to instantiate the "junk" before you return it. 
second i already said: caller needs to check if returned stuff is junk or valid. 

i'd  use your approach only if i have a very long method (for the sake or readability) or in case i need to rewind something. 

```

typedef unsigned long long ull;
       class LTYPE & operator [] (ull index) const
            {
                    if(index > size() || empty()) throw OVERRUN;
                    const List_element<LTYPE>*current = lcc(head);
                    for(; index; index--) current = lcc(current)->get_next();
                    return current->data;
              }

```


if you dont want to use exceptions just return junk directly.


hope this helps

---

### Post by schmendrick on 2009-08-10
ok, dwhitney67 is a more quick writer than me ;)

---

### Post by dwhitney67 on 2009-08-10
> **schmendrick said:**
> ok, dwhitney67 is a more quick writer than me ;)
Perhaps, but you gave a better description of why the OP should not catch his own exception.

---

### Post by pepperphd on 2009-08-10
>  What type of container is it that you are attempting to create?  Is it a list?

Yes it is just a list.  I started it to write an iterator class but I went beyond to try to learn other concepts which happened to include exception handling. Thanks for the replies.

---

### Post by nvteighen on 2009-08-10
Hm... in addition to the above, maybe it can be helpful to understand what an interface is. Before considering this post to be offtopic, please read it :) (it may be offtopic, though... but I think it's not :p)

A function's or a class's interface is how it connects to the "outside". In this case, we're looking at a function (ok, it's a method, but methods are functions). The way a function connects to the "outside" is usually through its parameters and return values.

So, if we have a function with interface **int *myfunc(SomeClass&, double);** (Yes, that looks like a header declaration, right? Well, headers set interfaces), it doesn't matter how its implemented, if using algorithm X or algorithm Y: if the interface is kept, then you'll be able to "connect" to this function without caring what happens inside.

Ok, how is this related to exceptions? Well, in languages that support them, exceptions are like another piece of the function's interface. Sadly, the header definition won't tell us what exceptions a certain function can throw/raise, but the API docs will (and should): "When this error happens, the function will throw this exception".

If you see it that way, you may get better why usually exceptions are caught at the caller. And also, why it makes returning a "junk" value usually irrelevant: you're already "returning" the exception...

---

