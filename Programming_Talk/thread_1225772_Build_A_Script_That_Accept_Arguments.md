---
title: "Build A Script That Accept Arguments"
date: 2009-07-28
forum: Programming Talk
---

### Post by nathanpc on 2009-07-28
Hello,
 I want to build a script file(**.sh*) to use with the *CeGCC* compiler, because to call the compiler i need to use this command:
```
**$** arm-wince-mingw32ce-g++ -o hello.exe hello.cpp
```
Like in *g++*, but it's a so much long command for a thing that i use all times, then i want to build this script to run it like this, remember that the filename will be *wince-g++*:
```
wince-g++ -o hello.exe hello.cpp
```
This is what i want a script that put all this arguments and execute the *CeGCC*, remember that i want to use shell script.

Thanks,
 Nathan Paulino Campos

---

### Post by JordyD on 2009-07-28
Why not use tab-completion?

```
arm<tab>
-->
arm-wince-mingw32ce-g++
```

or you can create a file with a shorter name that links to it.

```
sudo ln -s /usr/bin/arm-wince-mingw32ce-g++ /usr/local/bin/wince-g++
```

**EDIT:** Even better, create an alias:
```
alias arm-wince-mingw32ce-g++ wince-g++
```
Add it to your .bash_rc or .bash_profile (I'm not at an Ubuntu machine right now, not sure which one it is)

---

### Post by nathanpc on 2009-07-29
Hello JordyD,
Thanks very much, i have created an alias, it's much better, but the name of the file in Ubuntu is *.bashrc* ok.

Thanks,
 Nathan Paulino Campos

---

### Post by JordyD on 2009-07-29
Ah, so *both* of them were wrong.:P

You're welcome

---

### Post by dwhitney67 on 2009-07-29
> **nathanpc said:**
> Hello JordyD,
Thanks very much, i have created an alias, it's much better, but the name of the file in Ubuntu is *.bashrc* ok.

Thanks,
 Nathan Paulino Campos

Just so you know, here's a simple script that would have accepted a command line arg:
```

#!/bin/sh

# Deduce the filename and the extension of the command line argument (arg $1)
#
filename=`echo $1 | cut -d '.' -f1`
ext=`echo $1 | cut -d '.' -f2`


# Determine the compiler to use
#
if [ "$ext" == "cpp" ]
then
        CC="arm-wince-mingw32ce-g++"
elif [ "$ext" == "c" ]
then
        CC="arm-wince-mingw32ce-gcc"
else
        echo "Error: Unknown file type given."
        exit 1
fi


# Build the application
#
$CC $1 -o $filename.exe

if [ $? -eq 0 ]
then
        echo "Success!"
else
        echo "Failure!"
fi

```

Usage would be something like:
```

wince-g++ hello.cpp

```
The result, if the compilation and build is successful would be a hello.exe file.

What you really should do though, in lieu of creating scripts and/or aliases, is to create a Makefile.

---

