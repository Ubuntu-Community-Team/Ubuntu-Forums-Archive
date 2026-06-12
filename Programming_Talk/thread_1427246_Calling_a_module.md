---
title: "Calling a module"
date: 2010-03-11
forum: Programming Talk
---

### Post by newport_j on 2010-03-11
I know this may be an elementary question, but here goes. When a module is defined it is preceded by the word void, why? When this module is called in the context of a program it is not preceded by the word void. Again, why is this.
 
I said it was elementary.

Newport_j

---

### Post by CptPicard on 2010-03-11
Not sure what you mean... do you mean function declarations? "void" is just a placeholder for "no value".

---

### Post by dwhitney67 on 2010-03-11
> **newport_j said:**
> I know this may be an elementary question, but here goes. When a module is defined it is preceded by the word void, why? When this module is called in the context of a program it is not preceded by the word void. Again, why is this.
 
I said it was elementary.

Newport_j

CptPicard is correct.

There are occasions where you might come across code where a function returns a non-void value (eg. int), yet the caller wishes to indicate that they are going to ignore the value.  Thus you might see code like:
```

int function()
{
   ...
}

void otherFunction()
{
   (void) function();
}

```
The bottom line is that the function declaration (prototype) is used to indicate what type of value, if any, that the function will return.

You do not need to specify the return type when calling the function... at least not in our universe.

---

