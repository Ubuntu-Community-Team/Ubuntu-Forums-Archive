---
title: "compiling openssl error"
date: 2014-02-16
forum: Packaging and Compiling Programs
---

### Post by beelzebufo on 2014-02-16
this is really confusing, I am sure I am just not seeing something.  I am trying to install a snort monitor from source and the ./configure fails due to an openssl error, but I have openssl installed, not sure what to do, whether the monitor wants ubuntu to be an earlier version where openssl is installed somewhere else maybe?  I am running ubuntu 13.10 btw.

```
checking for OpenSSL... Error: SSL is required to build this package.
wreckingball@wreckingball-pc:~/sntm$ sudo apt-get install openssl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

any help would be greatly appreciated, I am befuddled.

thanks in advance
Beelze

---

### Post by wiremoons on 2014-02-16
Hi beelzebufo

If you are compiling a program from source code, I expect you need to install the development libraries also for OpenSSL.  Run this command from the Terminal window:

**[FONT=Courier New]sudo apt-get install libssl-dev[/FONT]**

Then re-run the ./configure command, and hopefully it will get past that error :)

You can check other SSL library packages that are available with the commands:

[FONT=Courier New]**sudo apt-cache search libssl **[/FONT]and [FONT=Courier New]**apt-cache search openssl**[/FONT]

If you want more information about one of the packages (say 'libssl-dev') use the command:

[FONT=Courier New]**sudo apt-cache show libssl-dev**[/FONT]

and it will tell you what the package is for, who maintains it, dependencies, version, etc.

Hope that helps

---

### Post by beelzebufo on 2014-02-16
thank you very much for the response, however, unfortunately it did not work.  I think I have installed every openssl related package known by now and I am still getting the error.   Any other ideas?

---

### Post by wiremoons on 2014-02-16
You can install the Ubuntu repository version (2.9.2.2-3) to save compiling it with the command:

[FONT=Courier New]**sudo apt-get install snort**[/FONT]

as I expect you already know :)

However - if you realy want to compile it to create your own bespoke version that is up to date you can follow these steps:

Download the source code from the Snort web site here: *[http://www.snort.org/snort-downloads?](http://www.snort.org/snort-downloads?)*   (ie the file **snort-2.9.6.0.tar.gz**)

1) Go to your Downloads folder in your Terminal window (ie **cd ~/Downloads** )
2) Unpack the tar gzip file ( ie  **tar -xzvf snort-2.9.6.0.tar.gz** )
3) Go into the directory it unpacked into:  (ie  **cd snort-2.9.6.0/** )
4) Install all the development libraries, compiler etc; ( ie **sudo apt-get install build-essential linux-headers-$(uname -r) libcap-dev libcap-ng-dev libpcap-dev libssl-dev libpcre3-dev libdnet-dev libdumbnet-dev libdaq-dev flex bison** )
5) ./configure
6) make

The above worked for me on a clean Gnome Ubuntu 13.10 install - so hopefully you will get the same result.

---

### Post by oldos2er on 2014-02-16
Moved to Packaging & Compiling Programs.

beelzebufo, can you provide a link to the source you downloaded? Also look in any README and/or INSTALL files for a list of dependencies you might need.

---

### Post by beelzebufo on 2014-02-16
thanks Ann, yes I can, the project home is [http://sourceforge.net/projects/sntm/](http://sourceforge.net/projects/sntm/) it looks like I need to do a heavily modified ./configure with custom locations for openssl, qt and iodbc. I am not going to bother, I spent enough hours with snort and it's friends to have saved some starving children or solved the world's political problems.  Obviously it's just not meant to be for me to have a front end for snort on this machine at this time.  Thank you guys for all the help.  You can close this thread.

---

### Post by oldos2er on 2014-02-16
That is really old, it expects a 2.4x kernel. Maybe it's a good thing to leave it alone.

---

