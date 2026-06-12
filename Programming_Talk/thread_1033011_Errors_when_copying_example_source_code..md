---
title: "Errors when copying example source code."
date: 2009-01-06
forum: Programming Talk
---

### Post by rplantz on 2009-01-06
Most of us have copy/pasted source code from electronic documents as a means of learning new things. Sometimes the code doesn't work, so we go to our favorite forum and ask for help. An example is [http://ubuntuforums.org/showthread.php?t=1026609](http://ubuntuforums.org/showthread.php?t=1026609), which prompted this "HOWNOTTO."

The OP of that thread had some problems with copy/paste of some source code from a (free) pdf version of a book. The GNU assembler (gas) gave a syntax error on one line. Several people commented. The OP came up with a correct solution, but for the *wrong reason*.

The issue had to do with an assembly language line
```

.equ UPPER_CONVERSION, ’A’ - ’a’

```
that caused the GNU assembler (gas) to complain that 'A' and 'a' are undefined. The OP "solved" the problem by noting that the syntax for gas is different. The info documentation specifies 'A - 'a instead of 'A' - 'a', the C syntax.

The *real problem* is that the copy/paste of this line did not produce the single quote character. I copy/pasted this line into a file (using gedit), then typed it by hand.
```

.equ UPPER_CONVERSION, ’A’ - ’a’
.equ UPPER_CONVERSION, 'A' - 'a'

```
Then I did
```

bob@bob-desktop:~/programming$ hexdump -C single_quote.txt
00000000  2e 65 71 75 20 55 50 50  45 52 5f 43 4f 4e 56 45  |.equ UPPER_CONVE|
00000010  52 53 49 4f 4e 2c 20 e2  80 99 41 e2 80 99 20 2d  |RSION, ...A... -|
00000020  20 e2 80 99 61 e2 80 99  0a 2e 65 71 75 20 55 50  | ...a.....equ UP|
00000030  50 45 52 5f 43 4f 4e 56  45 52 53 49 4f 4e 2c 20  |PER_CONVERSION, |
00000040  27 41 27 20 2d 20 27 61  27 0a                    |'A' - 'a'.|
0000004a

```
to see the actual characters. Seeing both lines side-by-side, it is clear that the pdf version did not use plain single quote characters.

Even worse, gas did not warn of any syntax errors in:
```

#The lower boundary of our search
.equ LOWERCASE_A, ’a’
#The upper boundary of our search
.equ LOWERCASE_Z, ’z’

```
which produced incorrect code (my comments added as explanation):
```

 189 00a4 80F900   	 cmpb $LOWERCASE_A, %cl  # less than lower case A?
 190 00a7 7C0B     	 jl    next_byte         # yes, do next byte
 191 00a9 80F900   	 cmpb $LOWERCASE_Z, %cl  # greater than lower case Z?
 192 00ac 7F06     	 jg    next_byte         # yes, do next byte

```
which is exactly the same (at the machine code level) as:
```

 189 00a4 80F900   	 cmpb $0, %cl            # less than 0?
 190 00a7 7C0B     	 jl    next_byte         # yes, do next byte
 191 00a9 80F900   	 cmpb $0, %cl            # greater than 0?
 192 00ac 7F06     	 jg    next_byte         # yes, do next byte

```

For those who do not read x86 assembly language, gas assembled the two constants, LOWERCASE_A and LOWERCASE_Z, as zero instead of the ASCII code for each of the two characters. BTW, the first jump (jl) will never occur and the second jump (jg) will always occur.

Moral: When copy/pasting code be especially wary of non-alphanumeric characters. I suggest copying at least any lines with non-alphanumeric characters by hand.

---

### Post by Stoodle on 2009-01-10
Thanks for the tip. So this means that 'a' is incorrect and 'a is correct as I thought? Also, what I was wondering was how could I have this problem? Is there some other single quote character defined in unicode that GAS didn't like? I copied this from a pdf, where fancy styles are allowed, but I assumed copying to an editor (gedit) would get rid of formatting so it could compile (or assemble) correctly.

---

### Post by rplantz on 2009-01-10
> **Stoodle said:**
> Thanks for the tip. So this means that 'a' is incorrect and 'a is correct as I thought?

According to the info documentation, you are correct. I and my students have used the 'a' form many times and it has always worked. I personally find the 'a' form a little easier to read, at least for the space character. For example,
```

        movb    $' , %al   # is a little hard to read
        movb    $' ', %al  # is easier to read

```

> 
Also, what I was wondering was how could I have this problem? Is there some other single quote character defined in unicode that GAS didn't like? I copied this from a pdf, where fancy styles are allowed, but I assumed copying to an editor (gedit) would get rid of formatting so it could compile (or assemble) correctly.
I'm not sure about this. I tried gedit, emacs, and vim and got e2 80 99 for the pdf single quote characters, instead of the ascii 27 value for single quote (all in hex).

This also surprised me. I even tried using pdftotext on the pages of Programming from the Ground Up that have the source code and got the same thing.

I've done this sort of thing (copy/paste) many times over many years and have sometimes encountered code that didn't compile/assemble. After fighting with it for a while, I often retype several lines by hand and it "magically" works. I used to think that an invisible character had somehow found its way into my code. So seeing how the pdf character got copied in this case was a learning experience for me.

And thank you for leading me into this exploration. Even though I have a PhD and am 70 years old, there are still new things to learn. :-)

---

