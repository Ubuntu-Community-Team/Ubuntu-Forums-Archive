---
title: "installing Qt; says it can't find compiler"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by mzimmers on 2012-03-20
I'm installing the Qt SDK onto 11.10. Early in the installation, I get a warning that I don't have a compiler. I've already installed GCC, but I notice it's not in my $PATH variable.

I also notice that there's no mention of $PATH in my .bashrc file, and I don't have a .bash_profile file like I do on the Mac.

So, two questions: is the lack of the path to GCC the likely culprit of this warning, and...where does one set environment variables in ubuntu?

Thanks.

---

### Post by lisati on 2012-03-20
You might want to install build-essential and then see if doing so makes a difference.

---

### Post by mzimmers on 2012-03-20
It sure did...thank you. What specifically did build-essential provide over the USC install that I did the first time?

---

### Post by Paqman on 2012-03-20
> **mzimmers said:**
> It sure did...thank you. What specifically did build-essential provide over the USC install that I did the first time?

It contains all the tools you need to compile from source. The full list of packages is at:
[http://packages.ubuntu.com/oneiric/build-essential](http://packages.ubuntu.com/oneiric/build-essential)

---

### Post by mzimmers on 2012-03-20
Interesting...thanks for the information.

---

### Post by ksa618 on 2012-03-21
I think the lack of g++ was your problem, as gcc is the c compiler, and Qt uses C++.

---

### Post by mzimmers on 2012-03-21
I thought gcc was everything...the Gnu Compiler Collection?

---

### Post by ksa618 on 2012-03-21
Yes, that is correct. GCC is the GNU Compiler Collection. However the 'gcc' command is the C frontend for the GNU Compiler Collection and the 'g++' command is the C++ frontend. It's a bit confusing, yes, but if I'm not mistaken, GCC originally stood for GNU C Compiler, but the meaning was changed because it supported more languages.

You can use g++ to compile C-files, but you can't compile C++ files with the gcc command.

---

