---
title: "What was rational to deprecating the .h extension in C++ header files"
date: 2010-01-23
forum: Programming Talk
---

### Post by Jonas thomas on 2010-01-23
I have a silly question.
I understand that they had to differentiate old header files from new header file with standard updates.
[http://www.codeguru.com/forum/showthread.php?t=344569]("http://www.codeguru.com/forum/showthread.php?t=344569")

What was the standards people thinking when they decided to drop the .h?  
Less typing?
I would think that if you where looking to manage header files a better standard would have been to change every thing to .hh or .hxx instead.  I suppose it's less typing,but if wanted i want to search for .h header files it's very easy..

It's something I've always been very curious about.  Anyone have a link?
Thanks,

---

### Post by nvteighen on 2010-01-23
First, only the *standard headers* dropped the extension. Any non-standard header should keep the extension. Second, I guess it's just a way to tell apart standard headers from those that aren't. Also, without dropping the extension, you'd have a weird conflict with the C string.h header... (ok, you refer to it as "cstring", but the how to distinguish the file?)

---

### Post by gnometorule on 2010-01-23
nvteighen is spot on with his string.h example. Bjarne Stroustrup, the inventor of C++, in his book 'The C++ Programming Language', devotes some time to discuss this change and mentions the standard committee (for C++) running into 'compatibility issues' because of such overlaps, and hence dropping them. It's apparently no philosophical change really; just pragmatic.

---

### Post by nmccrina on 2010-01-23
> **Jonas thomas said:**
> ...but if wanted i want to search for .h header files it's very easy..


All the standard C++ header files (the ones that you don't use the h with) are in /usr/include/C++. Convenient, one stop shopping. ;) Don't know if that's what you were referring to, but I thought I would whip it out there anyway. :D

---

### Post by Jonas thomas on 2010-01-24
Thank you everyone for the response... This is all starting to make sense..

---

