---
title: "How to install programs in tar.gz format"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by adithya2 on 2013-10-05
I am new to Ubuntu and I have downloaded a package in tar.gz format.I use archive manager to open the contents of the package,but I don't know how to install them.
Any help in this regard would very great.
Cheers and Thanks in advance.

---

### Post by SeijiSensei on 2013-10-05
Simple answer is don't.

Nearly any program you can imagine probably already exists in the Ubuntu repositories.  Either search for it by name using the package manager on your system, or from the command line with "apt-cache search name" where name can be something like "firefox".  Programs in the repositories have been reviewed by Debian or Ubuntu staff and known to work with Ubuntu.  They are also reviewed for possible security flaws.  While installing random binaries is common in the Windows world, it's not the preferred approach when it comes to Linux software.  Use a package manager.

---

### Post by The Cog on 2013-10-05
A tar.gz is just like a zip file. It could contain anything. With any luck, there is a readme file inside, telling you what to do.

It might contain source code that needs compiling, or it might contain pre-compiled executables, or scripts, or anything really. To help, we need to know more.

And SeijiSensei is right - almost all software is already in the repositories, and they should always be the first place to look for software.

---

### Post by adithya2 on 2013-10-06
The file name is :Multiple_Wine_241108.tar.gz
It is used to install different versions of wine.

---

### Post by claracc on 2013-10-06
You need to use the tar command in a terminal.

See this link: [http://www.pendrivelinux.com/how-to-open-a-tar-file-in-unix-or-linux/](http://www.pendrivelinux.com/how-to-open-a-tar-file-in-unix-or-linux/) about how to use tar comand.

 I have found this thread, [http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269) , I suppose you have downloaded the compressed file from there and I suppose you are going to follow the instructions there given in order to install the .deb package and you only need to uncompress it?

---

### Post by Rob Sayer on 2013-10-06
> **SeijiSensei said:**
> Simple answer is don't.

Nearly any program you can imagine probably already exists in the Ubuntu repositories.  Either search for it by name using the package manager on your system, or from the command line with "apt-cache search name" where name can be something like "firefox".  Programs in the repositories have been reviewed by Debian or Ubuntu staff and known to work with Ubuntu.  They are also reviewed for possible security flaws.  While installing random binaries is common in the Windows world, it's not the preferred approach when it comes to Linux software.  Use a package manager.

I have to agree with this unless you *seriously* know what you're doing.  Having beta tested repos is one of the big reasons linux is as secure as it is.

Especially, the version of wine you install should be the one tested for your ubuntu version in the repos.  People have enough problems with Wine ... which has tons of bugs/problems ... without dicking around with iffy sources of the program.

Actually I'd prefer to use a VM like virtualbox rather than wine.  From the repos.

---

### Post by heir4c on 2013-10-06
> **adithya2 said:**
> The file name is :Multiple_Wine_241108.tar.gz
It is used to install different versions of wine.

Why you will install a very old tar.gz? (2008)
Where you download it and how you come to that packages? 
I look it up on Google and I find just 1 link to this forum, to a old tread of 2008.

You have wine in the repo's and also the .deb files of the new beta 1.5
You must Add a ppa and than update and install the package:
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

