---
title: "smallest infinite loop in C"
date: 2010-08-13
forum: Programming Talk
---

### Post by piyush.neo on 2010-08-13
[http://golf.shinh.org/reveal.rb?Timeout/kt3k_1190000147&c](http://golf.shinh.org/reveal.rb?Timeout/kt3k_1190000147&c)
this code is a smallest infinite loop...how does this work??  :confused:

---

### Post by Bachstelze on 2010-08-13
> **piyush.neo said:**
> how does this work??  :confused:

It doesn't.

```
firas@tsukino ~ % cat test.c 
main=-277;
firas@tsukino ~ % cc -o test test.c
test.c:1: warning: data definition has no type or storage class
firas@tsukino ~ % ./test
zsh: bus error  ./test

```

---

### Post by piyush.neo on 2010-08-13
it was also giving segmentation fault on my machine Ubuntu 10.04 but was running perfectly on my frnz comp Ubuntu Mint.
Also it was an accepted code for a challenge...though it seems to be a kludge, just wondering what might make it run...what so special about -277..is it something related with stack frame?
Can u explain me even a bit of it...? just an idea..will be glad....

---

### Post by Bachstelze on 2010-08-13
> **piyush.neo said:**
> it was also giving segmentation fault on my machine Ubuntu 10.04 but was running perfectly on my frnz comp Ubuntu Mint.
Also it was an accepted code for a challenge...though it seems to be a kludge, just wondering what might make it run...what so special about -277..is it something related with stack frame?
Can u explain me even a bit of it...? just an idea..will be glad....

It works only if you assume the machine is IA32. ;)

