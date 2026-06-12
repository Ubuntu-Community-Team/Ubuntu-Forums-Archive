---
title: "how to use cin.get() and system() on linux systems"
date: 2011-08-14
forum: Programming Talk
---

### Post by martsul on 2011-08-14
Hello I just made a complete switch to Ubuntu, the main reason was because I liked programing on windows for I thought it was easier. Now I am have some problems with some of the code that i have begun to transfer over. I cant seem to get cin.get() to work and I have no idea how to communicate with the system for I am sure system("..") is not the same on Linux as it is windows.

edit: Forgot to mention that this was C++. I also finaly figured out what was wrong with cin.get(), I dint know I needed to add ctype.h so any help with the system issue and I would be very grateful.

---

### Post by gardnan on 2011-08-14
This is strange. As far as I can tell, system on Linux and Windows do pretty much the same thing (call the basic shell with a single command). Could you explain what you mean when you say "how to communicate with the system"? Also, cin.get works fine on my system without including ctype.h. It would also be helpful to see any compiler or run-time errors.

---

### Post by NovaAesa on 2011-08-14
If you're having trouble with code compatibility between Windows and Linux, there's not really anything we can do to help until you provide a minimal working example.

If you are wanting to get cross platform compatibility (always a worthy goal!) then it's best to stay away from system calls, and use a library to do the task instead.

---

### Post by martsul on 2011-09-04
Sorry for not replying back soon I have been busy with work.

@gardnan this is kinda weired because now i get no errors when I run a program with cin.get and no ctype.h.

@NovaAesa what would be a good library to use to communicate with a system than?

here is a simple code using system() and the error from compiling. Also I would like to be able to communicate with the system for pauses or clears because they tend to be more reliable for me. When I use the cin.get function more than a few times it tends to fall through.

[PHP]include <iostream>

int main()
{
    std::cout << "hello. \nPress enter to continue.\n";
    
    system("pause");

    return 0;
}[/PHP]```
g++ -Wall -W -Werror hello.cpp -o hello
hello.cpp: In function ‘int main()’:
hello.cpp:7:16: error: ‘system’ was not declared in this scope

```

---

### Post by dwhitney67 on 2011-09-04
system() is prototyped in stdlib.h; this file is not included in your code, and hence the reason the warning is produced.

But in your particular case, you should *not* be using system() to pause the program, because 1) it is unnecessary, and 2) "pause" is not a Linux program.

Stick to using standard C++, which should work on Linux, Unix, and even the dreadful Windoze:
```

#include <iostream>

int main()
{
   std::cout << "Hello.\nPress enter to continue." << std::endl;
   **std::cin.get();**
}

```

---

### Post by martsul on 2011-09-04
@dwhitney67 I appreciate that and understand how to use cin.get() considering I was having the beautiful operator error. However like I mentioned before if I use that function to often it tends to throw the argument and not work 100% of the time like I would like it and have never had that problem with the system() function. However I do appreciate the input, plus I like to use it for other functions besides pause like cls. Now if you have a better way of doing system commands than through the use of system I would appreciate it.

---

### Post by dwhitney67 on 2011-09-04
Again, Linux is not Windoze;  "pause", "cls", and undoubtedly other specific Windows commands are *not* available under Linux.

The system() command does have it's uses (and at moment, I cannot think of one!), however oftentimes the C library provides alternate ways to accomplish a goal.  The C library is what you should use, as opposed to using system-specific commands.

P.S. The Linux equivalent of "cls" is "clear".

---

### Post by martsul on 2011-09-04
yea sorry about that I still have the windows mentality and figured out the error with pause and cls just before you posted. While I can see its uses, just not for a sample program like this one. I appreaciate the help with the clarification on that. I was wondering if you would know why if I have an over use of the cin.get() command that it throws the command sometimes or if its just my computer, that would help me solve my last problem.

---

### Post by dwhitney67 on 2011-09-04
Most often it is the programmer that throws a "wrench" into the application.  Rarely can one blame the computer or even the compiler.

Bookmark the following website so that you may find pretty much any/all answers you may have for C++ programming, including the details of how cin.get() works:  [http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)

---

### Post by martsul on 2011-09-05
I found the cin.ignore() function which works to help prevent the code from just passing the cin.get() command so thank you dwhitney67.

---

