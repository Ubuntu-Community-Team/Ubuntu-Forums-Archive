---
title: "how to install from .tar.gz"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-07-06
help!!!
i have no clue what to do

EDIT:
(im trying to install openlaszlo)

---

### Post by quantumstitch on 2008-07-06
Usually you are trying to install something from source code if you are using .tar.gz. What program are you trying to install? It might be available in the repo.

Just, saw your edit...

You have to extract the files from the compressed archive.

```

gunzip filename.tar.gz
tar -xvf filename.tar

```

Then look for the README or INSTALL text file. Read the instructions. It usually involves running make and make install.

---

### Post by pikabuntu on 2008-07-06
> **quantumstitch said:**
> Usually you are trying to install something from source code if you are using .tar.gz. What program are you trying to install? It might be available in the repo.

I'm trying to install openlaszlo

---

### Post by tjwoosta on 2008-07-06
tar.gz is a compressed file   (kind of like a .zip or a .rar)

to extract do 
```
tar -xzvf filename.tar.gz
```
where filename.tar.gz is your .tar.gz that you just downloaded

this .tar.gz that you downloaded im guessing contains the source so you will probably have to compile it

after extracting the .tar.gz  there should be a readme file somewhere inside (read that to learn how to install and what dependencies you will need)

most likely you will need to do theese commands one at a time and in this order (from inside the extracted directory)

./configure
make
make install

---

### Post by pikabuntu on 2008-07-06
Here is the readme (i cannot figure out how to install it even with this):

LPS 4.1.0 README
[http://wiki.openlaszlo.org/SubversionBuildInstructions](http://wiki.openlaszlo.org/SubversionBuildInstructions)
Here's what you'll find:

    LICENSE.txt           - The End User License Agreement for the LPS.
    README.txt            - This file.
    3rdPartyCredits       - Acknowledgements for 3rd party contributions to the LPS
    Server                - Jakarta Tomcat Servlet container configured.
                            with LPS 4.1.0 web app.
    release-notes.html    - Release notes.
    changelog.html        - Change log.

Depending on your platform, you may find useful links and scripts 
in this directory as well.

For detailed installation instructions, please see 
[http://wiki.openlaszlo.org/SubversionBuildInstructions](http://wiki.openlaszlo.org/SubversionBuildInstructions)

The developer edition requires JDK 1.4 or later.  Please download
a copy from [http://java.sun.com](http://java.sun.com) and set your JAVA_HOME environment variable.

--

* T_LZ_COPYRIGHT_BEGIN ******************************************************
* Copyright 2001-2008 Laszlo Systems, Inc.  All Rights Reserved.            *
* Use is subject to license terms.                                          *
* T_LZ_COPYRIGHT_END ********************************************************

---

### Post by pikabuntu on 2008-07-06
Also, i have no clue as to how to compile anything...

---

### Post by Sef on 2008-07-06
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by pikabuntu on 2008-07-06
i got so lost in that how to

---

### Post by tjwoosta on 2008-07-06
did you try what i said you probably had to do in my first post?
(this is how to compile)
..well most of the time anyway


first off to compile source you will always need build-essential
```
sudo apt-get install build-essential
```

untar the file
```
tar -xzvf filename.tar.gz
``` (filename.tar.gz is your .tar.gz file)

then navigate to the directory you just extracted (the rest of the commands must be executed from within this directory)
```
cd filename
``` (filename is whatever file you extracted)

then 
```
make
``` (if you get errors here you probably are missing some dependencies)

then 
```
sudo make install
```

then reboot

---

### Post by Bentai on 2008-07-06
I suggest we keep any further install support of OpenLaszlo to Pikabuntu's original thread here: [http://ubuntuforums.org/showthread.php?t=851595](http://ubuntuforums.org/showthread.php?t=851595)

---

