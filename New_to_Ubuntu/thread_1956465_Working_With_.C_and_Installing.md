---
title: "Working With .C and Installing"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by saponempotenti on 2012-04-11
I have downloaded Crafty (chess program).  I downloaded it as a ZIP file and have unpacked it with the terminal.  I now have the unpacked folder of crafty on terminal.  There are a bunch of .c files along with some.h files.  Is there some sort of compile command that will work?  I have been researching for a long time and have not found an actual command that works.

Terminal -
josh@josh-VirtualBox:~/Desktop$ ls
crafty-23.4  crafty-23.4.zip
josh@josh-VirtualBox:~/Desktop$ cd crafty-23.4
josh@josh-VirtualBox:~/Desktop/crafty-23.4$ ls
analyze.c   data.h      evtest.c    lock.h       probe.c     test.c
annotate.c  drawn.c     hash.c      main.c       quiesce.c   thread.c
attacks.c   edit.c      init.c      make.c       repeat.c    time.c
bench.c     egtb.cpp    inline32.h  Makefile     resign.c    unmake.c
book.c      epd.c       inline64.h  Makefile.xp  root.c      utility.c
boolean.c   epddefs.h   input.c     movgen.c     search.c    validate.c
chess.h     epdglue.c   interupt.c  next.c       setboard.c  vcinline.h
crafty.c    epdglue.h   iterate.c   option.c     speak
crafty.hlp  epd.h       killer.c    output.c     swap.c
data.c      evaluate.c  learn.c     ponder.c     tbdecode.h
josh@josh-VirtualBox:~/Desktop/crafty-23.4$

---

### Post by bouncingwilf on 2012-04-11
With packages such as this, the usual trinity of commands to compile and install the program are:

./configure
make
sudo make install

There is usually a readme file to give you these instructions (and any make options) but I can't see one in your list. You will need to install the complier packages if you haven't already done so (use : sudo apt-get install build-essentials to install)


Bouncingwilf

---

### Post by saponempotenti on 2012-04-11
Not sure what this does - "apt-get install build-essentials to install" I ran this and got the below.

josh@josh-VirtualBox:~$ sudo apt-get install build-essentials to install
[sudo] password for josh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essentials
E: Unable to locate package to
E: Unable to locate package install
josh@josh-VirtualBox:~$ 

As you can see the above problem kind of explains itself.. I understand why it did not work and here comes the next question..

So my problem is not just that there is no instructions, but I am  unaware of how this process works and why it works.  I understand that  binary code needs to be compiled before it can be ran and executed.  Why  am I running the code above?  Is there a package I did not have that  allows me to compile?

------------------------------------------------------------------------------------------------------------------------------------------------------------

My understanding is the following -  (please correct me where needed! Thanks!)
There are binary code in txt files called .c files, that I downloaded from a repository.
1) A command takes all of the txt or .c files and gives them life by compiling them
2) Next, there is a command to bring them all together into something a windows user would best describe as the application file.
3) You execute the application file (which I understand would be called something else)

---

### Post by anewguy on 2012-04-11
First, after the obvious errors in your apt-get, did you rerun as:

sudo apt-get install build-essential

You really must do this before you'll be able to use the compilers.


Second, have you seen this forum, and in particular this post:

[http://www.chessbanter.com/rec-games-chess-computer-computer/2906-crafty-compiling-how-linux.html]("http://www.chessbanter.com/rec-games-chess-computer-computer/2906-crafty-compiling-how-linux.html")

It should cover what you need to know.

Dave ;)

---

### Post by saponempotenti on 2012-04-11
Thanks anewguy/dave! Thats a great forum post on installing crafty.  Can already tell its helping my general understanding of the terminal. :D

It is also nice to know that Ubuntu does not come with a compiler which was my initial thought.

---

