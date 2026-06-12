---
title: "PCRE installation issues"
date: 2014-09-23
forum: New to Ubuntu
---

### Post by Mike_Roslansky on 2014-09-23
Hello Friends,
I'm currently trying to install all the requirements needed to install Apache. However, I've become stuck on installing PCRE. [These instructions]("http://www.linuxfromscratch.org/blfs/view/svn/general/pcre.html") are pretty well written and let me understand what I'm doing when executing each command. My machine doesn't recieve an error until this line: 
```
--enable-pcregrep-libbz2          \
```
I recieve this error message:
```
** Cannot --enable-pcregrep-libbz2 because bzlib.h was not found
```
Why am I missing this file? What does this file do? All information that I can learn from is welcome. My issue is the same as [this guy]("http://stackoverflow.com/questions/13969513/cannot-enable-pcregrep-libbz2-because-bzlib-h-was-not-found") (except different distributions), but when I try to run yum commands, it tells me I need to enable repositories. What repositories do I need to enable? Why do I need to enable them? Again, all information is welcome!
Thank you for your time.

---

### Post by skompier on 2014-09-23
YUM isn't used by Ubuntu. Ubuntu uses APT. bzlib.h is part of bzip2 which should already be installed. Try installing it again and see what happens.

```
sudo apt-get install bzip2
```

---

### Post by Lars Noodén on 2014-09-24
bzlib.h should be in the package libbz2-dev:

[http://packages.ubuntu.com/trusty/libbz2-dev](http://packages.ubuntu.com/trusty/libbz2-dev)

You can search [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for filenames and it will tell you which package contains files with that name.  

It's in the repository.

Ubuntu is mostly a user-oriented system so development packages usually have to be added as needed if you are doing development or development-like activities.

---

### Post by Mike_Roslansky on 2014-09-26
I downloaded the package libbz2-dev, how do I go about installing it. I haven't found instructions. Thank you for your help!

---

### Post by Mike_Roslansky on 2014-09-26
That command seemed to work, but when I ran the configure command to install pcre, I recieved the same issue.

---

### Post by Lars Noodén on 2014-09-26
It should have been as simple as going into Synaptic and clicking on it.  If you would like to do it via the shell, then apt will do it:

```

sudo apt-get install libbz2-dev 

```

That should get the package  libbz2-dev  for you.

---

### Post by Mike_Roslansky on 2014-09-28
```
 ** Cannot --enable-pcretest-readline because readline/readline.h was not found. 
```
Getting this now.

---

### Post by Lars Noodén on 2014-09-28
There are two packages with a file with that name:

[http://packages.ubuntu.com/search?searchon=contents&keywords=readline%2Freadline.h&mode=exactfilename&suite=trusty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=readline%2Freadline.h&mode=exactfilename&suite=trusty&arch=any)

You can try one and, if it doesn't work, then the other.  

The search function on the lower half of the packages database can hunt for file names.  So when it complains about a missing file, and locate and find show it to be missing from your system.  Turn there to see which package it might be in.

---

