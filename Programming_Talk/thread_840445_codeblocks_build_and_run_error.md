---
title: "code::blocks build and run error"
date: 2008-06-25
forum: Programming Talk
---

### Post by ResilientBiscuit on 2008-06-25
I just finished my first day of computer science class and I am trying to get my hello world program to work in code::blocks.

Its written in C++ and if I use g++ I can compile and run in manually, but when I try to build and run it in code::blocks it pops up the command line and gives me a permission denied error.

Any ideas what might be going on here?

Thanks a bunch
Justin

---

### Post by MacAnthony on 2008-06-25
Got the exact error? Permission denied to what?

---

### Post by ResilientBiscuit on 2008-06-25
Im at work at the moment, ill post the exact error when I get home.

It was something along the lines of:

"sh: [path of the file here] permission denied"

---

### Post by ResilientBiscuit on 2008-06-25
Ok, so when I run it from code::blocks I get the following error:

```
sh: /home/jdwolford/CS161/helloworld/helloworld: Permission denied

Press enter to continue.
```

It looks like its trying to run the following command:
```

Executing: xterm -T '/home/jdwolford/CS161/helloworld/helloworld' -e /usr/bin/cb_console_runner "/home/jdwolford/CS161/helloworld/helloworld" (in /home/jdwolford/CS161/helloworld)
```

---

### Post by Mickeysofine1972 on 2008-06-26
check the permissions are executable.

when you compile a new program you may have to assign it a +x with chmod:
```
chmod + <name of program>
```

This may work, not absolutely sure

Mike

---

### Post by Xero121690 on 2008-08-22
I happen to have the same problem...
Does any one know how to allow code blocks to run and compile without getting that permission denied window? 
Would be appreciated :)

---

### Post by dwhitney67 on 2008-08-22
After you compile/link your program, verify that the resulting executable is indeed an executable.
```
$ ls -l a.out
-rwxrwxr-x 1 dwhitney dwhitney 4742 2008-08-22 17:01 a.out

```

The other thing is to try running the program such as:
```
./a.out
```
Some *nix systems do not include './' in the PATH environment setting as a security precaution.

---

### Post by chinchillart on 2008-10-17
Just installed Code::Blocks IDE 8.02 on Ubuntu 8.04.1.

Same problem.

After some trial-errors, I'v found a solution.

I've place the standard code::blocks dir for project in my home:

/home/rob/CB

Here I'll save all my C/C++ projects.

Now make executable the cb_console_runner for all users:

```

rob@ubuntu:~$ sudo chmod a+x /usr/bin/cb_console_runner

```

Finally, I've changed the settings in Code::Blocks like this:

[[IMG]http://img221.imageshack.us/img221/5687/schermataenvironmentsetoi8.th.png[/IMG]](http://img221.imageshack.us/my.php?image=schermataenvironmentsetoi8.png)

```

Shell to run commands in: [ /bin/bash -c ]
Terminal to launch console program: [ xterm -T $TITLE -e ]

```

Now it works! :popcorn:

Rob

---

### Post by stoyrulzu on 2008-11-02
Hey dude! Could you be a little more specific on what you did to make codeblocks compile and run under linux? I have the same problem and I can't get it to work.

I'm relatively new to ubuntu and I really want codeblocks to run. 
Small exact steps :) would be most appropriate.

hope you reply!

Thanks in advance!

---

### Post by stoyrulzu on 2008-11-03
I managed to get Codeblocks to Compile , but nothing happens when I click run.

Does anyone has an answer for this?

---

### Post by firefly07 on 2008-11-30
> **chinchillart said:**
> Just installed Code::Blocks IDE 8.02 on Ubuntu 8.04.1.

Same problem.

After some trial-errors, I'v found a solution.

I've place the standard code::blocks dir for project in my home:

/home/rob/CB

Here I'll save all my C/C++ projects.

Now make executable the cb_console_runner for all users:

```

rob@ubuntu:~$ sudo chmod a+x /usr/bin/cb_console_runner

```

Finally, I've changed the settings in Code::Blocks like this:

[[IMG]http://img221.imageshack.us/img221/5687/schermataenvironmentsetoi8.th.png[/IMG]](http://img221.imageshack.us/my.php?image=schermataenvironmentsetoi8.png)

```

Shell to run commands in: [ /bin/bash -c ]
Terminal to launch console program: [ xterm -T $TITLE -e ]

```

Now it works! :popcorn:

Rob

I just did this and Code::Blocks is working!!! One thing though, my .cpp files will build and run even if they are not in the project directory of C::B... I did what was stated here, added execution parameters to the projects directory, and also... I feel stupid to admit this... But I installed G++... Perhaps anyone of you guys didn't install it first as me

---

### Post by XelNaga on 2008-12-31
I got Code::Blocks working by doing these steps:
```

$ sudo chmod a+x /usr/bin/cb_console_runner
$ sudo apt-get install xterm

```
Hope this help :D

---

### Post by bongo264 on 2010-02-03
Be sure to save the file as .cpp when I did this things started working.....

Bongo264

[bongounderground.com]("http://bongounderground.com")

---

### Post by c2tarun on 2010-08-30
> **dwhitney67 said:**
> After you compile/link your program, verify that the resulting executable is indeed an executable.
```
$ ls -l a.out
-rwxrwxr-x 1 dwhitney dwhitney 4742 2008-08-22 17:01 a.out

```The other thing is to try running the program such as:
```
./a.out
```Some *nix systems do not include './' in the PATH environment setting as a security precaution.

hi dwhitney..
i checked and there is no a.out file there in the folder even after compilation.
to be more precise build log section is showing the message "Nothing to be done".
i don't know what does it mean. please help me. thanks

---

### Post by BFD1693 on 2012-08-29
everytime i try to build the program it show this in xterm:

```

sh:1: /home/user/CB/hello: Permission denied

Process returned 126 (0x7E)      execution time: 0.002 s
Press ENTER to continue

```

This is the code:

```

#include <iostream>
using namespace std;
int main(){
    cout<<"Hello World";
    cin.get();
    return 0;
}


```

and the build log:
```

Nothing to be done.

Checking for existence: /home/user/CB/hello
Executing: xterm -T '/home/user/CB/hello' -e /usr/bin/cb_console_runner "/home/user/CB/hello" (in /home/user/CB)


```

I have already installed the gcc and done the 
chmod a+x /usr/bin/cb_console_runner[FONT=monospace]
but I still couldnt find the settings that chinchillart used

hope you can help me 
thanks!
[/FONT]

---

