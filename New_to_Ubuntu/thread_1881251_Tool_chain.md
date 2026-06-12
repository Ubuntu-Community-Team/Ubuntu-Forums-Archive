---
title: "Tool chain"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by 213Wayne on 2011-11-15
Hi.

I have UBUNTU 10.04 installed on my laptop.
I have downloaded and installed tool chain (arm-linux_3.3.2_V1.0_Build11080410.sh) as instructed by the documentation that I am using.
I included the path for the tool chain (export PATH=/usr/local/arm-linux/bin:$PATH).
I attempted to run a sample program using the **make** command as instructed by the documentation.

I get an error:
/usr/local/arm-linux/bin/arm-linux-gcc -o hello-release hello.c
make: /usr/local/arm-linux/bin/arm-linux-gcc: Command not found
make: *** [release] Error 127

The makefile and documentation are attached.
Can anyone help urgently?

---

### Post by carranty on 2011-11-15
I'm not sure, but it are you sure gcc is installed? Running

```
dpkg --status gcc
```

from a terminal will tell you if it is or not.  If not, install it with

```
sudo apt-get install gcc
```

---

### Post by carranty on 2011-11-15
Ignore that last comment, it won't help.  I suspect your problem is you either haven't installed tool chain correctly or you've specified the wrong path.  Run

```
ls /usr/local/arm-linux/bin/arm-linux-gcc
```

If it doesn't output anything the file isn't there, but your telling the program to look there.

---

### Post by 213Wayne on 2011-11-15
Yes it is.

wayne@ubuntu:/tmp/example/hello$ sudo apt-get install gcc
[sudo] password for wayne: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by 213Wayne on 2011-11-15
wayne@ubuntu:/tmp/example/hello$ ls /usr/local/arm-linux/bin/arm-linux-gcc
/usr/local/arm-linux/bin/arm-linux-gcc

---

### Post by 213Wayne on 2011-11-15
I followed the documentation line by line.

---

### Post by carranty on 2011-11-15
Hmm, I don't know then.  I don't see any attachments to the documentation, could you try reuploading them, or send me a link to where I can download it.  I'd also like to see the arm-linux-gcc file if possible.

I'll try installing it myself and see if it throws up the same error, can you let me know where you downloaded it from, I can't seem to find it online.

EDIT : Another thought, where on your computer is the makefile?  It looks like its that the program can't find......

---

### Post by 213Wayne on 2011-11-15
Thank you

---

### Post by carranty on 2011-11-15
Can you let me know where you downloaded it from?

---

### Post by 213Wayne on 2011-11-15
I got it off a disk.

---

### Post by MG&amp;TL on 2011-11-15
Perhaps try something like:

```
CC=<path to armel gcc>

all: Hello.c

    $(CC) -o Hello Hello.c
```

---

### Post by 213Wayne on 2011-11-15
When I attempt to run my program, I run it from the directory that the makefile is in.

---

### Post by 213Wayne on 2011-11-15
That code is in the makefile that I am attempting to run:

PREFIXPATH=/usr/local/arm-linux/bin
CC=$(PREFIXPATH)/arm-linux-gcc
STRIP=$(PREFIXPATH)/arm-linux-strip
NAME=hello

all: release debug

clean:
    rm -f $(NAME)-release $(NAME)-debug

release:    $(NAME).c
    $(CC) -o $(NAME)-release $(NAME).c
    $(STRIP) -s $(NAME)-release

debug:        $(NAME).c
    $(CC) -ggdb -o $(NAME)-debug $(NAME).c

---

### Post by MG&amp;TL on 2011-11-15
If you just run <path to arm-gcc> in a terminal does it give you something like:

```
gcc: no input files
```

?

---

### Post by 213Wayne on 2011-11-15
When I attempt running this code from the makfile:

CC=/usr/local/arm-linux/bin/arm-linux-gcc

all: hello.c

$(CC) -o hello hello.c

I get this error:

wayne@ubuntu:/tmp/example/hello$ make
Makefile:6: *** missing separator.  Stop.

---

### Post by MG&amp;TL on 2011-11-15
*something like. [TAB] doesn't work on UF. That was just an example to make sure that the makefile hadn't been mucked about with in some way. Your one should be fine.

Could you try my other suggestion, see whether there is actually a program there or not?

---

