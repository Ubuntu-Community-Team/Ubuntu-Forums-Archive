---
title: "Save a list of folder contents to text file."
date: 2008-06-13
forum: New to Ubuntu
---

### Post by roscal on 2008-06-13
How can you save a text file, of the contents of a folder?
Just the filenames, not the full data.
Thanks....:)

---

### Post by iaculallad on 2008-06-13
> **roscal said:**
> How can you save a text file, of the contents of a folder?
Just the filenames, not the full data.
Thanks....:)

Basically you could dump folder contents by:

```
ls -a > content.txt
```

---

### Post by roscal on 2008-06-13
Thanks,.. to qualify...
I don't want to dump the folder.
I want to list the contents.
A list of the files within a folder.
Saved as a text file (or whatever).
Just a list of filenames.
Easy way would be nice .....
:)
Cant figure it out myself, took me 2 years to do it in windows.
Any and all help, mucho appreciated...

---

### Post by Vivaldi Gloria on 2008-06-13
> **roscal said:**
> 
I want to list the contents.
A list of the files within a folder.

iaculallad's command just does that. try it.

Let me say again, Start gnome-terminal. Now the command

```
ls -a 
```

lists all files in the current folder. You can move between the folders with the cd command and use ls -a to see their contents. If you want you can select an area with mouse, right click and copy it.

```
ls -a > save.txt
```

saves the output of ls -a to save.txt file. So you'll get the list of files saved in it. 

You should really read

[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

---

### Post by terrorsathan on 2008-06-13
```
 ls -al | grep ^\- > file.txt
```
Maybe it's that what you want?

---

### Post by ad_267 on 2008-06-13
You can also use "ls -1 > file.txt" to get everything in one column without any extra info (That's a one, not an L or an I). There's heaps of options, just type "man ls" to see what you can do.

Edit: If you want only files and not directories like in terrorsathan's method, you can use:

```
ls -l | grep ^\- | awk '{print $8}' > file.txt
```

Which will give the list of files without any extra information. (Found that here: [http://www.unix.com/unix-dummies-questions-answers/18814-ls-files-only.html](http://www.unix.com/unix-dummies-questions-answers/18814-ls-files-only.html))

---

