---
title: "[C/C++] Converting time structure to date format"
date: 2009-04-02
forum: Programming Talk
---

### Post by dwhitney67 on 2009-04-02
How does one convert from a struct timeval (or timespec) to a struct tm?

Is there a C library function, or does one have to use mktime() to build a struct tm?

My ultimate goal is to generate a timestamp using asctime() or its thread-safe equivalent asctime_r().

I do not require any code for this help... just the name(s) of any C library function(s) I can use.

Thank you!

---

### Post by Shpongle on 2009-04-02
here's a predefined function to return the system time. mabye it can be of help, its in the stdlib.h header,

```

#include<iostream>
#include<string>
#include<stdlib.h>

using namespace std;







   main()
{

// Get the current time in seconds since midnight 1/1/70.

time_t now;
time(&now);
printf("Its %.24s\n",ctime(&now));
} 



```

---

### Post by dwhitney67 on 2009-04-02
> **DillByrne said:**
> here's a predefined function to return the system time. mabye it can be of help, its in the stdlib.h header,

```

#include<iostream>
#include<string>
#include<stdlib.h>

using namespace std;







   main()
{

// Get the current time in seconds since midnight 1/1/70.

time_t now;
time(&now);
printf("Its %.24s\n",ctime(&now));
} 



```

Thanks, I am familiar with ctime().  The issue I had is converting a struct timespec to something that I can use to formulate the time.

After resting my thoughts on this issue for a few hours, I have realized that I can convert the tv_sec field of the timespec to a time_t, and then yield the date (using ctime).  Then all I have to do is append the nanoseconds.  However that is easier stated than done.

What are my options with this, other than writing a boat-load of code?  Here's a sample app that unfortunately does nothing with the tv_nsec field:
```

#include <ctime>
#include <iostream>

int main()
{
  timespec ts;

  clock_gettime(CLOCK_REALTIME, &ts);

  time_t tt = ts.tv_sec;
  std::cout << ctime(&tt) << std::endl;

  // I would really like to use tv_nsec, so that my final output looked
  // something like:
  //
  //   Thu Apr  2 22:01:32.nnnnnnnnn 2009
  //
  // where nnnnnnnnn is the nanoseconds.
}

```

Btw, to compile the code above:
```

g++ time.cpp -lrt

```

----------------------------------------------
EDIT

I suppose this could suffice... I just wish there was a cleaner way:
```

#include <ctime>
#include <cstdio>
#include <iostream>
#include <iomanip>

int main()
{
  timespec ts;

  clock_gettime(CLOCK_REALTIME, &ts);

  char day[4], mon[4];
  int  wday, hh, mm, ss, year;

  sscanf(ctime((time_t*) &(ts.tv_sec)), "%s %s %d %d:%d:%d %d",
         day, mon, &wday, &hh, &mm, &ss, &year);

  std::cout << day << ' '
            << mon << ' '
            << std::setw(2) << std::setfill(' ') << wday << ' '
            << std::setfill('0')
            << hh << ':' << mm << ':' << ss << '.' << ts.tv_nsec << ' '
            << year
            << std::endl;
}

```

---

### Post by PaulFr on 2009-04-03
If you use mktime() to get the struct tm, you can use the strftime() to format the output in many interesting ways; and you do not need the sscanf() call.  See **_[http://www.opengroup.org/onlinepubs/009695399/functions/strftime.html](http://www.opengroup.org/onlinepubs/009695399/functions/strftime.html)_** for a list of options for strftime.

---

### Post by dwhitney67 on 2009-04-03
> **PaulFr said:**
> If you use mktime() to get the struct tm, you can use the strftime() to format the output in many interesting ways; and you do not need the sscanf() call.  See **_[http://www.opengroup.org/onlinepubs/009695399/functions/strftime.html](http://www.opengroup.org/onlinepubs/009695399/functions/strftime.html)_** for a list of options for strftime.

How can I build a struct tm from a struct timespec?

---

### Post by lloyd_b on 2009-04-03
> **dwhitney67 said:**
> How does one convert from a struct timeval (or timespec) to a struct tm?

Is there a C library function, or does one have to use mktime() to build a struct tm?

My ultimate goal is to generate a timestamp using asctime() or its thread-safe equivalent asctime_r().

I do not require any code for this help... just the name(s) of any C library function(s) I can use.

Thank you!
```
struct tm *localtime(const time_t *timep);
struct tm *localtime_r(const time_t *timep, struct tm *result);
```
I don't really see the point in this, however.  Why not just use ctime_r()(the thread-safe version of ctime()) to output a string to a buffer, and then, if you want, insert the nanoseconds from tv_nsec into the string at the proper point?

```
#include <iostream>
#include <string>
#include <ctime>

int main()
{
  std::string output;
  timespec ts;
  char buf[120];

  clock_gettime(CLOCK_REALTIME, &ts);

  ctime_r(&ts.tv_sec, buf);
  output = buf;

  std::cout << output.substr(0, 19)  << "." << ts.tv_nsec
            << " " << output.substr(20) << std::endl;

}
```

Lloyd B.

---

### Post by dwhitney67 on 2009-04-03
> **lloyd_b said:**
> ..
I don't really see the point in this, however.  Why not just use ctime_r()(the thread-safe version of ctime()) to output a string to a buffer, and then, if you want, insert the nanoseconds from tv_nsec into the string at the proper point?
...
I do not always see then end-posts as clearly as I should.  It did not occur to me to use a std::string, along with substr().  I will go with your example; it sure beats the sscanf() approach by a long-shot.

Thank you!

---

