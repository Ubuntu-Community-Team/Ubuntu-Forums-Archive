---
title: "Tcl Rivet Make Problem"
date: 2010-04-09
forum: Packaging and Compiling Programs
---

### Post by notlistening on 2010-04-09
Hi all,

I have just moved to Lucid server 10.04 and have been trying to setup a new web server that uses rivet in apache. When I try to compile the rivet source I get all the way through until I get to the make stage when it errors out. I think these is a problem with autoconf.

This can be easily reproduced if your running either server or desktop and I do not have the knowledge or skill to begin to fix this, 

Step to reproduce:

sudo apt-get install apache2 mysql-server php5-mysql phpmyadmin libtool build-essential automake apache2-threaded-dev subversion tcl8.5 tcl8.5-dev

svn co [http://svn.apache.org/repos/asf/tcl/rivet/trunk](http://svn.apache.org/repos/asf/tcl/rivet/trunk) rivet

cd rivet

aclocal
autoreconf -i -f
./configure --with-tcl=/usr/lib/tcl8.4 --with-apxs=/usr/bin/apxs2
make

Then you will see this output:

[http://pastebin.org/142677](http://pastebin.org/142677)

Any ideas / help would be great

---

### Post by SevenMachines on 2010-04-10
i think when i saw this before the fix was to add the m4/* files to aclocal.m4 manually
$cat m4/* >> aclocal.m4

not sure if thats the 'correct' way, if someone knows it i'd be interested to hear, it does work though

---

