---
title: "pascal on ubuntu"
date: 2005-11-17
forum: Programming Talk
---

### Post by ofek on 2005-11-17
I'm programing in pascal at school (my second year).
In school we got windows and well borland pascal to go with it.
I took the source of a fully working program that i built in school("DATELIKE.PAS"), and downloaded gpc using apt-get.
Gpc working, but when i type gpc DATELIKE.PAS (in the source code directory) it says:
```

ofek@ubuntu:~/Programing/Pascal$ gpc DATELIKE.PAS
/usr/bin/ld:DATELIKE.PAS: file format not recognized; treating as linker script
/usr/bin/ld:DATELIKE.PAS:1: syntax error
collect2: ld returned 1 exit status

```
I realy don't know whats wrong.

I have another quick question on the subject: Is there a way to make a gui to a pascal program using linux (that will work on windows too if possible)?

---

### Post by ofek on 2005-11-17
O.k I fixed that problem using -x Pascal, but now it give me an error when it gets to the uses crt; line.
```

DATELIKE.PAS:2: error: module/unit interface `crt' could not be imported

```
uses crt isn't supported in gpc?

---

### Post by ofek on 2005-11-18
I realy need help and i didn't find what im looking for on google. please help

---

### Post by public_void on 2005-11-18
> I have another quick question on the subject: Is there a way to make a gui to a pascal program using linux (that will work on windows too if possible)?
Your'll have to use OO Pasal, aka Delphi. These also Kylix, but I've never looked at that. You have to use the CLX library components, instead of Windows VCL. CLX will work on windows, but there aren't as many components for it, but these enough for you to use.

Found this [link]("http://www.gnu-pascal.de/gpc/GPC-Units.html"), may be of some use. I'm a linux n00b, so I'm not too sure about your other problem.

---

### Post by LorenzoD on 2005-11-18
CRT should be included with GPC. I however, always preferred freepascal. 

As for the GUI programming: you may want to look into Lazarus ([http://lazarus.freepascal.org)](http://lazarus.freepascal.org)). It was a little unstable last time I tried it, but that was a while ago. I never use Windows, so I'm afraid I can't comment on how well it works for that platform (but I know there are Windows binaries).

---

### Post by ofek on 2005-11-18
ty people and i will try free pascal and about the delphi thing, i love delphi and all but my teacher wants a pascal program.

---

### Post by ofek on 2005-11-18
Fpc works like a charm and lazarus project looks very promising thx for all the help ppl.

---

