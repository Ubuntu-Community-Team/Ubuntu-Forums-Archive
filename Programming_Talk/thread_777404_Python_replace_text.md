---
title: "Python replace text"
date: 2008-05-01
forum: Programming Talk
---

### Post by idn on 2008-05-01
Hi, I am trying to develop a script which does a reasonable effort of figuring out the word count of my latex university essays. I have lots of refereces - like a good student :) - in my essays, that shouldnt actually contribute to the word count. They are all in the bibtex format, for example:

\cite{Nielsen:Overgaard:Pedersen:Stage:Stenild:2006}

I was wondering is there a way to remove this text from a string in python. I have already written all the code to replace a bunch of other stuff (see attachment) but I am completely useless with regular expressions and can't figure out how to do this at all.

Any help would be much appreciated

Jon

---

### Post by tseliot on 2008-05-01
you don't have to use regular expressions for such things. If you're reading the file line by line you can make sure that, for example:
```
line.strip().startswith('\cite{') == False
```

EDIT: I didn't notice the attached file

---

### Post by WW on 2008-05-01
I agree with tseliot--you don't need a regular expression.

Perhaps something like this:
[php]
    # Remove all occurrences of \cite{*}
    while lines.find("\cite{") != -1:
        pre,copen,rest = lines.partition("\cite{")
        citation,cclose,post = rest.partition("}")
        lines = pre + post
[/php]
It uses the partition() function of Python 2.5. If you are using 2.4, you could do something equivalent by using find() and pulling apart the string.

---

### Post by tseliot on 2008-05-01
If you want to use re, try this:
[PHP]pattern = r'\\cite{.*}\\n'
pat1 = re.compile(pattern)
m1 = pat1.match(lines)
if m1:
    lines = lines.replace(m1.group(0), '')[/PHP]

---

### Post by WW on 2008-05-01
P.S. In your code, you can replace this
[php]
    # Seek to the start position in the file
    fileHandle.seek(0)
    fileList = fileHandle.readlines()
    # Loop through each line in the file
    for fileLine in fileList:	
        lines += fileLine
[/php]
with this:
[php]
    lines = fileHandle.read()
[/php]

---

### Post by WW on 2008-05-01
> **tseliot said:**
> If you want to use re, try this:
[PHP]pattern = r'\\cite{.*}\\n'
pat1 = re.compile(pattern)
m1 = pat1.match(lines)
if m1:
    lines = lines.replace(m1.group(0), '')[/PHP]
This appears to assume that each \cite{} is on a line by itself.  This is not a  requirement in LaTeX.

A really concise way to get rid of \cite{...} is to use the **sub** function in the **re** module:
```

    lines = re.sub(r'\\cite{.*}','',lines)

```
(Add the line **import re** somewhere in the beginning of your file.) The first argument to sub is the same pattern as used by tseliot, but without the trailing newline.

Although I said above that you don't need a regular expression, I like this version better than my first one. :)

---

### Post by ghostdog74 on 2008-05-01
you might also want to check for non-greediness in the regexp.

---

### Post by WW on 2008-05-01
> **ghostdog74 said:**
> you might also want to check for non-greediness in the regexp.
Good point!  If a line contains two \cite{} functions, the re.sub function that I gave above will delete both of them and all text between them.  This version avoids that:
```

    lines = re.sub(r'\\cite{[^}]*}','',lines)

```

---

### Post by nanotube on 2008-05-01
> **WW said:**
> Good point!  If a line contains two \cite{} functions, the re.sub function that I gave above will delete both of them and all text between them.  This version avoids that:
```

    lines = re.sub(r'\\cite{[^}]*}','',lines)

```

better yet (or at least, alternatively), use non-greedy matching:
```

    lines = re.sub(r'\\cite{.*?}','',lines)

```

---

### Post by ghostdog74 on 2008-05-01
> **WW said:**
> Good point!  If a line contains two \cite{} functions, the re.sub function that I gave above will delete both of them and all text between them.  This version avoids that:
```

    lines = re.sub(r'\\cite{[^}]*}','',lines)

```

usually, the qualifier for non-greediness is ?, [here ]("http://www.amk.ca/python/howto/regex/regex.html#SECTION000730000000000000000")is a read. So another way is (but am not sure how the outcome of the .sub() will be..have to test out)
```

r'\\cite{.*?}'

```

---

### Post by nanotube on 2008-05-01
> **ghostdog74 said:**
> 
```

r'\\cite{.*?}'

```

ha, beat you to it :) :lolflag:

---

### Post by ghostdog74 on 2008-05-02
> **nanotube said:**
> ha, beat you to it :) :lolflag:

well done, but I am too poor to give you a prize for that :)

---

### Post by nanotube on 2008-05-02
> **ghostdog74 said:**
> well done, but I am too poor to give you a prize for that :)

hehe, and i'm too poor to expect one! :)

---

