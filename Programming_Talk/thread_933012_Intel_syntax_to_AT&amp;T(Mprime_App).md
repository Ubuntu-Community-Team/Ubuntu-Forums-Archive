---
title: "Intel syntax to AT&amp;T(Mprime App)"
date: 2008-09-29
forum: Programming Talk
---

### Post by syn_stanzer on 2008-09-29
Hey guys, does anyone has any idea or are there any converted AT&T assembly syntax for Mprime application? Im trying to search for Mprime application source codes in AT&T syntax asm instead of the original written intel asm syntax.

I've been trying to convert the original Mprime asm files using Intel2Gas however there are some understanding issues encountered. As for you information I hv no knowledge or background in GCC, GDB, vi/vim, Intel/AT&T syntax. 

Here are somethings I don understand bout the coding, could any of you kindly let me know what these codes mean?

```
        TITLE   setup

IFNDEF X86_64
        .586
        .MODEL  FLAT
ENDIF

INCLUDE unravel.mac

_TEXT SEGMENT
Sorivenul
EXTRN   _CPUID_EAX:DWORD
EXTRN   _CPUID_EBX:DWORD
EXTRN   _CPUID_ECX:DWORD
EXTRN   _CPUID_EDX:DWORD

;
; Utility routine to initialize the FPU
;

        PUBLIC  _fpu_init
_fpu_init PROC
IFNDEF X86_64
        fninit
ENDIF     
        ret
_fpu_init ENDP
```

These are part of the cpuidhlp.asm that belongs to the gwnum folder of Mprime. As I did the conversion for this particular asm file, the Intel2gas couldn't match the syntax:

" TITLE setup"

"IFNDEF X86_64"

".MODEL FLAT"

"ENDIF"

"INCLUDE unravel.mac"

"_TEXT SEGMENT"

"EXTRN _CPUID_EAXWORD"

"PUBLIC _fpu_init"
"_fpu_init PROC"


Could you guys en light me for these so I could have some ideas to proceed on my conversion. Thanks :KS:KS

---

### Post by syn_stanzer on 2008-10-02
Could anybody helps with this thread? Thanks a lot ^^

---

### Post by Zugzwang on 2008-10-05
You're not getting any helpful response because it is likely that nobody here actually knows "Mprime application". Furthermore without knowledge in assembler, the task to convert your stuff is quite tough. It's also quite likely that only very few readers will have used intel2gas so far. Finally, I had to read your post three times before actually knowing what you want.

Actually, your problem doesn't have anything to do with "mprime" (whatever that is). It looks like "Intel2Gas" cannot interpret some assembler control commands - These are just there for the assembler to organize the work and do not appear in the actual assembled binary. The assemblers MASM, TASM and NASM have different, incompatible such commands. It looks like as if Intel2Gas can only handle a (limited) subset of the NASM control commands and you are either using TASM or MASM source code or you are using the unsupported NASM ones. That's your problem.

Fixing it: Make the conversion of these control commands manually or adding the respective changes to Intel2Gas. Since you don't have knowledge in assembler (and even more important, linking and all that stuff), that task however looks like as if it is way over your head.

---

### Post by syn_stanzer on 2008-10-05
Hey Zugzwang, thanks for the kind reply in advanced(since Im not getting any and you're the first haha)

This is actually a proj given and it seems I hv no choice but to try my best to complete it.
Like you mentioned, I was suggested to use intel2gas to convert the .asm and .mac files then modified those mismatches or unhandled syntax by the intel2gas
So now my question is, do u hv any suggestion where should I be starting to do the rewrite of the mismatches/unhandled syntax in sense of what should I be looking for related knowledge/information in doing the whole conversion things. 

Thanks ^^

---

### Post by Zugzwang on 2008-10-06
> **syn_stanzer said:**
> This is actually a proj given and it seems I hv no choice but to try my best to complete it.
Like you mentioned, I was suggested to use intel2gas to convert the .asm and .mac files then modified those mismatches or unhandled syntax by the intel2gas
So now my question is, do u hv any suggestion where should I be starting to do the rewrite of the mismatches/unhandled syntax in sense of what should I be looking for related knowledge/information in doing the whole conversion things. 


I wonder what is the purpose of converting the source codes to AT&T syntax. Why don't you just use NASM? This of course still forces you to change those directives, but hey, that would be a little bit easier.

Also, I wonder why you were given a project you cannot handle very well (sorry, but if you have no knowledge of x86 assembly, then this is a little bit too hard).

If you want to get it done anyway, you should do the following:
[LIST]
[*]Check out for which assembler the original source codes are (my guess: MASM)
[*]Then read the manual for that assembler (Google tells me that there's a MASM manual, although that might not be official, at: [http://webster.cs.ucr.edu/Page_TechDocs/MASMDoc/]("http://http://webster.cs.ucr.edu/Page_TechDocs/MASMDoc/"). If you've got Windows, try downloading the Windows Driver development kit, it also contains a MASM copy and hopefully the manual as well)
[*]Read the manual of GAS.
[*]Then compare the directives in both copies and you are done.
[/LIST]

Keep in mind that you might also need to read a little bit about so-called calling conventions. Pick an assembly book from your University library (If you're enrolled) and read. If your are lucky, there's also a chapter about that in the assembler manuals. Good luck!

---

### Post by syn_stanzer on 2008-10-10
> **Zugzwang said:**
> I wonder what is the purpose of converting the source codes to AT&T syntax. Why don't you just use NASM? This of course still forces you to change those directives, but hey, that would be a little bit easier.

Also, I wonder why you were given a project you cannot handle very well (sorry, but if you have no knowledge of x86 assembly, then this is a little bit too hard).

If you want to get it done anyway, you should do the following:
[LIST]
[*]Check out for which assembler the original source codes are (my guess: MASM)
[*]Then read the manual for that assembler (Google tells me that there's a MASM manual, although that might not be official, at: [http://webster.cs.ucr.edu/Page_TechDocs/MASMDoc/]("http://http://webster.cs.ucr.edu/Page_TechDocs/MASMDoc/"). If you've got Windows, try downloading the Windows Driver development kit, it also contains a MASM copy and hopefully the manual as well)
[*]Read the manual of GAS.
[*]Then compare the directives in both copies and you are done.
[/LIST]

Keep in mind that you might also need to read a little bit about so-called calling conventions. Pick an assembly book from your University library (If you're enrolled) and read. If your are lucky, there's also a chapter about that in the assembler manuals. Good luck!

Thanks for the info, I will lookup to them. :guitar:

---

