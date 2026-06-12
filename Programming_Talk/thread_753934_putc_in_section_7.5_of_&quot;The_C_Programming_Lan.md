---
title: "putc in section 7.5 of &quot;The C Programming Language&quot; 2nd ed."
date: 2008-04-13
forum: Programming Talk
---

### Post by BattlePanic on 2008-04-13
I've been trying develop some programming skills and have been teaching myself C by reading the second edition of "The C Programming Language."

Section 7.5 titled "File Access" introduces the putc function and it is declared and explained with the following:

```
int putc(int c, FILE *fp)
```
> 
"putc writes the character c to to the file fp and returns the character written or EOF if an error occurs"

if c is supposed to be a character, why is it declared as an int?  When I tried using this function and passed it a char as the first function parameter I got no complaints and it produced the expected results.  Is there any reason behind this?  I thought swapping types was a no-no and in fact, wasn't allowed by the compiler without a typecast.

---

### Post by LaRoza on 2008-04-13
char are ints (short ints, I think).

It is because it is possible for it to return EOF.

[https://www.securecoding.cert.org/confluence/display/seccode/FIO34-C.+Use+int+to+capture+the+return+value+of+character+IO+functions;jsessionid=ABC74FF0D6F7EEFEB078C53FFF0709B9](https://www.securecoding.cert.org/confluence/display/seccode/FIO34-C.+Use+int+to+capture+the+return+value+of+character+IO+functions;jsessionid=ABC74FF0D6F7EEFEB078C53FFF0709B9)

---

### Post by Zugzwang on 2008-04-13
Additional reading: [http://www.trilithium.com/johan/2005/01/char-types/]("http://www.trilithium.com/johan/2005/01/char-types/")

---

