---
title: "/usr/lib/libGL.so.1 and /usr/local/lib/libGL.so.1"
date: 2009-02-16
forum: Programming Talk
---

### Post by kerryhall on 2009-02-16
For some reason, when I tried to install the latest Nvidia drivers, the installer complained about the existence of /usr/local/lib/libGL.so.1

I'm not sure why this file even exists, so I tried removing it on a temporary basis. 

It looks like that is what is getting linked when I compile OpenGL programs, but then it looks like /usr/lib/libGL.so is being used at run time. (According to ldd)

I think I probably want to link to /usr/lib/libGL.so right? How do I make sure that happens? Why is the linker even looking in /usr/local/lib/ ?

Also, with regard to Linux libraries, what's the deal with the libGL.so.x ?
Why use symbolic links? Why are there multiple entries (libGL.so.x.x.x) etc?

Thanks!

---

### Post by bruce89 on 2009-02-16
> **kerryhall said:**
> I think I probably want to link to /usr/lib/libGL.so right? How do I make sure that happens? Why is the linker even looking in /usr/local/lib/ ?

/usr/local is searched in preference to /usr so that locally installed binaries are used in preference to the originally packaged ones. This means you can compile a newer version of a package without overrwriting the original package.

> **kerryhall said:**
> Also, with regard to Linux libraries, what's the deal with the libGL.so.x ?
Why use symbolic links? Why are there multiple entries (libGL.so.x.x.x) etc?

It's an ABI thing. If the first number changes, the ABI is incompatable. AFAIK the other numbers are just for information.

See [http://en.wikipedia.org/wiki/Soname](http://en.wikipedia.org/wiki/Soname)

---

### Post by kerryhall on 2009-02-17
Thanks for the info.

I don't understand though, when I delete /usr/local/lib/libGL.so it still tries to link to that and doesn't try to link to /usr/lib/libGL.so

---

### Post by kerryhall on 2009-02-18
Bump

---

### Post by Gordon Bennett on 2009-02-19
Are you using 64-bit Linux?  There's an issue in regards to the link references to 32-bit compatibility libs; I made a post in my blog about it:

[http://mil-tdd-41p.net/?p=11](http://mil-tdd-41p.net/?p=11)

---

### Post by kerryhall on 2009-02-20
No, 32 bit. It's a 64 bit machine though.

---

