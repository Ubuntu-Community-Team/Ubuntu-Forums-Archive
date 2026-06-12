---
title: "How to change local time using C"
date: 2009-09-10
forum: Programming Talk
---

### Post by akvseiji on 2009-09-10
How to change date and time in PC using C?

I found a function: **settimeofday()** but don't know how to use it.

Can someone help me pls..

---

### Post by lloyd_b on 2009-09-10
> **akvseiji said:**
> How to change date and time in PC using C?

I found a function: **settimeofday()** but don't know how to use it.

Can someone help me pls..

In a terminal window:```
sudo apt-get install manpages-dev
man settimeofday
```
This will give you the documentation on the settimeofday() function.

Lloyd B.

---

### Post by akvseiji on 2009-09-10
> **lloyd_b said:**
> In a terminal window:```
sudo apt-get install manpages-dev
man settimeofday
```
This will give you the documentation on the settimeofday() function.

Lloyd B.

I've seen the manual of settimeofday().
But still can't understand how it works.
**Can someone give me some example on how to use it**.

From what I see, timeval struct in settimeofday() only provide seconds and microseconds.
But I want to change the whole system time including date.

---

### Post by lloyd_b on 2009-09-11
> **akvseiji said:**
> I've seen the manual of settimeofday().
But still can't understand how it works.
**Can someone give me some example on how to use it**.

From what I see, timeval struct in settimeofday() only provide seconds and microseconds.
But I want to change the whole system time including date.

What you need to understand is that the "seconds" in the timeval structure is the number of seconds since the "epoch" (00:00:00 UTC, January 1, 1970).  This is the basic unit of time on the system - it is converted, via various functions, to the year/date/hours/minutes/seconds format that you normally see.

So here's a list of steps changing the system time to any arbitrary value:

1.  Use gettimeofday() to get a struct timeval.
2.  Use localtime() to convert the "seconds" element of timeval into a struct tm (which has all the of individual values you might want to tweak).
3.  Change the values in the struct tm.
4.  Use mktime() to convert the struct tm back into a time_t, and assign it to the "seconds" element of the struct timeval.
5.  Use settimeofday() to apply the changes to the system clock.

I don't have any code handy to show this being done (and I don't feel like writing any at the moment), but between the instructions above and the manpages for those functions you should have enough to work with.

Lloyd B.

---

### Post by akvseiji on 2009-09-15
I've found another function that can change date and time; **execl()**.
Before I use this function, I have to disable sudo password.

When I run, it change my date/time successfully.

This is my code:
```
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <sys/time.h>
#include <errno.h>

int main()
{
    //MMDDhhmmYY.ss
    char dTime[13] = "0820102508.30";   //20 Aug 2008 10:25:30am
    int n;

    n = execl("/usr/bin/sudo", "/bin/date", "date", dTime, NULL);
    if (n == -1)
    {
        fprintf(stdout, "ERRNO[%d]:", errno);
        perror(" ");
    }

    fprintf(stdout, "Date Changed\n\n");   //Confirmation!!

    return 0;
}

```

However, after debugger execute execl(),
it will **terminated automatically**,
without execute the fprintf() function ("Date Change\n\n").
This is a big problem to me.

I don't understand why it happen.
How to counter this problem?
Can someone help me please...

TQ.

---

### Post by lloyd_b on 2009-09-15
Any "exec...()" function will do the same.  They do NOT return to the calling program, the *replace* the calling program with the program that is being executed.

Since you're just using a wrapper for the "date" command, I'd suggest using system() rather than execl():```
#include <stdio.h>

int main()
{
    system("date 0820102508.30");
    printf("Date changed!\n");

    return 0;
}
```

Lloyd B.

---

### Post by akvseiji on 2009-09-15
Hi Lloyd B.

Thank you very much for your help.
I've **solve** it.

Here is my code:
```
char dTime[14] = "0915175309.00";
char dInput[24];

sprintf(dInput, "sudo date %s", dTime);

system(dInput);

fprintf(stdout, "Date Changed\n\n");
```

It works successfully.
**Thanks** again.

---

### Post by dwhitney67 on 2009-09-15
Since you originally asked about settimeofday(), I thought it would (finally) be appropriate to post a short/simple piece of code.
```

#include <sys/time.h>
#include <time.h>

int main()
{
   time_t theTimeInSeconds = time(0);

   theTimeInSeconds += (3 * 60 * 60);   // add 3 hours (3 * 60 mins * 60 secs) to current time

   struct timeval tv = { theTimeInSeconds, 0 };

   settimeofday(&tv, 0);

   return 0;
}

```
An attempt to use settimeofday() will fail unless the user running the application has super-user privileges.  Thus to run the app above, login as root or use sudo.

P.S.  I probably should have used gettimeofday() instead of time().  Here's how:
```

#include <sys/time.h>

int main()
{
   struct timeval tv;

   gettimeofday(&tv, 0);

   tv.tv_sec += (3 * 60 * 60);   // add 3 hours (3 * 60 mins * 60 secs) to current time

   settimeofday(&tv, 0);

   return 0;
}

```

---

### Post by akvseiji on 2009-09-15
Hi dwhitney,

From what I see of your post,
settimeofday() **cannot** change to the specific date,
**unless** we know what is our current time.
Am I right?

**Let say**,
If I want to change my date to **14 Sept 2008 - 13h45m20s**,
but I **don't know** my current time,
so, when I use settimeofday(),
**how** much time I must put to tv.tv_sec?
**tv.tv_sec += ????**

Can settimeofday() do that?
Or I just miss understand..?

---

### Post by lloyd_b on 2009-09-16
> **akvseiji said:**
> Hi dwhitney,

From what I see of your post,
settimeofday() **cannot** change to the specific date,
**unless** we know what is our current time.
Am I right?

**Let say**,
If I want to change my date to **14 Sept 2008 - 13h45m20s**,
but I **don't know** my current time,
so, when I use settimeofday(),
**how** much time I must put to tv.tv_sec?
**tv.tv_sec += ????**

Can settimeofday() do that?
Or I just miss understand..?

The proper way to handle that is to create a struct tm with the values you want, and then pass it to mktime() to get the correct value for tv_sec:
```
#include <stdio.h>
#include <time.h>
#include <sys/time.h>

int main()
{
    struct tm mytime;
    struct timeval systime;
    char * text_time;

    mytime.tm_sec = 20;    // Seconds
    mytime.tm_min = 45;    // Minutes
    mytime.tm_hour = 13;   // Hours
    mytime.tm_mday = 14;      // Day of Month
    mytime.tm_mon = 8;     // Month
    mytime.tm_year = 108; // Year


    systime.tv_sec = mktime(&mytime);
    systime.tv_usec = 0;

    settimeofday(&systime, NULL);

    /* Time of day is set.  Now, let's get it, and verify that it looks right */
    gettimeofday(&systime, NULL);

    text_time = ctime(&systime.tv_sec);

    printf("The system time is set to %s\n", text_time);

    return 0;

}
```
 Note: like any program that sets the system time, this must be run with "sudo", or it won't have any effect.

For details on the mktime() command and struct tm, "man mktime" in a terminal window.

Lloyd B.

---

### Post by akvseiji on 2009-09-16
Hi **Lloyd B** and **dwhitney**,

**Thank you** for your help.
Very appreciate that.

---

