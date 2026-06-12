---
title: "[SOLVED] Compiling from source"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Cuttysark on 2008-10-20
Can anyone point me to some kind of instruction or walk through on how to do this. I know when I've read other posts regarding compiling, a lot of the response advises using Synaptic but once in a blue moon I'll see a program I'd like to try and it only comes as source code.

I have two machines running Hardy, my work machine (the one I'm using right now), and another strictly for learning all I can about Ubuntu, which initially, is the one I would use for compiling, so if things go belly up, I really haven't lost anything but time.

---

### Post by Thelasko on 2008-10-20
Off of the top of my head you will need to install the build-essential package.  Then go to the directory containing your source files and enter
```
./configure
make
```
You will probably have to do this as sudo,(apparently only for installation) and read all of the output carefully, you may have to install dependent packages.

It's been a while since I've compiled from source, so please excuse any errors.  [Here's an example.]("http://www.freetds.org/userguide/config.htm")

---

### Post by bsharp on 2008-10-20
Another tidbit worth mentioning is that after you un-tar the source package, there is **always** a README file which you should read to prevent alot of headaches.  After you read that, if there isn't much mentioned about the installation, look for a INSTALL file.

---

### Post by aeiah on 2008-10-20
there is a usual way of compiling something, but usual or not, the instructions are in a file called INSTALL, or perhaps README. 

after uncompressing the tar.gz, the usual steps include, in a terminal:
- navigating to the directory you uncompressed the files to
- running the config script (./configure)
- compiling the code (make)
- installing the compiled code to your path (sudo make install)


aannd it looks like someones beat me to it about README and INSTALL damnit

---

### Post by cwsnyder on 2008-10-20
Most places which have the source code also list the dependencies or have a 'make' file which returns errors if it cannot complete the compile.

I have never done this myself, except as directed by an install file.

Most source code is distributed either in .tar, .tar.bz, or .tar.gz form.  Type ```
man tar
``` for the syntax for regenerating the packages and their respective folder trees.

After that, check out any README or INSTALL files for specific installation instructions, hopefully in the newly created folder(s).

Look especially for a file called 'configure'.  Open a terminal window and navigate to that folder and type ```
./configure
``` in the window.  That should run the preprocessor part of the compiler and, hopefully, tell you if you are missing any dependencies.  If there are no problems with dependencies you can type ```
sudo make && sudo make install 
```  This should first compile, then link and install in the proper directories the new package.  You will probably have to find where the executable is hiding (probably in /bin, /sbin, or /user/bin, /user/sbin, or possibly in the original folder), and possibly create the menu launcher if you want it on your menu.  You may even have to grant rights to the appropriate users and groups.

It can be done, but I would hate to have you do this if you are not fairly comfortable with working with the command line.

If anything I just outlined looks strange to you, DON'T DO IT.  Read the documentation.  This is a fairly quick way to consign your installation to the bit-bucket if you just blindly follow anybody's directions.

---

### Post by hyper_ch on 2008-10-20
and you need to install
```

sudo apt-get install build-essential

```
the compiler and stuff ;)

---

### Post by igknighted on 2008-10-20
There is also something called "checkinstall", which takes the place of the "makeinstall" step.  Basically it creates a .deb file for your system (but only your system, don't share it, as it could break other people's systems) and installs that, so you can easily un-install it later.

---

### Post by Cuttysark on 2008-10-20
Okay thanks guys, this gives me something to work with, my project for the week. I'm doing a photography course and when I was browsing my local thrift store for a novel today, I noticed they had a Wacom tablet for £5 (about $8.50 at todays rate). Wacom do a Linux driver but it's code only.

---

