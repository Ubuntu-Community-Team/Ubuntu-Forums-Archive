---
title: "python-wxgtk 2.8"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by kmb9205 on 2013-09-26
I have tried quite a few times to upgrade to python-wxgtk 2.8
My install has python 2.7

I have used:
 **sudo apt-get install python-wxgtk2.8**

and I get this back:

kb@kb-OptiPlex-745:~$ sudo apt-get install python-wxgtk2.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
Suggested packages:
  wx2.8-doc wx2.8-examples editra
The following NEW packages will be installed:
  python-wxgtk2.8
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/5,078 kB of archives.
After this operation, 20.8 MB of additional disk space will be used.
(Reading database ... 175993 files and directories currently installed.)
Unpacking python-wxgtk2.8 (from .../python-wxgtk2.8_2.8.12.1-6ubuntu2_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/python-wxgtk2.8_2.8.12.1-6ubuntu2_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
                                                                                         Errors were encountered while processing:
 /var/cache/apt/archives/python-wxgtk2.8_2.8.12.1-6ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


it also says: (when I open the Software Center and it tries to complete the installation)
the following packages have unmet dependencies
playonlinux : depends: python-wxgtk 2.8 but it is not installed


AGAIN....any and all help would be greatly appreciated as I am quite the noob to linux

---

### Post by kmb9205 on 2013-09-26
I have tried 
[B]sudo apt-get -f autoremove

[/B]and got this back

:~$ sudo apt-get -f autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-wxgtk2.8
Suggested packages:
  wx2.8-doc wx2.8-examples editra
The following packages will be REMOVED:
  thunderbird-globalmenu
The following NEW packages will be installed:
  python-wxgtk2.8
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/5,078 kB of archives.
After this operation, 20.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 175993 files and directories currently installed.)
Unpacking python-wxgtk2.8 (from .../python-wxgtk2.8_2.8.12.1-6ubuntu2_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/python-wxgtk2.8_2.8.12.1-6ubuntu2_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
                                                                                         Errors were encountered while processing:
 /var/cache/apt/archives/python-wxgtk2.8_2.8.12.1-6ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kmb9205 on 2013-09-26
never mind.....i just deleted PlayOnLinux and all associated....installed Synaptic....installed python and did it that way

---

