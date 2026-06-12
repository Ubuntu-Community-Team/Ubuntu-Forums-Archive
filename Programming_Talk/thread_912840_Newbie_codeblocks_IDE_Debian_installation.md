---
title: "Newbie code::blocks IDE Debian installation"
date: 2008-09-07
forum: Programming Talk
---

### Post by resander on 2008-09-07
I have only just installed latest Ubuntu and compiled&run 'Hello World' from the command line. I have never used Ubuntu, tar balls etc before, but have used the MSDOS command line with mkdirs etc in the remote past.

As an old Windowser used to installers putting exe files on the desktop or on startmenus, I don't yet know how to install the Debian packages of the code::blocks IDE and I don't know where to look for the unpacked results.

I downloaded codeblocks_8.02-0ubuntu1.deb.tar.gz from codeblocks website and unzipped into a temp folder. This contains 

codeblocks_8.02-0ubuntu1_i386.deb
codeblocks-contrib_8.02-0ubuntu1_i386.deb
codeblocks-dbg_8.02-0ubuntu1_i386.deb
codeblocks-dev_8.02-0ubuntu1_i386.deb
libcodeblocks0_8.02-0ubuntu1_i386.deb
libwxsmithlib0_8.02-0ubuntu1_i386.deb
libwxsmithlib0-dev_8.02-0ubuntu1_i386.deb

A package installer dialog pops up when I double click codeblocks_8.02-0ubuntu1_i386 (from the File browser) and this dialog displays error status 'Dependency is not satisfiable libcodeblocks0'. The dialog also contains a tab 'Included Files' showing the destination folders, but when I look in these there is nothing there.
All the debians showed error status (but not the same) and also showed content in the Included Files tab, but again there was nothing there. 

At this point what do I need to do?

I have used MS Visual C++ version 6 daily since it was released ten or more years ago, and the derivatives packaged into Visual C++ 2005/2008 Express, so I have got used to the convenience of an IDE. I would not want to go back to the command line and Make files again. I picked codeblocks because it ws reported to look somewhat similar to the MS IDE(s). I know there are other IDEs, e.g. the Anjuta that I would like to try too, but it seemed even more daunting to install for an Ubuntu newbie.

---

### Post by kjohansen on 2008-09-07
Two options: randomly click the debs until you do them in the right order to satisfy the dependencies or the GOOD way is to change to the directory where you have the debs and do 

```

sudo dpkg -i *.deb

```

---

### Post by resander on 2008-09-07
Many thanks.

using sudo dpkg -i *.deb did it!

It showed that one more package, libwxgtk2.8, was needed.
Requested that via Synaptic loader and then retried the
dpkg command. After that code::blocks installed ok and
even got its own menuitem on the applications menu.

Again, many thanks.

---

