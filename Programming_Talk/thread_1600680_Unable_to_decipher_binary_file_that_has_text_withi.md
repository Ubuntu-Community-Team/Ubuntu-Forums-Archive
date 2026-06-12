---
title: "Unable to decipher binary file that has text within"
date: 2010-10-19
forum: Programming Talk
---

### Post by PartickThistle on 2010-10-19
Hi all,

I have a couple of files that contain simple text in them, however they are in a binary format that I just cannot decipher.  

I'm not sure if they are encrypted or simply compiled.

The filetype is .pck which is apparently a Pascal Pick File, however I am still unable to open it for viewing.

If anyone could help me I'd be eternally grateful!

I've uploaded an example - this one is US Presidents. 

[http://ubuntuone.com/p/LBq/](http://ubuntuone.com/p/LBq/)



Thanks for looking

---

### Post by epicoder on 2010-10-19
You could try strings, which takes the strings from a program and prints them.

For example, using it on a compiled C hello world program
```

strings hello
Hello, world
```
If they are encrypted, this will produce a bunch of jargon, so be careful.

---

### Post by dwhitney67 on 2010-10-19
> **PartickThistle said:**
> Hi all,

I have a couple of files that contain simple text in them, however they are in a binary format that I just cannot decipher.  

If it is a binary file, then it is not simple text.

The file you posted definitely is a data file; at least that is what Linux reports.  If you need to interpret the data, then you will either need to use a 3rd-party app to read it, or write your own.  Whether the data is encrypted or not is another question.
```

file Presidents.pck

```

---

### Post by PartickThistle on 2010-10-19
Thanks guys. 

I have already tried *file* and *strings* without garnering any more information than I did by simply opening the file.

I've used numerous tools on Linux and via Wine with no success at all. 

The program that can decrypt/depress/decompile these binary files is a Windows PE32 Executable built using C++ on Visual Studio, It doesn't use any DLLs outside the ones found as standard on a Windows XP install.  This leads me to believe it is not encrypted or if it is, it's along the lines of base64. 

I've got the ASM out of the .exe it but to understand the pages upon pages of it is a bit above my skills at the moment.

dwhitney67,  I'm happy to put the effort into writing an application that can interpret the data, however the problem is where to start. 

Do you have any pointers? 

Many thanks

---

### Post by Vox754 on 2010-10-19
> **PartickThistle said:**
> Thanks guys. 

I have already tried *file* and *strings* without garnering any more information than I did by simply opening the file.


I used "strings Presidents.pck"
```

[v|%
:Er&v
Bn<]
LeLQkB;
 45y

```

I used "hexdump -C Presidents.pck"
```

00000000  4a e5 30 ec 9a 60 bf bd  81 73 0e 11 6f 5e ec 20  |J.0..`...s..o^. |
00000010  6f 08 3d 43 d8 ab 35 db  7f 3f f4 c3 b9 e8 66 e9  |o.=C..5..?....f.|
00000020  57 7a e4 d6 f4 67 ad d8  8c 60 a2 a6 c2 5e da 68  |Wz...g...`...^.h|
00000030  4e 5c 9a c1 c4 0f 5f 92  1f 0f 1e a6 4e 28 2b ba  |N\...._.....N(+.|
00000040  45 d3 43 d9 ab ec e5 57  a2 b3 7b 7f 3d 79 d3 69  |E.C....W..{.=y.i|
00000050  3f 3a c6 26 10 81 64 ee  7c 9c ea 16 27 bc 97 74  |?:.&..d.|...'..t|
00000060  18 0f 50 ad 58 f4 0e 34  26 29 df 5f 84 15 5b 76  |..P.X..4&)._..[v|
00000070  7c 25 19 57 cb 2f 55 27  e2 b0 19 ba 0b 49 de 09  ||%.W./U'.....I..|
00000080  a6 3a 45 72 26 76 aa 24  bd db c7 b4 2a b8 dd 25  |.:Er&v.$....*..%|
00000090  0f 3d f6 f0 15 bf f2 47  6b bb 42 6e 3c 5d 1e b2  |.=.....Gk.Bn<]..|
000000a0  47 45 80 fa 28 0e 4a 8f  8d cc e0 b7 94 c7 92 a4  |GE..(.J.........|
000000b0  49 17 cb c1 81 83 de c2  41 e3 c5 fa 3f 35 14 cf  |I.......A...?5..|
000000c0  ae 4c 65 4c 51 6b 42 3b  b6 a5 8d c4 48 1e 9d fa  |.LeLQkB;....H...|
000000d0  36 f9 ce 49 de 59 d5 8b  e8 9f 10 0e ea 3b b5 bf  |6..I.Y.......;..|
000000e0  0c 91 25 d3 1d 0f 1e a6  4e 28 ea d5 a4 12 88 de  |..%.....N(......|
000000f0  ab dc 27 8e b5 ae 8d 7a  43 2e 83 b2 59 5f 0e 67  |..'....zC...Y_.g|
00000100  7a 6d f2 a7 4c 2b 17 bc  a2 0e 48 ef 14 5d 2f ac  |zm..L+....H..]/.|
00000110  f3 fc 85 10 d8 4d 12 e4  da 55 c7 af 84 c3 3b 25  |.....M...U....;%|
00000120  86 87 29 3e 18 82 2e d5  b6 29 16 86 48 e0 68 62  |..)>.....)..H.hb|
00000130  d2 6c 43 17 ee f4 32 c5  1b 30 e5 c4 5e fe 6e c4  |.lC...2..0..^.n.|
00000140  15 bf 33 38 fc 85 e7 6f  b8 28 b2 d0 dc e1 ec d7  |..38...o.(......|
00000150  17 a9 ee 87 92 cc 80 f5  97 70 bc bf ae 12 e7 9f  |.........p......|
00000160  1c 36 b9 c2 45 a6 8f 20  34 35 79 16 2c 86 1e b7  |.6..E.. 45y.,...|
00000170  9b 8e 1a c2 bd cc 8d c0  6e 23 39 12 4f af 56 49  |........n#9.O.VI|
00000180  e0 13 ed 41 11 43 da 6c  1e 45 dd 5c 9f 1d 23 ef  |...A.C.l.E.\..#.|
00000190  20 9d 58 6d 87 a3 7a da  e7 b8 ed b0 53 67 b0 34  | .Xm..z.....Sg.4|
000001a0  1e b2 47 45 80 8f c1 fa  63 f9 87 cc              |..GE....c...|
000001ac

```
As you can see, the file does not contain any meaningful text, it's just a bunch of binary data. You are confusing the people here by saying that it contains "text within". It does not. It contains binary information; how that information is interpreted by a particular program is a separate issue.

> 
I've used numerous tools on Linux and via Wine with no success at all. 

The program that can decrypt/depress/decompile these binary files is a Windows PE32 Executable built using C++ on Visual Studio, It doesn't use any DLLs outside the ones found as standard on a Windows XP install.  This leads me to believe it is not encrypted or if it is, it's along the lines of base64. 

If you have the program you should just run it in wine.
```

wine decompile.exe Presidents.pck

```
But apparently you tried that already? And didn't work? Please explain.

> 
I've got the ASM out of the .exe it but to understand the pages upon pages of it is a bit above my skills at the moment.

dwhitney67,  I'm happy to put the effort into writing an application that can interpret the data, however the problem is where to start. 

...
It is futile to try to "write an application that can interpret the data" if you don't know how the binary file is created in the first place. It's like trying to create a German translator without knowing German in the first place, it's not possible.

What you want at this point is trying to reverse-engineer a binary file, which is nearly impossible if you know nothing about that binary format.

---

### Post by PartickThistle on 2010-10-19
> **Vox754 said:**
> 
If you have the program you should just run it in wine.
```

wine decompile.exe Presidents.pck

```

Unfortunately the windows exe isn't an actual decompiler. It understands the binary file and outputs textual content to the program.  That's my reason for saying it contains text within. Technically it does.

I looked at the ASM/tried to decompile to see the function that does the above, however only get nonsensicle code from it.

> **Vox754 said:**
> 
It is futile to try to "write an application that can interpret the data" if you don't know how the binary file is created in the first place. 
...
What you want at this point is trying to reverse-engineer a binary file, which is nearly impossible if you know nothing about that binary format.
Exactly. That's my problem. I'm just at a loss here. 

There's two ways I think I could read the files;

* Decompile the executable into a readable code and find the function that loads the files.
* Dump the memory in a readable format once these resources have been loaded. 

Would you say this is feasible? 

There's 50-odd files with information that I'd like to read and I could easily trawl the 'net for all these lists, but I know these files have the information and see this as a challenge. 

If I'm wasting my time, please tell me! 

Thanks again

---

