---
title: "a C related question"
date: 2019-01-31
forum: Programming Talk
---

### Post by teage3 on 2019-01-31
Is it possible to look up C related info from terminal (man pages?) or is there a package from software center that would aid in looking up C related content? It would be nice to be able to pop open a terminal and just search for something specific like printf() formats and the like. Speaking of printf(), Is the use of printf() in bash the same as in C?

---

### Post by TheFu on 2019-02-01
[B]man man 
[/B]will show the different sections for the manpages.
```

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions eg /etc/passwd
       6   Games
       7   Miscellaneous  (including  macro  packages and conventions), e.g. man(7),
           groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]
```

Section 2 and 3 will contain functions which can be called by C and other programming languages with C binding.

To access the manpage for rmdir(), use ```
man -s 2 rmdir
```
```
man  readdir
``` will find the readdir() function in section 3 because there isn't another in section 1 or 2 which would be found first.  If you look at the header for every manpage, the section is there.

Also, you can use the **apropos** command to search the manpage summaries.  
```
$ apropos rmdir
rmdir (1)            - remove empty directories
rmdir (2)            - delete a directory

``` The specific section is there.  The *printf* search finds many more manpages than expected.

BTW, I never used printf() after the beginning C class.  It was always sprintf() to build a string for some other output call.

Many people find that having a C reference book online in a browser is faster. Just be certain that the C standard compiler you are using and the language standard level C89, C99, C11 are clearly understood.

---

### Post by SagaciousKJB on 2019-02-01
You might need to install them with 'manpages-dev'.

You can also just type 'man *function*' in Google and get the same type of manual pages.  Often times they're more up-to-date or have example codes that the Ubuntu manual files don't.

---

### Post by TheFu on 2019-02-01
man pages installed on a Unix system should 100% match the programs and libraries **installed on that system**.  With google, you don't know which version you might be seeing.  After spending a few hours trying to get something to work like the google-result said it should, checking the local manpages often shows it is a different version installed with different options, arguments.

---

### Post by SagaciousKJB on 2019-02-01
> **TheFu said:**
> man pages installed on a Unix system should 100% match the programs and libraries **installed on that system**.  With google, you don't know which version you might be seeing.  After spending a few hours trying to get something to work like the google-result said it should, checking the local manpages often shows it is a different version installed with different options, arguments.

Take a look at fgets's manual file on 16.04. Then compare it with this page...

[https://linux.die.net/man/3/fgets](https://linux.die.net/man/3/fgets)

Notice the entirety of the BUGS section missing from the Ubuntu man file. The linux.die manual file points out in no uncertain terms that fgets should not be used.

I am not saying there's a lot of examples like that, but there have been enough that I now look up the system manual file, as well as one available on Google to compare. In some instances which I can't specifically remember, there have even been entire example code sections missing from one manual file or the other despite them being for the same glibc version.

I don't know if it is merely the effect of some distirbuions having different documentation packages than others, but it seems that way. Either way these are pretty meaningful discrepancies.

---

### Post by lisati on 2019-02-01
> **SagaciousKJB said:**
> 

Notice the entirety of the BUGS section missing from the Ubuntu man file. The linux.die manual file points out in no uncertain terms that fgets should not be used.


I read the page you referred to. Unless we were looking at different versions of the page, it says not to use gets() but to use fgets() instead. Screenshot attached.

---

### Post by SagaciousKJB on 2019-02-01
> **lisati said:**
> I read the page you referred to. Unless we were looking at different versions of the page, it says not to use gets() but to use fgets() instead. Screenshot attached.

Oh whoops you're right, I goofed. But what I am saying is take a look at the difference between that page's manual file for fgets and one on a local system. On my local system at least, it doesn't mention gets() at all. I suppose that makes sense considering it's a different function, but these online sources just seem to have more information in one place whereas I would have had to look up gets() separately on my local system.

I'll see if I can remember one of the other ones I'm thinking of. Whole code examples were missing from the locally installed man pages which I was able to use from the man pages on that site.

---

