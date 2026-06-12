---
title: "Blitz++ Problems"
date: 2008-03-05
forum: Programming Talk
---

### Post by lvleph on 2008-03-05
So, I was not able to get blitz++ from the repositories like the Ubuntu repository list claims I should be able to. Anyway, I installed the most current version (0.9-7) from a deb file. I am using the current g++ released in the repositories.

I try to compile my code using ```
g++ -o matrix -lblitz Connect.cpp
```And I get a bunch of errors that all indicate to me that for some reason ```
#include <blitz/array.h>
``` is not working. However, I cannot figure out why. Can someone help me out here?

The first two errors seem to make it clear that the #include is not working.
> Connect.h:16: error: ISO C++ forbids declaration of &#8216;Array&#8217; with no type
Connect.h:16: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
And here is the line associated with that error.
```
Array<int,3> cloud;
```

---

### Post by WW on 2008-03-05
Does the directory /usr/include/blitz exist?  If not, you'll have to find where the headers were put when you installed the package.

---

### Post by lvleph on 2008-03-06
Yes, it exists and the file array.h is in there.

---

### Post by Zugzwang on 2008-03-06
Might be a namespace problem. In which namespace is the Array type?

---

### Post by lvleph on 2008-03-06
Okay, I did some more looking. I am not sure why it is different now after my fresh install of Ubuntu, but it appears I need to use namespace blitz instead of std. I used std in my last code using blitz and it worked fine. Now I just have to deal with my other errors. Hopefully, I will not be back asking more questions. Thanks for you help.

---

