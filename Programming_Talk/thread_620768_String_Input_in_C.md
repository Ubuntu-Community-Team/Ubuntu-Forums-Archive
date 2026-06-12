---
title: "String Input in C"
date: 2007-11-23
forum: Programming Talk
---

### Post by ankursethi on 2007-11-23
I was wondering how to cleanly read an arbitrary sized string from stdin in C without risks of overflow. I don't know what the size of the entered text will be.

Remember that this needs to work on Windows, too.

Anybody?

---

### Post by LaRoza on 2007-11-23
fgets.

You can specify the buffer to prevent overflow.

An alternative solution is do code a linked list and a function to get user input character by character without requiring the user to press enter and add it to the list.

Depending on what you want, just making a buffer large enough to hold whatever input you expect and using fgets would be the easier solution.

---

### Post by Compyx on 2007-11-23
Smells like homework to me. But I'll give you a tip:
```

man 3 realloc

```

---

### Post by samjh on 2007-11-23
> **ankursethi said:**
> I was wondering how to **cleanly read an arbitrary sized string from stdin in C without risks of overflow**. I don't know what the size of the entered text will be.

What do you mean by "cleanly"?

How thoroughly do you want to mitigate the risk of overflow?

As LaRoza suggested, try fgets, as it is the standard function for doing what you're asking.
[http://www.cppreference.com/stdio/fgets.html](http://www.cppreference.com/stdio/fgets.html)

---

### Post by Kadrus on 2007-11-23
Maybe this isn't what you are looking for..but I will post it anyway.
It's related to Welcome to Ubuntu:
```
#include<stdio.h>
int main()
{
char string[100];
printf("Hello,What's your name?");
fgets(string,100,stdin);
printf("Welcome to Ubuntu, %s", string);
getchar();
}

```

The string can only reach to 100

The program types : Hello What's your name?
You type your name
It gives you "Welcome to Ubuntu" + your name

I hope that is what you were looking for :)

---

### Post by LaRoza on 2007-11-23
The only problem with this is that who have a buffer which is possibly too small, or too large but still uses the memory.

---

### Post by samjh on 2007-11-23
> **LaRoza said:**
> The only problem with this is that who have a buffer which is possibly too small, or too large but still uses the memory.

The thing is, the OP asks about reading arbitrary length of string without risk of overflow.  It just doesn't make sense.  You've either got a fixed or bounded length of string which must be guarded against overflow, or an arbitrary length of string which never overflows (ignoring physical memory, the string could be of infinite length, but it can never overflow because its limit of length is never defined).

;)

---

### Post by public_void on 2007-11-23
Despite the string size being undetermined, there has to be an upper bound where the program will reject the string. Yes in theory the string could be infinite, but surely the user wouldn't input a stupidly long string. Yes it could happen, however IMO the program should reject input or read up to this upper bound. However this does depend on what this upper bound is, thats dependent on what the input is.

---

### Post by ankursethi on 2007-11-23
Thanks guys for the responses. I've already gone the realloc() way and grabbed the string. I was just wondering if there was a better way to do it in the standard library.

The linked list way seems very nice. I'll try that instead. I've had tough time making the implementation with realloc() work, and it's much like a hack. Linked lists might work better.

---

### Post by Sporkman on 2007-11-24
[http://ubuntuforums.org/showthread.php?p=3630020#post3630020](http://ubuntuforums.org/showthread.php?p=3630020#post3630020)

---

### Post by LaRoza on 2007-11-24
> **Sporkman said:**
> [http://ubuntuforums.org/showthread.php?p=3630020#post3630020](http://ubuntuforums.org/showthread.php?p=3630020#post3630020)

That is a different language, in a different context. 

That is for getting string input from a text file in C++, not getting a strings from the user in C.

---

### Post by Sporkman on 2007-11-24
> **LaRoza said:**
> That is a different language, in a different context. 

That is for getting string input from a text file in C++, not getting a strings from the user in C.

No, it's from a file - note the fgetc, feof, FILE, etc.

---

### Post by LaRoza on 2007-11-24
> **Sporkman said:**
> No, it's from a file - note the fgetc, feof, FILE, etc.

I know its from a file, that is what I said. This isn't about that. Also, the code segments use "new", a C++ concept. This is C.

---

