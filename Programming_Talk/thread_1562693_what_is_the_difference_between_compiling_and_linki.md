---
title: "what is the difference between compiling and linking"
date: 2010-08-28
forum: Programming Talk
---

### Post by jamesbon on 2010-08-28
I am not a computer science grad.So not clear as what should I be searching for.
I want to know what is the difference between compiling and linking?
I am referring to C programs.

---

### Post by worksofcraft on 2010-08-28
The compiler turns your C code into instructions that the processor must execute but you can make a program out of multiple modules. 
So the compiler doesn't know where in memory the things in other modules will be.

The linker takes all the modules and gives them a place in memory then it finds all the references from one module to another and pokes the address that it has allocated in there so that the program can run.

Modules are often stored in library files, like if you call a function from the standard C library, then the linker copies the appropriate module out of that library to combine it with your code and make an executable binary.

There are also shared object libraries. In Windows they are called dynamic link libraries, because it was very inefficient to copy common code into every program that uses it. A shared library is linked each when you run a program. That way many programs can share the same copy of the code in memory.

---

### Post by lisati on 2010-08-28
As worksofcraft, compiling translates your program into a form the computer can understand, and linking brings all the necessary parts together to form a complete program.

---

### Post by jamesbon on 2010-08-28
> **worksofcraft said:**
> 
The linker takes all the modules and gives them a place in memory then it finds all the references from one module to another and pokes the address that it has allocated in there so that the program can run.
Does that mean if I have a program which is using several modules then all of them would be loaded in memory i.e. RAM of my computer?
> **worksofcraft said:**
> 
Modules are often stored in library files, like if you call a function from the standard C library, then the linker copies the appropriate module out of that library to combine it with your code and make an executable binary.

I am not clear with this part.You mean to say the module which is being used by the program from the standard C library that would be called and loaded in memory.
For example if I have to do a mathematical calculation and then load a module which can do so then if the linker does not know where the module is the program can not be compiled.
> **worksofcraft said:**
> 
There are also shared object libraries. In Windows they are called dynamic link libraries, because it was very inefficient to copy common code into every program that uses it. 
Why was that inefficient.

---

### Post by MadCow108 on 2010-08-28
> **jamesbon said:**
> Does that mean if I have a program which is using several modules then all of them would be loaded in memory i.e. RAM of my computer?
yes this can be very wasteful on ram several programs link statically with the same library.
So there are dynamically linked libraries (shared libraries) where only one instance of the library is in ram which is shared by all processes which need it.
This saves ram for common stuff like libc.

you can see which shared libraries a program uses with *ldd executable-name*

---

### Post by jamesbon on 2010-08-28
Hmm that is really interesting information.
I did an 
```
ldd firefox ldd: 
./firefox: No such file or directory
```

---

### Post by Bachstelze on 2010-08-28
> **jamesbon said:**
> Hmm that is really interesting information.
I did an 
```
ldd firefox ldd: 
./firefox: No such file or directory
```

You must use the full path.  You can use the [font=monospace]which[/font] command to get the full path of a file in your PATH:

```
firas@itsuki ~ % ldd `which firefox`
        not a dynamic executable

```

Except that firefox is a bad example because /usr/bin/firefox is actually just a symlink to a wrapper shell script:

```
firas@itsuki ~ % file `which firefox`
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'

```

The real executable is

