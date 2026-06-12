---
title: "std::to_string -&gt; compiler error &quot;not a member of std&quot;"
date: 2013-04-18
forum: Programming Talk
---

### Post by Dirich on 2013-04-18
C++ reference specifies that in <string> there's the method "to_string ()" which allows me to insert a double into a string. For some reason my compiler tells me that to_string is not a method of <string>... any ideas?

The code used is in the attachment:
[ATTACH]241490[/ATTACH]

To compile you will need Eigen (just headers, no need to install)
[http://eigen.tuxfamily.org/index.php?title=Main_Page](http://eigen.tuxfamily.org/index.php?title=Main_Page)

without enabling EXTENDED_PRECISION you should have no need for mpfr++ (just a header) and mpfr (this library needs to be installed), thus in the compile line you should not add -lgmp and -lmpfr.

---

### Post by dwhitney67 on 2013-04-18
The std::string is API is documented here:  [http://www.cplusplus.com/reference/string/string/](http://www.cplusplus.com/reference/string/string/)

As you can confirm, there is no to_string() method associated with that object type.

If you want to insert a double into a string, perhaps with other text, then something like this is typically done:
```

#include <sstream>
#include <string>
...
double value = 3.145;
...
std::stringstream ss;
ss << "The value is: " << value;
...
std::string str = ss.str();    // unnecessary step, but shown to demonstrate how to obtain the string from stringstream.

```

EDIT:  It seems I misunderstood your post; there is an std::to_string() function available, that accepts a wide variety of types, and returns an std::string.  This function is only available with C++0X standards.  To compile your application with such, use the -std=c++0x compiler option.

---

