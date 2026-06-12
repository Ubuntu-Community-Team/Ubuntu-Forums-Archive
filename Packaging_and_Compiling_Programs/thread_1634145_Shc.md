---
title: "Shc"
date: 2010-11-30
forum: Packaging and Compiling Programs
---

### Post by jdb91 on 2010-11-30
Quick question; trying to compile some shell script with shc, usually an easy job, except I've hit the limit of lines it wants to accept.  Is there an easy way to get round this or am I going to have to start picking lines out?


```
shc: WARNING!!
   Scripts of length near to (or higher than) the current System limit on
   "maximum size of arguments to EXEC", could comprise its binary execution
```


Cheers,

---

### Post by TSJason on 2010-11-30
The size of your bash file must be impressive. I used shc pervasively for several years with a large contingent of scripts that continually changed and never hit the limit. 

You might want to consider cutting your variables into their own text-based file (to be sourced from the script) and moving large subroutines into separately compiled scripts. Just a thought.

---

### Post by jdb91 on 2010-12-01
That's the thing, it's 4000 lines long and only about 200k.

I'll be doing that soon anyway as it's going to be rewritten in python.

---

