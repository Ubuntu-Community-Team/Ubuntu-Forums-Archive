---
title: "Find time in C"
date: 2010-08-10
forum: Programming Talk
---

### Post by jfreak_ on 2010-08-10
Hi i would like to find out the current time in C and then convert it so that the minutes and seconds are eliminated and i can store it in a int variable for further processing.

---

### Post by geirha on 2010-08-10
```
man strftime
```

If you don't have that man-page, install the [manpages-dev](apt:manpages-dev) package. That manual page also has example code you may find useful.

---

### Post by jfreak_ on 2010-08-12
i tried to negotiate the manpage but being a nOOb in C I couldn't make head or tail of it. Could someone give me a simple 4 line code?

---

### Post by dwhitney67 on 2010-08-12
Your requirements were a little vague, but I think this is what you are asking for:
```

#include <time.h>
#include <stdio.h>

int main(void)
{
   // get the current time
   time_t     now = time(0);
   struct tm* theTime = localtime(&now);

   // eliminate seconds and minutes
   theTime->tm_sec = 0;
   theTime->tm_min = 0;

   // convert the adjusted time back to a numeric format
   time_t adjTime = mktime(theTime);

   // display results
   printf("the time right now: %d\n", (int) now);
   printf("the adjusted time : %d\n", (int) adjTime);

   return 0;
}

```

---

### Post by jfreak_ on 2010-08-12
```

jfreak@jfreak-linuxbox:~/Desktop$ gcc -Wall a.c -o a
jfreak@jfreak-linuxbox:~/Desktop$ ./a
the time right now: 1281604109
the adjusted time : 1281601800

```

This is the output I got.
A bit wierd?

---

### Post by jfreak_ on 2010-08-12
i am marking this thread as solved , because I just read that the forum policy does not allow any post even remotely related to college assignments. 

Anyway just to lessen my guilt, this piece of code was required as a part of a MUCH bigger program (multi-thousand line program is big for my standards), and I didn't get the answer anywhere else and the manpages were cryptic at best for me.

---

### Post by dwhitney67 on 2010-08-12
> **jfreak_ said:**
> ... and the manpages were cryptic at best for me.
Well, there's always space at the Business School.

---

### Post by dwhitney67 on 2010-08-12
> **jfreak_ said:**
> ```

jfreak@jfreak-linuxbox:~/Desktop$ gcc -Wall a.c -o a
jfreak@jfreak-linuxbox:~/Desktop$ ./a
the time right now: 1281604109
the adjusted time : 1281601800

```

This is the output I got.
A bit wierd?

The time outputs represent the number of seconds since the Linux Epoch (1970/Jan/01 00:00:00).

What format were you expecting?  Your OP indicated that you required that the time value reside in an int variable.  The data type time_t is close enough.

If this was not what you require, may I suggest you take a course in communication.  Writing skills are essential in the Computer Science/Engineering realm; without them, you will not go far in your career.

---

### Post by geirha on 2010-08-12
Or maybe you just want the value of *theTime->tm_hour* from dwhitney67's example?

---

### Post by jfreak_ on 2010-08-12
[CODE]
int w;
    time_t now;
    if ( time(&now) != (time_t)(-1) )
    {
        struct tm *mytime = localtime(&now);
        if ( mytime )
        {
            char buffer [ 32 ];
            if ( strftime(buffer, sizeof buffer, "%H", mytime) )
            {
                    printf("buffer = \"%s\"\n", buffer);
                    w = atoi(&buffer[0]);    
                    printf("%d", atoi(&buffer[0]));
            }
        }
    }
[\CODE]
 
After a bit of fiddling around with a different bit of code I got what I required. There is surely going to be a shorter way and I welcome suggestions.

---

### Post by jfreak_ on 2010-08-12
whoops , got the slashes mixed up

---

### Post by interval1066 on 2010-08-12
This is what I did when I needed to time stamp output with a command line utility I recently wrote:

```

#include <time.h>

time_t timer;
struct tm *ptm;

time(&timer);
ptm = localtime(&timer);
sprintf(szDate, "%2d/%02d/%02d", ptm->tm_mon+1, ptm->tm_mday, ptm->tm_year%100);

```

Yep, that was for windows, do this for linux.

---

### Post by dwhitney67 on 2010-08-12
> **jfreak_ said:**
> ```

int w;
    time_t now;
    if ( time(&now) != (time_t)(-1) )
    {
        struct tm *mytime = localtime(&now);
        if ( mytime )
        {
            char buffer [ 32 ];
            if ( strftime(buffer, sizeof buffer, "%H", mytime) )
            {
                    printf("buffer = \"%s\"\n", buffer);
                    w = atoi(&buffer[0]);    
                    printf("%d", atoi(&buffer[0]));
            }
        }
    }
[\CODE]
 
After a bit of fiddling around with a different bit of code I got what I required. There is surely going to be a shorter way and I welcome suggestions.

IMPO, you have way too much error checking above.  Also, if all you wanted is the current hour, then examine the tm_hour field of the struct tm object.

In other words, this how I would have done it:
[code]
time_t     now = time(0);
struct tm* mytime = localtime(&now);

printf("%02d\n", mytime->tm_hour);

```

---

### Post by dwhitney67 on 2010-08-12
> **interval1066 said:**
> This is what I did when I needed to time stamp output with a command line utility I recently wrote:

```

#include <time.h>
<...>
std::stringstream ss;
char date[9];
char time[9];
_strdate_s(date);
_strtime_s(time);
ss << date << " " << time << " ";

```

The _strdate_s & _strtime_s funcs are the safe versions of strdate_s & strtime_s funcs respectively, and the output already happened to be formatted the way I wanted it (mm:dd:yyyy hh:mm:ss I believe).
Those functions are not available under Linux, are they?  Are they perhaps "band-aids" for Windoze?

P.S. For C++ code, include <ctime>, not <time.h>

---

