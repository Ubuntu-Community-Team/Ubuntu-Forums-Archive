---
title: "Error installing Plymouth-manager"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-05-19
I downloaded and installed the Pymouth-manager.
```

glenn@acer:~/Downloads$ sudo dpkg -i plymouth-manager_1.5.0-1_all.deb
Selecting previously unselected package plymouth-manager.
(Reading database ... 247598 files and directories currently installed.)
Unpacking plymouth-manager (from plymouth-manager_1.5.0-1_all.deb) ...
dpkg: dependency problems prevent configuration of plymouth-manager:
plymouth-manager depends on python-glade2; however:
Package python-glade2 is not installed.
dpkg: error processing plymouth-manager (--install):
dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 plymouth-manager
glenn@acer:~/Downloads$

```And ran it from the gnome menu, but nothing happened. So I ran it from the command prompt and got the following error message:
```

glenn@acer:~/Downloads$ plymouth-manager
Traceback (most recent call last):
File "plymouth-manager.py", line 20, in <module>
import main
File "/usr/share/plymouth-manager/src/main.py", line 20, in <module>
import gtk, gtk.glade, pygtk                        #pygtk modules
ImportError: No module named gtk
glenn@acer:~/Downloads$ 

```So I downloaded python-glade2:
```

glenn@acer:~/Downloads$ sudo apt-get install python-glade2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
python-gtk2-doc
The following NEW packages will be installed:
python-glade2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 9,870 B of archives.
After this operation, 116 kB of additional disk space will be used.
Get:1 http://nz.archive.ubuntu.com/ubuntu/ precise/main python-glade2 i386 2.24.0-3 [9,870 B]
Fetched 9,870 B in 0s (23.2 kB/s)        
Selecting previously unselected package python-glade2.
(Reading database ... 247671 files and directories currently installed.)
Unpacking python-glade2 (from .../python-glade2_2.24.0-3_i386.deb) ...
Setting up python-glade2 (2.24.0-3) ...
Setting up plymouth-manager (1.5.0-1) ...
Processing triggers for python-support ...
glenn@acer:~/Downloads$ plymouth-manager
Traceback (most recent call last):
File "plymouth-manager.py", line 20, in <module>
import main
File "/usr/share/plymouth-manager/src/main.py", line 20, in <module>
import gtk, gtk.glade, pygtk                        #pygtk modules
ImportError: No module named gtk
glenn@acer:~/Downloads$ 

```Does anyone have a fix for this error?

---

### Post by jtarin on 2012-05-19
Is it possible at some point you had problems with a python install? [Check this.]("https://answers.launchpad.net/ubuntu/+source/gui-ufw/+question/142613")

---

### Post by Senior_Buckethead on 2012-05-19
Thanks Jtarin

Followed link to page:[https://answers.launchpad.net/ubuntu/+source/gui-ufw/+question/142613](https://answers.launchpad.net/ubuntu/+source/gui-ufw/+question/142613)
and followed this instruction:
> 
Please try to install/reinstall python-gtk2 from terminal type:
 sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo apt-get --reinstall install python-gtk2
 give your user password when requested, you don't see nothing when you type it, then press enter
 Then retry...

Then ran plymouth-manager and received the following error message:

```
glenn@acer:/var/www$ plymouth-manager
Traceback (most recent call last):
File "plymouth-manager.py", line 20, in <module>
import main
File "/usr/share/plymouth-manager/src/main.py", line 20, in <module>
import gtk, gtk.glade, pygtk                        #pygtk modules
ImportError: No module named gtk
glenn@acer:/var/www$ 

```I don't know how to attack this problem. Does it mean that my python installation is corrupt and need to be reinstalled, or is it a local problem with plymouth-manager?

---

### Post by jtarin on 2012-05-19
Maybe your install of the PyGTK module has gone wrong, To prove this run python from CLI (just type python into your console) and at the python prompt type "import pygtk". Do you get the import error again showing that pygtk is not setup right or does it complete with no error?
BTW...what desktop are you running?

---

### Post by Senior_Buckethead on 2012-06-04
Yeah my Python install had screwed the pooch. Reinstall fixed problem.

---

### Post by jtarin on 2012-06-04
YAAA! Mark it solved then.:p

---