-277 in hex is 0xFFFFFEEB. Since IA32 is little-endian, it is represented internally as EB FE FF FF. What does this mean? The Opcode Map of the [IA32 Software Developer's Manual, volume 2B]("http://www.intel.com/Assets/PDF/manual/253667.pdf") (page 671) tells us that opcode 0xEB corresponds to instruction jmp. Instruction jmp is documented in [volume 2A]("http://www.intel.com/Assets/PDF/manual/253666.pdf") (page 619), and we see that Opcode 0xEB is followed by a one-byte operand. The operand is therefore 0xFE, which is -2 in decimal.

The effect of the instruction EB FE is therefore to make the program jump back and forth: when the program reaches the end of the instruction, it will jump 2 bytes backwards (because of the operand of -2), which wil put it back at the start of the instruction.

---

### Post by piyush.neo on 2010-08-13
Thanks !!!great help sir...

---

### Post by Bachstelze on 2010-08-13
To illustrate:

```
firas@tsukino ~ % cat test.c 
main=-277;
firas@tsukino ~ % cc -m32 -o test test.c 
test.c:1: warning: data definition has no type or storage class
firas@tsukino ~ % objdump -D test | nl
unable to read unknown load command 0x22
      	
     1	test:     file format mach-o-i386
      	
      	
     2	Disassembly of section .text:
      	
     3	00001f54 <start>:
     4	    1f54:	6a 00                	push   $0x0
     5	    1f56:	89 e5                	mov    %esp,%ebp
     6	    1f58:	83 e4 f0             	and    $0xfffffff0,%esp
     7	    1f5b:	83 ec 10             	sub    $0x10,%esp
     8	    1f5e:	8b 5d 04             	mov    0x4(%ebp),%ebx
     9	    1f61:	89 1c 24             	mov    %ebx,(%esp)
    10	    1f64:	8d 4d 08             	lea    0x8(%ebp),%ecx
    11	    1f67:	89 4c 24 04          	mov    %ecx,0x4(%esp)
    12	    1f6b:	83 c3 01             	add    $0x1,%ebx
    13	    1f6e:	c1 e3 02             	shl    $0x2,%ebx
    14	    1f71:	01 cb                	add    %ecx,%ebx
    15	    1f73:	89 5c 24 08          	mov    %ebx,0x8(%esp)
    16	    1f77:	8b 03                	mov    (%ebx),%eax
    17	    1f79:	83 c3 04             	add    $0x4,%ebx
    18	    1f7c:	85 c0                	test   %eax,%eax
    19	    1f7e:	75 f7                	jne    1f77 <start+0x23>
    20	    1f80:	89 5c 24 0c          	mov    %ebx,0xc(%esp)
    21	    1f84:	e8 a7 00 00 00       	call   2030 <_main>
    22	    1f89:	89 04 24             	mov    %eax,(%esp)
    23	    1f8c:	e8 01 00 00 00       	call   1f92 <start+0x3e>
    24	    1f91:	f4                   	hlt    
      	
    25	Disassembly of section __TEXT.__symbol_stub:
      	
    26	00001f92 <__TEXT.__symbol_stub>:
    27	    1f92:	ff 25 1c 20 00 00    	jmp    *0x201c
      	
    28	Disassembly of section __TEXT.__stub_helper:
      	
    29	00001f98 < stub helpers>:
    30	    1f98:	68 18 20 00 00       	push   $0x2018
    31	    1f9d:	ff 25 14 20 00 00    	jmp    *0x2014
    32	    1fa3:	90                   	nop
    33	    1fa4:	68 00 00 00 00       	push   $0x0
    34	    1fa9:	e9 ea ff ff ff       	jmp    1f98 < stub helpers>
      	
    35	Disassembly of section __TEXT.__unwind_info:
      	
    36	00001fb0 <__TEXT.__unwind_info>:
    37	    1fb0:	01 00                	add    %eax,(%eax)
    38	    1fb2:	00 00                	add    %al,(%eax)
    39	    1fb4:	1c 00                	sbb    $0x0,%al
    40	    1fb6:	00 00                	add    %al,(%eax)
    41	    1fb8:	00 00                	add    %al,(%eax)
    42	    1fba:	00 00                	add    %al,(%eax)
    43	    1fbc:	1c 00                	sbb    $0x0,%al
    44	    1fbe:	00 00                	add    %al,(%eax)
    45	    1fc0:	00 00                	add    %al,(%eax)
    46	    1fc2:	00 00                	add    %al,(%eax)
    47	    1fc4:	1c 00                	sbb    $0x0,%al
    48	    1fc6:	00 00                	add    %al,(%eax)
    49	    1fc8:	02 00                	add    (%eax),%al
    50	    1fca:	00 00                	add    %al,(%eax)
    51	    1fcc:	00 00                	add    %al,(%eax)
    52	    1fce:	00 00                	add    %al,(%eax)
    53	    1fd0:	34 00                	xor    $0x0,%al
    54	    1fd2:	00 00                	add    %al,(%eax)
    55	    1fd4:	34 00                	xor    $0x0,%al
    56	    1fd6:	00 00                	add    %al,(%eax)
    57	    1fd8:	f9                   	stc    
    58	    1fd9:	0f 00 00             	sldt   (%eax)
    59	    1fdc:	00 00                	add    %al,(%eax)
    60	    1fde:	00 00                	add    %al,(%eax)
    61	    1fe0:	34 00                	xor    $0x0,%al
    62	    1fe2:	00 00                	add    %al,(%eax)
    63	    1fe4:	03 00                	add    (%eax),%eax
    64	    1fe6:	00 00                	add    %al,(%eax)
    65	    1fe8:	0c 00                	or     $0x0,%al
    66	    1fea:	01 00                	add    %eax,(%eax)
    67	    1fec:	10 00                	adc    %al,(%eax)
    68	    1fee:	01 00                	add    %eax,(%eax)
    69		...
      	
    70	Disassembly of section __DATA.__program_vars:
      	
    71	00002000 <_pvars>:
    72	    2000:	00 10                	add    %dl,(%eax)
    73	    2002:	00 00                	add    %al,(%eax)
    74	    2004:	20 20                	and    %ah,(%eax)
    75	    2006:	00 00                	add    %al,(%eax)
    76	    2008:	24 20                	and    $0x20,%al
    77	    200a:	00 00                	add    %al,(%eax)
    78	    200c:	28 20                	sub    %ah,(%eax)
    79	    200e:	00 00                	add    %al,(%eax)
    80	    2010:	2c 20                	sub    $0x20,%al
    81		...
      	
    82	Disassembly of section __DATA.__nl_symbol_ptr:
      	
    83	00002014 <__DATA.__nl_symbol_ptr>:
    84		...
      	
    85	Disassembly of section __DATA.__la_symbol_ptr:
      	
    86	0000201c <__DATA.__la_symbol_ptr>:
    87	    201c:	a4                   	movsb  %ds:(%esi),%es:(%edi)
    88	    201d:	1f                   	pop    %ds
    89		...
      	
    90	Disassembly of section .data:
      	
    91	00002020 <_NXArgc>:
    92	    2020:	00 00                	add    %al,(%eax)
    93		...
      	
    94	00002024 <_NXArgv>:
    95	    2024:	00 00                	add    %al,(%eax)
    96		...
      	
    97	00002028 <_environ>:
    98	    2028:	00 00                	add    %al,(%eax)
    99		...
      	
   100	0000202c <___progname>:
   101	    202c:	00 00                	add    %al,(%eax)
   102		...
      	
   103	00002030 <_main>:
   104	    2030:	eb fe                	jmp    2030 <_main>
   105	    2032:	ff                   	(bad)  
   106	    2033:	ff                   	.byte 0xff
      	
   107	Disassembly of section LC_UUID:
      	
   108	00000000 <LC_UUID>:
   109	   0:	d6                   	(bad)  
   110	   1:	fb                   	sti    
   111	   2:	e5 19                	in     $0x19,%eax
   112	   4:	25 2e 8b b7 81       	and    $0x81b78b2e,%eax
   113	   9:	ed                   	in     (%dx),%eax
   114	   a:	ce                   	into   
   115	   b:	91                   	xchg   %eax,%ecx
   116	   c:	a9                   	.byte 0xa9
   117	   d:	b9                   	.byte 0xb9
   118	   e:	49                   	dec    %ecx
   119	   f:	0a                   	.byte 0xa
      	
   120	Disassembly of section LC_THREAD.x86_THREAD_STATE32.0:
      	
   121	00000000 <LC_THREAD.x86_THREAD_STATE32.0>:
   122		...
   123	  28:	54                   	push   %esp
   124	  29:	1f                   	pop    %ds
   125		...

```

We see the instruction at line 104 of the objdump.  The instruction at address 0x2030 is 0xEBFE, which translates to jmp 2030. An equivalent C code would be:

```
int main(void)
{
start:
    goto start;
    return 0;
}
```

---

### Post by Puzzled Guy on 2010-08-14
might not be related but here's the smallest infinite loop in perl that actually prints something out:

perl -e 'while(1){print '0'}'

---

### Post by ja660k on 2010-08-14
> **Puzzled Guy said:**
> 
perl -e 'while(1){print '0'}'

i think youll find that thats more or less the same in any language.

---

### Post by trent.josephsen on 2010-08-14
> **Puzzled Guy said:**
> might not be related but here's the smallest infinite loop in perl that actually prints something out:

perl -e 'while(1){print '0'}'
"Smallest"?  You can lose the quotes around '0', and I can knock off one character just by replacing the while with a for:
```
for(;;){print 0}
```
A little more thought replaces the while(){} with a statement modifier:
```
print 0 while 1
```

I bet you could get it smaller.

The smallest non-useful Perl loop I can think of would be
```
x:goto x
```
But adding things before the goto becomes verbose.

---

### Post by mmix on 2010-08-15
```

//inline assembly
main(){asm("L: jmp L");}

//assembly
jmp $

//c, may not work
main=main;

//c, may not work
main(){return main();}

```

---

### Post by schauerlich on 2010-08-16
> **mmix said:**
> ```

//c, may not work
main(){return main();}

```

Main isn't allowed to be recursive. Even if it did work, it'd exhaust the stack pretty quickly. not really infinite. :)

