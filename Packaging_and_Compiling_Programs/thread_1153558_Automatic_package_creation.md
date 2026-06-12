---
title: "Automatic package creation"
date: 2009-05-08
forum: Packaging and Compiling Programs
---

### Post by Gannin on 2009-05-08
It used to be when I compiled something from source, I would install it using checkinstall, which would automatically make a simply .deb of the program then install that .deb.  However, with the complexity of installs being what they are these days, checkinstall very often no longer works.

I'm pretty sure there are some similar programs out there but I can't remember the names of any, even after doing a search.  I seem to remember reading about some of them in Linux Journal a while ago.  What are some good modern programs for automatically creating a .deb from something you've compiled?  Thanks.

---

### Post by andrew.46 on 2009-05-09
Hi Gannin,

> **Gannin said:**
> It used to be when I compiled something from source, I would install it using checkinstall, which would automatically make a simply .deb of the program then install that .deb.  However, with the complexity of installs being what they are these days, checkinstall very often no longer works.

There is a known bug with checkinstall that is usually seen as:

```
.......  No such file or directory 
```

followed by a failed package. Is this the error that you have come across? Apart from this, which can be bypassed by adding --fstrans=no to the checkinstall line, I was not aware of any major problems with checkinstall. But I have been wrong before :-).

Andrew

---

### Post by Gannin on 2009-05-09
That actually seemed to work.  Thank you :).

---

