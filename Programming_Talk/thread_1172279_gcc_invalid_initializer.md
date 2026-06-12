---
title: "gcc: invalid initializer"
date: 2009-05-28
forum: Programming Talk
---

### Post by Pidgin on 2009-05-28
```
#include <stdio.h>

const fpos_t pos = 1000;

int main()
{
	return 0;
}

```
The above code generates the following error when compiled with "gcc -Wall -o a a.c".
```
a.c:3: error: invalid initializer
```
What's wrong?
Thank you!

---

### Post by Zugzwang on 2009-05-28
"fpos_t" is a "struct" and not just a number, so you cannot simply assign such a variable a number.

---

### Post by Pidgin on 2009-05-28
> **Zugzwang said:**
> "fpos_t" is a "struct" and not just a number, so you cannot simply assign such a variable a number.

Well, could you please make more explanations? I could not find the definition of fpos_t in gcc. However the same code works with Microsoft Visual Studio 2008.

---

### Post by Zugzwang on 2009-05-28
> **Pidgin said:**
> Well, could you please make more explanations? I could not find the definition of fpos_t in gcc. However the same code works with Microsoft Visual Studio 2008.

```

me@here:/usr/include$ cd /usr/include
me@here:/usr/include$ grep -Hirn "fpos_t" *
_G_config.h:26:} _G_fpos_t;
boost/compatibility/cpp_c_headers/cstdio:12:  using ::fpos_t;
boost/iostreams/positioning.hpp:27:namespace std { using ::fpos_t; }
boost/iostreams/positioning.hpp:54:inline stream_offset fpos_t_to_offset(std::fpos_t pos)
boost/iostreams/positioning.hpp:70:    return fpos_t_to_offset(pos.seekpos()) +
boost/iostreams/positioning.hpp:81:    // use implementation-specific member function get_fpos_t().
boost/iostreams/positioning.hpp:82:    return fpos_t_to_offset(pos.get_fpos_t()) +
boost/iostreams/positioning.hpp:84:           stream_offset(std::streamoff(pos.get_fpos_t()));
c++/4.3.3/cstdio:101:  using ::fpos_t;
c++/4.3/cstdio:101:  using ::fpos_t;
libio.h:34:#define _IO_pos_t _G_fpos_t /* obsolete */
libio.h:35:#define _IO_fpos_t _G_fpos_t
grep: warning: lua50/lua: recursive directory loop

python2.6/pyconfig.h:882:/* The size of `fpos_t', as computed by sizeof. */
python2.6/pyconfig.h:883:#define SIZEOF_FPOS_T 16
stdio.h:91:typedef _G_fpos_t fpos_t;
stdio.h:93:typedef _G_fpos64_t fpos_t;
stdio.h:767:extern int fgetpos (FILE *__restrict __stream, fpos_t *__restrict __pos);
stdio.h:772:extern int fsetpos (FILE *__stream, __const fpos_t *__pos);
stdio.h:776:                             fpos_t *__restrict __pos), fgetpos64);
stdio.h:778:                   (FILE *__stream, __const fpos_t *__pos), fsetpos64);

```
So "fpos_t" is defined as being the same as "_G_fpos_t" (stdio.h:91), which in turn is defined in "_G_config.h", which contains:
```

typedef struct
{
  __off_t __pos;
  __mbstate_t __state;
} _G_fpos_t;

