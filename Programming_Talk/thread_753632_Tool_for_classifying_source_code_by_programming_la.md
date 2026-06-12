---
title: "Tool for classifying source code by programming language"
date: 2008-04-12
forum: Programming Talk
---

### Post by climatewarrior on 2008-04-12
Does anyone know of a good foss tool for classifying source code files by programming language? I can classify some of them(There are a lot of languages I have never dealt with) by hand, the problem is that I have to classify thousands of them. Does anyone know of a good tool that can do this? Thanks

---

### Post by pmasiar on 2008-04-12
So you are looking for a program what will read text file - source in some language, and will output which language is it? From like 6000 known languages?

And why you need that?

---

### Post by climatewarrior on 2008-04-12
I'm working on implementing some software metrics tools into the netbsd build process and I want to get good statistics related to how many files are written in this and that. I really don't need support for the 6000+ of them. Having support for the top 50 or 100 would make the cut. I'm already using a tool called cloc that can do what I want. But it's making a lot of mistakes when it comes to recognizing programming languages. So I want something else to improve cloc's abilities.

---

### Post by ghostdog74 on 2008-04-12
on *nix, you can use file command
```

# more test.c

#include <stdio.h>

# file test.c
test.c: ASCII C program text


```
you can try some other programming language source and see

---

### Post by nanotube on 2008-04-13
> **ghostdog74 said:**
> on *nix, you can use file command
```

# more test.c

#include <stdio.h>

# file test.c
test.c: ASCII C program text


```
you can try some other programming language source and see

not very good - it says "Java program text" when I feed it python files....

---

### Post by ghostdog74 on 2008-04-13
> **nanotube said:**
> not very good - it says "Java program text" when I feed it python files....

if you have the shebang eg #!/usr/bin/python if may work. For more info , check man file. there's a magic file you can define. think its in /usr/share/misc/magic. I have never played with it though.

---

### Post by popch on 2008-04-13
In a project I did a while back I wrote a generic parser which took two inputs, a syntax and a text, and produced a parse tree of the text.

For the task you describe, you could use such a parser and let it apply each syntax against every program to be classified. It then would produce a list of syntaxes which each text satisfies.

I am not quite sure if you just have to encode the lexical syntax for each language or if it is necessary to encode the full syntax. I suspect the latter.

I implemented parts of the parser twice, once in Prolog and once in Smalltalk. However, I have kept no scrap of it as I did that project just for fun and lost interest later on.

---

### Post by nanotube on 2008-04-13
> **ghostdog74 said:**
> if you have the shebang eg #!/usr/bin/python if may work. 

yes, that does make it work. :)

---

### Post by kknd on 2008-04-13
There is Ohloh counter.

---

### Post by climatewarrior on 2008-04-14
Yeah ohcount looks preety nice. I will check it out.

---

