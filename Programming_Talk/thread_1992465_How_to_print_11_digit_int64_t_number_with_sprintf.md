---
title: "How to print 11 digit int64_t number with sprintf ?"
date: 2012-05-31
forum: Programming Talk
---

### Post by etdsbastar on 2012-05-31
Hello there,

I want to print a 10 or 11 digit number say 99999999999 with sprintf. For this, I used this code:

```
gchar*
convert_value (const gchar *value, gchar type)
{
    gchar buff[strlen(value)];
    gchar *fstr = malloc (sizeof buff);
    int64_t dvalue; double fvalue;               <== CHECK HERE
    
    switch (type)
    {
        case 'd':
            dvalue = strtol (value, NULL, 0);
            sprintf (buff, "%lld", dvalue);              <== AND HERE
            break;
        case 'f':
            fvalue = strtof (value, NULL);
            sprintf (buff, "%.2lf", fvalue);
            break;
        default:
            strcpy (buff, value);
    }
    
    strcpy (fstr, buff);
    
    return fstr;
}
```Usage:

```
convert_value ("99999999999", 'd')
```But, the output is showing me some other 10 digit numbers probably starting from 2**********.
Please help.
NB: Format specifier "I64d" is also not working.

---

### Post by Bachstelze on 2012-05-31
Buffer overflows.

```
firas@av104151 ~ % cat foo.c | nl -b a                                 
     1	#include <stdio.h>
     2	#include <stdlib.h>
     3	#include <string.h>
     4	
     5	char*
     6	convert_value (const char *value, char type)
     7	{
     8	    char buff[strlen(value)];
     9	    char *fstr = malloc (sizeof buff);
    10	    int64_t dvalue; double fvalue;
    11	    
    12	    switch (type)
    13	    {
    14	        case 'd':
    15	            dvalue = strtol (value, NULL, 0);
    16	            sprintf (buff, "%lld", dvalue);
    17	            break;
    18	        case 'f':
    19	            fvalue = strtof (value, NULL);
    20	            sprintf (buff, "%.2lf", fvalue);
    21	            break;
    22	        default:
    23	            strcpy (buff, value);
    24	    }
    25	    
    26	    strcpy (fstr, buff);
    27	    
    28	    return fstr;
    29	}
    30	
    31	int main(void)
    32	{
    33	    char *s = convert_value("99999999999", 'd');
    34	    printf("%s\n", s);
    35	    free(s);
    36	}
firas@av104151 ~ % gcc -std=c99 -pedantic -Wall -Wextra -g -o foo foo.c
firas@av104151 ~ % valgrind ./foo                                      
==13208== Memcheck, a memory error detector
==13208== Copyright (C) 2002-2011, and GNU GPL'd, by Julian Seward et al.
==13208== Using Valgrind-3.7.0 and LibVEX; rerun with -h for copyright info
==13208== Command: ./foo
==13208== 
==13208== Invalid write of size 4
==13208==    at 0x7FFFFFE007C5: ???
==13208==    by 0x100000DFC: __inline_strcpy_chk (_string.h:91)
==13208==    by 0x100000DB9: convert_value (foo.c:26)
==13208==    by 0x100000E17: main (foo.c:33)
==13208==  Address 0x1002770e8 is 8 bytes inside a block of size 11 alloc'd
==13208==    at 0x100010679: malloc (vg_replace_malloc.c:266)
==13208==    by 0x100000CBD: convert_value (foo.c:9)
==13208==    by 0x100000E17: main (foo.c:33)
==13208== 
==13208== Invalid read of size 1
==13208==    at 0x100010B03: strlen (mc_replace_strmem.c:398)
==13208==    by 0x1000A3EF4: puts (in /usr/lib/libSystem.B.dylib)
==13208==    by 0x100000E24: main (foo.c:34)
==13208==  Address 0x1002770eb is 0 bytes after a block of size 11 alloc'd
==13208==    at 0x100010679: malloc (vg_replace_malloc.c:266)
==13208==    by 0x100000CBD: convert_value (foo.c:9)
==13208==    by 0x100000E17: main (foo.c:33)
==13208== 
99999999999
==13208== 
==13208== HEAP SUMMARY:
==13208==     in use at exit: 4,184 bytes in 2 blocks
==13208==   total heap usage: 3 allocs, 1 frees, 4,195 bytes allocated
==13208== 
==13208== LEAK SUMMARY:
==13208==    definitely lost: 0 bytes in 0 blocks
==13208==    indirectly lost: 0 bytes in 0 blocks
==13208==      possibly lost: 0 bytes in 0 blocks
==13208==    still reachable: 4,096 bytes in 1 blocks
==13208==         suppressed: 88 bytes in 1 blocks
==13208== Rerun with --leak-check=full to see details of leaked memory
==13208== 
==13208== For counts of detected and suppressed errors, rerun with: -v
==13208== ERROR SUMMARY: 2 errors from 2 contexts (suppressed: 0 from 0)

```

---

### Post by etdsbastar on 2012-05-31
Here is the corrected code, actually I got it to work:

```
gchar *
convert_value (const gchar *value, gchar type)
{
    gchar buff[256] = {0};
    int64_t dvalue; double fvalue; 
    gchar *final_value;
    final_value = malloc (sizeof buff);
    
    switch (type)
    {
        case 'd':
            dvalue = strtoll (value, NULL, 0);
            sprintf (buff, "%"PRId64"", dvalue);
            break;
        case 'f':
            fvalue = strtof (value, NULL);
            sprintf (buff, "%.2lf", fvalue);
            break;
        default:
            sprintf (final_value, "%s", value);
    }
    
    sprintf (final_value, "%s", buff);
    
    return final_value;
}
```

Actually, I was using strtol instead of strtoll. Thanks everybody.

---

