---
title: "C++, templates and arrays of pointers"
date: 2013-06-14
forum: Programming Talk
---

### Post by Dirich on 2013-06-14
Hi,

I have a small header where I defined some functions to manage dynamic arrays I need. One of these functions is:

```

/*!
    This subroutine increases the size of a dynamic array by 1 and writes data at such location, effectively
    implementing an append instruction.
    @params:
    Target:        IN        current array
    Array_Size:    IN        size of the current array
    Appendee:    IN        data to append to the array

    @return:            pointer to the extended array
*/
template <typename ArrayType, typename SizeType>
inline ArrayType* Array_Append (ArrayType* Target, SizeType& Array_Size, ArrayType& Appendee)
{
    ArrayType* tmp;
    tmp = new ArrayType [Array_Size + 1];
    memcpy (tmp, Target, Array_Size * sizeof (ArrayType));

    delete [] Target;

    tmp [Array_Size] = Appendee;
    Array_Size++;

    return tmp;
}
```

As it happens, it turns out that I am mostly using this with ArrayType = StructuredType*, where StructuredType is a structure. I.e.

```

struct TT
{int a;}

```

In the code something like this happens:

```

TT** Array (NULL);

int Elements (0);

Array = new TT* [1];
++Elements;

TT* AppendOneOfThese = new TT [10];

// I want to append a pointer to the 4th element of AppendOneOfThese in Array
Array_Append (Array, Elements, &AppendOneOfThese [3]);

```
 
The compiler gives me the following error:
```

error: no matching function for call to ‘Array_Append(TT**&, unsigned int&, TT*)’
note: candidates are: ArrayType* Array_Append(ArrayType*, SizeType&, ArrayType&) [with ArrayType = TT*, SizeType = unsigned int]

```

Actually, it only gives me this error on one line, in a new function. The 7 other times I use it on different types and different functions it gives me no problem (although I remember seeing this error on those too the first time I was debugging them).
So, I smell some error by my part... is Array_Append ok? Why does it searches for a function where its first parameter is TT**& instead of TT**?

---

### Post by PaulM1985 on 2013-06-14
I think you are looking for
Array_Append<TT*>(YOUR ARGS);
So that you are specifying the type for your template.
Paul

---

### Post by Dirich on 2013-06-14
First of all, thanks for the help.
Although you are right in saying I'm not specifying the template argument, the compiler deduces it correctly itself, so the problem is not that.
Proof is the second line (the "note" one) or the fact that it works perfectly on the other 7 instances I mentioned.
Anyway, once I followed your suggestion, the compiler gave the same output (without the hypotesis on the type, since now I've specified it, of course):

```


error: no matching function for call to &#8216;Array_Append(TT**&, unsigned int&, TT*)&#8217;
```

Once again, it adds an & after TT**.


UPDATE:
There is a difference between the two cases, the one in which everything works and the one when I get the error. In the first case the Appendee is a pointer to a dynamic struct, the other time it is a pointer to struct in a dynamic array (&otherArray [item_number]). But in the end they are both pointers to a certain kind of struct, the fact that one is standalone and the other is in a collection (array) should not matter. Also, this is the 3rd field, the compiler is making funny stuff with the first one.
Or so I thought...

This does not spawn the error:
```


TT** Array (NULL);
int Elements (0);

Array = new TT* [1];
++Elements;

TT* AppendThis = new TT;

Array_Append (Array, Elements, AppendThis);

```

This does spawn the error

```


TT** Array (NULL);
int Elements (0);

Array = new TT* [1];
++Elements;

TT* AppendOneOfThese = new TT [10];

// I want to append a pointer to the 4th element of AppendOneOfThese in Array
Array_Append (Array, Elements, &AppendOneOfThese [3]); 

```

I need to make it work in the second case, any idea? I still do not get why the error complains as he does.


UPDATE2:
Found a solution switching from:
```

template <typename ArrayType, typename SizeType>

inline ArrayType* Array_Append (ArrayType* Target, SizeType& Array_Size, **ArrayType& Appendee**)

```

to

```

template <typename ArrayType, typename SizeType>

inline ArrayType* Array_Append (ArrayType* Target, SizeType& Array_Size, **ArrayType Appendee**)

```

But it is still not clear to me the behavior of the compiler, and I would very much appreciate an explaination, if someone knows the reason of it.

---

### Post by GeneralZod on 2013-06-15
"&AppendOneOfThese [3]" is a temporary, and temporaries cannot be bound to non-const references.

This works:

```


#include <iostream>
#include <cstring>
/*!
    This subroutine increases the size of a dynamic array by 1 and writes data at such location, effectively
    implementing an append instruction.
    @params:
    Target:        IN        current array
    Array_Size:    IN        size of the current array
    Appendee:    IN        data to append to the array

    @return:            pointer to the extended array
*/
template <typename ArrayType, typename SizeType>
inline ArrayType* Array_Append (ArrayType* Target, SizeType& Array_Size, const ArrayType& Appendee)
{
    ArrayType* tmp;
    tmp = new ArrayType [Array_Size + 1];
    memcpy (tmp, Target, Array_Size * sizeof (ArrayType));

    delete [] Target;

    tmp [Array_Size] = Appendee;
    Array_Size++;

    return tmp;
}

struct TT
{int a;};

int main()
{
    TT** Array (NULL);

    int Elements (0);

    Array = new TT* [1];
    ++Elements;

    TT* AppendOneOfThese = new TT [10];

    // I want to append a pointer to the 4th element of AppendOneOfThese in Array
    TT* blah = &AppendOneOfThese[3];
    Array_Append (Array, Elements, AppendOneOfThese + 3);
}

```

---

### Post by Dirich on 2013-06-15
Thanks Zod, I tried both solutions. The arithmetic of pointers failed to provided a non-temporary object, but the instantiation of blah worked perfectly!
It is indeed the temporary and referement problem that is detected, although I'd say it's a clumsy output the compiler provides me!

---

### Post by GeneralZod on 2013-06-15
> **Dirich said:**
> Thanks Zod, I tried both solutions. The arithmetic of pointers failed to provided a non-temporary object, but the instantiation of blah worked perfectly!
It is indeed the temporary and referement problem that is detected, although I'd say it's a clumsy output the compiler provides me!

No problem :) clang's output is slightly better, but still doesn't quite get to the nub of  the matter.  Might file a bug report ...

---

### Post by dwhitney67 on 2013-06-15
@ Dirich

I'm glad you solved the problem with your program.

As I was looking through your code, I must say I found it difficult (not impossible) to determine which text was a variable (object) type and which was the variable itself.

I've been developing s/w in C++ for over 15 years (in a professional setting), and it is customary in C++ to define object using an uppercase letter for the first character in a word (name), and for variables to start with lowercase.  For example:
```

Array myArray;

MyObject object;

```

Also, why are you managing an array of data?  Why not just use the STL vector?  Are you precluded from using STL because of some restriction?  If you can't use STL, then perhaps modeling your own vector class should be something you could focus on.

In conclusion, if you are developing s/w for your own gratification, then my advice should not matter much to you.  However, if you plan on having others peer review your work (and posting on this forum seems like you do), then it would be helpful if you would assist them in being able to read your code in an efficient manner.

---

