---
title: "Help installing gcompris on Ubuntu"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by optimator prime on 2008-05-25
Hello,
New to Ubuntu & linux and am trying to install gcompris on my sons computer. Reading the instructions( I know this is a sign of weakness. :)) it seems simple enough.

Opan a terminal window, cd to the proper directory and... 
./configure
make
make install

configure produces the following error:

configure: error:  C compiler cannot create executables
See 'config.log' for more details.

The configure log contains the following info:

configure: 3262: result:
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "gcompris"
| #define VERSION "8.3.6"
| /* end confdefs.h. */
|
| int
| main()
| {
|
|  ;
|  return 0;
| }
configure:3269: error: C compiler cannot create executables
See 'config.log' for more details.


Has anyone experienced a similar problem? 

Any help would be greatly appreciated,

Cheers!

---

### Post by bsell on 2008-05-25
You can install it from the repositories. Use Add/Remove under the Applications menu.

---

### Post by optimator prime on 2008-05-26
Sure enough it worked.

Thanks!

---

