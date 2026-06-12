---
title: "x86_64bit vs. amd64?"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by whein on 2008-11-12
Ok, sorry for the dumb question but...

I'm running an amd64 version of Hardy.  I'd like to install Eclipse 3.4, but no .deb packages exist for anything past 3.2 in the repos, so off to compile source code for me.  I hit up the Eclipse download site and it has two source packages, Linux 32 bit and Linux 64 bit, but the description of the 64 bit one is x86_64, not amd64.  I'd always assumed that x86_64 was the Intel 64 bit, which isn't the same.  Since these are source files (I think...  Eclipse is all java and stuff so for all I know they are class files which aren't really source or compiled) does it matter which version I download and use?  In general, do source files care which kernel it is or does all that get taken care of in the compiling stage?  Are java class files portable between 32/64 bit architectures?

-Will

---

### Post by estamand on 2008-11-12
amd64 is x86_64.   

Not 100% sure why but my guess is because amd64 also works for the intel 64 bit processors they it needed to be called something alittle more generic then amd64.

---

### Post by tuxxy on 2008-11-12
> **whein said:**
> Ok, sorry for the dumb question but...

I'm running an amd64 version of Hardy.  I'd like to install Eclipse 3.4, but no .deb packages exist for anything past 3.2 in the repos, so off to compile source code for me.  I hit up the Eclipse download site and it has two source packages, Linux 32 bit and Linux 64 bit, but the description of the 64 bit one is x86_64, not amd64.  I'd always assumed that x86_64 was the Intel 64 bit, which isn't the same.  Since these are source files (I think...  Eclipse is all java and stuff so for all I know they are class files which aren't really source or compiled) does it matter which version I download and use?  In general, do source files care which kernel it is or does all that get taken care of in the compiling stage?  Are java class files portable between 32/64 bit architectures?

-Will

Try the x86_64 .deb, it should work fine :)

---

### Post by k_aneda on 2008-12-29
AMD64, EM64T = AMD and Intel x86 with 64-bit instructions (x86_64)

INTEL64 = Intel Itanium 64

Pretty common to even see with enterprise software three directories or builds (INTEL32, INTEL64, AMD64, etc.)

---

### Post by Greyed on 2008-12-29
> **estamand said:**
> amd64 is x86_64.   

Not 100% sure why but my guess is because amd64 also works for the intel 64 bit processors they it needed to be called something alittle more generic then amd64.

AMD64 was designed by AMD.  It then became the standard 64-bit instruction set.  Since the common moniker for chips compatible back to Intel's 8086 chip is x86 and this was a continuation of this line the standard was named x86_64 bit.

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by sdennie on 2008-12-29
In the desktop world, it's generally safe to assume that anything referring to 64-bit is referring to AMD64 and not IA-64.  The Itanium instruction set is not very common and you won't often find pre-built packages for it.  Even if you did, dpkg is smart enough to tell you that you are trying to install a package for the wrong architecture.  :)

---

### Post by k_aneda on 2008-12-29
> **vor said:**
> In the desktop world, it's generally safe to assume that anything referring to 64-bit is referring to AMD64 and not IA-64.  The Itanium instruction set is not very common and you won't often find pre-built packages for it.  Even if you did, dpkg is smart enough to tell you that you are trying to install a package for the wrong architecture.  :)

Wish that was the case, one of the software packages we use at work has distinctive INTEL64, AMD64, INTEL32 directories and we get a call from sites at least twice a week asking why the INTEL64\setup.exe or ./INTEL64/install won't work correctly on their new Core2Duo desktop..

Give them an inch, and they'll take a mile.. LOL

---

### Post by sdennie on 2008-12-29
> **k_aneda said:**
> Wish that was the case, one of the software packages we use at work has distinctive INTEL64, AMD64, INTEL32 directories and we get a call from sites at least twice a week asking why the INTEL64\setup.exe or ./INTEL64/install won't work correctly on their new Core2Duo desktop..

Give them an inch, and they'll take a mile.. LOL

Haha.  The fact that you've referred to setup.exe makes me believe that you are not receiving the omniscient advice of dpkg...  ;)

---

### Post by Nepherte on 2008-12-29
Or perhaps the people they get the calls from.

---

