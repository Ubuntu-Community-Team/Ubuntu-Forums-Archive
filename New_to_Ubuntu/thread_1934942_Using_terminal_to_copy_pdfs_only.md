---
title: "Using terminal to copy pdfs only"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by mferarri on 2012-03-03
Hi Ubuntu Forums,

I'm trying to use the terminal to organise my downloads folder. I want to be able to copy and paste items by file type into the right folder. 
My question is: 
1. How do i select all the pdfs in my downloads folder (using a terminal) by either using the mv or cp command? and move only the pdfs into the ebooks folder? 
2. Can i use the cp command to cut instead of copy?

thanks,

---

### Post by yeats on 2012-03-03
> 1. How do i select all the pdfs in my downloads folder (using a terminal) by either using the mv or cp command? and move only the pdfs into the ebooks folder?

```
mv /home/username/Downloads/*.pdf /home/username/ebooks/
```

(substituting your actual username for "username" and the correct directory path to your ebooks folder, of course)

> 2. Can i use the cp command to cut instead of copy?

cp is for "copy/paste"
mv is for "cut/paste" or can be thought of as "rename"

---

### Post by winh8r on 2012-03-03
enter the commands :


```
man cp
```

```
man mv
```


for explanation of all available functions of these commands.

You can enter

man <name of command> for info on usage and options of all commands.

---

### Post by McNils on 2012-03-03
If all files have the same extension (pdf) you can use this command to copy all pdfs.

```
cp *pdf toFolder
```


If you want to keep creation date use 
```
cp -p *pdf toFolder
```

Not sure what you mean with cut?

---

### Post by mferarri on 2012-03-03
> **yeats said:**
> ```
mv /home/username/Downloads/*.pdf /home/username/ebooks/
```(substituting your actual username for "username" and the correct directory path to your ebooks folder, of course)

cp is for "copy/paste"
mv is for "cut/paste" or can be thought of as "rename"


thanks yeats. this is exactly what i wanted to know.


> **winh8r said:**
> enter the commands :

```
man cp
``````
man mv
```
for explanation of all available functions of these commands.

You can enter

man <name of command> for info on usage and options of all commands.

thanks winh8r, but i read the man pages. they're pretty technical for a noob like me and it never mentioned antyhing bout using a star to copy only particular file types like what yeats was taking about.

> **McNils said:**
> If all files have the same extension (pdf) you can use this command to copy all pdfs.

```
cp *pdf toFolder
```
If you want to keep creation date use 
```
cp -p *pdf toFolder
```Not sure what you mean with cut?

what i meant was like Ctrl+C and Ctrl V, my bad, it's actually the mv command .thanks for the creation date tip though.

---

### Post by winh8r on 2012-03-03
Okay, glad you got it sorted out.

The * symbol is used in many scenarios as a "wildcard" option.

So when you are searching for or trying to isolate something when you use the * it basically means "every or any" of something.

So *.pdf specifies "everything which ends in the extension .pdf"

it is a very useful option to remember for all tasks where there are more than a couple of items you are working with.

It works with all filetypes too not just pdf files.

---