### Post by saponempotenti on 2012-04-11
So now finding out that a compiler is needed and running  "sudo apt-get install build-essential" on the terminal, this is what comes up. (the end of it)

Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-1build1) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libstdc++6-4.6-dev (4.6.1-9ubuntu3) ...
Setting up g++-4.6 (4.6.1-9ubuntu3) ...
Setting up g++ (4:4.6.1-2ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu1) ...

Am I ok to assume that it is already working and installed? haha

I will be back in 10 hours to do some extensive research/learning,  will not be able to respond until

---

### Post by anewguy on 2012-04-11
> **saponempotenti said:**
> So now finding out that a compiler is needed and running  "sudo apt-get install build-essential" on the terminal, this is what comes up. (the end of it)

Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-1build1) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libstdc++6-4.6-dev (4.6.1-9ubuntu3) ...
Setting up g++-4.6 (4.6.1-9ubuntu3) ...
Setting up g++ (4:4.6.1-2ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu1) ...

Am I ok to assume that it is already working and installed? haha

I will be back in 10 hours to do some extensive research/learning,  will not be able to respond until

Yep - looks like it installed the build-essential package as requested in the apt-get.

Build-essential includes the compilers and all kinds of other things really needed to compile in ubuntu.  Anyone who plans on compiling anything, running make to install something (which is a enhanced "wrapper" to compile the application), etc., needs to install build-essential first.

Let us know how it goes!

Dave ;)

---

### Post by saponempotenti on 2012-04-12
Still having some problems, all minor and I am fixing most of them.  I guess Crafty chess needed a lot of other packages to run.  (not a very good program for beginners to broaden there experience with)  I am now reading William Shotts book "The linux Command Line: A Complete Introduction" to learn more about terminal.  The book was recommended to me on one of my other threads.  I will continue to let you know what is going on, and about my downloading abilities! Thanks

---

### Post by anewguy on 2012-04-13
I *think* this only works with packages in repositories instead of just a downloaded .deb file, but just so you know:

- normally the dependencies are handled by the package manager, but sometimes something still comes up missing.  In that case you can do the following to get the dependencies:

sudo apt-get build-dep 


Dave ;)

---

### Post by saponempotenti on 2012-04-13
I *think* this only works with packages in repositories instead of just a downloaded .deb file, but just so you know:

- normally the dependencies are handled by the package manager, but  sometimes something still comes up missing.  In that case you can do the  following to get the dependencies:





.deb is a debian file is it not?  Why is Ubuntu using .deb files with some of its packages? And why do I need to run "sudo apt-get build-dep"?  Does that give me another package manger like program that translates Debian to Ubuntu file wise?

Also encounter this problem when running it -

josh@josh-VirtualBox:~$ sudo apt-get build-dep 
[sudo] password for josh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Must specify at least one package to check builddeps for
josh@josh-VirtualBox:~$

---

### Post by anewguy on 2012-04-13
I guess I should have added it to the sample - yes, build-dep requires a package name, and it will try to load all of the dependencies for that package:

sudo apt-get build-dep package-name


If a package is not in the repositories - as an example if you go into synaptic package manager and it's not there, so you manually download a .deb file, my understanding is that the package manager does not know how to determine the dependencies.  The .deb file is just a program and associated things like documentation, etc., made into a package the the package manager can understand to install - in debian distribution format.

---

### Post by saponempotenti on 2012-04-14
oh ok, I understand what you are saying.  Thanks for being patient with me :)
Still reading that book, getting further everyday.  It helps because it explains the semantics behind the syntax of shell commands.  Helps you get in the head of your Linux.

---

