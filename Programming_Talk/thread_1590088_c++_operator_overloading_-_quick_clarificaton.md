---
title: "c++ operator overloading - quick clarificaton"
date: 2010-10-07
forum: Programming Talk
---

### Post by akvino on 2010-10-07
FROM wiki:
[PHP]
class My_Array 
{
 
    int * array;
    int count;
 
public:
 
    My_Array & operator = (const My_Array & other)
    {
        if (this != &other) // protect against invalid self-assignment
        {
            // 1: allocate new memory and copy the elements
            int * new_array = new int[other.count];
            std::copy(other.array, other.array + other.count, new_array);
 
            // 2: deallocate old memory
            delete [] array;
 
            // 3: assign the new memory to the object
            array = new_array;
            count = other.count;
        }
        // by convention, always return *this
        return *this;
    }
 
    ...
 
};
[/PHP]

Few questions:
1) Someone please explain this - "if (this != &other) // protect against invalid self-assignment". I think this stands in order to prevent potential recursive call to itself, there for infinite loop - but would like clarification.

2) Which array - the other.array or this.array? Is this correct way of doing it? Elaborate if you can - thanks?
// 2: deallocate old memory
            delete [] array;// 2: deallocate old memory

---

### Post by dwhitney67 on 2010-10-07
Well, for starters, your code is fine as is.

For question 1:

You will not have to worry about recursive calls, since you are comparing pointers, not MyArray objects, using the != operator, for which you have not implemented.  And even if you did, the issue is moot because of the pointer comparison.

For question 2:

Delete the array that is no longer of interest; in other words, what you have is correct.

---

### Post by GeneralZod on 2010-10-07
Re: #1 - in general, it's pretty good practice to do this check*  both for efficiency reasons (in the example you gave, assigning to oneself without this check would unnecessarily do a lot of allocation, deallocation, and copying of objects) and often for correctness.

In your specific example, correctness is not an issue, but consider what would happen if you moved the delete[] array to *before* the std::copy statement and didn't guard against self-assignment.


* Meyers recommends it in "Effective C++", for example.

---

### Post by akvino on 2010-10-07
> **dwhitney67 said:**
> Well, for starters, your code is fine as is.

For question 1:

You will not have to worry about recursive calls, since you are comparing pointers, not MyArray objects, using the != operator, for which you have not implemented.  And even if you did, the issue is moot because of the pointer comparison.



Please provide a little bit wider explanation (such as - when is this not OK, or when do I need to worry about it)?

---

### Post by akvino on 2010-10-07
> **GeneralZod said:**
> Re: #1 - in general, it's pretty good practice to do this check*  both for efficiency reasons (in the example you gave, assigning to oneself without this check would unnecessarily do a lot of allocation, deallocation, and copying of objects) and often for correctness.

In your specific example, correctness is not an issue, but consider what would happen if you moved the delete[] array to *before* the std::copy statement and didn't guard against self-assignment.


* Meyers recommends it in "Effective C++", for example.
I get what it's doing, I am just wondering when calling
delete [] array; 
Is that the same as 
delete [] this.array;

---

### Post by dwhitney67 on 2010-10-07
No it is not the same; the latter will yield a compiler error.  Perhaps you meant to ask if these are the same:
```

delete [] array;

delete [] this->array;

```
In such case, yes they are.  Use the keyword "this" to reference member data only in cases where you need distinguish the member data from a local variable.  For example:
```

class MyClass
{
   int value;

public:
   MyClass(int value)
      : value(value)     // special case where use of this-> is not required.
   {
   }

   void setValue(int value)
   {
      this->value = value;     // need to distinguish one var from another
   }

   int getValue() const
   {
      return value;   // could use this->, but what's the point.
   }
};

```

---

### Post by dwhitney67 on 2010-10-07
> **akvino said:**
> Please provide a little bit wider explanation (such as - when is this not OK, or when do I need to worry about it)?

It is ALWAYS ok to perform.  Why would want to waste CPU cycles copying the same object onto itself?  Maybe you did not understand this, but that was what GeneralZod was implying.

What I was stating was that you are comparing two pointers!  You were not comparing two objects.  There's a difference between:
```

if (this != &other)

```
and
```

if (*this != other)

```

---

### Post by akvino on 2010-10-07
> **dwhitney67 said:**
> It is ALWAYS ok to perform.  Why would want to waste CPU cycles copying the same object onto itself?  Maybe you did not understand this, but that was what GeneralZod was implying.

What I was stating was that you are comparing two pointers!  You were not comparing two objects.  There's a difference between:
```

if (this != &other)

```
and
```

if (*this != other)

```

Gotcha - all clear now. Everything is the way I understand it, just wanted to make sure.

---

