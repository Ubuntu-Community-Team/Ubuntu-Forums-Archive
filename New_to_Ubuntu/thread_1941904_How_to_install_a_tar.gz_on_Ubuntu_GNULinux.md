---
title: "How to install a tar.gz on Ubuntu GNU/Linux"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by lxde7 on 2012-03-16
Can anyone help me  :( install a tar.gz file on to Ubuntu.

---

### Post by dolphin194 on 2012-03-16
Can you please tell us what exactly you are trying to install?

---

### Post by Frogs Hair on 2012-03-16
Hello and Welcome

Describe the file or application . If it is an application make sure is compatible with your version of Ubuntu. Check the software center to see if the application is available and install it from there. What you do with the file depends on what it is . If there is read me file see that first . You can find out by right clicking the package and selecting extract here and checking the folder .

---

### Post by codemaniac on 2012-03-16
[http://www.cyberciti.biz/faq/install-tarballs/]("http://www.cyberciti.biz/faq/install-tarballs/")

---

### Post by baytes on 2012-03-16
It shouldn't matter what application your installing, the standard way to install a *.tag.gz file on a linux distro is to open a terminal window navigate to the dir where the file is located and run these following commands (without the quotes) "gunzip fileName.tar.gz" then run "tar -xvf fileName.tar" then change directories into the new folder the tar command created after unzipping I.E. "cd fileName-0.08" then once inside that directory run the following commands to build and complie the program "./configure" then "make" then "sudo make install" then once it completes your program will be installed and you can launch it from either the terminal by typing its name or through the "start" menu. 

If you have any questions or trouble with this please feel free to reply and ill help you through it

-Brad

---

### Post by jerome1232 on 2012-03-16
Actually, it does matter, since a tarball is simply a compressed archive of files he could have source code in there, or precompiled binaries, or a simply python script.

How you would run or install each will vary depending on what is actually in the tarball, the assumption that it's source code isn't always true.

---

### Post by codemaniac on 2012-03-16
> **jerome1232 said:**
> Actually, it does matter, since a tarball is simply a compressed archive of files he could have source code in there, or precompiled binaries, or a simply python script.

How you would run or install each will vary depending on what is actually in the tarball, the assumption that it's source code isn't always true.

Exactly .That is why A README (in BOLD) is always bundled with tarballs in order to guide people to the right installation .

---

### Post by jerome1232 on 2012-03-16
> **codemaniac said:**
> Exactly .That is why A README (in BOLD) is always bundled with tarballs in order to guide people to the right installation .

eh, usually, if it's source code. But not always. Binaries in particular don't always have documentation outside of what's on the website. In order to actually help the OP we need to know what it is the OP is trying to install, it might be in the repositories and the OP simply doesn't know that you usually use the package manager to install software.

---

