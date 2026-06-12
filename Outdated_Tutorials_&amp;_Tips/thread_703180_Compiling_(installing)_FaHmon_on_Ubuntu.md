---
title: "Compiling (installing) FaHmon on Ubuntu"
date: 2008-02-21
forum: Outdated Tutorials &amp; Tips
---

### Post by two00lbwaster on 2008-02-21
I had trouble trying to compile the new FahMon release after reinstalling Ubuntu.  This is for the current version 2.3.99.1

[This is the guide you need to follow for compiling the new release](http://trac.fahmon.net/wiki/CompilingForLinux) 

Download the latest source code from [**here**](http://fahmon.net/downloads/current.php?linux) and extract to the home drive or where ever you feel comfortable.
This will do the job for you (copy and past into a terminal)
```
wget -O FahMon-2.3.99.1.tar.bz2 --no-check-certificate "http://fahmon.net/downloads/current.php?linux"
```
Now to extract the file (copy and past into a terminal)
```
tar xvf FahMon-2.3.99.1.tar.bz2
```

You'll need to make sure that you have g++,wxgtk 2.6.4 or higher and the wxgtk2.6-dev, and wx-common installed to compile the program. I would suggest the use of synaptic for installation but you can use the following commands:
```
sudo apt-get install libwxgtk2.8-dev
```
That will also install some required dependencies
```
sudo apt-get install wx-common
```
And finally for some users (although this may require your install CD)
```
sudo apt-get install g++
```
[COLOR="Orange"]To clear up the guide, I type in wxgtk into synaptic and select libwxgtk2.8-dev click mark for installation and allow it to select all the other required dependecies, I then run a search for wx-common tick that for installation too.  I then click the apply button.
For some users you may need to install the g++ package and dependancies.[/COLOR]


Then it's a case of following the instructions in the guide, which are:

Use the cd command in a console to place yourself in your fahmon folder.
type into the console```
cd /home/[USER NAME]/FahMon-2.3.99.1
```or whatever your folder is called

Type in the console```
./configure
```You *may* need to type y to confirm partway through this.

Type ```
make
```This will take a few minutes, even on a very fast machine.

Type ```
sudo make install
```

You'll get an error after make install if you don't use sudo.

You'll now find fahmon installed and an icon link to the program in Applications>System Tools


Thanks go to Uncle_Fungus for his help with this how-to.

---

### Post by Dngrsone on 2008-03-05
Okay, I installed the required libraries, but it's giving me an error:

> checking for wx-config... no
configure: error:
                wxWidgets must be installed on your system.

                Please check that wx-config is in path, the directory
                where wxWidgets libraries are installed (returned by
                'wx-config --libs' or 'wx-config --static --libs' command)
                is in LD_LIBRARY_PATH or equivalent variable and
                wxWidgets version is 2.8.0 or above.


I am unsure what to do.

---

### Post by Boydyboyd on 2008-06-13
thanks alot for this, i have been trying to find a way to compile fahmon onto my ubuntu for ages, now the folding can resume.

:)

---

### Post by chex313 on 2008-07-06
Thanks a lot! The directions are great!

I did not have to do this.

"You will need to type y to confirm partway through this."

---

### Post by two00lbwaster on 2008-07-13
> **chex313 said:**
> Thanks a lot! The directions are great!

I did not have to do this.

"You will need to type y to confirm partway through this."

Yes there seems to have been a change or something with Hardy.  With Gutsy I still had to press y part the way through.  I'll update the instructions to read "You *may* need to type y to confirm partway through this."

---

### Post by techstop on 2008-07-24
Thanks mate. Nice howto!

---

### Post by mr_raider on 2008-11-01
Has anyone successfully compiled it in Intrepid? It worked fine in Hardy but I'm guessing the libraries have changed.

---

### Post by pointici on 2008-11-01
Yes you do the same but you must compile with the new version: FahMon 2.3.3

---

### Post by mr_raider on 2008-11-01
Cool. That did it.

---

### Post by two00lbwaster on 2008-11-03
Sorry guys, I've not been running Linux SMPs for a while, having moved over to GPU2 folding, but I'll try to keep this up to date, just PM me to do so :)

Updated to 2.3.3. Hopefully this will work well for everyone.

---

### Post by pointici on 2008-11-07
There's a new version: FahMon 2.3.4

---

### Post by [BrainBug] on 2008-12-03
Thank you so much for this step-by-step guide!  Soooo friggin' happy! :D

---

### Post by two00lbwaster on 2008-12-21
> **pointici said:**
> There's a new version: FahMon 2.3.4

Yeah I know about 2 days after I updated the tutorial.  I'll try to get around to doing it again soon; right after I've gotten through the other 10k IIS log files that I'm cleaning and importing into a db.

---

### Post by MAD_JIHAD on 2009-03-29
Wow thx for this it really helped me get the right dependencies, what an epic install!
Now onto monitoring my folding:D

---

### Post by anonymous_user on 2009-04-13
Im trying to compile FAHmon 2.3.99.1 but after running ./configure, it says it cannot find a valid libcurl installed although I do have it.

Can FAHmon be compiled on 64-bit linux?

---

### Post by rmjohnson144 on 2009-04-15
I too can't get 2.3.99.1 to install properly in 8.10.  I see several warning signs, but they scroll by so fast I can't see what the issue is.

I installed the latest libcurl as it would error out right away, but now it shoots through the whole thing with the warnings and compiles without any major errors.  I go to my Applications --> System Tools and when I select FahMon nothing happens at all.

Thanks for any help.
-=Mark=-

---

