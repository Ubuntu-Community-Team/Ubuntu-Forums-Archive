---
title: "Just getting started with C and can't compile"
date: 2011-02-09
forum: Programming Talk
---

### Post by Meph1st0 on 2011-02-09
I'm just started a very basic introductory course on C and I'm already running into problems simply compiling the first bit of code.  Here what's found in the student file titled L1-1.C:

```
/* 

 * welcome.c - This program prints a welcome message to the screen, and uses

 *             a variable to display the length of this course in days.

*/



#include <stdio.h>                   

                          

main()                               

{                                         

     int num;                        

     

     num = 4;                        

     printf("\nWelcome to the C course.");                   

     printf("\nThis course is %d days long.", num); 

}       
```

When I attempt to compile this with gcc L1-1.C I get the following output:

```
/tmp/cclEt4oo.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
```

I've installed build-essential but that's about it.  The file though might have been created with windows notepad or similar.  Is it possible that it's choking on some sort of Windows file format?

---

### Post by geoffmcc on 2011-02-09
Compiled for me. Copied and pasted into test.c and then ran make test

---

### Post by johnl on 2011-02-09
Rename your file to end with a lower case c instead of an upper case (e.g file.c instead of file.C)

gcc interprets an upper-case C file extension as indicating a C++ file, which is causing this issue.

---

### Post by Meph1st0 on 2011-02-09
If I try make L1-1.C I get:

make: Nothing to be done for `L1-1.C'.

---

### Post by Meph1st0 on 2011-02-09
That worked.  I just had to use a lowercase c instead.  Thanks!!

---

