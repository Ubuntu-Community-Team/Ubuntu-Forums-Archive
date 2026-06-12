---
title: "Missing char* feature from Glib::ustring"
date: 2011-02-28
forum: Programming Talk
---

### Post by t1497f35 on 2011-02-28
Hi,
with a char* var one usually sets it to NULL and then the code can tell at any time if the var is already initiated (!= NULL). With Glib::ustring one can't do this, what do you folks usually do in this case?

---

### Post by ibuclaw on 2011-02-28
Glib::ustring looks to be pretty much the same as std::string

[http://library.gnome.org/devel/glibmm/unstable/classGlib_1_1ustring.html](http://library.gnome.org/devel/glibmm/unstable/classGlib_1_1ustring.html)


So you'd use 'empty() == true' or 'length() == 0' I guess.

```

Glib::ustring foo;
assert(foo.empty() == true);
assert(foo.length() == 0);

foo = "Hello";
assert(foo.empty() == false);
assert(foo.length() == 5);

foo.clear();
assert(foo.empty() == true);
assert(foo.length() == 0);

```

Regards

---

### Post by t1497f35 on 2011-02-28
Thanks, empty() reports if it's empty.
But **char*** can be
1) NULL (not initiated)
2) "" (initiated with value "", zero length)

See example below if you can spot the difference...

```

#include <iostream>
#include <glibmm.h>

int main() {
   
    Glib::ustring nonInited;
    Glib::ustring inited("");
    
    std::cout << "(ustring) not inited one is inited: " << nonInited.empty() << std::endl;
    std::cout << "(ustring) inited one is inited: " << inited.empty() << std::endl;
    
    const char *cNonInited = NULL;
    const char *cInited = "";
    
    std::cout << "(char*) not inited one is inited: " << (cNonInited != NULL) << std::endl;
    std::cout << "(char*) inited one is inited: " << (cInited != NULL) << std::endl;

    return 0;
}

```Which yields:
> 
(ustring) not inited one is inited: 1
(ustring) inited one is inited: 1
(char*) not inited one is inited: 0
(char*) inited one is inited: 1
Thus I can't find a way to tell if Glib::ustring has been initiated. With "char*" I test against NULL to figure out on the fly whether I need to do a one time initialization or not which in turn issues other benefits which for the sake of brevity I won't discuss (also cause it's a matter of taste too).

---

### Post by t1497f35 on 2011-02-28
There we go, Glib::ustring.length() != 0 works!
Thanks!

---

### Post by t1497f35 on 2011-02-28
Hmmm.. but length() also returns false even when the ustring is initiated with "".. so it's not quite what I need..
Here's the (same) code I used to check it with:

```

#include <iostream>
#include <glibmm.h>

int main() {
   
    Glib::ustring nonInited;
    Glib::ustring inited("");
    
    std::cout << "(ustring) not inited one is inited: " << nonInited.empty() << std::endl;
    std::cout << "(ustring) not inited one is inited: " << (nonInited.length() != 0) << std::endl;
    std::cout << "(ustring) inited one is inited: " << inited.empty() << std::endl;
    std::cout << "(ustring) inited one is inited: " << (inited.length() != 0) << std::endl;
    
    const char *cNonInited = NULL;
    const char *cInited = "";
    
    std::cout << "(char*) not inited one is inited: " << (cNonInited != NULL) << std::endl;
    std::cout << "(char*) inited one is inited: " << (cInited != NULL) << std::endl;

    return 0;
}  

```> 
(ustring) not inited one is inited: 1
(ustring) not inited one is inited: 0
(ustring) inited one is inited: 1
(ustring) inited one is inited: 0
(char*) not inited one is inited: 0
(char*) inited one is inited: 1
So length() is also only about the length of the string, not about whether it's been initiated or not.

---

### Post by Vaphell on 2011-02-28
can't you use similar method and go with pointers in this case? pointer empty - no object, pointer not empty - object created and initialized

---

### Post by t1497f35 on 2011-02-28
I'm actually using const char* in some cases because of this, and I started this thread cause I've been wondering how other people come around this, if at all.

---

### Post by ibuclaw on 2011-02-28
> **t1497f35 said:**
> Hmmm.. but length() also returns false even when the ustring is initiated with "".. so it's not quite what I need..
Here's the (same) code I used to check it with:

<snip>

So length() is also only about the length of the string, not about whether it's been initiated or not.

C++ string are always initialised. Even assigning a NULL pointer to one throws an exception.

---