```

firas@itsuki ~ % ldd /usr/lib/firefox-3.6.8/firefox-bin
        linux-gate.so.1 =>  (0x00b04000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00110000)
        libxul.so => not found
        libmozjs.so => not found
        libxpcom.so => not found
        libplds4.so => /usr/lib/libplds4.so (0x00772000)
        libplc4.so => /usr/lib/libplc4.so (0x00fb3000)
        libnspr4.so => /usr/lib/libnspr4.so (0x00128000)
        libdl.so.2 => /lib/libdl.so.2 (0x003f1000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00fb8000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00279000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00c01000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x0015d000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x007e5000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00a1a000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x005a7000)
        libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x0090d000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x001d3000)
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00cd2000)
        libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0x00474000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00216000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00728000)
        libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x0093c000)
        librt.so.1 => /lib/librt.so.1 (0x00642000)
        libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x00295000)
        libstartup-notification-1.so.0 => /usr/lib/libstartup-notification-1.so.0 (0x00750000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00d4c000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0x0064b000)
        libm.so.6 => /lib/libm.so.6 (0x0035f000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00815000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00255000)
        libc.so.6 => /lib/libc.so.6 (0x0c928000)
        /lib/ld-linux.so.2 (0x00ca4000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x00559000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00385000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00274000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0x0060c000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x0038f000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00397000)
        libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x003a1000)
        libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00c54000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x003a5000)
        libz.so.1 => /lib/libz.so.1 (0x003ab000)
        libexpat.so.1 => /lib/libexpat.so.1 (0x00b25000)
        libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x003f5000)
        libdirectfb-1.2.so.0 => /usr/lib/libdirectfb-1.2.so.0 (0x00f34000)
        libfusion-1.2.so.0 => /usr/lib/libfusion-1.2.so.0 (0x00ace000)
        libdirect-1.2.so.0 => /usr/lib/libdirect-1.2.so.0 (0x00bcd000)
        libpng12.so.0 => /lib/libpng12.so.0 (0x009ea000)
        libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0x00746000)
        libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0x00ef4000)
        libxcb.so.1 => /usr/lib/libxcb.so.1 (0x003c0000)
        libpcre.so.3 => /lib/libpcre.so.3 (0x007a5000)
        libresolv.so.2 => /lib/libresolv.so.2 (0x003da000)
        libselinux.so.1 => /lib/libselinux.so.1 (0x0044f000)
        libxcb-aux.so.0 => /usr/lib/libxcb-aux.so.0 (0x0046a000)
        libxcb-event.so.1 => /usr/lib/libxcb-event.so.1 (0x0046e000)
        libxcb-atom.so.1 => /usr/lib/libxcb-atom.so.1 (0x00fac000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0x00512000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0x0051b000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00534000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00538000)
        libuuid.so.1 => /lib/libuuid.so.1 (0x00afb000)
```

---

### Post by James78 on 2010-08-28
> **jamesbon said:**
> Hmm that is really interesting information.
I did an 
```
ldd firefox ldd: 
./firefox: No such file or directory
```

Edit: Ha, Bachstelze beat me too it.

It's looking for Firefox in the current working directory, however firefox has a different location. The only reason you can call 'firefox' without any directory information in the commandline is because 'firefox' is in the ENV.

This would technically work:
```
ldd `which firefox`
```

However if you notice, it returns:
```
        not a dynamic executable
```

This is because 'firefox' is a symbolic link to a shell script, so try this instead:

```
sudo updatedb
ldd `locate firefox-bin`
```

---

### Post by MadCow108 on 2010-08-28
if you are interested in details of the linking process I can recommend these 20 page notes on linking by Ian Lance Taylor (author of the gold ELF linker):
[http://www.airs.com/blog/archives/38](http://www.airs.com/blog/archives/38)

---

### Post by jamesbon on 2010-08-28
Madcow on the link you gave following words 
> An assembler is used to turn this assembly code into an *object file*. What is an object file?
Why is it actually needed?
What I understand from your link is that gcc has an assembler inbuilt.Is that correct?

I am having one more doubt with respect to this problem
[http://gcc.gnu.org/onlinedocs/gcc-4.1.1/gcc/Inline.html](http://gcc.gnu.org/onlinedocs/gcc-4.1.1/gcc/Inline.html)

note the last sentence of that doc
> 
               GCC does not inline any functions when not optimizing
unless you specify the `always_inline' attribute for the function,
like this:The use of word static inline in  functions written in timer.c  will make sense only when gcc is used with optimization enabled. So if this is the case then when some one is compiling his linux kernel. Is  by default optimization enabled  in gcc in that or Makefiles take care of this.
What is the default behavior of gcc? 
Is it always in optimized mode or we have to do it manually?

> **Bachstelze said:**
> 


```

firas@itsuki ~ % ldd /usr/lib/firefox-3.6.8/firefox-bin
        linux-gate.so.1 =>  (0x00b04000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00110000)
        libxul.so => not found
        libmozjs.so => not found
        libxpcom.so => not found
        libplds4.so => /usr/lib/libplds4.so (0x00772000)
        libplc4.so => /usr/lib/libplc4.so (0x00fb3000)
        libnspr4.so => /usr/lib/libnspr4.so (0x00128000)
        libdl.so.2 => /lib/libdl.so.2 (0x003f1000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00fb8000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00279000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00c01000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x0015d000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x007e5000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00a1a000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x005a7000)
        libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x0090d000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x001d3000)
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00cd2000)
        libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0x00474000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00216000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00728000)
        libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x0093c000)
        librt.so.1 => /lib/librt.so.1 (0x00642000)
        libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x00295000)
        libstartup-notification-1.so.0 => /usr/lib/libstartup-notification-1.so.0 (0x00750000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00d4c000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0x0064b000)
        libm.so.6 => /lib/libm.so.6 (0x0035f000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00815000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00255000)
        libc.so.6 => /lib/libc.so.6 (0x0c928000)
        /lib/ld-linux.so.2 (0x00ca4000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x00559000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00385000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00274000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0x0060c000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x0038f000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00397000)
        libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x003a1000)
        libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00c54000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x003a5000)
        libz.so.1 => /lib/libz.so.1 (0x003ab000)
        libexpat.so.1 => /lib/libexpat.so.1 (0x00b25000)
        libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x003f5000)
        libdirectfb-1.2.so.0 => /usr/lib/libdirectfb-1.2.so.0 (0x00f34000)
        libfusion-1.2.so.0 => /usr/lib/libfusion-1.2.so.0 (0x00ace000)
        libdirect-1.2.so.0 => /usr/lib/libdirect-1.2.so.0 (0x00bcd000)
        libpng12.so.0 => /lib/libpng12.so.0 (0x009ea000)
        libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0x00746000)
        libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0x00ef4000)
        libxcb.so.1 => /usr/lib/libxcb.so.1 (0x003c0000)
        libpcre.so.3 => /lib/libpcre.so.3 (0x007a5000)
        libresolv.so.2 => /lib/libresolv.so.2 (0x003da000)
        libselinux.so.1 => /lib/libselinux.so.1 (0x0044f000)
        libxcb-aux.so.0 => /usr/lib/libxcb-aux.so.0 (0x0046a000)
        libxcb-event.so.1 => /usr/lib/libxcb-event.so.1 (0x0046e000)
        libxcb-atom.so.1 => /usr/lib/libxcb-atom.so.1 (0x00fac000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0x00512000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0x0051b000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00534000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00538000)
        libuuid.so.1 => /lib/libuuid.so.1 (0x00afb000)
