---
title: "Help with compiling script?"
date: 2007-11-29
forum: Programming Talk
---

### Post by oiler920 on 2007-11-29
I'm trying to create my first bash script. It's supposed to be a bash script that compiles a package in Thunar, the XFCE file manager. I setup Thunar so there is a "Compile Package" link when you right-click on a .tar.gz file or a .tgz and it will call upon this script with the filename of the package. Problem is, it won't work.

Here's the terminal output:
```
nicholas@finalbuntu:~$ .scripts/compile.sh source/muine-0.8.8.tar.gz
got r00t?
muine-0.8.8.tar.gz
.scripts/compile.sh: line 15: unexpected EOF while looking for matching `"'
.scripts/compile.sh: line 18: syntax error: unexpected end of file
nicholas@finalbuntu:~$ 
```

Here's the script:

```
#!/bin/bash
#
# thunar-compile-package

BASENAME=`basename "$*"`
gksudo -k /bin/echo "got r00t?"
echo $BASENAME

if mkdir compileTR && cd compileTR && tar zvf $BASENAME && cd * && ./configure && make && make install && cd .. && cd .. && rmdir compileTR
then
        if zenity --question --title "Compile package $BASENAME" --text "$BASENAME successfully compiled.
        fi
        exit 0
else
        zenity --error --title "Compile package $BASENAME" --text "Unable to compile package!"
        exit 1
fi
```

Help? :confused:

---

### Post by kast on 2007-11-29
Can you do me a favour and step threw that script with me and tell me what your expecting it do t? just getting a little confused :)

---

### Post by kast on 2007-11-29
Sorry for the typo's!

---

### Post by oiler920 on 2007-11-29
OK, Thunar, my file manager, will launch the script like this: **.scripts/compile.sh muine-0.8.8.tar.gz** Then it'll run as root and ask the root password, create a directory, cd into it, untar the package, cd into the directory the package made, run the configure script, run make, and then run make install. Then it removes the directory it made. There, good enough?

---

### Post by kast on 2007-11-29
Ok so after it asked for the password, and then does your **echo** you go to do the **mkdir** etc.. why are you putting that in a IF statement? is there a circumstance that could be there that would make you not want to run that line of code?

---

### Post by kast on 2007-11-29
```
#!/bin/bash
#
# thunar-compile-package

BASENAME=`basename "$*"`
gksudo -k /bin/echo "got r00t?"
echo $BASENAME

mkdir compileTR && cd compileTR && tar zvf "$BASENAME" && cd * && ./configure && make && make install && cd .. && cd .. && rmdir compileTR

if zenity --question --title Compile package "$BASENAME" --text "$BASENAME" successfully compiled.
then; exit 0
else
      zenity --error --title Compile package "$BASENAME" --text "Unable to compile package!"
      exit 1
fi
```

---

### Post by geirha on 2007-11-30
I would do it in stages, and display the output along the way. Something like this perhaps:
```
#!/bin/bash

# The first entry in the tar should be the directory it creates
extract_path=$(tar tf "$1" | head -1)

[ -d compileTR ] || mkdir compileTR
if ! (tar xvf "$1" -C compileTR/ 2>&1; echo DONE)| 
     zenity --text-info --title="Unpacking"; then
    zenity --error --text="Error unpacking archive"
    exit 1
fi

if [ -d "compileTR/$extract_path" ]; then
    cd "compileTR/$extract_path"
else
    zenity --error --text="Archive not of expected format"
    exit 1
fi

if ! (./configure 2>&1 && make 2>&1; echo DONE) | 
     zenity --text-info --title="Building"; then
    zenity --error --text="Build failed"
    exit 1
fi

if ! (gksudo make install 2>&1; echo DONE) | 
     zenity --text-info --title="Installing"; then
    zenity --error --text="Install failed"
    exit 1
fi

cd ../.. 
zenity --question --text="Remove source tree?" && rm -rf compileTR
```

---

### Post by oiler920 on 2007-11-30
I really don't know why there is an IF statement. =P This is a modification of a Mount ISO script I found.

And thanks, geirtha, I'll try that. =)

---

### Post by kast on 2007-11-30
if (tar xvf "$1" -C compileTR/ 2>&1; echo DONE) = good

if mkdir compileTR && cd compileTR && tar zvf $BASENAME && cd * && ./configure && make && make install && cd .. && cd .. && rmdir compileTR =  ????????  

 :p really shouldn't be such a wise *** if you looking for, help have a nice life there oiler

---

