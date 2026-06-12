---
title: "Can't find package"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by rocknzen on 2008-08-11
I downloaded this package ActivePython-2.5.2.2-linux-x86.tar.gz and put it in my Home folder. When I try to install this what I get.

This is what I enter into terminal:```


sudo apt-get install ActivePython-2.5.2.2-linux-x86.tar.gz

```And this is output: 

```
E: Couldn't find package ActivePython-2.5.2.2-linux-x86.tar.gz
```What does the E: represent or mean?

---

### Post by tuxxy on 2008-08-11
tAR.GZ is similar to .ZIP in windows, you need to extract the contents first, right click on the icon and select extract here.  Now you will need to run the install file, apt-get will only install apps that are supported in the repos.

You do know that python will be available in the repos, open synaptic and search for python

---

### Post by atoponce on 2008-08-11
```
tar -xf ActivePython-2.5.2.2-liunx-x86-tar.gz
cd ActivePython-2.5.2.2-linux-x86
sh install.sh
```

Done!

---

### Post by rocknzen on 2008-08-11
atoponce this is the output I got when I tried what you suggested

> tar: ActivePython-2.5.2.2-liunx-x86-tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

---

### Post by iaculallad on 2008-08-11
On your terminal, change directory to your home directory:

```
cd ~
```

and the rest, you do what atoponce instructed.

NOTE: Be sure that the archive file is SAVED/COPIED in your home directory.

---

### Post by rocknzen on 2008-08-11
I am at my home directory

---

### Post by mcduck on 2008-08-11
> **rocknzen said:**
> atoponce this is the output I got when I tried what you suggested

There's a typo in that command. 

tar: ActivePython-2.5.2.2-**liunx**-x86-tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

The best way to handle long file names is to type couple of first letters and then just hit the tab key to let autocompletion fill the rest for you. This way it's pretty impossible to misspell file names. Autocompletion also works for commands. And if what you have typed is not enough for the autocompletion to know what you are trying to type you can either hit the tab again to get a list of all possibilitties, or type a copule of letters more and try again.

---

### Post by alienexplorers on 2008-08-11
ActivePython-2.5.2.2-linux-x86.tar.gz is not listed in the repositories so apt-get will not load that program.

---

### Post by srid on 2010-04-12
See installation instructions for ActivePython in Ubuntu in this post: [http://ubuntuforums.org/showthread.php?p=9113066#post9113066](http://ubuntuforums.org/showthread.php?p=9113066#post9113066)

---

