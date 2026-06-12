---
title: "How to sort out ??"
date: 2006-02-06
forum: Packaging and Compiling Programs
---

### Post by emo on 2006-02-06
Hi guys I'm struggling to compile those programm and just drive me mad, the whole point  is  C and I don't no much about C so take a look on my output is a like puzzle.Any ideas how to sort out I have trayed to debug but I couldn't.The first one I did quite good job because was worse and the second one like you see, looks awful :confused: 

$ gcc -o tpe tpe.c
tpe.c:1: error: syntax error before numeric constant
cc1: error: \x used with no following hex digits
cc1: error: \x used with no following hex digits
$

$ gcc -o n_tpe n_tpe.c
n_tpe.c:1: error: syntax error before ‘<’ token
n_tpe.c:7:1: error: \x used with no following hex digits
n_tpe.c:10: error: syntax error before ‘{’ token
n_tpe.c:17: error: conflicting types for ‘buffer’
n_tpe.c:14: error: previous declaration of ‘buffer’ was here
n_tpe.c:17: warning: incompatible implicit declaration of built-in function ‘malloc’
n_tpe.c:17: warning: initialization makes integer from pointer without a cast
n_tpe.c:17: error: initializer element is not constant
n_tpe.c:17: warning: data definition has no type or storage class
n_tpe.c:20: error: conflicting types for ‘ret’
n_tpe.c:13: error: previous declaration of ‘ret’ was here
n_tpe.c:20: warning: incompatible implicit declaration of built-in function ‘strlen’
n_tpe.c:20: error: ‘shellcode’ undeclared here (not in a function)
n_tpe.c:20: warning: initializer element is not constant
n_tpe.c:20: warning: (near initialization for ‘ret’)
n_tpe.c:20: error: initializer element is not constant
n_tpe.c:20: warning: data definition has no type or storage class
n_tpe.c:23: error: conflicting types for ‘ptr’
n_tpe.c:14: error: previous declaration of ‘ptr’ was here
n_tpe.c:23: error: initializer element is not constant
n_tpe.c:23: warning: data definition has no type or storage class
n_tpe.c:24: error: conflicting types for ‘addr_ptr’
n_tpe.c:13: error: previous declaration of ‘addr_ptr’ was here
n_tpe.c:24: warning: initialization makes integer from pointer without a cast
n_tpe.c:24: error: initializer element is not constant
n_tpe.c:24: warning: data definition has no type or storage class
n_tpe.c:25: error: syntax error before ‘for’
n_tpe.c:29: error: conflicting types for ‘buffer’
n_tpe.c:14: error: previous declaration of ‘buffer’ was here
n_tpe.c:29: error: invalid initializer
n_tpe.c:29: warning: data definition has no type or storage class
n_tpe.c:33: error: missing terminating " character
n_tpe.c:36: error: syntax error before ‘(’ token
n_tpe.c:36: warning: conflicting types for built-in function ‘execle’
n_tpe.c:36: warning: data definition has no type or storage class
$

---

### Post by gord on 2006-02-07
its kinda hard to know unless you show the source ;)

---

