---
title: "[SOLVED] terminal help, please...."
date: 2008-08-07
forum: New to Ubuntu
---

### Post by jmd9qs on 2008-08-07
hi,

i'm trying to find a way to search for all of the pdf's on my hard-drive and move them into one directory. how is this possible via terminal? i have heard of the *grep* command, but am not sure how to use it for this purpose. also, if there is a way to do this via terminal, can i do it in one line (like w/ "pipes")?

---

### Post by ahmatti on 2008-08-07
> **jmd9qs said:**
> hi,

i'm trying to find a way to search for all of the pdf's on my hard-drive and move them into one directory. how is this possible via terminal? i have heard of the *grep* command, but am not sure how to use it for this purpose. also, if there is a way to do this via terminal, can i do it in one line (like w/ "pipes")?

Hi,
An interesting problem, but the solution is luckily very simple:

```

sudo updatedb
mv $(locate *.pdf) target/

``` 

The updatedb updates your search database that locate uses so you will get also the most recent files. I guess updatedb is anyway run daily, so it not needed everytime you run locate. See "man updatedb" and "man locate" for details.

---

### Post by iaculallad on 2008-08-07
> **jmd9qs said:**
> hi,

i'm trying to find a way to search for all of the pdf's on my hard-drive and move them into one directory. how is this possible via terminal? i have heard of the *grep* command, but am not sure how to use it for this purpose. also, if there is a way to do this via terminal, can i do it in one line (like w/ "pipes")?

On your terminal:

```
mkdir ~/Desktop/MyPDF
```

Begin to search (starting from root directory) and move the file to ~/Desktop/MyPDF directory:

```
sudo find / -name '*.pdf' -exec mv '{}' ~/Desktop/MyPDF/ \;
```

---

### Post by Bucky Ball on 2008-08-07
> **ahmatti said:**
> Hi,
An interesting problem, but the solution is luckily very simple:

```

sudo updatedb
mv $(locate *.pdf) target/

``` 

ahmatti, where does this put the pdf files, then? Or am I missing something obvious? Should there be the name of the target directory somewhere in there?

---

### Post by ahmatti on 2008-08-07
> **Bucky Ball said:**
> ahmatti, where does this put the pdf files, then? Or am I missing something obvious? Should there be the name of the target directory somewhere in there?

"target/" is the target directory in this case, should've explained better, sorry!

---

### Post by Bucky Ball on 2008-08-07
> **ahmatti said:**
> "target/" is the target directory in this case, should've explained better, sorry!

ha, sorry, obviously. My mistake. ;p 

That is really neat little code, thanks. :)

---

### Post by ahmatti on 2008-08-07
Glad to help!

---

