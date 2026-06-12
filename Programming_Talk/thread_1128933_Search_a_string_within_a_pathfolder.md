---
title: "Search a string within a path/folder"
date: 2009-04-18
forum: Programming Talk
---

### Post by huangyingw on 2009-04-18
Hello, I am a beginnger at shell coding.
Let me take example to explain my need.
For example, I want to find some example about "find" command, I think the best way is a scripts which could search through a specified path, to show the files which contains a string "find".
Could some body provide me with such a script?
Great thanks.

---

### Post by huangyingw on 2009-04-18
Well, I have found it. And share:
find /usr -name \*.sh -exec grep -wnHA5 grep {} \; > ${script_path}/find.log.
the above script could search through the path /usr for any files that contain "grep" key word, and list out some location information.

---

### Post by dwhitney67 on 2009-04-18
EDIT: Nevermind; it appears that you found your own solution.

-------------

Use the 'find' command, which offers a rich array of options.  From your query, probably the following would suffice:

```

find start_dir -type f -exec grep search_str {} \;

```
where you would replace start_dir with the directory of your choice, and similarly you would replace search_str with the string of your choice.

For example:
```

find . -type f -exec grep foo {} \;

```

---

### Post by Keith Hedger on 2009-04-18
The first place to look for info on a command is the man pages ie:```
man find
```

---

### Post by huangyingw on 2009-04-21
> **dwhitney67 said:**
> EDIT: Nevermind; it appears that you found your own solution.

-------------

Use the 'find' command, which offers a rich array of options.  From your query, probably the following would suffice:

```

find start_dir -type f -exec grep search_str {} \;

```
where you would replace start_dir with the directory of your choice, and similarly you would replace search_str with the string of your choice.

For example:
```

find . -type f -exec grep foo {} \;

```
Thank you for your detail introduction.

---

### Post by huangyingw on 2009-04-21
> **Keith Hedger said:**
> The first place to look for info on a command is the man pages ie:```
man find
```
hi, on mentioning the man, BTW, could you tell me where to see my desired command's docs. I would prefer to see in a file.
I means, is there such a doc, like "/usr/sbin/docs/man/find*", which contains all the detail of "man find"'s output?
If my request is unclear, please let me know.

---

### Post by Bodsda on 2009-04-21
Man pages can be found in /usr/share/man

---

### Post by Keith Hedger on 2009-04-21
You can create and read a  html file with:
```

man2html $(man -w find) >/tmp/f.html
firefox /tmp/f.html
```

for instance

---

### Post by huangyingw on 2009-04-26
> **Keith Hedger said:**
> You can create and read a  html file with:
```

man2html $(man -w find) >/tmp/f.html
firefox /tmp/f.html
```

for instance

Yes, great, I really appreciate this form.

---

### Post by huangyingw on 2009-04-28
> **Keith Hedger said:**
> You can create and read a  html file with:
```

man2html $(man -w find) >/tmp/f.html
firefox /tmp/f.html
```

for instance

Hi, as I don't like to read docs in html. 
So, is there a man2txt command to replace man2html? So, I could use it like following example?
```

man2txt $(man -w find) >/tmp/f.txt
vim /tmp/f.txt
```

---

### Post by unutbu on 2009-04-28
```
gunzip -c $(man -w find) | nroff -man > /tmp/f.txt
vim /tmp/f.txt
```

Note that not all man pages are gzipped. If "$(man -w COMMAND)" returns a plain text man file, then 
```

nroff -man $(man -w COMMAND) > /tmp/command.txt
```

should work

---

### Post by Keith Hedger on 2009-04-28
Simpler```
man find > /tmp/f.txt
less /tmp/f.txt
```

---

### Post by huangyingw on 2009-04-29
> **Keith Hedger said:**
> Simpler```
man find > /tmp/f.txt
less /tmp/f.txt
```
Great thanks, that is indeed the most excitting find I need....

---

