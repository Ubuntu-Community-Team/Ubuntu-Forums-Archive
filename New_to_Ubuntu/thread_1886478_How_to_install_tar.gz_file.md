---
title: "How to install tar.gz file"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by SkyLinePH on 2011-11-25
Can i ask, how to install tar.gz file in Ubuntu 10.04, give it step by step, Thanks. :popcorn:

---

### Post by Immolatus on 2011-11-25
It really depends on what it is. If it were say a theme for gnome....you could just drag and drop it onto the theme manager and presto. If it is an application then you need to find out where it belongs:

in terminal

untar nameoffile 
(works for both .tar.gz and .tar.bz) in the directory it needs to be installed in.

make

make install

alternatively you can just move the file where it needs to be and cd (if you don't know how to traverse the file system on the command line, don't be discouraged just print out a reference of most common commands from the web somewhere)to that place if you are not already there.

chmod a+x precisenameoffilegoeshere  (makes it executable)

then

./precisenameoffile  (short form of the "make" business from above)

---

### Post by mutley89 on 2011-11-25
tar.gz files are just compressed archives, they can contain anything.  You can extract it with command tar -xzvf yourfile.tar.gz and then have a look for a README file or similar that will probably explain what to do with it. However, what are you trying to install, and have you checked the repositories, as it will be easier to install and keep up to date software installed through them.

---

### Post by donkyhotay on 2011-11-25
There are no step-by-step instructions for a tar.gz file. A tar.gz is simply a compressed file format, it's like asking how to install a .zip file. First of all before installing from tar.gz I would strongly recommend making certain the program you are trying to install isn't already in the repos. You should always install a program from the repos before attempting anything else. Now if you must have the program and the only way to get it is as a tar.gz file then you'll need to extract all the files in it. Usually just double-clicking on the file and then dragging the files there into a new folder works for that. Once that's done look for something that looks like instructions. Most developers will usually include the instructions on how what is needed to either install or run the software in a file called "readme" or "install" but there are no guarantees. If they have instructions included go ahead and follow them, if they don't... well... your guess is as good as ours.

---

