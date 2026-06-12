---
title: "NASM question: io.mac"
date: 2008-12-12
forum: Programming Talk
---

### Post by MaindotC on 2008-12-12
I'm reading the Guide to Programming Assembly in Linux and it gives a sample program that I want to assemble and link and run, but I keep getting this error:
```

amd64@amd64-desktop:~$ nasm -f elf sample.asm 
sample.asm:2: fatal: unable to open include file `io.mac'

```

The statement in the source, which I believe is called a directive, says:
```

%include "io.mac"

```

I couldn't find any files on my system called io.mac.  Where should it be located and where could I get it?  Thanks!

---

### Post by Zugzwang on 2008-12-12
This is no standard file but rather looks like something the author(s) write/wrote themselves (By using the preview function of Amazon, I've discovered that there's a note on than on page 154). So it should be stated somewhere in the book where to get it. Maybe it is on the DVD included with the book?

---

### Post by MaindotC on 2008-12-12
Ah, you're right! It didn't include a .deb installer because it is for Fedora so I just installed nasm from the repos.  I'm assuming once I get the io.mac (or any other libraries) it doesn't matter where I put them just as long as I put the absolute path in the directive, right?  Are the %include files called libraries?  Thanks for pointing this out to me.  No wonder google wasn't turning up anything!

---

### Post by MaindotC on 2008-12-12
```

amd64@amd64-desktop:~/source_linux_nasm/Linux_IOfiles$ ld -s -o sample sample.o io.o 
ld: i386 architecture of input file `sample.o' is incompatible with i386:x86-64 output
ld: i386 architecture of input file `io.o' is incompatible with i386:x86-64 output
amd64@amd64-desktop:~/source_linux_nasm/Linux_IOfiles$

```

I neglected to consider the fact that I'm using a 64-bit processor and o/s...

Edit:  I found [this thread on Fedora Forum](http://forums.fedoraforum.org/showthread.php?t=204194) that suggested:
> 
nasm -f elf32 sample.asm -l sample.lst

to link it I used

ld -m elf_i386 -o test sample.o io.o


It linked and I executed it properly.  Thanks for pointing me in the right direction :D

---

### Post by dave2008713 on 2011-03-11
Thanks! That works for me!

---

