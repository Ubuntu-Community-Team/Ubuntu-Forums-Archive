---
title: "about files"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by konza on 2008-09-03
This has to be simple but i can not find it using google or the search box.  HOW do i make a simple file for my home directory. I can create the folder but do not know how to add a document to it. :-(

---

### Post by S.A.A on 2008-09-03
Could you be more detailed, please?

---

### Post by nothingspecial on 2008-09-03
What sort of file do you want to make. For a text file you could use gedit. Or you could use open office for a word type doc.

---

### Post by iaculallad on 2008-09-03
> **konza said:**
> This has to be simple but i can not find it using google or the search box.  HOW do i make a simple file for my home directory. I can create the folder but do not know how to add a document to it. :-(

Doing those words in the terminal would be:

```
mkdir ~/SomeFolder
```

and to create/make a simple file:

```
gedit ~/SomeFolder/thefile_you_want_to_create
```

and how to add document to it (add =? move)

```
mv /source/document.ext ~/SomeFolder
```

---

### Post by whitethorn on 2008-09-03
open gedit and then File -> Save as -> select your folder

or if you're using the terminal.  gedit /home/user/foldername/filename  and then once you've finished writing just save, and the file will be created.  You can use any editor to do this with.

---

### Post by lordhaworth on 2008-09-03
Dont you normally save files in a folder once you've started working on them?

I dont see why you would want to save blank files to a location?

---

### Post by jemate18 on 2008-09-03
> **konza said:**
> This has to be simple but i can not find it using google or the search box.  HOW do i make a simple file for my home directory. I can create the folder but do not know how to add a document to it. :-(

go to that folder (inside ) and right click -> Create Document -> Empty File

---

