---
title: "Segmentation fault"
date: 2012-11-15
forum: Programming Talk
---

### Post by goldy2425 on 2012-11-15
Hi Everyone,
 
I am new to linux and need urgent help. I have installed Ubuntu 12.04 and wanted to run a small program in c to show bufferoverflow attack.I compiled this program using gcc compiler, but when I passed the address like (something."\x43\x40\x83") arrgument with memory address.
 
I am getting a "Segmentation fault(core dumped)"
I have tried -fno-stack-protector but it's not working.
 
please help me , thanks in advance.

---

### Post by lisati on 2012-11-15
*Thread moved to **Programming Talk**.*

---

### Post by trent.josephsen on 2012-11-15
That is what *should* generally happen when you overflow a buffer (and thereby scribble on memory you don't own). If you think there's a reason your code should *not* segfault, please post it.

It's possible, even likely, that the exploit you were trying to use does not affect the current Ubuntu kernel version.

---

### Post by goldy2425 on 2012-11-16
Thanks for the quick reply 
 
I have made file the victim.c with this code
```
#include <string.h>
#include <stdio.h> 

void foo(const char* input)
{
    char buf[10];

    printf("My stack looks like:\n%p\n%p\n%p\n%p\n%p\n% p\n\n");

    strcpy(buf, input);
    printf("%s\n", buf);

    printf("Now the stack looks like:\n%p\n%p\n%p\n%p\n%p\n%p\n\n");
}

void bar(void)
{
    printf("Augh! I've been hacked!\n");
}

int main(int argc, char* argv[])
{
    //Blatant cheating to make life easier on myself
    printf("Address of foo = %p\n", foo);
    printf("Address of bar = %p\n", bar);
    if (argc != 2) 
 {
        printf("Please supply a string as an argument!\n");
        return -1;
	} 
foo(argv[1]);
    return 0;
}
```

then when I am executing this file I am passing argument with the bar function addres.
but I am getting Segmentation fault (code dumped) error 
 
 
> **trent.josephsen said:**
> That is what *should* generally happen when you overflow a buffer (and thereby scribble on memory you don't own). If you think there's a reason your code should *not* segfault, please post it.
 
It's possible, even likely, that the exploit you were trying to use does not affect the current Ubuntu kernel version.

---

### Post by lisati on 2012-11-16
Where's printf getting the values to plug into the %p?

---

### Post by goldy2425 on 2012-11-16
when i run the victim file I get the address of both function then I am passing the address with the argument like
 
[SIZE=2][EMAIL="root@ubuntu:/home/BufferOverflow"]root@ubuntu:/home/BufferOverflow[/EMAIL]# ./victim aaaaaaa."\x81\x80\x04"
Address of foo = 0x8048444
Address of bar = 0x8818004[/SIZE]
[SIZE=2]My stack looks like:
(nil)
0xbffff6c8
0xb5c50c2f
0xb2fc5c10
0x8042357
0xbffcc6b4


Segmentation fault (core dumped)[/SIZE][COLOR=#888888]

[/COLOR] 
> **lisati said:**
> Where's printf getting the values to plug into the %p?

---

### Post by lisati on 2012-11-16
You might want to compare your printf statements......

---

### Post by spjackson on 2012-11-16
> **goldy2425 said:**
> 
[SIZE=2][EMAIL="root@ubuntu:/home/BufferOverflow"]root@ubuntu:/home/BufferOverflow[/EMAIL]# ./victim aaaaaaa."\x81\x80\x04"
Address of foo = 0x8048444
Address of bar = 0x8818004[/SIZE]

So, what I think you are trying to do is write the address of bar onto the stack by writing beyond the bounds of the stack variable buf. You are not doing that: you are writing beyond the bounds of buf, but you are not writing the address of bar.

First, the interpretation of \x81 etc. that the compiler applies to a string literal in C source code is not applied by the C runtime to command line arguments. So \x81 is not the byte whose hex value is 81, but rather it is 4 characters '\' 'x' '8' '1'.

Second (and I'm not an expert here), you need to think about the size of the pointer (4 or 8 bytes), the byte order and alignment. If you actually manage to write the address of bar after the end of buf, will it do what you want it to? Dunno.

---

### Post by Bachstelze on 2012-11-16
```
firas@itsuki ~ % cat test.c 
#include <string.h>
#include <stdio.h> 

void foo(const char* input)
{
    char buf[10];
    strcpy(buf, input);
}

void bar(void)
{
    printf("Augh! I've been hacked!\n");
}

int main(void)
{
    char input[] = {'1', '2',
                    '1', '2', '3', '4',
                    '1', '2', '3', '4',
                    '1', '2', '3', '4',
                    '1', '2', '3', '4',
                    '1', '2', '3', '4',
                    0x56, 0x84, 0x04, 0x08, '\0'};
    foo(input);
    return 0;
}
firas@itsuki ~ % gcc -fno-stack-protector -o test test.c                                    
firas@itsuki ~ % ./test 
Augh! I've been hacked!
zsh: segmentation fault (core dumped)  ./test

```

Still segfaults though... I'm not an expert either, so I would have to investigate it further but I don't have a lot of time on my hands right now...

---

### Post by schauerlich on 2012-11-16
> **lisati said:**
> Where's printf getting the values to plug into the %p?

x86 calling conventions are for parameters to be passed on the stack (although in some cases they may be passed in registers). printf takes a variable amount of arguments, and it assumes that the number of arguments specified by the format is how many arguments are actually passed at runtime. So, it will look down the stack for the arguments, taking however many bytes the format tells it to. %p is the pointer type, which generally is the size of a word on the CPU. So, it's a hack-y way to get a printout of the stack without GDB and friends. It's a hack, platform specific, and not guaranteed to work in other environments. If you compile this with -Wall or equivalent on most modern compilers, you will get a warning of "too few arguments for format" which tries to guard against this sort of thing, but this is an extension of the compiler, and not part of the C language.

---

### Post by Bachstelze on 2012-11-16
Some comments:

As you see, the string does not just consist of the address of bar (last 4 bytes), but also some gibberish before it (there is nothing sacred about "1234", it could be anything). This is because we are trying to overwrite the return address. On my machine, the stack looks like this:

```

+----------------+
| return address |   buf[22-25]
+----------------+
|  saved ebp     |   buf[18-21]
+----------------+
|   buf[14-17]   |
+----------------+
|   buf[10-13]   |
+----------------+
|   buf[6-9]     |
+----------------+
|   buf[2-5]     |
+--------+-------+
|        |buf[0-1]
+--------+-------+
```

So in order to overwrite the return address, we need to write on buf[22] to buf[25]. I suspect that in order to not segfault at all, we would need to write a good value on the saved ebp as well...

> **trent.josephsen said:**
> That is what *should* generally happen when you overflow a buffer (and thereby scribble on memory you don't own). If you think there's a reason your code should *not* segfault, please post it.

The point is that here we are writing on memory that we own, but shouldn't write to. This is why the x86 arch is so bad from a security standpoint: it trusts that you are not going to write to some places, even though you technically can because you own them.

---

### Post by Bachstelze on 2012-11-16
Also...

> **goldy2425 said:**
> 
I am new to linux and need urgent help.

I have no idea why something like this would be so urgent. If you want to use it for a prank, grow up. If it's homework, I suggest you actually pay attention in class.

---

### Post by goldy2425 on 2012-11-16
Thanks everyone for the quick response, I really appreciate that.
@Bachstelze I have to give a presentation on buffer overflow attack with a small demo. I am trying my best to make a small program to demonstrate this  attack . I have turn off all the security but still it giving me the same error...
> **Bachstelze said:**
> Also...
 
 
 
I have no idea why something like this would be so urgent. If you want to use it for a prank, grow up. If it's homework, I suggest you actually pay attention in class.

---

### Post by Bachstelze on 2012-11-16
Then you should tell whoever asked you to give a presentation on this that you do not have the necessary knowledge and to ask someone else.

---

### Post by dwhitney67 on 2012-11-16
> **goldy2425 said:**
> ... I have to give a presentation on buffer overflow attack with a small demo.

Depending on the audience at your demo, you may want to avoid any embarrassment from using the function strcpy().

Anybody who has any background with Information Assurance (IA) knows that function is considered evil and its use should be avoided.  Only an amateur programmer would use strcpy().

Use strncpy() (or better yet, strlcpy() if available) instead.

---

### Post by Bachstelze on 2012-11-16
> **dwhitney67 said:**
> 
Anybody who has any background with Information Assurance (IA) knows that function is considered evil and its use should be avoided.  Only an amateur programmer would use strcpy().


The problem is that there are a lot of mediocre ("amateur" is not the correct word since they get paid, sometimes a lot) programmers in the world, writing code that gets used in real programs. If the purpose is to demonstrate how to exploit real programs, then of course you are going to need a poorly written one. If the program is correctly written, there is nothing to exploit.

(As an aside, this is why I'm not terribly interested in software security. Taking advantage of people's stupidity and/or ignorance is only fun for so long.)

---

### Post by lisati on 2012-11-16
> **schauerlich said:**
> So, it's a hack-y way to get a printout of the stack without GDB and friends. It's a hack, platform specific, and not guaranteed to work in other environments. 
Thank you for the explanation. I know just enough C to know that something didn't look quite right.

---

