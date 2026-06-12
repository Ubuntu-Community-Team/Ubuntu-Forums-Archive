---
title: "Compression"
date: 2011-04-16
forum: Programming Talk
---

### Post by ki4jgt on 2011-04-16
If I have a file containing the strings:

"I love you
I love you
I love you"

I can define character(x) as "I love you" in the file. So I can print:

"x = I love you
x
x
x"

and the file would be compressed. My next question is: What characters would not be used in the file, to be mistaken for other parts of the file?

---

### Post by BkkBonanza on 2011-04-17
Some compression schemes are based on this idea but extended into a complete system. There are basic articles on wikipedia that explain the algorithms behind common compression schemes.

Usually they are not word or phrase based but bit-patterns encoded as tables.

---

### Post by NovaAesa on 2011-04-17
Take a look at [http://en.wikipedia.org/wiki/LZ77](http://en.wikipedia.org/wiki/LZ77) it's an algorithm that does something similar yet slightly different to what you have there (it has the same goals - run length encoding).

In your example, you could encode as:
```
49 20 6C 6F 76 65 20 79 6F 75 00 0B 0A 00 0E 0A 00 11 0A
```
The first 10 bytes are "I love you" in ASCII. The next 3 bytes 00 0B 0A mean 00-this is a repeat of something we had before, 0B-go back 0B bytes, 0A-copy 0A bytes. Then the next 3 bytes 00 0E 0A mean 00-this is a repeat of something we had before, 0E go back 0E bytes, copy 0A bytes. Then the next 3 bytes 00 11 0A mean 00-this is a repeat of something we had before, 11-go back 11 bytes, 0A-copy 0A bytes.

---

