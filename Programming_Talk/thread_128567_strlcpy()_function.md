---
title: "strlcpy() function"
date: 2006-02-11
forum: Programming Talk
---

### Post by kch_86 on 2006-02-11
I am trying to compile a program with g++ that uses strlcpy(), but I keep getting:

   "strlcpy() not declared in this scope"

When I try to compile this on my windows computer under cygwin, or when I ssh into one of my school's servers it compiles fine too. I have gcc/++ 4.0 along w/ the libstdc++5/6 and libstdc++6-4.0dev. What do I need?

---

### Post by hod139 on 2006-02-12
As far as I knew, strl* function were BSD only string functions and not part of any standard. I'm surprised that it worked under cygwin. If you need portability, you shouldn't use this function yet (hopefully it will be included into the standard someday). You can however define the function yourself based on openBSD's implementation
[http://www.openbsd.org/cgi-bin/cvsweb/src/lib/libc/string/]("http://www.openbsd.org/cgi-bin/cvsweb/src/lib/libc/string/")

For strlcat:
```

/* strlcat based on OpenBSDs strlcat */
#include <sys/types.h>

size_t  strlcat(char *, const char *, size_t);

/*
 * Appends src to string dst of size siz (unlike strncat, siz is the
 * full size of dst, not space left).  At most siz-1 characters
 * will be copied.  Always NUL terminates (unless siz <= strlen(dst)).
 * Returns strlen(src) + MIN(siz, strlen(initial dst)).
 * If retval >= siz, truncation occurred.
 */
size_t
strlcat(char *dst, const char *src, size_t siz)
{
        char *d = dst;
        const char *s = src;
        size_t n = siz;
        size_t dlen;

        /* Find the end of dst and adjust bytes left but don't go past end */
        while (n-- != 0 && *d != '\0')
                d++;
        dlen = d - dst;
        n = siz - dlen;

        if (n == 0)
                return(dlen + strlen(s));
        while (*s != '\0') {
                if (n != 1) {
                        *d++ = *s;
                        n--;
                }
                s++;
        }
        *d = '\0';

        return(dlen + (s - src));        /* count does not include NUL */
}

``` 

and for strlcpy:

```

/* strlcpy based on OpenBSDs strlcpy */
#include <stdio.h>
#include <sys/types.h>

size_t strlcpy(char *, const char *, size_t);

/*
 * Copy src to string dst of size siz.  At most siz-1 characters
 * will be copied.  Always NUL terminates (unless siz == 0).
 * Returns strlen(src); if retval >= siz, truncation occurred.
 */
size_t
strlcpy(char *dst, const char *src, size_t siz)
{
        char *d = dst;
        const char *s = src;
        size_t n = siz;

        /* Copy as many bytes as will fit */
        if (n != 0 && --n != 0) {
                do {
                        if ((*d++ = *s++) == 0)
                                break;
                } while (--n != 0);
        }

        /* Not enough room in dst, add NUL and traverse rest of src */
        if (n == 0) {
                if (siz != 0)
                        *d = '\0';                /* NUL-terminate dst */
                while (*s++)
                        ;
        }

        return(s - src - 1);        /* count does not include NUL */
}

``` 
Hope this helps

---

### Post by kch_86 on 2006-02-12
Hey thanks alot. This helps a lot. The server that I was logged into was a Solaris machine, so I guess it's included there too.

---

