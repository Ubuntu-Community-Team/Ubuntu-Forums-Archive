---
title: "Question"
date: 2011-07-14
forum: Programming Talk
---

### Post by Drenriza on 2011-07-14
Hi all.

So i have been wondering, about the following.
When you write a script or a program. What defines the script or program?

When is a script a script, or when is a program a program. Does the language it's written in define what it is?

Hope you know, what i mean.

Kind regards.

---

### Post by Phrea on 2011-07-14
OT: Topics are meant to shortly describe the question.

---

### Post by An Sanct on 2011-07-14
A nice mind blowing question :)

In my opinion:

-A script is a small piece of code, that can be executed, but still easily modified - with a simple text editor.

-A program is slightly complexer and needs a compiler, to convert (translate, if you want) the source from its textual - human readable form into some binary - processor readable form.

---

### Post by Nytram on 2011-07-14
I agree with An Sanct, I don't know if it's technically correct, but I think of a program as being compiled, while scripts are interpreted - generally speaking.

eg

JavaSCRIPT is interpreted.
Java is compiled.

---

### Post by An Sanct on 2011-07-14
Well, its how I see it :) I will be glad to hear any opinions.

---

### Post by Bachstelze on 2011-07-14
Frankly, who cares?

---

### Post by Drenriza on 2011-07-14
> **Bachstelze said:**
> Frankly, who cares?

Frankly, please don't post then. Shu Shu

---

### Post by An Sanct on 2011-07-14
> **Bachstelze said:**
> Frankly, who cares?

That is a deep thought! :) Thank you for sharing ;)

---

### Post by Drenriza on 2011-07-14
> **Phrea said:**
> OT: Topics are meant to shortly describe the question.

Your correct. But to be honest, i couldn't really think of anything to add to the topic/title box. If you have a suggestion i change it ,)

---

### Post by Bachstelze on 2011-07-14
> **An Sanct said:**
> That is a deep thought! :) Thank you for sharing ;)

Thank you. The OP question is very deep too, so I had to match it. :)

---

### Post by Drenriza on 2011-07-14
> **An Sanct said:**
> A nice mind blowing question :)

In my opinion:

-A script is a small piece of code, that can be executed, but still easily modified - with a simple text editor.

-A program is slightly complexer and needs a compiler, to convert (translate, if you want) the source from its textual - human readable form into some binary - processor readable form.

That makes sense. Not a biggie but as far as i know (and i can be VERY wrong) it is possible to write c code in for example vim. But sure still needs to be compiled.

Thanks An Sanct.

---

### Post by haqking on 2011-07-14
not that Wikipedia is always correct but:

[**Script**]("http://en.wikipedia.org/wiki/Script_%28computing%29") :
  [INDENT]   "Scripts" are distinct from the core   code of the application, which is   usually written in a different   language, and are often created or at   least modified by the end-user.    
Scripts are often interpreted from   source code or bytecode, whereas the   applications they control are   traditionally compiled  to native   machine code.
 [/INDENT]  [**Program**]("http://en.wikipedia.org/wiki/Computer_program") :
  [INDENT]   The program has an executable form   that the computer can use directly to   execute the instructions. 
The same   program in its human-readable source   code form, from which executable    programs are derived *(e.g., compiled)*
 [/INDENT]

---

### Post by Bachstelze on 2011-07-14
> **Drenriza said:**
> it is possible to write c code in for example vim.

It is possible but only wimps do it.  Real people write their binaries with cat.

---

### Post by Bachstelze on 2011-07-14
> **haqking said:**
> not that Wikipedia is always correct but:

[**Script**]("http://en.wikipedia.org/wiki/Script_%28computing%29") :
  [INDENT]   "Scripts" are distinct from the core   code of the application, which is   usually written in a different   language, and are often created or at   least modified by the end-user.    
Scripts are often interpreted from   source code or bytecode, whereas the   applications they control are   traditionally compiled  to native   machine code.
 [/INDENT]  [**Program**]("http://en.wikipedia.org/wiki/Computer_program") :
  [INDENT]   The program has an executable form   that the computer can use directly to   execute the instructions. 
The same   program in its human-readable source   code form, from which executable    programs are derived *(e.g., compiled)*
 [/INDENT]

Meh, what about Python, then?  Often, a Python program is the core application, and the only purpose of the interpreter is to run it.  But it is not compiled and can be edited like a "script".

Face it, people, the script vs. program distinction is context-dependent, there is no clear-cut answer. Not like it matters, though...

---

### Post by An Sanct on 2011-07-14
> **Drenriza said:**
> That makes sense. Not a biggie but as far as i know (and i can be VERY wrong) it is possible to write c code in for example vim. But sure still needs to be compiled.

Thanks An Sanct.

There is no limitation to where you write your code, it can be any text editor. But the result has to be compiled, to make it work and the output is not modifiable (binary)

