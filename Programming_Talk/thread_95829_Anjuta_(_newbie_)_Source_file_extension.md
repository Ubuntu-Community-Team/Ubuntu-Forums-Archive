---
title: "Anjuta ( newbie ): Source file extension ?"
date: 2005-11-27
forum: Programming Talk
---

### Post by Biased turkey on 2005-11-27
I used to program C++ with Kdevelop and switched to Anjuta.
With Kdevelop, a source file had the .c or .cpp extension ( depending if the program was a C or C++ ).
I  ( successfully ) compile a C++ "hello world" program with Anjuta, but the source file has a .cc extension.
I'm not familiar at all with that file extension.
Could someone please be kind enough to give me some info about that ?
tia for any help

---

### Post by tageiru on 2005-11-27
[QUOTE=Biased turkey]I used to program C++ with Kdevelop and switched to Anjuta.
With Kdevelop, a source file had the .c or .cpp extension ( depending if the program was a C or C++ ).
I  ( successfully ) compile a C++ "hello world" program with Anjuta, but the source file has a .cc extension.
I'm not familiar at all with that file extension.
Could someone please be kind enough to give me some info about that ?
tia for any help[/QUOTE]
.cpp and .cc are the same thing. If i remember correctly .cpp is more common in Windows programming and .cc more common in UNIX-like systems.

---

### Post by Biased turkey on 2005-11-27
[QUOTE=tageiru].cpp and .cc are the same thing. If i remember correctly .cpp is more common in Windows programming and .cc more common in UNIX-like systems.[/QUOTE]

Thanks for your help Tageiru.
I just compiled " by hand" a sourcefile doing:
g++ file1.cc -o file1
and it worked nicely.

---

### Post by David Marrs on 2005-11-28
The compiler won't care what the extension is. As long as there aren't any errors in the code, the file will compile. The extensions are there to help people first and foremost.

---

### Post by Burke on 2005-11-28
Yeah, GCC will compile a *.exe, as long as its actually a source code file. :)

---

