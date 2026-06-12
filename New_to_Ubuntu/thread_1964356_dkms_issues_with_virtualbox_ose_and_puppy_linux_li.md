---
title: "dkms issues with virtualbox ose and puppy linux libre office edition"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by Doxa on 2012-04-23
Hi, I'm on Ubuntu 10.04 LTS.  I've been working on and reading the help file off of virtualbox ose all day and i just can't seem to get it right.

I installed it, and now when I go to install lupu 5.2.8, it says that I do not have the dkms files, so I opened a terminal and installed the dkms files: 

doxa@Gloria:~$ sudo apt-get install virtualbox-ose-dkms
[sudo] password for doxa: 
Sorry, try again.
[sudo] password for doxa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose-dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up virtualbox-ose-dkms (3.1.6-dfsg-2ubuntu2) ...
Removing old virtualbox-ose-3.1.6 DKMS files...

-------- Uninstall Beginning --------
Module:  virtualbox-ose
Version: 3.1.6
Kernel:  2.6.32-02063223-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-02063223-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-02063223-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-02063223-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.......

DKMS: uninstall Completed.

------------------------------
Deleting module version: 3.1.6
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-ose-3.1.6 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-19-generic
Building for architecture i686
Building initial module for 3.0.0-19-generic

Error! Bad return status for module build on kernel: 3.0.0-19-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/virtualbox-ose/3.1.6/build/ for more information.
dpkg: error processing virtualbox-ose-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 virtualbox-ose-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
doxa@Gloria:~$ sudo apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up virtualbox-ose-dkms (3.1.6-dfsg-2ubuntu2) ...
Removing old virtualbox-ose-3.1.6 DKMS files...

------------------------------
Deleting module version: 3.1.6
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-ose-3.1.6 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-19-generic
Building for architecture i686
Building initial module for 3.0.0-19-generic

Error! Bad return status for module build on kernel: 3.0.0-19-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/virtualbox-ose/3.1.6/build/ for more information.
dpkg: error processing virtualbox-ose-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 virtualbox-ose-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
doxa@Gloria:~$ 

so this is what I got.
I have a few kernels installed.  I do not know how to uninstall them and I am unable at this point to reinstall because EVERYTHING is on this computer now.  I downloaded this program because it is long term support.  The only thing is that I can't find documentation that makes for any of this to be easy.  
I sit for hours searching for things and get five or six ideas, but then when it comes down to it, none of them work.

Could someone help me?
Thanks!

8-[ :oops:

---

### Post by Doxa on 2012-04-23
oh! and this just happened, my fglrx failed.  According to the little exclamation point in the explosion bubble on the top right hand side, it did it did. 

So what do I do about all this?

oh! and the 

linux-headers-3.0.0-19 3.0.0-19.33~lucid1 
oss4-dkms
linux-image-3.0.0-19-generic 3.0.0-19.33~lucid1
virtualbox-ose-dkms

just all failed on me as well.

Gah...! Did I break my machine?

---

### Post by Doxa on 2012-04-23
uninstall and reinstall :

doxa@Gloria:~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose-qt
doxa@Gloria:~$ sudo apt-get install virtualbox-ose-qt
[sudo] password for doxa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  virtualbox-ose virtualbox-ose-dkms
Suggested packages:
  virtualbox-guest-additions
The following NEW packages will be installed:
  virtualbox-ose virtualbox-ose-dkms virtualbox-ose-qt
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/13.4MB of archives.
After this operation, 47.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package virtualbox-ose.
(Reading database ... 286795 files and directories currently installed.)
Unpacking virtualbox-ose (from .../virtualbox-ose_3.1.6-dfsg-2ubuntu2_i386.deb) ...
Selecting previously deselected package virtualbox-ose-dkms.
Unpacking virtualbox-ose-dkms (from .../virtualbox-ose-dkms_3.1.6-dfsg-2ubuntu2_all.deb) ...
Selecting previously deselected package virtualbox-ose-qt.
Unpacking virtualbox-ose-qt (from .../virtualbox-ose-qt_3.1.6-dfsg-2ubuntu2_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up virtualbox-ose (3.1.6-dfsg-2ubuntu2) ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox-ose, action "restart" failed.

Setting up virtualbox-ose-dkms (3.1.6-dfsg-2ubuntu2) ...
Loading new virtualbox-ose-3.1.6 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-19-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox-ose, action "restart" failed.

Processing triggers for python-central ...
Setting up virtualbox-ose-qt (3.1.6-dfsg-2ubuntu2) ...

---

