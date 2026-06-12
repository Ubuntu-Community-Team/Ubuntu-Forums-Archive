---
title: "compiling rhythmbox from source"
date: 2008-01-19
forum: Packaging and Compiling Programs
---

### Post by zo3adams on 2008-01-19
Greetings, I am very new to development on Linux though experienced in programming on windows. Using an updated 7.10 OS build with build-essential and autogen and checkinstall installed. I got the rhythmbox code from the svn trunk.



I want to experiment and learn and am trying to compile Rhythmbox but have a hit a roadblock and can't get complete the autogen.sh script. I don't find a post that describes my problem.

When I first ran rhythmbox I it gave an error that it could not find gtk-doc, then failed a few lines later not finding gtk-doc.m4

I downloaded the tar file for gtk-doc and still got the error till I modified autgen to include the directory where I had extracted,ui modified like this:
original:
> ACLOCAL_FLAGS="$ACLOCAL_FLAGS -I"
becomes:
> ACLOCAL_FLAGS="$ACLOCAL_FLAGS -I /home/'myName'/projects/gtk-doc-1.8 macros"

Now the script gives no error message, but it finishes with the last line:
> Checking for required M4 macros...
Checking for forbidden M4 macros...

i then try to run make, but 'no make file found' so autogen must not have completed successfully ? I don't  know what I'm doing when it comes to setting ACLOCAL_FLAG, so I figure that is what's wrong, any suggestions?

---

### Post by stroyan on 2008-01-20
There is a quick shortcut to getting the dependencies for building rhythmbox.
There is a rhythmbox package in the repository.
That package includes the build dependency information.
You can install all the necessary packages by running ```
sudo apt-get build-dep rhythmbox
```

---

