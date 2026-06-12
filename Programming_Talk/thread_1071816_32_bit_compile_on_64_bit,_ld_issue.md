---
title: "32 bit compile on 64 bit, ld issue"
date: 2009-02-16
forum: Programming Talk
---

### Post by addmoreice on 2009-02-16
ok I'm compiling my 32 bit program on my 64 bit machine.

I *was* doing this in a virtual machine 32 bit environment but I'm tired of testing my kernel in Bochs IN another virtual machine.

So i used the -m32 switch for gcc and everything is working well there (I'm not using any standard library I'm turning all the pre-main stub stuff that is used to set up for a specific os work off etc etc etc).

So gcc _is_ working, I'm getting i386 object files. now over to ld, why am i using ld? because i'm also using nasm and a custom object generator tool from a custom language. _all_ object files are being outputted correctly, and link perfectly within the 32 bit environment.

when i switch to the 64 bit environment ld is not linking them together into an elf file. i've specified elf32_i386 as the output format with the 

```


--oformat=elf32-i386


```

flag but ld just seems to be ignoring it. any hints?

gcc is using these flags. 

```

-c -m32 -nostdlib -nostdinc -fno-builtin -fno-stack-protector -Wall -Wextra -Werror -nostartfiles -nodefaultlibs

```

Just to stem off the 'are you sure your compiling to 32bit and not using standard libraries' questions.


the ld error i get is:

```


ld: i386 architecture of input file `x' is incompatible with i386:x86-64 output


```

where x is every object file.

I'm even using the highest error level because I'm a masochist ](*,)


thank you for any suggestions or links to where i could possibly resolve this.
I have a feeling I'm just doing something very silly.

---

### Post by addmoreice on 2009-02-17
SOLVED!

ok the issue is that the newest version of ld uses -melf_i386 flag to indicate file output type....even though this is not apparently mentioned in the manual (i found it in some obscure Japanese forum on using ld, ugg!)

my kernel now compiles. i now have bochs related issues to solve before i can confirm that everything worked (but it looks like it worked!)

---

### Post by trapgate on 2009-04-03
Thanks for posting this - you saved me a whole bunch of searching. :-)

---

### Post by Frank Kotler on 2009-04-04
In my (32-bit) "man ld", this does get a mention. Easy to miss, because it refers to "-memulation" - which doesn't jump out as what we're looking for. Seems that "ld -V" is supposed to give a list of supported "emulations". So it does! We're learning!

Best,
Frank

---

### Post by michael_young on 2010-04-14
Thanks guys.
Saved my ***.
I am the principal developer for [http://www.streetperfect.com](http://www.streetperfect.com)
Address accuracy software running on multiple platforms.
We have been getting requests for a 64 bit client on Redhat Linux.
The Redhat I'm using did it without me asking. 
HOWEVER
I needed to maintain everything else as 32 bit.
I was pulling my hair out.
How the hell do you link it. gcc -m32 was trivial.
ld was a nightmare.
-m(emulation) was not obvious.

THANKS

---

### Post by jitsun7 on 2011-07-28
Thanks so much you saved me many hours of searching!

---

