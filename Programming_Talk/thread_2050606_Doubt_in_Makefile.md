---
title: "Doubt in Makefile"
date: 2012-08-31
forum: Programming Talk
---

### Post by IAMTubby on 2012-08-31
Hello,
Today is my first day with Makefiles. I have been able to understand what it does and why we need the concept of Makefiles. 
But I'm having an issue

I)Scenario : There is an existing application (which has a Makefile).  Now I have to add the CUnit unit testing functionality to it.
I am very grateful to dwhitney67, [http://ubuntuforums.org/showthread.php?t=1727067&highlight=CUnit]("http://ubuntuforums.org/showthread.php?t=1727067&highlight=CUnit"). It worked perfectly for me.

II)Question : How do I add this to the existing makefile ?

III)Steps for compiling and running a CUnit application :
```
Compile : gcc -Wall -I$HOME/local/include MyProg.c -L$HOME/local/lib -lcunit -o myprog
Run : LD_LIBRARY_PATH=$HOME/local/lib ./MyProg
``` 

IV)My understanding of changes required in the makefile : 
1)I know that $HOME/local/include has to be included to the -I part of the makefile. 
2)What should I add to the -L part of the makefile ?
$HOME/local/lib          or           $HOME/local/lib -lcunit
3)I know MyProg.o has to be added to the OBJS = part of the makefile
4)But how do I account for all the LD_LIBRARY_PATH=$HOME/local/lib ./MyProg in the makefile ?

Thanks

---

### Post by steeldriver on 2012-08-31
I'm not clear what you're trying to do - do you actually want to run unit tests (as targets) from the makefile? 

It sounds like you have the basics figured out, however to answer your specific questions it would be helpful if you posted the makefile - there are some conventions for where these things go there are variations depending on the specific platform / development environment and preferences of the developer

---

### Post by dwhitney67 on 2012-08-31
The Makefile is used to build the application.  Although it could be used to run the application (I sometimes do this because I'm lazy), it generally is expected that a script will be used to run an application that requires an environment setup prior to running the application.

As for a Makefile, a very simple one could look like this:
```

APP     = myprog

SRCS    = MyProg.c
OBJS    = $(SRCS:.c=.o)

CUNIT   = $(HOME)/local

CFLAGS  = -Wall -I$(CUNIT)/include
LDFLAGS = -L$(CUNIT)/lib
LIBS    = -lcunit

.PHONY: clean


$(APP) : $(OBJS)
    $(CC) $^ $(LDFLAGS) $(LIBS) -o $@

clean :
    $(RM) $(OBJS) $(APP)

```
For running the code, as I think you already know, LD_LIBRARY_PATH needs to be used to specify the location of the CUNIT library.  You could, if you plan to use this path for other projects, is either a) define the LD_LIBRARY_PATH in your $HOME/.bashrc file, or b) have the system administrator install the CUNIT package within /usr/local (or other location) and then make sure that the ldconfig cache is updated.

If you have admin rights on your system, and would like to pursue option (b), then let me know.


P.S.  I have not tested the Makefile above; let me know if it fails to function.

---

### Post by IAMTubby on 2012-08-31
steeldriver
I already got my helloworld kind of CUnit application working.
What I want to do is to incorporate a couple of test cases into the real application that I have. That application has a lot of files, and so to get it working along with CUnit test cases in it, I'll have to edit it's makefile. Am I more clear this time ?

dwhitney,
Yes, I have admin rights.
Which of the 2 options do you want me to do ? Can I come on IM with you, like we once did ?

---

### Post by IAMTubby on 2012-08-31
I'm sorry , I don't understand how to edit the ~./bashrc file.
This is how it looks now.


# .bashrc

# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi

# User specific aliases and functions

---

### Post by dwhitney67 on 2012-08-31
> **IAMTubby said:**
> I'm sorry , I don't understand how to edit the ~./bashrc file.

Edit the file, add what I have inserted below in bold text.
```

# .bashrc

# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi

# User specific aliases and functions
**export LD_LIBRARY_PATH=~/local/lib:${LD_LIBRARY_PATH}**

```
Once you have saved the file, re-source the .bashrc file for each terminal that you have open:
```

$ source ~/.bashrc

```
or alternatively, just close each terminal, and the re-launch them.

---

### Post by dwhitney67 on 2012-08-31
Making the CUNIT library available to all users on your system requires that you re-configure and re-install the CUNIT library in its default location (which, if I had to guess, is in /usr/local).  This will require admin privileges.

```

cd <cunit download directory>

./configure

make

sudo make install

```
Then comes the tricky part...

Depending on where the CUNIT library is installed, you *may* need to augment the search paths used by ldconfig.  For now, assume the path is known to ldconfig; to verify if CUNIT is "picked up", run this command:
```

sudo ldconfig -v | grep -i cunit

```
If you see that the library was found, then you are done.

Otherwise, you will need to create a file in /etc/ld.so.conf.d called, say cunit.d, and add to the file the path where the CUNIT library resides.  Then re-run ldconfig as shown above.

P.S.  If you follow these instructions, then you will not need to use LD_LIBRARY_PATH to specify the location of the CUNIT library.

---

### Post by IAMTubby on 2012-08-31
dwhitney,
Yes I have it working only by doing ./myprog now.

Now what I want to know is,
How do you add these steps to the makefile that I have. Sir,I know this will be difficult for you because you don't have my makefile.
But can we try and do a few things general to all makefiles. 

This is how you compile right?
```
gcc -Wall -I$HOME/local/include MyProg.c -L$HOME/local/lib -lcunit -o myprog
```

Assumptions:
My makefile has the following parts
1)LIBS = -L part, which has the path to a lot of libraries
2)COMMON_ABS_OBJS part
3)INCLUDE_PATHS += -I. part which has the path to a lot of includes
4)all
5)clean
6)install
7)OBJS = 

Steps to do:
1)So I put $HOME/local/include inside the -I part of the makefile.
2)What do I put in the -L part of the makefile
3)And what do I do about the -lcunit in the compile line ?

PS : This was posted without looking at your last comment as it's already working.

---

### Post by dwhitney67 on 2012-08-31
> **IAMTubby said:**
> 
PS : This was posted without looking at your last comment as it's already working.

I'm not sure at what point you are now, but if you still have questions/doubts about the Makefile, please refer to my previous post:  [http://ubuntuforums.org/showpost.php?p=12208167&postcount=3](http://ubuntuforums.org/showpost.php?p=12208167&postcount=3)

---

### Post by IAMTubby on 2012-08-31
dwhitney,I think I'm very close to getting it sorted out.
Just 1 more question.

What does -lcunit mean in
```
gcc -Wall -I$HOME/local/include MyProg.c -L$HOME/local/lib -lcunit -o myprog
```

If I get to understand this, I'll probably be able to edit my makefile

---

### Post by IAMTubby on 2012-08-31
dwhitney,
Found it from the internet, "-l is the name of the library you want to link to". Thanks a lot for all your help.

Although I am yet to try it out on my makefile, I understand this is the maximum that a remote person can help. So marking the thread as solved.

Thanks once again ! and hope it works on the makefile.

---

