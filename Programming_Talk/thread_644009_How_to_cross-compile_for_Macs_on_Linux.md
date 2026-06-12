---
title: "How to cross-compile for Macs on Linux?"
date: 2007-12-18
forum: Programming Talk
---

### Post by Vadi on 2007-12-18
Hi all,

I have a relatively small C program that currently runs on Linux (built with gcc) and Windows (mingw). I need it to run on Macs too though (I have some mac users bugging me).

I've never used/owned a mac, so that's a bit of a problem in itself. Nor can I afford a copy of OS X to virtualize (I heard though that'll be illegal anyhow). So, cross-compiling is my only option, as I understand.

I looked about the internet, and saw this page ([click]("http://www.mac.linux-m68k.org/docs/cross-dev.php")), but they compiler they use there is really old, gcc 2. Then there's also a page here ([click]("http://www.kegel.com/crosstool/crosstool-0.43/doc/crosstool-howto.html#quick")), but when compiling the powerpc compiler, it makes an error when auto-generating a file (misses two quotes at the end) and just quits. I tried correcting the file, but it simply erases it at start.

So, right now, I'm completely lost and confused as to what can I do. Like this smiley - :confused:.

Can anyone help please?

---

### Post by H264 on 2007-12-18
or you could ask somebody really nicely that does have a mac to compile it on... ;)
(hint: I happen to have a mac)

does it use a special library only found on linux? If so it could be a problem. If not then it's really simple to compile, OSX uses GCC just like everybody else (except windows - but we don't care anyway)

---

### Post by Vadi on 2007-12-18
Yeah that's what I'm leaning on. I got a clueless, but nice mac person. We figured out how to open the mac terminal so far and navigate within in it, heh.

No, I don't believe it uses any special libraries. The ones used are unistd.h, string.h, ctype.h, stdio.h, stdlib.h, errno.h, arpa/telnet.h, stdarg.h, signal.h, time.h, sys/stat.h, fcntl.h, sys/socket.h, sys/time.h, netdb.h, netinet/in.h, arpa/inet.h, dlfcn.h, and zlib.h. That's about it.

How can you get gcc installed in osx though? Bash says it doesn't recognize "make". And the cheat code of "sudo apt-get install build-essential" probably won't work :(

---

### Post by H264 on 2007-12-18
haha, no... it's not quite as fun installing programs as apt... 

I believe you need to either get gcc from the apple website or from the apple DVD that came with the mac... once it is installed you can compile it the same way as any other *nix box with gcc

Where is the code? Does the program need to run on PowerPC based macs too?

---

### Post by Vadi on 2007-12-18
Yeah, need it on powerpc too. The code it on my laptop ;)

I've tried a whole bunch of tutorials on making compiling the compiler, but no luck so far :/

---

### Post by H264 on 2007-12-18
good thing I happen to have a PowerPC mac too ;)
although it does not have OSX on it anymore - so that won't work :(

I should be able to compile for PowerPC mac with the newer Xcode though... never tried it - it should be easy, so I'v read.

---

### Post by sloggerkhan on 2007-12-18
How about having them run ubuntu in a virtual machine?

---

### Post by Auria on 2007-12-18
> **sloggerkhan said:**
> How about having them run ubuntu in a virtual machine?

hmm can't people just stop the OS flame war and just help the original poster by answering his question...

> 
I've tried a whole bunch of tutorials on making compiling the compiler, but no luck so far :/

What errors do you get? Usually you just need to install "developer tools" from the install DVD and then you can use gcc/g++ from terminal almost exactly like on linux.

---

### Post by Vadi on 2007-12-18
As far as I know, it's illegal to virtualize OS X on non-mac hardware. And I don't have a CD of OS X to begin with.

Auria: That's the problem, I don't have a mac. I did find a willing mac user though; and I'll get her to install xcode. After that though, will make work from the terminal like it does for me (with the same makefile?)

---

### Post by jespdj on 2007-12-19
> **Vadi said:**
> As far as I know, it's illegal to virtualize OS X on non-mac hardware. And I don't have a CD of OS X to begin with.
sloggerkhan meant that you ask your users to run Ubuntu on their Macs in a virtual machine... I guess that's not a real option for you.

---

### Post by Vadi on 2007-12-19
Hmm as far as I know, installing Ubuntu on a powerpc is a pain in the behind now. I got one mac user to try it a long while ago, only to find out powerpc isn't supported anymore, and there aren't real any good guides on it either.

---

