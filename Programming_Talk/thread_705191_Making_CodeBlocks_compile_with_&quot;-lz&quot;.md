---
title: "Making Code::Blocks compile with &quot;-lz&quot;"
date: 2008-02-23
forum: Programming Talk
---

### Post by runesvend on 2008-02-23
Hello all

When compiling some C code I execute the following command which compiles my source code without any problems:

*gcc -lz <source-code.c> -o <output-file>*

I'm starting to using Code::Blocks since it offers a bit more help compared to the Text Editor, but when I press the Build I get the following errors:


> -------------- Build: Release in tvixfw ---------------

g++  -o bin/Release/tvixfw obj/Release/decrypt.o   -s  
obj/Release/decrypt.o: In function `extract':
decrypt.c:(.text+0xc2): undefined reference to `uncompress'
collect2: ld returned 1 exit status
Process terminated with status 1 (0 minutes, 0 seconds)
1 errors, 0 warnings

How do I make Code::Blocks use the *-lz* option for the *gcc* compiler so it will compile?

Thanks in advance!


EDIT: I solved it myself. Perhaps I should have Googled "gcc lz" before posting :)

For the next person seeing this post having the same problem. 

[I]The -l flag means "link against these libraries when compiling the code" .

Thus, just as -lxml2 refers to "libxml2" and -lm refers to "libm" (math library), it is reasonable to assume that -lz refers to libz, which I would guess is a compression library.[/I]

So I found libz.so, added it under Linker settings for the Build options of my project.

---

