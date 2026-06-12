---
title: "[SOLVED] [Python] python challenge 2"
date: 2008-07-10
forum: Programming Talk
---

### Post by TreeFinger on 2008-07-10
[php]
no cheating
[/php]

I added the 'print lineCount' for debugging.

my program doesn't move to line 2.. at least not for as long as i ran it which was a good 5 minutes. What do I need to do?

info for anyone unfamiliar with this challenge..

got a text file with a large large amount of lines.
example of a line: }!)$]&($)@](+(#{$)_%^%_^^#][{*[)%}+[##(##^{$}^]#&(&*{)%)&][&{]&#]}[[^^&[!#}${@_(

Need to find characters that occur a very few amount of times.

---

### Post by WW on 2008-07-10
++i doesn't work in Python; try **i += 1**.

---

### Post by Lster on 2008-07-10
I'm not quite sure what you're trying to do there. The clue is that you need to shift each character 2 places forward in the alphabet. I have working code if you want to see it (likely spoilers).

---

### Post by archivator on 2008-07-10
This is hardly Pythonic and your approach has multiple problems associated with it. 

1. A dictionary should not be called dict. dict is built-in type and you might have troubles this way.
2. What's that `dict' doing at the end? Are you using python < script.py ?
3. You're using a C-ish approach to reading a file and it's .. well, wrong.
```

File = open("string.txt")
for line in File:
    print line

```
Much better, isn't it?
4. String are sequences.
```

for char in line:
    print char

```

I think you can figure the rest by yourself :)

---

### Post by TreeFinger on 2008-07-10
thank you all for the replies :)

first day programming in python and your guys tips helped me out a lot.

got the answer rather quickly after reading your posts.

could you guys check out my new program and tell me if there is anything not needed??

[php]
no cheating
[/php]

---

### Post by WW on 2008-07-10
line* [i]is* char, so you can replace each occurrence of line[i] with char; there is no need for the variable i.

---

### Post by ghostdog74 on 2008-07-10
```

data = open("file").read()
print [ (i,data.count(i)) for i in set(list(data)) 

```

---

### Post by Luggy on 2008-07-11
I stumbled across the same challenge!

My solution was 9 lines big, that's pretty heafty compared to the solutions but granted that I had no idea what I was looking for I think it is still good.

I've attached my solution in case you need some help, or if anyone else wants to look.

---

### Post by TreeFinger on 2008-07-11
alright, all done.

[php]
no cheatin
[/php]

---

