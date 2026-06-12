---
title: "geany with c++, how can I view warnings and errors separately?"
date: 2008-06-27
forum: Programming Talk
---

### Post by yangcheng on 2008-06-27
I am using geany for c++ development.
It is great, however, by default, all warning and error messages are mixed together, and make it hard to find errors when there are many warnings
Is there a way to display them separately ? 
thanks

---

### Post by LaRoza on 2008-06-27
> **yangcheng said:**
> I am using geany for c++ development.
It is great, however, by default, all warning and error messages are mixed together, and make it hard to find errors when there are many warnings
Is there a way to display them separately ? 
thanks

Besides turning warnings off, or grepping the results? Not that I know of.

(Turning warnings off is a bad idea, idealy, you'd be running it in paranoid mode)

---

### Post by dwhitney67 on 2008-06-27
You should attempt to correct the warnings!!!

Try compiling your C++ code like:
```
$ g++ -Werror -Wall -pedantic MyProg.cpp -o MyProg
```
This is guaranteed to eliminate all of your warnings, thus leaving you with only errors. :rolleyes:

---

### Post by LaRoza on 2008-06-27
> **dwhitney67 said:**
> You should attempt to correct the warnings!!!

Try compiling your C++ code like:
```
$ g++ -Werror -Wall -pedantic MyProg.cpp -o MyProg
```
This is guaranteed to eliminate all of your warnings, thus leaving you with only errors. :rolleyes:

That is the way to do it. I second that.

---

### Post by yangcheng on 2008-06-27
> **dwhitney67 said:**
> You should attempt to correct the warnings!!!

Try compiling your C++ code like:
```
$ g++ -Werror -Wall -pedantic MyProg.cpp -o MyProg
```
This is guaranteed to eliminate all of your warnings, thus leaving you with only errors. :rolleyes:

thank you, 
but sometimes or most times,warning messages can be useful, such as warning of typo == to = 

I think it is not a good idea to turn off all warnings, 

I just want to find errors quickly in mass warnings like 

"warning: comparison between signed and unsigned"
warning: deprecated conversion from string constant to ‘char*’

---

### Post by dwhitney67 on 2008-06-27
The sarcasm at the end of my previous post was perhaps misunderstood (this forum needs to come up with a better emoticon with rolling eyes!)

Anyhow, using the **-Werror** GCC option does _not_ mask the warnings... it reports any warning (including those similar to the example you provided) as an error!

Cheers.

---