PS. Okay, I know, you can still hex edit binaries, but there is no guarantee, that it will still work. 
Also, it is preferable to use the editor, that is (if it is) present with the programming language, mostly for debug reasons and source code highlighting and auto-completion etc.

But real programmers use vim ;)

---

### Post by Bachstelze on 2011-07-14
> **An Sanct said:**
> There is no limitation to where you write your code, it can be any text editor. But the result has to be compiled, to make it work and the output is not modifiable (binary)

PS. Okay, I know, you can still hex edit binaries, but there is no guarantee, that it will still work. 

When you edit a script, there is also no guarantee that it will still work.

---

### Post by An Sanct on 2011-07-14
This thread is kind of leaning toward trolling ... yet still, I will reply (probably for the last time ...)

simple example [taken here]("http://refactormycode.com/codes/521-simple-for-loop")

source: modifiable
```
#include <iostream.h>

int main() {
        
        int num;
        cout << "\n\nHow many characters do you want me to print per line: ";
        cin >> num;

        int c = 0;
        char a;
        for (a = 'A'; a <= 'Z'; a++) {  
                c++;
                cout << a << '\t' << (c % num == 0 ? "\n" : "");
        }

        cout << "\n\nHit enter to terminate: ";
        cin.ignore(); cin.ignore();

        return 0;
}
```
binary: not modifiable
once gotten from the compiler, you cannot - for example, localize this function any more.

I'm in a hurry, I hope I was clear enough.
Over and out! ):P

---

### Post by s.fox on 2011-07-14
Interesting question.  To me I think it would be this:

> 
A script is a single code module that is  designed to fullfill one function.  

A program is a collection of these  modules that collectively solve a user need.


Additionally, thread moved to **[[B]Programming Talk**]("http://ubuntuforums.org/forumdisplay.php?f=39")[/B]

---

### Post by Bachstelze on 2011-07-14
> **An Sanct said:**
> This thread is kind of leaning toward trolling ... yet still, I will reply (probably for the last time ...)

simple example [taken here]("http://refactormycode.com/codes/521-simple-for-loop")

source: modifiable
```
#include <iostream.h>

int main() {
        
        int num;
        cout << "\n\nHow many characters do you want me to print per line: ";
        cin >> num;

        int c = 0;
        char a;
        for (a = 'A'; a <= 'Z'; a++) {  
                c++;
                cout << a << '\t' << (c % num == 0 ? "\n" : "");
        }

        cout << "\n\nHit enter to terminate: ";
        cin.ignore(); cin.ignore();

        return 0;
}
```
binary: not modifiable
once gotten from the compiler, you cannot - for example, localize this function any more.

I'm in a hurry, I hope I was clear enough.
Over and out! ):P

Maybe you would be a bit more credible if you pasted correct code, because it's obvious you don't know what you are talking about. I can localize this function very well, there it is on lines 133 to 201 of the objdump:

