---
title: "problem with c++"
date: 2007-02-08
forum: Programming Talk
---

### Post by lionheartyoung on 2007-02-08
Hi, I am a newbie in c/c++ programming in ubuntu. So, I am testing the "helloworld" program. There was no problem at compilation, it also generated a executable file. But when I execute the file, it does nothing. I am really confused by it. Anyone can help me out? 
My program is like this:

"test.cpp" 

#include <iostream>
using namespace std;
int main()
{
        std::cout<<"hello world"<<endl;
        return 0;
}

I used "g++ -o test test.cpp" to compile the code.


When I run 'test',  it did nothing instead of printing 'hello world'.
here is the output:

liuyang@liuyang-desktop:~/cs354$ test
liuyang@liuyang-desktop:~/cs354$

Is it strange?

---

### Post by maxamillion on 2007-02-08
```
./test
```

To run an executable in the command line that is not in the system's $PATH you must specify its exact path or location ... and ./ (which means "this directory i am in right now") so in this case ./test is what you want.

---

### Post by lionheartyoung on 2007-02-08
thanks. It worked! Where can I set up the systems $PATH?

---

### Post by maxamillion on 2007-02-08
I have to ask, why would you want to put a hello world program in your system's $PATH?

It is generally only used for applications installed or scripts used regularly.

[EDIT]: good link about $PATH .... [http://www.faqs.org/docs/Linux-mini/Path.html](http://www.faqs.org/docs/Linux-mini/Path.html)

---

### Post by lionheartyoung on 2007-02-08
Forgive me my ignorance here. 
I just don't want to execute a program with './' before its name.  There must be a way to solve it, right?

---

### Post by maxamillion on 2007-02-08
nope, that's just how it is done 

its a characteristic of all *nix operating systems (atleast all those I have encountered)

---

### Post by lnostdal on 2007-02-08
> **lionheartyoung said:**
> Forgive me my ignorance here. 
I just don't want to execute a program with './' before its name.  There must be a way to solve it, right?

add . to your path

edit: . signifies the current directory in the same way that .. signifies the parent directory

edit2: you can also move your binary to a directory that already is in your path, like for instance /usr/local/bin

---

### Post by jblebrun on 2007-02-08
It should be noted that adding . (current directory) to your path is considered a **security risk**. 

It's not as dire for a restricted user, but it does open avenues for attackers to do malicious things. Since you may be in a directory writable by other people when you execute a command, if the "current directory" is in your path, than someone could, in theory, put replacement scripts in the path that will run instead of the system tools. 

This can be mitigated somewhat by making sure that "." is at the very end of your search path, always. But even then, there is the possibility of attack by taking advantage of common command typos (sl instead of ls, etc). 

It's not a HUGE deal on your own personal machine, but it's something that you should always keep in mind when you're using a multi-user machine. 

It's a good idea to NEVER set "." in the PATH for root.

---

### Post by LordHunter317 on 2007-02-08
You should get used to writing ./.

---

### Post by kpatz on 2007-02-08
Also, 'test' is a builtin command in certain shells (bash for example), so even if your test executable is in your path, just typing 'test' won't run it.  Better to give your program a different name.

If you don't like typing ./ you can always add /home/<your_user_name> to your PATH.  Or put whatever directory you tend to compile stuff into.  Maybe create a ~bin directory and set a path to that.  There, easier launching without the security risks. :)

---

