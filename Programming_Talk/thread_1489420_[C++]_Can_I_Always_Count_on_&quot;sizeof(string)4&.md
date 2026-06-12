---
title: "[C++] Can I Always Count on &quot;sizeof(string)/4&quot;"
date: 2010-05-21
forum: Programming Talk
---

### Post by dodle on 2010-05-21
Is the size of a C++/C "string" 4 bytes no matter how long the string is?  The reason I ask is because I need to know if I can count on this to find how many strings are in a string array:
[php]
string mystrings[] = {"A", "Friday", "Supercalafradgalisticexpialadocious"}
cout << "There are " << sizeof(mystrings)/4 << " items in mystrings!" << endl;[/php]

**Edit:** I think I found the answer by doing:
[php]string myname = "dodle";
cout << sizeof(myname.max_size()) << endl; // returns 4[/php]

I find it interesting that the byte size of:
[php]char foo[] = {'d', 'o', 'd', 'l', 'e'};[/php]
is more than:
[php]string foo[] = {"My name is dodle"};[/php]

---

### Post by Compyx on 2010-05-21
No. The size of a C 'string' can differ between implementations. For example, on my 64-bit system, sizeof(char *) == 8.

You can however use the following to determine the number of elements in the array:
```

sizeof mystrings / sizeof mystrings[0]

```
By using a second 'sizeof' on a single element in the array (mystrings[0]) you are guaranteed to get the correct number of elements in the array.

---

### Post by dodle on 2010-05-21
Thank you, that is very good advice.

---

### Post by dwhitney67 on 2010-05-21
Dodle, stop dwelling too much on the usage of arrays.  Try to use more advanced containers; in C++, a great substitute for an array is the STL vector.

```

#include <vector>
#include <string>

std::vector<std::string> myStrArray;

myStrArray.push_back("ABC");
myStrArray.push_back("DEF");
myStrArray.push_back("GHI");

```
Using the size() accessor offered by the STL vector, you could easily deduce that there are 3 strings in the vector shown above.  There is no need for you to perform any arithmetic.

Oh, and also, the STL string also offers a size() (and length()) method that can be used to determine the length of the string.

```

// this is inefficient code to demonstrate what was stated above

for (size_t i = 0; i < myStrArray.size(); ++i)
{
   std::cout << "My string has a size of: " << myStrArray[i].length() << std::endl;
}

```

---

### Post by nvteighen on 2010-05-21
> **Compyx said:**
> No. The size of a C 'string' can differ between implementations. For example, on my 64-bit system, sizeof(char *) == 8.

You can however use the following to determine the number of elements in the array:
```

sizeof mystrings / sizeof mystrings[0]

```
By using a second 'sizeof' on a single element in the array (mystrings[0]) you are guaranteed to get the correct number of elements in the array.

This is not always true. Look at this:
```

#include <iostream>

int main(void)
{
    char *a = new char[30]; // silly on purpose!
    a[0] = 'a';
    
    std::cout << sizeof(a)/sizeof(a[0]) << std::endl;

    delete[] a;
    return 0;
}

```

This is because a dynamically allocated array, even if one does the stupid thing to use a constat number in the **new** statement, the compiler doesn't know the string's length at compile-time but the pointer's and therefore, **sizeof** (which is a compile-time operator), will spit out the pointer's size.

Not like this, which works:
```

#include <iostream>

int main(void)
{
    char a[] = "hello";
    
    std::cout << sizeof(a)/sizeof(a[0]) << std::endl;

    return 0;
}

```

Of course, dividing by **sizeof(char)** is to divide by 1 (char is set to 1 byte, IIRC, by the standard). But it turns relevant for other data types.

---

### Post by trent.josephsen on 2010-05-21
> **nvteighen said:**
> 
This is because a dynamically allocated array, even if one does the stupid thing to use a constat number in the **new** statement, the compiler doesn't know the string's length at compile-time but the pointer's and therefore, **sizeof** (which is a compile-time operator), will spit out the pointer's size.

That is because a is not an array.  The fact that sizeof(a) doesn't return the length of a has nothing to do with the new operator and everything to do with the explicitly declared type of a.

But as dwhitney67 says, since you're using C++, don't use C techniques.  You know what they say about premature optimization.

---

### Post by nvteighen on 2010-05-21
> **trent.josephsen said:**
> That is because a is not an array.  The fact that sizeof(a) doesn't return the length of a has nothing to do with the new operator and everything to do with the explicitly declared type of a.


I know... and the issue is exactly the fact that one has to pay attention to that distinction if one's about to use C strings. I wanted to point out that dynamically allocated C "strings" will fail that test though we call those strings the same as the "strings" formed from arrays.

Also, sizeof() seems to confuse people a lot (it confused me time ago) as it is a compile-time operator; sometimes some tutorials don't place emphasis on that fundamental fact and unintentionally show it like it were some kind of runtime function or the like.

I don't like C++, but std::string is a major contribution (together with std::vector) that solves 90% of the issues related to C strings.

---

### Post by soltanis on 2010-05-21
All he is really asking is if he can always count on the size of a pointer being 4 bytes long, to which the answer is NO, the 64 bit system being the obvious example of that.

But if you are trying to determine the length of a string you should not at all be doing what you are doing. If you are trying to determine the length of a character array then you must use the strlen function which will search for the null terminator on the end of the string. If you are trying to determine the length of a statically allocated array, you can use sizeof but you should really be able to have deduced that yourself. If you are trying to determine the length of a dynamically allocated array, you cannot use sizeof but more importantly you should really know what its length is, because you're the one who asked for it to be allocated.

---

