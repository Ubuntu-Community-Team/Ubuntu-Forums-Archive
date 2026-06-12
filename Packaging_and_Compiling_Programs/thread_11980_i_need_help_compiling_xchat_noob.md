---
title: "i need help compiling xchat *noob*"
date: 2005-01-20
forum: Packaging and Compiling Programs
---

### Post by akurashy on 2005-01-20
i downloaded the new source of xchat 
can someone help me how to compile it :(

---

### Post by Viro on 2005-01-21
[QUOTE=akurashy]i downloaded the new source of xchat 
can someone help me how to compile it :([/QUOTE]
 > 
tar -xvzf *package*.tar.gz or tar -xvjf *package*.tar.bz2
cd *package*
./configure
make
*wait for a bit while everything compiles*
sudo make install


That's assuming nothing goes wrong :). If something does, just post back.

---

### Post by az on 2005-01-21
Three steps.

1-  Extract the archive.  Use either nautilus or the command line
tar xvzf xchat*

2-  Enter the new directory
cd xchat*

3-  Read the *README
nano README


*  This may be named INSTALL.TXT or something else.

P.S.  To compile stuff on your system you need the build-essential package.
sudo apt-get install build-essential

Good Luck.
Typically the way it should go is, 
1-install the neccessary dependand packages (-dev packages)  These are needed for compiling (DEVelopment)
2-./configure
3-make
4-make install

But just read the readme.

---

### Post by sirukin on 2005-02-01
I've compiled it myself, the only problem is....
I have no perl/python plugins.
apt-cache search perl
apt-get install perl
apt-get install libgtk2-dev
etc

---

### Post by Jad on 2005-02-01
why not just Apt get it ?

---

### Post by dikki on 2005-02-01
Well I don't get it. I downloaded the newest source, untarred, it, ./configure:

[...]

checking for GLIB - version >= 2.0.3... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: "Cannot find glib"

---

### Post by Roptaty on 2005-02-01
Why do you don't apt get it? 
sudo apt-get install xchat

---

### Post by dikki on 2005-02-01
The Warty contains 2.0.1 or something like that. apt says xchat already the newest version.
The source I'd like to install is 2.4.1.

---

### Post by ubuntu UsER on 2005-02-01
[QUOTE=dikki]The Warty contains 2.0.1 or something like that. apt says xchat already the newest version.
The source I'd like to install is 2.4.1.[/QUOTE]

There is 2.4.1 in backports repository :)

[http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe 

Enjoy!

---

### Post by dikki on 2005-02-01
Thanks :-) I have ubuntu only since yesterday (today) I don't know these tricks yet ;)

---

### Post by crane on 2005-02-01
[QUOTE=ubuntu UsER]There is 2.4.1 in backports repository :)

[http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe 

Enjoy![/QUOTE]

Yep, thats where I got mine. Version 2.4.1 Works great!

---

### Post by dikki on 2005-02-02
Thanks, it's great :) I upgraded my Firefox a bit strange way (downloaded the bin from mozilla.org, installed to /etc/mozilla-firefox, rm-ed the /usr/bin/firefox and mozilla-firefox files, and symlinked the new ones to the /etc/mozilla-firefox/firefox file :) ) but you say, the apt-get from the backports is the easier way? :P Thx, got the 2.4.1 now.

---

