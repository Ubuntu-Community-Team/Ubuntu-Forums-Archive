---
title: "Transferring from Windows to Linux as a programmer"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by matanc1 on 2012-11-26
So I've recently made my move to Ubuntu from windows. 
Up until now everything is going quite well, but I still feel as if I don't really know the OS well enough to feel completely comfortable with it. For instance, I don't know what some of the linux commands such as sudo, apt, etc do (not in depth atleast) and how to use them without using a guide. 
I'm a computer science college student, so I've done some c,c++ programming, and have done some Bash as well (meaning that I know how to write a proper script). 
So can you guys recommend anything for me so that I'll get to know the system better and know how to fully use it? 
Reading material, websites, or anything that comes to mind will be great.
Thank! :)

---

### Post by audiomick on 2012-11-26
You named a few commands and said that you didn't know what they mean. On a linux system, a command should always come with a man page. That is man as in manual. You can look at them via the terminal.

The usage is
```
man <command>
```

so
```
man man
```

will get you one about the man function itself,

```
man sudo
```

will tell you about the sudo function, and

```
man apt
```

will tell you what apt is.

While you are at it, look at 
```
man apt-get
```
to find out how to install via apt.

As a comp science student, you should fairly quickly learn how to decipher the man pages. They are a bit confusing at first, but you soon find your way around.

---

### Post by squakie on 2012-11-26
You may also want to look at:

[http://www.linux-books.us/linux_general_0003.php](http://www.linux-books.us/linux_general_0003.php) for generic linux information

[http://www.makeuseof.com/tag/download-ubuntu-absolute-beginners-guide/](http://www.makeuseof.com/tag/download-ubuntu-absolute-beginners-guide/)  for ubuntu specific things, but not sure how current it is

---

### Post by HeroOfCanton on 2012-11-26
As mentioned, man pages are a great resource. Nothing like having the guide built into the OS. :)

Getting comfortable will take time. But the best way to learn is to do! A great start would be to make sure your linux setup looks like no other. I'm using Xubuntu (different desktop) with the Ubuntu login manager (because it looks nicer on startup), with PC stats running across various areas of the desktop (check out [Conky]("http://conky.sourceforge.net/")) nicely blended into a custom desktop image (created in GIMP), with tool bars (hidden and visible) to organize things to personal tastes, etc.

Personalizing things will force you out of the "casual user" realm a bit and help you get familiar with the command line and editing config files. Not sure if you do any web programming, but setting up a localhost LAMP server is another great way to get familiar with commands and file permissions.

Welcome to Ubuntu!

---

### Post by matanc1 on 2012-11-27
Did any of you do any sort of project to get yourself more familiar?
Maybe I need one of those. You , mentioned  customization, any advise on where to start?

---

### Post by squakie on 2012-11-27
Do you want to do a true programming project, and if so, in what language?

---

### Post by gnusci on 2012-11-27
Here a list of apps you may need to install:

#Install utils:
sudo apt-get -y install subversion
sudo apt-get -y install cvs git-core mercurial
sudo apt-get -y install vim

#Install C and C++ Compilers in Ubuntu
sudo apt-get -y install build-essential
sudo apt-get -y install build-essential checkinstall

#Fortran
sudo apt-get -y install gfortran

#Autotools:
sudo apt-get -y install autoconf automake autotools-dev m4

#X11:
sudo apt-get -y install libx11-dev libxrandr-dev

#OpenGL:
sudo apt-get -y install freeglut3-dev

#Image libraries
sudo apt-get -y install libjpeg-dev libpng-dev libz-dev

---

### Post by mastablasta on 2012-11-27
> **matanc1 said:**
> Did any of you do any sort of project to get yourself more familiar?

 
i read the free linux e-book linuxcommand.org to leanr a bit about command line and there are also nice examples in th ebook. i also read ubuntu manual to get myself familiar with the OS.
 
next i did a few projects on LAMP using the opensource tools avaiable. but since i had to tweka everytool i needed to dive into the code. and i plan two more projects like that. still a noob with the system though.
 
another good book is Dive into python.

---

### Post by Cheesemill on 2012-11-27
There's a great page on the Ubuntu wiki about learning the command line:

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by coldraven on 2012-11-27
I'm still a bit nooby and sometimes stuck for a command but I can do
```
man -k your_query
``` which should list all the man pages that contain your_query
Also ```
apropos your_query
``` will just list all the commands
For example:
```
apropos copy
``` gives these results
```
bcopy (3)            - copy byte sequence
copysign (3)         - copy sign of a number
copysignf (3)        - copy sign of a number
copysignl (3)        - copy sign of a number
cp (1)               - copy files and directories
cpgr (8)             - copy with locking the given file to the password or group file
cpio (1)             - copy files to and from archives
cppw (8)             - copy with locking the given file to the password or group file
dd (1)               - convert and copy a file
debconf-copydb (1)   - copy a debconf database
File::Copy::Recursive (3pm) - Perl extension for recursively copying files and directories
getutmp (3)          - copy utmp structure to utmpx, and vice versa
getutmpx (3)         - copy utmp structure to utmpx, and vice versa
install (1)          - copy files and set attributes
mcopy (1)            - copy MSDOS files to/from Unix
memccpy (3)          - copy memory area
memcpy (3)           - copy memory area
memmove (3)          - copy memory area
mempcpy (3)          - copy memory area
ntfscp (8)           - copy file to an NTFS volume.
objcopy (1)          - copy and translate object files
rcp (1)              - secure copy (remote file copy program)
rsync (1)            - a fast, versatile, remote (and local) file-copying tool
scp (1)              - secure copy (remote file copy program)
ssh-copy-id (1)      - install your public key in a remote machine's authorized_keys
stpcpy (3)           - copy a string returning a pointer to its end
stpncpy (3)          - copy a fixed-size string, returning a pointer to its end
strcpy (3)           - copy a string
strncpy (3)          - copy a string
tiffcp (1)           - copy (and possibly convert) a TIFF file
tiffcrop (1)         - select, copy, crop, convert, extract, and/or process one or more TIFF files.
va_copy (3)          - variable argument lists
wcpcpy (3)           - copy a wide-character string, returning a pointer to its end
wcpncpy (3)          - copy a fixed-size string of wide characters, returning a pointer to its end
wcscpy (3)           - copy a wide-character string
wcsncpy (3)          - copy a fixed-size string of wide characters
wmemcpy (3)          - copy an array of wide-characters
wmemmove (3)         - copy an array of wide-characters
wmempcpy (3)         - copy memory area

```

This is a good thing to know!
[http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/](http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/)

---

### Post by audiomick on 2012-11-27
> **matanc1 said:**
> Did any of you do any sort of project to get yourself more familiar?

The main thing for me was to simply start using Linux as a matter of course. I used to have a SuSe install, then found Ubuntu around 7.10 or so. I had a dual-boot on the old desktop, and still do on the Laptop as I need windows for a couple of work-specific programs like my audio analyzer. Anyway, the breakthrough was to stop trying to learn Linux whilst using windows to do "real" work, and start using Linux as a matter of course and only go back to windows when I was stuck on something that had to urgently get finished yesterday. Now, I never start windows on the laptop or the netbook unless it is for one of those specifically work related programs. I always fell sorry for my laptop when I am at work... ;) My desktop has no windows install.

