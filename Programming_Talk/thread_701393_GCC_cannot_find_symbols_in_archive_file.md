---
title: "GCC cannot find symbols in archive file"
date: 2008-02-19
forum: Programming Talk
---

### Post by akwatve on 2008-02-19
Hi

I am re-posting it here as this seems the right place, Please see [http://ubuntuforums.org/showthread.php?p=4335729](http://ubuntuforums.org/showthread.php?p=4335729) for original post.

I am using g++ to compile some cpp files.
When I used
```

g++ a.o b.o c.o  foo.cpp
```

Everything works fine. code gets compiled.
But If I create an archive file using :

```
ar -rc common.a  a.o b.o c.o
```

and then use

```
g++ common.a foo.cpp
```

g++ throws a linking error which basically says that it was unable to find any libraries...

```
foo.cpp:(.text+0x47a): undefined reference to `Class::hello()'
```

Can someone tell me what is going wrong. I also tried creating archive using ark instead of command line but no success. Is there anything else we need to do while building library archive. BTW I did rename archive to libcommon.a and tried -lcommon but that too gives the same problem. Although this is not a show stopper, I am unable to understand why does g++ rejects archive .....

As per lloyd_b's suggestion, I even tried creating indices using ```
ranlib common.a
``` or by using ```
ar -rcs 
```but it didn't resolve the issue.

Thanks in advance
__________________

---

### Post by WW on 2008-02-20
Try ```
g++ foo.cpp common.a
```
The  order of the files matters when linking.

---

### Post by akwatve on 2008-02-20
Thanks a ton WW. That was the problem. I will make sure to use the right order next time.
Thanks again..........

---

