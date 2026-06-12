---
title: "[Python] RegEx simple pattern help"
date: 2010-12-24
forum: Programming Talk
---

### Post by Nexusx6 on 2010-12-24
Hello, I'm in need of a little help coding a RegEx pattern. What I'm looking for is pattern that will match a sequence like this:

```

abc
abcd
abcde
abcdef
etc..
```

where the next letter (or number) in the sequence may or may not be there, but not to match if the next letter is *not* part of the sequence

```

abced
abcdegf
etc

```

I feel like the answer is right in front of me, but I cant seem to get it. Any help is appreicated

---

### Post by Vaphell on 2010-12-25
so you want to check if given 'words' are built from characters in their natural order? I may suck at regular expressions but i don't think it's trivial at all.
It's much easier to test if ord(word[i]) != (ord(word[i+1])-1)

---

### Post by Nexusx6 on 2010-12-25
> **Vaphell said:**
> so you want to check if given 'words' are built from characters in their natural order? 

Not quite. Say I have some sequence asd123, what I want is to match the sequences
```
asd
// or
asd1
// or
asd12
// or
asd123
```

but not

```
asd2
// or
asd321
// or
ads123
etc...
```

---

### Post by Some Penguin on 2010-12-25
```

^a((b(c?))?)$

```

would accept 'a', or 'ab', 'abc'.  The c is optional within the bc sequence, and the b(c?) sequence is optional following an a.

---

### Post by Nexusx6 on 2010-12-27
> **Some Penguin said:**
> ```

^a((b(c?))?)$

```

would accept 'a', or 'ab', 'abc'.  The c is optional within the bc sequence, and the b(c?) sequence is optional following an a.

This works great! Thanks for responding :)

---

### Post by Vaphell on 2010-12-27
either way regex is an overkill plus it's not too flexible.
you can achieve similar effect with **in** or **startswith()**

```
sequence = "abcdefgh"
tested_str = "abc"

print tested_str in sequence

print sequence.startswith( tested_str )
```

---

### Post by Nexusx6 on 2010-12-27
> **Vaphell said:**
> either way regex is an overkill plus it's not too flexible.
you can achieve similar effect with **in** or **startswith()**

```
sequence = "abcdefgh"
tested_str = "abc"

print tested_str in sequence

print sequence.startswith( tested_str )
```

Yeah, actually I agree. I have to use regex in other parts of my program for more complex matching than a sequence, so when I got to this stage I just kept moving with regex. It didn't hit me till your first post that I could probably just use array functions to achieve the same thing :redface:

---

### Post by Joshimitsu on 2010-12-29
Hi,

I have a request similar to this.

 I'm learning Arabic, and for my learning I type documents that have  both English and Arabic text.  The Arabic renders much smaller in things  like OpenOffice compared to English, so I have to highlight and  increase the font size of the Arabic text as I write. 

For example, when I write a wordpress post, the html looks like:

```
<p>Naseehatu Ibraheema - Advice of Ibraheem</p>
<span  style="color:#000000;"><span style="font-family:Times New  Roman,serif;"><span style="font-size:x-large;">&#1614;&#1603;&#1614;&#1575;&#1606;&#1614;  &#1573;&#1576;&#1618;&#1585;&#1614;&#1575;&#1607;&#1616;&#1610;&#1605;&#1615; &#1610;&#1614;&#1602;&#1615;&#1608;&#1604;&#1615;  &#1604;&#1616;&#1608;&#1575;&#1604;&#1616;&#1583;&#1616;&#1607;&#1616;</span></span></span></span></p>

```

So  in an ideal world, I would like to type everything in normal font in  both English and Arabic and then run some sort of script or something  that will wrap all the Arabic in <span  style="font-size:x-large;"></span> .  

Can someone help me with this?

Thanks

---

### Post by ziekfiguur on 2010-12-29
> **Joshimitsu said:**
> Can someone help me with this?

