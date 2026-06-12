---
title: "Error while compiling c program for getting system time"
date: 2009-03-22
forum: Programming Talk
---

### Post by sreeyeshns on 2009-03-22
I want to get the system time with millisecond precision. When I searched the net I got the following code.

```
#include <stdio.h>
#include <sys/timeb.h>
#include <time.h>
int main()
{
   struct _timeb timebuffer;
   char *timeline;

   _ftime( &timebuffer );
   timeline = ctime( & ( timebuffer.time ) );

   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm, &timeline[20] );
   return 0;
}
```

But when I compile it I get an error message.

asd.c:7: error: storage size of ‘timebuffer’ isn’t known

Can someone tell me where and why the code went wrong?
I will be grateful if someone explain how the code works too.

 I haven't used the time.h and sys/timeb.h library before.One more thing. I'm not an expert in C but just an electronic student learning C. Someone please reply keeping these facts in mind....... :)

---

### Post by jpeddicord on 2009-03-22
_timeb on line 6 should probably just be timeb. /usr/include/sys/timeb.h has the full structure definition:

```
struct timeb
  {
    time_t time;		/* Seconds since epoch, as from `time'.  */
    unsigned short int millitm;	/* Additional milliseconds.  */
    short int timezone;		/* Minutes west of GMT.  */
    short int dstflag;		/* Nonzero if Daylight Savings Time used.  */
  };
```

---

### Post by sreeyeshns on 2009-03-29
> **jacobmp92 said:**
> _timeb on line 6 should probably just be timeb. /usr/include/sys/timeb.h has the full structure definition:

```
struct timeb
  {
    time_t time;		/* Seconds since epoch, as from `time'.  */
    unsigned short int millitm;	/* Additional milliseconds.  */
    short int timezone;		/* Minutes west of GMT.  */
    short int dstflag;		/* Nonzero if Daylight Savings Time used.  */
  };
```
Hurray. At last it worked. Thank you very much. The correct code is

```
#include <stdio.h>
#include <sys/timeb.h>
#include <time.h>

int main()
{
   struct timeb timebuffer;
   char *timeline;

   ftime( &timebuffer );
   timeline = ctime( & ( timebuffer.time ) );

   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm, &timeline[20] );
   return 0;
}
```

---

