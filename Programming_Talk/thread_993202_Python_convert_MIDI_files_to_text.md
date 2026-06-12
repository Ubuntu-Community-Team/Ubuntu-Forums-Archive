---
title: "Python convert MIDI files to text"
date: 2008-11-25
forum: Programming Talk
---

### Post by alberto ferreira on 2008-11-25
Hi, I would like to create a program in python that would convert a MIDI file into text in ascii and/or hexadecimal. I have tried opening the file in "rb" mode, using chr(), ord() but to no avail. Basically I'm completely clueless.

This would then serve to analyze the data more easily.

Can someone post     a little piece of script or tell me how to convert binary to hexadecimal or  ascii in a small example?

Thanks

---

### Post by opscure on 2008-11-25
I'm not sure if this is what you're asking, but why not just cat the file to dump it's contents and convert each character to hex from there?

ie:

```
cat music.mid
```

bunch of garbage echo's out.

---

### Post by alberto ferreira on 2008-11-25
My problem is the conversion itself to hex not the reading of the file.

---

### Post by snova on 2008-11-25
[PHP]open( 'output.txt', 'w' ).write( __import__( 'binascii' ).hexlify( open( 'input.midi' ).read() ) )[/PHP]

That'll do it! :p

The key, for those who don't appreciate (mildly) obfuscated code, is the 'hexlify' function in the 'binascii' module.

---

### Post by opscure on 2008-11-26
how about:
```
od x song.mid
```

Is that what you are looking to do?

---

### Post by snova on 2008-11-26
Well, it's 'od -x', not 'od x', but with a few extra options to od to remove formatting, that would do it.

He did say he wanted a Python program, though...

---

### Post by opscure on 2008-11-26
> **snova said:**
> Well, it's 'od -x', not 'od x', but with a few extra options to od to remove formatting, that would do it.

He did say he wanted a Python program, though...

thanks for the -

and here:
```
#!/usr/bin/env python
import subprocess
subprocess.call("od -x song.mid", shell=True)

```

now it's python

---

### Post by alberto ferreira on 2008-11-27
Thanks a lot !!!
Will that work in windows? using subprocess?

Anyways, now I read this: [http://jedi.ks.uiuc.edu/~johns/links/music/midifile.html]("http://jedi.ks.uiuc.edu/%7Ejohns/links/music/midifile.html") and I don't understand how they do the conversion from 
>  
        Number (hex)   <|> Representation (hex)
        00000000       <|> 00
        00000040       <|> 40
        0000007F       <|> 7F
        00000080       <|> 81 00
        00002000       <|> C0 00
        00003FFF       <|> FF 7F
        00004000       <|> 81 80 00
        00100000       <|> C0 80 00
        001FFFFF       <|> FF FF 7F
        00200000       <|> 81 80 80 00
        08000000       <|> C0 80 80 00
        0FFFFFFF       <|> FF FF FF 7F
The Number (hex) to Representation (hex)

Could someone explain this to me? Because I read that page but having no knowledge of hex I'm lost :S:)

---

### Post by L-mental on 2008-11-30
Ok, I'll try to explain it easily, but the fact that you don't know hexa makes it a little harder...

What they are doing is converting an hexa number into another representation, which -unfortunately- uses an hexa format. But what you gotta have in mind is that your first column is the right hexa number, while the second is the same number coded with a little twist.

Number (hex) <|> Representation (hex)
00000000 <|> 00
00000040 <|> 40
0000007F <|> 7F
00000080 <|> 81 00
00002000 <|> C0 00
00003FFF <|> FF 7F
00004000 <|> 81 80 00
00100000 <|> C0 80 00
001FFFFF <|> FF FF 7F
00200000 <|> 81 80 80 00
08000000 <|> C0 80 80 00
0FFFFFFF <|> FF FF FF 7F 


What's the trick: They take the hexa number, and instead of taking 8 bits at a time to write down the 2-digits/letters number, they take just 7 bits at a time, and the 8th is made up from a very simple rule. I'll explain it with examples:

let's take the **40** hexa number.
binary coded: 0100 0000
we take 7 bits chunks: 0 / **_**100 0000
as you can see, we take seven bits -right to left- and then we left a space for the "specially asigned" 8th bit. The 0 bit left out is just ignored for being just zero, so you just have to care for the **_**100 0000 number. 
Now the "special bit" rule: is always 1, except when at the last byte -the one you read last, which is the one at the right end of the number-.
In this case, being the number just one byte, the "special bit" is 0!!! -the only special bit is the one at the right end byte-.
So the number, once coded, is  **0**100 0000
We repackage it into hex, and it stays the same!: **40**

It becomes clear with this example:

let's take the **80** hexa number.
binary code:  1000 0000
taking 7 bits chunks:  (1) (**_**000 0000)
we can't just drop that leftmost bit, so writing the whole number in "7 bits plus the special one" chunks, we have:
**_**000 0001    **_**000 0000
because of the rule, the special bit should be 1 at the left byte, and 0 at the leftmost one, giving you the complete specially coded:
**1**000 0001  **0**000 0000
Now, if you repackage it in hex, you should read 
(**1**000)(0001) (**0**000)(0000), that is: **81 00**

One last example: hex number **4000**
binary code: 0100 0000 0000 0000
taking 7-bits chunks: (01)(00   0000   0)(000   0000) -maybe showing it like this makes it more clear-.
So when trying to code it with the "special bit treatment", we receive:
(**_**000 0001)  (**_**000 0000)  (**_**000 0000)
that is because we have in each byte the 7 bits plus the "special bit"

we assign the special bit, which is always 1... but 0 in the rightmost byte!!!! -remember, that is the rule.
So we have:
(**1**000 0001) (**1**000 0000) (**0**000 0000)
Now is coded!!! of course, writing it in binary is too long, so we package it in hex again:
**81 80 00**
that's how  00004000 <|> 81 80 00

Now, I hope you got the idea, so go to the list and try to code your way from the left column to the right one. Remember, the steps are:
a- unpackage the hex number to binary
b- divide the binary number in 7 bits chunks, and make space for the "special" bits
c- assign the values for the "special" bits (rule: all to 1 except the rightmost byte one)
d- repackage your number in hexa again 

Remember that it's always the same number, you're just coding it with a "special bit" twist!!!




Let me know if you were now able to understand the coding, and if you've been successful at coding the rest of the list!

---

### Post by L-mental on 2008-12-06
so?
has you solved it?

any doubt?

are you still alive?

---

