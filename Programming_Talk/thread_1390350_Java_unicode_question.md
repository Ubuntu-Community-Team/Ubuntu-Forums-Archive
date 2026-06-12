---
title: "Java unicode question"
date: 2010-01-25
forum: Programming Talk
---

### Post by andrew222 on 2010-01-25
I have these unicode code point values in a properties file that are keys and the values are what they are to be replaced with.


\u2010=-
\u2011=-
\u2012=-
\u2013=-
\u2014=-
\u2015=-
\u2016=-
\u2017=-
\u2018='
\u2019='
\u201A='
\u201B='
\u201C=\"
\u201D=\"
\u201E=\"
\u201F=\"
\u2020=-
\u2021=-
\u2022=-
\u2023=-
\u2024=.
\u2025=.
\u2026=.
\u2027=.


When I put the code point values in a char array and print it out in a for loop, some of them are printed out as '?'. I can't seem to figure out why.  Would anyone happen to know why

---

### Post by myrtle1908 on 2010-01-25
Print them out?  Where?  It is likely that your font does not contain the relevant glyphs.

---

### Post by Reiger on 2010-01-25
If you have non-ASCII characters in a properties file, you could use the native2ascii tool for converting them to their proper escape sequences; instead of manual search & replace.

---

### Post by andrew222 on 2010-01-26
These values are loaded into a java.util.Properties instance and are used replace special characters in a string containing XML.  The keys (code points) are the chars that need to be replaced and are basically chars in a .doc file that are different from the equivalent that we will in a .txt file.  

The values are the chars that those special characters will be replaces with.

Both keys and values are put into their own respective Array and are passed as parameters into the Apache StringUtils replaceEach() method to replace the special chars in the string containing XML.

---

### Post by Some Penguin on 2010-01-26
Code points don't fit in the 'char' type, as char is a single byte, so don't store them in a char array.

Use codePointAt, not toCharArray, if you were doing the latter.

---

### Post by NovaAesa on 2010-01-26
> **Some Penguin said:**
> Code points don't fit in the 'char' type, as char is a single byte, so don't store them in a char array.

Use codePointAt, not toCharArray, if you were doing the latter.

Remember that in Java, the char type is a unicode char, rather than an ASCII char. So in java, char is 2 bytes rather than 1 byte like it would be in C or C++. So the code points will fit in the char type, and the toCharArray should work fine I would think.

=]

---

