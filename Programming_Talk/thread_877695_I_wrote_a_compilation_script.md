---
title: "I wrote a compilation script"
date: 2008-08-02
forum: Programming Talk
---

### Post by collinp on 2008-08-02
I wrote a fairly simple compile script done in bash a while back, but i never posted it here. It can compile most of the common methods of compiling.

---

### Post by RuleMaker on 2008-08-02
Man, no hard feelings, but this script will only work if all dependencies and dev packages are available otherwise it'll fail.
If you could make somehow to automatically install all missing packages needed to build, this would be my favorite script.
Anyway, this could be useful to beginners.

---

### Post by bobbocanfly on 2008-08-02
> **RuleMaker said:**
> Man, no hard feelings, but this script will only work if all dependencies and dev packages are available otherwise it'll fail.
If you could make somehow to automatically install all missing packages needed to build, this would be my favorite script.
Anyway, this could be useful to beginners.

```
#!/bin/bash
echo "Welcome to Hellow's compile script. The script will ask you a few questions, then it will perform all the work. Please enter all answers in lower-case letters"
echo "Please enter if this directory contains install-sh"
read install-sh
clear
echo "Please enter if this directory contains install.sh"
read install.sh
clear
echo "Please enter if this directory contains a Makefile"
read Makefile
clear
echo "Please enter if this directory contains a configure script"
read configure

echo "Does this piece of software have an Ubuntu package in the repositories?"
read ubuntu-package
if [$ubuntu-package = Yes]
then
    echo "Please enter its name so we can automatically download dependencies"
    read pkg-name
    sudo apt-get build-dep $pkg-name
fi
clear

if [ $install-sh = Yes ]
             then ./install-sh
fi
if [ $install.sh = Yes ]
             then ./install.sh
fi
if [ $configure = yes ]
             then ./configure
fi
if [ $Makefile = yes ]
             then make && sudo make install
fi
echo "The compile script is now complete. Please attempt to execute the program to check the success of the compile. Also, if the compile is unsuccessful, please scroll up to see if there was errors."
```

If the software you are trying to install has an Ubuntu package we can auto-download its build dependencies. Havent tested that script but something like it should work.

---

### Post by collinp on 2008-08-02
> **bobbocanfly said:**
> ```
#!/bin/bash
echo "Welcome to Hellow's compile script. The script will ask you a few questions, then it will perform all the work. Please enter all answers in lower-case letters"
echo "Please enter if this directory contains install-sh"
read install-sh
clear
echo "Please enter if this directory contains install.sh"
read install.sh
clear
echo "Please enter if this directory contains a Makefile"
read Makefile
clear
echo "Please enter if this directory contains a configure script"
read configure

echo "Does this piece of software have an Ubuntu package in the repositories?"
read ubuntu-package
if [$ubuntu-package = Yes]
then
    echo "Please enter its name so we can automatically download dependencies"
    read pkg-name
    sudo apt-get build-dep $pkg-name
fi
clear

if [ $install-sh = Yes ]
             then ./install-sh
fi
if [ $install.sh = Yes ]
             then ./install.sh
fi
if [ $configure = yes ]
             then ./configure
fi
if [ $Makefile = yes ]
             then make && sudo make install
fi
echo "The compile script is now complete. Please attempt to execute the program to check the success of the compile. Also, if the compile is unsuccessful, please scroll up to see if there was errors."
```If the software you are trying to install has an Ubuntu package we can auto-download its build dependencies. Havent tested that script but something like it should work.

I should add this to my script, will update in a min.
EDIT: Script updated!

---

