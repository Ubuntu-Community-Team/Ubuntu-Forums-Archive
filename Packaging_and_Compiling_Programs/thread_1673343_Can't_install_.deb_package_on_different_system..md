---
title: "Can't install .deb package on different system."
date: 2011-01-22
forum: Packaging and Compiling Programs
---

### Post by buzai.andras on 2011-01-22
Hi,

I created a .deb package (for ed version 1.0) following the instructions from MOTU videos ([http://www.youtube.com/watch?v=VyEl3w7SFK4](http://www.youtube.com/watch?v=VyEl3w7SFK4)).
The problem is that the resulting package can be installed properly on the build machine,
but when I try to install it on another machine I get the following errors:
[INDENT] (Reading database ... 24041 files and directories currently installed.)
Unpacking ed (from ed_1.0-0ubuntu1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg: error processing ed_1.0-0ubuntu1_i386.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste returned error exit status 2
Errors were encountered while processing:
 ed_1.0-0ubuntu1_i386.deb
[/INDENT]Both machines are Ubuntu 10.04 LTS running inside VirtualBox.
Both virtual machines have the same hardware configuration.
Any ideas what could be the problem? What I did wrong?

Thank you,

Buzai

---

### Post by SevenMachines on 2011-01-22
"short read in buffer_copy (failed to write to pipe in copy)" usually means you haven't got the complete archive but you've only partially copied it across or downloaded it. Try transferring the file again and check chat the file sizes of the two things are the same

---

### Post by buzai.andras on 2011-01-22
Unfortunately that didn't solve the error.
I tried to copy it again over FTP and HTTP but the result is the same.
It installs properly on the machine it was built on, but it won't install on another machine :(.

Thank you,

Buzai

---

### Post by SevenMachines on 2011-01-22
Did you compare the size of the original and the copy?

---

### Post by gmargo on 2011-01-22
Also compare a checksum. 

Do you have a **preinst** or **postinst** script?  Does it rely on something that's installed on one system but not the other?

---

### Post by buzai.andras on 2011-01-22
Thank you both for your reply.
You were right; it seems that the copy was not performed properly. The copied file was smaller with 1 byte.
After a reboot of the virtual machines the copy was performed properly and I could install the package :D

Thank you for your help,

Buzai

---

