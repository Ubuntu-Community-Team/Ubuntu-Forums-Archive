---
title: "Can I use YASM to compile TASM z80 assembly source code?"
date: 2015-08-30
forum: New to Ubuntu
---

### Post by Eric_Piphany on 2015-08-30
On Windows I can compile to a .bin file if I have the files tasm.exe and tasm80.tab, by running tasm in the command prompt.
I've installed DOSBox and I can compile there, but it takes quite a while, and I've set the cycles to max.
So I'm looking if there is a way to compile with a program that runs on ubuntu, downloaded yasm, but when I run 'tasm -t80 file_name.z80' in the terminal I get a whole list of errors.
Any suggestions? Be clear, because I don't really know what I am doing...

Source file: hw.z80

#include "ti83plus.inc"
    .org 9D93h
    .db $BB, $6D
    ld a, 0
    ld (CurCol), a
    ld (CurRow), a
    ld hl,text
    bcall(_PutS)
    bcall(_NewLine)
    ret
text:
    .db "Hello, World", 0
.end
.end

When I try to compile:

mendel@mendel-Inspiron-1012:~/Downloads/ASM/Main$ tasm -t80 hw.z80
*Warning* hw.z80(1) ignoring unrecognized character `#'
**Error** hw.z80(1) junk at end of line, first unrecognized character is `"'
**Error** hw.z80(2) junk at end of line, first unrecognized character is `9'
**Error** hw.z80(3) junk at end of line, first unrecognized character is `$'
**Error** hw.z80(4) junk at end of line, first unrecognized character is `a'
**Error** hw.z80(5) redefinition of `ld'
**Error** hw.z80(4) `ld' previously defined here
**Error** hw.z80(6) redefinition of `ld'
**Error** hw.z80(4) `ld' previously defined here
**Error** hw.z80(7) redefinition of `ld'
**Error** hw.z80(4) `ld' previously defined here
**Error** hw.z80(8) junk at end of line, first unrecognized character is `('
**Error** hw.z80(9) redefinition of `bcall'
**Error** hw.z80(8) `bcall' previously defined here
**Error** hw.z80(12) redefinition of `.db'
**Error** hw.z80(3) `.db' previously defined here
**Error** hw.z80(14) redefinition of `.end'
**Error** hw.z80(13) `.end' previously defined here

---

### Post by Double.J on 2015-09-01
Hi there, Welcome to the forums!

I'm gonna give this a bump for you as I'm also very interested in this. Were you coding for the TI calculator or a Z80 homebrew if you don't mind me asking? I've been looking into home brew 8bits for a while and I want to go Z80 because of my childhood, but there seems to be a more co-ordinated community for the 6502's. 

In terms of answering your question, the netwide assembler (NASM) compiler has a -t switch for TASM, but I don't know if that will work. 8 bit assembly seems to be a bit unloved nowadays... Maybe easier to run something like dfreedos or windows in a VM?

JJ

---