```

Are the above symlinks referring to libraries loaded while linking what are the above numbers like 0x00afb000

---

### Post by MadCow108 on 2010-08-28
by default gcc does not optimize.
You can enable it with the  -O flag
[http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html)

when compiling projects the makefile is usually set up to compile with -O2 but that can be overridden by the user by setting CFLAGS/CXXFLAGS variable (mostly at least)

the hexadecimal number is should be the address of the entry point to the library which is randomized in default kernel setup to prevent certain exploits (e.g. return to libc).
For more information read the blog I posted

---

### Post by Bachstelze on 2010-08-28
> **jamesbon said:**
> 
note the last sentence of that doc
The use of word static inline in  functions written in timer.c  will make sense only when gcc is used with optimization enabled. So if this is the case then when some one is compiling his linux kernel. Is  by default optimization enabled  in gcc in that or Makefiles take care of this.
What is the default behavior of gcc? 
Is it always in optimized mode or we have to do it manually?


The default is -O0, no optimisations:

```
firas@aoba ~ % gcc -m32 -S -O2 -o fact.O2.s fact.c
firas@aoba ~ % gcc -m32 -S -O1 -o fact.O1.s fact.c
firas@aoba ~ % gcc -m32 -S -O0 -o fact.O0.s fact.c
firas@aoba ~ % gcc -m32 -S fact.c                 
firas@aoba ~ % diff fact.s fact.O2.s
1a2
> 	.align 4,0x90
6,18d6
< 	subl	$24, %esp
< 	movl	$1, -16(%ebp)
< 	movl	$1, -12(%ebp)
< 	jmp	L2
< L3:
< 	movl	-16(%ebp), %eax
< 	imull	-12(%ebp), %eax
< 	movl	%eax, -16(%ebp)
< 	incl	-12(%ebp)
< L2:
< 	movl	-12(%ebp), %eax
< 	cmpl	8(%ebp), %eax
< 	jle	L3
firas@aoba ~ % diff fact.s fact.O1.s
6,18d5
< 	subl	$24, %esp
< 	movl	$1, -16(%ebp)
< 	movl	$1, -12(%ebp)
< 	jmp	L2
< L3:
< 	movl	-16(%ebp), %eax
< 	imull	-12(%ebp), %eax
< 	movl	%eax, -16(%ebp)
< 	incl	-12(%ebp)
< L2:
< 	movl	-12(%ebp), %eax
< 	cmpl	8(%ebp), %eax
< 	jle	L3
19a7,14
> 	testl	%eax, %eax
> 	jle	L2
> 	movl	$1, %edx
> L4:
> 	incl	%edx
> 	cmpl	%edx, %eax
> 	jge	L4
> L2:
firas@aoba ~ % diff fact.s fact.O0.s
firas@aoba ~ % 

