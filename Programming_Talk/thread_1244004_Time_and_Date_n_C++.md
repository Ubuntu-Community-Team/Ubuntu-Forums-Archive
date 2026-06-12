---
title: "Time and Date n C++"
date: 2009-08-19
forum: Programming Talk
---

### Post by Sly Rudolf on 2009-08-19
Hi,
 
I am writing a C++ program (on Ubuntu) and was wondering how to get the time and date (from real life) into the program so I can use it to compare dates form data to.

Any help or advice on where to look would be most appreciated.

---

### Post by gtr32 on 2009-08-19
[http://www.cplusplus.com/reference/clibrary/ctime/time/](http://www.cplusplus.com/reference/clibrary/ctime/time/)

---

### Post by dwhitney67 on 2009-08-19
[http://www.boost.org/doc/libs/1_37_0/doc/html/date_time.html](http://www.boost.org/doc/libs/1_37_0/doc/html/date_time.html)

---

### Post by MindSz on 2009-08-19
This is small C program that prints out current date
```
#include <stdio.h>
#include <time.h>
#include<string.h>

int main (){

  time_t date_temp;       // Stores seconds elapsed since 01-01-1970
  struct tm *date_format; // Saves in Date format
  char date_out[25];      // Output string

  time(&date_temp);
  date_format = localtime(&date_temp);
  strftime(date_out, 25, "%Y-%m-%d, %H:%M:%S", date_format);
  
  printf ("\nDate: %s\n\n", date_out);
  
  return 0;
}

```

---

### Post by Sly Rudolf on 2009-08-19
Cheers. Thanks

---

