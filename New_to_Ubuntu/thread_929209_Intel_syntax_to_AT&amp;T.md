---
title: "Intel syntax to AT&amp;T"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by syn_stanzer on 2008-09-24
Hey guys does anyone has any idea or are they any converted AT&T assembly syntax for Mprime application? Im trying to search for Mprime application source codes in AT&T syntax asm  instead of the original written intel asm syntax. Thx:guitar:

---

### Post by Sorivenul on 2008-09-26
You're talking about [this]("http://www.mersenne.org/") mprime, yes?
I'm not wholly familar with assembly, yet I am learning.  Why do you want to convert or use the other syntax, just out of curiosity?  You could try intel2gas, which is in the repositories and should be installable via Synaptic or ```
sudo apt-get install intel2gas
```.  Good luck!

---

### Post by syn_stanzer on 2008-09-29
Thanks Sorivenul

This conversion is actually a project of mine. I've been using Intel2gas for doing the conversion, however as you know the Intel2gas just convert it without understanding the coding. Here are somethings I don understand bout the coding, could any of you kindly let me know what these codes mean?

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

"EXTRN _CPUID_EAX:DWORD"

"PUBLIC _fpu_init"
"_fpu_init PROC"


Could you guys en light me for these so I could have some ideas to proceed on my conversion.

P/S: I have no background or any knowledge in the whole conversion thingy, just started to learn everything like gcc, vi/vim, intel/at&t syntax thru wiki/google. Thanks :guitar::guitar:

---

### Post by Sorivenul on 2008-09-29
I'm still learning assembly myself.
I'm linking to some helpful PDF files on Intel syntax to help get the file converted manually if need be.
[http://www.jegerlehner.ch/intel/IntelCodeTable.pdf]("http://www.jegerlehner.ch/intel/IntelCodeTable.pdf")
[URL="http://upload.wikimedia.org/wikibooks/en/1/11/X86_Assembly.pdf"]
http://upload.wikimedia.org/wikibooks/en/1/11/X86_Assembly.pdf[/URL]
And another helpful link:
[http://faydoc.tripod.com/cpu/]("http://faydoc.tripod.com/cpu/")

As you are self-teaching as well, I would assume you probably already have looked at some, if not all, of these.  I'll take a closer look and see what I can figure out about the conversion of the code you posted as well.

---

### Post by syn_stanzer on 2008-09-30
> **Sorivenul said:**
> I'm still learning assembly myself.
I'm linking to some helpful PDF files on Intel syntax to help get the file converted manually if need be.
[http://www.jegerlehner.ch/intel/IntelCodeTable.pdf]("http://www.jegerlehner.ch/intel/IntelCodeTable.pdf")
[URL="http://upload.wikimedia.org/wikibooks/en/1/11/X86_Assembly.pdf"]
http://upload.wikimedia.org/wikibooks/en/1/11/X86_Assembly.pdf[/URL]
And another helpful link:
[http://faydoc.tripod.com/cpu/]("http://faydoc.tripod.com/cpu/")

As you are self-teaching as well, I would assume you probably already have looked at some, if not all, of these.  I'll take a closer look and see what I can figure out about the conversion of the code you posted as well.


Kool Sorivenul, this certainly helps........thanks there
Update me somemore info if u got thanks :KS:KS

---

