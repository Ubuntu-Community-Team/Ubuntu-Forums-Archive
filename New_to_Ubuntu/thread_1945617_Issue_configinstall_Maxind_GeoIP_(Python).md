---
title: "Issue config/install Maxind GeoIP (Python)"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by j666gak on 2012-03-23
Hello,

I am trying configure / install Maxmind GeoOIP for use with quite a few  apps in the Splunk product. However when trying to install I am getting  the following error, I would really appreciate any help.


```
root@server:/opt/splunk/etc/apps/Maxmind/Python-1.2.7# python setup.py build
running build
running build_ext
building 'GeoIP' extension
creating build
creating build/temp.linux-x86_64-2.7
gcc  -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall  -Wstrict-prototypes -fPIC -I/usr/local/include -I/usr/include/python2.7  -c py_GeoIP.c -o build/temp.linux-x86_64-2.7/py_GeoIP.o
unable to execute gcc: No such file or directory
error: command 'gcc' failed with exit status 1
```


Many Thanks

---

### Post by Cheesemill on 2012-03-23
Have you got gcc installed?
```
sudo apt-get install build-essential
```

---

### Post by anewguy on 2012-03-23
I don't know anything about the product except what it does - never tried it myself.  I wanted to try installing this purely to see if I could duplicate the error.  What I found so far indicates the source for all of this is on sourceforge.  Did you download from there, and if so, did you download the python tar ball or something different?

Dave ;)

---

### Post by j666gak on 2012-03-23
I am currently runing Ubuntu Server 11.10 which has no internet connectivity due to firewalls

Cheesemill = I don't think that I have gcc unless it is part of the standard build, is there another way of getting it except for the apt-get command as the server has no internet connectivity?


anewguy = When used with other apps it looks really good, although I think more work needs doing the the documentation for install. I didn't get the files from Sourceforge, I got them directly from the Maxmind website. The first step is to install the Python part which is what I am stuck on before installing the C API and then uploading the database.


Thanks for the help guys

---

### Post by anewguy on 2012-03-23
Is the python part free?  If so, point me in the right direction and I'll download it and see if I can duplicate the error.  

As far as the build-essential package goes, that package is what installs gcc and a lot of "essential" (hence the name ;) ) pieces so you can build programs in ubuntu.  Since you have the server installed, at least for server 10.04 LTS, the build-essential package is on the CD you installed from:  look in the /pool/main/b folder and you'll find the build-essential folder.  Within that folder is the .deb you need to install - unfortunately I'm not familiar with the command line syntax to install it - if you have a GUI on your server, just double-click the file.  I'll look in the mean time for the command line syntax.

Dave ;)

EDIT:  here's the command line info:

cd directory  <- folder where the package is
sudo dpkg -i package_name.deb <- obviously, the name of the package goes here

*hopefully* that will take of things, but it may be that the server install already installs build-essential as just part of the nature of the beast.  If so, I would like to try that python package (be aware I know *nothing* about python or the software you are attempting to use - I'm just hoping I can figure out where your problem is coming in. ;)

---

### Post by anewguy on 2012-03-23
I downloaded the python stuff - which also depends on their c library which I also downloaded.  There is actually supposed to be  "make" from what I could tell - Iinstalled autoconf and built makefile.  Make still didn't want to work - I either don't have path set to get things include right, or there be something else I need to install since it aborted with you gcc error but also telling me it coulndn't find the python.h or some such file.

I also downloaded and tried to install the "C" Library but it refused to work also, even trying to usue the install.sh script gave errors.

So,based on their readme files, there's not much to go on to get the source compiled and installed.

---

### Post by anewguy on 2012-03-25
I'm curious if you've been able to make any further progress.  Did you download and follow the installation instructions for their supporting C library prior to trying to trying to use their installation instructions for the Python module?  Does the message from GCC actually have a filename that it says is not found - it really should?  

I wish I could do more with it here, but I don't know anything about Python so I don't know how to tell the make where the Python headers, etc., are.  Perhaps I'll try your command line and see how it goes.

Dave ;)

EDIT:  Just tried your python line to compile - got the same error about python.h not being found.  Also, for the C library, I ran as per the readme:

./configure (this builds the makefile based on your system)
make (compile and link the program[s])

At this point I got the error about line 21 invalid null value.  I tried looking at the makefile, but I'm not sure what they're trying to do.

---

### Post by j666gak on 2012-03-25
Hi Dave,

I have been trying the GeoIP Lite (free). I tried installing Python and have not looked at C yet, do you think I should try installing C first? It looks like you might be right, reading the install instructions for C it gives a lot more info and under the section 'Defining Variables' mentioning GCC

I really appreciate your support. When I get in to work tomorrow I will try installing C


Cheers

---

### Post by anewguy on 2012-03-25
From what I saw on the download for the Python piece, it REQUIRES their C library - they have a link to it right on the Python page.  Unfortunately I haven't been able to make either one go anywhere.  I do a ./configure - runs ok.  The make aborts with what appears to me to be syntax errors in the make file created by configure.  So, can't install the C library even though it's required for the Python piece.  And it kind of sounds like one of the things the C library provides is the python.h file, which comes up missing if you try to build the python piece.  I'll keep digging and let you know.  I'm laid up for a while, so working from a netbook while laying in bed isn't real condusive for me finding solutions right now.

Dave ;)

> **j666gak said:**
> Hi Dave,

I have been trying the GeoIP Lite (free). I tried installing Python and have not looked at C yet, do you think I should try installing C first? It looks like you might be right, reading the install instructions for C it gives a lot more info and under the section 'Defining Variables' mentioning GCC

I really appreciate your support. When I get in to work tomorrow I will try installing C


Cheers

---

### Post by j666gak on 2012-03-27
Hello Dave,

I manage to get a bit further. I was extracting the compressed file with Winzip on my Windows machine before transfering the files/folder structure to the Linux box, however this still did not resolve the issue. I then found out that GCC and one of its dependancies needed installing, once GCC was installed I ran again the install for C whic completed sucessfully.

I gues that I now need to install the Python API : / haha

---

### Post by anewguy on 2012-03-27
I'm glad you're getting further.  If you have further problems, be sure to follow the link on the Python page for just the C library, but I would have thought it would be installed as part of the C package.  I suppose paths will need to be updated as well to find everything.

Good job!

Dave ;)

---

