---
title: "C++ libxml2 compile errors"
date: 2009-03-30
forum: Programming Talk
---

### Post by ddili on 2009-03-30
hey all!

i've installed the libxml2 development package using:
**sudo apt-get install libxml2-dev**

and i have a simple test program to make sure it installed properly:

testxml.cpp:```
#include <libxml2/libxml/tree.h>
#include <libxml2/libxml/parse.h>

using namespace std;

int main()
{
        xmlDocPtr doc;

        return 0;
}
```but get a slew of errors from the libxml2 header files when compiling with the following:
**g++ testxml.cpp**

[i]/usr/include/libxml2/libxml/tree.h:87: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:154: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:155: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:156: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:201: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:215: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:226: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:228: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:229: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:268: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:272: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:308: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:319: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:351: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:352: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:368: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:381: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:382: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:396: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:418: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:420: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:435: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:437: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:451: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:461: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:515: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:516: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:519: error: expected ‘;’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:543: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/libxml2/libxml/tree.h:614: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:619: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:622: error: expected constructor, destructor, or type conversion before ‘const’
/usr/include/libxml2/libxml/tree.h:630: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:632: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:635: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:637: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:639: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:642: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:645: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:647: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:650: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:654: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:658: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:661: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:664: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:667: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:670: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:672: error: expected constructor, destructor, or type conversion before ‘const’
/usr/include/libxml2/libxml/tree.h:674: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:677: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:683: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:688: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:693: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:695: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:703: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:707: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:709: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:711: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:713: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:715: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:726: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:731: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:736: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:738: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:740: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:743: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:758: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:763: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:768: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:771: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:781: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:784: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:786: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:790: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:793: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:797: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:800: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:803: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:805: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:809: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:812: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:815: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:818: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:822: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:825: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:845: error: expected constructor, destructor, or type conversion before ‘long’
/usr/include/libxml2/libxml/tree.h:851: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:853: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:855: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:857: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:873: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:876: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:890: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:893: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:896: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:898: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:901: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:905: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:907: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:909: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:912: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:918: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:922: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:932: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:935: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:937: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:954: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:957: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:960: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:963: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:967: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:971: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:974: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:978: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:988: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:997: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:1000: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:1004: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:1006: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:1009: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:1011: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:1021: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:1033: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:1048: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:1051: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:1054: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:1155: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:1162: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:1164: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:1167: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:1169: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:1175: error: ‘XMLPUBFUN’ does not name a type
/usr/include/libxml2/libxml/tree.h:1177: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/libxml2/libxml/tree.h:1179: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:1183: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:1190: error: expected constructor, destructor, or type conversion before ‘int’
/usr/include/libxml2/libxml/tree.h:1195: error: expected constructor, destructor, or type conversion before ‘int’[/i]

anyone have any idea how to resolve these errors?

---

### Post by dwhitney67 on 2009-03-30
Write your code like:
```

#include <libxml/tree.h>

int main()
{
  xmlDocPtr doc;
}

```

Note the path leading to the 'tree.h' header file; you do not need to specify libxml2.

When compiling/linking, use something similar to:
```

g++ -I/usr/include/libxml2 testxml.cpp -lxml2

```
You may also want to get into the habit of using the '-Wall', '-pedantic', and '-ansi' g++ flags.  Don't be alarmed if you use these compiler flags and a warning is given concerning that 'doc' is not used.

---

### Post by ddili on 2009-03-31
thanks for your reply **dwhitney67**!

the reason i put the full path is because eclipse was complaining that it couldn't resolve the inclusion! now i added xml2 to my eclipse project's libraries and /usr/include/libxml2 to the project's directory includes and everything seems to do working fine!

thanks again for your reply! :D

---

