---
title: "Programming Challenge"
date: 2011-07-21
forum: Programming Talk
---

### Post by jramshu on 2011-07-21
I know the first challenge is old to all you guys, but it is the first time I sat down and wrote, compiled and debugged anything that I didn't copy from a book, or the internet. It took me a little time getting it to compile right. I had several errors at first.

I have been reading books on C, and how it looks in assembly. The bigger picture they say. LOL, it's a brain full.

So, since I am a beginner at this, I figured I should start at the beginning and since the thread is closed I figured it may be ok to post a thread about it. Kind of exciting getting it to compile and run. It probably looks butchered to all you advanced folks, have mercy. LOL.

[PHP]#include <stdio.h>

	main()
{
	  int i;
	  i = 99;
	  	
		for(i; i >= 2; i--)
	 	  printf("%d bottles of beer on the wall,\n%d bottles of beer,\ntake one down, pass it around,\n",i ,i);
                
                if(i = 1);
		  printf("One bottle of beer on the wall,\none bottle of beer,\ntake it down, pass it around,\n");
		if(i = 0);
		  printf("no more bottles of beer on the wall.\n");
		  
		
return 0;
}[/PHP]

EDIT: Can't get it to line up right here, but is fine in editor.

EDIT: Added a part I missed in the song.

[PHP]
#include <stdio.h>

  int main()
{
    int i;
    i = 99;
      for(i; i >= 2; i--)
	 printf("\n%d bottles of beer on the wall,\n%d bottles of beer,\ntake one down, pass it around,\n%d bottles of beer on the wall.\n",i ,i, i-1);
      if(i == 1);
	 printf("\nOne bottle of beer on the wall,\none bottle of beer,\ntake it down, pass it around,\n");
      if(i == 0);
	 printf("\nNo more bottles of beer on the wall.\n");
		  
		
return 0;
}
[/PHP]

EDIT: Well crap, it's still a little off. It still show "1 bottles."
EDIT: I changed the bottom codes spacing so it would be easier to read in terminal, still got the "1 bottles" though.

---

### Post by robgraves on 2011-07-21
i'm not entirely sure what your're asking, but i copied your code and got a compile error and realized you don't have **int **in front of **main()** on line 3, my edited version of your code compiled fine and ran fine:
```
#include <stdio.h>

    int main()
{
      int i;
      i = 99;

        for(i; i >= 2; i--)
           printf("%d bottles of beer on the wall,\n%d bottles of beer,\ntake one down, pass it around,\n",i ,i);

                if(i = 1);
          printf("One bottle of beer on the wall,\none bottle of beer,\ntake it down, pass it around,\n");
        if(i = 0);
          printf("no more bottles of beer on the wall.\n");


return 0;
}

```

hope that helps.

---

### Post by jramshu on 2011-07-21
Thanks, I changed it. It doesn't make any difference when I compile it though.

What I'm trying to figure out is how to get it to stop using "bottles" when it gets to one. That's where I am stuck. I'm tinkering with some stuff on it but haven't ran across it yet.

---

### Post by lisati on 2011-07-21
> **jramshu said:**
> Thanks, I changed it. It doesn't make any difference when I compile it though.

What I'm trying to figure out is how to get it to stop using "bottles" when it gets to one. That's where I am stuck. I'm tinkering with some stuff on it but haven't ran across it yet.

I suspect a stray semicolon, amongst other things:
> if(i = 1)[COLOR="Red"];[/COLOR]

---

### Post by lisati on 2011-07-21
I loaded the supplied source into Codeblocks, made a couple of minor tweaks related to stray semicolons (there are a couple of other minor tweaks that could be done), and came up with the following which seems to work perfectly:
```
#include <stdio.h>

int main()
{
    int i;
    i = 99;

    for(i; i >= 2; i--)
        printf("%d bottles of beer on the wall,\n%d bottles of beer,\ntake one down, pass it around,\n",i ,i);

    if(i = 1)
        printf("One bottle of beer on the wall,\none bottle of beer,\ntake it down, pass it around,\n");
    if(i = 0)
        printf("no more bottles of beer on the wall.\n");


    return 0;
}

```

Edit: just noticed: the tests should be:
```
if(i == 1)
```
and
```
if(i == 0)
```
which leaves one more tweak: decrement between the tests. This is left as an exercise for the reader.

---

### Post by jramshu on 2011-07-21
> **lisati said:**
> I suspect a stray semicolon, amongst other things:

When I take the semi-colon out it doesn't make it past the first 'if' statement. Then I completely lose the 'if(i = 0)' and it's printf() funtion.

I am an amateur at this and appreciate the input. I need it. I'm sure my syntax is incorrect.

EDIT: Thanks, was posting while you were posting. I appreciate the help, am going to make changes and recompile it.

---

### Post by lisati on 2011-07-21
> **jramshu said:**
> When I take the semi-colon out it doesn't make it past the first 'if' statement. Then I completely lose the 'if(i = 0)' and it's printf() funtion.

I am an amateur at this and appreciate the input. I need it. I'm sure my syntax is incorrect.

EDIT: Thanks, was posting while you were posting. I appreciate the help, am going to make changes and recompile it.

Don't sweat it: I'm relatively inexperienced with C as well, it wasn't an option when I started learning ForTran many years ago using punched cards.

---

### Post by jramshu on 2011-07-21
This is how I have it now. I had already caught the "==" a few minutes earlier. This output looks better and the only thing I'm left with is the "1 bottles" instead of it being "1 bottle." I'll will keep on it though. 

