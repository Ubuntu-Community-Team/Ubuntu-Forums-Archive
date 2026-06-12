---
title: "Assembly code"
date: 2009-10-11
forum: Programming Talk
---

### Post by ubuntuubuntu on 2009-10-11
Hello,
I have a program, let's say foo.cpp . If I do "g++ -S foo.cpp". That generates the file "foo.S" with assembly code. I would like to compare the assembly code foo.S with the assembly code generated if I put foo.S in a c program (even though there should be no difference), but I don't know how to do it. For foo.cpp = 
```

#include <iostream>

using namespace std;
int main() {
  cout << "a47" << endl;
  return 0;
}

```
for example, I get foo.S = 
```
	.mod_init_func
	.align 2
	.long	__GLOBAL__I_main
.lcomm __ZSt8__ioinit,1,0
	.cstring
LC0:
	.ascii "a\0"
	.text
	.align 1,0x90
.globl _main
_main:
LFB1480:
	pushl	%ebp
LCFI0:
	movl	%esp, %ebp
LCFI1:
	pushl	%ebx
LCFI2:
	subl	$20, %esp
LCFI3:
	call	L3
"L00000000001$pb":
L3:
	popl	%ebx
	leal	LC0-"L00000000001$pb"(%ebx), %eax
	movl	%eax, 4(%esp)
	leal	L__ZSt4cout$non_lazy_ptr-"L00000000001$pb"(%ebx), %eax
	movl	(%eax), %eax
	movl	%eax, (%esp)
	call	L__ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc$stub
	movl	%eax, %edx
	leal	L__ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_$non_lazy_ptr-"L00000000001$pb"(%ebx), %eax
	movl	(%eax), %eax
	movl	%eax, 4(%esp)
	movl	%edx, (%esp)
	call	L__ZNSolsEPFRSoS_E$stub
	movl	$0, %eax
	addl	$20, %esp
	popl	%ebx
	leave
	ret
LFE1480:
	.align 1,0x90
___tcf_0:
LFB1489:
	pushl	%ebp
LCFI4:
	movl	%esp, %ebp
LCFI5:
	pushl	%ebx
LCFI6:
	subl	$20, %esp
LCFI7:
	call	L6
"L00000000002$pb":
L6:
	popl	%ebx
	leal	__ZSt8__ioinit-"L00000000002$pb"(%ebx), %eax
	movl	%eax, (%esp)
	call	L__ZNSt8ios_base4InitD1Ev$stub
	addl	$20, %esp
	popl	%ebx
	leave
	ret
LFE1489:
	.section __TEXT,__StaticInit,regular,pure_instructions
	.align 1
__Z41__static_initialization_and_destruction_0ii:
LFB1488:
	pushl	%ebp
LCFI8:
	movl	%esp, %ebp
LCFI9:
	pushl	%ebx
LCFI10:
	subl	$36, %esp
LCFI11:
	call	L12
"L00000000003$pb":
L12:
	popl	%ebx
	movl	%eax, -12(%ebp)
	movl	%edx, -16(%ebp)
	cmpl	$65535, -16(%ebp)
	jne	L11
	cmpl	$1, -12(%ebp)
	jne	L11
	leal	__ZSt8__ioinit-"L00000000003$pb"(%ebx), %eax
	movl	%eax, (%esp)
	call	L__ZNSt8ios_base4InitC1Ev$stub
	leal	L___dso_handle$non_lazy_ptr-"L00000000003$pb"(%ebx), %eax
	movl	(%eax), %eax
	movl	%eax, 8(%esp)
	movl	$0, 4(%esp)
	leal	___tcf_0-"L00000000003$pb"(%ebx), %eax
	movl	%eax, (%esp)
	call	L___cxa_atexit$stub
L11:
	addl	$36, %esp
	popl	%ebx
	leave
	ret
LFE1488:
	.align 1
__GLOBAL__I_main:
LFB1490:
	pushl	%ebp
LCFI12:
	movl	%esp, %ebp
LCFI13:
	subl	$8, %esp
LCFI14:
	movl	$65535, %edx
	movl	$1, %eax
	call	__Z41__static_initialization_and_destruction_0ii
	leave
	ret
LFE1490:
	.section __TEXT,__eh_frame,coalesced,no_toc+strip_static_syms+live_support
EH_frame1:
	.set L$set$0,LECIE1-LSCIE1
	.long L$set$0
LSCIE1:
	.long	0x0
	.byte	0x1
	.ascii "zPR\0"
	.byte	0x1
	.byte	0x7c
	.byte	0x8
	.byte	0x6
	.byte	0x9b
	.long	L___gxx_personality_v0$non_lazy_ptr-.
	.byte	0x10
	.byte	0xc
	.byte	0x5
	.byte	0x4
	.byte	0x88
	.byte	0x1
	.align 2
LECIE1:
	.globl _main.eh
_main.eh:
LSFDE1:
	.set L$set$1,LEFDE1-LASFDE1
	.long L$set$1
LASFDE1:
	.long	LASFDE1-EH_frame1
	.long	LFB1480-.
	.set L$set$2,LFE1480-LFB1480
	.long L$set$2
	.byte	0x0
	.byte	0x4
	.set L$set$3,LCFI0-LFB1480
	.long L$set$3
	.byte	0xe
	.byte	0x8
	.byte	0x84
	.byte	0x2
	.byte	0x4
	.set L$set$4,LCFI1-LCFI0
	.long L$set$4
	.byte	0xd
	.byte	0x4
	.byte	0x4
	.set L$set$5,LCFI3-LCFI1
	.long L$set$5
	.byte	0x83
	.byte	0x3
	.align 2
LEFDE1:
___tcf_0.eh:
LSFDE3:
	.set L$set$6,LEFDE3-LASFDE3
	.long L$set$6
LASFDE3:
	.long	LASFDE3-EH_frame1
	.long	LFB1489-.
	.set L$set$7,LFE1489-LFB1489
	.long L$set$7
	.byte	0x0
	.byte	0x4
	.set L$set$8,LCFI4-LFB1489
	.long L$set$8
	.byte	0xe
	.byte	0x8
	.byte	0x84
	.byte	0x2
	.byte	0x4
	.set L$set$9,LCFI5-LCFI4
	.long L$set$9
	.byte	0xd
	.byte	0x4
	.byte	0x4
	.set L$set$10,LCFI7-LCFI5
	.long L$set$10
	.byte	0x83
	.byte	0x3
	.align 2
LEFDE3:
__Z41__static_initialization_and_destruction_0ii.eh:
LSFDE5:
	.set L$set$11,LEFDE5-LASFDE5
	.long L$set$11
LASFDE5:
	.long	LASFDE5-EH_frame1
	.long	LFB1488-.
	.set L$set$12,LFE1488-LFB1488
	.long L$set$12
	.byte	0x0
	.byte	0x4
	.set L$set$13,LCFI8-LFB1488
	.long L$set$13
	.byte	0xe
	.byte	0x8
	.byte	0x84
	.byte	0x2
	.byte	0x4
	.set L$set$14,LCFI9-LCFI8
	.long L$set$14
	.byte	0xd
	.byte	0x4
	.byte	0x4
	.set L$set$15,LCFI11-LCFI9
	.long L$set$15
	.byte	0x83
	.byte	0x3
	.align 2
LEFDE5:
__GLOBAL__I_main.eh:
LSFDE7:
	.set L$set$16,LEFDE7-LASFDE7
	.long L$set$16
LASFDE7:
	.long	LASFDE7-EH_frame1
	.long	LFB1490-.
	.set L$set$17,LFE1490-LFB1490
	.long L$set$17
	.byte	0x0
	.byte	0x4
	.set L$set$18,LCFI12-LFB1490
	.long L$set$18
	.byte	0xe
	.byte	0x8
	.byte	0x84
	.byte	0x2
	.byte	0x4
	.set L$set$19,LCFI13-LCFI12
	.long L$set$19
	.byte	0xd
	.byte	0x4
	.align 2
LEFDE7:
	.section __IMPORT,__jump_table,symbol_stubs,self_modifying_code+pure_instructions,5
L___cxa_atexit$stub:
	.indirect_symbol ___cxa_atexit
	hlt ; hlt ; hlt ; hlt ; hlt
	.section __IMPORT,__pointers,non_lazy_symbol_pointers
L__ZSt4cout$non_lazy_ptr:
	.indirect_symbol __ZSt4cout
	.long	0
	.section __IMPORT,__jump_table,symbol_stubs,self_modifying_code+pure_instructions,5
L__ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc$stub:
	.indirect_symbol __ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	hlt ; hlt ; hlt ; hlt ; hlt
L__ZNSolsEPFRSoS_E$stub:
	.indirect_symbol __ZNSolsEPFRSoS_E
	hlt ; hlt ; hlt ; hlt ; hlt
	.section __IMPORT,__pointers,non_lazy_symbol_pointers
L__ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_$non_lazy_ptr:
	.indirect_symbol __ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_
	.long	0
L___dso_handle$non_lazy_ptr:
	.indirect_symbol ___dso_handle
	.long	0
	.section __IMPORT,__jump_table,symbol_stubs,self_modifying_code+pure_instructions,5
L__ZNSt8ios_base4InitD1Ev$stub:
	.indirect_symbol __ZNSt8ios_base4InitD1Ev
	hlt ; hlt ; hlt ; hlt ; hlt
	.section __IMPORT,__pointers,non_lazy_symbol_pointers
L___gxx_personality_v0$non_lazy_ptr:
	.indirect_symbol ___gxx_personality_v0
	.long	0
	.section __IMPORT,__jump_table,symbol_stubs,self_modifying_code+pure_instructions,5
L__ZNSt8ios_base4InitC1Ev$stub:
	.indirect_symbol __ZNSt8ios_base4InitC1Ev
	hlt ; hlt ; hlt ; hlt ; hlt
	.constructor
	.destructor
	.align 1
	.subsections_via_symbols
```


