---
title: "Bash converter from pwd to txt?"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by honeybear on 2012-12-10
Hi,

I would like to find a script (bash) that can convert the code of a microsoft pocket word or an app from the repositories.

pwd is visibly not so common to be used (MS) and there is not so much results for that.

Thanks

```
{\pwd2\ansi{\*\pwdcomment 

************************************************************************
* 
* This is a Microsoft Pocket Word document. 
* 
* To view this Pocket Word document in Microsoft Word, you will need the 
* Pocket Word Converter for Microsoft Office. For further details visit 
* the Microsoft Handheld PC web site, at 
* 
*         http://www.microsoft.com/mobile/hpc
* 
************************************************************************

}\ansicpg1252\deff0\deflang1033{\fonttbl{\f0\fnil\fcharset0 Times New Roman;}}
{\colortbl ;}
\viewkind4\uc1\pard\cf0\f0\fs28 Hello \tab World\par

}

```

---

### Post by Impavidus on 2012-12-10
I've never heard of pwd, but I must say it looks as if inspired by TeX, so not totally unfamiliar.

Converting to txt means just stripping all formatting from the file, so you may be able to write a script yourself to remove all strings starting with backslash, comments, font declarations etc. and just keep the plain text. I've done things like that in the past using sed, to make word frequency statistics of tex files:```
$ cat script
#Remove comments (I know escaped %-signs do not occur in my text)
s/%.*//
#Replace dotless j by ordinary j
s/\\j{}/j/g
#Replace some commands by (one of) their argument(s)
s/\\emph{\([^}]*\)}/\1/g
s/\\mbox{\([^}]*\)}/\1/g
s/\\glslink{[^}]*}{\([^}]*\)}/\1/g
s/\\chapter{\([^}]*\)}/\1/g
...
#Delete other commands
s/\\[A-Za-z][0-9A-Za-z\*]*//g
...
$ cat file1.tex file2.tex | sed -f script >output
```Of course, your script will look differently, using a different source format. Sed may not be the best tool to do this, I used it because I already was familiar with it.

---

