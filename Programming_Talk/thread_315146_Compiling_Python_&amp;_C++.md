---
title: "Compiling Python &amp; C++"
date: 2006-12-08
forum: Programming Talk
---

### Post by Wybiral on 2006-12-08
Hello. I've been using embedded python in c++ for quite a while now (despite the slight lack of documentation) and I have developed some pretty nice stuff with it. I've been using the standard "Python.h" method (not using boost or anything) but I've ran into a problem...

What would be the proper PORTABLE way to include and compile my python program? Up until now I have been including it with...
"#include <python2.5/Python.h>"

And compiling with...
"g++ -lpython2.5 program.cpp"

But obviously this is grossly inefficient when it comes to sharing and porting these programs (unless everyone had the same version of python). If anyone knows a better, more portable method, I would love to see it. Thanks!

---

### Post by maddog39 on 2006-12-08
Maybe have a shell script on compilation that detects the python version and then creates the proper compilation command. But then again, this would only work for people who are compiling for source. :/

---

### Post by Wybiral on 2006-12-08
Yeah, it would also have to change the "#include" line in my cpp source which probably wouldn't be the safest way to go about things. Thanks for the response though.

---

### Post by Wybiral on 2006-12-11
No... You were right, I can use a shell script. I don't know what I was thinking, I just changed "#include <python2.5/Python.h>" to "#include <Python.h>" and added the python directory to the include path when I compile it. It still doesn't auto detect the python version or anything, but it is very easy to change (just change the pyVersion variable). Now, if someone had a way to detect the python version and return it as "pythonx.x" then this compile script would work like a charm.

```

# Shell file to compile

# Python Version to compile with
pyVersion="python2.5"

# Path of Python.h
iPath="-I/usr/include/$pyVersion"

# Create objects
g++ -c Main.cpp -o Main.o $iPath
g++ -c pyWrapper/pyWrapper.cpp -o pyWrapper/pyWrapper.o $iPath

# Compile Main program
g++ Main.o pyWrapper/pyWrapper.o -l$pyVersion

```

---

### Post by po0f on 2006-12-11
Wybiral,

```
[FONT="Courier New"]#!/bin/bash
CXXFLAGS=''

if [[ -f /usr/include/python2.5/Python.h ]] ; then
	echo -e "found /usr/include/python2.5"
	CXXFLAGS+=-lpython2.5
elif [[ -f /usr/include/python2.4/Python.h ]] ; then
	echo -e "found /usr/include/python2.4"
	CXXFLAGS+=-lpython2.4
else
	echo -e "could not find /usr/include/python"
fi

echo -e "${CXXFLAGS}"

exit 0
[/FONT]
```

---

### Post by Wybiral on 2006-12-11
THANKS po0f, that's exactly what I wanted!

---

### Post by po0f on 2006-12-11
Wybiral,

I forgot to add -I (eye) to the script, but it's easy enough to figure out, right?  ;)

---

### Post by Wybiral on 2006-12-11
Yep, thats all I needed, it will be a big help, I've been working on a lot of projects with python interfacing and I'd like them to be more portable for people with other version of python. I'd also like them to be easily changed whenever another python version comes out. Using the path in the include line was a terrible approach, but that was the only method I had ever seen until now. But, once again, thanks for the help (maddog39 and po0f).

---

