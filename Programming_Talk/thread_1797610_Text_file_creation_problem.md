---
title: "Text file creation problem"
date: 2011-07-05
forum: Programming Talk
---

### Post by stamatiou on 2011-07-05
Hey guys,
I am new to C (actually I am still learning) and I tried to create a file with the command fopen("file","wb"); and then I wrote an array of structs on it with the command: fwrote(array,sizeof(struct name),100,fp); and the file was created but when I tried to open the file with gedit it told me:
Could not display "/root/Documents/file"
The file is of an unknown type

How can I fix that?

---

### Post by Zugzwang on 2011-07-05
It looks like as if the file is just fine, but gedit is a *text* editor and seemingly refuses to open non-text files. Try installing a hex editor from the repository and use that one instead.

---

### Post by stamatiou on 2011-07-05
> **Zugzwang said:**
> It looks like as if the file is just fine, but gedit is a *text* editor and seemingly refuses to open non-text files. Try installing a hex editor from the repository and use that one instead.
Hex Editor can also read text files?

---

### Post by Zugzwang on 2011-07-05
> **stamatiou said:**
> Hex Editor can also read text files?

It can read any file type. The point is that, judging from the error message you are getting from gedit, your code is *not* writing a text file. 

By the way, there is also a hex viewer coming with Ubuntu: try "hd /yourfile" in the terminal, and it will print you the content of the file you wrote. Then you can have a look what was actually written to the file.

---

### Post by Arndt on 2011-07-05
> **stamatiou said:**
> Hey guys,
I am new to C (actually I am still learning) and I tried to create a file with the command fopen("file","wb"); and then I wrote an array of structs on it with the command: fwrote(array,sizeof(struct name),100,fp); and the file was created but when I tried to open the file with gedit it told me:
Could not display "/root/Documents/file"
The file is of an unknown type

How can I fix that?

What you are creating is not a text file. It will contain the byte sequences corresponding to the types in the struct, which may be integers, pointers, etc. There are likely to be many control characters in it (ASCII value < 32).

Writing structs directly to file like this can be a proper thing to do, if you are sure that the same program, on the same architecture, and compiled with a closely related compiler, will read the file later. Otherwise you can't be sure that they use the same format.

---

### Post by cgroza on 2011-07-05
> **Arndt said:**
> What you are creating is not a text file. It will contain the byte sequences corresponding to the types in the struct, which may be integers, pointers, etc. There are likely to be many control characters in it (ASCII value < 32).

Writing structs directly to file like this can be a proper thing to do, if you are sure that the same program, on the same architecture, and compiled with a closely related compiler, will read the file later. Otherwise you can't be sure that they use the same format.
In this case one would use serialization. cPickle is one of them.

---

