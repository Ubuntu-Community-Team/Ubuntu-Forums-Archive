---
title: "python replace backslash"
date: 2009-09-19
forum: Programming Talk
---

### Post by eggdeng on 2009-09-19
I'm trying to get a Python script working on W*nd*ws & am running into trouble with file paths.
In order to be able to create a shortcut, I need to replace the backslashes in a file path with double backslashes 
Both
```
name = name.replace("\","\\")
```
and
```
name = name.replace("\",r"\\")
```
throw the error
```
unexpected character after line continuation character
```
:confused:
Help appreciated.

---

### Post by matmatmat on 2009-09-19
I think it should be:
```

name = name.replace("\\","\\\\")

```

---

### Post by Can+~ on 2009-09-19
```
name = name.repalce(r"\", r"\\")
```

You should use os.path functions to avoid this.

---

### Post by smartbei on 2009-09-19
@Can+~: This doesn't actually work. (I wanted to give that same reply but tested first). It gives the same error:
```

s = "abcdefg\\hijk\\\\"
s.replace(r'\', r'\\')

```
Results in:
```

  File "<stdin>", line 1
    s.replace(r'\', r'\\')
                         ^
SyntaxError: unexpected character after line continuation character

```

So matmatmat's solution is good.

---

### Post by Can+~ on 2009-09-19
> **smartbei said:**
> @Can+~: This doesn't actually work. (I wanted to give that same reply but tested first). It gives the same error:
```

s = "abcdefg\\hijk\\\\"
s.replace(r'\', r'\\')

```

It worked for me...

no, wait, I actually did:

[PHP]>>> r"C:\hello\world\with\slashes".replace("\\", r"\\")
'C:\\\\hello\\\\world\\\\with\\\\slashes'[/PHP]

---

### Post by eggdeng on 2009-09-19
Thanks everyone for the help - matmatmat's solution does the trick. Sadly, I can't treat the file path as a string because it is taken from user input, so I'll check out the os.path methods to see if there is a simpler way. Thanks again :)

---

### Post by fiddler616 on 2009-09-19
> **eggdeng said:**
> Sadly, I can't treat the file path as a string because it is taken from user input
Eh...what? Am I missing something? But I guess if your problems are solved I should stay out of it.

---

