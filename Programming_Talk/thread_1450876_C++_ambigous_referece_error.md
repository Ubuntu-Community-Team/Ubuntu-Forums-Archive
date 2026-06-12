---
title: "C++ ambigous referece error"
date: 2010-04-09
forum: Programming Talk
---

### Post by Houman on 2010-04-09
hello there;

I am linking against two libraries and it seems they are both defining something with the same name and this is causing a lot of errors like this:

```

 error: reference to 'real' is ambiguous
 error: candidates are: ....

```

 and a few such errors like this;

is there any way i can compile my code without having to mess with the codes of these individual libraries?

regards

H

---

### Post by gnometorule on 2010-04-09
Maybe I'm blanking, but couldn't you write your own header while wrapping the older header file into an unnamed namespace:

namespace{
#include "header for lib1"
}, 

or into a named one, then include this new header file instead? Currently not 100% sure if it works.

---

### Post by Houman on 2010-04-09
hi there;

no luck, i tried it but it spews out a zillion errors when i do;

H

---

### Post by gnometorule on 2010-04-09
Do you use any 'using directives' in your own code, referring to those 2 libraries?

Do the 'ambigous references' refer to bits of your own code? You probably get a file/line number (?).

Does one or the other library (or both) provide (also) access to its functions using a namespace qualifier (e.g. lib1::real, lib2::real), or are the functions provided by both put straight into the global namespace and you can only access them with 'real'?

---

### Post by Houman on 2010-04-11
hello ;

I dont use any "using" directives to refer to these libraries, actually this name conflict occurrs in the case of a few structures that i dont use directly but the libraries use in their own code. 

The 'ambigous references' errors only refer to the header files in the two libraries and not to my own code, so the line numbers refer not to my code. 

thank you
H

---

### Post by azagaros on 2010-04-15
if all else fails,

cast it, or prototype it to see if that helps to clear up the ambiguity.

---

