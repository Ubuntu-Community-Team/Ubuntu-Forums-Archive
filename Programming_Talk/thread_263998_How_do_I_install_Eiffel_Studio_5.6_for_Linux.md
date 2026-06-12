---
title: "How do I install Eiffel Studio 5.6 for Linux?"
date: 2006-09-24
forum: Programming Talk
---

### Post by aqwabawks on 2006-09-24
One of my programming classes in the Winter term requires the use of Eiffel Studio to program in the Eiffel programming language.  I've found the install for Windows to be a breeze (with the MSI package), but however am running into some difficulties installing it under Dapper.

I've recently re-installed Ubuntu Linux and would like to find a solution to my dilemma prior to re-downloading the files from the Eiffel website.  The Windows version does work, however I am required by my school's Computer Science department to ensure my programs work under a Linux environment, and I genuinely prefer doing my coding in Linux.

I've followed the instructions that are contained within the tar file that is downloaded from the Eiffel website, I managed to get it to compile, but then it mentions that in a shell I should enter the following commands:

export ISE_EIFFEL=/usr/local/Eiffel56
export ISE_PLATFORM=linux-x86
export PATH=$PATH:$ISE_EIFFEL/studio/spec/$ISE_PLATFORM/bin

Source: [http://docs.eiffel.com/eiffelstudio/installation/studio56/060_linux.html](http://docs.eiffel.com/eiffelstudio/installation/studio56/060_linux.html)

This should update my environment variables and allow me to run Eiffel Studio (or the compiler ec) by simply entering it into the Run Application window or anywhere in a terminal.

Each time I've tried to install it, the only times I've managed to run it is when I am in the exact directory of the executable file for eiffel studio.  I'm trying to figure out what keeps preventing from installing it and getting it to work properly.

Any help would be greatly appreciated.

---

### Post by aqwabawks on 2006-10-19
Is there no one who can help me out with this?

---

### Post by sas917 on 2006-11-06
Hi, have you entered the export commands into your .bashrc file in your home directory? They must be there for the env. variables to be set each time you login/use a terminal.

To check type the following command:

env | grep ISE

and you should see something like this (my machine shown - your paths may be different):


user1@server2:~$ env | grep ISE
ISE_EIFFEL=/home/eiffel/Eiffel56
ISE_PLATFORM=linux-x86


and you can check that the PATH has been set correctly by running this command and making sure the eiffel folder is listed:

user1@server2:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/home/eiffel/Eiffel56/studio/spec/linux-x86/bin

Now you can type estudio from anywhere.

Hope this helps.

---

### Post by sas917 on 2006-11-06
By the way, I could not get the examples in Eiffel 5.6 to compile under my ubuntu (6.06 LTS). Did you compile them successfully?

I get the following error:

/usr/include/time.h:184: error: conflicting types for &#8216;time&#8217;
/home/eiffel/Eiffel56/precomp/spec/linux-x86/vision2/EIFGEN/W_code/C29/ev932.c:363: error: previous implicit declaration of &#8216;time&#8217; was here
make[1]: *** [big_file_C29_c.o] Error 1
make[1]: Leaving directory `/home/eiffel/Eiffel56/precomp/spec/linux-x86/vision2/EIFGEN/W_code/C29'
make: *** [C29/Cobj29.o] Error 2

---

### Post by thepopasmurf on 2007-12-22
I just eiffel running just a few minutes ago.
What I did was I got **smarteiffel**.

Once you install that you can compile your code using
```
se-compile **filename** -o **outputName** 
```

where **outputName** is the name you want your file to be

---

