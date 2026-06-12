---
title: "Anjuta and libdc1394"
date: 2007-07-24
forum: Programming Talk
---

### Post by Deichgraf on 2007-07-24
Hi,

I am needing a HOW TO to add libdc1394 to Anjuta IDE.

I already tried to install libdc1394-dev on my system, but for reasons not know libdc1394 header files such as  dc1394_control.h and others are missing, although the library itself seems to be present on my system (feisty).

Any suggestions??

Thanks

Christian

---

### Post by Deichgraf on 2007-07-24
Hi,

I found the solution myself:

In Anjuta, open  Settings -> Compiler and Linker Settings, then type dc1394_control into the text box, click Add button  and finally close the dialog. That's it.

In Anjuta the "lib" prefix and the ".a" suffix of the lib name are omitted when entering it into the above mentioned text box.

The dc1394_control.h file was finally found in /usr/include/libdc1394, so text line

#include "libdc1394/dc1394_control.h"

was added on top of main.c

Now the project can be sucessfully generated, all header files and libraries are found.


Christian

---

