---
title: "New to programming on linux machine"
date: 2008-09-22
forum: Programming Talk
---

### Post by ChazZeromus on 2008-09-22
I'm really looking forward to programming on a linux machine and I would love to start programming GUI programs.  I'd like to know what libraries I should use to begin writing GUI applications.  And another question,  I've been using NASM and when I use the AOUT object format, I can't seem to link with the GCC linker with the other ELF object files.  Judging by the Nasm reference, the object emitted by the linker is a very only unix object format.  So, what can I do about this?

The only linker that actually puts together modern elf32 object files is the DJGPP linker.  But that belongs to a collection of DOS compilers for windows.  I've tried running it with wine but I cam across programs I can't seem to fix, at first it was the 64K memory problem where the program could not access the bottom 64K area of memory.  I fixed it, even though it was patched because of the exploit.  But when I ran it again a different problem happened when the program complained about interrupt vectors.  So I guess Wine doesn't support 16-bit DOs programs.


So are there any alternative linkers?  That I can use with all ELF formats?

---

