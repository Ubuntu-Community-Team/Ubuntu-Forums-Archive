---
title: "How to move certain files from a directory"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by rohan013 on 2012-03-16
i want to move all the .epub files from a folder(and all it's sub-folders).What command should i use ???

i know i can use ""mv *.epub destination_folder""
but it won't move files from the sub-folders 

Thanks in advance :p

---

### Post by overdrank on 2012-03-16
Hi and welcome, moved and bumped to  Absolute Beginner Talk

---

### Post by MG&amp;TL on 2012-03-16
I think something like:

```

for $files in $(find . -name "*.epub"); do mv $files <folder>; done
```I'm sure somebody will correct me in a minute. Use cp rather than mv to be safe.

---

### Post by cortman on 2012-03-16
> **MG&TL said:**
> I think something like:

```

for $files in $(find . -name ".epub"); do mv $files <folder>; done
```I'm sure somebody will correct me in a minute. Use cp rather than mv to be safe.

Rather than correct, let me compliment your nice little script, MG&TL. But if you're using cp anyway you may as well

```
cp -r *.epub destination_folder
```

Oddly enough, mv doesn't appear to have a recursive option...

---

### Post by MG&amp;TL on 2012-03-17
> **cortman said:**
> Rather than correct, let me compliment your nice little script, MG&TL. But if you're using cp anyway you may as well

```
cp -r *.epub destination_folder
```Oddly enough, mv doesn't appear to have a recursive option...


Thanks, Cortman. I was under the impression that -r moved directories...nice to know. :)

And nice sticky, btw. ;)

---

### Post by cortman on 2012-03-17
> **MG&TL said:**
> Thanks, Cortman. I was under the impression that -r moved directories...nice to know. :)

And nice sticky, btw. ;)

Thanks, MG&TL! It seems to be growing at a comfortable rate and hopefully is proving useful. Thanks for your recent contribution. :)

---

