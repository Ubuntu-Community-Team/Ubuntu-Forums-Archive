---
title: "How to install software google gadget for linux 10.1"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by prifer on 2008-09-10
Friends,
I want to install google gadgets for linux 10.1, but dunno how. I have download the package and read the file "INSTALL", but i dont understand the instruction:

[I]Briefly, the shell commands `./configure; make; make install' should
configure, build, and install this package.  The following
more-detailed instructions are generic; see the `README' file for
instructions specific to this package.[/I]

where should I exeecute this command?

:confused:

---

### Post by hyper_ch on 2008-09-10
in the terminal in the dir that you go after extracting the compressed .tar.gz or whatever file it is... for compiling you also need to install the build-essential package. Very likely you'll also need to install some -dev libraries.

---

### Post by prifer on 2008-09-10
I am opening the dir of it, but i can't see the "terminal" to be clicked?

---

### Post by hyper_ch on 2008-09-10
The linux terminal or command-line interface is very powerful. Open a terminal via Applications -> Accessories -> Terminal (Gnome) or K-menu -> System -> Konsole (KDE).  Guide: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by nothingspecial on 2008-09-10
The terminal is acessed Accessories > Terminal in your menu.
This will open a terminal in your home directory.
From there you must navigate to the downloaded and extracted file using the cd command.

---

### Post by Bölvaður on 2008-09-10
> **nothingspecial said:**
> From there you must navigate to the downloaded and extracted file using the cd command.

He might not know the commands, not everyone used to use DOS and Unix before graphical user interfaces.


The commands which you need for this job are simple


ls   <- list all the files and folders inside the folder you are located in

cd Desktop   <- cd means change directory, and then you write which directory that is either by telling it which directory either by full path like cd /home/your_user_name/Desktop or by selecting a folder you are located next to.. like Desktop if you are inside your /home/your_user_name/

when you have traveled to the right location where the files you found are, then just copy what it said:

./configure; make; make install

Im not sure if you need to put sudo in front of that for super admin access.... they really should put this to synaptic....

---

### Post by biji on 2008-09-10
whats google gadget for?

---

