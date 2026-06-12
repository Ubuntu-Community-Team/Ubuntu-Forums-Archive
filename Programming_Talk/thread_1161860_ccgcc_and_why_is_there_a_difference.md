---
title: "cc/gcc and why is there a difference?"
date: 2009-05-17
forum: Programming Talk
---

### Post by chuuk on 2009-05-17
I just began learning C today (5 minutes ago) and have a question already.
My notes use gcc, and the reference book I'm using (The C Programming Language by Kernighan and Ritchie) uses cc.

I started off, beginning with the Hello World program as usual. Only, I found that the code for the Hello World program is different in my notes and different in the book. And the code for one compiles in gcc while not in cc, and vice versa.

What's the difference between gcc and cc?

Sorry if the question is incredibly stupid, it's just that in the other languages I've learned, I've never come across such an issue.

---

### Post by Nemooo on 2009-05-17
In Ubuntu (and most other Linux distributions I guess) cc *is* gcc. Try gcc --version and compare it to cc --version.

The difference between your "Hello World" examples are probably just what the main function returns. I imagine one example using **void main()** and the other **int main()** (see [http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?id=1043284376&answer=1044841143](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?id=1043284376&answer=1044841143))? Or perhaps one is using the printf function and the other one puts?

---

### Post by chuuk on 2009-05-17
Yes, you've hit it on the spot.
Very very puzzling.

---

### Post by k2t0f12d on 2009-05-17
*cc* is the name of the original UNIX c compiler command. The default c compiler for your operating system should be executable with that command. *gcc* is the GNU operating system c compiler. On GNU+Linux systems it is usual for *cc* to be a link to *gcc* so you and your scripts can use either interchangeably.

Traditionally, a c compiler that is named or linked to *cc* has to obey certain standards and respect certain command arguement interfaces in order for it to be used in this capacity.

While using GNU+Linux (like Ubuntu) consider *cc* and *gcc* to be synonyms for each other.

[COLOR="DarkRed"]PS: Like all *nix typically ends with an "x", it is also traditional for c compilers to end with "cc", eg. tcc (tiny c compiler) or icc (intel c compiler).[/COLOR]

---

### Post by chuuk on 2009-05-17
I thought I could use them interchangeably until I tried compiling this in gcc:

#include <stdio.h>
main() {
    printf("Hello World");
}

It compiled fine in cc. But not in gcc.
Why is this? In gcc I have to specify int as a return type and void as a parameter before the code compiles.

---

### Post by Martin Witte on 2009-05-17
> **k2t0f12d said:**
> 
While using GNU+Linux (like Ubuntu) consider *cc* and *gcc* to be synonyms for each other.


That is right:```

martin@toshibap200:~$ which cc
/usr/bin/cc
martin@toshibap200:~$ file /usr/bin/cc
/usr/bin/cc: symbolic link to `/etc/alternatives/cc'
martin@toshibap200:~$ file /etc/alternatives/cc
/etc/alternatives/cc: symbolic link to `/usr/bin/gcc'
martin@toshibap200:~$ which gcc
/usr/bin/gcc
```

---

### Post by k2t0f12d on 2009-05-17
> **chuuk said:**
> It compiled fine in cc. But not in gcc.
An example of this kind of divergent behavior can also be found the the Bourne Again SHell (which is the accepted GNU replacement for the traditional UNIX Bourne SHell).  In GNU+Linux *sh* is linked to bash, however; if bash is run with *sh*, it will attempt to emulate tradition Bourne SHell behavior as closely as possible.

Similarly, when run as *cc*, *gcc* emulates traditional UNIX c compiler behavior, ie. without any revised behaviors that are included in modern c compilers.

You can get your code to compile with *gcc* if the correct behavior modifiers are included (or excluded) as arguments on the command line.

[COLOR="DarkRed"]PS: I don't know what your problem is.  I compiled this```
#include <stdio.h>

main(){
printf("Hello, World!\n");
return 0;
}
```with```
cc -o hello hello.c
```*or*```
gcc -o hello hello.c
```
[/COLOR]

---

### Post by chuuk on 2009-05-17
Cheers guys, that was great, I think I've understood now.

---

### Post by chuuk on 2009-05-17
> **k2t0f12d said:**
> 
[COLOR="DarkRed"]PS: I don't know what your problem is.  I compiled this```
#include <stdio.h>

main(){
printf("Hello, World!\n");
return 0;
}
```with```
cc -o hello hello.c
```*or*```
gcc -o hello hello.c
```
[/COLOR]


cc doesn't need the return line.

---

### Post by k2t0f12d on 2009-05-17
> **chuuk said:**
> cc doesn't need the return line.

I commented out the return line and it still compiles correctly with *cc* or *gcc*.

[COLOR="DarkRed"]PS: The only difference in compiling w/o the return statement is that the program doesn't return an acceptable return value after execution.  Otherwise it compiles fine with or without a return value with either *cc* or *gcc*.[/COLOR]

:popcorn:

---

### Post by chuuk on 2009-05-17
Meh. I'm feeling stupid now. One of those "but it wasn't working five minutes ago!!" sort of problems.
Thanks for the help though.

---

### Post by k2t0f12d on 2009-05-17
> **chuuk said:**
> Meh. I'm feeling stupid now. One of those "but it wasn't working five minutes ago!!" sort of problems.
Thanks for the help though.Its nothing to feel stupid over, we all have had those moments! ):P

---

### Post by s3gf4u1t on 2011-03-08
> **chuuk said:**
> I thought I could use them interchangeably until I tried compiling this in gcc:

#include <stdio.h>
main() {
    printf("Hello World");
}

It compiled fine in cc. But not in gcc.
Why is this? In gcc I have to specify int as a return type and void as a parameter before the code compiles.
Actually your prgm got compiled but u hv just warning message, just ignore it and execute it. have  a fun!!

---

