---
title: "Copy files with Nautilus."
date: 2008-05-04
forum: New to Ubuntu
---

### Post by kikapu on 2008-05-04
Hi,

i am just trying to do the following:

I know by now, how i can copy files/directories in the terminal, from my home directory to another one that i do not own (e.x /etc/lib/...)
But how i can do it through Nautilus ?? I have a window open with the source files and another one which is the destination, how i can i copy them there by using the GUI and without getting a "permission denied" message ?? It is very inconvinient to go to the terminal and start writing all this stuff just to copy these files.

---

### Post by otrojake on 2008-05-04
Have you tried starting a nautilus window as root and then copying the files from the one directory to your own?```
gksudo nautilus
```

---

### Post by yamawho on 2008-05-04
If you need a GUI file browser with super user access, run:

Code:

sudo nautilus

---

### Post by kikapu on 2008-05-04
Xxxmmm....i knew that i would be back to that termnal :lolflag:

So, i have to use nautilus from there to be able to do this stuff. I thought that there would be a way to this "on the fly".

Anyway. Thanks for the help!

A, what is the difference between sudo and gksudo ??

---

### Post by yamawho on 2008-05-04
When you use sudo nautilus it opens the GUI.

Here is a good link ...

[http://ubuntuforums.org/showthread.php?t=781355&highlight=superuser+mode](http://ubuntuforums.org/showthread.php?t=781355&highlight=superuser+mode)

---

### Post by Oldsoldier2003 on 2008-05-04
rather than reopen the long running sudo vs gksudo argument i'll point you to a link. Personally I believe in using gksudo for graphical apps because its better to be safe than sorry.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by otrojake on 2008-05-04
EDIT:  That links a good reference, I'd recommend checking that out.

---

### Post by kikapu on 2008-05-04
> **otrojake said:**
> EDIT:  That links a good reference, I'd recommend checking that out.

Ok, i just did. So, gksudo for the GUI apps and sudo for non-graphics, correct ?

---

### Post by otrojake on 2008-05-04
That's pretty much the bottom line.

---

### Post by yamawho on 2008-05-04
> **Oldsoldier2003 said:**
> rather than reopen the long running sudo vs gksudo argument i'll point you to a link. Personally I believe in using gksudo for graphical apps because its better to be safe than sorry.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Many thanks for explaining :)

---

