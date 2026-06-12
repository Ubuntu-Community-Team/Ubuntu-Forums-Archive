---
title: "about c &amp; c++"
date: 2009-05-25
forum: Programming Talk
---

### Post by vardhan0789 on 2009-05-25
how to work on c & c++ in ubuntu???
how to change the present/current working directory in the terminal ?

---

### Post by vardhan0789 on 2009-05-25
how to work on c & c++ in ubuntu???
how to change the present/current working directory in the terminal ?

---

### Post by alphacrucis2 on 2009-05-25
> **vardhan0789 said:**
> how to work on c & c++ in ubuntu???
how to change the present/current working directory in the terminal ?

Install the gcc package.

Use the cd command to change directory e.g

cd /home

Preceed the directory with a / to change to an absolute location. If you don't have the leading / then it is relative to the current directory. Probably a good idea to look for a tutorial on basic Unix commands and file system.

---

### Post by niteshifter on 2009-05-25
Hi,

You'll need to install some packages. In the repositories is a package named "build-essential" - that will get you the compiler, linker, etc that you need. Either search for "build-essential" in Synaptic or
```
apt-get install build-essential
```

To change directory use the cd command:
When you first open terminal you are in your home directory (/home/your-user-name). To change to the Documents directory:
```
cd Documents
```

To go "up" one level:
```
cd ..
```

To make a new directory, let's call it testpgms:
```
mkdir testpgms
```

Both of these commands can use a full path. Let's pretend we've opened a terminal and have changed to the Documents directory. We wish to go to testpgms which happens to be in a directory named Projects in our home directory:
```
cd ~/Projects/testpgms
```
or this:
```
cd /home/your-user-name/Projects/testpgms
```
These two do the exact same thing, the ~ is shorthand for /home/your-user-name.

---

### Post by frodon on 2009-05-26
Moved to programming talk forum.

---

### Post by Zugzwang on 2009-05-26
Dear OP, read the stickies in this forum to get to know about "compiling your first C program"/"compiling your first C++ program".

For changing directories in the shell, use the "cd" command, e.g., "cd /tmp/". Search for a console tutorial using your favorite search machine for details.

---

### Post by simeon87 on 2009-05-26
> **vardhan0789 said:**
> how to work on c & c++ in ubuntu???

First, you need to write some code in C or C++. This can be done in a text editor, like gedit, or in an IDE (I'm sure someone can suggest a few).

Then you need to compile it with gcc or g++ (for C and C++ respectively). This can be done by typing in the terminal (an IDE has a menu option for this):

```
gcc -o file file.c
```

Then you can run it with:

```
./file
```

> **vardhan0789 said:**
> how to change the present/current working directory in the terminal ?

You can use the command cd for that. For example, when you're in the home directory, you can type cd Pictures to go to the Pictures directory.

---

### Post by monkeyking on 2009-05-26
also pwd, will print the working directory

---

### Post by ibuclaw on 2009-05-26
And threads merged.

vardhan0789, as a verbal warning, please don't post duplicate threads in these forums.

Regards
Iain

---

