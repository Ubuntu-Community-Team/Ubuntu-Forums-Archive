---
title: "how to identify what version of gcc was used?"
date: 2007-08-23
forum: Programming Talk
---

### Post by kcy29581 on 2007-08-23
Hi all,

I bet this is easy...

How can identify which version of gcc compiled an application?

Thanks

---

### Post by ghostdog74 on 2007-08-23
what did the man page say.. don't be lazy. read the man page

---

### Post by kcy29581 on 2007-08-23
...

I do not have access to the man page; I'm at work and using MSYS. Google hasn't yielded anything yet either. I do not have access to my Linux PC at the moment. I'll try gcc's site now.

So, please, if you know the command, what is it?

---

### Post by ghostdog74 on 2007-08-23
> **kcy29581 said:**
> ...
Google hasn't yielded anything yet either.
its as simple as typing "how to find gcc version" in google. The first return result says it all. Now that isn't hard at  all right?

---

### Post by kcy29581 on 2007-08-23
> **ghostdog74 said:**
> its as simple as typing "how to find gcc version" in google. The first return result says it all. Now that isn't hard at  all right?

if you are talking about:```
gcc -v
``` then I implore you to read the question before answering, especially when you are "trying" to patronise people.
The question was: > How can identify which version of gcc **compiled an application**

To put it even simply for you to understand, someone compiled an application, I need to verify they used a specific version of gcc; how do I do that?

---

### Post by fct on 2007-08-23
As far as I know normally there is no information about the compiler version added to executables. You can use "ldd" to check the libraries linked, though. The command "file" also outputs some helpful info on binaries, like the architecture it was compiled for.

---

### Post by kcy29581 on 2007-08-23
> **fct said:**
> As far as I know normally there is no information about the compiler version added to executables. You can use "ldd" to check the libraries linked, though. The command "file" also outputs some helpful info on binaries, like the architecture it was compiled for.

Thanks fct.

Unfortunately neither of those two commands appear to work on MSYS. I'll have to wait until tomorrow when my Linux development PC is set up.

It's crazy though, we have to verify gcc versions for executables, but they don't tell us how. Typical work! :)

---

### Post by LaRoza on 2007-08-23
> **kcy29581 said:**
> 
It's crazy though, we have to verify gcc versions for executables, but they don't tell us how. Typical work! :)

If they don't know how, and you don't know, how will they know you're not making it up? :D

---

### Post by kcy29581 on 2007-08-23
> **LaRoza said:**
> If they don't know how, and you don't know, how will they know you're not making it up? :D

I work for a games development company, and the game we're working on will end up going to Sony, and they know how to check this! But knowing them, they'll only tell us AFTER they fail the game. :D

---

### Post by Dark Star on 2007-08-23
Have you tried 

```
aptitude show gcc
```

---

### Post by kcy29581 on 2007-08-23
> **Dark Star said:**
> Have you tried 

```
aptitude show gcc
```

I'll give that a go tomorrow, thanks.

---

### Post by LaRoza on 2007-08-23
> **kcy29581 said:**
> I work for a games development company, and the game we're working on will end up going to Sony, and they know how to check this! But knowing them, they'll only tell us AFTER they fail the game. :D

Can you recompile?

---

### Post by kcy29581 on 2007-08-23
> **LaRoza said:**
> Can you recompile?

I work on the testing side so I don't have the source code. I'm here to make sure the development teams don't screw up. If I asked them for verification, I know they'd just say "it's ok" without actually checking! :rolleyes:

---

### Post by Dark Star on 2007-08-23
> **kcy29581 said:**
> I'll give that a go tomorrow, thanks.

Plz tell :) Pleasure helping :D Hope that helps :D

---

### Post by ghostdog74 on 2007-08-23
> **kcy29581 said:**
> if you are talking about:```
gcc -v
``` then I implore you to read the question before answering, especially when you are "trying" to patronise people.
The question was: 

To put it even simply for you to understand, someone compiled an application, I need to verify they used a specific version of gcc; how do I do that?

even if its so, then change your search term ("how to determine compiler version")... here's the first result
```

strings - yourapplication | grep GCC

```
you can try that. btw, i don't patronise people. i just want them to be self sufficient.

---

### Post by kcy29581 on 2007-08-23
> **ghostdog74 said:**
> even if its so, then change your search term ("how to determine compiler version")... here's the first result
```

strings - yourapplication | grep GCC

```
you can try that. btw, i don't patronise people. i just want them to be self sufficient.

sorry ghostdog74, but the tone of your replies was very similar to all the replies I've had in the office: RTFM; if I had the manual or knew which manual had the answer then I'd be fine reading away. I try to use the forums only as a last resort.

Thanks for the suggestion, I'll give it a shot.

---

### Post by kcy29581 on 2007-08-23
SOLVED!

Thanks ghostdog74! You :guitar:

The command you suggested works like a charm!

---

### Post by Dark Star on 2007-08-23
What abt mine ? :?```
shashwat@shashwat-desktop:~$ aptitude show gcc
Package: gcc
State: installed
Automatically installed: no
Version: 4:4.1.2-1ubuntu1
Priority: optional
Section: devel
Maintainer: Ubuntu Core developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 65.5k
Depends: cpp (>= 4:4.1.2-1ubuntu1), gcc-4.1 (>= 4.1.2)
Recommends: libc6-dev | libc-dev
Suggests: make, manpages-dev, autoconf, automake1.9, libtool, flex, bison, gdb,
          gcc-doc
Conflicts: gcc-doc (< 1:2.95.3)
Provides: c-compiler
Description: The GNU C compiler
 This is the GNU C compiler, a fairly portable optimizing compiler for C. 
 
 This is a dependency package providing the default GNU C compiler.

``` This is my output :D

---

### Post by ghostdog74 on 2007-08-23
> **kcy29581 said:**
> if I had the manual or knew which manual had the answer then I'd be fine reading away. I try to use the forums only as a last resort.

first of all, glad that it worked for you. 
second, i did not give you the answer. Google did. :)

---

### Post by kcy29581 on 2007-08-23
> **ghostdog74 said:**
> first of all, glad that it worked for you. 
second, i did not give you the answer. Google did. :)

Yeah, but Google gave it via you! :)

---

### Post by nanotube on 2007-08-23
> **Dark Star said:**
> What abt mine ? :?```
shashwat@shashwat-desktop:~$ aptitude show gcc
Package: gcc
State: installed
Automatically installed: no
Version: 4:4.1.2-1ubuntu1
Priority: optional
Section: devel
Maintainer: Ubuntu Core developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 65.5k
Depends: cpp (>= 4:4.1.2-1ubuntu1), gcc-4.1 (>= 4.1.2)
Recommends: libc6-dev | libc-dev
Suggests: make, manpages-dev, autoconf, automake1.9, libtool, flex, bison, gdb,
          gcc-doc
Conflicts: gcc-doc (< 1:2.95.3)
Provides: c-compiler
Description: The GNU C compiler
 This is the GNU C compiler, a fairly portable optimizing compiler for C. 
 
 This is a dependency package providing the default GNU C compiler.

``` This is my output :D

that just shows what version of gcc is available from the repositories. that does not answer the question of what version of gcc was used to compile some particular application.

---

### Post by Lster on 2007-08-23
That looks interesting... I will try that...

---

