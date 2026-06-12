---
title: "Does STLSoft work on Mac OS X?"
date: 2008-10-31
forum: Programming Talk
---

### Post by Tadpole on 2008-10-31
I know this is an Ubuntu forum but I'm trying to write portable C++ code so I need it to work on my Mac as well. I'm using one of the [STLSoft](http://www.digitalmars.com/~stlsoft/) libraries called PlatformSTL, which allows me to do various functions like creating a directory in a platform-agnostic manner. Unfortunately it returns the following error:

**Operating system not discriminated. Only UNIX, Win32 and Win64 are currently recognised by PlatformSTL**

Obviously OS X is unix, but it doesn't seem to recognize that. If I use the UnixSTL library, it works fine, but I'd like to use PlatformSTL so I don't have to make any code changes between the various platforms.

Thanks in advance.

---

