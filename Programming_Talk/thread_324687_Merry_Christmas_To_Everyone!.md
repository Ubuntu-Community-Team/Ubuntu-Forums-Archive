---
title: "Merry Christmas To Everyone!"
date: 2006-12-24
forum: Programming Talk
---

### Post by Wybiral on 2006-12-24
If I left anyone out, feel free to post it!



ASM (NASM):
```

section .data
 merry: db 'Merry Christmas!\n',10
 len: equ $-merry
 
section .text
 global _start
 
_start:
 mov eax,4
 mov ebx,1
 mov ecx,merry
 mov edx,len
 int 80h
 
 mov eax,1
 int 80h

```

ASM (FASM):
```

format ELF executable
entry start
 
segment readable executable
 
start:
 
 mov eax,4
 mov ebx,1
 mov ecx,merry
 mov edx,len
 int 0x80
 
 mov eax,1
 xor ebx,ebx
 int 0x80
 
segment readable writeable
 
merry db 'Merry Christmas!\n',0xA
len = $-merry

```

ASM (GAS):
```

.data
 merry: .string "Merry Christmas!\n"
 len= .-merry
 
.globl _start
_start:
 movl $4, %eax
 movl $merry, %ecx
 movl $len, %edx
 int $0x80
 
 movl $1, %eax
 int $0x80

```

BASH:
```

echo "Merry Christmas!"

```

BASIC:
```

PRINT "Merry Christmas!"

```

C:
```

#include <stdio.h>
int main() { printf ("Merry Christmas!"); }

```

C++:
```

#include <iostream>
int main() { std::cout << "Merry Christmas!"; }

```





Java:
```

class MerryChristmas {
	public static void main (String args[]) {
		System.out.print("Merry Christmas!");
	}
}

```

Javascript:
```

<script language="javascript">
	document.write("Merry Christmas!");
	alert("Merry Christmas!");
</script>

```

Pascal:
```

program MerryChristmas;
begin
 write('Merry Christmas!');
end.

```

Python:
```

print "Merry Christmas!"

```

Ruby:
```

puts "Merry Christmas!"

```

---

### Post by Coldbird on 2006-12-24
nice one... :-)

---

### Post by Desi-Tek.com on 2006-12-24
oh u forget to write it in php :)

```

<?php
echo "Merry Christmas!";
?> 
```

jsp

```

<html>
<!-- JavaServer Page -->
<body>
Merry Christmas!
</body>
</html>

```

---

### Post by Verminox on 2006-12-24
Technically your "Javascript" block is actually "A Javascript within HTML" because of the tags lol... but I'll forgive the errors because of Christmas :D

Merry Christmas!

---

### Post by Wybiral on 2006-12-24
Good point, and even more technically, it's really two "Merry Christmas!" examples in one.

:)

---

### Post by cocteau on 2006-12-24
How horrible is this. Posting geek on christmas day... wonderful :)

Merry Rock 'n Roll Christmas!

---

### Post by gh0st on 2006-12-24
Merry Christmas to you as well :)

---

### Post by rekahsoft on 2006-12-24
Very nice :) but it raises a question...you have three different assembly source files...what is the difference?

---

### Post by Wybiral on 2006-12-24
That's the one thing that makes assembly so hard to learn... Almost every assembler has a slightly different syntax. Compare NASM and FASM to GAS and you can see that the operands are backwards!

mov a, b in NASM or FASM moves b to a, but in GAS, it moves a to b.

Other differences between them are things like segment declarations and data entries. NASM and GAS are similar, except for the whole backwards issue.

GAS is my favorite, but AT&T syntax assembly for linux has VERY little documentation... It's really hard to find good tutorials or howto's. FASM is a really good one too, I've seen some impressive programs written in FASM (I believe FASM is self compiled too, meaning FASM's source code can compile itself)

---

### Post by christhemonkey on 2006-12-24
perl? 	:cry:

---

### Post by Wybiral on 2006-12-24
Perl:
```

print "Merry Christmas!";

```

---

### Post by pmasiar on 2006-12-27
Quick wikipedia search for [hello world]("http://en.wikipedia.org/wiki/Hello_world") linked me to [List of hello world programs]("http://en.wikibooks.org/wiki/List_of_hello_world_programs") including APL, first known hello world program ever written (in B). I was most impressed :-) by Forte from standard languages, and Brainfuck, Piet, Whitespace from esoteric languages.

---

### Post by Wybiral on 2006-12-27
Holy crap, that's some crazy stuff. Nice link pmasiar.

---

