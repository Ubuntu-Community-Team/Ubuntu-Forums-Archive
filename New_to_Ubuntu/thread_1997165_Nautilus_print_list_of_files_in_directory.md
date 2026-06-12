---
title: "Nautilus print list of files in directory?"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by held7over on 2012-06-04
Ubuntu 10.10 and Ubuntu 12.04

Can Nautilus print to printer a list of files contained in a directory that a person is looking at on screen?

If not, what command do I need to do this from the command line? I am not sure how I discover and identify my printer choice to use from the command line...(I have one printer attached to each computer right now).

Thanks! :)

---

### Post by cariboo on 2012-06-04
The easiest way to print a file listing, is to open a terminal and use the following command to create a text file:

```
ls -Rla > files.txt
```

On my system the above command creates a 5.6MiB text file, but it lists everything.

---

### Post by held7over on 2012-06-05
Ah! Super cool! 

Thanks cariboo907! That's a great solution. It works perfect for what I needed.

---

