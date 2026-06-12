---
title: "[SOLVED] gdb: How to show variable values?"
date: 2008-11-21
forum: Programming Talk
---

### Post by WitchCraft on 2008-11-21
Hi! Question: a C program, containing the following array of unsigned int:

```

static const unsigned pak_checksums[] = {
	1566731103u,
	298122907u,
	412165236u,
	2991495316u,
	1197932710u,
	4087071573u,
	3709064859u,
	908855077u,
	977125798u
};

```

When I look at the program that contains this checksums, I go into the GNU Debugger, type "info address pak_checksums", and gdb says ""Symbol "pak_checksums" is at 0x8195bc0 in a file compiled without debugging.""


How can I see the values of the array, that is to say:
	1566731103u,
	298122907u,
	412165236u,
	2991495316u,
	1197932710u,
	4087071573u,
	3709064859u,
	908855077u,
	977125798u
?

---

### Post by Linteg on 2008-11-21
I think "print" works.

---

### Post by WitchCraft on 2008-11-21
> **Linteg said:**
> I think "print" works. But your code looks a bit werid to me, pak_checksums[] doesn't have a type?

Unsigned also has a default type, you know...

And I know the print command, but print only gives the first value.
```

(gdb) print pak_checksums
$1 = 1566731103
(gdb) 

```

But i found the solution in the meantime:
```

(gdb) print pak_checksums@9
$1 = {1566731103, 298122907, 412165236, -1303471980, 1197932710, -207895723, 
  -585902437, 908855077, 977125798}

```

or
```

(gdb) p *0x8195bc0@9
$1 = {1566731103, 298122907, 412165236, -1303471980, 1197932710, -207895723, 
  -585902437, 908855077, 977125798}
(gdb) 

```

and more importantly the corresponding hex values:
```

(gdb) p/x pak_checksums@9
$1 = {0x5d626b5f, 0x11c4fe9b, 0x18912474, 0xb24e9894, 0x476700a6, 0xf39bc355, 
  0xdd13d69b, 0x362c0725, 0x3a3dc1a6}
(gdb) 

```

which in turn corresponds to the hexdump:
```

.rodata:0x8195bc0 pak_checksums   db 5Fh, 6Bh, 62h, 5Dh, 9Bh, 0FEh, 0C4h, 11h, 74h, 24h
.rodata:0x8195bc0                 db 91h, 18h, 94h, 98h, 4Eh, 0B2h, 0A6h, 0, 67h, 47h, 55h
.rodata:0x8195bc0                 db 0C3h, 9Bh, 0F3h, 9Bh, 0D6h, 13h, 0DDh, 25h, 7, 2Ch
.rodata:0x8195bc0                 db 36h, 0A6h, 0C1h, 3Dh, 3Ah
.rodata:0x8195bc0 _rodata         ends
.rodata:0x8195bc0

```

```

0000:0480      5f 6b 62 5d 9b fe c4 11 74 24 91 18 94 98 4e b2 
0000:0490      a6 00 67 47 55 c3 9b f3 9b d6 13 dd 25 07 2c 36 
0000:04a0      a6 c1 3d 3a 00 00 00 00 ff ff ff ff 00 00 00 5f 

```

Problem solved.

---

