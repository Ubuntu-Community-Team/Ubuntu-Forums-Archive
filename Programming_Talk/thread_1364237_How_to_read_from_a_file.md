---
title: "How to read from a file?"
date: 2009-12-25
forum: Programming Talk
---

### Post by tom66 on 2009-12-25
```

/**
 * Tries to convert an SWF to an XML file which can be parsed
 * later by another (read: simple, Python) program. The list is 
 * quite simple; sets of shapes to be drawn in each frame 
 * and (possibly) ActionScript code output. 
 *
 * Planned features:
 *  - Images embedded as hexadecimal or Base64.
 *  - Videos, including streaming videos. This might require a bit of 
 *    hacking to get it working.
 *  - Text.
 *  - ActionScript version 1.0 through 3.0.
 *
 * GPLv2, Copyright (C) 2009 Thomas Oldbury <thomas@tgohome.com>.
 */

#include "../config.h"

#if 0
# ifdef HAVE_SYS_STAT_H
#  include <sys/stat.h>
# else
#  undef HAVE_STAT
# endif
# 
# ifdef HAVE_SYS_TYPES_H
#  include <sys/types.h>
# else
#  undef HAVE_STAT
# endif
#endif

#include <stdbool.h>
#include <stdlib.h>
#include <stdarg.h>
#include <stdio.h>
//#include "../lib/rfxswf.h"
//#include "../lib/args.h"

FILE *swf_file, *xml_file;

void error_assert(bool cond, char *msg)
{
    if(cond) 
        return;
    fprintf(stderr, "ERROR: %s\n", msg);
    perror("Possible error message (if a file-related error)");
    exit(1);
}

// Allocate @size@ bytes of memory, clear it, or exit on error.
void *my_calloc(int size)
{
    void *ptr = calloc(1, size);
    error_assert(ptr != NULL, "Error allocating/clearing memory.");
    return ptr;
}

// Free some memory, and set the pointer to NULL.
#define my_free(x) \
    free(x); \
    x = NULL; 

int main(int argc, char *argv[])
{
    char *header = my_calloc(4);
    bool is_flash;
    
    error_assert(argc == 3, "Must provide an input file and an output file.");
    
    swf_file = fopen(argv[1], "rb");
    xml_file = fopen(argv[2], "wb");
    
    error_assert(swf_file != NULL, "Error opening input file.");
    error_assert(xml_file != NULL, "Error opening output file.");
    
    // Verify if it is an SWF file.
    fread(header, 1, 4, swf_file);
    is_flash = (header[0] == 'F' && header[1] == 'W' && header[2] == 'S') ||
               (header[0] == 'C' && header[1] == 'W' && header[2] == 'S');
    printf("Header: <-- \"%s\" -->\n", header);
    error_assert(is_flash, "Input file doesn't appear to be a SWF file.");
    
    // Clean up. 
    fclose(swf_file);
    fclose(xml_file);
    my_free(header);
    exit(0);
} 

```

Work in development... 

Compile with GCC and send the following program two temporary/empty files, or if you want to be "flash" (heh), send it a SWF and an empty file which can be written. At the moment it shouldn't matter.

But fread() doesn't write anything into the buffer! And then the program exits, because the assertion fails. 

I have properly allocated the array, because I can strcpy into that with ease, and the data shows up...

Any help would be appreciated, I'm learning here, I only just grasped the pointers in C. :)

---

### Post by lloyd_b on 2009-12-25
I tested it here, using some dummy files I made up, and it seems to be working...

May I suggest you test the return value from fread() to see how many bytes (if any) you read from the file?```
if (fread(header, 1, 4, swf_file) < 4)
    printf("Error - couldn't read 4 bytes from the input file!\n");
```(or an equivalent assert for the printf).

One question I have - why are you dynamically allocating 'header'?  If you know at compile time that it's going to be 4 bytes, then it's simpler and more reliable to just make it "char header[4]" rather than messing with calloc().

Lloyd B.

---

### Post by MaxIBoy on 2009-12-25
I **strongly** suggest using another language besides C for that task. A mix of Shell and Python is probably better. Doing lots of string processing is a major weak point of the C language.

Lloyd_b is right about fread though.

---

### Post by Hellkeepa on 2009-12-25
HELLo!

I'd go with Perl, but yeah: C isn't exactly the best language for massive string manipulation, a scripting language like Perl, PHP, Python, Bash or similar is much better equipped for it. Use the one you are the most comfortable with.
For distribution, Perl and Bash are the two safe bets.

Happy codin'!

---

### Post by ghostdog74 on 2009-12-25
> **MaxIBoy said:**
> I **strongly**A mix of Shell and Python is probably better. 
its actually not better. if you are talking about using the shell to execute a Python script, then that's alright.

---

### Post by tom66 on 2009-12-25
I am using C because there are already bindings in C to read SWF files. Trust me, I tried Python, I love Python, but it has no libraries (as far as I am aware) for SWF reading.

---

### Post by dwhitney67 on 2009-12-25
> **tom66 said:**
> I am using C because there are already bindings in C to read SWF files. Trust me, I tried Python, I love Python, but it has no libraries (as far as I am aware) for SWF reading.

Could you please recite what error or anomaly you are experiencing with your application?

As lloyd_b indicated, and as I have verified, your application is doing exactly what you programmed it to do.

Is there some functionality missing?  The following statement is not true; fread() does work.
> 
But fread() doesn't write anything into the buffer!


---

### Post by ghostdog74 on 2009-12-25
> **tom66 said:**
> I am using C because there are already bindings in C to read SWF files. Trust me, I tried Python, I love Python, but it has no libraries (as far as I am aware) for SWF reading.

how about [this?]("http://www.libming.org/")

---

### Post by MaxIBoy on 2009-12-26
If suitable bindings don't exist for Python, write some and then do the bulk of your coding in Python. Probably less work that way.

But it looks like, from Ghostdog's link, such bindings do exist. Does that library not suit your purposes?

---

### Post by nvteighen on 2009-12-26
@OP:

I strongly advice you to avoid constant sizes in fread() and well... any function that needs to know type sizes. Use the **sizeof()** compile-time operator, which gives you the exact length of any variable **at compile-time** (so, dynamically allocated variables will return the size of a pointer).

sizeof() will save you from assuming the wrong size of a type in a certain architecture.

Of course, the error comes from dynamically allocating a variable you could allocate statically without any issue, as lloyd_b pointed out. But, as you're allocating dynamically, you can't use sizeof() to get the size... although you already know the size...

In one word: if you know the size, use the stack!

---

