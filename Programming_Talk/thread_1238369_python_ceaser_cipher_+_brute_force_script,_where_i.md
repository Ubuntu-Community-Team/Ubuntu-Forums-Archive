---
title: "python ceaser cipher + brute force script, where is my mistake?"
date: 2009-08-12
forum: Programming Talk
---

### Post by bodyharvester on 2009-08-12
i made a ceaser cipher script with the added function of a brute force, however when i typed the message for encryption as "poo poo" and encrypted it with key 1 my encrypted text was "qpp qpp". i could decrypt that text with key 1. like in the screen shot 1, however using key 26 its still "poo poo" and when i use brute force for all keys the text is wrong like in screen shot 2.

where are my mistakes?

i got the idea from "Invent Your Own Computer Games With Python" [http://pythonbook.coffeeghost.net/book1/index.html](http://pythonbook.coffeeghost.net/book1/index.html) - this is an updated version of the book

p.s. yes im new to this

---

### Post by Reiger on 2009-08-12
Caesar cyphers work by considering an alphabet a "cycle" of symbols which you can traverse. That means: given a input set of symbols and a cypher you basically rotate the input by cypher-value of positions.

However this has an implication: your total alphabet length must be correct in order for the cypher to be interpreted properly. So if your original uses an alphabet of 26 chars to encrypt but relies on built-in char manipulation methods it is possible that the decryption actually uses the entire alphabet at its disposal: typically far larger (e.g. 2^16 -1 or 65535 for all common characters from UTF-8, namely those in the BMP).

In short there is likely a flaw in the application logic which disregards constraints imposed during encryption when decrypting.

---

### Post by jeffathehutt on 2009-08-12
```
            if symbol.isupper():
                if num > ord('Z'):
                    num -= 26
                elif num < ord('A'):
                    **num += 1**

            elif symbol.islower():
                if num > ord('z'):
                    num -= 26
                elif num < ord('a'):
                    **num += 1**

```

I looked at the code in that book, and noticed you used num += 1 instead of num += 26.  The code should run correctly after you change that (it ran for me, at least) :)

---

### Post by bodyharvester on 2009-08-13
> **jeffathehutt said:**
> ```
            if symbol.isupper():
                if num > ord('Z'):
                    num -= 26
                elif num < ord('A'):
                    **num += 1**

            elif symbol.islower():
                if num > ord('z'):
                    num -= 26
                elif num < ord('a'):
                    **num += 1**

```I looked at the code in that book, and noticed you used num += 1 instead of num += 26.  The code should run correctly after you change that (it ran for me, at least) :)

oh, thank you so much!:popcorn:

---

