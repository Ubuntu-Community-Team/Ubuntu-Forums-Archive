---
title: "asking help with prints methods in NASM."
date: 2011-10-15
forum: Programming Talk
---

### Post by Proudhonite on 2011-10-15
this humble newbie created this thread to ask a simple question...
how do you print a number in the screen with nasm(or the sum of to integers )? i have been reading various tutorials, but they are very technical, and while by no means useless, i find them quite umpractical for a newbie in assambler like me.

i tried to simulate a "hello world" tutorial, but it did not work at all.
here is my code, just in case:

```

section .data
        dat1      db    3             ;
        dat2      db    2             ;
        len       equ   $-dat1        ;
                                      ;

section .text
        global _start

_start:

        mov eax,4         ;
        mov ebx,1         ;
        mov ecx,dat1      ;
        add ecx,dat2      ;
        mov edx,len       ;

        int 80h           ;

        mov eax,1         ;
        mov ebx,0         ;
        int 80h
```

thanks beforehand, and if someone has a link to a more practical tutorial, it would be apreciated too.

---

### Post by gnometorule on 2011-10-16
Your variable definition doesn't quite work; also, this obviously wouldn't print out "Hello World" (but I assume you know that, just called it "Hello World" figuratively). Here's a link to a working version:

[http://www.cs.umbc.edu/portal/help/nasm/sample.shtml#hello](http://www.cs.umbc.edu/portal/help/nasm/sample.shtml#hello)

---

### Post by Proudhonite on 2011-10-16
thank you for your reply, and sorry for not explaining myself right.

what i tried to say, is that i tried to simulate the way that the hello world example prints out the hello world message, but instead of that, i wanted it to print the sum of two numbers. of course, my code didn't work (i used what i undestood of the very same code that you just put), so i wanted to know how could i manage to print and integer (and a sum of two integers) and how exactly does it work.

thanks again.

---

### Post by gnometorule on 2011-10-16
I think we're on the same page, but just to make sure: you did notice that you were missing some colons at the top, right? Adding those, your program should be fine for what you try to do.

---

### Post by Proudhonite on 2011-10-16
i fixed the colon error, but it still does not work.

However, reading online, i found that to print an integer, i would need to convert it to the ascii value, but i have no idea as how to accomplish this 
(the only idea i have, and it would only work with single digits, would be to sum the integer to 30 (the ascii hexadecimal value were numbers start) and then convert that number to "3Xh" x being the number, but i have no idea as how to accomplish this conversion in nasm)

any kind of help will be appreciated.

and thanks again.

---

### Post by gnometorule on 2011-10-16
I'm out and about and have only a minute, but some pointers that hopefully allow you to do this as you like:

(1) recall how printf works. You also have a format string. As you want to print an integer, you need one with %d in it. Define that string too.

(2) check (google?) which register holds the format string when you call, from assembly, printf

(3) move the address of the format string you defined in (1) into that register. You should find code examples by googling, but it's essentially the same again you already do

(4) after adding these two lines, your call should work fine

---

### Post by Proudhonite on 2011-10-17
yes, i have found various examples that use printf calling external libraries form c, an normally use the register eax as the integer input.

however, i was actually seeking for more native method, without the use of external libraries (to have a better understanding).

what i tried, unsuccessfully, was to make a loop that would sum 1 to eax (with an intial value of 30h) the number of time of the value of the integer.
this:

```
section .data
        dat1:      db    3             ;
        dat2:      db    2             ;
        trhs:      db    30h           ;
                                       ;

section .text
        global _start

_start:
        mov ecx,dat1      ;
        add ecx,dat2      ;
        mov eax,trhs      ;
loop_start:
        inc eax           ;
        loop loop_start   ;

        mov ecx,eax       ;
        mov eax,4         ;
        mov ebx,1         ;
        mov edx,1         ;

        int 80h           ;

        mov eax,1         ;
        mov ebx,0         ;
        int 80h
```

that does not outputs a single thing. if, however, instead of giving ecx the value of the addition of dat1 and dat2, and instead give it a simple value like 5(mov ecx,5) it outputs ...things (in the case of 5 it outputs "."); but of course, i don know why. 

and thanks again for your earlier post.

---

### Post by gnometorule on 2011-10-17
Well, you still don't add the format string. Recall the syntax of printf:

```

a = 5;
char* fmt = "integer is %d\n";
printf(fmt, a);

```

You are still not defining fmt, and are not putting it into its register. 

Instead of getting really confused, here is what I suggest you spend a couple of hours with. It will serve you well for any serious coding. Get familiar with gdb:

[http://sunsite.ualberta.ca/Documentation/Gnu/gdb-4.18/html_chapter/gdb_toc.html](http://sunsite.ualberta.ca/Documentation/Gnu/gdb-4.18/html_chapter/gdb_toc.html)

Write your toy program in C, then single-step through the disassembly with gdb. It's a skill to have anyway if you want to do this from scratch in NASM. You will see how your conpuler puts the different parameters  into their registers, and then only need to translate that into NASM.

---

