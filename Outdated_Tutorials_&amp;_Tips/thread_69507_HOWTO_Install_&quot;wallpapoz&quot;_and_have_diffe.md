---
title: "HOWTO: Install &quot;wallpapoz&quot; and have different wallpapers on each workspace"
date: 2005-09-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Tomy on 2005-09-27
You can find information about the program here:
[http://wallpapoz.sourceforge.net/]("http://wallpapoz.sourceforge.net/")

To create a script file:
1. Open Applications>Accessories>Text Editor.
2. Copy and past everything from the code block below.
3. Save your new file--I saved mine as wallpapoz-install.
4. Open the file browser and right-click on your new file and select "Properties" go to the "Permissions" tab and check the "Execute" box.
You now have an executable script file.

To execute the script file:
1. Open Applications>System Tools>Terminal
2. Update your repositories just to be safe:
sudo apt-get update
3. Make sure you are in the directory you saved your file in and enter:
sudo ./wallpapoz-install 

Well, that's what I did;). But I am no GNU/Linux guru. 
```

#!/bin/sh
# Here are my notes from installing wallpapoz on Ubuntu Hoary Hedgehog 5.04. 
# You can copy and save this and run it as a script.
# The instructions are all here as comments.
# I am an end-user and know not what I am doing. Use at your own risk
# Good Luck! Tomy
# STEP 1. Download two files:
sudo wget -c [http://wallpapoz.sf.net/temp/wallpapoz-0.2.tar.bz2]("http://wallpapoz.sf.net/temp/wallpapoz-0.2.tar.bz2")
sudo wget -c [http://members.iinet.net.au/~gracey88/libxml++-2.10.0-1_i386.deb]("http://members.iinet.net.au/%7Egracey88/libxml++-2.10.0-1_i386.deb")
# STEP 2. Install libxml++-2.10 from  manicka's deb.
sudo dpkg -i libxml++-2.10.0-1_i386.deb
#STEP 3. Install the dependencies: (modified from Akbar's instructions )
# You probably don't need the dev versions and I added  libxml++2.6
sudo apt-get -y install build-essential
sudo apt-get -y install libsigc++-2.0-dev
sudo apt-get -y install libglibmm-2.4-dev
sudo apt-get -y install libgtkmm-2.4-dev
sudo apt-get -y install libglademm-2.4-dev
sudo apt-get -y install  libxml++2.6
# STEP 4. Install the wallpapoz program 
sudo tar -jxvf wallpapoz-0.2.tar.bz2
cd wallpapoz-0.2
sudo make
sudo sh install.sh /usr
# The End

``` 
At this moment I do not know if this script works. This is just a cut-n-paste of a previous post with several changes. I will test it later on a computer that runs Ubuntu 5.04 Hoary and has not yet had wallpapoz installed.

If everything worked click on Applications>Accessories>Wallpapoz.

After you create a configuration file you can set the daemon to run every time you boot Ubuntu by selecting:
Systems>Preferences>Sessions and then the tab for 'Startup Programs'
choose 'Add' and enter:
daemon_wallpapoz

Hope it works for you
Tomy

Update: I have run the script on a fresh install of Ubuntu 5.04 Hoary (after I installed all upgrades).
It works!!  :) At least it did for me. 

The script installs the "dev" versions of the libraries and therefore a lot of files are installed that you probably don't need. The reason I choose the "dev" versions is that Akbar's instructions include this line: > Remember, you must install the development files too not just runtime files 
The only glitch I ran into was the first line in /etc/apt/sources.list that refers to the cd repository needs to be commented out. I have already deleted the line so I am not able to post it here. FYI here is my file:
```

# modified version of /etc/apt/sources.list

deb /http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted


deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe
# The End

``` Edit 09/27/2005:  added sudo to tar command -- seems to work better
Edit 10/18/05:added sudo to make command -- had a permissions error and this seemed to work

---

### Post by Bob Morane on 2005-11-13
Hello, this is for all "Breezy users that get a "segmentation fault" when trying to run "daemon_wallpapoz"

I contacted Akbar by mail about this issue. It looks like it's unique to Ubuntu and maybe limited to some users. Akbar haven't been able to correct it with the c++ code, so he recoded the daemon in python. It looks like it works well. At least, it works for me.

Akbar will rewrite the daemon and GUI in python, but currently, neither are available on the web site. Here is the python code if you can't wait ;) 

