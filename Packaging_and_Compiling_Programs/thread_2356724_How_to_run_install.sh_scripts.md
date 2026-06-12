---
title: "How to run install.sh scripts"
date: 2017-03-26
forum: Packaging and Compiling Programs
---

### Post by mrtejaslol on 2017-03-26
):P):PYesterday I was trying to install Arduino 1.8.2. I had downloaded the package from [https://downloads.arduino.cc/arduino-1.8.2-linux64.tar.xz](https://downloads.arduino.cc/arduino-1.8.2-linux64.tar.xz)
I extracted the .tar.xz file and tried running ./install.sh but it keeps on opening in gedit For the solution of this problem I already referred [https://ubuntuforums.org/showthread.php?t=1762776](https://ubuntuforums.org/showthread.php?t=1762776) and [http://ubuntuhandbook.org/index.php/2015/11/install-arduino-ide-1-6-6-ubuntu/](http://ubuntuhandbook.org/index.php/2015/11/install-arduino-ide-1-6-6-ubuntu/). My laptop specs Lenovo G50-80 ci3 4th gen 4GB RAM Ubuntu 16.04. Please help me Thanks.

---

### Post by TheFu on 2017-03-26
Welcome to the forums.

Can't use a GUI to run scripts unless the permissions allow it.  There are a few different ways to make this work, but it depends on the file system being used whether the execute permission bit can be enabled for user, group or other permissions.

TL;DR - open a terminal. Try **bash /full/or/relative/path/to/install.sh**.  Of course, the /full/or/relative/path/to/install.sh is dependent on your system.  If you are in the same CWD as the script, use **bash ./install.sh**  That is a relative path.

A little beginning level unix knowledge will save you lots and lots of frustration. There is a free PDF book that provides the needed background: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)   Most beginning classes teach relative paths and permissions fairly early.  In my classes, we cover that stuff in chapter 2 since it is central to everything on Linux.  Permissions are the core of Unix security.

Of course, all of this assumes there aren't any issues with the downloaded package or script.  If the 1st line of the script doesn't similar to this:

#!/bin/sh

Then something isn't correct. Use the 'head' command to see the first few lines of the file.

---

