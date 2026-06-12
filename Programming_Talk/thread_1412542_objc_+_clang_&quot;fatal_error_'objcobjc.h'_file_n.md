---
title: "objc + clang: &quot;fatal error: 'objc/objc.h' file not found&quot;"
date: 2010-02-21
forum: Programming Talk
---

### Post by JordyD on 2010-02-21
This is not a problem, but a solution for those of you that have had the same problem as I have had. :) (This is all on Ubuntu Karmic)

The problem:
Whenever you attempt to compile an Objective-C file with clang that imports <objc/objc.h>, you get the error message in this post's title.

The fix:
For some strange reason, the objc include folder is located in a *really* strange place. So type ```
locate objc.h
```. If this comes up with nothing, either try ```
sudo updatedb && locate objc.h
``` or install gobjc, then ```
sudo updatedb && locate objc.h
```.

Mine looks like this:
```
jordy@data:~$ locate objc.h
/usr/lib/gcc/i486-linux-gnu/4.4/include/objc/objc.h

```

We want to link the include directory into /usr/local/include

So use this command: ```
sudo ln -s <your-objc-directory> /usr/local/include/objc
```

So, for example, mine looked like this:
```
jordy@data:~$ sudo ln -s /usr/lib/gcc/i486-linux-gnu/4.4/include/objc/ /usr/local/include/objc

```

Now after having done that, your compiles should go much smoother.

---