### Post by anonymous_user on 2009-05-16
I found this PPA for Jaunty:

[https://launchpad.net/~tsunetomo/+archive/ppa](https://launchpad.net/~tsunetomo/+archive/ppa)

No more need to compile FahMon :)

---

### Post by jrennell on 2009-05-28
I thought people would be interested in a script I wrote that will download the newest version of FahMon from their site, compile, and install it on a Ubuntu machine. This has been tested on 8.04 64-bit, 8.10 64-bit, and 9.04 64-bit with the FahMon 2.3.99.1 source. Here's the script:

```

#!/bin/bash

#############################################################
#                                                           #
# This script will install FahMon 2.3.x on a Ubuntu machine #
#                                                           #
#############################################################

TEMP_DIR="fahmon-temp-install"
LIBS="build-essential libwxbase2.8-0 libwxbase2.8-dev libwxgtk2.8-0 libwxgtk2.8-dev wx2.8-headers wx-common libcurl3-gnutls libcurl4-gnutls-dev g++"

if [ $1 ];
then
	TEMP_DIR=$1;
	echo "Using temp directory '$TEMP_DIR'"
fi

#First, get the packages required for build
sudo apt-get update
sudo apt-get install $LIBS

#download fahmon
mkdir $TEMP_DIR
cd $TEMP_DIR
wget http://fahmon.net/downloads/current.php?linux
tar -xjf FahMon-*
cd FahMon-*

#make and install fahmon
./configure
make
sudo make install

#cleanup
cd ../..
rm -rf $TEMP_DIR

#run ldconfig to update shared libraries
#(thanks altech6983)
sudo ldconfig

```

As a note: It uses a default temp directory "fahmon-temp-install" in the current working directory. I feel this is pretty safe, but you can pass in the name of the folder to use as the only argument to the script and it will use that instead. It deletes this directory when it's done.

You'll have to watch the output if you're not familiar with building this before. If something is not installed on your machine that was on my copies of 8.10 and 9.04 then you should get a message early on from the ./configure step. You'll have to add another package to get. Otherwise you should have executables for FahMon installed in the Applications menu (under Gnome) or in /usr/local/bin/fahmon

Let me know if you have any problems with it.

---

### Post by altech6983 on 2009-05-31
Just wanted to let people know that found this thread that it worked after running the command

```
sudo ldconfig
```

after his commands because I was getting this error:

```
fahmon: error while loading shared libraries: libwxcurl.so.1: cannot open shared object file: No such file or directory
```

---

### Post by rmjohnson144 on 2009-06-12
Well, I'm just guessing, but I'd assume you need to install the latest version of wxWidgets. Synaptic Package Manager says V2.8 is the newest one.

Good luck
-=Mark=-

---

### Post by sites on 2009-06-17
I'm also getting the libcurl error...

configure:20369: error:
    Could not find a valid libCURL installation on your system.

I've installed curl, but still get this error.  I'm using Hardy.

---

### Post by jrennell on 2009-07-20
> **sites said:**
> I'm also getting the libcurl error...

configure:20369: error:
    Could not find a valid libCURL installation on your system.

I've installed curl, but still get this error.  I'm using Hardy.

altech6983 had a good tip and suggested running "sudo ldconfig" after running the script. [COLOR="Red"]That should clear up that issue (worked on 9.04 at least)[/COLOR]. 

I update the commands in my post to include that step. Sorry for its omission. :(

EDIT: Oops, I'm dumb... that might be a problem with 8.04 packages, I'll test it out on a 8.04 VM and see if I get the same thing...

EDIT2: Good news, this script will work for 8.04. Make sure you do a
```
$ sudo apt-get update
```
before you run it to make sure you get the newest libcurl along with the other packages.

---

### Post by GeekGirl1 on 2010-09-03
I compiled FaHmon using the latest available code from svn. FWIW, the latest code is 2.3.99.1, so it's no different than the downloaded file. However, I wanted to show how to do this using a different technique. Also, thanks to two00lbwaster for this install guide.

I inserted the steps from Post #1 so you can see the entire sequence. As jrennell suggests, get everything up to date first.
```
sudo apt-get update
sudo apt-get dist-upgrade
```

You'll need to make sure that you have g++,wxgtk 2.6.4 or higher and the wxgtk2.6-dev, and wx-common installed to compile the program.
```
sudo apt-get install libwxgtk2.8-dev
```
```
sudo apt-get install wx-common
```
```
sudo apt-get install g++
```

Download subversion (svn).
```
sudo apt-get install subversion
```

Get the latest FaHmon code. It's the command at the bottom of the [Download FaHmon]("http://fahmon.net/download.html") page. This will create a fahmon subdirectory.
```
svn export http://svn.fahmon.net/trunk fahmon
```

Change to the fahmon subdirectory.
```
cd fahmon
```

From here, it's the same as Post #1. Follow the instructions in the INSTALL file, which are the same instructions used to build just about anything in Linux:

Configure your compiling environment.
```
./configure
```

Compile the code. This will take a while.
```
make
```

Install the code on Ubuntu. Be sure to enter your root password or the installation will get an error.
```
sudo make install
```

If everything went smoothly, you'll find an icon link to the program in Applications>System Tools

---

### Post by David Coton on 2011-02-03
Tried all this on 9.04 (64 bit) and it still can't find libcurl -- even after sudo ldconfig and the update commands.

Are there any other known fixes?

    David

EDIT: Update: Instructions at [https://help.ubuntu.com/community/FoldingAtHome/FahMon](https://help.ubuntu.com/community/FoldingAtHome/FahMon) resolve this -- there is an additional library to install.

---

