---
title: "GCC support of xautopar option"
date: 2012-01-18
forum: Programming Talk
---

### Post by erotavlas on 2012-01-18
Hi,

can you tell me about the support of the -xautopar option by GCC? I know that Sun Studio compiler supports it. 

Thank you

---

### Post by Zugzwang on 2012-01-18
So here is what a quick google search found for me. Does it answer your question? [http://gcc.gnu.org/wiki/AutoParInGCC]("http://gcc.gnu.org/wiki/AutoParInGCC")

---

### Post by erotavlas on 2012-01-19
Hi,

thank you very much, it is what I was searching. For me this opens a new world. :)

---

### Post by erotavlas on 2012-01-24
Hi,

I have read all informations available on the wiki of GCC. If I'm not wrong the informations are not updated and I couldn't find the current status of autopar-graphite option of GCC.
Here [http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html) there is a complete list of all available options for optimizing the code. I'm new of this subject but I have understood that the base options are ```
-ftree-parallelize-loops=thread -floop-parallelize-all
```. Can you tell me about the useful of the following options?
```

-ftree-loop-distribution 
-fgraphite-identity 
-floop-block 
-funroll-loops 
-floop-flatten

```
I know that the major part of the options depends on the code, but I would like to know if there is a general rule.

Thank you

---

