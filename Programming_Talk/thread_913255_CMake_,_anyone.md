---
title: "CMake , anyone?"
date: 2008-09-07
forum: Programming Talk
---

### Post by StOoZ on 2008-09-07
I want to distribute my app , now I decided to go with cmake , any good tutorial for it?
the docs on the site arent that good, search on google , but found nothing really helpful.

---

### Post by LaRoza on 2008-09-07
> **StOoZ said:**
> I want to distribute my app , now I decided to go with cmake , any good tutorial for it?
the docs on the site arent that good, search on google , but found nothing really helpful.

Without telling us what you had problems with, you'll only get more tutorials, likely the ones you found because most of us use google also.

[http://www.cmake.org/Wiki/CMake](http://www.cmake.org/Wiki/CMake)

---

### Post by StOoZ on 2008-09-07
ok , for a start , the FIND_LIBRARY doesnt work for me , even though I have these libaries...
I did that :
> 
MESSAGE( STATUS "Looking for quux")

FIND_LIBRARY (ALUT_LIBRARY alut /usr/local/lib /usr/lib /sw/lib)


IF (ALUT_LIBRARY)
       MESSAGE( STATUS "Looking for quux - found")
ELSE (ALUT_LIBRARY)
       MESSAGE( FATAL_ERROR "Looking for quux - not found")
ENDIF ( ${ALUT_LIBRARY} )


no sources , its only for testing , now I run it with cmake TEST 

where the CMakeLists.txt is in the TEST DIR.
and it doesnt find the libs....
any idea why?

---

### Post by hod139 on 2008-09-08
For FIND_LIBRARY, try:
```

FIND_LIBRARY(ALUT_LIBRARY  
    NAMES alut 
    PATHS 
      /usr/local/lib 
      /usr/lib
      /sw/lib) 

```

EDIT: I should add, this is looking for a file called libalut.so in one of the paths.  Your message stated that it is looking for quuz, so I just wanted to clarify what the find_library is looking for.

---

### Post by SeanHodges on 2008-09-09
Did hod139's suggestion help you? 

See [http://manpages.ubuntu.com/manpages/hardy/man1/cmake.html](http://manpages.ubuntu.com/manpages/hardy/man1/cmake.html) and search the page for FIND_LIBRARY. There is some detailed documentation on how to use it there.

Or if you want to read it off-line, type: "man cmake"

---

### Post by Jahocolips on 2010-07-11
I case anyone else comes across this, I just wrote a tutorial I think is pretty helpful. [http://mathnathan.com/2010/07/11/getting-started-with-cmake/](http://mathnathan.com/2010/07/11/getting-started-with-cmake/)

---

