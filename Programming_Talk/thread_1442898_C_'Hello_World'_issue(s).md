---
title: "C 'Hello World' issue(s)"
date: 2010-03-30
forum: Programming Talk
---

### Post by Barriehie on 2010-03-30
Hello all,
Well either I'm missing something or my system is, based on the -voluminous- errors I'm getting.  I tried compiling this:
```

#include <stdio.h>

int main()
{
  printf("Hello World!\n");
  return 0;
}
```

with this command line:
```

gcc hello.c -o hello
```

and got this:
```

In file included from /usr/include/stdio.h:28,
                 from hello.c:1:
/usr/include/features.h:346:25: error: sys/cdefs.h: No such file or directory
In file included from /usr/include/stdio.h:34,
                 from hello.c:1:
/usr/lib/gcc/x86_64-linux-gnu/4.3.2/include/stddef.h:214: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘typedef’
In file included from hello.c:1:
/usr/include/stdio.h:49: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘typedef’
/usr/include/stdio.h:54: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__USING_NAMESPACE_STD’
In file included from /usr/include/stdio.h:75,
                 from hello.c:1:
/usr/include/libio.h:332: error: expected specifier-qualifier-list before ‘size_t’
/usr/include/libio.h:364: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/libio.h:373: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/libio.h: In function ‘_IO_feof’:
/usr/include/libio.h:460: error: expected declaration specifiers before ‘__THROW’
/usr/include/libio.h:461: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/libio.h:463: error: storage class specified for parameter ‘_IO_peekc_locked’
/usr/include/libio.h:469: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/libio.h:470: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/libio.h:471: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/libio.h:489: error: storage class specified for parameter ‘_IO_vfscanf’
/usr/include/libio.h:491: error: storage class specified for parameter ‘_IO_vfprintf’
/usr/include/libio.h:492: error: storage class specified for parameter ‘_IO_padn’
/usr/include/libio.h:493: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_IO_sgetn’
/usr/include/libio.h:495: error: storage class specified for parameter ‘_IO_seekoff’
/usr/include/libio.h:496: error: storage class specified for parameter ‘_IO_seekpos’
/usr/include/libio.h:498: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
In file included from hello.c:1:
/usr/include/stdio.h:89: error: expected declaration specifiers before ‘__BEGIN_NAMESPACE_STD’
/usr/include/stdio.h:95: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
In file included from hello.c:1:
/usr/include/stdio.h:146: error: storage class specified for parameter ‘stdout’
/usr/include/stdio.h:147: error: storage class specified for parameter ‘stderr’
/usr/include/stdio.h:153: error: expected declaration specifiers before ‘__BEGIN_NAMESPACE_STD’
/usr/include/stdio.h:157: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/stdio.h:158: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
/usr/include/stdio.h:166: error: expected declaration specifiers before ‘__BEGIN_NAMESPACE_STD’
/usr/include/stdio.h:186: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/stdio.h:187: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
/usr/include/stdio.h:205: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/stdio.h:209: error: expected declaration specifiers before ‘__BEGIN_NAMESPACE_STD’
/usr/include/stdio.h:219: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:220: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
/usr/include/stdio.h:243: error: expected declaration specifiers before ‘__BEGIN_NAMESPACE_STD’
/usr/include/stdio.h:255: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/stdio.h:272: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
/usr/include/stdio.h:296: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/stdio.h:302: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/stdio.h:306: error: expected declaration specifiers before ‘__BEGIN_NAMESPACE_STD’
/usr/include/stdio.h:313: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:315: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
/usr/include/stdio.h:324: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:328: error: expected declaration specifiers before ‘__BEGIN_NAMESPACE_STD’
/usr/include/stdio.h:339: error: storage class specified for parameter ‘printf’
/usr/include/stdio.h:342: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/stdio.h:348: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:354: error: storage class specified for parameter ‘vprintf’
/usr/include/stdio.h:357: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/stdio.h:358: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
/usr/include/stdio.h:367: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:369: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/stdio.h:370: error: expected declaration specifiers before ‘__END_NAMESPACE_C99’
/usr/include/stdio.h:398: error: storage class specified for parameter ‘dprintf’
/usr/include/stdio.h:402: error: expected declaration specifiers before ‘__BEGIN_NAMESPACE_STD’
/usr/include/stdio.h:413: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wur’
/usr/include/stdio.h:416: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/stdio.h:434: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:436: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wur’
/usr/include/stdio.h:438: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/stdio.h:445: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
/usr/include/stdio.h:462: error: storage class specified for parameter ‘vscanf’
/usr/include/stdio.h:462: error: expected ‘,’ or ‘;’ before ‘__wur’
/usr/include/stdio.h:467: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/stdio.h:490: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:494: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wur’
/usr/include/stdio.h:497: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/stdio.h:504: error: expected declaration specifiers before ‘__END_NAMESPACE_C99’
/usr/include/stdio.h:514: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:520: error: storage class specified for parameter ‘getchar’
/usr/include/stdio.h:521: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
/usr/include/stdio.h:533: error: storage class specified for parameter ‘getchar_unlocked’
/usr/include/stdio.h:543: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:547: error: expected declaration specifiers before ‘__BEGIN_NAMESPACE_STD’
/usr/include/stdio.h:556: error: expected declaration specifiers or ‘...’ before ‘FILE’
/usr/include/stdio.h:556: error: storage class specified for parameter ‘putc’
/usr/include/stdio.h:562: error: storage class specified for parameter ‘putchar’
/usr/include/stdio.h:563: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
/usr/include/stdio.h:584: error: expected declaration specifiers or ‘...’ before ‘FILE’
/usr/include/stdio.h:584: error: storage class specified for parameter ‘putc_unlocked’
/usr/include/stdio.h:585: error: storage class specified for parameter ‘putchar_unlocked’
/usr/include/stdio.h:592: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:595: error: expected declaration specifiers or ‘...’ before ‘FILE’
/usr/include/stdio.h:595: error: storage class specified for parameter ‘putw’
/usr/include/stdio.h:599: error: expected declaration specifiers before ‘__BEGIN_NAMESPACE_STD’
/usr/include/stdio.h:612: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wur’
/usr/include/stdio.h:613: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
/usr/include/stdio.h:642: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:643: error: expected declaration specifiers or ‘...’ before ‘FILE’
/usr/include/stdio.h:643: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wur’
/usr/include/stdio.h:652: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:653: error: expected declaration specifiers or ‘...’ before ‘FILE’
/usr/include/stdio.h:653: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wur’
/usr/include/stdio.h:657: error: expected declaration specifiers before ‘__BEGIN_NAMESPACE_STD’
/usr/include/stdio.h:668: error: storage class specified for parameter ‘puts’
/usr/include/stdio.h:675: error: expected declaration specifiers or ‘...’ before ‘FILE’
/usr/include/stdio.h:675: error: storage class specified for parameter ‘ungetc’
/usr/include/stdio.h:682: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fread’
/usr/include/stdio.h:688: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fwrite’
/usr/include/stdio.h:690: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
/usr/include/stdio.h:712: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fwrite_unlocked’
/usr/include/stdio.h:717: error: expected declaration specifiers before ‘__BEGIN_NAMESPACE_STD’
/usr/include/stdio.h:727: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:732: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:733: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
/usr/include/stdio.h:751: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:765: error: expected declaration specifiers before ‘__BEGIN_NAMESPACE_STD’
/usr/include/stdio.h:776: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:788: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
/usr/include/stdio.h:801: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:803: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:804: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
/usr/include/stdio.h:809: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:810: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:814: error: expected declaration specifiers before ‘__BEGIN_NAMESPACE_STD’
/usr/include/stdio.h:820: error: expected declaration specifiers before ‘__END_NAMESPACE_STD’
In file included from /usr/include/stdio.h:826,
                 from hello.c:1:
/usr/include/bits/sys_errlist.h:28: error: storage class specified for parameter ‘sys_errlist’
In file included from hello.c:1:
/usr/include/stdio.h:831: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:836: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:846: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/stdio.h:852: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:858: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__THROW’
/usr/include/stdio.h:886: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:890: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:893: error: expected ‘)’ before ‘*’ token
/usr/include/stdio.h:916: error: expected declaration specifiers before ‘__END_DECLS’
hello.c:7: error: old-style parameter declarations in prototyped function definition
hello.c:7: error: expected ‘{’ at end of input
```

