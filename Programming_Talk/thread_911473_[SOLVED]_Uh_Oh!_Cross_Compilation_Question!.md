---
title: "[SOLVED] Uh Oh! Cross Compilation Question!"
date: 2008-09-05
forum: Programming Talk
---

### Post by matburton on 2008-09-05
I have a Wii and, since I'm addicted to fiddling with technology, I got Linux going on it as described [[COLOR="Blue"]here[/COLOR]]("http://wiibrew.org/wiki/Wii_Linux").

I figured it would be fun to write a few little projects for it since it could act as an underpowered server (at somewhere between 13 and 18 Watts but with very little RAM).

Since it's so underpowered, compiling anything on it would be painful.

Since the Wii has a PPC processor if I wanted to compile any C++ stuff I'd have to cross compile on my x86 ubuntu machine, targeted for the PPC.

So I installed these packages: ppu-binutils, ppu-g++, ppu-gcc, ppu-sysroot, ppu-sysroot64 and wrote this boring program:

```
int main()
{
   return 0;
}
```

Tried building and running it with g++ first and it worked lol.

Then I tried building it with:
```
ppu-g++ main.cpp
```
and copied a.out to my Wii and (drum roll) when I run it I get a segfault :(

I'm a bit confused as to what I'm doing wrong. The Debian version the Wii is using seems to be able to use programs from the Debian PPC repository without any problems.

I guess I'm just not building with the right flags for the architecture, but I have no idea what the right flags to change would be... I've been fiddling with -mcpu, -mtune for a while but with no luck.

Any suggestions?

---

### Post by matburton on 2008-09-06
Doh :mad: I've been an idiot and not read the package descriptions properly.
The ppu packages I installed are for the PS3's cell processor.

For anyone wanting to do the same in the future:
1. I used the powerpc-750 scripts from [[COLOR="Blue"]crosstool[/COLOR]]("http://www.kegel.com/crosstool/") since the 750 is the closest match to the Wii's CPU.
2. I applied the patch as described in [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=532052") post by peiworld.

So there were no pre-built cross tools I could use, but using the scripts was painless anyway :)

---

### Post by WW on 2008-09-06
Thanks for answering your own post! :)  Since I hope to experiment with this type of cross-compiling (some day), I appreciate it.

---

