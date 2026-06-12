---
title: "Simple bash script question"
date: 2009-03-27
forum: Programming Talk
---

### Post by 16777216 on 2009-03-27
I made a very simple script to get then compile and install the bespin Qt style from SVN and thought I should make it more portable so that other people could use it.

At first the script assumed that the **~/cloudcity/build** directory exists, which it does not on a fresh SVN checkout.

The problem is that I can't seem to get it to create the build directory on first run then **cd** into it for the rest of the script.

This is what I have so far.

```
#!/bin/bash

# This script will get, then build and install the Bespin style, window decoration, and xbar plasmoid for KDE.
# You should have all of the build dependencies installed already. Consult your distribution's documentation for instructions on how to do this.

svn co https://cloudcity.svn.sourceforge.net/svnroot/cloudcity

if [ -d ~/cloudcity/build ]; then
    cd ~/cloudcity/build
        while [ ! -d ~/cloudcity/build ]; dwhile [ ! -d ~/cloudcity/build ]; do
        # Sleep until build directory is created
        sleep 1
        done
else 
    mkdir ~/cloudcity/build
fi

cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
make
sudo make install
```

---

### Post by ghostdog74 on 2009-03-27
> **16777216 said:**
> 
if [ -d ~/cloudcity/build ]; then
    cd ~/cloudcity/build
        while [ ! -d ~/cloudcity/build ]; dwhile [ ! -d ~/cloudcity/build ]; do
        # Sleep until build directory is created
        sleep 1
        done
else 
    mkdir ~/cloudcity/build
fi


what is the while loop for?
```

if [ ! -d ~/cloudcity/build ] ;then
  mkdir ~/cloudcity/build
fi

```

---

### Post by 16777216 on 2009-03-27
Yeah, I was just coming back to say that I figured out that I was kind of going backwards with my **if**.

This is what I came up with.

```
#!/bin/bash

# This script will get, then build and install the Bespin style, window decoration, and xbar plasmoid for KDE.
# You should have all of the build dependencies installed already. Consult your distribution's documentation for instructions on how to do this.

svn co https://cloudcity.svn.sourceforge.net/svnroot/cloudcity

if [ ! -d ~/cloudcity/build ]; then
    mkdir ~/cloudcity/build
        while [ ! -d ~/cloudcity/build ]; dwhile [ ! -d ~/cloudcity/build ]; do
        # Sleep until build directory is created
        sleep 1
        done
    cd ~/cloudcity/build
else
    cd ~/cloudcity/build
fi

cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
make
sudo make install
```Is the **while** still useless? I will test on my own later to see for myself but I was wondering if it was good to keep for some reason or if their were any unnecessary bits or no-nos in it.

---

### Post by ghostdog74 on 2009-03-27
the while loop is not needed. mkdir will create the directory even before you go into the while loop. mkdir will give you error messages if it can't create directories, so all you need to do, if you want to check for errors, is to grab for the value of return, $?.

---

### Post by 16777216 on 2009-03-27
Thanks for your help.
I am still trying to learn scripting and will add layers of complexity on this until it does everything I want it to.

---

