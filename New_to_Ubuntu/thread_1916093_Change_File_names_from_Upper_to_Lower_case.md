---
title: "Change File names from Upper to Lower case"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by cressrt on 2012-01-27
Does anyone know of an easy way to change a whole folder of files that have been saved in Upper (Capitals) case to Lower Case without having to individually rename them.
Thanks for any help.

---

### Post by Grenage on 2012-01-27
I was going to type something out, but Google was that much quicker! ;)

[http://www.linuxjournal.com/content/convert-filenames-lowercase](http://www.linuxjournal.com/content/convert-filenames-lowercase)

---

### Post by nothingspecial on 2012-01-27
> **Grenage said:**
> I was going to type something out, but Google was that much quicker! ;)

[http://www.linuxjournal.com/content/convert-filenames-lowercase](http://www.linuxjournal.com/content/convert-filenames-lowercase)

That script is full of bad practice, for example it will fail if the file names have spaces in them.

I would use the rename command. From the directory the files are located in

```
rename -n 'y/[A-Z]/[a-z]/' *
```

The -n option means that rename will just tell you what would happen without actually doing it. If you are happy with the results, run it again without -n

```
~/test$ ls
54FTH.jpg  87Gyytr.jpg  BHGyGTy.jpg  FTrEWb.jpg  LPJUYT.jpg
~/test$ rename -n 'y/[A-Z]/[a-z]/' *
54FTH.jpg renamed as 54fth.jpg
87Gyytr.jpg renamed as 87gyytr.jpg
BHGyGTy.jpg renamed as bhgygty.jpg
FTrEWb.jpg renamed as ftrewb.jpg
LPJUYT.jpg renamed as lpjuyt.jpg
~/test$ ls
54FTH.jpg  87Gyytr.jpg  BHGyGTy.jpg  FTrEWb.jpg  LPJUYT.jpg
~/test$ rename 'y/[A-Z]/[a-z]/' *
~/test$ ls
54fth.jpg  87gyytr.jpg  bhgygty.jpg  ftrewb.jpg  lpjuyt.jpg

```

---

### Post by Grenage on 2012-01-27
> **nothingspecial said:**
> That script is full of bad practice, for example it will fail if the file names have spaces in them.

I would use the rename command. From the directory the files are located in


Excellent, I wasn't aware of the rename program; that's one to remember.

---

### Post by Vaphell on 2012-01-27
using common approach with *for file in *.jpg; do mv $file $newfile; done* loop one can take advantage of standard bash features
${file^^} = uppercase
${file,,} = lowercase

```
$ for f in abc DeF GHI; do echo "${f}" "->" upper: "${f^^}" lower: "${f,,}"; done
abc -> upper: ABC lower: abc
DeF -> upper: DEF lower: def
GHI -> upper: GHI lower: ghi
```

---

### Post by cressrt on 2012-01-27
That was great, thanks very much for the info, especially the ability to check the result before actually doing it.

---

