---
title: "[Challenge] Encryptions"
date: 2008-12-08
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-12-08
The Challenge:

make a program that encrypts a file...to make it more fun try and make your own cypher (very hard)

also...try and make programs to unencrypt these files

to make it interesting put your source in an attatchment and atttatch a basic .txt file that is encrypted so we can try and crack it without knowing your algorithem...also in the source if you used a know algorithem please mention it in a comment

have fun

(and yes i know there was a previous challenge like this but i am giving more freedom and the unscrabling part)

---

### Post by snova on 2008-12-08
Quick and dirty, mildly obfuscated XOR, as jimi_hendrix has already seen earlier:

```
main(int c,char**v){v[0]=v[1];while((c=getchar())!=-1)putchar(c^*(v[0]=*(++v[0])?v[0]:v[1]));}
```

Usage: First argument is the key. Redirect the input file into stdin and stdout to the output file. Example:

```
gcc -o xor xor.c
./xor secret-key >output <input
```

> to make it interesting put your source in an attatchment and atttatch a basic .txt file that is encrypted so we can try and crack it without knowing your algorithem...also in the source if you used a know algorithem please mention it in a comment

How silly. It is a fundamental assumuption in cryptography that you know all the details of the algorithm. Only the key (and plaintext, obviously) are assumed to be secret.

I'll write up a simple TEA program next; a mild step up in difficulty.

---

