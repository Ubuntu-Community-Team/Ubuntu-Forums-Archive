---
title: "problem while using inline assembly"
date: 2009-11-09
forum: Programming Talk
---

### Post by bshankha on 2009-11-09
Hi,
I am trying to use the inline assembly on X86 (compiler is gcc)
        int y;
        asm ("mov %fs:thread_local@TPOFF, %rax");
        asm ("mov %%rax, %%rbx;"
                :"=Ab" (y) 
        );

This code works perfectly fine. 

when i try to compile the following piece of code
             int y;
 20         asm ("mov %fs:thread_local@TPOFF, %rax;"
 21                 "mov %%rax, %%rbx;"
 22                 :"=Ab" (y)
 23         );

This gives a error 

tls.c:20: error: invalid 'asm': operand number missing after %-letter
tls.c:20: error: invalid 'asm': operand number missing after %-letter

I think it is not recognising the %fs:thread_local@TPOFF

Can someone please explain as to what is wrong with the second part. 

thanks
shankha

---

### Post by Mister.Vash on 2009-11-10
when you post code, you should wrap it, it makes it easier to read.

I haven't done this in a while, but I believe it should work as listed below.  I don't think you were properly separating the instructions, so I removed the quotes where I thought they were off

[PHP]
asm ("mov %fs:thread_local@TPOFF, %rax;
      mov %%rax, %%rbx;"
     :"=Ab" (y)
    );
[/PHP]

If that doesn't do it, post again

---

### Post by bshankha on 2009-11-10
[php]
 26         asm ("mov %fs:thread_local@TPOFF, %rax;
 27                 mov %%rax, %%rbx;"
 28                 :"=Ab" (y)
 29         );
[/php][php]
gcc -m64 tls_long.c -lpthread
tls_long.c:26:7: warning: missing terminating " character
tls_long.c: In function &#8216;check_read_reloc&#8217;:
tls_long.c:26: error: missing terminating " character
tls_long.c:27: error: expected string literal before &#8216;mov&#8217;
tls_long.c:27:20: warning: missing terminating " character
tls_long.c:27: error: missing terminating " character
[/php]This doesn't work. My whole idea was to transform it to two lines something like this

[php]
asm ("mov %fs:thread_local@TPOFF, %rax;"
           :"=Ab" (y)
         );
[/PHP]

Is this possible?

---

### Post by bshankha on 2009-11-10
I have posted the same query at google groups ..

> 
[http://groups.google.com/group/comp.lang.asm.x86/browse_thread/thread/c86d50c623ef9baf?hl=en](http://groups.google.com/group/comp.lang.asm.x86/browse_thread/thread/c86d50c623ef9baf?hl=en)


---

