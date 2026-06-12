---
title: "nasm + irvine32.inc"
date: 2008-05-25
forum: Programming Talk
---

### Post by jmwalloh on 2008-05-25
Hi,im a bit new to assembly language programming. There's this asm code i have that includes the irvine32.inc lib that am trying to assemble in ubuntu using NASM but it's not working(it works pefect in windows using MASM). It simply moves hexadecimal values to reg eax, adds them up then dumps the contents of eax. Any bright ideas how to tackle it ????

---

### Post by Zugzwang on 2008-05-25
"is it not working" is not very precise. What doesn't work? What error messages do you get?

---

### Post by jmwalloh on 2008-05-26
Here is the code snippet

TITLE Add and Sub
; This is a comment
INCLUDE Irvine32.inc

.code
Main proc
	MOV EAX, 10000h
	ADD EAX, 40000h
	SUB EAX, 20000h
	CALL DumpRegs
	EXIT
Main endp
End Main


This is what i typed at the terminal:
$nasm -f elf -l ex1.lst ex1.asm

---

### Post by Zugzwang on 2008-05-26
And what happens?

It might be worthwhile mentioning that MASM and NASM have a different syntax of "control commands" (like the assignment of stuff to the segments, etc.)

---

### Post by NathanB on 2008-05-26
> **jmwalloh said:**
> Hi,im a bit new to assembly language programming. There's this asm code i have that includes the irvine32.inc lib that am trying to assemble in ubuntu using NASM but it's not working(it works pefect in windows using MASM). It simply moves hexadecimal values to reg eax, adds them up then dumps the contents of eax. Any bright ideas how to tackle it ????

That header file is specific to Windows and MASM.  If someone has converted it for use with NASM (quite possible), then you might find it in the files section of this group:

[http://tech.groups.yahoo.com/group/win32-nasm-users/?v=1&t=search&ch=web&pub=groups&sec=group&slk=1](http://tech.groups.yahoo.com/group/win32-nasm-users/?v=1&t=search&ch=web&pub=groups&sec=group&slk=1)

If someone has further converted that header file for use in Linux (mostly doubtful), then you might find it in the files section of this group:

[http://groups.yahoo.com/group/linux-nasm-users?v=1&t=search&ch=web&pub=groups&sec=group&slk=2](http://groups.yahoo.com/group/linux-nasm-users?v=1&t=search&ch=web&pub=groups&sec=group&slk=2)

However, I suspect you will have better luck if you start with these alternative books and tutorials:

[http://www.drpaulcarter.com/pcasm/](http://www.drpaulcarter.com/pcasm/)

[http://savannah.nongnu.org/projects/pgubook](http://savannah.nongnu.org/projects/pgubook)

[http://www.artofasm.com](http://www.artofasm.com)

[http://linuxassembly.org](http://linuxassembly.org)

---

