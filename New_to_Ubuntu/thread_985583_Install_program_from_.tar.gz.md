---
title: "Install program from .tar.gz"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by gvanb on 2008-11-17
Can someone please give me some real answers on how to install a program.
I have a .tar.gz file sitting on my desktop.  None of the instructions or online helps have produced any results for me.  So far I have only been able to  create a new directory, but i can't access it because I don't have permission. Thanks.

---

### Post by karlr42 on 2008-11-17
What's the program? You should never install from tar.gz if you don't have to.

Or, just right click and select "extract here". If there's a file ending in .deb, double click it.

---

### Post by chips24 on 2008-11-17
i hate it when poeple dont answer right away... so im going to
 
type "sudo apt get install build-essential" once you insert the ubuntu disk...
 
extract the file by right on clicking the package and and clicking on "extract here"
 
open the command line and type "cd "( make sure you add the space) click and drag the folder into the command line.
 
find the "configure" file
 
drag it into the cammand line (./configure doesnt always work...)
 
type "make"
 
type "sudo make install"
 
and than your done, make sure you install other packages that it tells you to get in order to make the program run... sorry if you think this instruction is a bit complicated...
 
and if you ont have permissions, just type "sudo" before the command. ^_^

---

### Post by chips24 on 2008-11-17
> **karlr42 said:**
> What's the program? You should never install from tar.gz if you don't have to.
 
Or, just right click and select "extract here". If there's a file ending in .deb, double click it.
 
 he said .TAR.GZ file not .DEB

---

### Post by karlr42 on 2008-11-17
.debs often come compressed as tar.gz's, I find, I thought maybe this was on of these cases. In any case, installing from the repo's is a much better option if possible for this program.

---

### Post by chips24 on 2008-11-17
> **karlr42 said:**
> .debs often come compressed as tar.gz's, I find, I thought maybe this was on of these cases. In any case, installing from the repo's is a much better option if possible for this program.
 
ok, sorry

---

