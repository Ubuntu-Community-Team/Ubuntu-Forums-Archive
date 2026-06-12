---
title: "Help a noob with sed"
date: 2012-01-27
forum: Programming Talk
---

### Post by Greeface on 2012-01-27
I'm trying to append some text to the end of every line in a file.  I do this:
```
sed -i 's/$/ (Route 704)/' $TEMP1
```

and the output looks like this:
```
28
 (Route 4)
48
 (Route 4)
67
 (Route 4)
```

but I want it to look like this:
```
28 (Route 4)
48 (Route 4)
67 (Route 4)
```



How do I append the string to the same line rather than creating a new one?

Sorry if this is a stupid question.  I searched far and wide but couldn't find anything beyond my initial command.

---

### Post by Arndt on 2012-01-27
> **Greeface said:**
> I'm trying to append some text to the end of every line in a file.  I do this:
```
sed -i 's/$/ (Route 704)/' $TEMP1
```

and the output looks like this:
```
28
 (Route 4)
48
 (Route 4)
67
 (Route 4)
```

but I want it to look like this:
```
28 (Route 4)
48 (Route 4)
67 (Route 4)
```



How do I append the string to the same line rather than creating a new one?

Sorry if this is a stupid question.  I searched far and wide but couldn't find anything beyond my initial command.

It works for me:

```
$ (echo a;echo b; echo c) | sed 's/$/ Route/'
a Route
b Route
c Route
```

What does your file contain, exactly? Use the 'od' command, like this:

```
$ (echo a;echo b; echo c) | od -c
0000000   a  \n   b  \n   c  \n
0000006
```

---

### Post by ofnuts on 2012-01-27
Hmmm. works for me. How does your input file really looks like? Only regular LF at the end of lines?

---

### Post by SeijiSensei on 2012-01-27
This file doesn't happen to be coming from Windows, does it?  If so, try installing the **tofrodos** package, then use the dos2unix program it contains to strip any <CR> characters from each line.  You should be able to use it in a pipe like this:

```
dos2unix < file | sed -i 's/$/ (Route 704)/'
```

---

### Post by Greeface on 2012-01-27
[COLOR="DarkRed"]**EDIT:** I just solved it by piping through *tr -d '\r'*.  Thanks for the help!  I'll have to remember that command, Arndt.[/COLOR]



> **Arndt said:**
> What does your file contain, exactly? Use the 'od' command, like this:

```
$ (echo a;echo b; echo c) | od -c
0000000   a  \n   b  \n   c  \n
0000006
```

Hmm.  When I do *cat /path/to/file.txt | od -c* it gives me this:
```

0000000   7  \r       (   R   o   u   t   e       4   )  \n   2   4  \r
0000020       (   R   o   u   t   e       4   )  \n   4   0  \r       (
0000040   R   o   u   t   e       4   )  \n
0000051

```
I have no idea what that means, heh.  What's the \r?


> **ofnuts said:**
> Hmmm. works for me. How does your input file really looks like? Only regular LF at the end of lines?

$TEMP1 in my example is just the direct path to the text file, which looks exactly like what I posted.  Sorry for my noobishness but I'm not sure exactly what an LF is, just a line break?


> **SeijiSensei said:**
> This file doesn't happen to be coming from Windows, does it?  If so, try installing the **tofrodos** package, then use the dos2unix program it contains to strip any <CR> characters from each line.  You should be able to use it in a pipe like this:

```
dos2unix < file | sed -i 's/$/ (Route 704)/'
```

Nope, it's all Linux.  My script is pulling some numbers out of an HTML file.  I'll double check this part of it to make sure it's only grabbing the number.

---

### Post by Vaphell on 2012-01-27
doesn't matter, the file you process was most likely created under windows

[http://en.wikipedia.org/wiki/Newline#Representations](http://en.wikipedia.org/wiki/Newline#Representations)
windows uses 2 separate symbols to end the line: carriage return( CR,\r) and line feed (LF, \n), while linux uses only LF and that additional CR wreaks havok.

---

### Post by Arndt on 2012-01-27
> **Greeface said:**
> [COLOR="DarkRed"]

Hmm.  When I do *cat /path/to/file.txt | od -c* it gives me this:
```

0000000   7  \r       (   R   o   u   t   e       4   )  \n   2   4  \r
0000020       (   R   o   u   t   e       4   )  \n   4   0  \r       (
0000040   R   o   u   t   e       4   )  \n
0000051

```
I have no idea what that means, heh.  What's the \r?


LF stands for linefeed, which 'od' shows as \n (n for newline). \r is carriage return (CR), which Unix programs usually don't produce or handle well, since the end of line marker in Unix is a simple \n. On Windows it is \r\n.

Your file seems to have things between \r and \n, which may confuse 'sed' even more.

---

