---
title: "Need to compile some legacy C++ code"
date: 2012-02-11
forum: Programming Talk
---

### Post by DBQ on 2012-02-11
Hi Everybody.

I have some code designed for g++4.1 to 4.3.

I am Ubuntu 10.10 with g++ version 4.6.1-9.

I tried compiling the code using the current version of g++, but it gives errors.

Is there any way to compile this code on my system using the current version of g++? 

If not, is there a way to install 4.1-4.3 without messing everything up and condemning oneself to the dependency hell?

---

### Post by trent.josephsen on 2012-02-12
Sounds like you're diagnosing the problem a bit prematurely -- "it gives errors" could mean anything from mismatched libraries to corrupted source to it just plain doesn't work.  4.1 is hardly what I'd call "legacy" and I'd be surprised to find game breaking changes since then.

Can you post the errors you got, at least?

---

### Post by DBQ on 2012-02-12
Thanks for your reply!

Most errors are similar to this one

```

1077:11: error: &#8216;ptrdiff_t&#8217; does not name a type

```

---

### Post by Arndt on 2012-02-12
> **DBQ said:**
> Thanks for your reply!

Most errors are similar to this one

```

1077:11: error: ‘ptrdiff_t’ does not name a type

```

If you add

```
#include <cstddef>
```

does the problem go away then?

---

### Post by DBQ on 2012-02-13
Thank you for the reply.  In my case modifying the code is not an option -- that part of the code needs to stay the same.

---

### Post by Zugzwang on 2012-02-13
> **DBQ said:**
> Thank you for the reply.  In my case modifying the code is not an option -- that part of the code needs to stay the same.

They you have a problem: the files that need to be included change from version to version - recently, the GCC folks have made a lot of cleaning up with respect to the header files, so you won't get around modifying the source code.

I don't know why modifying the source is a problem for you, but you could write some script that copies all source files into a different folder, adds the #include lines in all of them, and compiles from there. Technically, this is just a build script and you are not modifying the original source.

---

### Post by Arndt on 2012-02-13
> **DBQ said:**
> Thank you for the reply.  In my case modifying the code is not an option -- that part of the code needs to stay the same.

If ptrdiff_t is the only problem, you could define it on the compile line, like

```
g++ -Dptrdiff_t='unsigned long' ...
```

What happens if you try?

---

### Post by conradin on 2012-02-13
Another idea, which matches your desire to run dated g++ is to download the source for g++ 4.1 then compile that, and run g++ in some non system specified folder.

---

### Post by ggeorgak on 2012-02-13
You can install multiple toolchain versions, if you don't mind the installation overhead. There is a guide at gcc faq:
[http://gcc.gnu.org/faq.html#multiple]("http://gcc.gnu.org/faq.html#multiple")
Apart from the above, I recall that Ubuntu had multiple gcc versions available to install through apt and I believe with few symlinks correctly set up, everything works fine.

---

