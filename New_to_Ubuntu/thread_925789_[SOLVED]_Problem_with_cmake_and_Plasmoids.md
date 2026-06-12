---
title: "[SOLVED] Problem with cmake and Plasmoids"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-09-21
Hi, all:

I'm trying to install a weather plasmoid on my KDE 4.1.1 Kubuntu 8.04 system.  I installed cmake and ran it in the build directory but I'm getting this error:

tarahmarie@tarahmarie-desktop:~/Documents/Software/weather/build$ make
make: *** No targets specified and no makefile found.  Stop.


What am I doing wrong?

Here's the plasmoid: [http://www.kde-look.org/content/show.php/Weather+Plasmoid?content=84251](http://www.kde-look.org/content/show.php/Weather+Plasmoid?content=84251)

And I followed the instructions under "How to Install", including cd'ing into the build directory and using the cmake command just like this: 

cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` .. 

Was that the wrong command?

---

### Post by phidia on 2008-09-21
Do you actually have cmake installed? Take a look at [this tutorial]("http://techbase.kde.org/Development/Tutorials/CMake") on cmake. From the terminal you should get a version # if you enter "cmake -v", and it's installed.

---

### Post by tarahmarie on 2008-09-21
Here's the output from "cmake -v"

tarahmarie@tarahmarie-desktop:~/Documents/Software/weather/build$ cmake -v
CMake Error: The source directory "/home/tarahmarie/Documents/Software/weather/build/-v" does not exist.
Specify --help for usage, or press the help button on the CMake GUI.


What does this mean?

---

### Post by phidia on 2008-09-21
It means you didn't enter the command correctly-I think.
Open the terminal app and type "cd" (all commands entered without the quotation marks).
That should put you in the root directory. Then just copy and paste this: > cmake -v

I don't have cmake installed. This is what my system outputs: 
"phidia@neverland:~$ cmake -v
The program 'cmake' is currently not installed.  You can install it by typing:
sudo apt-get install cmake
bash: cmake: command not found"

Well when I re-read your output it looks like cmake is installed-it found some problem being called from that directory.

---

### Post by tarahmarie on 2008-09-21
Here's the output when I'm in the root directory:

tarahmarie@tarahmarie-desktop:/$ cmake -v
CMake Error: The source directory "/-v" does not exist.
Specify --help for usage, or press the help button on the CMake GUI.


What the heck?

---

### Post by phidia on 2008-09-21
I guess this is a good idea: > Specify --help for usage, or press the help button on the CMake GUI
I'm not very familar with cmake, but apparently the "-v" option isn't applicable.
Sorry for the confusion. 
Back to the original problem: > tarahmarie@tarahmarie-desktop:~/Documents/Software/weather/build$ make
make: *** No targets specified and no makefile found. Stop.

Were you suppose to run "make" there or is that a mistake? If the build directory doesn't contain a make file you won't be able to run it-since it doesn't exist.

---

### Post by tarahmarie on 2008-09-21
Running "make" was originally what I was trying to do.  I've googled cmake, and I'm wondering if I need to have gcc installed to make it work.  Is that the case?

---

### Post by phidia on 2008-09-21
To get all the compling/building environment on ubuntu have your install cd at hand and enter: > sudo apt-get install build-essential

---

### Post by tarahmarie on 2008-09-21
I think the build-essentials package was the one I needed.  Thanks!

---

### Post by tarahmarie on 2008-09-22
So I seem to have successfully used cmake, but I don't know if others have had this problem: the plasmoid I want to use, commandwatch, is only a tiny little bar, instead of the full widget.  A couple of other plasmoids are also like this; they look like tiny squares instead of showing the full plasmoid.  Anyone else seen this problem?

---

