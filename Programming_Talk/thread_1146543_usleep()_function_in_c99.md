---
title: "usleep() function in c99"
date: 2009-05-02
forum: Programming Talk
---

### Post by sdunatunga on 2009-05-02
Hi all,

I am writing a small program where I need to sleep for a small amount of time (50 milliseconds), but one of the requirements is that it must compile cleanly (no warnings) with -std=c99. I keep getting an ```
"error: implicit declaration of function ‘usleep’"
``` when I try to use usleep, and a similar ```
"error: implicit declaration of function ‘nanosleep’"
``` when I try to use nanosleep. It's normally just a warning but to enforce the requirements I compile with -Werror. Good old sleep() works, but its granularity is too large for this application -- ideally the program would only wait for 50-100 ms. I know I could probably adopt clock() for this but I'd prefer not to waste cycles in an do-nothing loop. Does anyone have any suggestions?

Thanks,

sdunatunga

---

### Post by eye208 on 2009-05-02
Did you include the header files for those functions?

usleep() is declared in unistd.h.

nanosleep() is declared in time.h.

---

### Post by sdunatunga on 2009-05-02
Yes, they're included, the problem is that -std=c99 means that those two functions are unavailable. The program compiles fine (no warnings) without the -std=c99 option, but I can't just leave it out because it is part of the requirements.

Looking through these threads, I see that there is a way to (ab)use select() to do a delay; does anyone have any thoughts on this method? My other way was going to use clock() but that would surely waste a ton of cycles, and I'm assuming select() will yield instead of wasting them...

---

### Post by Arndt on 2009-05-02
> **sdunatunga said:**
> Yes, they're included, the problem is that -std=c99 means that those two functions are unavailable. The program compiles fine (no warnings) without the -std=c99 option, but I can't just leave it out because it is part of the requirements.

Looking through these threads, I see that there is a way to (ab)use select() to do a delay; does anyone have any thoughts on this method? My other way was going to use clock() but that would surely waste a ton of cycles, and I'm assuming select() will yield instead of wasting them...

After some experimenting, I see that you can use -ansi to make gcc quiet about 'usleep':

```
gcc --std=c99 -ansi -o usleep usleep.c
```

But I can't make it find the needed declaration of "struct timespec" when I use 'nanosleep' (and that's the recommended one - 'usleep' being obsolete according to the man page).

---

### Post by dwhitney67 on 2009-05-02
> **Arndt said:**
> ...
But I can't make it find the needed declaration of "struct timespec" when I use 'nanosleep' (and that's the recommended one - 'usleep' being obsolete according to the man page).

I found, from experimenting and reviewing the /usr/include/features.h file, that this will work for nanosleep().
```

/usr/bin/gcc -std=c99 -D_POSIX_C_SOURCE=199309L nanosleeptest.c

```
P.S.  The -std=c99 is optional.

---

### Post by Arndt on 2009-05-02
> **Arndt said:**
> After some experimenting, I see that you can use -ansi to make gcc quiet about 'usleep':

```
gcc --std=c99 -ansi -o usleep usleep.c
```

But I can't make it find the needed declaration of "struct timespec" when I use 'nanosleep' (and that's the recommended one - 'usleep' being obsolete according to the man page).

Now I succeeded. The solution lies in the file /usr/include/features.h. What it says is probably documented somewhere else too, but I don't know where.

```
$ cat nano.c
#define _POSIX_C_SOURCE	199309L
#include <time.h>

int main(void)
{
    struct timespec s;
    s.tv_sec = 0;
    s.tv_nsec = 500000000L;
    nanosleep(&s, NULL);
    return 0;
}
$ gcc --std=c99 -o nano nano.c
$
```

---

### Post by sdunatunga on 2009-05-02
Thanks guys, I now have several different options to choose from. If anyone can recommend something in terms of portability I'd like to hear it.

---

### Post by wmcbrine on 2009-05-02
usleep() is a POSIX function. I wouldn't expect it to be portable beyond POSIX systems. Pure standard C will not give you anything finer-grained than sleep(), AFAIK. Such is life.

---

### Post by dwhitney67 on 2009-05-02
> **wmcbrine said:**
> usleep() is a POSIX function. I wouldn't expect it to be portable beyond POSIX systems. Pure standard C will not give you anything finer-grained than sleep(), AFAIK. Such is life.

Windoze is POSIX compliant... yes, I know, hard to believe, but that is the truth.

Additionally, there's always select(); it is available in Linux, Unix, and Windoze.

---

### Post by wmcbrine on 2009-05-03
> **dwhitney67 said:**
> Windoze is POSIX compliant...[After a fashion...](http://en.wikipedia.org/wiki/Microsoft_POSIX_subsystem) as a dodge... and not anymore, without [an optional add-on](http://en.wikipedia.org/wiki/Microsoft_Windows_Services_for_UNIX).

---

### Post by dwhitney67 on 2009-05-03
> **wmcbrine said:**
> [After a fashion...](http://en.wikipedia.org/wiki/Microsoft_POSIX_subsystem) as a dodge... and not anymore, without [an optional add-on](http://en.wikipedia.org/wiki/Microsoft_Windows_Services_for_UNIX).

Yep, you were quite right to correct me.  A few years ago a company, whose s/w product I was evaluating, was using Windows 2000 as their POSIX-compliant system for JTRS waveform development.  At the time, I also believed Windows to be non-POSIX compliant, but with a little research, I found out otherwise.

I guess today M$ has not committed themselves to providing their new releases with the POSIX features, unless a special package is installed (at possibly extra cost).  Yet another reason to detest M$ and its use in the s/w industry.  Too bad I'm in the minority.

---

### Post by smyrman on 2010-02-10
If you can use "-std=gnu99" instead of "-std=c99", at leas usleep() works (nonosleep() not tested by me). gnu99 is almost the same as c99.

- Sindre

---

### Post by akvino on 2010-02-10
> **dwhitney67 said:**
> I found, from experimenting and reviewing the /usr/include/features.h file, that this will work for nanosleep().
```

/usr/bin/gcc -std=c99 -D_POSIX_C_SOURCE=199309L nanosleeptest.c

```
P.S.  The -std=c99 is optional.

What does this do:

-D_POSIX_C_SOURCE=199309L

---

### Post by dwhitney67 on 2010-02-10
> **akvino said:**
> What does this do:

-D_POSIX_C_SOURCE=199309L

It defines a pre-processor macro, and assigns it the value 199309L.  The 'L' denotes long value.

View the comments within /usr/include/features.h for more information.

Btw, this is an old thread; who conjured it back to life?

---

