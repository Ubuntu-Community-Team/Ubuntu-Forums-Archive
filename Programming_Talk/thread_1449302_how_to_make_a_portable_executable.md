---
title: "how to make a portable executable?"
date: 2010-04-07
forum: Programming Talk
---

### Post by reinc2u on 2010-04-07
Hi.
for some reasons I would like to distribute small C code as an executable. Assuming I have two Ubuntu distributions, say, 9.10 and 7.10, or 8.04. If I compile the code under new Ubuntu, I can't run it on the old system. But it works other way around - compiled with old GLIBC code works on new installation. 
So, I have  a sort of solution - to keep some old box with old GLIBC, but I wonder - is it possible to find more elegant solution. 
  Thanks!

---

### Post by NathanB on 2010-04-07
> **reinc2u said:**
> Hi.
for some reasons I would like to distribute small C code as an executable. Assuming I have two Ubuntu distributions, say, 9.10 and 7.10, or 8.04. If I compile the code under new Ubuntu, I can't run it on the old system. But it works other way around - compiled with old GLIBC code works on new installation. 
So, I have  a sort of solution - to keep some old box with old GLIBC, but I wonder - is it possible to find more elegant solution. 
  Thanks!

You can try porting your project to a different implementation of Small C.  There are several:  [http://www.cpm.z80.de/small_c.html](http://www.cpm.z80.de/small_c.html)

Hope that helps!

---

### Post by davec64 on 2010-04-07
Hi reinc2u,

First off I'm not a programmer, but your question got me interested so I thought I would see what I could find!

Thinking about this logically, when you compile on older versions and then execute on a newer version it appears backwards compatibility is coming into play. (Sorry if thats staing the obvious! :))
Therfore when you compile on the newer version references are probably being made to newer libraries than the older versions have.
Assuming you can identify the libraires etc in question (that the compiler/programme is referencing), what about including the necessary libraries as part of the programme?

Hopefully this link might make more sense to you!

[http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html]("http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html")

Just thought I'd try and help, so if this all a load of rubbish, sorry!  :)

---

### Post by wmcbrine on 2010-04-07
You can do a statically-linked build, but I don't recommend it -- it makes the binary huge.

---

### Post by davec64 on 2010-04-07
> **wmcbrine said:**
> You can do a statically-linked build, but I don't recommend it -- it makes the binary huge.

Thanks wmcbrine, that sounds like what I found but put nice and simply in 1 line!  :)

---

### Post by reinc2u on 2010-04-07
I don't think that a static bind of GLIBC is a good solution. 

The best idea I have so far:
- install GLIBC 2.3 (or even earlier)
- link against it.

What I am really dreaming about - is to have an option during compilation/linking: please, use portable part of GLIBC!! But more I am looking at the problem, more I convinced that this is just a dream.

---

### Post by Npl on 2010-04-07
> **wmcbrine said:**
> You can do a statically-linked build, but I don't recommend it -- it makes the binary huge.And apart from that you must honour the LGPL should you distribute the result - ie provide object-files or sources.
So if you dont want to do that or want to depend on a compatible glibc being installed everywhere, you gonna have to write your own C library routines(which is the best solution if you want your binary to run everywhere, for example the nvidia-drivers have their own memcopy and string-routines)

---

### Post by reinc2u on 2010-04-08
solution (partial, but still) is found at: [http://freegamedev.net/wiki/Portable_binaries](http://freegamedev.net/wiki/Portable_binaries)
  Thanks.

---

### Post by Cracauer on 2010-04-10
Static binaries used to be the way to go for this but not anymore. These days you get broken earlier by somebody messing with the memory layout or whatever and breaking a static binary than getting broken by lack of backward compatibility in libc.

If you have to rely on this I would build on an old libc version OS, and then ship it with all libraries needed and even a full chroot. So the customer can try running the binary, if the binary doesn't work outright use the included libs and if that doesn't work you use the chroot (pain, though).

---

