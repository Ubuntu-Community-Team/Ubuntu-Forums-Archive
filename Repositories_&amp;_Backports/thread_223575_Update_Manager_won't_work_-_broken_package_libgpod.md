---
title: "Update Manager won't work - broken package libgpod0_0.3.2-0ubuntu1_i386.deb"
date: 2006-07-26
forum: Repositories &amp; Backports
---

### Post by morrisonpeter on 2006-07-26
Hello Everyone, hopefully I found the right forum to post in, correct me if I'm wrong.

I just tried to run the update manager under the systems menu, but I get an error:

> It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

So after i "sudo apt-get install -f" in the console, I get this:
> 
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgpod0
Recommended packages:
  libgpod-common
The following NEW packages will be installed:
  libgpod0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/64.2kB of archives.
After unpacking, 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 175288 files and directories currently installed.)
Unpacking libgpod0 (from .../libgpod0_0.3.2-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgpod0_0.3.2-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgpod.so.0', which is also in package libgpod
Errors were encountered while processing:
 /var/cache/apt/archives/libgpod0_0.3.2-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can anyone help me fix this?  I'm somewhere between a noob to an average user.

---

### Post by ajgreeny on 2006-07-26
Simplest way is to open up synaptic and go to edit>fix broken packages and see if that sorts out the problem.  I hope it does, but if not open a terminal and type:-
sudo sudo apt-get install -f libgpod0
and see if that fixes the problem.  If you still have a problem after that I think you need to purge the offending package with:-
sudo apt-get remove libgpod0
or if you prefer using synaptic try to remove it that way.

---

### Post by morrisonpeter on 2006-07-27
Well, uninstalling gtkpod seemed to work for me.  I have already tried your suggestions, and it seems to me that libgpod.so.0 was installed without a package somehow, anyways I can't install libgpod or gtkpod because it hangs when it tries to write that file...  maybee automatix or some other script I tried off the net installed those files and now it's screwing with synaptic.  

Is there an option to force writing over any other files it finds when installing the package?  I'm a noob, so maybee that's too dangerous, I don't know.  I've tried deleting the file libgpod.so.0, but that didn't seem to help either.

Hopefully I can still access my ipod's songs, I don't really know what gtkpod was!  If it's not important, then I guess I can live without it.

---

