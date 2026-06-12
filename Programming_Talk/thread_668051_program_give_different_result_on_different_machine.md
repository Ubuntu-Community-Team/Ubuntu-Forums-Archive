---
title: "program give different result on different machines (both 32bit) gcc"
date: 2008-01-15
forum: Programming Talk
---

### Post by monkeyking on 2008-01-15
Hi I'm,
writing a 32bit program.
And I've got a strange problem.

If I make and run the program on one computer it will work.

But if I take my source and make it on another computer,
it will compile. But the program give different results.

The source is exactly the same.

If I take the compiled binary from one machine and copy it to the other,
the problem persist.


does anyone have any idea what could be causing the strange behavier.

The computer on which the program fails is a fresh install.
but I did a build-essential.

I've never experienced something like this before.
Anyone have any ideas?

thanks in advance

---

### Post by hardyn on 2008-01-15
the are both PCs?

or one is a PPC and one is intel?  what does the program do? are you using IO? BIOS hooks? anything that might vary machine to machine?  relying on descreet timing?

---

### Post by monkeyking on 2008-01-15
The computers are exactly same type.
both Dell 795, with excatly same configuration.
The only IO is reading a file and writing to terminal.

these are the ldd
```

ldd relateHMM
        linux-gate.so.1 =>  (0xffffe000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7e58000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e33000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7e27000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7cdd000)
        /lib/ld-linux.so.2 (0xb7f63000)


```
The non working version
```

ldd relateHMMOLDBIN 
        linux-gate.so.1 =>  (0xffffe000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7e70000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e4b000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7e3f000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7cf5000)
        /lib/ld-linux.so.2 (0xb7f7b000)

```
gcc info non working

```

gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

```
gcc info working

```

gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

```

---

### Post by Compyx on 2008-01-15
Show us your code, sounds like a typical case of UB.

---

### Post by monkeyking on 2008-01-15
Hmm, the file that spawns the problem, is a almost 3000 lines files.
And that again depends on other files.
So I don't think anyone will look through all this.

But what is the most likely cause, of this undefined bahavior?

thanks the the replys

---

### Post by Zugzwang on 2008-01-15
Here are some hints:

[LIST]
[*] If you do complex stuff with pointers, the byte order of the computer might be important (little endian/big endian)
[*] The two compilers apply different optimizations to your code, which might cause mathematical expressions to evaluate differently. This is especially true if you are using floating point arithmetic. In this case please also see this thread:[http://ubuntuforums.org/showthread.php?t=651331]("http://ubuntuforums.org/showthread.php?t=651331")
[*] Even if the floating point instructions are evaluated in the same order on both of your platforms, it is not guranteed that both round up or truncate the last digit in the same way. Normally they do, but you should never rely on this.
[*] Are you using multi-threading? In that case maybe your code isn't thread-safe.
[*] Does your application handle errors correctly? Even when doing only console I/O, you have to check the error codes. 
[/LIST]

This list is far from being complete but these are the common cause I can think of at the moment. It appear that only the last two points are applicable for your scenario. Hopefully that helps. :)

---

