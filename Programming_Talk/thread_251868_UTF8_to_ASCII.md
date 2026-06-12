---
title: "UTF8 to ASCII"
date: 2006-09-06
forum: Programming Talk
---

### Post by musther on 2006-09-06
A while ago I posted asking about a command line method of converting UTF8 files to ASCII, ([http://ubuntuforums.org/showthread.php?t=224552](http://ubuntuforums.org/showthread.php?t=224552))  The solution which was posted seemed to work, until I noticed that all none alphanumerical characters were going missing, - and ' were being replaced with question marks, so

He'd had a hard night

became:

He?d had a hard night

IN short, I'm still looking for a way to convert my UTF8 files, at the moment I open them in open office, save as, select text encoded, and finally select Western (ASCII/US).  THe only problem with this is that I have a lot of files and it can take a long time.

Thanks

---

### Post by toojays on 2006-09-06
Does iconv do what you want?```
iconv --from-code UTF-8 --to-code US-ASCII -c inputfile > outputfile
```

---

### Post by musther on 2006-09-06
Seems to do the trick, thanks a lot!

---

### Post by molavec on 2009-02-12
Hello, I tried used the iconv command to convert from utf8 to ascii, but all character likes áéíóú disappear in the output file. what I must to do to convert this symbol to ascii numeration instead simply delete them??

---

### Post by geirha on 2009-02-12
That's because those characters do not exist in [ASCII](http://en.wikipedia.org/wiki/Ascii). There is a command called unaccent (installed by the package of the same name) that will translate áéíóú to aeiou, so filter through that first, then convert to ascii.

---

### Post by molavec on 2009-02-12
thank to reply geirha, 

I will look this command, because it can be a good "temporally" solution (and i will used right now) to solve my problem but i think the accent its a little important. I try to covert a lot of spanish e-books,in a fast way, from pdf to pdb(palm ereader books) follow this sequence:

PDF -> txt -> pml -> pdb.

My problem is convert áéíóú characters from txt(ú) to pml(/a213). Maybe AWK resolved my problem. 

THX Again geirha for your answer.

---

### Post by geirha on 2009-02-12
I have no experience with palm ereader books, but I'm guessing that if it does not accept utf-8, then it probably accepts one of the latin charset instead. A google for commonly used character sets for spanish gave this result: [http://www.w3.org/International/O-charset-lang.html](http://www.w3.org/International/O-charset-lang.html), which lists iso-8859-1 and windows-1252 for spanish, so try converting to one of those instead. They should both have the accented letters.

```
iconv -f UTF-8 -t ISO-8859-1 inputfile.txt >outputfile.txt
```

---