```
## daemon_wallpapoz.py
#
# This file will check desktop continously and change wallpaper 
# with preferences from configuration file

from xml.dom import minidom
import xml
import os
import sys
import array
import time
import threading
import random

## number -- global variable
#
# this is index of wallpaper list of workspaces
# for example: number[0] is index of wallpaper list in first workspace
number = array.array('i')

## delay -- global variable, how many time will wallpaper list thread
#
# has to wait before it manipulate its index
delay = 1.0

## random -- global variable, is wallpaper list thread randomize its index
randomvar = 0

exit_code = 0

## XMLProcessing -- class for processing wallpapoz xml file
class XMLProcessing:

    ## The constructor
    def __init__(self, file):
	try:
	    self.xmldoc = minidom.parse(file)
	except IOError:
	    print "There is no configuration file. Create it first by running wallpapoz!"
	    sys.exit()
	except xml.parsers.expat.ExpatError:
	    print "The configuration file is corrupted. Remove it then create it again with wallpapoz!"
	    sys.exit()
	self.wallpapoz_node = self.xmldoc.childNodes[1]
	self.workspace_node_list = self.wallpapoz_node.getElementsByTagName('workspace')
	self.workspace_num = self.workspace_node_list.length

    ## class method -- get delay time that wallpaper list thread manipulate its index
    def delay(self):
	return self.wallpapoz_node.attributes["interval"].value

    ## class method -- whether the wallpaper list thread randomize its index
    def is_random(self):
	return self.wallpapoz_node.attributes["random"].value

    ## class method -- method for fill list with wallpaper path file
    def fill_list(self):
	worklist = []
	for i in range(self.workspace_num):
	    worklist.append( [] )
	index = -1
	for file in self.workspace_node_list:
	    file_node_list = file.getElementsByTagName('file')
	    index = index + 1
	    for node in file_node_list:
		if node.nodeName == "file":
		    worklist[index].append(node.firstChild.data)
	return worklist

    ## class method -- to know how many workspace we use
    def get_workspace_num(self):
	return self.workspace_num

## System -- class for knowing current desktop and change wallpaper
#
# with calling external program
class System:
    ## class method to know what workspace we are in now
    def current_desktop(self):
	desktop = os.popen('xprop -root _NET_CURRENT_DESKTOP').read()
	return int(desktop[33] + desktop[34])

    ## class method
    def change_wallpaper(self, wallpaper):
	os.system('gconftool-2 -t string -s /desktop/gnome/background/picture_filename ' + "\"" + wallpaper + "\"")

## AsyncIndex -- class for making thread that manipulating index wallpaper list
class AsyncIndex(threading.Thread):
    ## constructor
    def __init__(self, index):
	threading.Thread.__init__(self)
	self.index = index

    ## the function that thread will execute
    def run(self):
	if randomvar == 1:
	    number[self.index] = 0
	    size = len(worklist[self.index])
	    while True:
		number[self.index] = int(random.random() * size)
		time.sleep(delay)
	else:
	    while True:
		number[self.index] = 0
		for i in worklist[self.index]:
		    time.sleep(delay)
		    number[self.index] = number[self.index] + 1

## the main program
if __name__ == "__main__":

    # generate seed for random number
    random.seed()

    # the configuration file
    file = os.environ['HOME'] + "/.wallpapoz/wallpapoz.xml"

    # call the xmlprocessing class to read it
    wallpapozxml = XMLProcessing(file)

    # fill the workspace list
    worklist = wallpapozxml.fill_list()

    # how many workspace we use
    total_workspace = wallpapozxml.get_workspace_num()

    # create the index for wallpaper list thread
    number.fromlist( range( total_workspace ) )

    # create the system class ( to change wallpaper and read current desktop )
    # by calling external program
    system = System()

    # previous workspace
    previous_desktop = -1

    # previous wallpaper list index
    previous_index = -1

    # get the delay time and random preferences
    delay = 60 * float(wallpapozxml.delay())
    randomvar = int(wallpapozxml.is_random())

    # create the thread
    wallpaper_list = []
    for i in range(total_workspace):
	wallpaper_list.append(AsyncIndex(i))
	wallpaper_list[i].start()

    # the daemon that works forever
    while True:
	try:
	    # don't get rush
	    time.sleep(1)

	    # what workspace we are in now?
	    cur_desk = system.current_desktop()

	    # requirement for changing wallpaper
	    # 1. we change workspace
	    # 2. index of wallpaper list change
	    if previous_desktop != cur_desk or previous_index != number[cur_desk]:
		# if we move to workspace that we don't use, just ignore
		if cur_desk >= total_workspace:
		    continue

		# command to change wallpaper
		system.change_wallpaper(worklist[cur_desk][number[cur_desk]])

		# our previous workspace and index of wallpaper list
		previous_desktop = cur_desk
		previous_index = number[cur_desk]

	# ok, we stop this daemon
	except KeyboardInterrupt:
	    # now it's time for the main thread to exit
	    os._exit(0)

```

You have to copy it, paste in a new file, and save your file as daemon_wallpapoz.py (or whatever you like). Than run the daemon with *python daemon_wallpapoz.py*

If it runs fine (you can check if you have different wallpapers on differents workspaces), just add an entry to your session to have the daemon loaded each time you log in.

---

### Post by tofudrifter on 2005-11-28
I'm running Breezy with "Enlightened Gnome" and i get these errors when i try to run wallpapoz

when i run wallpapoz
```
I/O error : No such file or directory
terminate called after throwing an instance of 'xmlpp::exception'
  what():  do_write_to_file() failed.
Aborted

```

when i run python daemon_wallpapoz.py
```
  File "daemon_wallpapoz.py", line 36
    try:
    ^
IndentationError: expected an indented block

```

have i done something wrong? or is wallpapoz not compatible with Enlightenment?

---

### Post by dezier on 2005-12-03
I ran the script and everything seemed alright. Then i got this message when running wallpapoz:

```

andreas@dezier:/usr/bin$ wallpapoz
wallpapoz: error while loading shared libraries: libxml++-2.6.so.2: cannot open shared object file: No such file or directory

```

When I looked in Synaptic Package Manager i noticed the package libxml++2.6c2. I installed it, and then it worked. I don't know if I initially did something wrong or if this was the right solution, but maybe this solution be can be helpful to other people.

---

### Post by merinda on 2005-12-06
Hi,

Initially I developed Wallpapoz using C++, libxml++ ( C++ version of libxml ) and gtkmm ( C++ version of gtkmm ). Later this choice gave many users problems. Most of them had difficulties installing gtkmm library if not libxml++. 

However the big problem is the program ( the daemon ) crashes when running in Ubuntu Breezy Badger but the program runs fine in Fedora Core 4. The gui however runs fine in both distro. So I tracked it down.... then found that the problem was located in threading part. After reading and thinking it many times, I couldn't find the solution. I have no idea why the program get crashed when the program creates the threads. 

