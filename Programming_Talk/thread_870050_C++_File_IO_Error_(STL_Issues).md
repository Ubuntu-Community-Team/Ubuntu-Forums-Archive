---
title: "C++ File IO Error (STL Issues?)"
date: 2008-07-25
forum: Programming Talk
---

### Post by era86 on 2008-07-25
```
In file included from /usr/lib/gcc/.../3.4.6/../../../../include/c++/3.4.6/fstream:840,
                 from x.cpp:41:
/usr/lib/gcc/.../3.4.6/../../../../include/c++/3.4.6/bits/fstream.tcc: In member function `virtual typename std::basic_filebuf<_CharT, _Traits>::int_type std::basic_filebuf<_CharT, _Traits>::underflow()':
**/usr/lib/gcc/.../3.4.6/../../../../include/c++/3.4.6/bits/fstream.tcc:277: error: expected unqualified-id before '(' token**
/usr/lib/gcc/.../3.4.6/../../../../include/c++/3.4.6/bits/fstream.tcc: In member function `virtual std::streamsize std::basic_filebuf<_CharT, _Traits>::xsputn(const _CharT*, std::streamsize)':
[B]/usr/lib/gcc/.../3.4.6/../../../../include/c++/3.4.6/bits/fstream.tcc:600: error: expected unqualified-id before '(' token
[/B]
```

I'm having a little trouble figuring out this code.  I have checked my actual code again and again, it seems to be fine.  Is this a STL bug?  Please help.  Thanks in advanced.

---

### Post by dribeas on 2008-07-25
> **era86 said:**
> Is this a STL bug?  Please help.  Thanks in advanced.

Without seeing the code that produced the error is hard to tell. My first assumption is that most bugs in g++ 3.4 would have already been detected, try to search google.

---

### Post by WW on 2008-07-25
I assume x.cpp is your code.  Could you show the contents of x.cpp up to and including line 41 (which is apparently the #include statement that leads to the errors)?

---

### Post by era86 on 2008-07-25
I'm sorry to cause such inconvenience, but for certain purposes I cannot expose the code.... I know... against the hacker ethic. :(

If that makes it impossible to solve the problem, then I'll just find a workaround.

I do, however, #include <fstream> on line 41.

After a little bit of googling, I found that it might be a bug in the STL, but I'm not sure since googling only led me to other forums, nothing official.

---

### Post by escapee on 2008-07-25
Why are you assuming its an STL error?  fstream is part of IOStream, not the STL.  Your code is much more likely to have the bug than fstream.  If you can't show us your code, modify parts of the code so we won't know what it is or show us an example of what you're doing with the fstream.

---

### Post by dribeas on 2008-07-25
> **escapee said:**
> Why are you assuming its an STL error?  fstream is part of IOStream, not the STL.  Your code is much more likely to have the bug than fstream.  If you can't show us your code, modify parts of the code so we won't know what it is or show us an example of what you're doing with the fstream.

Agree. Also, not just for this case but for most other hard to solve problems, try reducing the problem to the smallest simplest case. Try reordering includes so that fstream is up top, and try to locate whether one of the other includes contains macros (#define's) for words that occur around where the errors in bits/fstream are reported.

---

### Post by era86 on 2008-07-25
> **escapee said:**
> Why are you assuming its an STL error?  fstream is part of IOStream, not the STL.  Your code is much more likely to have the bug than fstream.  If you can't show us your code, modify parts of the code so we won't know what it is or show us an example of what you're doing with the fstream.

Will do.  I'll get it on here ASAP.  Thanks.

---

