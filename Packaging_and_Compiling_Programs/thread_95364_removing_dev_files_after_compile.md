---
title: "removing dev files after compile"
date: 2005-11-26
forum: Packaging and Compiling Programs
---

### Post by timczer on 2005-11-26
It seems that each time I compile something from source, invariably I will need to download another -dev package.  There are now a lot of them on my system.  Since I tend to tweak my system on a regular basis, I end up with a lot of memory taken up with things I probably don't need.  My question is that I don't know that after the immediate install these -dev files are ever needed again.  Can they safely be removed after the program has been installed, or are they needed for the program to run?

---

### Post by Xian on 2005-11-26
[QUOTE=timczer]My question is that I don't know that after the immediate install these -dev files are ever needed again.  Can they safely be removed after the program has been installed, or are they needed for the program to run?[/QUOTE]
In general they will continue to be needed as long as the package which required them as deps in the first place remains installed on your system.

---

### Post by Roptaty on 2005-11-27
Development files are only needed for compilation of the program, and not running it. Also, development files take generally low space on your computer.

---

### Post by urukrama on 2007-07-19
So if I get this right, it could do no harm to remove -dev packages? If I select them for removal in Synaptic, no often it doesn't tell me other packages depend on it.

Some of these packages do take a lot of space. I just removed the dev files I needed for an application that I no longer use, and it came to about 55 MB!

---

### Post by kknd on 2007-07-19
You can remove -dev packages without worry. They are used only in compiling.

---

### Post by Duranxl on 2009-03-30
i tried doing this, but it also marks build-essential, automake etc for removal when i mark '-dev' files for removal..
I can't remove the -devs without removing build-essential etc:confused:

---