### Post by 213Wayne on 2011-11-15
When I run:
wayne@ubuntu:~$ /usr/local/arm-linux/bin/arm-linux-gcc

I get this response:
bash: /usr/local/arm-linux/bin/arm-linux-gcc: No such file or directory

When I navigate to the directory, I can see the file (blue ,diamond shaped).

---

### Post by MG&amp;TL on 2011-11-15
What package did you install to get the ARM compiler? Then I can install and troubleshoot.

Run this:

```
locate arm-linux-gcc
```

---

### Post by 213Wayne on 2011-11-15
When I run locate arm-linux-gcc I get this:

wayne@ubuntu:/tmp/example/hello$ locate arm-linux-gcc
/usr/local/arm-linux/bin/arm-linux-gcc
/usr/local/arm-linux/bin/arm-linux-gcc-3.3.2
/usr/local/arm-linux/bin/arm-linux-gccbug

This is the tool chain that I installed arm-linux_3.3.2_V1.0_Build11080410.sh

I will try to attach it.

---

### Post by 213Wayne on 2011-11-15
I just want to say that I am VERY impressed with your response time. :P

Your response time is OUTSTANDING!

---

### Post by MG&amp;TL on 2011-11-15
> **213Wayne said:**
> When I run locate arm-linux-gcc I get this:

wayne@ubuntu:/tmp/example/hello$ locate arm-linux-gcc
/usr/local/arm-linux/bin/arm-linux-gcc
/usr/local/arm-linux/bin/arm-linux-gcc-3.3.2
/usr/local/arm-linux/bin/arm-linux-gccbug

This is the tool chain that I installed arm-linux_3.3.2_V1.0_Build11080410.sh

I will try to attach it.

That is very werid. Bash says it's not there, nautilus says it is...locate says it is. Can you run:

```
file /usr/local/arm-linux/bin/arm-linux-gcc
```

And post please?

