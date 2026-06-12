---
title: "how to use g++ on linux?"
date: 2007-05-06
forum: Programming Talk
---

### Post by outer_space on 2007-05-06
On windows it was 'g++ main.cpp -o main.exe'  

but on ubuntu exe files dont work.  What works?

Thanks.

---

### Post by Auria on 2007-05-06
> **outer_space said:**
> On windows it was 'g++ main.cpp -o main.exe'  

but on ubuntu exe files dont work.  What works?

Thanks.

I think you're definitely on the wrong forum. This is not a proposal for Gutsy... just use packages manager to install build-essential

---

### Post by 23meg on 2007-05-06
Moved to Programming Talk.

---

### Post by jespdj on 2007-05-06
> **outer_space said:**
> On windows it was 'g++ main.cpp -o main.exe'  

but on ubuntu exe files dont work.  What works?

Thanks.

You can give executables any extension you like, or no extension at all. On Linux (and Unix in general), executables usually have no extension. "exe" will work as well as anything or no extension.

```
g++ main.cpp -o main
./main
```

Note the the "./" which means, "look in the current directory for the file named 'main'".

---

### Post by WW on 2007-05-06
There is nothing wrong with the example that you gave.  If you want to call the executable program "main.exe", you can.  However, it is not required to use the .exe extension. In Linux, usually the executable file would just be called "main". For example,
```

$ g++ main.cpp -o main    # Compile  main.cpp, call the executable program "main"
$ ./main                  # Run the program

```
Of course, this will only work if you have g++ installed.  You can install g++, gcc, and some other useful development tools and libraries by installing the package **build-essential**.  You can do this with Synaptic Package Manager, or with the command
```

$ sudo apt-get install build-essential

```

EDIT: Heh, looks like I echoed jespdj's response.

---

### Post by outer_space on 2007-05-06
Thanks, this works.  I didnt know about './'

---

