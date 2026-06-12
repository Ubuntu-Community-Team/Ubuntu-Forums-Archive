---
title: "How do you install programs from tar.gz?"
date: 2017-04-08
forum: New to Ubuntu
---

### Post by chris-burmajster on 2017-04-08
Hi,

How do you install programs from tar.gz? I'm at a loss!

Can somebody help me?

Chris Burmajster

---

### Post by howefield on 2017-04-08
What is it that you are trying to install, or even the filename ?

Generally you would firstly untar the compressed file and follow the instructions in the README file, should there be one.

---

### Post by Impavidus on 2017-04-08
A .tar.gz is a compressed archive, just a bunch of files. Unpack it. You can do so using the file manager, but if you prefer another way, do whatever you like. Then see what's inside. With a bit of luck there's a file named readme or install. There are no rules for installation of these tarballs, you have to install them in the way the maker of the tarball thought best.

---

### Post by kingneutron on 2017-04-08
( as your non-root id )
$ sudo su -
# cd /usr/local/src
# tar xzvf /path/to/your/tar.gz
# ls -l

--Then 'cd' to the program's extracted directory and look for a README.  Usually it's just ' make && make install ' but will be specific to the software. You may need to install some dependencies like " build-essential " first, check the software's webpage for more details.

---

### Post by oldrocker99 on 2017-04-08
Most .tar.gz files have a **configure** script```
./configure
``` which sees what kind of compiler you have, which libraries, etc. It may end with a "generating makefile," after which you type```
make && sudo make install
``` It may also end with a "missing dependencies" error, in which case you have to install some libraries. Please post results of ```
make
```

You can also extract .tar.gz files with a file manager.

---

### Post by sevendogs on 2017-04-09
The first questions I have to ask is why - is the application you are attempting to install not in the Ubuntu repositories?

---

### Post by chris-burmajster on 2017-04-09
Thank you for all the instructions. I'll have to read them my Ubuntu machine!

---

### Post by Paddy Landau on 2017-04-10
I shall expand on the reply by sevendogs.

Often newcomers to Ubuntu come from a Windows background, where they are used to searching for programs on the Internet, downloading them, and installing them.

Debian systems (which Ubuntu is) have a very different approach. Applications are stored on *repositories*, so to install a program, you just use the installed package manager.

Open the Ubuntu Software Manager, search for the application that you require, and press the Install button. To uninstall an application, go through the same process but press the Remove button.

This method has several advantages:

[LIST]
[*]You get applications from reliable sources, usually checked for compatibility with Ubuntu, and sometimes tailored for Ubuntu
[*]The system manages installation and removal
[*] The system *automatically* installs updates when it does the regular updates
[*]The system automatically handles missing dependencies
[/LIST]
So, please first try to find the application that you want in the Ubuntu Software Manager. If you can't find it there, ask on the forums; often people know the package and can give you an idea.

Failing that, the package may be available as a "deb" package (which is how they are stored on the repositories). You still use the package manager to install a deb package.

Unless you are doing some fancy advanced stuff, you should *never* have to download tar files and install them!

---

### Post by oldrocker99 on 2017-04-10
Here's five free Ubuntu books, including the official Ubuntu book:[https://itsfoss.com/5-free-ubuntu-books-for-beginners/](https://itsfoss.com/5-free-ubuntu-books-for-beginners/).

---

### Post by leunam12 on 2017-04-11
The first thing that you have to do before attempting to install something from source is to download clonezilla, burn it to a USB stick, boot from that USB stick and make a backup of your hard drive. Attempting to install something from source can easily break your system if you don't know what you are doing and you are taking information from here and there.

---

