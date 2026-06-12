---
title: "C++: Structs?"
date: 2010-10-22
forum: Programming Talk
---

### Post by fallenshadow on 2010-10-22
Ive been learning about structs, or attempting to learn them but they are not working.

Does this look right? According to my notes Im doing everything correctly.

[PHP]
struct Date
{
	string flightdate;
};

typedef struct Date D;

using namespace std;

//the rest of my program continues below this...
[/PHP]

Here is the error:
```
structs.cc:6: error: ‘string’ does not name a type
```

It says it does not name a type... but its right there!!

---

### Post by Zugzwang on 2010-10-22
Put the "using namespace..." command before your structure definition, because in it, you are already referring to an element in the namespace "std", namely "string". If the structure definition should go to a header file, you might rather simply want to use the fully qualified name for the "string" class, namely "std::string".

---

### Post by dwhitney67 on 2010-10-22
And in C++, there is no need to use the "struct" qualifier when referring to a structure.  Thus, it is moot to define a typedef.

The is correct syntax:
```

#include <string>

struct Date
{
   std::string flightdate;
};

int main()
{
   Date theDate;
   ...
}

```

P.S.  In C++, a struct and a class are identical in every way, except that with a class, all member data and functions are by default, treated as private members.  With a class, one must explicitly define which member data and functions should be protected and public.  The same concepts apply to structs, but by default member data and functions in a struct are public.

---

### Post by MadCow108 on 2010-10-22
a struct in c++ is just a class with public as default access level (compared to private).
So you do not really need the struct keyword in the typedef (or any other place except the declaration).
This also works:
typedef Date D;

---

### Post by fallenshadow on 2010-10-26
I was kinda getting on grand with structs but now ive come across this error:

```
error: cannot convert 'F*' to 'char*' for argument '1' to 'void Addnewflight(char*, std::string*, int&)'|
||=== Build finished: 1 errors, 0 warnings ===|

```

The error is on line 65 which looks correct to me:
```
Addnewflight(array, size, index);
```

What does that error message mean?

---

### Post by spjackson on 2010-10-26
> **fallenshadow said:**
> I was kinda getting on grand with structs but now ive come across this error:

```
error: cannot convert 'F*' to 'char*' for argument '1' to 'void Addnewflight(char*, std::string*, int&)'|
||=== Build finished: 1 errors, 0 warnings ===|

```The error is on line 65 which looks correct to me:
```
Addnewflight(array, size, index);
```What does that error message mean?
The error message tells you that there's a problem with the first argument.

From the error message, I guess that array is an array of F, but Addnewflight requires a char array (or char pointer) as its first argument.

The second argument looks a bit suspect since a std::string pointer is required, and the variable is called "size" which I'd usually expect to be some sort of int. This could be OK though; I can't say without the code.

---

### Post by dwhitney67 on 2010-10-26
It is also odd to see that the function expects an std::string pointer.  Pass the string by reference!

---

### Post by fallenshadow on 2010-10-26
Here is a cut down version of the code if you need to understand it better.

The line which gives the error is only calling the function, so I believe it should not need things like int and string in front of the variables.

---

### Post by dwhitney67 on 2010-10-26
As indicated by spjackson, the call to Addnewflight() is being called with the wrong type of parameters.

This is how you have defined Addnewflight()
```

void Addnewflight(char * code, string codearray[], int & index);

```

These are the data types you are passing the function:
```

Addnewflight(F*, int, int);

```
See anything wrong?  The compiler sure does!

---

### Post by night_fox on 2010-10-26
You are trying to call Addnewflight with arguments that you would pass to Flightcode.

This is easy to fix. Either pass different arguments, or change the function to accept different arguments. This isn't really a programming error, it's just a silly mistake which everyone makes.

Part of the point of C++ is to reduce errors caused by using pointers and getting it wrong. C forces you to use pointers for certain things, whereas in C++, you avoid them by using references. Even if you are confident and a pro at using pointers (and they are worth learning), you should use references when you can, and pointers when you have to.
For instance, std::string uses pointers internally because it has to store an array of characters, but you never see the underlying pointers. Try and use std::string instead of char* whenever you can.
If you make an array of something, you are using pointers. You can use std::vector or std::deque or something instead, depending on what needs to be fast. This is much better because the size of the array is easy to change, by using push_back(). It is much better if you want to make a vector of type std::vector<bool> because the bool only takes up 1 bit in memory.

---

### Post by spjackson on 2010-10-26
> **fallenshadow said:**
> Here is a cut down version of the code if you need to understand it better.

The line which gives the error is only calling the function, so I believe it should not need things like int and string in front of the variables.
No, at the point of call (line 61) you do not need to and indeed must not put a type in front of your variable; nobody said you should.

On line 28 you have:

```

void Addnewflight(char * code, string codearray[], int & index);

```and on line 105
```

   void Addnewflight(char * code, string codearray[], int & index)

```That's OK.

On lines 36-38 and 61 you have:
```

    int index = 0;
    int size = 0;
    F*array = new F[size];

    Addnewflight(array, size, index);

```Now that in itself would be OK. But can you spot the discrepancies between the types here and the ones you say that Addnewflight needs on lines 28 and 105? Look closely at 1st and 2nd parameters.

---

### Post by fallenshadow on 2010-10-31
Thanks! Im sorted now! Sigh... I post up such stupid errors and its annoying the way I can't see them myself. :oops:

---