Anybody ever seen this massive a foul up b4?

TIA,

:confused:

---

### Post by MindSz on 2010-03-30
```
sudo apt-get install build-essential
```

You're probably missing this package.

---

### Post by azagaros on 2010-03-30
My suggestion re-install the gcc package.

---

### Post by Barriehie on 2010-03-30
> **MindSz said:**
> ```
sudo apt-get install build-essential
```

You're probably missing this package.

My bad for not including that info in the original post; it's installed.

---

### Post by Barriehie on 2010-03-30
> **azagaros said:**
> My suggestion re-install the gcc package.

I'll try that right now, thanks!

Edit: 10 min. later - same thing!

---

### Post by Compyx on 2010-03-30
Usually this kind of massive amount of error messages is caused by a missing semi-colon somewhere (usually after the prototype of a function in a header file). However, your code looks fine (except for the definition of 'main', that should be 'int main(void)').

The file that's missing according to the error message can be found in the package libc6-dev, perhaps (re)installing that one will fix things, although build-essential should have pulled that one in.

---

### Post by TheBuzzSaw on 2010-03-30
int main() == int main(void)

---

### Post by Compyx on 2010-03-30
> **TheBuzzSaw said:**
> int main() == int main(void)

Maybe in C++, but not in C. In C, 'int main()' declares main as a function *accepting an unspecified number of arguments* returning int, while 'int main(void)' declares main as a function *accepting no arguments* returning int. Although 'int main()' is not an error, it is -in my opinion- poor style.

---

### Post by Barriehie on 2010-03-30
> **Compyx said:**
> Maybe in C++, but not in C. In C, 'int main()' declares main as a function *accepting an unspecified number of arguments* returning int, while 'int main(void)' declares main as a function *accepting no arguments* returning int. Although 'int main()' is not an error, it is -in my opinion- poor style.

Alright well now that I've got the worlds longest to generate 'Hello World' program going I can work on the style. little steps...  Anyway, something to be said for installing packages NOT in the repos.  No more electricsheep for me!

Thanks Everyone! :)
Barrie

---

### Post by truls.pingen on 2011-01-20
I have the exact same problem, did you solve it?

---

### Post by ibuclaw on 2011-01-20
Arise thread long since dead! Haunt thy forums from which thou art created! :twisted:

On a serious note, please check the thread date before you post.


[CENTER][IMG]http://www.vfl-fanforum.de/board/wcf/images/smilies/thread_closed.gif[/IMG][/CENTER]

---