---

### Post by matanc1 on 2012-11-27
Thanks for all the responses guys :)
So since I'm a CS student and I have so C++ projects this semster, is there anything that you'd recommend to learn about Ubuntu/Linux regarding coding? I've been told to give Vim a try, which I intend to do this weekend. Anything else?

---

### Post by Promille on 2012-11-27
> **matanc1 said:**
> Thanks for all the responses guys :)
So since I'm a CS student and I have so C++ projects this semster, is there anything that you'd recommend to learn about Ubuntu/Linux regarding coding? I've been told to give Vim a try, which I intend to do this weekend. Anything else?

Use a IDE that you're comfortable with. Since I'm at an introduction course to programming(Java) I want as little help as possible, so I try to learn "the hard way". Therefore gedit seems to work fine with me, or just simply nano if I have to ssh into the university's network. I also liked Geany([http://www.geany.org/](http://www.geany.org/)) alot, since you can compile and run the program inside Geany. On the other hand I have learned that more experienced programmers tend you use more "intellectual" IDE's, in example Eclipse. 

If I should give you some easy guidelines it would be 
[LIST]
[*]Learn by *doing*
[*]Use the man pages for information about programs.
[*]Use this forum or #ubuntu(or programming specific channels) on irc.freenode.org for questions. Be humble and polite and you would be amazed how willing people are to help you. Good luck :)
[/LIST]

---

### Post by squakie on 2012-11-27
or codeblocks.  cross platform and be used for several programming languages.  Depending on what your classes are using you may find it impossible to do the work - in example:  if the class is using Microsoft development tools then such things as developing a gui would be very different.

---

