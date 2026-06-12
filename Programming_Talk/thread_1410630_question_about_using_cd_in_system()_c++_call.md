---
title: "question about using cd in system() c++ call"
date: 2010-02-19
forum: Programming Talk
---

### Post by daweefolk on 2010-02-19
I'm trying to write a simple little terminal-based navigation program that shows what files are in your working directory and asks your desired destination folder. It should then cd to said folder, clear the screen, ls again, and ask again.
the bit of code concerned is
```

string fullcommand;//takes the user input and combines it with the cd command to get the full command to pass through system()
string userinput;//the directory the user wishes to cd into
system("ls");
cout<<"enter which directory?\n";
cin>>userinput;
fullcommand="cd "+userinput;
system(fullcommand.c_str());
system("clear");
system("ls");

```
however, the directory never changes. if i launch the program in my home folder and tell it to cd into Desktop via my program, the directory stays as my home folder.
is it possible to use the cd command like this?

---

### Post by falconindy on 2010-02-19
Your system() call is creating its own shell. It won't modify the shell that it was called from. Generally, you can't modify the parent process.

---

### Post by Simon17 on 2010-02-19
Look up chdir() from unistd.h

---

### Post by PaulM1985 on 2010-02-19
Hi

I have been doing some work with directory contents recently.  I found this:

[http://www.gnu.org/software/libc/manual/html_node/File-System-Interface.html#File-System-Interface](http://www.gnu.org/software/libc/manual/html_node/File-System-Interface.html#File-System-Interface)

really useful.

Using opendir(const char* aDirectory) and the function readdir() to access the files in the directory was really useful and could be worth looking at.

Also, doing it this way, you don't need to use "cd" to change the directory, you just pass in a directory path as an argument.

Hope this is of some help.

Paul

---

### Post by daweefolk on 2010-02-19
how would i use unistd.h and chdir() with the variable "userinput"? like if userinput was "/bin" how would i get chdir() to send me to /bin?  I tried "chdir(userinput)" and "chdir(userinput.c_str())" but neither worked.

---

### Post by Simon17 on 2010-02-19
What do you mean "neither worked"? What have you tried?
Can you run this program?

```
#include <iostream>
#include <string>
#include <unistd.h>

int main()
{
    char buffer[BUFSIZ];
    std::string directory("/bin");
    getcwd (buffer, BUFSIZ);
    std::cout<<"Current working directory is "<<buffer<<std::endl;
    chdir(directory.c_str());
    getcwd (buffer, BUFSIZ);
    std::cout<<"Current working directory is now "<<buffer<<std::endl;
    return 0;
}

```

---

### Post by falconindy on 2010-02-19
```
#include <unistd.h>
#include <stdio.h>
#include <fcntl.h>

int main(int argc, char** argv) {
    int fd = open(argv[1], O_RDONLY);
    int ret = fchdir(fd);
    if (ret == 0)
        printf("%s\n", get_current_dir_name());
    else
        fprintf(stderr, "%s: No such file or directory: %s\n", argv[0], argv[1]);

    return ret;
}
```

You still can't modify the parent process, though.

---

### Post by daweefolk on 2010-02-19
> **Simon17 said:**
> What do you mean "neither worked"? What have you tried?


When I said neither worked, i meant both the examples i gave, gave errors upon attempting to compile. I'll post them in a while, as I'm not currently booted into linux.

---

