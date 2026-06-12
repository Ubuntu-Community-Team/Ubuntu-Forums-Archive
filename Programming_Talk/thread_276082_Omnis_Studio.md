---
title: "Omnis Studio"
date: 2006-10-12
forum: Programming Talk
---

### Post by AAM on 2006-10-12
Had a long time running Linux and been through many distros but not really dug deeply into any. Don't have the background and the learning curve is steep! 

I have a medical record project that requires a GUI sitting over a database (how common is that!) and I am searching for a Rapid Development Application that is GUI based and 'friendly'. I have come across Omnis Studio and wanted to give the downloadable a run. So I downloaded the rpm and used *alien* to install as a deb package. All this went well.

However I have been unable to run the program from CLI or desktop launcher - message says "**cannot execute binary file**". I have tried typing 

[INDENT]**sudo sh omnis** and **sh omnis**[/INDENT]

but the answer is unchanging. The file resides in

[INDENT]**/usr/local/rainingdata/os4**[/INDENT]

and has the permissions 

[INDENT]**-rwxr-xr-x**[/INDENT]

In addition, Nautilus recognises the file as an **executable**.

I just feel that I am missing something obvious, other than the application not working! Any help would be appreciated,

AAM

---

### Post by AAM on 2006-10-13
One step forward in fixing the problem!

The shell command to be run is NOT omnis, but that of the shell script **omnisI386** in the same directory.

Now there is a problem in omnis.cfg - another day another problem!

AAM

---

### Post by johnaaronrose on 2011-03-21
I'm trying to install Omnis Studio 5.1 under Ubuntu 10.04. I get "Cannot initialize: Error creating file Omnis.cfg". Any ideas?

PS Only thing that I can think of is that LD_LIBRARY_PATH is not used any longer in 10.04 - procedure is to now create in /etc/ld.so.conf.d a .conf file containing a path reference to the os51 directory (i.e. where Omnis Studio is installed). Running sudo ldconfig & sudo ldconfig --verbose shows that the Omnis Studio files have been 'picked up'. Running ./omset is successful and creates the omnisI386 shell script. This shell script contains:
#!/bin/sh
LD_LIBRARY_PATH=/opt/OmnisStudio/os51:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH
/opt/OmnisStudio/os51/omnis $1 $2 $3 $4 $5 $6 $7 $8

However, echo $LD_LIBRARY_PATH and printenv LD_LIBRARY_PATH both show nothing.

I've tried executing (in terminal) /opt/OmnisStudio/os51/omnis but that gives 
"/opt/OmnisStudio/os51/omnis: error while loading shared libraries: omnisxi.so: cannot open shared object file: No such file or directory"
However, omnisxi.so does exist in /opt/OmnisStudio/os51/.

---

### Post by ikt on 2011-03-21
that's quite a thread necro you got thar :P

Are you following this guide?

[http://www.linuxuser.co.uk/tutorials/get-started-with-omnis-studio/](http://www.linuxuser.co.uk/tutorials/get-started-with-omnis-studio/)

---

### Post by slavik on 2011-03-21
back into the ground with you

---

