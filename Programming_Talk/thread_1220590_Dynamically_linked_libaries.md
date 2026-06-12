---
title: "Dynamically linked libaries"
date: 2009-07-23
forum: Programming Talk
---

### Post by J05HYYY on 2009-07-23
Hello all,

I have a question:

If I compile using a dynamically linked library (which I have installed on my system). Then transfer the binary across to another computer - which doesn't have the library anymore. Will my program still run, or will the computer throw up some error about having a missing library?

I don't wanna start coding something on my machine; only to realize that I have to install the same library on every other machine my program runs on after compiling.

Cheers

---

### Post by abhilashm86 on 2009-07-23
is that binary you talking is executable?? if executable, sure it'll run on other machine, but in cases of interpreters like shell, you need a native host environment......

---

### Post by soltanis on 2009-07-23
No. If you compile your binary against a shared object (or a DLL in winspeak) library, and you transfer the binary to another computer, unless the other computer also has the same version of that library, it won't be able to run.

Link your program against the static library if you don't want to run into this problem -- it will make the executable bigger, but won't make it depend on the shared object being on every platform its installed on.

---

### Post by J05HYYY on 2009-08-26
If my program's license was proprietary, and the library's license was LGPL:


Would I have to rely on my customers obtaining the library themselves?
or
Would I be allowed to release the library with the program somehow?


(... Richard Stallman rekons you can't statically link a LGPL library.)

---

### Post by nvteighen on 2009-08-27
> **J05HYYY said:**
> If my program's license was proprietary, and the library's license was LGPL:


Would I have to rely on my customers obtaining the library themselves?
or
Would I be allowed to release the library with the program somehow?


(... Richard Stallman rekons you can't statically link a LGPL library.)


Hm... it depends... If you're developing aiming to Debian-based distros, you can create a .deb that depends on the library's package and you're fit... you'll be able to link dynamically because APT will guarrantee it works.

In the case of Red Hat-based distros, I guess that also applies.

In other cases, you may get into some legal trap... Statically linking a LGPL library forces your program to be LGPL too. And distributing them that way that they don't constitute a single work may be really difficult if not impossible... Maybe a link to where the library can be found could be considered as not distributing something, but GPLv3 Section 6 makes this unclear by allowing such a method to be used for conveying the "Corresponding Source".

---

### Post by Arndt on 2009-08-27
> **J05HYYY said:**
> Hello all,

I have a question:

If I compile using a dynamically linked library (which I have installed on my system). Then transfer the binary across to another computer - which doesn't have the library anymore. Will my program still run, or will the computer throw up some error about having a missing library?

I don't wanna start coding something on my machine; only to realize that I have to install the same library on every other machine my program runs on after compiling.

Cheers

Others answered the main question. Use 'ldd' to see whether a program uses any dynamic libraries and whether they are available.

---