No problem, sick, so  not much else to do. :(

---

### Post by carranty on 2011-11-15
I'm afraid I've not been able to find this version anywhere so I can't install it on my end and compare results/errors.  Maybe you can upload it (along with the documentation) to rapidshare and post the link, if adding it as an attachment doesn't work.

---

### Post by 213Wayne on 2011-11-15
Tool chain is taking a while to upload on Rapidshare. I will send the link as soon as it's done.

Makefile:
[https://rapidshare.com/files/3744324034/Makefile](https://rapidshare.com/files/3744324034/Makefile)

Documentation:
[https://rapidshare.com/files/4262563302/Moxa_C_Programmable_RTU_Controllers_User_s_Manual.pdf](https://rapidshare.com/files/4262563302/Moxa_C_Programmable_RTU_Controllers_User_s_Manual.pdf)

---

### Post by carranty on 2011-11-15
I've read the relevant part of the documentation, it looks quite simple, I'm beginning to think this isn't anything to do with your toolchain but rather with bash.  Can you please create a blank file called script, and in it write the below

```
#! /bin/bash
echo "Bash Test"
```Then save and exit, make it executable by typing

```
chmod 766 script

```and then run it from the terminal using

```
./script
```Does it output the string "Bash Test", or does it also throw up an error message?

---

### Post by 213Wayne on 2011-11-15
I will try this tomorrow Unfortunately.

---

### Post by MG&amp;TL on 2011-11-15
If BASH is the problem (unlikely) try sh (what came before BASH)-just:

```
sh
```

at BASH.

---

### Post by 213Wayne on 2011-11-16
I created the file called script
This is the result:
wayne@ubuntu:~$ vi script
wayne@ubuntu:~$ chmod 766 script
wayne@ubuntu:~$ ./script
Bash Test

---

### Post by 213Wayne on 2011-11-16
The tool chain:

[https://rapidshare.com/files/1158748985/arm-linux_3.3.2_V1.0_Build11080410.sh](https://rapidshare.com/files/1158748985/arm-linux_3.3.2_V1.0_Build11080410.sh)

---

### Post by ofnuts on 2011-11-16
Are the files marked as executable? How have trhey been installed?

---

### Post by 213Wayne on 2011-11-16
This tool chain is for Linux OS. I copied the tool chain file to my desktop and then I ran it as instructed by the manual:

At the terminal I typed:

sh /home/wayne/Desktop/arm-linux_3.3.2_V1.0_Build11080410.sh and it installed.

---

### Post by ofnuts on 2011-11-16
> **213Wayne said:**
> This tool chain is for Linux OS. I copied the tool chain file to my desktop and then I ran it as instructed by the manual:

At the terminal I typed:

sh /home/wayne/Desktop/arm-linux_3.3.2_V1.0_Build11080410.sh and it installed.
and if you "ls -l" the files they have "x" in the flags?

---

### Post by 213Wayne on 2011-11-16
Have you installed the tool chain?

wayne@ubuntu:~/Desktop$ ls -l
total 150924
-rwxrwxrwx 1 wayne wayne 154537010 2011-08-04 04:11 arm-linux_3.3.2_V1.0_Build11080410.sh
drwxr-xr-x 2 wayne wayne      4096 2011-11-14 15:06 hello
-rw-r--r-- 1 wayne wayne        47 2011-11-16 12:29 Unsaved Document 2
wayne@ubuntu:~/Desktop$ cd
wayne@ubuntu:~$ cd /usr/local/arm-linux/bin
wayne@ubuntu:/usr/local/arm-linux/bin$ ls -l
total 11720
-rwxr-xr-x 1 root root  306296 2003-10-21 09:07 arm-linux-addr2line
-rwxr-xr-x 2 root root  284088 2003-10-21 09:07 arm-linux-ar
-rwxr-xr-x 2 root root  490572 2003-10-21 09:07 arm-linux-as
-rwxr-xr-x 2 root root   82228 2003-10-21 09:07 arm-linux-c++
-rwxr-xr-x 1 root root  305044 2003-10-21 09:07 arm-linux-c++filt
-rwxr-xr-x 1 root root   82004 2003-10-21 09:07 arm-linux-cpp
-rwxr-xr-x 2 root root   82228 2003-10-21 09:07 arm-linux-g++
-rwxr-xr-x 1 root root   85908 2003-10-21 09:07 arm-linux-g77
-rwxr-xr-x 2 root root   81812 2003-10-21 09:07 arm-linux-gcc
-rwxr-xr-x 2 root root   81812 2003-10-21 09:07 arm-linux-gcc-3.3.2
-rwxr-xr-x 1 root root   15653 2003-10-21 09:00 arm-linux-gccbug
-rwxr-xr-x 1 root root   85908 2003-10-21 09:07 arm-linux-gcj
-rwxr-xr-x 1 root root   65244 2003-10-21 09:07 arm-linux-gcjh
-rwxr-xr-x 1 root root   18580 2003-10-21 09:07 arm-linux-gcov
-rwxr-xr-x 1 root root 5982190 2005-11-02 23:54 arm-linux-gdb
-rwxr-xr-x 1 root root  540680 2003-10-21 09:07 arm-linux-gnatbind
-rwxr-xr-x 1 root root   63200 2003-10-21 09:07 arm-linux-jcf-dump
-rwxr-xr-x 1 root root   66704 2003-10-21 09:07 arm-linux-jv-scan
-rwxr-xr-x 2 root root  510200 2003-10-21 09:07 arm-linux-ld
-rwxr-xr-x 2 root root  317112 2003-10-21 09:07 arm-linux-nm
-rwxr-xr-x 1 root root  449624 2003-10-21 09:07 arm-linux-objcopy
-rwxr-xr-x 1 root root  470300 2003-10-21 09:07 arm-linux-objdump
-rwxr-xr-x 2 root root  284088 2003-10-21 09:07 arm-linux-ranlib
-rwxr-xr-x 1 root root  172960 2003-10-21 09:07 arm-linux-readelf
-rwxr-xr-x 1 root root  263232 2003-10-21 09:07 arm-linux-size
-rwxr-xr-x 1 root root  263148 2003-10-21 09:07 arm-linux-strings
-rwxr-xr-x 2 root root  449624 2003-10-21 09:07 arm-linux-strip
-rwxr-xr-x 1 root root    7385 2011-06-30 00:19 binencryptor
-rwxr-xr-x 1 root root   27126 2003-05-20 05:44 genext2fs
-rwxr-xr-x 1 root root    8960 2006-04-18 22:32 ucfinder

---

### Post by 213Wayne on 2011-11-16
hjghh?

---

### Post by carranty on 2011-11-16
Hi Wayne,

I'm installing it now myself, will let you know how it goes.

---

### Post by carranty on 2011-11-16
Ok so I've installed and it seems to be running ok on mine.  I created a fresh folder called 'Example', copied a simple c program into it and compiled it using your tool chain.  Here are the results

```
carranty@carranty-laptop:~/Example$ ls -l
total 12
-rw-r--r-- 1 carranty carranty 59 2011-11-16 12:25 hello.c
carranty@carranty-laptop:~/Example$ /usr/local/arm-linux/bin/arm-linux-gcc hello.c -o hellojj
carranty@carranty-laptop:~/Example$ ls -l
total 32
-rw-r--r-- 1 carranty carranty    59 2011-11-16 12:25 hello.c
-rwxr-xr-x 1 carranty carranty 11015 2011-11-16 12:25 hellojj
```As you can see, it creates an executable without any errors.  I can't actually run the file though
```
carranty@carranty-laptop:~/Example$ ./hellojj 
bash: ./hellojj: cannot execute binary file
```though that may be normal using this compiler (I'm not actually sure what arm-linux-gcc is supposed to do).  The point is I don't get an error message when I compile.  

The only thing I did that I don't see you mentioning is installing the libncurse5-dev package.  On page 59 of the documentation it says you must install it if using Ubuntu.  Did you install it?  It's not the quickest thing to install, I couldn't find it in the repositories so had to download it from here
[URL="http://packages.debian.org/squeeze/libncurses5-dev"]
http://packages.debian.org/squeeze/libncurses5-dev[/URL]

Note you'll need to install the      [libncurses5]("http://packages.debian.org/squeeze/libncurses5") and      [ncurses-bin]("http://packages.debian.org/squeeze/ncurses-bin") first, which can be found on the same page.  If you've done that already, I'm really not sure what more to suggest, I installed it exactly as you (and the documentation) described.

---

### Post by 213Wayne on 2011-11-16
After installing these things, must I restart my PC?

---

### Post by carranty on 2011-11-16
No need to restart the PC, though you may need to reinstall the arm-linux_3.3.2_V1.0_Build11080410.sh file.

---

### Post by 213Wayne on 2011-11-16
What happens when you run your program using the **make** command (as instructed in the documentation)?

---

### Post by carranty on 2011-11-16
Can you give me a page reference in the documentation?

---

### Post by 213Wayne on 2011-11-16
Page 25

---

### Post by carranty on 2011-11-16
Ok, so I copy the make file you uploaded into my 'Example folder',

```
carranty@carranty-laptop:~/Example$ ls -l
total 24
-rw-r--r-- 1 carranty carranty  59 2011-11-16 12:25 hello.c
-rw-r--r-- 1 carranty carranty 324 2011-11-16 13:17 Makefile
```and then I run the command make

```
carranty@carranty-laptop:~/Example$ make 
/usr/local/arm-linux/bin/arm-linux-gcc -o hello-release hello.c
/usr/local/arm-linux/bin/arm-linux-strip -s hello-release
/usr/local/arm-linux/bin/arm-linux-gcc -ggdb -o hello-debug hello.c

```which creates two new files

```
carranty@carranty-laptop:~/Example$ ls -l
total 60
-rw-r--r-- 1 carranty carranty    59 2011-11-16 12:25 hello.c
-rwxr-xr-x 1 carranty carranty 15835 2011-11-16 13:18 hello-debug
-rwxr-xr-x 1 carranty carranty  2492 2011-11-16 13:18 hello-release
-rw-r--r-- 1 carranty carranty   324 2011-11-16 13:17 Makefile
```exactly as the documentation describes.  Its weird, the warning about needing the libncurse5-dev package in Ubuntu is on page 59, so I'm not surprised you missed it.  They should really put that at the beginning!

---

### Post by 213Wayne on 2011-11-16
How do I check if those files were installed?

---

### Post by carranty on 2011-11-16
They weren't included in the sh file, so unless you've installed them manually they won't be.  Just to be sure though type 

```
dpkg --status libncurses5-dev
```

into a terminal, if it is it will output something similar to the below

```
carranty@carranty-laptop:/$ dpkg --status libncurses5-dev
Package: libncurses5-dev
Status: install ok installed
Priority: optional
Section: libdevel
```

---

### Post by carranty on 2011-11-16
I've just realised you can actually download it from the repositories, I couldn't find it because the documentation has a typo -- it calls it libncurse5-dev instead of libncurses5-dev -- I'm really starting to dislike this documentation!!

To install it type

```
sudo apt-get install libncurses5-dev
```into a terminal.

---

### Post by MG&amp;TL on 2011-11-16
Couple of things....

From what you've said I think you need to:

```
_sudo_ sh /home/wayne/armlinuxgcc.sh
```

But maybe you have.

ARM-gcc compiles executables for ARM architecture. If you have an ARM machine, you can test that.

Oh and if you want to search for a package like libncurses:

```
apt-cache search libncurses
```

---

### Post by 213Wayne on 2011-11-16
Me too!

wayne@ubuntu:~$ sudo apt-get install libncurses5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libncurses5-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by carranty on 2011-11-16
> **carranty said:**
> I've just realised you can actually download it from the repositories, I couldn't find it because the documentation has a typo -- it calls it libncurse5-dev instead of libncurses5-dev -- I'm really starting to dislike this documentation!!

To install it type

```
sudo apt-get install libncurses5-dev
```into a terminal.


Apologies, I don't think you can. apt-get can't seem to resolve the dependencies so I think you will have to install them manually.

---

### Post by carranty on 2011-11-16
> **213Wayne said:**
> Me too!

wayne@ubuntu:~$ sudo apt-get install libncurses5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libncurses5-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


Ok, I'm afraid I'm all out of ideas then.  Hopefully MG&TL can be more help. Sorry :(.

---

### Post by MG&amp;TL on 2011-11-16
To fix your arm-linux problem (I hope!):

```
sudo apt-get install gcc-arm-linux-gnueabi gcc-arm-linux-gnueabihf
```what other problems are there?

Why do you want to compile for ARM, anyway?

---

### Post by 213Wayne on 2011-11-16
Let's see. I want to program a  Moxa iopac 8020.

---

### Post by MG&amp;TL on 2011-11-16
Oh okay, cool. Are you having any issues at present? Sorry, never programmed a mobile, never tried.

---

### Post by 213Wayne on 2011-11-16
No. The only issue I have is this tool chain.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gcc-arm-linux-gnueabi

---

### Post by MG&amp;TL on 2011-11-16
Can you post:

```
apt-cache search gcc-arm-linux
```

---

### Post by 213Wayne on 2011-11-16
wayne@ubuntu:~$ apt -cache search gcc-arm-linux
The program 'apt' is currently not installed.  You can install it by typing:
sudo apt-get install openjdk-6-jdk

I/m installing the jdk

---

### Post by MG&amp;TL on 2011-11-16
NO, don't do that, it's unrelated. Lol, apt-get installing apt.

You want apt-cache, not apt(space)-cache. :D

---

### Post by 213Wayne on 2011-11-16
Okay. I'm a newbie.

We will have to pick this up tomorrow.

---

### Post by MG&amp;TL on 2011-11-16
It's no problem, I've done this myself a couple of times. You're not a newbie, doing this. :D Normally, you are right, you pass option with a -x.

Okay, see you tommorow.

---

### Post by carranty on 2011-11-16
> **213Wayne said:**
> No. The only issue I have is this tool chain.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gcc-arm-linux-gnueabi

MG&TL, for what its worth, I can't install these either (the OP and myself use the same version of Ubuntu, and have both installed the same tool chain using the same method, mine works, his doesn't).  Also when I type apt-cache search gcc-arm-linux I get nothing

```
carranty@carranty-laptop:~/Example$ apt-cache search gcc-arm-linux
carranty@carranty-laptop:~/Example$ 
```I really don't understand why it won't work for him, bash just can't seem to see the file, even though its clearly there.

When he types

*/usr/local/arm-linux/bin/arm-linux-gcc -o hello-release hello.c*

he gets the error message
```
/usr/local/arm-linux/bin/arm-linux-gcc: Command not found
```

when I type it it compiles hello.c into the executable hello-release.

---

### Post by MG&amp;TL on 2011-11-16
How bizarre. I have a default ubuntu install, yet:

```
michael@michael-laptop:~$ apt-cache search gcc-arm-linux
gcc-arm-linux-gnueabi - The GNU C compiler for armel architecture
gcc-arm-linux-gnueabihf - The GNU C compiler for armhf architecture
michael@michael-laptop:~$ 

```

:confused:


I think we need some 'bigger guns' i.e. some apt experts and some people who coded bash. I don't suppose you could post the install script's contents?

---

### Post by carranty on 2011-11-16
213Wayne, it probably is nothing to do with this but when you get back can you make sure the standard gcc command works.  I know you've already shown it's installed, but lets make sure bash can see it.  Just go into the folder you've stored the example file in (hello.c) and type

```
gcc hello.c -o hello
```

it should create an executable called 'hello'.

---

### Post by carranty on 2011-11-16
> **MG&TL said:**
> How bizarre. I have a default ubuntu install, yet:

```
michael@michael-laptop:~$ apt-cache search gcc-arm-linux
gcc-arm-linux-gnueabi - The GNU C compiler for armel architecture
gcc-arm-linux-gnueabihf - The GNU C compiler for armhf architecture
michael@michael-laptop:~$ 

```:confused:


I think we need some 'bigger guns' i.e. some apt experts and some people who coded bash. I don't suppose you could post the install script's contents?

What version are you running? We're both using 10.04.

213Wayne has already uploaded the install script to rapidshare and posted the link on this thread.  You can get it here

[https://rapidshare.com/files/1158748...ild11080410.sh]("https://rapidshare.com/files/1158748985/arm-linux_3.3.2_V1.0_Build11080410.sh")

and the manual here
[https://rapidshare.com/files/4262563...r_s_Manual.pdf]("https://rapidshare.com/files/4262563302/Moxa_C_Programmable_RTU_Controllers_User_s_Manual.pdf")

Note the manual has two seperate (yet mostly identical) installation instructions on pages 23 and 59.

I agree, bigger guns would be nice, I'm feeling rather out of my depth :confused:

EDIT : I used the wrong link in the above, I've fixed it.

---

### Post by MG&amp;TL on 2011-11-16
> **carranty said:**
> What version are you running? We're both using 10.04.

213Wayne has already uploaded the install script to rapidshare and posted the link on this thread.  You can get it here

[https://rapidshare.com/files/1158748...ild11080410.sh]("https://rapidshare.com/files/1158748985/arm-linux_3.3.2_V1.0_Build11080410.sh")

and the manual here
[https://rapidshare.com/files/4262563...r_s_Manual.pdf]("https://rapidshare.com/files/4262563302/Moxa_C_Programmable_RTU_Controllers_User_s_Manual.pdf")

Note the manual has two seperate (yet mostly identical) installation instructions on pages 23 and 59.

I agree, bigger guns would be nice, I'm feeling rather out of my depth :confused:

EDIT : I used the wrong link in the above, I've fixed it.

Yeah, sorry, *was* on slow internet, not now. :D

gcc (normal) is a good idea. 

Ah. I'm using 11.10. That would be the difference. 12.04 is meant to be compatible with tablets, etc, so 11.10 has many of the repos.

---

### Post by MG&amp;TL on 2011-11-16
Does this help in some way?

[http://www.aleph1.co.uk/oldsite/armlinux//docs/toolchain/toolchHOWTO.pdf]("http://www.aleph1.co.uk/oldsite/armlinux//docs/toolchain/toolchHOWTO.pdf")

Although be careful with your sources.list.

---

### Post by matt_symes on 2011-11-16
Hi

Is this a 64-bit install of Ubuntu ? Do you have the 32-bit libs installed and are they required for gcc-arm ?

Please post the output of

```
uname -a
``` 

You will get the same not found message if gcc-arm cannot load a library it needs as well as if it cannot find the executable.

```
matthew@matthew-laptop:~/arm_compilation$ ldd !$
ldd /usr/local/arm-linux/bin/arm-linux-gcc
        linux-gate.so.1 =>  (0xf774f000)
        libc.so.6 => /lib32/libc.so.6 (0xf75cf000)
        /lib/ld-linux.so.2 (0xf7750000)
matthew@matthew-laptop:~/arm_compilation$
```

Kind regards

---

### Post by carranty on 2011-11-16
I think I may have sorted it. We haven't examined the PATH variable yet. Can you type 

```
echo $PATH
```into a terminal.  If you've rebooted your computer since installing the script it should look (*)  like this

```
carranty@carranty-laptop:~/Example$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```If it doesn't, please paste

```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```into the terminal.  This is a list of all the places bash will look for a command you type.  We now need to add to it our /usr/local/arm-linux/bin directory, because it is in this directory the arm-linux-gcc executable is in.  Do this by typing

```

PATH=$PATH:/usr/local/arm-linux/bin
```into the terminal.

To test whether this has worked type

```
arm-linux-gcc
```
into the terminal and hit return.  It'll probably give the error

```
carranty@carranty-laptop:~/Example$ arm-linux-gcc
arm-linux-gcc: no input files
```

This is good news. it means bash is now able to find the arm-linux-gcc command!

Finally, go into whatever folder you have stored your example file in (any file with a '.c' extension will do) and type

```
arm-linux-gcc -o example.c example
```If that creates an executable called example, you're sorted.  Just DON'T use that make file, at least until we know the above works. 



* Mine did not look at all like this after installation, the documentation uses the wrong syntax when it explains how to rename your PATH file, and it prevents bash from finding the arm-linux-gcc file

---

### Post by matt_symes on 2011-11-16
Hi

The make file uses the full path.

```

PREFIXPATH=/usr/local/arm-linux/bin
CC=$(PREFIXPATH)/arm-linux-gcc
STRIP=$(PREFIXPATH)/arm-linux-strip
NAME=hello

all: release debug

clean:
        rm -f $(NAME)-release $(NAME)-debug

release:        $(NAME).c
        $(CC) -o $(NAME)-release $(NAME).c
        $(STRIP) -s $(NAME)-release

debug:          $(NAME).c
        $(CC) -ggdb -o $(NAME)-debug $(NAME).c
```

Check for a 64 bit install without 32 bit libs.

Kind regards

---

### Post by 213Wayne on 2011-11-17
HI Carranty.

I have altered the path:
wayne@ubuntu:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
wayne@ubuntu:~$ PATH=$PATH:/usr/local/arm-linux/bin
wayne@ubuntu:~$ arm-linux-gcc
bash: /usr/local/arm-linux/bin/arm-linux-gcc: No such file or directory
wayne@ubuntu:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/arm-linux/bin


wayne@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 16:11:24 UTC 2011 x86_64 GNU/Linux


I do not understand the last comment posted about 64 bit and 32 libs:confused:

---

### Post by 213Wayne on 2011-11-17
wayne@ubuntu:~$ arm_compilation$ ldd !$
arm_compilation$ ldd -a
arm_compilation$: command not found

---

### Post by 213Wayne on 2011-11-17
wayne@ubuntu:~$ gcc hello.c -o hello works

---

### Post by 213Wayne on 2011-11-17
wayne@ubuntu:~$ apt-cache search gcc-arm-linux
wayne@ubuntu:~$ 

nothing.

---

### Post by 213Wayne on 2011-11-17
So much has happened while I was away.

---

### Post by 213Wayne on 2011-11-17
Will the hardware (laptop specs) affect tool chain?

---

### Post by matt_symes on 2011-11-17
Hi

> Linux ubuntu 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 16:11:24 UTC 2011 **x86_64** GNU/Linux

You are using 64-bit Ubuntu. 

You may not have the 32-bit libraries installed and this may be your problem.

```
sudo apt-get install ia32-libs
```
> 
wayne@ubuntu:~$ arm_compilation$ ldd !$
arm_compilation$ ldd -a
arm_compilation$: command not found

Let me explain those commands. !$ will repeat the parameters of the last command for you.

Take a look at this.```


matthew@matthew-Aspire-7540:~$ pwd
/home/matthew
matthew@matthew-Aspire-7540:~$ mkdir test
matthew@matthew-Aspire-7540:~$ cd !$
cd test
matthew@matthew-Aspire-7540:~/test$ pwd
/home/matthew/test
matthew@matthew-Aspire-7540:~/test$ 
```

Not so useful if your last parameter was just test as above but very useful if your last parameter was /path/to/long/filename or any other long parameter.

The ldd command will tell you what libraries an executable requires to run.

```

matthew@matthew-Aspire-7540:~/test$ ldd /bin/gzip 
        linux-gate.so.1 =>  (0x00a45000)
        librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0x00950000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x00110000)
        libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0x0045f000)
        /lib/ld-linux.so.2 (0x00736000)
matthew@matthew-Aspire-7540:~/test$
```

Kind regards

---

### Post by 213Wayne on 2011-11-17
This is a bit off topic.
If I upload the executable file (through ftp) that was generated by the gcc hello.c -hello, How can I run it from the file from the device?

---

### Post by carranty on 2011-11-17
Ok, so it doesn't look like it was your PATH.  Just to humour me, can you type

```
cd /usr/local/arm-linux/bin/

ls -l arm-linux-gcc

file arm-linux-gcc

./arm-linux-gcc

```and print the output of each. 

Matt had a good idea about the 32 bit libraries but both you and I are both running 64 bit versions of Ubuntu and it worked on mine (the output of uname -a is how we know your running 64bit).  I don't see why my computer would use different libraries to yours, we're both running 10.04.

> I do not understand the last comment posted about 64 bit and 32 libs:confused:I don't understand that one either.

EDIT : Matt posted while I was writing.  Perhaps I did install the 32 bit libraries at some point in the past, it's a good idea.

---

### Post by 213Wayne on 2011-11-17
wayne@ubuntu:/tmp/example$ cd hello
wayne@ubuntu:/tmp/example/hello$ make
/usr/local/arm-linux/bin/arm-linux-gcc -o hello-release hello.c
/usr/local/arm-linux/bin/arm-linux-strip -s hello-release
/usr/local/arm-linux/bin/arm-linux-gcc -ggdb -o hello-debug hello.c

It's working:shock:

---

### Post by carranty on 2011-11-17
> **213Wayne said:**
> It's working:shock:
Great!! :guitar:

Thanks Matt!, we've been working on this for days!  Can you please explain how you knew from

```
matthew@matthew-laptop:~/arm_compilation$ ldd !$
 ldd /usr/local/arm-linux/bin/arm-linux-gcc
 linux-gate.so.1 =>  (0xf774f000) 
        libc.so.6 => /lib32/libc.so.6 (0xf75cf000)
 /lib/ld-linux.so.2 (0xf7750000)
```

that the package  ia32-libs needed installing.  I wouldn't have been able to tell that even if I'd known about the ldd command, I'd like to learn how :).

---

### Post by matt_symes on 2011-11-17
Hi
[FONT=monospace]
[/FONT]> libc.so.6 => /lib32/libc.so.6 libc.so.6 is pointing to /lib32/libc.so.6; the 32-bit C library. /lib32/libc.so.6 is actually a symbolic link to the actual libc library it will use so you can never be 100% sure unless you check what it points to.
```

matthew@matthew-Aspire-7540:/**lib32**$ ls -l libc.so.6 
lrwxrwxrwx 1 root root 14 May 24 14:11 libc.so.6 -> libc-2.11.1.so
matthew@matthew-Aspire-7540:/**lib32**$ file libc-2.11.1.so
libc-2.11.1.so: **ELF 32-bit LSB shared object**, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), BuildID[sha1]=0x8dfc69b7961b85c40d48e1a8c1e113691f83eb28, for GNU/Linux 2.6.15, stripped
matthew@matthew-Aspire-7540:/lib32$ 
```[FONT=monospace]
[/FONT]Plus the fact, in the past, this has had me pulling my hair out as well.

Once you get that *lightbulb* moment, you don't tend to forget it :)

Kind regards

---

### Post by MG&amp;TL on 2011-11-17
> **213Wayne said:**
> This is a bit off topic.
If I upload the executable file (through ftp) that was generated by the gcc hello.c -hello, How can I run it from the file from the device?


You can't, that was compiled for 64-bits, your phone runs on ARM. That's why you needed arm-gcc.

---

### Post by 213Wayne on 2011-11-17
Thanks.

Hopefully I can move forward programming my device without any hiccups.

---

### Post by 213Wayne on 2011-11-17
wayne@ubuntu:~$ cd /usr/local/arm-linux/bin/
wayne@ubuntu:/usr/local/arm-linux/bin$ ls -l arm-linux-gcc
-rwxr-xr-x 2 root root 81812 2003-10-21 09:07 arm-linux-gcc
wayne@ubuntu:/usr/local/arm-linux/bin$ ./arm-linux-gcc
arm-linux-gcc: no input files

---

### Post by MG&amp;TL on 2011-11-17
That's good, it means it's there.

---

