---
title: "[SOLVED] Debug symbols"
date: 2008-02-18
forum: Programming Talk
---

### Post by WitchCraft on 2008-02-18
Hi! Question:

If i have a ELF file on Linux  (or PE file on Windows respectively), which includes some functions, eg. function1, function2, function3 then i can read out these function's address using the "nm <executable filename>" command. However, as far as i know, this only works if the file was compiled with debug symbols.

Now my question: if i compile the file to NOT use debug symbols, does this change the address of the functions? I mean, is the address of the function in the release compile equal to the address of the function in the debug compile ?

I would first have supposed that this is not the case, but i just saw that the debug info is at the end of the file, so I wounder whether this leaves the rest intact ("as is")...

---

### Post by Zugzwang on 2008-02-18
Normally, the release version is compiled with compiler optimizations switched on while that is normally not the case for the debug version. At least in this case the answer is clearly no.

---

### Post by WitchCraft on 2008-02-18
Thanks, for optimization that's correct, so for optimized release executables the question is answered. 
What about compiled without optimization? And what about debug compile with the same optimization flags set?

---

### Post by WitchCraft on 2008-02-18
bump

---

### Post by stroyan on 2008-02-18
Basic information about symbol addresses is present without -g debug mode.
The -g debug information is more complete than what nm uses.
The symbol table that nm uses is striped off by 'ld -s' or the strip command.
Compiling with and without -g can result in exactly the same function addresses.
I just verified that here.
```
$ cc -o bench bench.c -lrt; nm bench > bench.nm
$ cc -g -o bench_debug bench.c -lrt; nm bench_debug > bench_debug.nm
$ cmp bench.nm bench_debug.nm 
$ cc -O2 -o bench_O2 bench.c -lrt; nm bench_O2 > bench_O2.nm
$ cc -O2 -g -o bench_O2_debug bench.c -lrt; nm bench_O2_debug > bench_O2_debug.nm
$ cmp bench_O2.nm bench_O2_debug.nm 
```
But I wouldn't count on the symbols always being the same.
Another compiler might change code generation when using -g.

---

### Post by WitchCraft on 2008-02-18
> **stroyan said:**
> Basic information about symbol addresses is present without -g debug mode.
The -g debug information is more complete than what nm uses.
The symbol table that nm uses is striped off by 'ld -s' or the strip command.
Compiling with and without -g can result in exactly the same function addresses.
I just verified that here.
```
$ cc -o bench bench.c -lrt; nm bench > bench.nm
$ cc -g -o bench_debug bench.c -lrt; nm bench_debug > bench_debug.nm
$ cmp bench.nm bench_debug.nm 
$ cc -O2 -o bench_O2 bench.c -lrt; nm bench_O2 > bench_O2.nm
$ cc -O2 -g -o bench_O2_debug bench.c -lrt; nm bench_O2_debug > bench_O2_debug.nm
$ cmp bench_O2.nm bench_O2_debug.nm 
```
But I wouldn't count on the symbols always being the same.
Another compiler might change code generation when using -g.

Very interesting, so you confirm that i just found a convenient way of getting the function offsets without using a modified executable - i can just recompile a duplicate with the appropriate options, get the symbols from there, and use them in the original without symbols without modifying that executable - if i have the sourcecode of the application ;-)

---

### Post by aks44 on 2008-02-18
> **WitchCraft said:**
> Very interesting, so you confirm that i just found a convenient way of getting the function offsets without using a modified executable - i can just recompile a duplicate with the appropriate options, get the symbols from there, and use them in the original without symbols without modifying that executable - if i have the sourcecode of the application ;-)
Just curious... what would be the whole point of that?


As a side note: as long as it's not documented, you can't count on it... ;)

---

### Post by WitchCraft on 2008-02-18
> **aks44 said:**
> Just curious... what would be the whole point of that?


As a side note: as long as it's not documented, you can't count on it... ;)
Well, but I can assume that it's correct on my machine. And if it changes/proofs incorrect, I will realize it, sooner or later. That's enough for me.

The point is: if you do a CRC / MD5 checksum on a executable WITH debug symbols, then the checksum is different from the checksum of the very same executable WITHOUT debug symbols.

So it can be detected that you modified the executable. And I don't want this.

---

### Post by stroyan on 2008-02-18
I couldn't quite follow what you said about the checksum.
It seems that this similarity between files might be useful if you have a program that core dumped.
You could rebuild the program the same way, except for adding -g and linking it unstripped.
Then you could use the unstripped debug version with the original core file.
You could use md5sum or cmp between the original program and a stripped version of your new debuggable program to confirm that they are identical except for the addition of the symbol and debug information that strip will remove.
```

$ cc -O2 -g -o bench_O2_debug bench.c -lrt
$ cc -O2 -s -o bench_O2 bench.c -lrt
$ nm bench_O2
nm: bench_O2: no symbols
$ cp bench_O2_debug bench_O2_debug_stripped 
$ strip bench_O2_debug_stripped
$ cmp bench_O2  bench_O2_debug_stripped
$ md5sum bench_O2  bench_O2_debug_stripped
ccba5f13e28f7459881caf07a1f85510  bench_O2
ccba5f13e28f7459881caf07a1f85510  bench_O2_debug_stripped
```

---

### Post by WitchCraft on 2008-02-19
> **stroyan said:**
> 
I couldn't quite follow what you said about the checksum.
It seems that this similarity between files might be useful if you have a program that core dumped.
You could rebuild the program the same way, except for adding -g and linking it unstripped.
Then you could use the unstripped debug version with the original core file.
You could use md5sum or cmp between the original program and a stripped version of your new debuggable program to confirm that they are identical except for the addition of the symbol and debug information that strip will remove.
```

$ cc -O2 -g -o bench_O2_debug bench.c -lrt
$ cc -O2 -s -o bench_O2 bench.c -lrt
$ nm bench_O2
nm: bench_O2: no symbols
$ cp bench_O2_debug bench_O2_debug_stripped 
$ strip bench_O2_debug_stripped
$ cmp bench_O2  bench_O2_debug_stripped
$ md5sum bench_O2  bench_O2_debug_stripped
ccba5f13e28f7459881caf07a1f85510  bench_O2
ccba5f13e28f7459881caf07a1f85510  bench_O2_debug_stripped
```


Well, that's a logical consequence of the 'fact' that the debug file is the same as the release file, except the debug info, of which you get rid off by using strip... 

What I mean with the checksum is, that you can modify the program in RAM, leaving the file on disc "as is". But you need to get the offsets of the functions from the original file. This can be done automatically using nm, if the file contains debug info. 

If it doesn't, you need to get the offsets manually, and adjust them every time a change to the executable that changes the offsets has been made.

So if you want to use nm on the file, you need a executable with debug info. But if the executable doesn't contain debug info, then you need to generate an executable with debug info. However, if the offsets would not be the same, you would also have to replace the original executable with the debug one. This means a change of the file on disk, not in RAM, and this can be detected by running a md5checksum test on the executable on disk. 

Now if the debug and release offsets are the same, you can just read the debug info from a duplicate file on disc compiled with debug info, and apply the offsets to change the RAM of the executable with no debug info, and you don't have a detectable md5 change in the executable with no debug info...

---

