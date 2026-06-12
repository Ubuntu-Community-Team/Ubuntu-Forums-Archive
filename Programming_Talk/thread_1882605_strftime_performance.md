---
title: "strftime performance"
date: 2011-11-17
forum: Programming Talk
---

### Post by karlson on 2011-11-17
I have run into an interesting performance conundrum but before I start delving into glibc and entering bugs left right and center I just wanted to get to get any insight that might be out there.

I have code that in one of the functions does this:

```

gettimeofday( &tv, 0);
localtime_r( &tv.tv_sec, &local_tm );
char result[25];
strftime( result, 24, "%Y-%m-%d %H:%M:%S", &local_tm);

```

The rest of the code is irrelevant for this question.  When I replace it with this:

```

gettimeofday( &tv, 0);
localtime_r( &tv.tv_sec, &local_tm );
char result[25];
snprintf(result, sizeof(result), "%04d-%02d-%02d %02d:%02d:%02d",
         local_tm.tm_year+1900, local_tm.tm_mon+1,
         local_tm.tm_mday, local_tm.tm_hour, local_tm.tm_min,
         local_tm.tm_sec);

```

on average I get 20% performance boost.

Has anyone ran into this?

---

### Post by Bachstelze on 2011-11-17
> **karlson said:**
> 
on average I get 20% performance boost.


You mean it makes your program

[img]http://fc05.deviantart.net/fs70/f/2011/110/8/e/20_cooler_rd_by_chivadecorazon-d3eg5yl.jpg[/img]

Is it really so surprising? strftime is a big function, and in particular, it is locale-dependent. That means everything has to be computed depending on the locale, which adds a lot of computation time. snprintf is also a big function, but still more straightforward because it isn't locale-dependent (as long as you stick to ASCII characters).

---

### Post by MadCow108 on 2011-11-17
how is 20% performance difference relevant when you are formating timestamps?
that should hardly be the bottleneck of applications.

for me the strftime variant is double as fast as snprintf btw., don't know why my result is the opposite of yours.

---

### Post by crdlb on 2011-11-17
A google search turned up: [https://bugzilla.redhat.com/show_bug.cgi?id=171351](https://bugzilla.redhat.com/show_bug.cgi?id=171351)

Apparently, strftime stats /etc/localtime every time it's called.

---

### Post by karlson on 2011-11-17
> **crdlb said:**
> A google search turned up: [https://bugzilla.redhat.com/show_bug.cgi?id=171351](https://bugzilla.redhat.com/show_bug.cgi?id=171351)

Apparently, strftime stats /etc/localtime every time it's called.

This one I have seen.

---

### Post by karlson on 2011-11-17
> **MadCow108 said:**
> how is 20% performance difference relevant when you are formating timestamps?
that should hardly be the bottleneck of applications.

for me the strftime variant is double as fast as snprintf btw., don't know why my result is the opposite of yours.

Not sure how, but I just repeated the test with this code on Solaris and got:
```


#include <stdio.h>
#include <sys/time.h>

int main(int argc, char *argv[])
{
   int num_iter = atoi(argv[1]);

   struct timeval start_tv, end_tv;
   char result[25];
   gettimeofday(&start_tv, 0);
   for(int i = 0 ; i < num_iter ; ++i)
   {
        struct timeval tv;
        struct tm local_tm;
        gettimeofday(&tv, 0);
        localtime_r( &tv.tv_sec, &local_tm);
        strftime( result, 24, "%Y-%m-%d %H:%M:%S", &local_tm);
   }
   gettimeofday(&end_tv, 0);

   fprintf(stderr, "STRFTIME took: %d seconds", end_tv.tv_sec - start_tv.tv_sec);


   gettimeofday(&start_tv, 0);
   for(int i = 0 ; i < num_iter ; ++i)
   {
        struct timeval tv;
        struct tm local_tm;
        gettimeofday(&tv, 0);
        localtime_r( &tv.tv_sec, &local_tm);
        snprintf(result, sizeof(result), "%04d-%02d-%02d %02d:%02d:%02d",
                 local_tm.tm_year+1900, local_tm.tm_mon+1,
                 local_tm.tm_mday, local_tm.tm_hour, local_tm.tm_min,
                 local_tm.tm_sec);
   }
   gettimeofday(&end_tv, 0);
   fprintf(stderr, "SNPRINTF took: %d seconds", end_tv.tv_sec - start_tv.tv_sec);
}

```
Result:
```


./a.out 10000000
STRFTIME took: 28 seconds
SNPRINTF took: 22 seconds

```

---

### Post by Bachstelze on 2011-11-17
Actually, yes, snprintf is also slower here on Ubuntu (it is faster on OS X). Very interesting, maybe Debian/Ubuntu did something about the issue described in crdlb's link?

---

### Post by karlson on 2011-11-17
> **Bachstelze said:**
> Actually, yes, snprintf is also slower here on Ubuntu (it is faster on OS X). Very interesting, maybe Debian/Ubuntu did something about the issue described in crdlb's link?

Here is RHEL w/glibc-2.5-34
```

./a.out 10000000
STRFTIME took: 23 seconds
SNPRINTF took: 13 seconds

```

Could it be that they didn't fix strftime but messed up snprintf?
I guess it's GLIBC diving for me....

---

### Post by karlson on 2011-11-17
> **MadCow108 said:**
> how is 20% performance difference relevant when you are formating timestamps?
that should hardly be the bottleneck of applications.

for me the strftime variant is double as fast as snprintf btw., don't know why my result is the opposite of yours.

Curioser and curioser...  Ubuntu works correctly.

---

