---
title: "Run-time of a C-program"
date: 2010-09-10
forum: Programming Talk
---

### Post by gaurish108 on 2010-09-10
Hi I am a beginner in learning C, and I wanted to know the simplest way to find the* total time my program takes to run*. 

If some-one can give me the necessary lines of code / links to web-pages explaining how to do this I will be grateful.

---

### Post by Bachstelze on 2010-09-10
Run it with

```
time program
```

---

### Post by gaurish108 on 2010-09-10
Thank you very much  for your reply. I just tested this on a simple Hello World program and I wish to understand the output that was created using the*** time*** keyword.

Hello World 

real    0m0.001s
user    0m0.000s
sys    0m0.000s


Could you tell me what real, usr and sys mean? Also what does the m sandwiched between the two zeros mean? 

Thank you

---

### Post by Bachstelze on 2010-09-10
"real" is the time elapsed in the real world between the moment the program started and the moment it terminated.

"user" and "sys" are CPU time, i.e. the amount of time the CPU was actually working on your program, as opposed to waiting for an I/O event, for example.

"user" is the amount of time the CPU was working on your program only, excluding syscalls (functions requested by your program but performed by the kernel). "sys" includes syscalls.

As an illustration, consider this program:

```
#include <fcntl.h>
#include <stdio.h>
#include <unistd.h>

int main(void)
{
    int n, i, fd;
    scanf("%d", &n);
    switch(n) {
        case 1:
            /* Spend a lot of time doing syscalls:
             * open a file, close it, repeat.
             */
            for (i=0; i<1e6; i++) {
                fd = open("/dev/null", O_RDONLY);
                close(fd);
            }
            break;
        case 2:
            /* Spend a lot of time doing nothing */
            sleep(5);
    }
    return 0;
}

```

And try running it with different values of n.

---

### Post by nvteighen on 2010-09-11
A note... maybe it's just nitpicking, but I believe you have to learn the technical terms in order to understand a community and also be part of it.

If English is not your native language (as it isn't mine either), I know this can be a bit frustrating... English compund words are treacherous... :P Don't worry, in the end, you'll always find people that will help you and you'll master the programming technobabble sooner as you might think.

"Run-time" or, better, "runtime" it's usually used to refer to the execution environment for a program or, at least, the time when your code is executed as opposed as when it is compiled (compile-time)... but never the amount of time. If you know some Python, the runtime is the interpreter. In C, it's a bit more complex, but you could say it is the kernel (specially the ELF interpreter). Actually, that's what I thought of when reading the title.

Usually, we use "execution time" for what you mean. Some prefer to talk about "execution speed", which isn't quite correct because they're actually talking about time, but it's somehow intituive. There might be other terms too that I don't remember, but that's one that's unambiguous.

---

