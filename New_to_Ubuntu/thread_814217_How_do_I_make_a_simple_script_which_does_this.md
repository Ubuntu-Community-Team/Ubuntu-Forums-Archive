---
title: "How do I make a simple script which does this?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by deleyd on 2008-05-31
Now it's time for me to learn how to make a script.

I got program html2text installed, and I figured out it works from a terminal prompt as:

html2text   <input.html   >output.txt

Now I want to convert all the *.html files in a directory to text. What would be a simple way to do that?

(I hope 'script' is the correct name for a file which does a bunch of line mode commands, the equivalent of a .BAT batch file in windows.)

---

### Post by dracayr on 2008-05-31
hi,
are the html files supposed to output in one big all_output file, or is there supposed to be a text file for each html file?

---

### Post by decoherence on 2008-05-31
open up the terminal and cd in to the directory with the html files.

```
for i in *.html; do html2text $i >`basename $i .html`.txt; done

```

this will write a text version of each file. now if you want, rm *.html to get rid of the html files.

---

### Post by deleyd on 2008-05-31
OK, now I need a reference to a book or website on writing these script files, and a whole bunch of simple real world examples is nice to learn from (nothing like real working code examples when the documentation is abstract).


> **dracayr said:**
> hi,
are the html files supposed to output in one big all_output file, or is there supposed to be a text file for each html file?
Either way actually for my needs. I was thinking of one output file for each input file.

---

### Post by dracayr on 2008-05-31
hi,
well, for one file, simply type 
```
html2text *.html -o output.txt
```
for seperate files, follow decoherence's instructions

dracayr

---

### Post by Monicker on 2008-05-31
> **deleyd said:**
> OK, now I need a reference to a book or website on writing these script files, and a whole bunch of simple real world examples is nice to learn from (nothing like real working code examples when the documentation is abstract).



Either way actually for my needs. I was thinking of one output file for each input file.

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")
[http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

---