### Post by saponempotenti on 2012-04-17
What is this? grrrr  I have tried going through the man page on sudo - I am not able to understand anything it is talking about :(  There is just one problem after another trying to install crafty.  I have taken computer science classes and programming, but still cannot figure this out.  I work at bestbuy selling computers all day talking to coworkers about computers.. and yet I have this much trouble with a simple install.  Is this kind of trouble normal or am I just really stupid? : /

I am reading a book on shell.. is this not the basic idea to go into the root folder?  I know "cd /" is the main command.. but I was able to move a file into the /root and wanted to actually use a "ls" inside of it.  Seems impossible though. 

josh@josh-VirtualBox:/$ cd /root
bash: cd: /root: Permission denied
josh@josh-VirtualBox:/$ sudo cd /root
sudo: cd: command not found
josh@josh-VirtualBox:/$ sudo | cd /root
bash: cd: /root: Permission denied
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-g groupname|#gid] [-p prompt] [-u user name|#uid]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U user name] [-u user name|#uid] [-g
            groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user name|#uid] [-g
            groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user name|#uid] file ...
josh@josh-VirtualBox:/$



p.s How long on average does it take someone to get used to  Linux?  I am trying to learn(spending 8 hours a day on average besides work days), and not  making a lot of progress.  It seems that every time I try to download  and install something I run into a problem. (purposely trying to learn how to use repositories(download/compile/install) on the terminal)  Is Linux something that  needs to be taught in a classroom environment?  I realize it is possible  to teach yourself(most people do), but after reading several books on basic terminal  use, I am still encountering problems/glitches rapidly.  Is that also  normal? And will I really get that much better with time?

Every time I try to attempt literally anything I run into a problem...

josh@josh-VirtualBox:/usr/share/games$ sudo rm -r supertux2
josh@josh-VirtualBox:/usr/share/games$ ls
gbrainy (no supertux2)
josh@josh-VirtualBox:/usr/share/games$ clear

josh@josh-VirtualBox:/usr/share/games$ sudo apt-get install supertux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
supertux is already the newest version.

---

### Post by oldos2er on 2012-04-17
/root is root's (the administrator) home folder. If you want to get to the root directory of the file system, you'd run **cd /**

It's not clear to me what exactly you're trying to do.

---

### Post by jerome1232 on 2012-04-17
First in response to your query about Ubuntu using Debian packages, each release of Ubuntu is based on a snapshot of Debian, so Ubuntu is a Debian based flavor of Linux.

Secondly installing from source is not the ideal method of installing programs, without a good knowledge of the way packages work etc.. this program is in the Ubuntu repo's, search for it in the package manager, or install with apt-get.

```
sudo apt-get install crafty
```

third, I forget the reason but cd as sudo doesn't work, if you wanted to get into root's home folder (which is what /root is) you'd have to get a root shell, then cd into it. But why are you trying to get into root's home folder? There's not much purpose to that.

an example of cd'ing into a folder which your user doesn't have permision to browse would be

```
sudo -i
cd /root
ls
exit
```

---

### Post by saponempotenti on 2012-04-17
To ann - I am not sure what I am doing either.  My main goal is to learn the terminal/shell as quickly and productively as possible.  I am in a pen testing course that uses backtrack, and since I did not know anything about Linux, I started with Ubuntu.  The goal is to switch over to backtrack with a decent skill set.  So I play with the terminal a lot and run into problems left and right :/

---

### Post by saponempotenti on 2012-04-17
**Responses are in bold :)**

> **jerome1232 said:**
> First in response to your query about Ubuntu using Debian packages, each release of Ubuntu is based on a snapshot of Debian, so Ubuntu is a Debian based flavor of Linux. **(thanks, did not know that!)**

Secondly installing from source is not the ideal method of installing programs, without a good knowledge of the way packages work etc.. this program is in the Ubuntu repo's, search for it in the package manager, or install with apt-get.
**(I used apt-get and got the zipped up files. Unzipped them and got a bunch of .c files.  Used ./configure which gives me an error message, then realize there is a makefile within the .c files.  Used "make linux" which is the command they say to use, and get a huuuuge list of error files.)**

```
sudo apt-get install crafty
```third, I forget the reason but cd as sudo doesn't work, if you wanted to get into root's home folder (which is what /root is) you'd have to get a root shell, then cd into it. But why are you trying to get into root's home folder? There's not much purpose to that.
**(was just messing around trying to see if "cd /" == "cd root")**
an example of cd'ing into a folder which your user doesn't have permision to browse would be

```
sudo -i
cd /root
ls
exit
```

---

### Post by oldos2er on 2012-04-17
> **saponempotenti said:**
>  My main goal is to learn the terminal/shell as quickly and productively as possible. 

Click the "I want to tell you..." link in my sig, it's a PDF about learning the command line that may help you.

---

### Post by saponempotenti on 2012-04-17
I am currently using that pdf :)  I am around pg 200 and it is very helpful.  It  was nice in the beginning when it was teaching how to use cd and mkdir, and the easier navigating simple commands.  I am at the point now that when I follow his examples I run into glitches to frequently.  I can fix them usually, just requires a lot of time and is quite frustrating.

---

### Post by jerome1232 on 2012-04-17
That is a very nice pdf! I'll be taking a look some of it myself.

---

### Post by saponempotenti on 2012-04-17
Do you think that book covers enough to allow a user to use backtrack? Just don't want to end up like this guy -> ](*,)

---

### Post by MG&amp;TL on 2012-04-17
The reason "sudo cd" does not work is that *cd* is not an actual program, but a module built into the shell (terminal is a graphical wrpper for a shell). When sudo tries to execute cd, it can't find it.

As for the OP-try not to make the mistake of mixing package manager and other utillity commands-you should not try to remove system files (usr/share/games/supertux in this case) with rm-unless you put them there yourself. Otherwise apt gets confused and you put more effort in. If you want to try out moving and editing files via CLI, muck about with some files in your homefolder. :)

BTW-the reason supertux didn't appear in /usr/share/games/ is because it was probably installed somewhere else (/usr/games springs to mind). For some reason, there is multiple places you can put things in a UNIX filesystem. I still think there should be a standard. :(

I quite like [LinuxCommand.org]("http://ubuntuforums.org/LinuxCommand.org") as a site for bash-it's what got me started-don't worry, things will get easier with time.

I would say that book allows you to get *started* with backtrack-it's a huge distribution with lots of specialist tools for various applications. Not an easy thing to use properly, but you should be able to get by eventually.

---

### Post by jerome1232 on 2012-04-17
> **saponempotenti said:**
> Do you think that book covers enough to allow a user to use backtrack? Just don't want to end up like this guy -> ](*,)

When working with computers, becoming that guy is inevitable, the more advanced you are, the more you do it.

---

### Post by oldos2er on 2012-04-17
> **saponempotenti said:**
>   I am at the point now that when I follow his examples I run into glitches to frequently.  I can fix them usually, just requires a lot of time and is quite frustrating.

Well, I would just encourage you to keep asking questions as you have been. I know nothing about Backtrack, but have you checked out the forums there?

---

### Post by saponempotenti on 2012-04-18
> **MG&TL said:**
> The reason "sudo cd" does not work is that *cd* is not an actual program, but a module built into the shell (terminal is a graphical wrpper for a shell). When sudo tries to execute cd, it can't find it.

As for the OP-try not to make the mistake of mixing package manager and other utillity commands-you should not try to remove system files (usr/share/games/supertux in this case) with rm-unless you put them there yourself. Otherwise apt gets confused and you put more effort in. If you want to try out moving and editing files via CLI, muck about with some files in your homefolder. :)

BTW-the reason supertux didn't appear in /usr/share/games/ is because it was probably installed somewhere else (/usr/games springs to mind). For some reason, there is multiple places you can put things in a UNIX filesystem. I still think there should be a standard. :(

I quite like [LinuxCommand.org]("http://ubuntuforums.org/LinuxCommand.org") as a site for bash-it's what got me started-don't worry, things will get easier with time.

I would say that book allows you to get *started* with backtrack-it's a huge distribution with lots of specialist tools for various applications. Not an easy thing to use properly, but you should be able to get by eventually.

That explains a lot.  I remember the book saying the cd was built in the shell, makes sense now.  And using "locate supertux*" I was able to find out that it is literally all over the place.  I dis-installed correctly with a gui.  LinuxCommand.org looks like a nice learning tool, bookmarked it!  And the funny thing is, when I was growing up I got familiar with a lot of backtracks tools with windows, I am just now realizing that Linux is really what I need in the long run :) And you may be happy to know that I installed it with minimum problems, only thing I have to do now is get the resolution right.

---

### Post by saponempotenti on 2012-04-18
> **jerome1232 said:**
> When working with computers, becoming that guy is inevitable, the more advanced you are, the more you do it.


The more advanced I am the more I run into a brick wall?  I know the brick wall with programming is not that bad, you find a lot of problems and fix them quickly.  I just want the Linux problems to show up a little less, and be fixed a lot easier, but I guess that is what you get a week into learning shell.

---

### Post by saponempotenti on 2012-04-18
> **oldos2er said:**
> Well, I would just encourage you to keep asking questions as you have been. I know nothing about Backtrack, but have you checked out the forums there?


Backtrack is a distribution that focuses on Internet security.  It is used by professional PEN testers as well as hackers alike.  It is preloaded with every great hacking program you could ever imagine!

I have checked out the backtrack forums.  I am sticking with Ubuntu forums becasue there are a lot more people like you that are quick to help and polite :)  If I have specific questions on backtrack programs such as nmap, I will stick a question over there, but for now I really like it here. :p

---

### Post by anewguy on 2012-04-18
> **saponempotenti said:**
> Well the idea is to compile that unzipped folder you have. "./configure" is the command. After compiling it you should get a makefile.  Run the "make" command to make an executable like file.  And that should be it.  You might want to take some notes from others sources because I have still not been able to do this. (been really busy with other problems)

Technically speaking, configure sets up the make file after seeing what types of compilation tools, dependencies, etc., options your system supports.  Make does the compilation, using the make file and creates the executable.   Make install jumps into the make file at the install section and does what is specified there - usually copying files, etc., into the appropriate folders.

Dave ;)

---

### Post by saponempotenti on 2012-04-18
^ What I meant to say! haha

---

### Post by saponempotenti on 2012-05-20
This entire time I thought that synaptic package manager was a terminal based background program.. did not know it had its on powerful gui :)

---

### Post by gordintoronto on 2012-05-20
I think you have not said what version of Ubuntu you are using? By now, you know that the right way to install Crafty is by using Synaptic Package Manager, but that doesn't help you learn the Terminal.

Here's one of thousands of places which might help: [http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

But mostly, I depend on Google.

---

### Post by saponempotenti on 2012-05-22
> **gordintoronto said:**
> I think you have not said what version of Ubuntu you are using? By now, you know that the right way to install Crafty is by using Synaptic Package Manager, but that doesn't help you learn the Terminal.

Here's one of thousands of places which might help: [http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

But mostly, I depend on Google.

Thanks for the link! And synaptic is a great program I did not fully give credit to in the beginning.

---

### Post by roelforg on 2012-05-22
I saw that there's already a makefile,
just run:
```

make

```
and if any errors occurr, you can usually see what dependencies are missing.

---

### Post by saponempotenti on 2012-05-22
Still having problems manually installing! So first off let me just say that synaptic and ubuntu software does not have aircrack-ng.  I downloaded the tar.gz, moved it to usr/bin/ , extracted, deleted the aircrack-ng-tar.gz , cd to the aircrack folder, and ran "sudo make" and got  the following -


```
josh@josh-Charles-E420:/usr/bin$ cd aircrack-ng-1.1/
josh@josh-Charles-E420:/usr/bin/aircrack-ng-1.1$ ls
AUTHORS    common.mak  INSTALLING  LICENSE.OpenSSL  manpages  patchchk  README   src   VERSION
ChangeLog  evalrev     LICENSE     Makefile         packages  patches   scripts  test
josh@josh-Charles-E420:/usr/bin/aircrack-ng-1.1$ sudo make
make -C src all
make[1]: Entering directory `/usr/bin/aircrack-ng-1.1/src'
make -C osdep
make[2]: Entering directory `/usr/bin/aircrack-ng-1.1/src/osdep'
Building for Linux
make[3]: Entering directory `/usr/bin/aircrack-ng-1.1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux.o linux.c
linux.c: In function ‘is_ndiswrapper’:
linux.c:165:17: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘linux_set_rate’:
linux.c:334:22: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘linux_set_channel’:
linux.c:807:22: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘linux_set_freq’:
linux.c:896:22: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘set_monitor’:
linux.c:1022:22: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘do_linux_open’:
linux.c:1366:12: error: variable ‘unused_str’ set but not used [-Werror=unused-but-set-variable]
linux.c:1352:15: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘get_battery_state’:
linux.c:1982:35: error: variable ‘current’ set but not used [-Werror=unused-but-set-variable]
cc1: all warnings being treated as errors
make[3]: *** [linux.o] Error 1
make[3]: Leaving directory `/usr/bin/aircrack-ng-1.1/src/osdep'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/bin/aircrack-ng-1.1/src/osdep'
make[1]: *** [osd] Error 2
make[1]: Leaving directory `/usr/bin/aircrack-ng-1.1/src'
make: *** [all] Error 2
josh@josh-Charles-E420:/usr/bin/aircrack-ng-1.1$ 
```

anyone know what is going on? Or why this is not working? -Thanks

---

### Post by roelforg on 2012-05-23
> **saponempotenti said:**
> Still having problems manually installing! So first off let me just say that synaptic and ubuntu software does not have aircrack-ng.  I downloaded the tar.gz, moved it to usr/bin/ , extracted, deleted the aircrack-ng-tar.gz , cd to the aircrack folder, and ran "sudo make" and got  the following -


```
josh@josh-Charles-E420:/usr/bin$ cd aircrack-ng-1.1/
josh@josh-Charles-E420:/usr/bin/aircrack-ng-1.1$ ls
AUTHORS    common.mak  INSTALLING  LICENSE.OpenSSL  manpages  patchchk  README   src   VERSION
ChangeLog  evalrev     LICENSE     Makefile         packages  patches   scripts  test
josh@josh-Charles-E420:/usr/bin/aircrack-ng-1.1$ sudo make
make -C src all
make[1]: Entering directory `/usr/bin/aircrack-ng-1.1/src'
make -C osdep
make[2]: Entering directory `/usr/bin/aircrack-ng-1.1/src/osdep'
Building for Linux
make[3]: Entering directory `/usr/bin/aircrack-ng-1.1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux.o linux.c
linux.c: In function ‘is_ndiswrapper’:
linux.c:165:17: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘linux_set_rate’:
linux.c:334:22: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘linux_set_channel’:
linux.c:807:22: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘linux_set_freq’:
linux.c:896:22: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘set_monitor’:
linux.c:1022:22: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘do_linux_open’:
linux.c:1366:12: error: variable ‘unused_str’ set but not used [-Werror=unused-but-set-variable]
linux.c:1352:15: error: variable ‘unused’ set but not used [-Werror=unused-but-set-variable]
linux.c: In function ‘get_battery_state’:
linux.c:1982:35: error: variable ‘current’ set but not used [-Werror=unused-but-set-variable]
cc1: all warnings being treated as errors
make[3]: *** [linux.o] Error 1
make[3]: Leaving directory `/usr/bin/aircrack-ng-1.1/src/osdep'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/bin/aircrack-ng-1.1/src/osdep'
make[1]: *** [osd] Error 2
make[1]: Leaving directory `/usr/bin/aircrack-ng-1.1/src'
make: *** [all] Error 2
josh@josh-Charles-E420:/usr/bin/aircrack-ng-1.1$ 
```

anyone know what is going on? Or why this is not working? -Thanks

You'll need to kill that warn.

But aircrack-ng installed from the repos on my system fine.

---

### Post by saponempotenti on 2012-05-23
> **roelforg said:**
> You'll need to kill that warn.

But aircrack-ng installed from the repos on my system fine.

How do I kill the warning?

---

