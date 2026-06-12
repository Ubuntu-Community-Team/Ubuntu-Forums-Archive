---
title: "Preeprocessor Errror"
date: 2011-01-03
forum: Programming Talk
---

### Post by newport_j on 2011-01-03
```

[FONT=Courier New][SIZE=3]ifdef _cplusplus[/SIZE][/FONT]
[SIZE=3][FONT=Courier New]#include <complex>[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]typedef complex<double. dcomplex;[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#else[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#include <complex.h>[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]typedef double complex dcomplex;[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#endif[/FONT][/SIZE]
 

```
 
 
[SIZE=3][FONT=Courier New]In file included from WEGtest.c:17:[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]sel_lang.h:6: error: expected initializer before ‘dcomplex’[/FONT][/SIZE]
 
 
The code at the top resulted in an error message that follows the code. I am unsure as to what it means. I took this code literally from a previous post.
 
I did get a deprecated header warning (not shown) so is that the problem? This is by no means all of the output, but the warning and the error shown are the first two phenomenon when I compile.
 
It seems that there is nothing wrong with the code.
 
I am unsure what to do next.
 
Why do I have this error?
 
Any help appreciated, Thanx in advance.
 
Newport_j

---

### Post by GeneralZod on 2011-01-03
> **newport_j said:**
> ```

[SIZE=3][FONT=Courier New]typedef complex<double**.** dcomplex;[/FONT][/SIZE]

```
 


There's at least one error, there ("." instead of ">").

---

### Post by MadCow108 on 2011-01-03
please read the new answers in your other thread
your on the completely wrong track and wasting your (and our) time

---

### Post by newport_j on 2011-01-04
I think that I see the problem. The precompiler directive _cplusplus should have a double underscore __cplusplus.
 
That is at least one error.
 
 
Newport_j

---

### Post by newport_j on 2011-01-04
I think I have most of the errors out, but one remains. The preprocessor directive is:
 
```

[FONT=Courier New][SIZE=3]#ifdef __cplusplus[/SIZE][/FONT]
[SIZE=3][FONT=Courier New]#include <complex>[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]typedef complex<double> dcomplex;[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#else[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#include <complex.h>[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]typedef double complex dcomplex;[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#endif[/FONT][/SIZE]

```
 
This results n the following error on compiling.
 
[FONT=Courier New][SIZE=3]In file included from WEGtest.c:17:[/SIZE][/FONT]
[SIZE=3][FONT=Courier New]sel_lang.h:3: error: expected initializer before ‘<’ token[/FONT][/SIZE]
 
 
 
It clearly does not like the third line of this directive. 
 
[SIZE=3][FONT=Courier New]typedef complex<double> dcomplex;[/FONT][/SIZE]
 
I believe that is not recognizing the term complex. I have found the complex file for c++ complex numbers so I knw it exists. But why am I getting the error? I choose to write this program in c++ so I must use something like the above to introduce and use complex numbers. This is one way in c++.
 
 
In Stanley Lippman's, C++ Primer, 2 ed on page 65 this is exactly how he does it syntactically; he of course usess a different example. I have also seen other code that does it this way. I am just not sure why i am gettng the error.
 
This should work. Any help appreciated, Thanx in advance.
 
 
Newport_j

---

### Post by worksofcraft on 2011-01-04
> **newport_j said:**
> I think I have most of the errors out, but one remains. The preprocessor directive is:
 
```

[FONT=Courier New][SIZE=3]#ifdef __cplusplus[/SIZE][/FONT]
[SIZE=3][FONT=Courier New]#include <complex>[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]typedef complex<double> dcomplex;[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#else[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#include <complex.h>[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]typedef double complex dcomplex;[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#endif[/FONT][/SIZE]

```
 
This results n the following error on compiling.
 
[FONT=Courier New][SIZE=3]In file included from WEGtest.c:17:[/SIZE][/FONT]
[SIZE=3][FONT=Courier New]sel_lang.h:3: error: expected initializer before ‘<’ token[/FONT][/SIZE]
 
 
 
It clearly does not like the third line of this directive. 
 
[SIZE=3][FONT=Courier New]typedef complex<double> dcomplex;[/FONT][/SIZE]
 
I believe that is not recognizing the term complex. I have found the complex file for c++ complex numbers so I knw it exists. But why am I getting the error? I choose to write this program in c++ so I must use something like the above to introduce and use complex numbers. This is one way in c++.
 
 
In Stanley Lippman's, C++ Primer, 2 ed on page 65 this is exactly how he does it syntactically; he of course usess a different example. I have also seen other code that does it this way. I am just not sure why i am gettng the error.
 
This should work. Any help appreciated, Thanx in advance.
 
 
Newport_j


my first guess is that you need to specify:
[php]
using namespace std;
[/php]

---

