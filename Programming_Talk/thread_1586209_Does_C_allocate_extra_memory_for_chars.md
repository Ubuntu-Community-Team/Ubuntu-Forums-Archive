---
title: "Does C allocate extra memory for chars?"
date: 2010-10-01
forum: Programming Talk
---

### Post by Senesence on 2010-10-01
I have the following program:

[PHP]
#include <stdio.h>
#include <string.h>

int main(int argc, char** argv){
    
    char input[1];

    strcpy(input, "Word");

    printf("%s\n", input);

    return 0;

}
[/PHP]

Now, as far as I understand, an input of more than 1 character should trigger a segfault, because I only own memory for 1 character.

However, that doesn't happen in the above program.

Can anyone explain why?

Thanks.

---

### Post by Tony Flury on 2010-10-01
> **Senesence said:**
> 

Now, as far as I understand, an input of more than 1 character should trigger a segfault, because I only own memory for 1 character.

However, that doesn't happen in the above program.

Can anyone explain why?

Thanks.

Firstly your char array is allocated on the stack, so that will change some of how it behaves.

What is almost certainly happening though is that memory is allocated by the operating system in chunks, and not as individual bytes. Also C itself has no error checking to see if you are writing over the end of the array.

If you wrote a few hundred characters into your single char array, it would probably segfault, as you would go off the end of the chunk allocated to your program.

Fairly sure integers would do something similar.

The answer for the C language is that the result of writing over the end of an array of any type is undefined - so it might segfault, it might overwrite another variable, it might overwrite part of the code, or the stack frame, or it could do anything. Think about the impact of writing over a file buffer just before it gets written to disk - and then think about what the impact is if that file is a key config file say for grub or your system boot processes. in the worst case writing over the end of an array could be catasrophic.

If you think about what this means in terms of the language : 

```

char input[1] ;

```
Does not mean "Only give me space for one character and don't allow me to write any more" - it more closely means "My programme only intends to write one character, and if i write more, then that is my problem"

---

### Post by spjackson on 2010-10-01
As Tony Flury points out, writing beyond the end of an array is undefined behaviour.

As an indication of what is happening here,
```

#include <stdio.h>
#include <string.h>

int main(int argc, char** argv){

    char w='w';
    char x='x';
    char y='y';
    char input[1];
    char z='z';

    printf("w='%c', x='%c', y='%c', z='%c'\n", w, x, y, z);
    strcpy(input, "Word");

    printf("%s\n", input);
    printf("w='%c', x='%c', y='%c', z='%c'\n", w, x, y, z);

    return 0;

}

```Output on my system
```

w='w', x='x', y='y', z='z'
Word
w='d', x='r', y='o', z='z'

```Can you see where the o r and d have gone?

---

### Post by Senesence on 2010-10-01
> **Tony Flury said:**
> What is almost certainly happening though is that memory is allocated by the operating system in chunks, and not as individual bytes. Also C itself has no error checking to see if you are writing over the end of the array.

Ah, I see. I suspected something along those lines, but I wasn't really sure.

Thanks.

As for the fact that C has no error checking; I understood that "Segfault" was a message from the OS, rather than from the program itself.

Anyway, I have an additional question (if you don't mind):

If the OS allocates memory in arbitrary chunks, does malloc always call for a new chunk, or does it grab any remaining memory from the last chunk?

For example, if I were to do:

[PHP]
char* first = malloc(1);
char* second = malloc(1);
[/PHP]

Is that getting two chunks of memory, of which I'll only use two bytes, or is it two bytes from a single chunk (assuming that the first chunk has bytes to spare)?

---

### Post by Bachstelze on 2010-10-01
Also different platforms will react differently. On OS X, for example, it always exits with an abort trap. On Linux, the assembly code gives us a better idea about what's going on:

```
firas@itsuki ~ % cat test.c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(void)
{
    char input[1];
    strcpy(input, "foo");
    printf("%s\n", input);
    return EXIT_SUCCESS;
}

firas@itsuki ~ % gcc -m32 -S test.c
firas@itsuki ~ % cat test.s | nl  
     1          .file   "test.c"
     2          .section        .rodata
     3  .LC0:
     4          .string "foo"
     5          .text
     6  .globl main
     7          .type   main, @function
     8  main:
     9          pushl   %ebp
    10          movl    %esp, %ebp
    11          andl    $-16, %esp
    12          subl    $32, %esp
    13          movl    $.LC0, %eax
    14          movl    $4, 8(%esp)
    15          movl    %eax, 4(%esp)
    16          leal    31(%esp), %eax
    17          movl    %eax, (%esp)
    18          call    memcpy
    19          leal    31(%esp), %eax
    20          movl    %eax, (%esp)
    21          call    puts
    22          movl    $0, %eax
    23          leave
    24          ret
    25          .size   main, .-main
    26          .ident  "GCC: (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5"
    27          .section        .note.GNU-stack,"",@progbits
```

The important part is line 11 and 12, which tell us that the compiler will allocate 48 bytes on the stack for your data, more than enough for "foo". You can even replace "foo" with "supercalifragilisticexpialidocious", you will get a segfault, but it will still produce the intended result, because even when the stack of the main function overflows, the overflow data will (probably) not overwrite anything. This, however, will not work:

```
firas@itsuki ~ % cat test.c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void foo(char* dest)
{
    char buf[1];
    strcpy(buf, "supercalifragilisticexpialidocious");
    strcpy(dest, buf);
}

int main(void)
{
    char input[1];
    foo(input);
    printf("%s\n", input);
    return EXIT_SUCCESS;
}


```

because when the stack frame of the foo function overflows, the overflow data will write over the stack frame of the main function.

---

### Post by Bachstelze on 2010-10-01
> **Senesence said:**
> 
If the OS allocates memory in arbitrary chunks, does malloc always call for a new chunk, or does it grab any remaining memory from the last chunk?

For example, if I were to do:

[PHP]
char* first = malloc(1);
char* second = malloc(1);
[/PHP]

Is that getting two chunks of memory, of which I'll only use two bytes, or is it two bytes from a single chunk (assuming that the first chunk has bytes to spare)?

Allocating memory with malloc and by declaring an array are totally different things, but to answer your question, when you do this, you get two one-byte chunks of data, which may or may not be contiguous, you must not make any assumption about whether or not they will be, because the OS is free to give you bytes located anywhere.

---

### Post by slavik on 2010-10-02
> **Bachstelze said:**
> Allocating memory with malloc and by declaring an array are totally different things, but to answer your question, when you do this, you get two one-byte chunks of data, which may or may not be contiguous, you must not make any assumption about whether or not they will be, because the OS is free to give you bytes located anywhere.
Another thing to keep in mind is the overcommit. Because you can ask for more memory than you have (talking about virtual memory, that is RAM+swap) and malloc will return with success, but when you try to fill it all, the OOM killer will kick in.

---

