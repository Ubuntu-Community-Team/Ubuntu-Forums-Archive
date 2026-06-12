---
title: "[C] Impossible Segmentation Fault while reading a file"
date: 2013-06-15
forum: Programming Talk
---

### Post by imvelox on 2013-06-15
Hello, i can't find why my program go to segfault.
If i type in console "./vcpl file_that_doesnt_exist" it print "... No such file or directory".
But if i type "./vcpl fiel_that_exit" it print "segmentation fault"! 

I can't understand why :(
Please help me

main.c:
```
#ifdef __linux__
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "config.h"
#include "c_vector.h"
#include "vcpl.h"




int main(int argc, char **argv)
{
    FILE *input;
    vcplOptions *options = (vcplOptions *)malloc(sizeof(struct vcplOptions));
    char c;
    char LineBuffer[255];
    strcpy(LineBuffer, "");
    
    if(argc < 2)
    {
        printf("Usage error!\n");
        return -1;
    }
    
    input = fopen(argv[1], "r");
    
    if(input == 0)
    {
        printf("(vcpl) %s: No such file or directory", argv[1]);
        fclose(input);
        return -1;
    }
    else
    {
        options->InputName=argv[1];
        /* Get file's lines */
        while((c = fgetc(input)) != EOF)
            if(c == '\n')
                options->Lines++;
    
        fsetpos(input, 0);
        /* Read code from file and store it into a variable-size vector node (like C++'s STL's vector class)*/
        /* Init vector */
        vector Vector;
        vector_init(&Vector);
        
        while(!feof(input))
        {
            c = fgetc(input);
            if(c == '\n')
            {
                vector_set(&Vector, (vector_count(&Vector) - 1), LineBuffer);
                vector_add(&Vector, "");
                strcpy(LineBuffer, "");
            }
            else strcat(LineBuffer, (char *)c);
        }
        for(int i = 0; i < vector_count(&Vector) ; i++)
            printf("%s", (char *)vector_get(&Vector, i));
        /* Exit */
        fclose(input);
        free(options);
        return 0;
    }
}
#endif
```

---

### Post by lisati on 2013-06-15
A segfault can happen when a program accesses an area of memory that it shouldn't. In your program it's most likely that the buffer you are using isn't big enough. 

I'm also a little concerned that the way you are appending the character to the buffer might need a little bit of tidying up, but will leave that to others more proficient in using C.

---

### Post by ofnuts on 2013-06-15
I don't know what you expect when you cast a character to pointer to char: 

```

strcat(LineBuffer, (char *)c);

```

Otherwise, plenty of things:
[LIST]
[*]reading the file just to count the lines isn't good for performance, and you don't seem to use that line count later yourself, so maybe you could count the lines while doing the rest 
[*]counting LF isn't really counting lines, the last line may not end with a LF so you maybe be missing one. You should add one when you hist EOF, unless the previous char was a LF. 
[*]as noted by dw67 you should be very careful about  the length of your buffers, whan the already contain, and what you are putting in them 
[*]don't cast the return of malloc() ('vcplOptions *options = (vcplOptions *)malloc(sizeof(struct vcplOptions));'. malloc() returns a void* that will fit any kind of pointer. When you cast you hide the fact that you didn't include malloc.h (by default the compiler will think malloc returns an int, and so will complain when you assign this int to a pointer) 
[*]instead of 'printf("Usage error!\n");' you can use  ''printf("Usage: my_program {file_name}...\n");'. Doesn't cost much more :) 
[*]it looks like you Linebuffer is added to the vector... and then overwritten when you build the next line. In other words your vector will be a collection of pointers all pointing to the same Linebuffer, which will contain the last line read. Either you strdup() your Linebuffer to add it to the vector, or you malloc() a new Linebuffer for each line. This will also avoid you having pointers to stack variables which is bound to cause problems later. 
[*]to add a character to the buffer, instead of using strcat, keep a count, set it to 0 for a new line, and use 'Linebuffer[count++]=c'. Finish with Linebuffer[count++]=0. With of course all the caveats about blindly adding things in a fixed-length memory area (but memory is cheap, use a 8K buffer, and just abort if the count goes over 8K). 
[/LIST]