```
firas@aoba ~ % cat test.cpp 
#include <iostream.h>

int main() {
        
        int num;
        cout << "\n\nHow many characters do you want me to print per line: ";
        cin >> num;

        int c = 0;
        char a;
        for (a = 'A'; a <= 'Z'; a++) {  
                c++;
                cout << a << '\t' << (c % num == 0 ? "\n" : "");
        }

        cout << "\n\nHit enter to terminate: ";
        cin.ignore(); cin.ignore();

        return 0;
}
firas@aoba ~ % g++ test.cpp
In file included from /usr/include/c++/4.2.1/backward/iostream.h:31,
                 from test.cpp:1:
/usr/include/c++/4.2.1/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
firas@aoba ~ % objdump -d a.out| nl
      	
     1	a.out:     file format mach-o-x86-64
      	
      	
     2	Disassembly of section .text:
      	
     3	0000000100000a74 <__Z41__static_initialization_and_destruction_0ii>:
     4	   100000a74:	55                   	push   %rbp
     5	   100000a75:	48 89 e5             	mov    %rsp,%rbp
     6	   100000a78:	48 83 ec 10          	sub    $0x10,%rsp
     7	   100000a7c:	89 7d fc             	mov    %edi,-0x4(%rbp)
     8	   100000a7f:	89 75 f8             	mov    %esi,-0x8(%rbp)
     9	   100000a82:	83 7d fc 01          	cmpl   $0x1,-0x4(%rbp)
    10	   100000a86:	75 2d                	jne    100000ab5 <__Z41__static_initialization_and_destruction_0ii+0x41>
    11	   100000a88:	81 7d f8 ff ff 00 00 	cmpl   $0xffff,-0x8(%rbp)
    12	   100000a8f:	75 24                	jne    100000ab5 <__Z41__static_initialization_and_destruction_0ii+0x41>
    13	   100000a91:	48 8d 3d 38 06 00 00 	lea    0x638(%rip),%rdi        # 1000010d0 <__ZStL8__ioinit>
    14	   100000a98:	e8 b7 02 00 00       	callq  100000d54 <__ZNSt8ios_base4InitC1Ev$stub>
    15	   100000a9d:	48 8d 15 5c f5 ff ff 	lea    -0xaa4(%rip),%rdx        # 100000000 <__mh_execute_header>
    16	   100000aa4:	be 00 00 00 00       	mov    $0x0,%esi
    17	   100000aa9:	48 8d 3d 72 02 00 00 	lea    0x272(%rip),%rdi        # 100000d22 <___tcf_0>
    18	   100000ab0:	e8 bd 02 00 00       	callq  100000d72 <___cxa_atexit$stub>
    19	   100000ab5:	c9                   	leaveq 
    20	   100000ab6:	c3                   	retq   
      	
    21	0000000100000ab7 <__GLOBAL__I_main>:
    22	   100000ab7:	55                   	push   %rbp
    23	   100000ab8:	48 89 e5             	mov    %rsp,%rbp
    24	   100000abb:	be ff ff 00 00       	mov    $0xffff,%esi
    25	   100000ac0:	bf 01 00 00 00       	mov    $0x1,%edi
    26	   100000ac5:	e8 aa ff ff ff       	callq  100000a74 <__Z41__static_initialization_and_destruction_0ii>
    27	   100000aca:	c9                   	leaveq 
    28	   100000acb:	c3                   	retq   
      	
    29	0000000100000acc <start>:
    30	   100000acc:	6a 00                	pushq  $0x0
    31	   100000ace:	48 89 e5             	mov    %rsp,%rbp
    32	   100000ad1:	48 83 e4 f0          	and    $0xfffffffffffffff0,%rsp
    33	   100000ad5:	48 8b 7d 08          	mov    0x8(%rbp),%rdi
    34	   100000ad9:	48 8d 75 10          	lea    0x10(%rbp),%rsi
    35	   100000add:	89 fa                	mov    %edi,%edx
    36	   100000adf:	83 c2 01             	add    $0x1,%edx
    37	   100000ae2:	c1 e2 03             	shl    $0x3,%edx
    38	   100000ae5:	48 01 f2             	add    %rsi,%rdx
    39	   100000ae8:	48 89 d1             	mov    %rdx,%rcx
    40	   100000aeb:	eb 04                	jmp    100000af1 <start+0x25>
    41	   100000aed:	48 83 c1 08          	add    $0x8,%rcx
    42	   100000af1:	48 83 39 00          	cmpq   $0x0,(%rcx)
    43	   100000af5:	75 f6                	jne    100000aed <start+0x21>
    44	   100000af7:	48 83 c1 08          	add    $0x8,%rcx
    45	   100000afb:	e8 1f 01 00 00       	callq  100000c1f <_main>
    46	   100000b00:	89 c7                	mov    %eax,%edi
    47	   100000b02:	e8 71 02 00 00       	callq  100000d78 <_exit$stub>
    48	   100000b07:	f4                   	hlt    
      	
    49	0000000100000b08 <__ZStL17__verify_groupingPKcmRKSs>:
    50	   100000b08:	55                   	push   %rbp
    51	   100000b09:	48 89 e5             	mov    %rsp,%rbp
    52	   100000b0c:	53                   	push   %rbx
    53	   100000b0d:	48 83 ec 58          	sub    $0x58,%rsp
    54	   100000b11:	48 89 7d b8          	mov    %rdi,-0x48(%rbp)
    55	   100000b15:	48 89 75 b0          	mov    %rsi,-0x50(%rbp)
    56	   100000b19:	48 89 55 a8          	mov    %rdx,-0x58(%rbp)
    57	   100000b1d:	48 8b 7d a8          	mov    -0x58(%rbp),%rdi
    58	   100000b21:	e8 16 02 00 00       	callq  100000d3c <__ZNKSs4sizeEv$stub>
    59	   100000b26:	48 ff c8             	dec    %rax
    60	   100000b29:	48 89 45 e0          	mov    %rax,-0x20(%rbp)
    61	   100000b2d:	48 8b 45 b0          	mov    -0x50(%rbp),%rax
    62	   100000b31:	48 ff c8             	dec    %rax
    63	   100000b34:	48 89 45 d0          	mov    %rax,-0x30(%rbp)
    64	   100000b38:	48 8d 75 d0          	lea    -0x30(%rbp),%rsi
    65	   100000b3c:	48 8d 7d e0          	lea    -0x20(%rbp),%rdi
    66	   100000b40:	e8 1b 02 00 00       	callq  100000d60 <__ZSt3minImERKT_S2_S2_$stub>
    67	   100000b45:	48 8b 00             	mov    (%rax),%rax
    68	   100000b48:	48 89 45 d8          	mov    %rax,-0x28(%rbp)
    69	   100000b4c:	48 8b 45 e0          	mov    -0x20(%rbp),%rax
    70	   100000b50:	48 89 45 c8          	mov    %rax,-0x38(%rbp)
    71	   100000b54:	c6 45 ef 01          	movb   $0x1,-0x11(%rbp)
    72	   100000b58:	48 c7 45 c0 00 00 00 	movq   $0x0,-0x40(%rbp)
    73	   100000b5f:	00 
    74	   100000b60:	eb 2b                	jmp    100000b8d <__ZStL17__verify_groupingPKcmRKSs+0x85>
    75	   100000b62:	48 8b 75 c8          	mov    -0x38(%rbp),%rsi
    76	   100000b66:	48 8b 7d a8          	mov    -0x58(%rbp),%rdi
    77	   100000b6a:	e8 d3 01 00 00       	callq  100000d42 <__ZNKSsixEm$stub>
    78	   100000b6f:	0f b6 10             	movzbl (%rax),%edx
    79	   100000b72:	48 8b 45 c0          	mov    -0x40(%rbp),%rax
    80	   100000b76:	48 03 45 b8          	add    -0x48(%rbp),%rax
    81	   100000b7a:	0f b6 00             	movzbl (%rax),%eax
    82	   100000b7d:	38 c2                	cmp    %al,%dl
    83	   100000b7f:	0f 94 c0             	sete   %al
    84	   100000b82:	88 45 ef             	mov    %al,-0x11(%rbp)
    85	   100000b85:	48 ff 4d c8          	decq   -0x38(%rbp)
    86	   100000b89:	48 ff 45 c0          	incq   -0x40(%rbp)
    87	   100000b8d:	48 8b 45 c0          	mov    -0x40(%rbp),%rax
    88	   100000b91:	48 3b 45 d8          	cmp    -0x28(%rbp),%rax
    89	   100000b95:	73 2f                	jae    100000bc6 <__ZStL17__verify_groupingPKcmRKSs+0xbe>
    90	   100000b97:	80 7d ef 00          	cmpb   $0x0,-0x11(%rbp)
    91	   100000b9b:	75 c5                	jne    100000b62 <__ZStL17__verify_groupingPKcmRKSs+0x5a>
    92	   100000b9d:	eb 27                	jmp    100000bc6 <__ZStL17__verify_groupingPKcmRKSs+0xbe>
    93	   100000b9f:	48 8b 75 c8          	mov    -0x38(%rbp),%rsi
    94	   100000ba3:	48 8b 7d a8          	mov    -0x58(%rbp),%rdi
    95	   100000ba7:	e8 96 01 00 00       	callq  100000d42 <__ZNKSsixEm$stub>
    96	   100000bac:	0f b6 10             	movzbl (%rax),%edx
    97	   100000baf:	48 8b 45 d8          	mov    -0x28(%rbp),%rax
    98	   100000bb3:	48 03 45 b8          	add    -0x48(%rbp),%rax
    99	   100000bb7:	0f b6 00             	movzbl (%rax),%eax
   100	   100000bba:	38 c2                	cmp    %al,%dl
   101	   100000bbc:	0f 94 c0             	sete   %al
   102	   100000bbf:	88 45 ef             	mov    %al,-0x11(%rbp)
   103	   100000bc2:	48 ff 4d c8          	decq   -0x38(%rbp)
   104	   100000bc6:	48 83 7d c8 00       	cmpq   $0x0,-0x38(%rbp)
   105	   100000bcb:	74 06                	je     100000bd3 <__ZStL17__verify_groupingPKcmRKSs+0xcb>
   106	   100000bcd:	80 7d ef 00          	cmpb   $0x0,-0x11(%rbp)
   107	   100000bd1:	75 cc                	jne    100000b9f <__ZStL17__verify_groupingPKcmRKSs+0x97>
   108	   100000bd3:	48 8b 45 d8          	mov    -0x28(%rbp),%rax
   109	   100000bd7:	48 03 45 b8          	add    -0x48(%rbp),%rax
   110	   100000bdb:	0f b6 00             	movzbl (%rax),%eax
   111	   100000bde:	84 c0                	test   %al,%al
   112	   100000be0:	7e 32                	jle    100000c14 <__ZStL17__verify_groupingPKcmRKSs+0x10c>
   113	   100000be2:	0f b6 5d ef          	movzbl -0x11(%rbp),%ebx
   114	   100000be6:	48 8b 7d a8          	mov    -0x58(%rbp),%rdi
   115	   100000bea:	be 00 00 00 00       	mov    $0x0,%esi
   116	   100000bef:	e8 4e 01 00 00       	callq  100000d42 <__ZNKSsixEm$stub>
   117	   100000bf4:	0f b6 10             	movzbl (%rax),%edx
   118	   100000bf7:	48 8b 45 d8          	mov    -0x28(%rbp),%rax
   119	   100000bfb:	48 03 45 b8          	add    -0x48(%rbp),%rax
   120	   100000bff:	0f b6 00             	movzbl (%rax),%eax
   121	   100000c02:	38 c2                	cmp    %al,%dl
   122	   100000c04:	0f 9e c0             	setle  %al
   123	   100000c07:	0f b6 c0             	movzbl %al,%eax
   124	   100000c0a:	21 d8                	and    %ebx,%eax
   125	   100000c0c:	85 c0                	test   %eax,%eax
   126	   100000c0e:	0f 95 c0             	setne  %al
   127	   100000c11:	88 45 ef             	mov    %al,-0x11(%rbp)
   128	   100000c14:	0f b6 45 ef          	movzbl -0x11(%rbp),%eax
   129	   100000c18:	48 83 c4 58          	add    $0x58,%rsp
   130	   100000c1c:	5b                   	pop    %rbx
   131	   100000c1d:	c9                   	leaveq 
   132	   100000c1e:	c3                   	retq   
      	
   133	0000000100000c1f <_main>:
   134	   100000c1f:	55                   	push   %rbp
   135	   100000c20:	48 89 e5             	mov    %rsp,%rbp
   136	   100000c23:	48 83 ec 20          	sub    $0x20,%rsp
   137	   100000c27:	48 8d 35 52 01 00 00 	lea    0x152(%rip),%rsi        # 100000d80 <_exit$stub+0x8>
   138	   100000c2e:	48 8b 3d 03 04 00 00 	mov    0x403(%rip),%rdi        # 100001038 <__ZSt4cout$stub>
   139	   100000c35:	e8 2c 01 00 00       	callq  100000d66 <__ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc$stub>
   140	   100000c3a:	48 8d 75 f8          	lea    -0x8(%rbp),%rsi
   141	   100000c3e:	48 8b 3d eb 03 00 00 	mov    0x3eb(%rip),%rdi        # 100001030 <__ZSt3cin$stub>
   142	   100000c45:	e8 04 01 00 00       	callq  100000d4e <__ZNSirsERi$stub>
   143	   100000c4a:	c7 45 f4 00 00 00 00 	movl   $0x0,-0xc(%rbp)
   144	   100000c51:	c6 45 ff 41          	movb   $0x41,-0x1(%rbp)
   145	   100000c55:	eb 5c                	jmp    100000cb3 <_main+0x94>
   146	   100000c57:	ff 45 f4             	incl   -0xc(%rbp)
   147	   100000c5a:	8b 45 f8             	mov    -0x8(%rbp),%eax
   148	   100000c5d:	8b 55 f4             	mov    -0xc(%rbp),%edx
   149	   100000c60:	89 c1                	mov    %eax,%ecx
   150	   100000c62:	89 d0                	mov    %edx,%eax
   151	   100000c64:	c1 fa 1f             	sar    $0x1f,%edx
   152	   100000c67:	f7 f9                	idiv   %ecx
   153	   100000c69:	89 d0                	mov    %edx,%eax
   154	   100000c6b:	85 c0                	test   %eax,%eax
   155	   100000c6d:	75 0d                	jne    100000c7c <_main+0x5d>
   156	   100000c6f:	48 8d 05 43 01 00 00 	lea    0x143(%rip),%rax        # 100000db9 <_exit$stub+0x41>
   157	   100000c76:	48 89 45 e8          	mov    %rax,-0x18(%rbp)
   158	   100000c7a:	eb 0b                	jmp    100000c87 <_main+0x68>
   159	   100000c7c:	48 8d 0d 38 01 00 00 	lea    0x138(%rip),%rcx        # 100000dbb <_exit$stub+0x43>
   160	   100000c83:	48 89 4d e8          	mov    %rcx,-0x18(%rbp)
   161	   100000c87:	0f be 75 ff          	movsbl -0x1(%rbp),%esi
   162	   100000c8b:	48 8b 3d a6 03 00 00 	mov    0x3a6(%rip),%rdi        # 100001038 <__ZSt4cout$stub>
   163	   100000c92:	e8 d5 00 00 00       	callq  100000d6c <__ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_c$stub>
   164	   100000c97:	48 89 c7             	mov    %rax,%rdi
   165	   100000c9a:	be 09 00 00 00       	mov    $0x9,%esi
   166	   100000c9f:	e8 c8 00 00 00       	callq  100000d6c <__ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_c$stub>
   167	   100000ca4:	48 89 c7             	mov    %rax,%rdi
   168	   100000ca7:	48 8b 75 e8          	mov    -0x18(%rbp),%rsi
   169	   100000cab:	e8 b6 00 00 00       	callq  100000d66 <__ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc$stub>
   170	   100000cb0:	fe 45 ff             	incb   -0x1(%rbp)
   171	   100000cb3:	80 7d ff 5a          	cmpb   $0x5a,-0x1(%rbp)
   172	   100000cb7:	7e 9e                	jle    100000c57 <_main+0x38>
   173	   100000cb9:	48 8d 35 fc 00 00 00 	lea    0xfc(%rip),%rsi        # 100000dbc <_exit$stub+0x44>
   174	   100000cc0:	48 8b 3d 71 03 00 00 	mov    0x371(%rip),%rdi        # 100001038 <__ZSt4cout$stub>
   175	   100000cc7:	e8 9a 00 00 00       	callq  100000d66 <__ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc$stub>
   176	   100000ccc:	48 8b 3d 5d 03 00 00 	mov    0x35d(%rip),%rdi        # 100001030 <__ZSt3cin$stub>
   177	   100000cd3:	e8 70 00 00 00       	callq  100000d48 <__ZNSi6ignoreEv$stub>
   178	   100000cd8:	48 8b 3d 51 03 00 00 	mov    0x351(%rip),%rdi        # 100001030 <__ZSt3cin$stub>
   179	   100000cdf:	e8 64 00 00 00       	callq  100000d48 <__ZNSi6ignoreEv$stub>
   180	   100000ce4:	b8 00 00 00 00       	mov    $0x0,%eax
   181	   100000ce9:	c9                   	leaveq 
   182	   100000cea:	c3                   	retq   
      	
   183	0000000100000ceb <__ZSt3minImERKT_S2_S2_>:
   184	   100000ceb:	55                   	push   %rbp
   185	   100000cec:	48 89 e5             	mov    %rsp,%rbp
   186	   100000cef:	48 89 7d f8          	mov    %rdi,-0x8(%rbp)
   187	   100000cf3:	48 89 75 f0          	mov    %rsi,-0x10(%rbp)
   188	   100000cf7:	48 8b 45 f0          	mov    -0x10(%rbp),%rax
   189	   100000cfb:	48 8b 10             	mov    (%rax),%rdx
   190	   100000cfe:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
   191	   100000d02:	48 8b 00             	mov    (%rax),%rax
   192	   100000d05:	48 39 c2             	cmp    %rax,%rdx
   193	   100000d08:	73 0a                	jae    100000d14 <__ZSt3minImERKT_S2_S2_+0x29>
   194	   100000d0a:	48 8b 45 f0          	mov    -0x10(%rbp),%rax
   195	   100000d0e:	48 89 45 e8          	mov    %rax,-0x18(%rbp)
   196	   100000d12:	eb 08                	jmp    100000d1c <__ZSt3minImERKT_S2_S2_+0x31>
   197	   100000d14:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
   198	   100000d18:	48 89 45 e8          	mov    %rax,-0x18(%rbp)
   199	   100000d1c:	48 8b 45 e8          	mov    -0x18(%rbp),%rax
   200	   100000d20:	c9                   	leaveq 
   201	   100000d21:	c3                   	retq   
      	
   202	0000000100000d22 <___tcf_0>:
   203	   100000d22:	55                   	push   %rbp
   204	   100000d23:	48 89 e5             	mov    %rsp,%rbp
   205	   100000d26:	48 83 ec 10          	sub    $0x10,%rsp
   206	   100000d2a:	48 89 7d f8          	mov    %rdi,-0x8(%rbp)
   207	   100000d2e:	48 8d 3d 9b 03 00 00 	lea    0x39b(%rip),%rdi        # 1000010d0 <__ZStL8__ioinit>
   208	   100000d35:	e8 20 00 00 00       	callq  100000d5a <__ZNSt8ios_base4InitD1Ev$stub>
   209	   100000d3a:	c9                   	leaveq 
   210	   100000d3b:	c3                   	retq   
      	
   211	Disassembly of section __TEXT.__symbol_stub1:
      	
   212	0000000100000d3c <__ZNKSs4sizeEv$stub>:
   213	   100000d3c:	ff 25 16 03 00 00    	jmpq   *0x316(%rip)        # 100001058 <__ZNKSs4sizeEv$stub>
      	
   214	0000000100000d42 <__ZNKSsixEm$stub>:
   215	   100000d42:	ff 25 18 03 00 00    	jmpq   *0x318(%rip)        # 100001060 <__ZNKSsixEm$stub>
      	
   216	0000000100000d48 <__ZNSi6ignoreEv$stub>:
   217	   100000d48:	ff 25 1a 03 00 00    	jmpq   *0x31a(%rip)        # 100001068 <__ZNSi6ignoreEv$stub>
      	
   218	0000000100000d4e <__ZNSirsERi$stub>:
   219	   100000d4e:	ff 25 1c 03 00 00    	jmpq   *0x31c(%rip)        # 100001070 <__ZNSirsERi$stub>
      	
   220	0000000100000d54 <__ZNSt8ios_base4InitC1Ev$stub>:
   221	   100000d54:	ff 25 1e 03 00 00    	jmpq   *0x31e(%rip)        # 100001078 <__ZNSt8ios_base4InitC1Ev$stub>
      	
   222	0000000100000d5a <__ZNSt8ios_base4InitD1Ev$stub>:
   223	   100000d5a:	ff 25 20 03 00 00    	jmpq   *0x320(%rip)        # 100001080 <__ZNSt8ios_base4InitD1Ev$stub>
      	
   224	0000000100000d60 <__ZSt3minImERKT_S2_S2_$stub>:
   225	   100000d60:	ff 25 22 03 00 00    	jmpq   *0x322(%rip)        # 100001088 <__ZSt3minImERKT_S2_S2_$stub>
      	
   226	0000000100000d66 <__ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc$stub>:
   227	   100000d66:	ff 25 24 03 00 00    	jmpq   *0x324(%rip)        # 100001090 <__ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc$stub>
      	
   228	0000000100000d6c <__ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_c$stub>:
   229	   100000d6c:	ff 25 26 03 00 00    	jmpq   *0x326(%rip)        # 100001098 <__ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_c$stub>
      	
   230	0000000100000d72 <___cxa_atexit$stub>:
   231	   100000d72:	ff 25 28 03 00 00    	jmpq   *0x328(%rip)        # 1000010a0 <___cxa_atexit$stub>
      	
   232	0000000100000d78 <_exit$stub>:
   233	   100000d78:	ff 25 2a 03 00 00    	jmpq   *0x32a(%rip)        # 1000010a8 <_exit$stub>
      	
   234	Disassembly of section __TEXT.__stub_helper:
      	
   235	0000000100000dd7 < stub helpers>:
   236	   100000dd7:	4c 8d 1d 72 02 00 00 	lea    0x272(%rip),%r11        # 100001050 <>
   237	   100000dde:	41 53                	push   %r11
   238	   100000de0:	ff 25 62 02 00 00    	jmpq   *0x262(%rip)        # 100001048 <>
   239	   100000de6:	90                   	nop
   240	   100000de7:	68 00 00 00 00       	pushq  $0x0
   241	   100000dec:	e9 e6 ff ff ff       	jmpq   100000dd7 < stub helpers>
   242	   100000df1:	68 15 00 00 00       	pushq  $0x15
   243	   100000df6:	e9 dc ff ff ff       	jmpq   100000dd7 < stub helpers>
   244	   100000dfb:	68 8e 00 00 00       	pushq  $0x8e
   245	   100000e00:	e9 d2 ff ff ff       	jmpq   100000dd7 < stub helpers>
   246	   100000e05:	68 ce 00 00 00       	pushq  $0xce
   247	   100000e0a:	e9 c8 ff ff ff       	jmpq   100000dd7 < stub helpers>
   248	   100000e0f:	68 0c 01 00 00       	pushq  $0x10c
   249	   100000e14:	e9 be ff ff ff       	jmpq   100000dd7 < stub helpers>
   250	   100000e19:	68 21 01 00 00       	pushq  $0x121
   251	   100000e1e:	e9 b4 ff ff ff       	jmpq   100000dd7 < stub helpers>
   252	   100000e23:	68 6e 00 00 00       	pushq  $0x6e
   253	   100000e28:	e9 aa ff ff ff       	jmpq   100000dd7 < stub helpers>
   254	   100000e2d:	68 4f 00 00 00       	pushq  $0x4f
   255	   100000e32:	e9 a0 ff ff ff       	jmpq   100000dd7 < stub helpers>
   256	   100000e37:	68 3d 00 00 00       	pushq  $0x3d
   257	   100000e3c:	e9 96 ff ff ff       	jmpq   100000dd7 < stub helpers>
   258	   100000e41:	68 27 00 00 00       	pushq  $0x27
   259	   100000e46:	e9 8c ff ff ff       	jmpq   100000dd7 < stub helpers>
      	
   260	Disassembly of section __TEXT.__unwind_info:
      	
   261	0000000100000e50 <__TEXT.__unwind_info>:
   262	   100000e50:	01 00                	add    %eax,(%rax)
   263	   100000e52:	00 00                	add    %al,(%rax)
   264	   100000e54:	1c 00                	sbb    $0x0,%al
   265	   100000e56:	00 00                	add    %al,(%rax)
   266	   100000e58:	02 00                	add    (%rax),%al
   267	   100000e5a:	00 00                	add    %al,(%rax)
   268	   100000e5c:	24 00                	and    $0x0,%al
   269	   100000e5e:	00 00                	add    %al,(%rax)
   270	   100000e60:	01 00                	add    %eax,(%rax)
   271	   100000e62:	00 00                	add    %al,(%rax)
   272	   100000e64:	28 00                	sub    %al,(%rax)
   273	   100000e66:	00 00                	add    %al,(%rax)
   274	   100000e68:	02 00                	add    (%rax),%al
   275		...
   276	   100000e72:	00 11                	add    %dl,(%rcx)
   277	   100000e74:	40 10 00             	adc    %al,(%rax)
   278	   100000e77:	00 00                	add    %al,(%rax)
   279	   100000e79:	00 00                	add    %al,(%rax)
   280	   100000e7b:	00 40 00             	add    %al,0x0(%rax)
   281	   100000e7e:	00 00                	add    %al,(%rax)
   282	   100000e80:	40 00 00             	add    %al,(%rax)
   283	   100000e83:	00 f9                	add    %bh,%cl
   284	   100000e85:	0f 00 00             	sldt   (%rax)
   285	   100000e88:	00 00                	add    %al,(%rax)
   286	   100000e8a:	00 00                	add    %al,(%rax)
   287	   100000e8c:	40 00 00             	add    %al,(%rax)
   288	   100000e8f:	00 03                	add    %al,(%rbx)
   289	   100000e91:	00 00                	add    %al,(%rax)
   290	   100000e93:	00 0c 00             	add    %cl,(%rax,%rax,1)
   291	   100000e96:	06                   	(bad)  
   292	   100000e97:	00 24 00             	add    %ah,(%rax,%rax,1)
   293	   100000e9a:	01 00                	add    %eax,(%rax)
   294	   100000e9c:	00 00                	add    %al,(%rax)
   295	   100000e9e:	00 00                	add    %al,(%rax)
   296	   100000ea0:	74 0a                	je     100000eac < stub helpers+0xd5>
   297	   100000ea2:	00 01                	add    %al,(%rcx)
   298	   100000ea4:	cc                   	int3   
   299	   100000ea5:	0a 00                	or     (%rax),%al
   300	   100000ea7:	00 08                	add    %cl,(%rax)
   301	   100000ea9:	0b 00                	or     (%rax),%eax
   302	   100000eab:	02 1f                	add    (%rdi),%bl
   303	   100000ead:	0c 00                	or     $0x0,%al
   304	   100000eaf:	01 3c 0d 00 00 01 00 	add    %edi,0x10000(,%rcx,1)
   305	   100000eb6:	01 11                	add    %edx,(%rcx)

```