So I decided to convert the daemon source to python. It works fine. But it's weird if the gui source is in C++ but the daemon is in python. Then I convert the gui source to python source using pygtk.

Ok, go to the official site to download the wallpapoz in python version.
[http://wallpapoz.sf.net](http://wallpapoz.sf.net)

Someday maybe I will fix the bug in C++ version of Wallpapoz but I'm not sure.

Regards,

Akbar

---

### Post by toemos on 2006-04-24
[QUOTE=tofudrifter]I'm running Breezy with "Enlightened Gnome" and i get these errors when i try to run wallpapoz

when i run wallpapoz
```
I/O error : No such file or directory
terminate called after throwing an instance of 'xmlpp::exception'
  what():  do_write_to_file() failed.
Aborted

```

when i run python daemon_wallpapoz.py
```
  File "daemon_wallpapoz.py", line 36
    try:
    ^
IndentationError: expected an indented block

```

have i done something wrong? or is wallpapoz not compatible with Enlightenment?[/QUOTE]
did you ever get it going? how?

---

### Post by rez on 2006-04-28
[QUOTE=tofudrifter]I'm running Breezy with "Enlightened Gnome" and i get these errors when i try to run wallpapoz

when i run wallpapoz
```
I/O error : No such file or directory
terminate called after throwing an instance of 'xmlpp::exception'
  what():  do_write_to_file() failed.
Aborted

```

when i run python daemon_wallpapoz.py
```
  File "daemon_wallpapoz.py", line 36
    try:
    ^
IndentationError: expected an indented block

```

have i done something wrong? or is wallpapoz not compatible with Enlightenment?[/QUOTE]

I'm getting the same problem ... except, when I try to run the python script, i get:

```
There is no configuration file. Create it first by running wallpapoz!

```

If i try and run wallpapoz, I get the error: 

```
I/O error : No such file or directory
terminate called after throwing an instance of 'xmlpp::exception'
  what():  do_write_to_file() failed.
Aborted

```

---

### Post by Rinzwind on 2006-05-01
edit: wrong topic

---

### Post by l4v4_f10w on 2006-05-10
Nice one, i did run into sum problems, but after reading onwards was able to fix it, it was coz of ur solution denzier. Got to say my linux was SUSE and i really liked it specially teh kde enviroment coz it was so nice and easy to use, after using ubuntu i realized the vast amount of guides on ubuntu switched straight away. Thanks all of u guys who make my life alot easier specially in the sense of knowing what to do. Think i learned quite abit over the last couple of weeks but still learning theres along way for me to go yet, but hopefully i'll get there because of u guys, all credits go to the ubuntu forum.

---

### Post by Raito on 2006-07-28
Hmm, it didn't work for me. I think one of the mirrors is dead. What should I do?

```
sokuban@Arche:~$ sudo ./wallpapoz-install
--21:18:07--  http://wallpapoz.sf.net/temp/wallpapoz-0.2.tar.bz2
           => `wallpapoz-0.2.tar.bz2'
Resolving wallpapoz.sf.net... 66.35.250.209
Connecting to wallpapoz.sf.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://wallpapoz.sourceforge.net/temp/wallpapoz-0.2.tar.bz2 [following]
--21:18:07--  http://wallpapoz.sourceforge.net/temp/wallpapoz-0.2.tar.bz2
           => `wallpapoz-0.2.tar.bz2'
Resolving wallpapoz.sourceforge.net... 66.35.250.209
Connecting to wallpapoz.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 41,941 (41K) [application/x-tar]

100%[====================================>] 41,941       102.15K/s

21:18:08 (101.80 KB/s) - `wallpapoz-0.2.tar.bz2' saved [41941/41941]

--21:18:08--  http://members.iinet.net.au/~gracey88/libxml++-2.10.0-1_i386.deb
           => `libxml++-2.10.0-1_i386.deb'
Resolving members.iinet.net.au... 203.0.178.90
Connecting to members.iinet.net.au|203.0.178.90|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:18:09 ERROR 404: Not Found.

dpkg: error processing libxml++-2.10.0-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libxml++-2.10.0-1_i386.deb
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev
  libstdc++6-4.0-dev linux-kernel-headers make
Suggested packages:
  binutils-doc cpp-doc gcc-4.0-locales debian-keyring gcc-4.0-doc lib64stdc++6
  manpages-dev autoconf automake1.9 libtool flex bison gcc-doc libc6-dev-amd64
  lib64gcc1 glibc-doc libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  binutils build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0
  libc6-dev libstdc++6-4.0-dev linux-kernel-headers make
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.0MB of archives.
After unpacking, 47.1MB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com dapper/main linux-kernel-headers 2.6.11.2-0ubuntu18 [1039kB]
Get:2 http://security.ubuntu.com dapper-security/main binutils 2.16.1cvs20060117-1ubuntu2.1 [1407kB]
Get:3 http://ca.archive.ubuntu.com dapper/main libc6-dev 2.3.6-0ubuntu20 [2822kB]
Get:4 http://ca.archive.ubuntu.com dapper/main cpp-4.0 4.0.3-1ubuntu5 [1987kB]
Get:5 http://ca.archive.ubuntu.com dapper/main cpp 4:4.0.3-1 [31.0kB]
Get:6 http://ca.archive.ubuntu.com dapper/main gcc-4.0 4.0.3-1ubuntu5 [513kB]
Get:7 http://ca.archive.ubuntu.com dapper/main gcc 4:4.0.3-1 [5048B]
Get:8 http://ca.archive.ubuntu.com dapper/main libstdc++6-4.0-dev 4.0.3-1ubuntu5 [1471kB]
Get:9 http://ca.archive.ubuntu.com dapper/main g++-4.0 4.0.3-1ubuntu5 [2271kB]
Get:10 http://ca.archive.ubuntu.com dapper/main g++ 4:4.0.3-1 [1386B]
Get:11 http://ca.archive.ubuntu.com dapper/main make 3.80+3.81.b4-1 [286kB]
Get:12 http://ca.archive.ubuntu.com dapper/main dpkg-dev 1.13.11ubuntu6 [163kB]
Get:13 http://ca.archive.ubuntu.com dapper/main build-essential 11.1 [6826B]
Fetched 12.0MB in 32s (370kB/s)
Selecting previously deselected package binutils.
(Reading database ... 79688 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb) ...Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu18_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.6-0ubuntu20_i386.deb) ...
Selecting previously deselected package cpp-4.0.
Unpacking cpp-4.0 (from .../cpp-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package cpp.
Unpacking cpp (from .../cpp_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../make_3.80+3.81.b4-1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.11ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up binutils (2.16.1cvs20060117-1ubuntu2.1) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu18) ...
Setting up libc6-dev (2.3.6-0ubuntu20) ...
Setting up cpp-4.0 (4.0.3-1ubuntu5) ...
Setting up cpp (4.0.3-1) ...

Setting up gcc-4.0 (4.0.3-1ubuntu5) ...
Setting up gcc (4.0.3-1) ...

Setting up make (3.80+3.81.b4-1) ...

Setting up dpkg-dev (1.13.11ubuntu6) ...
Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  libsigc++-2.0-doc
The following NEW packages will be installed:
  libsigc++-2.0-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 140kB of archives.
After unpacking, 1774kB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com dapper/main libsigc++-2.0-dev 2.0.16-3 [140kB]
Fetched 140kB in 1s (131kB/s)
Selecting previously deselected package libsigc++-2.0-dev.
(Reading database ... 81812 files and directories currently installed.)
Unpacking libsigc++-2.0-dev (from .../libsigc++-2.0-dev_2.0.16-3_i386.deb) ...
Setting up libsigc++-2.0-dev (2.0.16-3) ...
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libglib2.0-dev
Suggested packages:
  libglib2.0-doc libgtkmm-2.4-dev libgtkmm-2.4-doc
The following NEW packages will be installed:
  libglib2.0-dev libglibmm-2.4-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1473kB of archives.
After unpacking, 11.2MB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com dapper-updates/main libglib2.0-dev 2.10.3-0ubuntu1 [498kB]
Get:2 http://ca.archive.ubuntu.com dapper-updates/main libglibmm-2.4-dev 2.10.4-0ubuntu1 [976kB]
Fetched 1473kB in 4s (341kB/s)
Selecting previously deselected package libglib2.0-dev.
(Reading database ... 81901 files and directories currently installed.)
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.10.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libglibmm-2.4-dev.
Unpacking libglibmm-2.4-dev (from .../libglibmm-2.4-dev_2.10.4-0ubuntu1_i386.deb) ...
Setting up libglib2.0-dev (2.10.3-0ubuntu1) ...
Setting up libglibmm-2.4-dev (2.10.4-0ubuntu1) ...

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libatk1.0-dev libcairo2-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libgtk2.0-dev libpango1.0-dev libpng12-dev libx11-dev
  libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev
  libxi-dev libxinerama-dev libxrandr-dev libxrender-dev x-dev
  x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev zlib1g-dev
Suggested packages:
  libcairo2-doc libgtk2.0-doc libpango1.0-doc
The following NEW packages will be installed:
  libatk1.0-dev libcairo2-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libgtk2.0-dev libgtkmm-2.4-dev libpango1.0-dev libpng12-dev
  libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev
  libxft-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev x-dev
  x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev zlib1g-dev
0 upgraded, 30 newly installed, 0 to remove and 0 not upgraded.
Need to get 7549kB of archives.
After unpacking, 32.1MB of additional disk space will be used.
Get:1 http://security.ubuntu.com dapper-security/main libfreetype6-dev 2.1.10-1ubuntu2.2 [677kB]
Get:2 http://ca.archive.ubuntu.com dapper/main x11proto-core-dev 7.0.4-0ubuntu2 [75.0kB]
Get:3 http://ca.archive.ubuntu.com dapper/main x11proto-kb-dev 1.0.2-0ubuntu2 [26.0kB]
Get:4 http://ca.archive.ubuntu.com dapper/main x11proto-input-dev 1.3.2-0ubuntu2 [13.0kB]
Get:5 http://ca.archive.ubuntu.com dapper/main libxau-dev 1:1.0.0-0ubuntu4 [9996B]
Get:6 http://ca.archive.ubuntu.com dapper/main libxdmcp-dev 1:1.0.0-0ubuntu2 [9358B]
Get:7 http://ca.archive.ubuntu.com dapper/main libx11-dev 2:1.0.0-0ubuntu9 [1239kB]
Get:8 http://ca.archive.ubuntu.com dapper/main x11proto-render-dev 1:0.9.2-0ubuntu2 [6090B]
Get:9 http://ca.archive.ubuntu.com dapper/main libxrender-dev 1:0.9.0.2-0ubuntu2 [23.5kB]
Get:10 http://ca.archive.ubuntu.com dapper/main libxext-dev 2:1.0.0-0ubuntu4 [72.2kB]
Get:11 http://ca.archive.ubuntu.com dapper/main libxi-dev 2:1.0.0-0ubuntu3 [61.6kB]
Get:12 http://ca.archive.ubuntu.com dapper/main x11proto-xext-dev 7.0.2-0ubuntu2 [41.1kB]
Get:13 http://ca.archive.ubuntu.com dapper/main x11proto-fixes-dev 1:3.0.2-0ubuntu2 [4858B]
Get:14 http://ca.archive.ubuntu.com dapper/main libxfixes-dev 1:3.0.1.2-0ubuntu3 [10.7kB]
Get:15 http://ca.archive.ubuntu.com dapper/main libxcursor-dev 1.1.5.2-0ubuntu4 [29.2kB]
Get:16 http://ca.archive.ubuntu.com dapper/main libexpat1-dev 1.95.8-3 [127kB]
Get:17 http://ca.archive.ubuntu.com dapper/main zlib1g-dev 1:1.2.3-6ubuntu4 [405kB]
Get:18 http://ca.archive.ubuntu.com dapper/main libfontconfig1-dev 2.3.2-1.1ubuntu12 [532kB]
Get:19 http://ca.archive.ubuntu.com dapper/main x-dev 7.0.4-0ubuntu2 [2954B]
Get:20 http://ca.archive.ubuntu.com dapper/main libxft-dev 2.1.8.2-0ubuntu2 [54.1kB]
Get:21 http://ca.archive.ubuntu.com dapper/main x11proto-xinerama-dev 1.1.2-0ubuntu2 [4596B]
Get:22 http://ca.archive.ubuntu.com dapper/main libxinerama-dev 2:1.0.1-0ubuntu2 [3916B]
Get:23 http://ca.archive.ubuntu.com dapper/main x11proto-randr-dev 1.1.2-0ubuntu2 [4252B]
Get:24 http://ca.archive.ubuntu.com dapper/main libxrandr-dev 1:1.1.0.2-0ubuntu4 [14.0kB]
Get:25 http://ca.archive.ubuntu.com dapper/main libatk1.0-dev 1.11.4-0ubuntu1 [103kB]
Get:26 http://ca.archive.ubuntu.com dapper/main libpng12-dev 1.2.8rel-5 [240kB]
Get:27 http://ca.archive.ubuntu.com dapper/main libcairo2-dev 1.0.4-0ubuntu1 [349kB]
Get:28 http://ca.archive.ubuntu.com dapper-updates/main libpango1.0-dev 1.12.3-0ubuntu1 [300kB]
Get:29 http://ca.archive.ubuntu.com dapper-updates/main libgtk2.0-dev 2.8.18-0ubuntu2 [2220kB]
Get:30 http://ca.archive.ubuntu.com dapper-updates/main libgtkmm-2.4-dev 1:2.8.8-0ubuntu1 [891kB]
Fetched 7549kB in 17s (429kB/s)
Selecting previously deselected package x11proto-core-dev.
(Reading database ... 83047 files and directories currently installed.)
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.4-0ubuntu2_all.deb) ...
Selecting previously deselected package x11proto-kb-dev.
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.2-0ubuntu2_all.deb) ...
Selecting previously deselected package x11proto-input-dev.
Unpacking x11proto-input-dev (from .../x11proto-input-dev_1.3.2-0ubuntu2_all.deb) ...
Selecting previously deselected package libxau-dev.
Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.0-0ubuntu4_i386.deb) ...
Selecting previously deselected package libxdmcp-dev.
Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.0.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package libx11-dev.
Unpacking libx11-dev (from .../libx11-dev_2%3a1.0.0-0ubuntu9_i386.deb) ...
Selecting previously deselected package x11proto-render-dev.
Unpacking x11proto-render-dev (from .../x11proto-render-dev_1%3a0.9.2-0ubuntu2_all.deb) ...
Selecting previously deselected package libxrender-dev.
Unpacking libxrender-dev (from .../libxrender-dev_1%3a0.9.0.2-0ubuntu2_i386.deb) ...
Selecting previously deselected package libxext-dev.
Unpacking libxext-dev (from .../libxext-dev_2%3a1.0.0-0ubuntu4_i386.deb) ...
Selecting previously deselected package libxi-dev.
Unpacking libxi-dev (from .../libxi-dev_2%3a1.0.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package x11proto-xext-dev.
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.0.2-0ubuntu2_all.deb) ...
Selecting previously deselected package x11proto-fixes-dev.
Unpacking x11proto-fixes-dev (from .../x11proto-fixes-dev_1%3a3.0.2-0ubuntu2_all.deb) ...
Selecting previously deselected package libxfixes-dev.
Unpacking libxfixes-dev (from .../libxfixes-dev_1%3a3.0.1.2-0ubuntu3_i386.deb) ...
Selecting previously deselected package libxcursor-dev.
Unpacking libxcursor-dev (from .../libxcursor-dev_1.1.5.2-0ubuntu4_i386.deb) ...Selecting previously deselected package libexpat1-dev.
Unpacking libexpat1-dev (from .../libexpat1-dev_1.95.8-3_i386.deb) ...
Selecting previously deselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3-6ubuntu4_i386.deb) ...
Selecting previously deselected package libfreetype6-dev.
Unpacking libfreetype6-dev (from .../libfreetype6-dev_2.1.10-1ubuntu2.2_i386.deb) ...
Selecting previously deselected package libfontconfig1-dev.
Unpacking libfontconfig1-dev (from .../libfontconfig1-dev_2.3.2-1.1ubuntu12_i386.deb) ...
Selecting previously deselected package x-dev.
Unpacking x-dev (from .../x-dev_7.0.4-0ubuntu2_all.deb) ...
Selecting previously deselected package libxft-dev.
Unpacking libxft-dev (from .../libxft-dev_2.1.8.2-0ubuntu2_i386.deb) ...
Selecting previously deselected package x11proto-xinerama-dev.
Unpacking x11proto-xinerama-dev (from .../x11proto-xinerama-dev_1.1.2-0ubuntu2_all.deb) ...
Selecting previously deselected package libxinerama-dev.
Unpacking libxinerama-dev (from .../libxinerama-dev_2%3a1.0.1-0ubuntu2_i386.deb) ...
Selecting previously deselected package x11proto-randr-dev.
Unpacking x11proto-randr-dev (from .../x11proto-randr-dev_1.1.2-0ubuntu2_all.deb) ...
Selecting previously deselected package libxrandr-dev.
Unpacking libxrandr-dev (from .../libxrandr-dev_1%3a1.1.0.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package libatk1.0-dev.
Unpacking libatk1.0-dev (from .../libatk1.0-dev_1.11.4-0ubuntu1_i386.deb) ...
Selecting previously deselected package libpng12-dev.
Unpacking libpng12-dev (from .../libpng12-dev_1.2.8rel-5_i386.deb) ...
Selecting previously deselected package libcairo2-dev.
Unpacking libcairo2-dev (from .../libcairo2-dev_1.0.4-0ubuntu1_i386.deb) ...
Selecting previously deselected package libpango1.0-dev.
Unpacking libpango1.0-dev (from .../libpango1.0-dev_1.12.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgtk2.0-dev.
Unpacking libgtk2.0-dev (from .../libgtk2.0-dev_2.8.18-0ubuntu2_i386.deb) ...
Selecting previously deselected package libgtkmm-2.4-dev.
Unpacking libgtkmm-2.4-dev (from .../libgtkmm-2.4-dev_1%3a2.8.8-0ubuntu1_i386.deb) ...
Setting up x11proto-core-dev (7.0.4-0ubuntu2) ...
Setting up x11proto-kb-dev (1.0.2-0ubuntu2) ...
Setting up x11proto-input-dev (1.3.2-0ubuntu2) ...
Setting up libxau-dev (1.0.0-0ubuntu4) ...
Setting up libxdmcp-dev (1.0.0-0ubuntu2) ...
Setting up libx11-dev (1.0.0-0ubuntu9) ...
Setting up x11proto-render-dev (0.9.2-0ubuntu2) ...
Setting up libxrender-dev (0.9.0.2-0ubuntu2) ...
Setting up libexpat1-dev (1.95.8-3) ...

Setting up zlib1g-dev (1.2.3-6ubuntu4) ...
Setting up libfreetype6-dev (2.1.10-1ubuntu2.2) ...

Setting up libfontconfig1-dev (2.3.2-1.1ubuntu12) ...
Setting up x-dev (7.0.4-0ubuntu2) ...
Setting up libxft-dev (2.1.8.2-0ubuntu2) ...
Setting up x11proto-xinerama-dev (1.1.2-0ubuntu2) ...
Setting up x11proto-randr-dev (1.1.2-0ubuntu2) ...
Setting up libatk1.0-dev (1.11.4-0ubuntu1) ...
Setting up libpng12-dev (1.2.8rel-5) ...

Setting up libcairo2-dev (1.0.4-0ubuntu1) ...
Setting up libpango1.0-dev (1.12.3-0ubuntu1) ...
Setting up libxext-dev (1.0.0-0ubuntu4) ...
Setting up libxinerama-dev (1.0.1-0ubuntu2) ...
Setting up libxrandr-dev (1.1.0.2-0ubuntu4) ...
Setting up libxi-dev (1.0.0-0ubuntu3) ...
Setting up x11proto-xext-dev (7.0.2-0ubuntu2) ...
Setting up x11proto-fixes-dev (3.0.2-0ubuntu2) ...
Setting up libxfixes-dev (3.0.1.2-0ubuntu3) ...
Setting up libxcursor-dev (1.1.5.2-0ubuntu4) ...
Setting up libgtk2.0-dev (2.8.18-0ubuntu2) ...
Setting up libgtkmm-2.4-dev (2.8.8-0ubuntu1) ...
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libglade2-dev libxml2-dev
Suggested packages:
  glade-2 glade-gnome-2 libgtkmm-2.4-doc
The following NEW packages will be installed:
  libglade2-dev libglademm-2.4-dev libxml2-dev
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1067kB of archives.
After unpacking, 5005kB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com dapper/main libxml2-dev 2.6.24.dfsg-1ubuntu1 [641kB]
Get:2 http://ca.archive.ubuntu.com dapper/main libglade2-dev 1:2.5.1-2ubuntu2 [126kB]
Get:3 http://ca.archive.ubuntu.com dapper/main libglademm-2.4-dev 2.6.2-0ubuntu1 [300kB]
Fetched 1067kB in 3s (294kB/s)
Selecting previously deselected package libxml2-dev.
(Reading database ... 85390 files and directories currently installed.)
Unpacking libxml2-dev (from .../libxml2-dev_2.6.24.dfsg-1ubuntu1_i386.deb) ...
Selecting previously deselected package libglade2-dev.
Unpacking libglade2-dev (from .../libglade2-dev_1%3a2.5.1-2ubuntu2_i386.deb) ...Selecting previously deselected package libglademm-2.4-dev.
Unpacking libglademm-2.4-dev (from .../libglademm-2.4-dev_2.6.2-0ubuntu1_i386.deb) ...
Setting up libxml2-dev (2.6.24.dfsg-1ubuntu1) ...
Setting up libglade2-dev (2.5.1-2ubuntu2) ...

Setting up libglademm-2.4-dev (2.6.2-0ubuntu1) ...

Reading package lists... Done
Building dependency tree... Done
Package libxml++2.6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  libxml++2.6c2a
E: Package libxml++2.6 has no installation candidate
wallpapoz-0.2/
wallpapoz-0.2/COPYING
wallpapoz-0.2/share/
wallpapoz-0.2/share/wallpapoz.png
wallpapoz-0.2/share/wallpapoz.desktop
wallpapoz-0.2/share/wallpapoz/
wallpapoz-0.2/share/wallpapoz/wallpapoz.png
wallpapoz-0.2/share/wallpapoz/wallpapoz.glade
wallpapoz-0.2/prefix.h
wallpapoz-0.2/bin/
wallpapoz-0.2/NEWS
wallpapoz-0.2/INSTALL
wallpapoz-0.2/walltreeview.h
wallpapoz-0.2/uninstall.sh
wallpapoz-0.2/Makefile
wallpapoz-0.2/Process.h
wallpapoz-0.2/walltreeview.cpp
wallpapoz-0.2/Process.cpp
wallpapoz-0.2/AUTHORS
wallpapoz-0.2/install.sh
wallpapoz-0.2/README
wallpapoz-0.2/wallpapoz.cpp
wallpapoz-0.2/prefix.c
wallpapoz-0.2/daemon_wallpapoz.cpp
wallpapoz-0.2/main.cpp
wallpapoz-0.2/wallpapoz.h
g++ `pkg-config libxml++-2.6 --cflags` -c daemon_wallpapoz.cpp
Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
daemon_wallpapoz.cpp:19:31: error: libxml++/libxml++.h: No such file or directory
daemon_wallpapoz.cpp: In function ‘int main()’:
daemon_wallpapoz.cpp:127: error: ‘xmlpp’ has not been declared
daemon_wallpapoz.cpp:127: error: ‘DomParser’ was not declared in this scope
daemon_wallpapoz.cpp:127: error: expected `;' before ‘parser’
daemon_wallpapoz.cpp:128: error: ‘parser’ was not declared in this scope
daemon_wallpapoz.cpp:129: error: ‘xmlpp’ has not been declared
daemon_wallpapoz.cpp:129: error: ‘Node’ was not declared in this scope
daemon_wallpapoz.cpp:129: error: ‘pNode’ was not declared in this scope
daemon_wallpapoz.cpp:130: error: ‘xmlpp’ has not been declared
daemon_wallpapoz.cpp:130: error: ‘NodeList’ was not declared in this scope
daemon_wallpapoz.cpp:130: error: expected `;' before ‘list’
daemon_wallpapoz.cpp:131: error: ‘xmlpp’ has not been declared
daemon_wallpapoz.cpp:131: error: ‘Element’ was not declared in this scope
daemon_wallpapoz.cpp:131: error: ‘el’ was not declared in this scope
daemon_wallpapoz.cpp:132: error: ‘xmlpp’ has not been declared
daemon_wallpapoz.cpp:132: error: ‘TextNode’ was not declared in this scope
daemon_wallpapoz.cpp:132: error: ‘t’ was not declared in this scope
daemon_wallpapoz.cpp:140: error: ‘xmlpp’ has not been declared
daemon_wallpapoz.cpp:140: error: expected initializer before ‘*’ token
daemon_wallpapoz.cpp:142: error: ‘xmlpp’ has not been declared
daemon_wallpapoz.cpp:142: error: ‘Attribute’ was not declared in this scope
daemon_wallpapoz.cpp:142: error: ‘attribute’ was not declared in this scope
daemon_wallpapoz.cpp:142: error: ‘element’ was not declared in this scope
daemon_wallpapoz.cpp:154: error: ‘list’ was not declared in this scope
daemon_wallpapoz.cpp:156: error: ‘xmlpp’ has not been declared
daemon_wallpapoz.cpp:156: error: missing template arguments before ‘iter’
daemon_wallpapoz.cpp:156: error: expected `;' before ‘iter’
daemon_wallpapoz.cpp:156: error: ‘iter’ was not declared in this scope
daemon_wallpapoz.cpp:162: error: ‘xmlpp’ has not been declared
daemon_wallpapoz.cpp:162: error: expected `;' before ‘workspacelist’
daemon_wallpapoz.cpp:165: error: ‘xmlpp’ has not been declared
daemon_wallpapoz.cpp:165: error: missing template arguments before ‘workspaceiter’
daemon_wallpapoz.cpp:165: error: expected `;' before ‘workspaceiter’
daemon_wallpapoz.cpp:165: error: ‘workspaceiter’ was not declared in this scope
daemon_wallpapoz.cpp:165: error: ‘workspacelist’ was not declared in this scope
daemon_wallpapoz.cpp:169: error: ‘xmlpp’ has not been declared
daemon_wallpapoz.cpp:169: error: expected initializer before ‘*’ token
daemon_wallpapoz.cpp:172: error: ‘fileelement’ was not declared in this scope
make: *** [daemon_wallpapoz.o] Error 1
Installing wallpapoz to /usr
cp: cannot stat `bin/wallpapoz': No such file or directory
cp: cannot stat `bin/daemon_wallpapoz': No such file or directory
sokuban@Arche:~$ sudo aptitude install libxml++2.6c2a
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  libxml++2.6c2a
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 61.9kB of archives. After unpacking 193kB will be used.
Writing extended state information... Done
Get:1 http://ca.archive.ubuntu.com dapper/universe libxml++2.6c2a 2.14.0-0ubuntu1 [61.9kB]
Fetched 61.9kB in 0s (90.8kB/s)
Selecting previously deselected package libxml++2.6c2a.
(Reading database ... 85956 files and directories currently installed.)
Unpacking libxml++2.6c2a (from .../libxml++2.6c2a_2.14.0-0ubuntu1_i386.deb) ...
Setting up libxml++2.6c2a (2.14.0-0ubuntu1) ...

sokuban@Arche:~$

```

Nevermind, I got it working. I just got the latest version from the site and used it. It works fine, only it takes a couple of seconds to switch wallpapers when you change desktops. I mean it is fine, (I guess I am too used to KDE.) but is that a normal problem? If it isn't maybe someone could help me. If it is normal, then I am fine.

---

### Post by Tomy on 2006-07-29
It does take a loong time to switch between desktops when using wallpapoz. Hopefully Akbar can fix this when he gets a little free time.

Tomy

---

### Post by Oppi on 2006-08-04
For total Noobs, like me:

I downloaded  the wallpapoz-0.3.tar.bz2 file from wallpapoz.sourceforge.net 

Then followed the instructions on the INSTALL-Text which is in the extracted wallpapoz-package:

_____________

To install:

1. Extract wallpapoz package
$ tar -jxvf wallpapoz-0.3.tar.bz2 
2. Go to wallpapoz directory
$ cd wallpapoz-0.3

(did not su like in step 3., rather typed sudo in 4.)

4. Install it
# sudo python install.py install

Later if you want to uninstall it:
# python install.py uninstall

However installation is optional. You can run the program from the directory
directly after you extracted it.

Just run "wallpapoz.py" in src directory to launch the gui for creating
configuration file. Then run "daemon_wallpapoz.py" to launch the daemon it
self.
____________

This worked for me ! 

Only a minor problems left:

There is no entry in my applications menu for wallpapoz. How can i fix this? I created a launcher on my panel but also want to have it in the applications menu.


Greets, Oppi

---

### Post by merinda on 2006-08-07
You must install it in order to have application menu for wallpapoz.

---

### Post by Techman010 on 2006-08-15
Thanks Oppi, that worked just fine for me.  I beleive you also need you put the daemon_wallpapoz.py in the startup programs (if you want if to always run). 

It is slow switching wallpapers, hopefully that will change in the future.

---

### Post by axiomata on 2007-09-08
I didn't have any luck with the script.  It appears to be outdated.  This was the thread that I found when googleing how to have different wallpapers on each workspace so others may come across it. Bbut I was able to get 4.1 installed from the wallpapoz homepage following the readme.

I really hope it is possible to make the change between wallpapers instantaneous when switching between workstations, especially using compiz.  Anyone know if there is a newer method to accomplish this?

---

### Post by oomingmak on 2007-09-12
> **Techman010 said:**
> It is slow switching wallpapers
I noticed that too. In fact i find it quite visually jarring to briefly see one type of wallpaper and then have it suddenly jump to another.

I therefore uninstalled this program within 2 minutes of trying it.

The program author says that it's the Gnome's implementation that causes the delay (which I can well believe) but regardless of who's to blame, the switching as it stands looks lame.

---

### Post by Paul_Ottar on 2008-01-17
```
paul@razor:~$ wallpapoz 
No configuration file. Use default configuration.
Traceback (most recent call last):
  File "/usr/local/bin/wallpapoz", line 1239, in <module>
    wallpapozgui = Wallpapoz()
  File "/usr/local/bin/wallpapoz", line 125, in __init__
    self.load_treeview()
  File "/usr/local/bin/wallpapoz", line 680, in load_treeview
    worklist = self.wallpapozxml.fill_list()
  File "../share/wallpapoz/lib/xml_processing.py", line 247, in fill_list
    worklist[index].append(node.firstChild.data)
AttributeError: 'NoneType' object has no attribute 'data'

```

Anyone else have this problem? Searched around on google, but only found french pages where people have the same problem. Tried to find some commands in there, but I didn't... And I don't understand French ;)

---

### Post by PartisanEntity on 2008-04-07
Worked fine for me in Gutsy, but unfortunately still takes 1-3 seconds to change desktop wallpaper when switching workspaces. I'm going to write the author to thank him for making it and to enquire about any improvements and time frame that could be expected for further releases.

---

### Post by dushy4 on 2010-04-08
Sorry to bump into such a old thread but i just found the solution at some other site.
I had the following error while running wallpapoz:
/usr/local/bin/wallpapoz
Traceback (most recent call last):
 File "/usr/local/bin/wallpapoz", line 1239, in <module>
   wallpapozgui = Wallpapoz()
 File "/usr/local/bin/wallpapoz", line 125, in __init__
   self.load_treeview()
 File "/usr/local/bin/wallpapoz", line 680, in load_treeview
   worklist = self.wallpapozxml.fill_list()
 File "../share/wallpapoz/lib/xml_processing.py", line 247, in fill_list
   worklist[index].append(node.firstChild.data)
AttributeError: 'NoneType' object has no attribute 'data'

and the solution is at: [http://wallpapoz.akbarhome.com/faq.html](http://wallpapoz.akbarhome.com/faq.html)

which is 
Open the Wallpapoz configuration file, /home/your_user_name/.wallpapoz/wallpapoz.xml.
You will have something like this:
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE Wallpapoz>
<wallpapoz interval="5" random="0" style="2" type="workspace">
   <workspace name="rename this" no="1">
       <file></file>
   </workspace>
   <workspace name="rename this" no="2">
       <file></file>
   </workspace>
</wallpapoz>
Make it something like this:
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE Wallpapoz>
<wallpapoz interval="5" random="0" style="2" type="workspace">
   <workspace name="rename this" no="1">
       <file>blabla</file>
   </workspace>
   <workspace name="rename this" no="2">
       <file>blabla</file>
   </workspace>
</wallpapoz>
Restart Wallpapoz.

works perfectly!!!!

---