Compile with all flags on

---

### Post by dwhitney67 on 2013-06-15
I agree with lisati; the buffer size could be too small, although without having knowledge of what the data looks like, it's impossible to definitely point to this as the root of the problem.

The problem could also lie within the "vector" functions that you are employing.  Without having the privilege to see that code, again it is impossible to determine if the problem lie within there.

A few critique points:

1.  Don't read the file twice.  You can determine how many lines are in it as you read the data.

2.  Don't assume the fopen() returns 0 on failure; it returns NULL.  Just because NULL has been defined to be equivalent to (void*)0 doesn't mean that this is the case on every system you may deal with in the future.

3.  Since it appears that you are reading lines from a file that are newline character delimited, use fgets() instead of reading character by character.

4.  Will your program not work on other systems?  I'm confused as to why you require the #ifdef __linux__ statement.

5.  Consider including your projects header files before the system header files.  This will tell you whether they can stand alone, or if they are dependent on a system header file that you have failed to include.

---

### Post by trent.josephsen on 2013-06-15
Just to add a little to what's been said already...

This is a better way to ensure you're compiling on the right platform:
```
#ifndef __linux__
#error "You must use Linux to compile this, sorry!"
#endif
/* followed by code */
```
However, you don't appear to be using any platform-specific features, at least not in this file, so I'd leave it off entirely.

ofnuts already mentioned that you shouldn't cast the return value of malloc(), but there are two other points I'd like to call attention to on that line. First, use the other form of sizeof:
```
    options = malloc(sizeof *options);
```
This idiom always works for any pointer type and is immune to maintenance bugs resulting from changing the type of `options'.

The second point is more stylistic. You've mixed `struct vcplOptions' with just `vcplOptions'; this tells me that you've probably typedef'd the latter to the former in one of the header files you didn't provide. (That or you're using C++, in which case you have other problems.) This is fine in that it's a legal way to use C, but from a code maintenance standpoint, typedef's are for hiding irrelevant information about a type. The fact that `options' points to a struct is in fact highly relevant information, since you go on to access its members using ->. I think it's better to always call things by their real names, unless you're deliberately hiding information about an opaque or very complex type. Hiding `struct' behind a typedef makes reading the code harder, not easier. At least, if you choose to do it this way, call the typedef a name ending in _t, for consistency with the standard typedefs and to signal to the reader that he's going to have to look up the definition to figure out what kind of a thing it is.

I'd use char LineBuffer[255] = ""; to initialize the string. Quicker, and doesn't depend on <string.h>. Later, if you want to set it to the empty string, just do LineBuffer[0] = 0.

```

        /* Read code from file and store it into a variable-size vector node (like C++'s STL's vector class)*/
        /* Init vector */
        vector Vector;
        vector_init(&Vector);

```
Since I mentioned it before, here's a good example of where a typedef is used appropriately -- I don't care when I'm using this code whether `Vector' is a struct or a pointer or something else, because all I do with it is pass it (well, its address) to functions that know how to use it. (In other words, `vector' is an opaque type.) This is a case where calling it a `struct vector' would do nothing for clarity.

strcat(LineBuffer, (char *)c); made me flinch, and is a great example of why a cast is pretty much never the right way to avoid a warning. New C programmers often use lots of casts in the mistaken belief that silencing type system warnings is desirable. In standard C, most conversions are done implicitly and when you see the type system complaining, it usually means you've done something wrong that a simple cast won't fix. Unfortunately, adding a cast will often silence the warning without forcing you to fix the underlying problem.

Finally, does Vector need to be cleaned up in the Exit section? If not, that's fine, but if you have a vector_destroy function or something like that, it needs to be called somewhere.

---

