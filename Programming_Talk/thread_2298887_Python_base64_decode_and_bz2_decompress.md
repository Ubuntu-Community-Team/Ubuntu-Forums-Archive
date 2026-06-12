---
title: "Python base64 decode and bz2 decompress"
date: 2015-10-14
forum: Programming Talk
---

### Post by lio6 on 2015-10-14
Hello,

I have a string which needs decoding. This is the string: [FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]QlpoOTFBWSZTWQyQhfwAAAWVgEAEABAz93MwIABUUDTQyMmINU8Q1NGTyniNm7sdsz3jfp9FKs41\nfYwWkEIB9AhHU5MqqlamYbfxdyRThQkAyQhfwA==

[COLOR=#000000]So in my little knowledge, I see a base64 encoding. After decoding this I get a bz2 compress string: BZh91AY&SY\x0c\x90\x85\xfc\x00\x00\x05\x95\x80@\x04\x00\x103\xf7s0 \x00TP4\xd0\xc8\xc9\x885O\x10\xd4\xd1\x93\xcax\x8d\x9b\xbb\x1d\xb3=\xe3~\x9fE*\xce5}\x8c\x16\x90B\x01\xf4\x08GS\x93*\xaaV\xa6a\xb7\xf1w$S\x85\t\x00\xc9\x08_\xc0

After a bz2 decompress of the bytes I get this string : Jryy qbar, zragvba gur jbeq evgnmmn jura lbh fraq lbhe pi.
Now that is ascii characters but it means nothing or it is a language internet(google) can't detect.

Any help?[/COLOR]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by PaulM1985 on 2015-10-14
I have reproduced the steps that you have done and I managed to produce the same result.  What is it that you are trying to achieve?  Where did the string come from?  Why are you trying to read it?  How did you know you needed to use base64 followed by bz2?  My guess is that it is some sort of cipher on the top that has changed the characters.  What language do you expect it to be in?

Paul

---

### Post by PaulM1985 on 2015-10-14
Ok, I cracked it, is it for a job application?

---

### Post by lio6 on 2015-10-14
It is a quiz we received in school. It should be in English - French - Nederlands. I live in Belgium so these are the languages we speak here. 
What am I missing here?

---

### Post by spjackson on 2015-10-14
> **lio6 said:**
> It is a quiz we received in school. It should be in English - French - Nederlands. I live in Belgium so these are the languages we speak here. 
What am I missing here?
The decompressed string is a cipher that needs to be decrypted.

---

### Post by PaulM1985 on 2015-10-14
To point you in the right direction, have a look at a caesar cipher.

---

### Post by lio6 on 2015-10-14
Ohhh, that's it. I was missing that part. First time heard of cipher.
Cheers guys.

---

