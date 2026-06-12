---
title: "C++ Noob question"
date: 2009-01-27
forum: Programming Talk
---

### Post by mhh91 on 2009-01-27
now i'm learning to program in C++,still in the basic stuff

how can i show the result of something like this


```
(5 == 7)
```

i know this will be "false" but it just doesn't show up in the code


thanks for any help :)

---

### Post by cabalas on 2009-01-27
I'm a little unsure of what you mean by show, if you want it to be printed out to a console then this will work

[PHP]std::cout << (5 == 7) << std::endl;[/PHP]

Though all you will get is printed is 0 (remembering that 0 is false and 1 is true) due to the way that boolean values are handled by C++.

---

### Post by monkeyking on 2009-01-27
I normally interpret bools as ints so I would do

printf("res:%d\n",5==7)

which would be res:0

---

### Post by noerrorsfound on 2009-01-27
> **monkeyking said:**
> I normally interpret bools as ints so I would do

printf("res:%d\n",5==7)

which would be res:0
That's the C way to do it.
```

    if ((5 == 7) == false)
        std::cout << "It is false." << std::endl;
    else
        std::cout << "It is true." << std::endl;

```
False is defined as zero, but true can be any non-zero value.

---

### Post by mhh91 on 2009-01-27
> **cabalas said:**
> I'm a little unsure of what you mean by show, if you want it to be printed out to a console then this will work

[PHP]std::cout << (5 == 7) << std::endl;[/PHP]

Though all you will get is printed is 0 (remembering that 0 is false and 1 is true) due to the way that boolean values are handled by C++.

that did help,thanks :)


but does it have to be in a separate function?

the zero didn't show up until i created another function and put these lines in it

---

### Post by noerrorsfound on 2009-01-27
Compiles fine for me:
```
#include <iostream>

int main()
{
    std::cout << (5 == 7) << std::endl;
    return EXIT_SUCCESS;
}


```

---

### Post by mhh91 on 2009-01-27
> **noerrorsfound said:**
> Compiles fine for me:
```
#include <iostream>

int main()
{
    std::cout << (5 == 7) << std::endl;
    return EXIT_SUCCESS;
}


```

i'm using "geany" ,it says :

```
untitled.cpp:6: error: ‘EXIT_SUCCESS’ was not declared in this scope
```

---

### Post by noerrorsfound on 2009-01-27
> **mhh91 said:**
> i'm using "geany" ,it says :

```
untitled.cpp:6: error: &#8216;EXIT_SUCCESS&#8217; was not declared in this scope
```
Try returning 0, then. EXIT_SUCCESS is just a more portable way of doing it.

[http://www.cplusplus.com/reference/clibrary/cstdlib/EXIT_SUCCESS.html](http://www.cplusplus.com/reference/clibrary/cstdlib/EXIT_SUCCESS.html)

Oh, my fault. EXIT_SUCCESS is defined in cstdlib, thus you must also:
#include <cstdlib>

Or simply use 0.

---

### Post by mhh91 on 2009-01-27
> **noerrorsfound said:**
> Try returning 0, then. EXIT_SUCCESS is just a more portable way of doing it.

[http://www.cplusplus.com/reference/clibrary/cstdlib/EXIT_SUCCESS.html](http://www.cplusplus.com/reference/clibrary/cstdlib/EXIT_SUCCESS.html)

Oh, my fault. EXIT_SUCCESS is defined in cstdlib, thus you must also:
#include <cstdlib>

Or simply use 0.

thanks,it worked :)


but can you tell me why we put " std::" there?

---

### Post by DeadRobot on 2009-01-27
We use std to access the C++ standard library.
[http://en.wikipedia.org/wiki/C%2B%2B_standard_library](http://en.wikipedia.org/wiki/C%2B%2B_standard_library)

---

### Post by cabalas on 2009-01-27
'std' is the namespace to which cout (along with the rest of the standard library) belongs to, we use :: to access items in that namespace.  We could have just as easily put 

[PHP]using namespace std;[/PHP]

after the headers and then omitted the all of the 'std::' I think wikipedia probably has a better explanation [http://en.wikipedia.org/wiki/Namespace_(computer_science](http://en.wikipedia.org/wiki/Namespace_(computer_science))

---

### Post by mhh91 on 2009-01-27
> **cabalas said:**
> 'std' is the namespace to which cout (along with the rest of the standard library) belongs to, we use :: to access items in that namespace.  We could have just as easily put 

[PHP]using namespace std;[/PHP]

after the headers and then omitted the all of the 'std::' I think wikipedia probably has a better explanation [http://en.wikipedia.org/wiki/Namespace_(computer_science](http://en.wikipedia.org/wiki/Namespace_(computer_science))

i already use this method to declare a namespace ,thank you again :)

---

### Post by sujoy on 2009-01-28
> **noerrorsfound said:**
> That's the C way to do it.
```

    if ((5 == 7) == false)
        std::cout << "It is false." << std::endl;
    else
        std::cout << "It is true." << std::endl;

```
False is defined as zero, but true can be any non-zero value.

(5 == 7) == false is a bit redundant, dont you think?

```

if (5 == 7)
    std::cout << "It is true." << std::endl;
else
    std::cout << "It is false." << std::endl;

```

---

### Post by geirha on 2009-01-28
You can also have cout print "true" and "false" instead of "1" and "0", when given a bool.
```
cout << boolalpha << (5==7) << endl;
```

---

