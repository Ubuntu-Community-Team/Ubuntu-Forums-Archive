---
title: "No symbols in libpcre."
date: 2007-05-16
forum: Programming Talk
---

### Post by ichijoji on 2007-05-16
Hi all,

I'm trying to compile a third party library (CEGUI) that requires the pcre library but when I try to run I get:

CEGUI Exception occured: DynamicModule::DynamicModule - Failed to load module 'libCEGUIXercesParser.so': /usr/local/lib/libCEGUIXercesParser.so: undefined symbol: pcre_free

The pcre library is installed to /usr/lib/libpcre.so and I linked with -L/usr/lib and -lpcre with no errors, but when I check the symbols in the output file I get:

         U pcre_compile
         U pcre_exec
         U pcre_free

Upon further inspection, nm /usr/lib/pcre.so yields no symbols. I tried reinstalling the library with the same results. I'm fairly new to ubuntu and I may be missing something obvious, but I can't see it. Does anyone know how I can get this to work?

---

### Post by WW on 2007-05-16
I don't know what is going on with the CEGUI program, but if you want to verify that the pcre library is OK, you can compile and run this test program:

**pcretest.c**
```

/*
 *  pcretest.c
 */

#include <stdio.h>
#include <pcre.h>
#include <string.h>

int main(int argc, char **argv)
    {
    pcre *p;
    const char *errmsg;
    int  errpos;
    int rc;
    int ovector[60];
    char buf[300];
    int flags = 0;

    if (argc != 3)
        {
        printf("use: pcretest regex string\n");
        printf("For example,\n");
        printf("     pcretest \"(\\d\\d\\d)-(\\d\\d)-(\\d\\d\\d\\d)\" \"123-45-6789\"\n");
        exit(-1);
        }

    p = pcre_compile(argv[1],flags,&errmsg,&errpos,NULL);

    if (p != NULL)
        {
        rc = pcre_exec(p,NULL,argv[2],strlen(argv[2]),0,0,ovector,50);
        printf("%d\n",rc);
        int i;
        for (i = 0; i < rc; ++i)
            {
            printf("[%d,%d]\n",ovector[2*i],ovector[2*i+1]);
            int k;
            for (k = ovector[2*i]; k < ovector[2*i+1]; ++k)
                {
                buf[k-ovector[2*i]] = argv[2][k];
                }
            buf[ovector[2*i+1]-ovector[2*i]] = 0;
            printf("%s\n",buf);
            }
        pcre_free(p);
        }
    }

```
To compile and run:
```

$ gcc -o pcretest pcretest.c -lpcre
$ ./pcretest  "(\d\d\d)-(\d\d)-(\d\d\d\d)" "123-45-6789"
4
[0,11]
123-45-6789
[0,3]
123
[4,6]
45
[7,11]
6789
$

```

For what it's worth, I also get the "no symbols" message when I run **nm /usr/lib/libpcre.so**.

A few more details, for comparison: I am running dapper, and I have the packages **libpcre3**, **libpcre3-dev**, and **libpcrecpp0** installed.  You will need the -dev package to compile the program.

---

