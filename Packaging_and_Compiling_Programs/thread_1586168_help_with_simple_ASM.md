---
title: "help with simple ASM"
date: 2010-10-01
forum: Packaging and Compiling Programs
---

### Post by puneet21 on 2010-10-01
Hi,

i want to use a near jmp (opcode EB) in my program to skip the 
instruction c=1 and directly print the value as 0.

main(){

int c=0;
__asm__("jmp 7;");
c=1;
printf("c:%d",c);
}

disass main
[http://img838.imageshack.us/img838/4157/screenshot1lr.png](http://img838.imageshack.us/img838/4157/screenshot1lr.png)

when i run the program, it gives me a segmentation fault.
The reason is it takes the jmp 7 instruction as a far jump (E9) rather than near jmp (EB). How can i jst use near jmp??

---

### Post by Bachstelze on 2010-10-01
You Can't Do That&#8482;

For direct jumps, even though the address is actually encoded relative to the PC in the bytecode, in assembler it is absolute:

```
firas@aoba ~ % cat test.c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    int c = 0;
    __asm__("jmp .L1");
    c = 1;
    __asm__(".L1:");
    printf("%d\n", c);
    return EXIT_SUCCESS;
}

firas@aoba ~ % cc -m32 -o test test.c
firas@aoba ~ % ./test
0
firas@aoba ~ % objdump -D test | nl
unable to read unknown load command 0x22
          
     1    test:     file format mach-o-i386
          
          
     2    Disassembly of section .text:
          
     3    00001f00 <start>:
     4        1f00:    6a 00                    push   $0x0
     5        1f02:    89 e5                    mov    %esp,%ebp
     6        1f04:    83 e4 f0                 and    $0xfffffff0,%esp
     7        1f07:    83 ec 10                 sub    $0x10,%esp
     8        1f0a:    8b 5d 04                 mov    0x4(%ebp),%ebx
     9        1f0d:    89 1c 24                 mov    %ebx,(%esp)
    10        1f10:    8d 4d 08                 lea    0x8(%ebp),%ecx
    11        1f13:    89 4c 24 04              mov    %ecx,0x4(%esp)
    12        1f17:    83 c3 01                 add    $0x1,%ebx
    13        1f1a:    c1 e3 02                 shl    $0x2,%ebx
    14        1f1d:    01 cb                    add    %ecx,%ebx
    15        1f1f:    89 5c 24 08              mov    %ebx,0x8(%esp)
    16        1f23:    8b 03                    mov    (%ebx),%eax
    17        1f25:    83 c3 04                 add    $0x4,%ebx
    18        1f28:    85 c0                    test   %eax,%eax
    19        1f2a:    75 f7                    jne    1f23 <start+0x23>
    20        1f2c:    89 5c 24 0c              mov    %ebx,0xc(%esp)
    21        1f30:    e8 09 00 00 00           call   1f3e <_main>
    22        1f35:    89 04 24                 mov    %eax,(%esp)
    23        1f38:    e8 45 00 00 00           call   1f82 <.L1+0x24>
    24        1f3d:    f4                       hlt    
          
    25    00001f3e <_main>:
    26        1f3e:    55                       push   %ebp
    27        1f3f:    89 e5                    mov    %esp,%ebp
    28        1f41:    53                       push   %ebx
    29        1f42:    83 ec 24                 sub    $0x24,%esp
    30        1f45:    e8 00 00 00 00           call   1f4a <_main+0xc>
    31        1f4a:    5b                       pop    %ebx
    32        1f4b:    c7 45 f4 00 00 00 00     movl   $0x0,-0xc(%ebp)
    33        1f52:    e9 07 00 00 00           jmp    1f5e <.L1>
    34        1f57:    c7 45 f4 01 00 00 00     movl   $0x1,-0xc(%ebp)
          
    35    00001f5e <.L1>:
    36        1f5e:    8b 45 f4                 mov    -0xc(%ebp),%eax
    37        1f61:    89 44 24 04              mov    %eax,0x4(%esp)
    38        1f65:    8d 83 34 00 00 00        lea    0x34(%ebx),%eax
    39        1f6b:    89 04 24                 mov    %eax,(%esp)
    40        1f6e:    e8 15 00 00 00           call   1f88 <.L1+0x2a>
    41        1f73:    b8 00 00 00 00           mov    $0x0,%eax
    42        1f78:    83 c4 24                 add    $0x24,%esp
    43        1f7b:    5b                       pop    %ebx
    44        1f7c:    c9                       leave  
    45        1f7d:    c3                       ret    
          
    46    Disassembly of section .cstring:
          
    47    00001f7e <.cstring>:
    48        1f7e:    25                       .byte 0x25
    49        1f7f:    64 0a 00                 or     %fs:(%eax),%al
          
    50    Disassembly of section __TEXT.__symbol_stub:
          
    51    00001f82 <__TEXT.__symbol_stub>:
    52        1f82:    ff 25 1c 20 00 00        jmp    *0x201c
    53        1f88:    ff 25 20 20 00 00        jmp    *0x2020
          
    54    Disassembly of section __TEXT.__stub_helper:
          
    55    00001f8e < stub helpers>:
    56        1f8e:    68 18 20 00 00           push   $0x2018
    57        1f93:    ff 25 14 20 00 00        jmp    *0x2014
    58        1f99:    90                       nop
    59        1f9a:    68 0c 00 00 00           push   $0xc
    60        1f9f:    e9 ea ff ff ff           jmp    1f8e < stub helpers>
    61        1fa4:    68 00 00 00 00           push   $0x0
    62        1fa9:    e9 e0 ff ff ff           jmp    1f8e < stub helpers>
          
    63    Disassembly of section __TEXT.__unwind_info:
          
    64    00001fb0 <__TEXT.__unwind_info>:
    65        1fb0:    01 00                    add    %eax,(%eax)
    66        1fb2:    00 00                    add    %al,(%eax)
    67        1fb4:    1c 00                    sbb    $0x0,%al
    68        1fb6:    00 00                    add    %al,(%eax)
    69        1fb8:    00 00                    add    %al,(%eax)
    70        1fba:    00 00                    add    %al,(%eax)
    71        1fbc:    1c 00                    sbb    $0x0,%al
    72        1fbe:    00 00                    add    %al,(%eax)
    73        1fc0:    00 00                    add    %al,(%eax)
    74        1fc2:    00 00                    add    %al,(%eax)
    75        1fc4:    1c 00                    sbb    $0x0,%al
    76        1fc6:    00 00                    add    %al,(%eax)
    77        1fc8:    02 00                    add    (%eax),%al
    78        1fca:    00 00                    add    %al,(%eax)
    79        1fcc:    00 00                    add    %al,(%eax)
    80        1fce:    00 00                    add    %al,(%eax)
    81        1fd0:    34 00                    xor    $0x0,%al
    82        1fd2:    00 00                    add    %al,(%eax)
    83        1fd4:    34 00                    xor    $0x0,%al
    84        1fd6:    00 00                    add    %al,(%eax)
    85        1fd8:    f9                       stc    
    86        1fd9:    0f 00 00                 sldt   (%eax)
    87        1fdc:    00 00                    add    %al,(%eax)
    88        1fde:    00 00                    add    %al,(%eax)
    89        1fe0:    34 00                    xor    $0x0,%al
    90        1fe2:    00 00                    add    %al,(%eax)
    91        1fe4:    03 00                    add    (%eax),%eax
    92        1fe6:    00 00                    add    %al,(%eax)
    93        1fe8:    0c 00                    or     $0x0,%al
    94        1fea:    01 00                    add    %eax,(%eax)
    95        1fec:    10 00                    adc    %al,(%eax)
    96        1fee:    01 00                    add    %eax,(%eax)
    97        ...
          
    98    Disassembly of section __DATA.__program_vars:
          
    99    00002000 <_pvars>:
   100        2000:    00 10                    add    %dl,(%eax)
   101        2002:    00 00                    add    %al,(%eax)
   102        2004:    24 20                    and    $0x20,%al
   103        2006:    00 00                    add    %al,(%eax)
   104        2008:    28 20                    sub    %ah,(%eax)
   105        200a:    00 00                    add    %al,(%eax)
   106        200c:    2c 20                    sub    $0x20,%al
   107        200e:    00 00                    add    %al,(%eax)
   108        2010:    30 20                    xor    %ah,(%eax)
   109        ...
          
   110    Disassembly of section __DATA.__nl_symbol_ptr:
          
   111    00002014 <__DATA.__nl_symbol_ptr>:
   112        ...
          
   113    Disassembly of section __DATA.__la_symbol_ptr:
          
   114    0000201c <__DATA.__la_symbol_ptr>:
   115        201c:    a4                       movsb  %ds:(%esi),%es:(%edi)
   116        201d:    1f                       pop    %ds
   117        201e:    00 00                    add    %al,(%eax)
   118        2020:    9a                       .byte 0x9a
   119        2021:    1f                       pop    %ds
   120        ...
          
   121    Disassembly of section .data:
          
   122    00002024 <_NXArgc>:
   123        2024:    00 00                    add    %al,(%eax)
   124        ...
          
   125    00002028 <_NXArgv>:
   126        2028:    00 00                    add    %al,(%eax)
   127        ...
          
   128    0000202c <_environ>:
   129        202c:    00 00                    add    %al,(%eax)
   130        ...
          
   131    00002030 <___progname>:
   132        2030:    00 00                    add    %al,(%eax)
   133        ...
          
   134    Disassembly of section LC_UUID:
          
   135    00000000 <LC_UUID>:
   136       0:    6c                       insb   (%dx),%es:(%edi)
   137       1:    ea c6 57 f7 88 ae e9     ljmp   $0xe9ae,$0x88f757c6
   138       8:    7e 2d                    jle    37 <__mh_execute_header-0xfc9>
   139       a:    df 8b ee 92 93 2b        fisttp 0x2b9392ee(%ebx)
          
   140    Disassembly of section LC_THREAD.x86_THREAD_STATE32.0:
          
   141    00000000 <LC_THREAD.x86_THREAD_STATE32.0>:
   142        ...
   143      28:    00 1f                    add    %bl,(%edi)
   144        ...

```

See line 33 of the objdump. Since you have no way of knowing beforehand what the absolute address will be, you must use labels.

Also don't post huge screenshots like that, especially when it is text data that can be copy-and-pasted.

---

