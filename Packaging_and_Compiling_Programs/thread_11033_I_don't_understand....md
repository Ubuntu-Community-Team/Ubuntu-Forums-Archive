---
title: "I don't understand..."
date: 2005-01-13
forum: Packaging and Compiling Programs
---

### Post by deception on 2005-01-13
what I'm doing wrong! 

I'm following the wiki for compiling a kernel [http://www.ubuntulinux.org/wiki/KernelCompileHowto](http://www.ubuntulinux.org/wiki/KernelCompileHowto) .

I get to this bit and theres no deb package! : 

Install

The new kernel package is located one directory up, in /usr/src.

# cd ..
# dpkg -i kernel-image-2.6.8.1_custom.1.0_i386.deb


I've followed the guide perfectly. Any ideas? BTW if it helps im running an AMD 65 3000+ .

THanks ever so much in advance, 
Matt

---

### Post by zeroK on 2005-01-13
[QUOTE=deception]what I'm doing wrong! 

I'm following the wiki for compiling a kernel [http://www.ubuntulinux.org/wiki/KernelCompileHowto](http://www.ubuntulinux.org/wiki/KernelCompileHowto) .

I get to this bit and theres no deb package! : 

Install

The new kernel package is located one directory up, in /usr/src.

# cd ..
# dpkg -i kernel-image-2.6.8.1_custom.1.0_i386.deb


I've followed the guide perfectly. Any ideas? BTW if it helps im running an AMD 65 3000+ .

THanks ever so much in advance, 
Matt[/QUOTE]
 And you've run dpkg-kpkg [...] kernel_image?

---

### Post by deception on 2005-01-13
I ran make-kpkg and got a command not found. I'm in root. I tried 

make -kpkg 

and that seemed to work.. but seems not. 

dpkg with the space or not both say command not found / option not found.

---

### Post by zeroK on 2005-01-13
[QUOTE=deception]I ran make-kpkg and got a command not found. I'm in root. I tried 

make -kpkg 

and that seemed to work.. but seems not. 

dpkg with the space or not both say command not found / option not found.[/QUOTE]
 Sorry, was a typo. I meant make-kpkg :-) It is in the "kernel-package" :-)

---

### Post by deception on 2005-01-13
I think im gonna start from scratch again, pay more attention, i must have done something wrong! Thanks for the help so far  :)

---

### Post by deception on 2005-01-13
Nope, same thing happens :(

---

### Post by digirudi on 2005-03-16
[QUOTE=deception]Nope, same thing happens :([/QUOTE]
 make-kpkg is part of the kernel-package

solution:
apt-get install kernel-package

Ruud

---