I can help only partly I'm afraid. I don't know any arabic, so i had to look the characters up in a unicode table. Here is what i came up with:
```
#!/usr/bin/env python3
import re
import sys

sys.stdout.write(re.sub('(([\u0600-\u06ff]\s*)+)',
       '<span style="font-size:x-large;">\\1</span>', sys.stdin.read()))

```
Please note that this one uses python 3 (it's not installed by default, but it's in the repositories) because that works easier with unicode.

It seems to work mostly but it misses some characters.
```
&#1614;&#1603;&#1614;&#1575;&#1606;&#1614;  &#1573;&#1576;&#1618;&#1585;&#1614;&#1575;&#1607;&#1616;&#1610;&#1605;&#1615; &#1610;&#1614;&#1602;&#1615;&#1608;&#1604;&#1615;  &#1604;&#1616;&#1608;&#1575;&#1604;&#1616;&#1583;&#1616;&#1607;&#1616;
```
gets translated to:
```
<span style="font-size:x-large;">&#1603;&#1614;&#1575;&#1606;&#1614;  &#1573;&#1576;&#1618;&#1585;&#1614;&#1575;&#1607;&#1616;&#1610;&#1605;&#1615; &#1610;&#1614;&#1602;&#1615;&#1608;&#1604;&#1615;  &#1604;&#1616;&#1608;&#1575;&#1604;&#1616;&#1583;&#1616;&#1607;&#1616;</span>
```
Notice that the leftmost arabic character (or is it punctuation?) is missing.
However, if you know the unicode codes for this (and maybe more, you'll have to test that) character it's fairly trivial to expand my regex.

---

### Post by Joshimitsu on 2010-12-29
Wow thanks ziekfiguur!  I don't know anything about python so I'll try what you've suggested and get back to you.

---

### Post by Joshimitsu on 2010-12-29
Erm, really embarrassing question, but how do I use the above code?

If I have a text file called 'notes', which contains the Arabic script, how do I make the code run in it?

Thanks

---

### Post by ziekfiguur on 2010-12-29
> **Joshimitsu said:**
> Erm, really embarrassing question, but how do I use the above code?

If I have a text file called 'notes', which contains the Arabic script, how do I make the code run in it?

Thanks
Sorry, I should have explained. The script reads its input from stdin and writes to stdout.
So if you save it as large_arab.py you can make it executable with: ```
$chmod a+x large_arab.py
```
and use it, from the folder where you saved it, with: ```
$./large_arab.py < notes > large_notes
```
This will create a file large_notes with where the arab sentences should have a large font.

---

### Post by Joshimitsu on 2010-12-29
Hey Z,

When I run $chmod a+x large_arab.py , I get:

```
$chmod a+x large_arab.py
No command 'a+x' found, did you mean:
 Command 'a2x' from package 'asciidoc' (main)
 Command 'a+' from package 'aplus-fsf' (universe)
a+x: command not found
```

I'm not sure if I did something wrong.  

I created a folder on my Desktop called Arabic.  In here I placed the code in a text file and saved it as large_arab.py.  I then placed the text file with all the Arabic I want enlarged called 'notes'.  I then opened terminal and run $chmod a+x large_arab.py and got the above error.

---

### Post by Some Penguin on 2010-12-29
$ was the command prompt.  Don't type it, or $chmod will be interpreted as a variable -- presumably unset, and therefore an empty string.

---

### Post by Joshimitsu on 2010-12-29
> **Some Penguin said:**
> $ was the command prompt.  Don't type it, or $chmod will be interpreted as a variable -- presumably unset, and therefore an empty string.

Doh!

There should be a feature where you can delete your stupid posts  :lolflag:

Please pretend that I didn't use the command prompt and just make a fool of myself in public... it'll make me a feel a lil better about myself!

Thanks again ziekfiguur, the code worked perfectly.

:guitar:

---

