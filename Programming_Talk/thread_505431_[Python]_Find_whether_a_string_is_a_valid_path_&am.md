---
title: "[Python] Find whether a string is a valid path &amp; handling numbered exceptions"
date: 2007-07-20
forum: Programming Talk
---

### Post by ankursethi on 2007-07-20
The questions are clear. I want to know whether a given string is a valid path to a directory or not (could be done with isdir() I suppose).

What's troubling me is handling exceptions which are numbered. For example, the exception OSError has many different numbers (OSError 17, OSError 7 etc.). I can handle OSError, but how do I handle OSError 17 specifically?

---

### Post by pmasiar on 2007-07-20
> **ankursethi said:**
> I want to know whether a given string is a valid path to a directory or not (could be done with isdir() I suppose).

Reading module os.path

exists() : Return True if path refers to an existing path. 

> What's troubling me is handling exceptions which are numbered. For example, the exception OSError has many different numbers (OSError 17, OSError 7 etc.). I can handle OSError, but how do I handle OSError 17 specifically?

Reading docs for module os:

"The accompanying value is a pair containing the numeric error code from errno and the corresponding string... See the module errno, which contains names for the error codes defined by the underlying operating system. "

---

### Post by steve.horsley on 2007-07-21
You probably have to catch all OSError exceptions, check the number, and re-raise the errors you didn't want to catch.

---

### Post by ankursethi on 2007-07-22
I got that. But how do I know the number of the exception I just caught?

I'm sorry, I'm not too good at this.

EDIT : I got how to get the error number, but how do I raise the exception with the specified error number?
```
raise OSError, ErrorNumber
```
Is that right?

---