---

### Post by Tony Flury on 2011-07-14
Personally I think that the distinction between a script and a programm has to do with as much how it is written, rather than the language it is written in.

For me a script is something (in almost any language) that I cut together in a few minutes to do a specific single job - i might run that "script" multiple times, but it is a script. Most of my scripts are written in python (as that is the language I know), but in my time i have cut together a script in bash, or even in C - a one off file processing do-dad - took about 10 minutes to do and was easier to write than trying to learn grep/awk etc.

A programm is any complex application that can do a set of functions which are related - you can write a program in any language - it does not have to be compiled to native code - which actually excludes Java (as that compiles to bytecode which needs the JVM to execute).

---

### Post by nvteighen on 2011-07-14
Technically, a script is a program: it consists in a series of statements written in some formal artificial language that represents a solution for a computable problem. It doesn't matter whether compiled or interpreted, those are implementation details external to the program itself. Neither matter the length or amount of functions defined: one single function could be a program.

It's possible to write a Bash implementation on top of Common Lisp macros (but nobody said easy nor practical) and then use that to compile Bash to binary (a so-called Lisp image)... Or, when written on paper, code written in C is as impossible to execute as if it was written in Guile or zsh.

Informally, people refer as scripts to programs that are run by interpreters or written in shell scripting languages whose usual implementations lack any FFI. Again, those are issues external to the code itself, but to the specific implementation used to execute it. So, code in Bash, sh, ksh, would be scripts. Then, there's some gray zone where things become confusing in informal programming speech: Perl, Python, Javascript are considered scripting languages by some and "full-fledged" programming languages by others (like myself). And then, nobody seems to call C, C++, Common Lisp, Smalltalk-80, Haskell, etc. scripting languages.

But that's valid for informal programming speech like what we do here in these forums or in an IRC channel... those are ways of expressing things that have been developed mostly by chance and social customs rather than by technical CS knowledge. But when discussing a CS paper, you better don't make that distinction (you rather have to make other kind of distinctions).

---

### Post by cgroza on 2011-07-14
According to some people's logic, a 20 000 line text editor written in python would be still considered a script... Something is fishy here.

---

### Post by nvteighen on 2011-07-14
> **cgroza said:**
> According to some people's logic, a 20 000 line text editor written in python would be still considered a script... Something is fishy here.

Very well said :)

---