I thought this would work, but it doesn't:

```

asm(" ** ALL THE ASSEMBLY CODE ABOVE ** "); 
```
A friend suggested me to use 
perl -pi~ -e ’s/\"/\\\"/g; s/(.*)/\"$1\\\n\"/ig’ foo.s
but it didn't work either.
Does anyone know how to do this? Thank you in advance!

---

### Post by samjh on 2009-10-11
deleted

---

### Post by Zugzwang on 2009-10-11
> **ubuntuubuntu said:**
> 
I thought this would work, but it doesn't:

```

asm(" ** ALL THE ASSEMBLY CODE ABOVE ** "); 
```


First of all, in C, you cannot just put some code somewhere in your source-file (as far as I know). All executable code must reside in functions (for example, in function "int main(...)".

Second, these assembler files contain some control commands about in which segments to put the stuff in, the memory alignment, etc., etc. You cannot put these into functions (at least, without changing the meaning).

Third, note that C++ adds some stuff to the assembler file which for which there is no correspondence in the code. Consider the end of your .S source file. You will see some atexit() stub and some streaming-related stuff. It does not make sense to put this code into a function.

---

### Post by grayrainbow on 2009-10-12
Since, Zugzwang, gave good explanation about why it's not working, I'm going to restrict myself to fiew suggestions.
 
First IMO AT&T syntax is something realy ugly.
 
2) Assuming your question, think you should start with something more...natural...like simple aritmetic function, then structs(C), then classes, abstract classes. Streams are class objects, so you generaly jump in the deep. In general all this wan't be big deal if done consistenly(only becouse sometimes ago some smart people make all hard work for us).
 
3) Try using debuggers disassembly not .s files for learning how C/C++ code is transform in instructions.
 
4) Good Luck :)

---

