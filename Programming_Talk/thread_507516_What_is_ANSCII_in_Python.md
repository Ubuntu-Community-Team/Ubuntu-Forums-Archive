---
title: "What is ANSCII in Python ?"
date: 2007-07-23
forum: Programming Talk
---

### Post by mocqueanh on 2007-07-23
I type this code and hit F5 to run it, but when i run, a dialog appear and warning me about ANSCII:
```

# Pizza Slicer
# Demonstrates string slicing
# Michael Dawson - 1/27/03

word = "pizza"

print \
"""
   Slicing 'Cheat Sheet'
0     1     2     3     4     5
+—--+—--+—--+—--+-—-+
|  p  |  i  |  z  |  z  |  a  |
+—-+—-+—-+—-+—-+
-5   -4   -3   -2   -1

"""

print "Enter the beginning and ending index for your slice of 'pizza'."
print "Press the enter key at 'Begin' to exit."


begin = None
while begin != "":
    begin = (raw_input("\nBegin: "))

    if begin:
        begin = int(begin)

        end = int(raw_input("End: "))

        print "word[", begin, ":", end, "]\t\t",
        print word[begin:end]


```

[img]http://img127.imageshack.us/img127/4917/slicerot9.jpg[/img]

I'm just a newbie in programming and dont know what is ANSCII, plz define for me ):P

---

### Post by lisati on 2007-07-23
From memory, ASCII means "American Standard Code for Information Interchange", and roughly translates to "a way of representing information". In the context of your example it means (roughly) "stuff you can type on your keyboard"

There's another, "ANSI" with a related meaning.

---

### Post by apoth on 2007-07-23
[ASCII](http://en.wikipedia.org/wiki/ASCII).

You've probably tried to use a character which isn't one of these:

[img]http://upload.wikimedia.org/wikipedia/commons/thumb/4/42/ASCII_full.svg/217px-ASCII_full.svg.png[/img]

---

### Post by mocqueanh on 2007-07-23
So, why does Python warning me about ANSCII in my code

---

### Post by Siph0n on 2007-07-23
My guess is because of your comment on the top... also its ASCII not ANSCII, just for clarification. Take out all the | and see if it works? :) I'm just a newbie also tho, but thats my 2-cents ;)

Siph0n

---

### Post by Siph0n on 2007-07-23
Nevermind :( I see in a few posts above that | is ASCII :( Well there goes my suggestion :) Tho I still think it has to do with your comment, anyone else think so? :)

Edit: Or maybe this line:
print \

---

### Post by cwaldbieser on 2007-07-23
> **mocqueanh said:**
> So, why does Python warning me about ANSCII in my code

It is ASCII.
Here is a link to the relevant PEP why python is warning you:
[http://www.python.org/dev/peps/pep-0263/]("http://www.python.org/dev/peps/pep-0263/")

---

### Post by Peyton on 2007-07-23
Your problem lies here:
```
+&#8212;--+&#8212;--+&#8212;--+&#8212;--+-&#8212;-+
|  p  |  i  |  z  |  z  |  a  |
+&#8212;-+&#8212;-+&#8212;-+&#8212;-+&#8212;-+
```
Hidden among the hyphens and addition signs are some dashes (which aren't allowed in ASCII). Simply replace them with hyphens (and fix up the formatting):
```
0     1     2     3     4     5
+-----+-----+-----+-----+-----+
|  p  |  i  |  z  |  z  |  a  |
+-----+-----+-----+-----+-----+
-5   -4    -3    -2    -1
```

---

