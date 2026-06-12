---
title: "Using a .so file (c++):?:"
date: 2006-01-27
forum: Programming Talk
---

### Post by bartbes on 2006-01-27
I want to use a .so (shared object/library) file in my program, one you have outside of your program and can be changed whenever you want. Does anyone knows how to do this?

---

### Post by toojays on 2006-01-27
Do you mean that you want to use someone elses shared library, or that you want to make your own shared library? If it's someone elses library, and it's installed properly in Ubuntu, you just need to give gcc the correct include path and pass the -lsomelibrary flag when you link.

---

### Post by bartbes on 2006-01-28
It's my own and I want to be able to **[SIZE="2"]REPLACE**[/SIZE] it when I want to make a different program out of it

---

### Post by David Marrs on 2006-01-28
You need to use libtool to generate the config file, but I've never built one from scratch before; I've just stripped the code out of other people's. :d Google found this [ebook](http://www.fifi.org/doc/autobook/html/autobook.html), which might help you.

Whoops, no you don't. That's for library objects, not shared objects.

---

### Post by LordHunter317 on 2006-01-28
I'm confused by waht you want to do.

If you want the ability to arbitrarily replace your .so with another, you have to code your .so and the replacement one very carefully in order for that to work.  They must be in perfect API and ABI compatibilty, or it will not work.

More details, please.

---

### Post by bartbes on 2006-01-28
I want to use the .so file for a function, say I have a program to read files and in different so files I have the function for different file types.. like libdoc.so for docfiles etc. something like that (hope you understand)
But I already have the so file it's just how to get it into my program now

---

### Post by toojays on 2006-01-28
If you already know how to make the so file, you can either pass it to your linker command line, or use dlopen() and friends to load the library and use it.

Have a look at the [Shared Libraries howto](http://www.tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html"), but don't take it as gospel---last time I tried using this, I had to do things a bit differently . . . but this doc did at least suggest which llinker options I needed to look at.

---

### Post by LordHunter317 on 2006-01-28
My point was, putting functions in a shared library doesn't mean you can just swap in another abritrary shared library that provides the same functions.  At anyrate, to do dynamical linking, read the GCC manual.

---

### Post by toojays on 2006-01-28
[QUOTE=LordHunter317]My point was, putting functions in a shared library doesn't mean you can just swap in another abritrary shared library that provides the same functions.[/QUOTE]
Actually, it does mean that, if that's what you want it to mean. ;)

It requires bit of up-front design work to structure things though, if you want to do this with C++ classes and not just C functions.

---

### Post by LordHunter317 on 2006-01-28
It requires more than that, you can't arbitrarly add virtual functions to existing classes and such or you'll break ABI compatibility.

There's a host of other issues, too.

If the documentation is still up, the Trolltech guys have some *excellent* documentation on how to maintain C++ ABI compatability and workarounds to avoid breaking it.

---

### Post by asimon on 2006-01-28
[QUOTE=LordHunter317]If the documentation is still up, the Trolltech guys have some *excellent* documentation on how to maintain C++ ABI compatability and workarounds to avoid breaking it.[/QUOTE]
Do you mean by any chance [Binary Compatibility Issues With C++](http://developer.kde.org/documentation/other/binarycompatibility.html)? Anyway, a good reading for C++ developers.

---

### Post by LordHunter317 on 2006-01-28
Yes, I do, and that's just the tip of the iceberg, as it doesn't cover template considerations.

---

### Post by toojays on 2006-01-28
[QUOTE=LordHunter317]It requires more than that, you can't arbitrarly add virtual functions to existing classes and such or you'll break ABI compatibility.[/QUOTE]

Aye, but that's not what we were talking about, which was swapping shared libraries with the same functions. I was assuming that the interfaces would be the same.

---

### Post by bartbes on 2006-01-29
I done it with this site [http://tldp.org/HOWTO/C++-dlopen/index.html](http://tldp.org/HOWTO/C++-dlopen/index.html) and it worked! :D I finally got my program working! Thanks for helping\\:D/

---

### Post by bartbes on 2006-02-11
I made an, well I think I have to call it a header.. Just include it in your file and use the command ```
libloader(*absolute path, called function*) and in the file you are going to compile to a .so file put this in front of the function you're going to call (without single-quotes): 'extern "C"'
eg. [code]
extern "C" int main() {
*code*
}

```

EDIT: forgot to post it.. here it is

---