```

---

### Post by nvteighen on 2009-05-28
In other words, have you read the API documentation for whatever library (boost?) you're using? There's where you'll find what each type is expected to do and behaive!

---

### Post by hod139 on 2009-05-28
You are not suppose to touch the internals of fpos_t objects.  Doing so instantly makes your code non-portable.  You are suppose to use the functions fgetpos and fsetpos, passing a reference of the fpos_t object.

---

### Post by soltanis on 2009-05-28
> **hod139 said:**
> Doing so instantly makes your code non-portable.

So instantly, in fact, that even a passing glance could render your entire project doomed to be bound to the platform you wrote it on (cue horror music)!!!

---

### Post by Pidgin on 2009-05-28
> **nvteighen said:**
> In other words, have you read the API documentation for whatever library (boost?) you're using? There's where you'll find what each type is expected to do and behaive!

Yes, I have. I have read the documentation of glibc. But it does not explain how the structure fpos_t works.

---

### Post by Pidgin on 2009-05-28
> **hod139 said:**
> You are not suppose to touch the internals of fpos_t objects.  Doing so instantly makes your code non-portable.  You are suppose to use the functions fgetpos and fsetpos, passing a reference of the fpos_t object.

Could you please give an example on how to use fsetpos to reach a specific location without touching fpos_t objects?

---

### Post by nvteighen on 2009-05-29
> **Pidgin said:**
> Yes, I have. I have read the documentation of glibc. But it does not explain how the structure fpos_t works.

You don't need any initializer... fsetpos() is all you need; it will "save" the (FILE *)'s current position and then you'll be able to reuse it with fgetpos().

```

#include <stdio.h>

int main(void)
{
    fpos_t pos; /* Not a pointer! */
    FILE *myfile = fopen("a", "r");

    /* ... */

    fsetpos(myfile, &pos); /* You should check if fsetpos returns -1 (error). */

    /* ... */

    fgetpos(myfile, &pos); /* Not sure why it asks for a (fpos_t *). */

    fclose(myfile);

    return 0;
}

```

---

### Post by Pidgin on 2009-05-29
> **nvteighen said:**
> You don't need any initializer... fsetpos() is all you need; it will "save" the (FILE *)'s current position and then you'll be able to reuse it with fgetpos().

```

#include <stdio.h>

int main(void)
{
    fpos_t pos; /* Not a pointer! */
    FILE *myfile = fopen("a", "r");

    /* ... */

    fsetpos(myfile, &pos); /* You should check if fsetpos returns -1 (error). */

    /* ... */

    fgetpos(myfile, &pos); /* Not sure why it asks for a (fpos_t *). */

    fclose(myfile);

    return 0;
}

```

I am sorry but I cannot understand your code.
You pass the address of an object of the type fpos_t to fsetpos before initializing the object. Where do you think fsetpos would take you?
Additionally, I really want to seek to a specific offset within a file. Should I use fseek instead?
Thank you!

---

### Post by Zugzwang on 2009-05-29
> **Pidgin said:**
> I am sorry but I cannot understand your code.
You pass the address of an object of the type fpos_t to fsetpos before initializing the object. Where do you think fsetpos would take you?


nvteighen mixed up fgetpos and fsetpos. Just swap them and the code should be fine.

> **Pidgin said:**
> 
Additionally, I really want to seek to a specific offset within a file. Should I use fseek instead?


As it is now obvious that "fpos_t" objects are really just for getting back to a position you've already been at in the file, the answer should now be obvious as well: yes!

---

### Post by Pidgin on 2009-05-29
> **Zugzwang said:**
> nvteighen mixed up fgetpos and fsetpos. Just swap them and the code should be fine.



As it is now obvious that "fpos_t" objects are really just for getting back to a position you've already been at in the file, the answer should now be obvious as well: yes!

Oh, I see. Thank you!

---

### Post by nvteighen on 2009-05-29
> **Zugzwang said:**
> nvteighen mixed up fgetpos and fsetpos. Just swap them and the code should be fine.

Thanks. I thought fsetpos() and fgetpos() were "methods" of fpos_t, but now I see they are "methods" of FILE *. That's why I got it inverted. Sorry for the confusion! :)

---

### Post by Pidgin on 2009-05-29
> **nvteighen said:**
> Thanks. I thought fsetpos() and fgetpos() were "methods" of fpos_t, but now I see they are "methods" of FILE *. That's why I got it inverted. Sorry for the confusion! :)

Never mind.

---