```
main(){for(;;);}
```

---

### Post by worseisworser on 2010-08-16
> **schauerlich said:**
> Main isn't allowed to be recursive.

Yup.

> **schauerlich said:**
> Even if it did work, it'd exhaust the stack pretty quickly. not really infinite. :)

```
main(){for(;;);}
```

Note that GCC can generate tail recursive code;

```
void blah(){
  blah();
}


int main(){
  blah();
  return(0);
}
```


```

lnostdal@blackbox:~/programming/c$ gcc -Wall -g tail-recursion.c -o tail-recursion
lnostdal@blackbox:~/programming/c$ ./tail-recursion 
Segmentation fault
lnostdal@blackbox:~/programming/c$ # I.e., no tail recursion.


lnostdal@blackbox:~/programming/c$ gcc -Wall -g -O2 tail-recursion.c -o tail-recursion
lnostdal@blackbox:~/programming/c$ ./tail-recursion 
...
...
...

```

I.e., it recurses forever.

---

### Post by schauerlich on 2010-08-16
> **worseisworser said:**
> Note that GCC can generate tail recursive code;

Actually, on O2 it optimizes away the whole function.

```
.globl _blah
_blah:
LFB2:
	pushq	%rbp
LCFI0:
	movq	%rsp, %rbp
LCFI1:
	leave
	ret

```

But yes, I know what you meant. The code produced by gcc for a for loop and a similar/equivalent tail recursive function will often be (almost) identical.

---

### Post by worseisworser on 2010-08-17
> **schauerlich said:**
> Actually, on O2 it optimizes away the whole function.

```
.globl _blah
_blah:
LFB2:
	pushq	%rbp
LCFI0:
	movq	%rsp, %rbp
LCFI1:
	leave
	ret

```


Whoops; indeed! Sloppy of me not checking that. :)


> **schauerlich said:**
> But yes, I know what you meant. The code produced by gcc for a for loop and a similar/equivalent tail recursive function will often be (almost) identical.

---

