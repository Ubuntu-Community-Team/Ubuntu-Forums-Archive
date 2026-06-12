---
title: "HowTo: Install Peer Guardian for Linux"
date: 2005-11-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Arktis on 2005-11-28
1.) You'll need to install the following packages:

```
sudo apt-get install libncurses5-dev iptables-dev checkinstall automake1.9 texinfo
```

2.) Then, go [here]("http://prdownloads.sourceforge.net/peerguardian/") and grab the latest linux version, currently "pglinux-1.5beta.tar.gz", near the bottom of the list of files there. (***Note:** These instructions may not apply to future versions of pglinux, but as of the time of this post, they do.)

3.) Extract it somewhere in our home directory, then in a terminal cd to that location.

4.) Now we must edit the configure file:

```
gedit configure
```

Go to line 1316 and change am__api_version="1.4" to am__api_version="1.9", then save and exit.

5.) Run configure:

```
./configure
```

6.) Then edit the makefile:

```
gedit Makefile
```

Go to line 80 and change mkinstalldirs = $(SHELL) $(top_srcdir)/../mkinstalldirs to mkinstalldirs = $(SHELL) $(top_srcdir)/mkinstalldirs, then save and exit.

7.) Run make:

```
make
```

8.) Run checkinstall:

```
sudo checkinstall
```

You should be done now!  The rest is optional:

When checkinstall completes, the newly created package will be installed.  It will also have put a file called "pglinux-1.5beta_1.5beta-1_i386.deb" inside the current directory.  You may wish to rename this and change it's permissions:

```
sudo chown your_username_here pglinux-1.5beta_1.5beta-1_i386.deb
```
then
```
mv pglinux-1.5beta_1.5beta-1_i386.deb pglinux-1.5beta-1_i386.deb
```
Now the filename for the package is proper, plus you can move it around as a normal user.  I suggest storing it somewhere you keep backup files so that you can install it again later with dpkg thus avoiding going through all the above steps.

For instance, if you fresh install breezy again one day, you need only do step one of this guide, then use dpkg on your backed-up peer guardian package:
```
sudo dpkg -i /path/to/package/pglinux-1.5beta-1_i386.deb
```

---

### Post by Grimlock on 2005-11-30
Cheers for the how to but i am having problems with make. My error i this

richie@ubuntu:~/pglinux-1.5beta$ make
cd . && automake-1.9 --gnu Makefile
configure.ac:6: version mismatch.  This is Automake 1.9.5,
configure.ac:6: but the definition used by this AM_INIT_AUTOMAKE
configure.ac:6: comes from Automake 1.4-p6.  You should recreate
configure.ac:6: aclocal.m4 with aclocal and run automake again.
Makefile.am: required file `./depcomp' not found
/usr/share/automake-1.9/am/depend2.am: am__fastdepCXX does not appear in AM_CONDITIONAL
/usr/share/automake-1.9/am/depend2.am: AMDEP does not appear in AM_CONDITIONAL
make: *** [Makefile.in] Error 63
richie@ubuntu:~/pglinux-1.5beta$

I have tried reverting back to auto make 1.4 and it didn't work either. Could you help me at all? As I used to use this in windows.

---

### Post by no1wantdthisname on 2005-11-30
Same problem.
EDIT: Solved it by just getting automake and not changing the configure file.  Everything else is same though.

---

### Post by Arktis on 2005-11-30
People may also find this different method howto useful:
[http://ubuntuforums.org/showthread.php?t=95793](http://ubuntuforums.org/showthread.php?t=95793)
I didn't see it because I spelled guardian wrong In my search before I posted this. :rolleyes:

---

### Post by ace2005 on 2005-12-04
Can i ask, what does it show when you do a scan at sygate's site?

[http://scan.sygatetech.com/prestealthscan.html](http://scan.sygatetech.com/prestealthscan.html)

---

### Post by smoove on 2006-08-09
> **no1wantdthisname said:**
> Same problem.
EDIT: Solved it by just getting automake and not changing the configure file.  Everything else is same though.

What do you mean by this? i dont understand sorry, only just got linux. I got stuck at the same part.

---

### Post by smoove on 2006-08-11
Great help :mad:

---

### Post by smoove on 2006-08-14
bump

---

### Post by njzillest on 2006-08-14
thanks alot man.. good good good lookz

---

### Post by MachineBucket on 2006-08-21
I get this error when I try to run checkinstall. Any ideas on what I'm doing wrong?

```
dpkg: error processing /home/machinebucket/Desktop/pglinux-1.5beta/pglinux-1.5beta_1.5beta-1_x86_64.deb (--install):
 package architecture (x86_64) does not match system (amd64)
Errors were encountered while processing:
 /home/machinebucket/Desktop/pglinux-1.5beta/pglinux-1.5beta_1.5beta-1_x86_64.deb
```

Thanks.

EDIT: I got it working by changing the architecture during checkinstall from x86_64 to amd64.

---

