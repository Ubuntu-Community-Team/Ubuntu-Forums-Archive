---
title: "getting JES-3.1 to work on ubuntu"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by chiefboo on 2008-11-17
hello. newbie here. in my computer science class we are using jython. i just recently installed ubuntu on my desktop and i was trying to get jython working but i've run into a couple of problems. 

first i had to install java from their website which was difficult for me hA hA. I wasn't familiar with how to save programs or move files via cle. anyways i saved  it in the /usr/bin folder like the java website said to and finally got it working properly with firefox (so i'm assuming java is now properly installed on my ubuntu machine). 

i downloaded the jes3.1 package and extracted it to my public folder. the instructions from the website said to run the jes.sh file but every time i try to a prompt asks if i want to display or run the jes.sh file. after i click run nothing appears to happen. after i click display a gnome-terminal (or soemthign which looks exactly like a gnome-terminal pops up).

any ideas?

---

### Post by spiderbatdad on 2008-11-17
I'm guessing the program has not been made executable. navigate to the directory that holds the progam, and run the command ```
ls -l
```you will see, in order of user/group/other, the set of permissions: rwx,rwx,rwx...without commas. If you dont see an x for at least user...the program will not run. ```
sudo chmod +x jes.sh
```

Also run the program from the terminal ```
./jes.sh
```

---

### Post by chiefboo on 2008-11-19
JES.sh is executable for user (everyone actually). Strange thing is whenever I am in the directory /home/chihbu/Public/jes-3-1 (the directory i saved the extracted jes folder to) it says

> bash: ./JES.sh: /bin/sh^M: bad interpreter: No such file or directory


The instructions on the website i downloaded it from didn't really specify where I needed to save the extracted jes3.1 folder but maybe they assumed everyone would know what they were doing. Does it matter where i save the folder?

::EDIT:: I just tried moving it to /usr/bin but same thing happened. any ideas?

Thanks for reply also :)

---

### Post by spiderbatdad on 2008-11-19
bad interpreter indicates a problem with the file...ie, bad line breaks or maybe #!/bin/sh is not on the first line...or is preceded by a space?
Maybe #!/bin/sh has extra characters after it...like ^M?

Please post the fist few lines of the script if you need help.

---

### Post by gauss on 2008-11-26
> **chiefboo said:**
> 
The instructions on the website i downloaded it from didn't really specify where I needed to save the extracted jes3.1 folder but maybe they assumed everyone would know what they were doing. Does it matter where i save the folder?
No, it doesn't. If you're the only user on your box who uses JES you can save it in your home directory.

The ^M indicates that the file is in DOS and not UNIX text format. I'm trying to get JES working on Gentoo and my first step was to change all files in the unzipped directory *jes-3-1* to UNIX format with
```
find jes-3-1 -exec dos2unix {} \;
``` This assumes you have *dos2unix* installed. (I believe it's a standard part of Ubuntu.)

But I still haven't got it working as it appears that *JESstartup* cannot find a required class, *org/python/util/jython*, which should be in *jes-3-1/jar/jython.jar* and appears not to be. Whenever I list the contents of *jython.jar* I get a *java.util.zip.ZipException: invalid entry size*. This appears to indicate a corrupted file.

Good luck with your and my installation!

---

### Post by gauss on 2008-11-26
JES-3.0.6 works out of the box:

[http://coweb.cc.gatech.edu/mediaComp-teach/uploads/26/jes-3-0-6-linux.zip](http://coweb.cc.gatech.edu/mediaComp-teach/uploads/26/jes-3-0-6-linux.zip)

So I'm giving up on JES-3.1 for Linux until they get the bugs out.

---

