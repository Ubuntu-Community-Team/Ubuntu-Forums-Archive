---
title: "Cryptography - Open and Modify File Contents"
date: 2012-08-10
forum: Programming Talk
---

### Post by SelbyRowleyCannon on 2012-08-10
I have written a small crypto application that currently only works on user-inputted text. Does nyone know how I can have the user specify a textfile, and have the crypto function work on that (and ignore things like brackets, hyphens, non-letters etc)

EDIT: Working in Python, sorry I forgot to mention

---

### Post by Bachstelze on 2012-08-10
What language?

---

### Post by steeldriver on 2012-08-10
It depends what you mean by 'ignore' - if you need to pass the non-alphabetic characters through then really it would be up to you to do any character class testing internally

Otherwise if your program reads stdin, you could try  piping input through 'tr' to strip out any non-alphabetical characters

```
cat *file* | tr -C [:alpha:] ' ' | *yourprog*
```

---

### Post by trent.josephsen on 2012-08-10
> **steeldriver said:**
> It depends what you mean by 'ignore' - if you need to pass the non-alphabetic characters through then really it would be up to you to do any character class testing internally

Otherwise if your program reads stdin, you could try  piping input through 'tr' to strip out any non-alphabetical characters

```
cat *file* | tr -C [:alpha:] ' ' | *yourprog*
```
Useless cat.

```
tr -C [:alpha:] ' ' <file | program
```

---

### Post by ofnuts on 2012-08-10
> **trent.josephsen said:**
> Useless cat.

From a strict processing point of view, yes, from a readability point of view, no :)

---

### Post by trent.josephsen on 2012-08-10
Conceded.

---

