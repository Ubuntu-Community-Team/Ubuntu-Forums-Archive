---
title: "Concatenating strings and pointers to strings"
date: 2009-06-16
forum: Programming Talk
---

### Post by Nuticulus on 2009-06-16
Hi,

I'm trying to concatenate several strings together, like so:

```
arg = "Games/" + (*gamename) + "/resource.dat"
```

arg is a char* , and gamename is a const char*.

When I compile with gcc I get the error "**error: invalid operands of types ‘const char*’ and ‘const char [14]’ to binary ‘operator+’**"

Anyone have any suggestions?

---

### Post by ad_267 on 2009-06-16
Is this C or C++? I'm not an expert by any means but I don't think you can concatenate strings like that in C, have a look at strcat.

---

### Post by Nuticulus on 2009-06-16
This is C++

---

### Post by ad_267 on 2009-06-16
You can only concatenate string objects like that. If you're using char arrays I think you'll have to use strcat or sprintf.

---

### Post by lisati on 2009-06-16
I don't have any experience in C++ but concur that **strcat** comes to mind for C

---

### Post by Arppa on 2009-06-16
You could do this in C-style with strcat/strcpy but since you are coding in C++ I strongly recommend to use strings. If you are new to pointers, strings will save you from a whole world of pain and suffering:
```

#include <string>

string arg;
string gamename = "gamename";
arg = "Games/" + gamename + "/resource.dat";
cout << arg << endl;      // Prints "Games/gamename/resource.dat"

```

---

### Post by stair314 on 2009-06-16
Here's how you'd concatenate it using strings:

string argStr = string("Games/")+(*gamename)+"/resource.dat";

If you need the result to be a char *, you can get a char * out like this:
arg = argStr.c_str();

This makes a "shallow copy" that is only good as long as argStr is in scope and does not change. To make a "deep copy" on the heap you can do:
arg = strdup(argStr.c_str())

If you use strdup, when you are done with arg you need to free it:
free(arg);


Or if you can't change where arg points, do
strcpy(arg, argStr.c_str());

(just be sure that arg points to a long enough buffer; if you want this code to be secure use strncpy instead)

---

### Post by Can+~ on 2009-06-16
C++'s string constructor can accept a c-string as an argument.

```
string arg = "Games/" + string(gamename) + "/resource.dat";
```

-C++ string is a class which handles a char* "under the hood" and overloads the "+" operator to allow concatenation (OO Paradigm).
-char* is a pointer to a space of memory (Imperative Paradigm).

Now you see why my signature holds that quote.

---

### Post by Nuticulus on 2009-06-18
Got it working! I ended up using Can+~'s "string arg = "Games/" + string(gamename) + "/resource.dat";".Thanks everyone!

---

