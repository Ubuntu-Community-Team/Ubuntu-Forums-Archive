---
title: "Coreutils source questions"
date: 2011-02-06
forum: Programming Talk
---

### Post by Odexios on 2011-02-06
Hello everybody!

I decided it would be a good idea to look at the source of some coreutils application in order to learn something about actual implementation of C programs.

I decided to start with the simple ones, so echo's the first one I'm looking at. The source seems pretty straightforward, but I have some doubts I wasn't able to clarify.

First, I found repeatedly used the token (right word to use?) program_name. I thought it was from an included header, but I couldn't find it in system.h, which is the only non-system header included, so... where is it declared?

Second, I frequently found this token, _("somekindofstring"); I suppose it's a macro, can anyone tell me where can I find it?

Third, and last. While I was looking at system.h I saw this:

[php]
#if 2 <= __GLIBC__ && 2 <= __GLIBC_MINOR__
# if ! defined _SYS_TYPES_H
you must include <sys/types.h> before including this file
# endif
#endif[/php]Besides from the completely not understandable first if's condition (I suppose I'll have to find __GLBC__ and __GLIBC_MINOR__ ), what's the ```
 you must include <sys/types.h> before including this file 
``` part? Why isn't it within quotation marks, or whatever?

Thank you everyone for your attention and sorry for the possibly dumb questions! I can write here echo.c 's source if you need, but it's kind of long for a post.

---

### Post by MadCow108 on 2011-02-06
1) PROGRAM_NAME is just a macro to define the name of the program once globally
e.g. src/du.c:49 "du" for the disk usage tool

2) _ is a macro for gettext which translates strings to the native os language
definition e.g. argmatch.c:33:
#define _(msgid) gettext (msgid)

3) __GLIBC__ && 2 <= __GLIBC_MINOR__ are macros containing the version of glibc used for compilation. they are definied somewhere in the glibc headers

the text in that message is not legal C and will thus force the compiler to emit an error.
you should use #error for that actually but probably this method is more portable to compilers not supporting #error

to find this stuff the program cscope is extremely useful. grep is also ok for simpler tasks.

---

### Post by Odexios on 2011-02-06
> **MadCow108 said:**
> 1) PROGRAM_NAME is just a macro to define the name of the program once globally
e.g. src/du.c:49 "du" for the disk usage toolYeah, I saw PROGRAM_NAME. The issue is that in echo.c I can also find program_name, lowercased.

> 2) _ is a macro for gettext which translates strings to the native os language
definition e.g. argmatch.c:33:
#define _(msgid) gettext (msgid)

3) __GLIBC__ && 2 <= __GLIBC_MINOR__ are macros containing the version of glibc used for compilation. they are definied somewhere in the glibc headers

the text in that message is not legal C and will thus force the compiler to emit an error.
you should use #error for that actually but probably this method is more portable to compilers not supporting #error

to find this stuff the program cscope is extremely useful. grep is also ok for simpler tasks.Thanks for the answers. I'll look into cscope.

---

### Post by MadCow108 on 2011-02-06
the lower case program_name is defined in lib/progname.c and set with set_program_name by each program.

---

### Post by gmargo on 2011-02-06
> **Odexios said:**
> 
First, I found repeatedly used the token (right word to use?) program_name. I thought it was from an included header, but I couldn't find it in system.h, which is the only non-system header included, so... where is it declared?

src/system.h includes "progname.h" which is in the lib/ directory (along with progname.c, which holds the instantiation of program_name.)

---

### Post by worksofcraft on 2011-02-06
Instead of just building in a fixed string the way they do it is so that you can rename your program and it still gets it right:
```

$ cp /bin/echo e.out
$ ./e.out --help
Usage: ./e.out [SHORT-OPTION]... [STRING]...

```

see all those macros are almost as clever as using argv[0] :popcorn:

---

### Post by MadCow108 on 2011-02-06
> **worksofcraft said:**
> Instead of just building in a fixed string the way they do it is so that you can rename your program and it still gets it right:
```

$ cp /bin/echo e.out
$ ./e.out --help
Usage: ./e.out [SHORT-OPTION]... [STRING]...

```

see all those macros are almost as clever as using argv[0] :popcorn:

actually set_program_name is always called with argv[0]
the PROGRAM_NAME macro is only used for --version

all the logic is required to remove some libtool craziness and debugging.

---

