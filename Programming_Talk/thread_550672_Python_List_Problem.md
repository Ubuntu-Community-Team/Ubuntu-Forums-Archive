---
title: "Python List Problem"
date: 2007-09-14
forum: Programming Talk
---

### Post by Catsworth on 2007-09-14
Hey Guys,

Slight problem.

Here's the code:

```

morseTable = []

fin = open(fileName,'r')
for line in fin.readlines():
    
    morseTable.append(str(line.strip()))
    
print morseTable

```

Here's the output:

```

['A,\xc2\xb7\xe2\x80\x93', 'B,\xe2\x80\x93\xc2\xb7\xc2\xb7\xc2\xb7', 'C,\xe2\x80\x93\xc2\xb7\xe2\x80\x93\xc2\xb7', 'D,\xe2\x80\x93\xc2\xb7\xc2\xb7', 
'E,\xc2\xb7', 'F,\xc2\xb7\xc2\xb7\xe2\x80\x93\xc2\xb7', 'G,\xe2\x80\x93\xe2\x80\x93\xc2\xb7', 'H,\xc2\xb7\xc2\xb7\xc2\xb7\xc2\xb7', 'I,\xc2\xb7\xc2\xb7', 
'J,\xc2\xb7\xe2\x80\x93\xe2\x80\x93\xe2\x80\x93', 'K,\xe2\x80\x93\xc2\xb7\xe2\x80\x93', 'L,\xc2\xb7\xe2\x80\x93\xc2\xb7\xc2\xb7', 'M,\xe2\x80\x93\xe2\x80\x93', 
'N,\xe2\x80\x93\xc2\xb7', 'O,\xe2\x80\x93\xe2\x80\x93\xe2\x80\x93', 'P,\xc2\xb7\xe2\x80\x93\xe2\x80\x93\xc2\xb7', 
'Q,\xe2\x80\x93\xe2\x80\x93\xc2\xb7\xe2\x80\x93', 'R,\xc2\xb7\xe2\x80\x93\xc2\xb7', 'S,\xc2\xb7\xc2\xb7\xc2\xb7', 'T,\xe2\x80\x93', 
'U,\xc2\xb7\xc2\xb7\xe2\x80\x93', 'V,\xc2\xb7\xc2\xb7\xc2\xb7\xe2\x80\x93', 'W,\xc2\xb7\xe2\x80\x93\xe2\x80\x93', 'X,\xe2\x80\x93\xc2\xb7\xc2\xb7\xe2\x80\x93', 
'Y,\xe2\x80\x93\xc2\xb7\xe2\x80\x93\xe2\x80\x93', 'Z,\xe2\x80\x93\xe2\x80\x93\xc2\xb7\xc2\xb7', '1,\xc2\xb7\xe2\x80\x93\xe2\x80\x93\xe2\x80\x93\xe2\x80\x93', 
'2,\xc2\xb7\xc2\xb7\xe2\x80\x93\xe2\x80\x93\xe2\x80\x93', '3,\xc2\xb7\xc2\xb7\xc2\xb7\xe2\x80\x93\xe2\x80\x93', 
'4,\xc2\xb7\xc2\xb7\xc2\xb7\xc2\xb7\xe2\x80\x93', '5,\xc2\xb7\xc2\xb7\xc2\xb7\xc2\xb7\xc2\xb7', '6,\xe2\x80\x93\xc2\xb7\xc2\xb7\xc2\xb7\xc2\xb7', 
'7,\xe2\x80\x93\xe2\x80\x93\xc2\xb7\xc2\xb7\xc2\xb7', '8,\xe2\x80\x93\xe2\x80\x93\xe2\x80\x93\xc2\xb7\xc2\xb7', 
'9,\xe2\x80\x93\xe2\x80\x93\xe2\x80\x93\xe2\x80\x93\xc2\xb7', '0,\xe2\x80\x93\xe2\x80\x93\xe2\x80\x93\xe2\x80\x93\xe2\x80\x93']

```

As you might guess, the file is in the format:

```

A,·&#8211;
B,&#8211;···
C,&#8211;·&#8211;·
D,&#8211;··
E,·
F,··&#8211;·
G,&#8211;&#8211;·
H,····

```

And so on.....  So the code should be showing the dots and dashes instead of their (hex?) representations.....

Anybody got any ideas what I've done wrong, and how I can fix it?

Thanks.

---

### Post by cwaldbieser on 2007-09-14
Could you post the output of the following?
```

$ hexdump <filename>

```
or
```

$ od -x <filename>

```
where <filename> is the file you tried to read with your python program.  I just want to make sure the file is a plain text file.

---

### Post by Catsworth on 2007-09-14
Both come back as:

```
0000000 2c41 b7c2 80e2 0a93 2c42 80e2 c293 c2b7
0000020 c2b7 0ab7 2c43 80e2 c293 e2b7 9380 b7c2
0000040 440a e22c 9380 b7c2 b7c2 450a c22c 0ab7
0000060 2c46 b7c2 b7c2 80e2 c293 0ab7 2c47 80e2
0000100 e293 9380 b7c2 480a c22c c2b7 c2b7 c2b7
0000120 0ab7 2c49 b7c2 b7c2 4a0a c22c e2b7 9380
0000140 80e2 e293 9380 4b0a e22c 9380 b7c2 80e2
0000160 0a93 2c4c b7c2 80e2 c293 c2b7 0ab7 2c4d
0000200 80e2 e293 9380 4e0a e22c 9380 b7c2 4f0a
0000220 e22c 9380 80e2 e293 9380 500a c22c e2b7
0000240 9380 80e2 c293 0ab7 2c51 80e2 e293 9380
0000260 b7c2 80e2 0a93 2c52 b7c2 80e2 c293 0ab7
0000300 2c53 b7c2 b7c2 b7c2 540a e22c 9380 550a
0000320 c22c c2b7 e2b7 9380 560a c22c c2b7 c2b7
0000340 e2b7 9380 570a c22c e2b7 9380 80e2 0a93
0000360 2c58 80e2 c293 c2b7 e2b7 9380 590a e22c
0000400 9380 b7c2 80e2 e293 9380 5a0a e22c 9380
0000420 80e2 c293 c2b7 0ab7 2c31 b7c2 80e2 e293
0000440 9380 80e2 e293 9380 320a c22c c2b7 e2b7
0000460 9380 80e2 e293 9380 330a c22c c2b7 c2b7
0000500 e2b7 9380 80e2 0a93 2c34 b7c2 b7c2 b7c2
0000520 b7c2 80e2 0a93 2c35 b7c2 b7c2 b7c2 b7c2
0000540 b7c2 360a e22c 9380 b7c2 b7c2 b7c2 b7c2
0000560 370a e22c 9380 80e2 c293 c2b7 c2b7 0ab7
0000600 2c38 80e2 e293 9380 80e2 c293 c2b7 0ab7
0000620 2c39 80e2 e293 9380 80e2 e293 9380 b7c2
0000640 300a e22c 9380 80e2 e293 9380 80e2 e293
0000660 9380 000a
0000663

```

---

### Post by Catsworth on 2007-09-14
I'm guessing that's not good.....

---

### Post by pmasiar on 2007-09-14
interesting... Looks like .append() does not like morse code. Looking into it...

Found it! "print morseTable" was causing the problem! Your data are stored correctly, but repr() got confused!
[php]
morseTable = []
for line in open('morse.txt'):
    morseTable.append(line.strip())

for x in morseTable:
    print x
[/php]

---

