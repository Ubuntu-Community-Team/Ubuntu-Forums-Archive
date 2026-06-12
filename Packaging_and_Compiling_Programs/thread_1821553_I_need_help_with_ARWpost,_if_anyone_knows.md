---
title: "I need help with ARWpost, if anyone knows"
date: 2011-08-09
forum: Packaging and Compiling Programs
---

### Post by avi k on 2011-08-09
[LEFT]I try to compile the ARWpost, but keep getting an error.
 I installed the netcdf package on my computer, and I set a environment variable like this:
 export NETCDF = / usr / local / netcdf
 It seemed he could not find the package netcdf
 Does anyone know how I fix it.
 Here's the log:

[http://pastebin.com/AEV19QBq](http://pastebin.com/AEV19QBq)
[/LEFT]

---

### Post by avi k on 2011-08-10
[SIZE=3]Please someone.
 No one knows this software?.
 I really need help because I'm stuck with the installation.[/SIZE]

---

### Post by SevenMachines on 2011-08-10
Hi, have you actually build netcdf from source and put it in /usr/local?
Or have you installed the development files from the repository ```
$ sudo apt-get install libnetcdf-dev
```

---

### Post by avi k on 2011-08-10
Yes I built the netcdf from source Code.
I installed the software wrf, this software requires that all its components are  compiled wite the same compiler.
Here is the link of the wrf Guide:

[http://www.mmm.ucar.edu/wrf/OnLineTutorial/index.htm](http://www.mmm.ucar.edu/wrf/OnLineTutorial/index.htm)


Here is a guide wite instructions on how to install the ARWpost:

[http://www.mmm.ucar.edu/wrf/OnLineTutorial/Graphics/ARWpost/index.html](http://www.mmm.ucar.edu/wrf/OnLineTutorial/Graphics/ARWpost/index.html)

---

### Post by SevenMachines on 2011-08-10
So you did something like 
```
 $ ./configure --prefix=/usr/local/netcdf
```
when compiling netcdf.
Have you tried
```
 $ find /usr/local -name 'libnetcdf*'
```

---

### Post by avi k on 2011-08-11
Yes I did this command:

./configure --prefix=/usr/local/netcdf




[SIZE=3]I must say that I have no Experience in Linux, I'm just getting started in Linux.
I tried the command you gave me, it seems that he did not find anything.
 I tried this command:

locate libnetcdf

Then he found quite a lot of files.
Can I fix this so that the ARWpost can find the necessary files?
Here is the console:[/SIZE]


[SIZE=3]http://pastebin.com/txd7KbrS[/SIZE]

---

### Post by SevenMachines on 2011-08-11
Looks like you've picked a complicated one to start with in linux :)

How about,

* Install a 'local' version of netcdf as required by arwpost
```
$ ./configure --prefix=/usr/local
$ make
$ sudo checkinstall
```Here i've used checkinstall to allow the package manager to install rather than 'sudo make install'

The when you configure ARWpost specify the directories
```
$ ./configure
** WARNING: No path to NETCDF and environment variable NETCDF not set.
** would you like me to try to fix? [y]

Enter full path to NetCDF include directory on your system
/usr/local/include
Enter full path to NetCDF library directory on your system
/usr/local/lib

```

[EDIT] Note, I had to add  -lnetcdff to the ARWpost.exe target in src/Makefile to compile, otherwise i get lots of undefined reference to `nf_inq_varid_' and so on on ./compile. So if you see those errors you'll need to do the same

---

### Post by avi k on 2011-08-12
Let's see if I understand correctly, I should reinstall the package netcdf from source code, but this time to install it on / usr / local instead of home / user.
Another question - if I install a new package of netcdf elsewhere, it would not destroy the package already installed on my computer?.

---

### Post by SevenMachines on 2011-08-12
The system version of netcdf from official ubuntu repositories installs in the prefix /usr, so /usr/include and /usr/lib. You shouldnt install here unless you know what you're doing as it will overwrite them. 
If you need a local version for all users you generally install to the prefix /usr/local, which isnt used by system libraries so wont overwrite them or itself be overwritten on system upgrades.
If you only need something for one user (yourself for instance) then use a directory inside /home/user, whichever ones you prefer

---

### Post by avi k on 2011-08-12
to Tell the truth, I still did not understand.
At / home / user /   the  package netcdf currently installed .
to   compiled the ARWpost i need to Put path, so the  ARWpost knew where to get the libraries.
I can give the path This way:

export NETCDF=/home/user/WRF/netcdf-4.1.2/

---

### Post by SevenMachines on 2011-08-12
You have netcdf *compiled* in /home/user/WRF/netcdf-4.1.2, you dont have it actually *installed*, its not quite the same thing. If you installed netcdf like
```

# Configure to install to /usr/local
$ ./configure --prefix=/usr/local

# Build netcdf
$ make

# Install netcdf to /usr/local, libraries will now be in /usr/local/lib
$ sudo make install
```

Then you as I mentioned when building ARWpost either run ./configure and then type the netcdf directories in manually or.
```
$ export NETCDF=/usr/local
$ ./configure
$ ./compile

# It worked!
$ ./ARWpost.exe 

!!!!!!!!!!!!!!!!
  ARWpost v3.1
!!!!!!!!!!!!!!!!
ls: cannot access ./wrfout_d01_2000-01-24_12:00:00: No such file or directory
ls: cannot access ./wrfout_d01_2000-01-24_12:00:00*: No such file or directory
 Oops, we need at least ONE input file for the program to read.
```

---

### Post by avi k on 2011-08-18
[SIZE=3]Thank you very much.
 I hope I did right this time, I still get an error. It seems the console accepts only one path of two I had given him, how I can fix this?.

[/SIZE][SIZE=3]Here is [/SIZE][SIZE=3]the console:
[/SIZE]
[http://pastebin.com/P2Tp1ftx](http://pastebin.com/P2Tp1ftx)

[SIZE=3]Here's [/SIZE][SIZE=3]the log:[/SIZE]

[http://pastebin.com/cryniFyA](http://pastebin.com/cryniFyA)

---

### Post by SevenMachines on 2011-08-18
Not this
```
user@user-desktop:~/WRF/ARWpost$ export NETCDF=/usr/local/include/
user@user-desktop:~/WRF/ARWpost$ export netcdf=/usr/local/lib/
```just this
```
user@user-desktop:~/WRF/ARWpost$ export NETCDF=/usr/local
```[Post #11]("http://ubuntuforums.org/showpost.php?p=11144239&postcount=11") is the complete step by step to how I compiled netcdf and ARWPost, you shouldnt need to change a thing

---

### Post by avi k on 2011-08-18
[SIZE=3]Now I understood.
 I gave the path, I wrote the command compile, but I still get an error.
 Do you know how to fix this?.

 Here's the console:

[http://pastebin.com/0N3NykSD](http://pastebin.com/0N3NykSD)

 Here's the log:

[http://pastebin.com/KTsdDuTM](http://pastebin.com/KTsdDuTM)
[/SIZE]

---

### Post by SevenMachines on 2011-08-18
That error means ./compile isnt finding the new compiled version of netcdf in /usr/local. Try this command and compare the output,

```
$ find /usr/local/ |grep netcdf
/usr/local/lib/libnetcdf_c++.so.4.1.0
/usr/local/lib/pkgconfig/netcdf.pc
/usr/local/lib/libnetcdf.a
/usr/local/lib/libnetcdff.la
/usr/local/lib/libnetcdf_c++.so
/usr/local/lib/libnetcdff.so.5
/usr/local/lib/libnetcdf.so
/usr/local/lib/libnetcdf_c++.la
/usr/local/lib/libnetcdff.a
/usr/local/lib/libnetcdf.so.7.1.1
/usr/local/lib/libnetcdf.la
/usr/local/lib/libnetcdf.so.7
/usr/local/lib/libnetcdf_c++.a
/usr/local/lib/libnetcdff.so.5.1.0
/usr/local/lib/libnetcdf_c++.so.4
/usr/local/lib/libnetcdff.so
/usr/local/include/netcdf.hh
/usr/local/include/netcdfcpp.h
/usr/local/include/netcdf.h
/usr/local/include/netcdf.inc
/usr/local/include/netcdf.mod

```Note, /usr/local/lib and /usr/local/include is where everthing needed is, what do you get?

---

### Post by avi k on 2011-08-18
[SIZE=3]After I put the command you gave me, it seems that / usr / local / include is where he should be, but / usr / local / lib, it seems he can not find. Can I fix this?.

 Here's the console:

[http://pastebin.com/LGBg225V](http://pastebin.com/LGBg225V)
[/SIZE]

---

### Post by SevenMachines on 2011-08-18
Try the netcdf build and install again, any errors?
     ```
# Configure to install to /usr/local 
$ ./configure --prefix=/usr/local  

# Build netcdf 
$ make  

# Install netcdf to /usr/local, libraries will now be in /usr/local/lib 
$ sudo checkinstall
# or 
$ sudo make install 
```

---

### Post by avi k on 2011-08-18
[SIZE=3]If I understand correctly, I need to reinstall the package netcdf, using the command:

 . / configure - prefix = / usr / local
 And then the command:

 sudo make
 Then the command:

 sudo make install

 Do I understand correctly what you said?.
  Because I have no experience in Linux, I want to know, if I understood you correctly, so I do not make a mistake.[/SIZE]

---

### Post by SevenMachines on 2011-08-18
Yes, they are exactly as put in my last post, the way you have them has additional spaces and things that I'm hoping are just cut and paste errors?

---

### Post by avi k on 2011-08-19
[SIZE=3]Good morning.
 So I reinstalled the package netcdf in path / usr / local
 Here's the console:

[http://pastebin.com/xrKci70W](http://pastebin.com/xrKci70W)

 Then I ran the command and compared to the list you gave me, it seems that everything matches:
 find / usr / local / | grep netcdf
 Here's the console:

[http://pastebin.com/n0yDc8aB](http://pastebin.com/n0yDc8aB)

 Then I ran configure and compile, and I still get an error,in one of your previous posts, you told me that if I encounter in this error, and I quote:
 "otherwise i get lots of undefined reference to` nf_inq_varid_ 'and so on on "

 I would have put the file, and I quote:
 "lnetcdff to the ARWpost.exe target in src / Makefile to compile"

I need an  accurate explanation How to do it.
Here's the log[/SIZE]:

[http://pastebin.com/p8dveRtu](http://pastebin.com/p8dveRtu)

---

### Post by SevenMachines on 2011-08-19
If you open up the ARWpost file src/Makefile you will see a section that looks as below
```
ARWpost.exe: $(OBJS)
  $(FC) $(FFLAGS) $(LDFLAGS) -o $@ $(OBJS)  \
    -L$(NETCDF)/lib -I$(NETCDF)/include  -lnetcdf

```

You need to add -l netcdff linking to this so it now looks like below
```
ARWpost.exe: $(OBJS)
  $(FC) $(FFLAGS) $(LDFLAGS) -o $@ $(OBJS)  \
    -L$(NETCDF)/lib -I$(NETCDF)/include  -lnetcdf  -lnetcdff

```

---

### Post by avi k on 2011-08-19
[SIZE=3]Thank you very much for your help, ARWpost.exe file is created as you can see here[/SIZE][SIZE=3]:
[/SIZE]
[http://pastebin.com/iFjZTvA4](http://pastebin.com/iFjZTvA4)

[SIZE=3]Now I have a question for you: Did you also know the software ncl Graphics?.
 I'm now at the running of wrf, because I learn the Linux, and the wrf I try to run the two possibilities: the ncl Graphics, and the ARWpost.
 I already ran the wrf experience of Hurricane Katrina, and created a pdf file to make it a png file, and I did not succeed. So I was wondering if you know the software ncl Graphics?.[/SIZE]

[SIZE=3]And again  I want to thank you for your help[/SIZE].

[SIZE=3]Avi[/SIZE].

---

### Post by SevenMachines on 2011-08-19
No problem. Sorry, I dont know anything about acl graphics, or what ARWpost is. Sounds specialist though, it probably needs a specialist forum to find people who know about it. good luck

---

### Post by avi k on 2011-08-20
[SIZE=3]Thank you.[/SIZE]

---

### Post by biranchi on 2012-07-18
[QUOTE=avi k;11134173][LEFT]I try to compile the ARWpost, but keep getting an error.
 I installed the netcdf package on my computer, and I set a environment variable like this:
 export NETCDF = / usr / local / netcdf
 It seemed he could not find the package netcdf
 Does anyone know how I fix it.
 Here's the log:

[http://pastebin.com/AEV19QBq](http://pastebin.com/AEV19QBq)
[/LEFT]
try the following
export LD_LIBRARY_PATH=/usr/local/netcdf/lib
export NETCDF=/usr/local/netcdf
then ./configure
and
./compile
:D

---

