---
title: "ANSI C for computer science students"
date: 2008-10-11
forum: Programming Talk
---

### Post by druca on 2008-10-11
Hello to all,

I am a beginning computer sci student, I usually develop on the red hat server at school, but circumstance lets me not do that at the moment. So I was curious if, besides downloading lib6c-dev cause none of my stupid header files are working, what could i do so that i could develop on my laptop? We are using ANSI C, is there a specific development package for that?

thanks,
druca

---

### Post by geirha on 2008-10-11
Install [build-essential](apt://build-essential). Then compile using the -ansi and -pedantic options to force strict ansi ```
gcc -ansi -pedantic -o hello hello.c
```

---

### Post by LaRoza on 2008-10-11
The sticky on tools will give you guides as well.

---

### Post by Canis familiaris on 2008-10-11
Isn't the -pedantic enough?

---

### Post by druca on 2008-10-11
Ok thank you everyone for all of your help, but I am still getting some errors and they all have to do with my header files:

gcc -ansi -pedantic -lm log.c
In file included from /usr/include/stdio.h:75,
                 from log.c:10:
/usr/include/libio.h:332: error: expected specifier-qualifier-list before ‘size_t’
/usr/include/libio.h:364: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/libio.h:373: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/libio.h:493: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_IO_sgetn’
In file included from log.c:10:
/usr/include/stdio.h:312: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:678: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fread’
/usr/include/stdio.h:684: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fwrite’
In file included from log.c:11:
/usr/include/stdlib.h:140: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__ctype_get_mb_cur_max’
/usr/include/stdlib.h:471: error: expected ‘)’ before ‘__size’
/usr/include/stdlib.h:473: error: expected ‘)’ before ‘__nmemb’
/usr/include/stdlib.h:485: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:681: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:681: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:682: error: nonnull argument with out-of-range operand number (argument 1, operand 5)
/usr/include/stdlib.h:686: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:686: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:687: error: nonnull argument with out-of-range operand number (argument 1, operand 4)
/usr/include/stdlib.h:779: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:783: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:790: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mbstowcs’
/usr/include/stdlib.h:793: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘wcstombs’


any ideas I havent read the sticky on tools yet couldnt find it but im looking 

thanks

---

### Post by druca on 2008-10-11
Disregard the last post please,

I got it to work thank you all so much!! 

they kept booting me off the server cause i did a bunch of infinite loops :) lol 

thank you i did install the the essentials and read the sticky appreciate it!

thank you,
drew

---

