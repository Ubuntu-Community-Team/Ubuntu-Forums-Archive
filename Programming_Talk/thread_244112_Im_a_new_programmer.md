---
title: "Im a new programmer"
date: 2006-08-25
forum: Programming Talk
---

### Post by Icon41 on 2006-08-25
Im a new C++ programmer, I can make a hello world program or a calculator in C++ in windows but I dont know how to do it in linux, if I were to make a hello world in c++ for linux how would the script look and how would I run it?

---

### Post by johnnymac on 2006-08-26
#include <stdio.h>

int main( int argc, char **argv )
{

    printf( "Hello World\n" );
    return 0;
}

save it as hello.c and then issue this from a command line.

gcc hello.c -o hello
./hello

yay - hello world....

---

### Post by Jessehk on 2006-08-26
> **johnnymac said:**
> #include <stdio.h>

int main( int argc, char **argv )
{

    printf( "Hello World\n" );
    return 0;
}

save it as hello.c and then issue this from a command line.

gcc hello.c -o hello
./hello

yay - hello world....

No, that would be in C.

Here is hello world in C++.

**hello.cpp**
```

#include <iostream>

int main() {
	std::cout << "Hello, world!" << std::endl;
}

```

Your compilation instructions are correct, but use "g++" instead of "gcc" and call it *.cpp instead of *.c.

---

### Post by ssam on 2006-08-26
if you want to do things with a graphic user interface you might want to look at glade.

---

### Post by Icon41 on 2006-08-26
whats glade, a programming language?

---

### Post by ifokkema on 2006-08-26
Glade is a program used to design GTK interfaces.
```
sudo apt-get install glade
```

---

### Post by X.Cyclop on 2006-08-26
Glade, KDevelop (Designer) and QtDesigner are GUI makers, "equivalents" to Visual *.

;)

---

### Post by peabody on 2006-08-27
From my understanding, if you're more of a C++ guy, Qt and the KDE platform are more fun to work with, although there's C++ stuff for GTK and Glade.  Another library that can be used in C++ is wxWindows (now known as wxWidgets).

---

### Post by ifokkema on 2006-08-27
> **peabody said:**
> Another library that can be used in C++ is wxWindows (now known as wxWidgets).

I've been told that using wxWindows allows you to distribute your apps to Windows easily.

---

### Post by X.Cyclop on 2006-08-27
I think wxWidgets is more for cross-platform apps.

---

### Post by johnnymac on 2006-08-27
Oops...sorry - didn't see the "++" :)

---

