---
title: "Python problem"
date: 2011-10-11
forum: Programming Talk
---

### Post by Kr1551 on 2011-10-11
I just followed this

[http://learnpythonthehardway.org/book/ex6.html](http://learnpythonthehardway.org/book/ex6.html)

Exercise, and I always get this error.

```
$ python ex6.py
  File "ex6.py", line 1
    x = "Tad eru til %d typur af folki." % 10
    ^
IndentationError: unexpected indent

```

Here is the code.

```
 x = "Tad eru til %d typur af folki." % 10
 binary = "binary"
 do_not = "kunna ekki"
 y = "Tessi sem kunna %s og tessi sem %s." % (binary, do_not)

 print x
 print y
 
 print "Eg sagdi: %r." % x
 print "Eg sagdi lika: '%s'." % y
 
 fyndinn = False
 brandari_fyndinn = "Er brandarinn ekki fyndinn? %r"
 
 print brandari_fyndinn % fyndinn
 
 w = "Tetta er vinstri hlid af..."
 e = "af streng med haegri hlid."
 
 print w + e
```

Sorry, it is on Icelandic. By the way, how do I get Icelandic letters to work?

---

### Post by simeon87 on 2011-10-11
You have indented the code with one space. Don't indent the code as it has meaning in Python: indentation is used to define control blocks. For example, an if-statement is written like this:

```
 if condition:
    # do something here
```

The second line has to be indented, otherwise it is not correct Python code. So the solution to your problem is, in short, to remove the space in each line of your code.

---

### Post by karlson on 2011-10-11
> **Kr1551 said:**
> I just followed this

[http://learnpythonthehardway.org/book/ex6.html](http://learnpythonthehardway.org/book/ex6.html)

Exercise, and I always get this error.

```
$ python ex6.py
  File "ex6.py", line 1
    x = "Tad eru til %d typur af folki." % 10
    ^
IndentationError: unexpected indent

```

Here is the code.

```
 x = "Tad eru til %d typur af folki." % 10
 binary = "binary"
 do_not = "kunna ekki"
 y = "Tessi sem kunna %s og tessi sem %s." % (binary, do_not)

 print x
 print y
 
 print "Eg sagdi: %r." % x
 print "Eg sagdi lika: '%s'." % y
 
 fyndinn = False
 brandari_fyndinn = "Er brandarinn ekki fyndinn? %r"
 
 print brandari_fyndinn % fyndinn
 
 w = "Tetta er vinstri hlid af..."
 e = "af streng med haegri hlid."
 
 print w + e
```

Sorry, it is on Icelandic. By the way, how do I get Icelandic letters to work?

Looks like you added some spaces before "x =".  Did you post what you have or the code from the webpage?

---

### Post by ofnuts on 2011-10-11
> **Kr1551 said:**
> I just followed this

[http://learnpythonthehardway.org/book/ex6.html](http://learnpythonthehardway.org/book/ex6.html)

Exercise, and I always get this error.

```
$ python ex6.py
  File "ex6.py", line 1
    x = "Tad eru til %d typur af folki." % 10
    ^
IndentationError: unexpected indent

```Here is the code.

```
 x = "Tad eru til %d typur af folki." % 10
 binary = "binary"
 ekki = "kunna ekki"
 y = "Tessi sem kunna %s og tessi sem %s." % (binary, do_not)

 print x
 print y
 
 print "Eg sagdi: %r." % x
 print "Eg sagdi lika: '%s'." % y
 
 fyndinn = False
 brandari_fyndinn = "Er brandarinn ekki fyndinn? %r"
 
 print brandari_fyndinn % fyndinn
 
 w = "Tetta er vinstri hlid af..."
 e = "af streng med haegri hlid."
 
 print w + e
```Sorry, it is on Icelandic. By the way, how do I get Icelandic letters to work?
"Unexpected indent" in python means that the indentation of your line is not correct, ie, it hasn't got the same number of leading spaces that the ones around it, or the line before doesn't end with ":". You may not notice a different indent if one line is indented with spaces and the other is indented with tabs, which for python are different. A very common mistake :)

Using icelandic characters in strings should be no problem, if you editor supports it. A good editor will spot such characters and suggest to add a  line with something like:
```
# -*- coding: iso-8859-15 -*-
``` at the top of the file and save the file with the corresponding encoding (I don' remember is 8859-15 is the one that iincludes icelandic, and you can likely also use UTF-8).

---

### Post by Kr1551 on 2011-10-11
> **karlson said:**
> Looks like you added some spaces before "x =".  Did you post what you have or the code from the webpage?
I posted the code that I wrote, you can click on the link bellow it and theres the real code.

---

### Post by Kr1551 on 2011-10-11
> **simeon87 said:**
> You have indented the code with one space. Don't indent the code as it has meaning in Python: indentation is used to define control blocks. For example, an if-statement is written like this:

```
 if condition:
    # do something here
```

The second line has to be indented, otherwise it is not correct Python code. So the solution to your problem is, in short, to remove the space in each line of your code.
It is fixed, thanks for this!

---

### Post by Arndt on 2011-10-11
> **ofnuts said:**
> "Unexpected indent" in python means that the indentation of your line is not correct, ie, it hasn't got the same number of leading spaces that the ones around it, or the line before doesn't end with ":". You may not notice a different indent if one line is indented with spaces and the other is indented with tabs, which for python are different. A very common mistake :)


If you use the traditional tab spacing of 8, you won't notice the difference. My editor's python mode probably usually converts everything to spaces, but I just tried indenting one line with eight spaces and the next one with one tab, and it worked.

---

### Post by Arndt on 2011-10-11
> **ofnuts said:**
> 
Using icelandic characters in strings should be no problem, if you editor supports it. A good editor will spot such characters and suggest to add a  line with something like:
```
# -*- coding: iso-8859-15 -*-
``` at the top of the file and save the file with the corresponding encoding (I don' remember is 8859-15 is the one that iincludes icelandic, and you can likely also use UTF-8).

Using utf-8 probably works best, since it's what most other programs use in Ubuntu. If there is a need to convert, one can use the program 'iconv'.

If one tries to use non-ASCII character in python without such a line, python will complain and point to some documentation:

```
$ python tmp/varf.py 
  File "tmp/varf.py", line 4
SyntaxError: Non-ASCII character '\xc3' in file tmp/varf.py on line 4, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details

```

---

