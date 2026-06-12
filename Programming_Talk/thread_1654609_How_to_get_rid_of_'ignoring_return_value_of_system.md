---
title: "How to get rid of 'ignoring return value of system()'"
date: 2010-12-28
forum: Programming Talk
---

### Post by hakermania on 2010-12-28
I am using gcc as compiler with QtCreator IDE, I don't understand what's the problem, but for every system() (#include <stdlib.h>) function I use it outputs warnings:
```
warning: ignoring return value of ‘int system(const char*)’, declared with attribute warn_unused_result
```
I have uploaded my package to REVU and I was told to get rid of these warnings.


Any help is welcome:)!

---

### Post by MadCow108 on 2010-12-28
well the obvious method (besides not using system) is handling the return value:
int ret = system("some unsafe stuff");
if (ret == NOT_GOOD)
  return OH_NO;

you can also disable the warning:
gcc -Wno-unused-result ...

or you can silence it:
if (system("..."));

---

### Post by hakermania on 2010-12-29
Ok, this worked like a charm.
For any following this thread and has problem with fgets (which return char*) can do a check:
```
if(fgets(arguments)==NULL)
  cout << "ERROR";
```
:)

---

### Post by Vox754 on 2010-12-29
> **hakermania said:**
> Ok, this worked like a charm.
For any following this thread and has problem with fgets (which return char*) can do a check:
```
if(fgets(arguments)==NULL)
  cout << "ERROR";
```
:)

Oh my God.

You are mixing C and C++, using "system()", and then you are uploading the monstrosity to REVU.

Why is the world so cruel?

---

### Post by dwhitney67 on 2010-12-29
> **Vox754 said:**
> Oh my God.

You are mixing C and C++, using "system()", and then you are uploading the monstrosity to REVU.

Why is the world so cruel?

Indeed; Hackermania could get a bashing peer review here.

---

### Post by hakermania on 2010-12-29
Haha thx for your good words :D
But it works :D So?

---

