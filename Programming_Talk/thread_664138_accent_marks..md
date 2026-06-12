---
title: "accent marks."
date: 2008-01-10
forum: Programming Talk
---

### Post by CapitanYochua on 2008-01-10
I'm new to programming. I am trying to create a dictionary with a "ñ" in the name. I guess this causes an error. So, how could I solve this error? what would I do if my keys or elements of my dictionary had accent marks?

The error output mentions something about a Non-ASCII character. 
Thank you for any help.

---

### Post by LaRoza on 2008-01-10
The language you are using would help...

---

### Post by CapitanYochua on 2008-01-10
python. so sorry I forgot to mention it. :/

---

### Post by LaRoza on 2008-01-10
You can use that character in strings, but not as names in Python, at least, by default.

I am looking into it now...

**<edit>**
I just found a lot on encoding in Python, but non of it would help use non ascii characters as identifiers. Stick to ascii names in the script, but you can have unicode (or other encodings, including Latin-1) in strings.
**</edit>**

---

### Post by CapitanYochua on 2008-01-10
Okay. Thanks for looking. (:

---

### Post by CapitanYochua on 2008-01-10
How would you use that character in a string? It doesn't seem to be working in a string either. Do you have to do some encoding or something?

---

### Post by ghostdog74 on 2008-01-10
you might want to look at[ this]("http://www.amk.ca/python/howto/unicode") and[ this]("http://docs.python.org/lib/module-unicodedata.html") and of course, the [tutorial ]("http://docs.python.org/tut/node5.html#SECTION005130000000000000000")

---

### Post by CapitanYochua on 2008-01-11
Thank you for the links. I encoded the string. I am able to use the string and print it properly in other programs, but the string doesn't work properly as either a key or value in a dictionary. I am trying to print that character in the string with print mydict.values() and print mydict.keys(). These won't print the characters correctly. Any help?

---

### Post by popch on 2008-01-12
[The source character set is defined by the encoding declaration; it is ASCII if no encoding declaration is given in the source file; see section 2.1.4.]("http://docs.python.org/ref/strings.html")

**[ 2.1.4 Encoding declarations]("http://docs.python.org/ref/encodings.html")**

---

