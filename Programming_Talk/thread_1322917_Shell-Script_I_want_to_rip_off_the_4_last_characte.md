---
title: "Shell-Script: I want to rip off the 4 last characters of a var."
date: 2009-11-11
forum: Programming Talk
---

### Post by Repgahroll on 2009-11-11
I'm making a shell script to efficiently "thumbnalize" lotsa PNG images and convert them into JPG and also watermark their respective PNG sources. The problem is, after some "runtime", i need to delete the ".png" at the end of the variable "$img" (ls *png) , so i can save it as "something.jpg" and not "something.png.jpg".
I tried to use cut and sed but they don't work with variables (i think), a workaround is to "rename" the jpg images after saving them... but i would like to just remove the last 4 char of the variable at runtime and save them correctly.

Thank you in advance.

---

### Post by Sacker on 2009-11-11
You might be able to use something like

basename filename.png .png

---

### Post by Repgahroll on 2009-11-11
Exactly what I need! Thank you very much!!

---

### Post by ghostdog74 on 2009-11-11
no need to use external command. in shell
```

for filename in *.png
do
  echo ${filename%.png}
done

```

---

### Post by Repgahroll on 2009-11-11
> **ghostdog74 said:**
> no need to use external command. in shell
```

for filename in *.png
do
  echo ${filename%.png}
done

```

COOL!!

Many thanks! ;)

---

### Post by John Bean on 2009-11-11
> **Repgahroll said:**
> I tried to use cut and sed but they don't work with variables (i think)
If you want to use cut you could do this sort of thing:
```
for pngfile in *.png; do
    echo $(echo $pngfile | cut -d. -f1).jpg
done
```

---

### Post by ghostdog74 on 2009-11-11
> **John Bean said:**
> If you want to use cut you could do this sort of thing:
```
for pngfile in *.png; do
    echo $(echo $pngfile | cut -d. -f1).jpg
done
```
no need to use external tools. since the shell can do this, using the shell is much faster ( although to some, they do not care.)

---

### Post by John Bean on 2009-11-12
> **ghostdog74 said:**
> no need to use external tools. since the shell can do this, using the shell is much faster ( although to some, they do not care.)
I'm perfectly aware of that. My reply was in the context of the part of the OP I quoted, to demonstrate the error in his assumption that "cut doesn't work with variables". Although it's not needed or desirable in this case, the use of echo output piped into a filter like cut is a valid (if often abused) technique.

This sort of query deserves a number of possible solutions in order to learn anything from it. Choice is good.

---

### Post by raffaele181188 on 2009-11-12
@John Bean
But that doesn't work if your png is named
```

dotted.image.filename.png

```

---

### Post by John Bean on 2009-11-12
> **raffaele181188 said:**
> @John Bean
But that doesn't work if your png is named
```

dotted.image.filename.png

```
Sigh. Let me say it one more time: the OP wrote "I tried to use cut and sed but they don't work with variables", so I used an example to show him that his assumption was incorrect. He may really need to use a similar construct at some point, so it's useful to know how to use variables with filters like cut.

The most appropriate solution to his problem using the shell's inbuilt functions had already been given.

---

