---
title: "Problem running a program from terminal"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by benbran on 2013-06-05
Hi all,
I have downloaded a program called FSL from here :[http://neuro.debian.net/pkgs/fsl.html](http://neuro.debian.net/pkgs/fsl.html)

I followed all the steps from where you click install this package, I opened up the program and it works beautifully. Now I want to be able to open this program from my terminal, however it doesn't seem to work no matter what I try to type. I tried fsl, fsl 5.4, fsl5.4, fsl-5.4 and nothign works. I wanted to maybe find its path and create a new alias to it on my .bashrc file, but I can't locate where it is on my computer. Help please?

---

### Post by Lars Noodén on 2013-06-05
I couldn't get it to install, it claims to have both 32 bit and 64 bit, but nonetheless it complained when I  tried apt-get.

That said, you might try looking to see what files were included in the package with [dpkg](http://manpages.ubuntu.com/manpages/raring/en/man1/dpkg.1.html).

```

dpkg -L dsl-5.0

```

For the executables, look for something in /usr/bin or /usr/local/bin

Or if the installation successfully set up an icon for you, try right-clicking on it and choose "properties" to see what is under the field "command"

---

### Post by oldos2er on 2013-06-05
According to its description fsl "consists of various command line tools, as well as simple GUIs for its core analysis pipelines." I'd run ```
dpkg -L fsl
``` and look for files in /usr/bin/

---

### Post by TNFrank on 2013-06-05
I know the other day when I was playing around with Conky and wanted to run it I typed "conky &" and it ran it. Might try the program name and the "&" symbol.  I'm very, very far from and expert at Terminal but it is one of the things I'm really lovin' about Linux.

---

### Post by deadflowr on 2013-06-05
If the program created an icon, then most likely it also created a desktop file.
You can locate program desktop files in /usr/share/applications.
Like stated above, right click on the desktop file and look at the command listing.
That is what is called upon to execute the program, and is what you would type in the terminal.

---

