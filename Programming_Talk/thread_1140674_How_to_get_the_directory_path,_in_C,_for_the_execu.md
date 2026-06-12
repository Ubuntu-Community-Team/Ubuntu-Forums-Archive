---
title: "How to get the directory path, in C, for the executing application?"
date: 2009-04-27
forum: Programming Talk
---

### Post by rich1939 on 2009-04-27
I have an executable application that I wrote in C and Gtk+ and I want to create a Launcher for it that will be placed in a submenu to the Applications menu.

I designed the GUI using Glade 3, so the application needs to read the "program.xml" file in order to instantiate the user interface components.

When I create a Launcher with a path to the executable, it doesn't change to that directory, so the application can't find its "program.xml" file, or any other file that may be needed.

When the Launcher "launches" the program, how do I programatically acquire the application's directory, so that I can use **chdir()** to change to that directory before continuing execution of the application?

Sorry for being so long-winded, but that's my current problem, and there is probably a simple C library function that will let me acquire the application's directory pathname.

---

### Post by cabalas on 2009-04-27
I ran across a similar problem with an application I was developing this was how I solved it.

Due to building my program with autotools I was able to get the install prefix when configure was run I passed this to the compiler with like the following:

```

gcc -c <file_name> -DINSTALL_PATH="/install/path" 

```

Then I could reference INSTALL_PATH from within my files as if I had defined it myself. Of course you can supply this all manually and INSTALL_PATH is just an arbitrary name.

Hope that helps

---

### Post by dwhitney67 on 2009-04-27
There are several ways to solve this problem.  One, as you pointed out, is to use chdir() at the opening of your application.  This library call takes the string-literal of the path where to change directory to.
```

chdir("/home/foo/somePath");
...

```

Another alternative is to change directory before running the application.  For instance:
```

cd somedir && ./app

```

The best solution is probably to place your data file(s) into a subdirectory within /usr/share (e.g. /usr/share/myapp).  Then your application would use the hard-coded path to these files, and it does not matter from where the application is launched.

---

### Post by rich1939 on 2009-04-27
> **dwhitney67 said:**
> There are several ways to solve this problem.  One, as you pointed out, is to use chdir() at the opening of your application.  This library call takes the string-literal of the path where to change directory to.
```

chdir("/home/foo/somePath");
...

```

Another alternative is to change directory before running the application.  For instance:
```

cd somedir && ./app

```

The best solution is probably to place your data file(s) into a subdirectory within /usr/share (e.g. /usr/share/myapp).  Then your application would use the hard-coded path to these files, and it does not matter from where the application is launched.

Ideally, I would rather have some way to determine in the executable's code in what path the executable resides. I surmise that there isn't a library function that can return the executable's current path...but that would be best.

Placing the application and its files in a constant location (e.g., /usr/share/myapp/) just doesn't seem very clean to me.

I have .jpg image files that load into Gtk+ button containers in the GUI and even I was surprised that they couldn't be found unless I changed to the directory in which they resided before running the application. I'm not sure how to solve that situation without doing a **chdir()** to the application's directory at the beginning of the application's execution.

Finding a library function that returns the executable's directory would be best, so I could put the application anywhere, do the **chdir()** and it would execute properly.

---

### Post by soltanis on 2009-04-28
You are looking for getcwd(), a part of unistd.h.

[man 3 getcwd]("http://www.manpagez.com/man/3/getcwd/")

---

### Post by eye208 on 2009-04-28
> **soltanis said:**
> You are looking for getcwd()
getcwd() will fail most of the time because the application folder is not the current directory.

On Linux, the file /proc/self/exe is a symbolic link to the application executable. The readlink() function will return the full path of the link target. You can use this to extract the folder pathname:
```
#include <iostream>
#include <string>
#include <unistd.h>
#include <limits.h>

std::string getpath() {
        char buf[PATH_MAX + 1];
        if (readlink("/proc/self/exe", buf, sizeof(buf) - 1) == -1)
                throw std::string("readlink() failed");
        std::string str(buf);
        return str.substr(0, str.rfind('/'));
}

int main() {
        std::cout << "This program resides in " << getpath() << std::endl;
        return 0;
}
```

---

### Post by nvteighen on 2009-04-28
> **eye208 said:**
> getcwd() will fail most of the time because the application folder is not the current directory.

On Linux, the file /proc/self/exe is a symbolic link to the application executable. The readlink() function will return the full path of the link target. You can use this to extract the folder pathname:
```
#include <iostream>
#include <string>
#include <unistd.h>
#include <limits.h>

std::string getpath() {
        char buf[PATH_MAX + 1];
        if (readlink("/proc/self/exe", buf, sizeof(buf) - 1) == -1)
                throw std::string("readlink() failed");
        std::string str(buf);
        return str.substr(0, str.rfind('/'));
}

int main() {
        std::cout << "This program resides in " << getpath() << std::endl;
        return 0;
}
```
Thanks for the tip. I don't know when I'm going to use that, but it's worth to know :)

---

### Post by rich1939 on 2009-04-28
> **eye208 said:**
> getcwd() will fail most of the time because the application folder is not the current directory.


That's right, I found that out.

> 
On Linux, the file /proc/self/exe is a symbolic link to the application executable. The readlink() function will return the full path of the link target. You can use this to extract the folder pathname:


Thanks very much for the info. I was almost sure there would be a way to get the executable's path. I appreciate your input.

---