```

A Makefile can of course override this.

> Are the above symlinks referring to libraries loaded while linking what are the above numbers like 0x00afb000

It depends what you mean by "loaded" and "linking". ;)  They are loaded in memory when you run the program, by the runtime linker (ld.so).  The "numbers" are the addresses in virtual memory where the library is located.

---

### Post by jamesbon on 2010-08-28
> **Bachstelze said:**
> The default is -O0, no optimisations:

```
firas@aoba ~ % gcc -m32 -S -O2 -o fact.O2.s fact.c
firas@aoba ~ % gcc -m32 -S -O1 -o fact.O1.s fact.c
firas@aoba ~ % gcc -m32 -S -O0 -o fact.O0.s fact.c

```
I could not understand the -m32 above 
I did a man gcc and searched for /-m32

following is what I got 
> 
  -m32
       -m64
           Generate code for a 32-bit or 64-bit environment.  The 32-bit environment sets int, long and pointer to 32 bits.  The 64-bit environment sets int to 32
           bits and long and pointer to 64 bits.
In fact the way you used above gcc -m32 -S -O1 -o is not clear to me.

> **Bachstelze said:**
> 
firas@aoba ~ % gcc -m32 -S fact.c                 
firas@aoba ~ % diff fact.s fact.O2.s
1a2
>     .align 4,0x90
6,18d6
<     subl    $24, %esp
<     movl    $1, -16(%ebp)
<     movl    $1, -12(%ebp)
<     jmp    L2
< L3:
<     movl    -16(%ebp), %eax
<     imull    -12(%ebp), %eax
<     movl    %eax, -16(%ebp)
<     incl    -12(%ebp)
< L2:
<     movl    -12(%ebp), %eax
<     cmpl    8(%ebp), %eax
<     jle    L3
firas@aoba ~ % diff fact.s fact.O1.s
6,18d5
<     subl    $24, %esp
<     movl    $1, -16(%ebp)
<     movl    $1, -12(%ebp)
<     jmp    L2
< L3:
<     movl    -16(%ebp), %eax
<     imull    -12(%ebp), %eax
<     movl    %eax, -16(%ebp)
<     incl    -12(%ebp)
< L2:
<     movl    -12(%ebp), %eax
<     cmpl    8(%ebp), %eax
<     jle    L3
19a7,14
>     testl    %eax, %eax
>     jle    L2
>     movl    $1, %edx
> L4:
>     incl    %edx
>     cmpl    %edx, %eax
>     jge    L4
> L2:
firas@aoba ~ % diff fact.s fact.O0.s
firas@aoba ~ % 

What was to be observed in above?

> **Bachstelze said:**
> 
It depends what you mean by "loaded" and "linking". ;)  

Not clear with this part.

---

### Post by lisati on 2010-08-28
> **jamesbon said:**
> Madcow on the link you gave following words 
What is an object file?
Why is it actually needed?


You might want to think of it as an intermediate form of the program. The compiler has done its stuff, calling in an assembler as needed, and produced a binary "machine code" file that resembles what the computer actually runs. 

Why it is needed isn't always obvious to beginners - it threw me off the first time I encountered the idea. Chances are you'll need to combine the output from the compiler with other modules, using a linker. If you're working on anything more complex than a simple "Hello World" program, it's sometimes easier to compile different parts of the program separately, which, amongst other things, lets you do a short compilation of the part of the program that has changed instead of doing a long compilation of the whole program.

---

### Post by Bachstelze on 2010-08-28
> **jamesbon said:**
> I could not understand the -m32 above 
I did a man gcc and searched for /-m32

Used to generate IA32 (x86) assembly, as opposed to x86-64. x86-64 adds a lot of complexity, that only gets into the way when you're trying to figure out the basic concepts.

> In fact the way you used above gcc -m32 -S -O1 -o is not clear to me.

-m32: work in 32-bit mode
-S: only generate assembly code, do not assemble or link.
-O1: optimisation level 1
-o: output file

> What was to be observed in above?

That the assembly code generated without the -O flag is the same as with -O0 (indicated by the fact that diff on the two files gave no output), illustrating that -O0 is indeed the default.

---

### Post by jamesbon on 2010-08-28
Thanks for making it all clear.

---