[PHP]
#include <stdio.h>

int main()
{
    int i;
    i = 99;
      
    for(i; i >= 2; i--)
	 printf("\n%d bottles of beer on the wall,\n%d bottles of beer,\ntake one down, pass it around,\n%d bottles of beer on the wall.\n",i ,i ,i-1);
    if(i == 1)
	 printf("\nOne bottle of beer on the wall,\none bottle of beer,\ntake it down, pass it around,\n");
	 printf("\nNo more bottles of beer on the wall.\n");
		  
		
return 0;
}

[/PHP]

Had to put the semi's back in there to get the output right. Without them on the "if(i==0)" it doesn't print out the "No more bottles of beer on the wall."

EDIT: Removed "if(i == 0);"

---

### Post by Bachstelze on 2011-07-21
> **jramshu said:**
> 
Had to put the semi's back in there to get the output right. Without them on the "if(i==0)" it doesn't print out the "No more bottles of beer on the wall."

Then you might as well delete it altogether because

```
    if(i == 0);
```

or more eloquently

```

    if(i == 0)
        ;
```

Means "if i equals 0, do nothing". So it may as well not be there at all. ;)

---

### Post by jramshu on 2011-07-21
> **Bachstelze said:**
> Then you might as well delete it altogether because

```
    if(i == 0);
```

or more eloquently

```

    if(i == 0)
        ;
```

Means "if i equals 0, do nothing". So it may as well not be there at all. ;)

I getcha now. I removed it. Thanks.

---

### Post by jramshu on 2011-07-21
Does anyone know the correct way to get it to run and when it gets to "take one down, pass it around, 1 bottles of beer on the wall" to drop the plural and just say "bottle"?

EDIT: I guess I could read through all the posts that are written in C and 'cheat.' LOL

---

### Post by JupiterV2 on 2011-07-21
One such solution is:

```
for (i = 2; i > 0; i++) {
  printf ("Bottle%c\n", i > 1 ? 's' : '');
}
```

It's a little hacky but it gets the job done.

---

### Post by Bachstelze on 2011-07-21
> **JupiterV2 said:**
> One such solution is:

```
for (i = 2; i > 0; i++) {
  printf ("Bottle%c\n", i > 1 ? 's' : '');
}
```

It's a little hacky but it gets the job done.

Actually no, it does not.

```
firas@aoba ~ % cat test.c 
#include <stdio.h>

int main(void)
{
        for (int i=2; i>0; i--) {
                printf("%d bottle%c\n", i, i > 1 ? 's' : '');
        }
        return 0;
}
firas@aoba ~ % cc -std=c99 -o test test.c
test.c:6:58: error: empty character constant

```

Remember that a character really is an integer, so you *must* give it a value, it can't be empty like a string.

(Also [font=monospace]for (i=2; i>0; i++)[/font] is going to run for a long time.)

---

### Post by jramshu on 2011-07-23
Thanks for the input guys. I'll experiment with them and see how I come out.

---

### Post by ziekfiguur on 2011-07-23
instead of using a character in the ternary operator use a string, than it should work
```
printf("%d bottle%s\n", i, i > 1 ? "s" : "");
```

Also, remove the if in front of the last two print statements, after the for loop i will always be 1, there's no need to test for it.

here is a version i just wrote, it took me a lot longer than it should, i should really practise more.
```
;nasm -f elf64 beer.asm
;ld beer.o

section .text
global _start
_start:
    mov rbx, 99
loop:
    call print
    sub rbx, 1
    cmp rbx, 2
    jge loop

    mov rax, 1
    mov rsi, onebeer
    mov rdx, onebeerlen
    syscall
    mov rax,1
    mov rsi, nobeer
    mov rdx, nobeerlen
    syscall
    mov rax, 60 ; exit syscall
    xor rdi, rdi; return value 0
    syscall

print:
    call printn_calc
    mov rax, 1
    mov rsi, beer1
    mov rdx, beer1len
    syscall
    mov rsi, [printn_start]
    call printn_print
    mov rax, 1
    mov rsi, beer2
    mov rdx, beer2len
    syscall
    ret

printn_calc:
    mov rax, rbx
    mov rsi, printn_buf + 64
    mov rcx, 10
printn_loop:
    xor rdx, rdx
    div rcx ; divide rdx:rax by rcx, rax will hold the quotient, rdx the remainder
    add rdx, 0x30 ; ascii numbers are valued 0x30 to 0x39
    dec rsi
    mov byte [rsi], dl
    cmp rax, 0
    jg printn_loop
    mov [printn_start], rsi
    mov rdi, 1 ; write to stdout
printn_print:
    mov rax, 1 ; write syscall
    mov rdx, printn_buf + 64
    sub rdx, rsi
    syscall
    ret

section .data
    beer1 db " bottles of beer on the wall,", 0xa
    beer1len equ $ - beer1
    beer2 db " bottles of beer,", 0xa, "take one down, pass it around,", 0xa
    beer2len equ $ - beer2

    onebeer db "One bottle of beer on the wall,",0xa,"one bottle of beer,",0xa,"take it down, pass it around,", 0xa
    onebeerlen equ $ - onebeer
    nobeer db "no more bottles of beer on the wall.", 0xa
    nobeerlen equ $ - nobeer

section .bss
    printn_buf resb 64
    printn_start resq 1

```

---

