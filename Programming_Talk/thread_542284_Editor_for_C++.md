---
title: "Editor for C++"
date: 2007-09-03
forum: Programming Talk
---

### Post by paneas13 on 2007-09-03
Is there any similar to Dev++ in Ubuntu Linux ?

---

### Post by Mirrorball on 2007-09-03
Eclipse + CDT plugin (my favorite)
Anjuta
Kdevelop
Netbeans with C++ support
Code::Blocks

---

### Post by ryno519 on 2007-09-03
KDevelop is my favourite and I use GNOME. I would have to recommend that. I didn't like Anjuta too much, but others seem to like it a lot. Just not my cup of tea I guess.

---

### Post by samjh on 2007-09-03
> **paneas13 said:**
> Is there any similar to Dev++ in Ubuntu Linux ?

Codeblocks is probably the most similar:
[www.codeblocks.org](www.codeblocks.org)

To download the nightly build (do not use the RC version, it is very old), go here and download one of the pre-built .deb files.  Take note that the version of wxwidgets required for Codeblocks is newer than supplied by Ubuntu repos, but the pre-build Ubuntu packages should have the newer wxwidgets included:
[http://forums.codeblocks.org/index.php?board=20.0](http://forums.codeblocks.org/index.php?board=20.0)

The latest Ubuntu 6.10/7.04 build can be downloaded directly here (August 31st release):
[http://prdownload.berlios.de/codeblocks/CB_20070831_rev4418_Ubuntu6.10+7.04_wx2.8.4.tar.gz](http://prdownload.berlios.de/codeblocks/CB_20070831_rev4418_Ubuntu6.10+7.04_wx2.8.4.tar.gz)

---

### Post by Arwen on 2007-09-17
Hello,I downloaded codeblocks from [http://prdownload.berlios.de/codeblocks/CB_20070831_rev4418_Ubuntu6.10+7.04_wx2.8.4.tar.gz](http://prdownload.berlios.de/codeblocks/CB_20070831_rev4418_Ubuntu6.10+7.04_wx2.8.4.tar.gz) but when I double click on each of the .deb files I get when I un-tar it,it says "Error:Dependency is not satisfiable:libcodeblocks0"
Does anyone know what can I do about it?
Thanx..

---

### Post by cstudent on 2007-09-17
> **Arwen said:**
> Hello,I downloaded codeblocks from [http://prdownload.berlios.de/codeblocks/CB_20070831_rev4418_Ubuntu6.10+7.04_wx2.8.4.tar.gz](http://prdownload.berlios.de/codeblocks/CB_20070831_rev4418_Ubuntu6.10+7.04_wx2.8.4.tar.gz) but when I double click on each of the .deb files I get when I un-tar it,it says "Error:Dependency is not satisfiable:libcodeblocks0"
Does anyone know what can I do about it?
Thanx..

From the Codeblocks Wiki page: [http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu)

 Since revision 4281 and after, the nightly builds are made differently. Codeblocks is now packaged into separate Debian packages and the packages are archived together in a tar.gz file.

1. Download the tar.gz file to your computer and extract the files to an empty directory, such as one called temp for example.

```
tar xvf CB_date-of-build_revision-number_Ubuntu6.10+7.04_wx2.8.4.tar.gz

```
2. Install all the packages at the same time.

```
sudo dpkg -i *.deb
```

The packages can be installed individually, if you prefer not to install everything. The first package to install is libcodeblocks0 followed by the codeblocks package. All the other packages are optional. If you want to install the wxsmith and/or contrib packages, you must install the libwxsmithlib0 package first.

---

### Post by Arwen on 2007-09-17
It seemed that it's correctly installed and it appears in Apps->Programming but when I double click on code blocks icon,nothing happens,only the little clock of ubuntu and then nothing..

---

### Post by Arwen on 2007-09-17
Also I typed "codeblocks" in terminal and got this:
"codeblocks: error while loading shared libraries: libwx_gtk2u_aui-2.8.so.0: cannot open shared object file: No such file or directory"

Can I somehow add these libraries?

---

### Post by Arwen on 2007-09-17
I installed libwxgtk2.8-dev via synaptic but when I open codeblocks it crashes and I can see this in terminal: 
"(codeblocks:12079): Gtk-CRITICAL **: gtk_window_realize_icon: assertion `info->icon_pixmap == NULL' failed"
I would appreciate any help cause I really need it to work.

---

### Post by cstudent on 2007-09-17
You have to install wxWidgets 2.8.4. The version in synaptic is 2.8.3 in the Feisty repos. 2.8.3 contains a bug which will crash Codeblocks. Carefully read the wiki page. It tells you everything you need to get Codeblocks up and running.

---

### Post by CptPicard on 2007-09-17
You need a newer wxwidgets than Ubuntu has... put these repositories in your /etc/apt/sources.list and do an apt-get update; apt-get upgrade:

```

#code::blocks

deb http://lgp203.free.fr/ubuntu/ feisty main

#new wxwidgets

deb http://apt.tt-solutions.com/ubuntu/ feisty main

```

(Note that I'm on Feisty, edit as appropriate)

This way you get to follow the nightly builds by a simple apt-get upgrade. :)

---

### Post by Arwen on 2007-09-18
I've done this but it crashes(not responding)..I use feisty too.
I even folloed the guide here([http://ubuntuforums.org/showthread.php?p=2816470](http://ubuntuforums.org/showthread.php?p=2816470))
but still it crashes and gives that error on terminal :-(

---

### Post by CptPicard on 2007-09-18
Hmm... odd... sorry, can't help you much further than that, worked for me.. :(

---

### Post by Arwen on 2007-09-18
Sth was wrong with libwxbase2.8-dev and libwxgtk2.8-0 but after a couple of sudo dpkg -i *deb it seems ok..at least it's not crashing in the beginning\\:D/ I hope it won't crash with my programs:-P
Thanx for the help:-)

---

### Post by Arwen on 2007-09-18
OMG,I did sudp apt-get update -f to fix my update manager and now it's not working again!I need to find libwxbase2.8.4-dev and libwxgtk2.8.4-0.When it fixes the namager it doesn't upgrade to 2.8.4 and keeps 2.8.1.1 and codeblocks doesn't work!Any ideas?

---

### Post by cstudent on 2007-09-18
```
sudo update-alternatives --config wx-config

```

Make sure gtk2 2.8 version is selected as default.

---

### Post by Arwen on 2007-09-18
It is.Update manager shows it has to make an update for libwxgtk2.8-0 from 2.8.4.0-0 to 2.8.4.0-0(!!!!) I won't let it do anything,finally codeblocks seems to work fine I don't want to mess it up again..Thank you.

---

### Post by Brian_X7 on 2007-09-18
> **paneas13 said:**
> Is there any similar to Dev++ in Ubuntu Linux ?

Seriously, why not use Emacs?  It has excellent C++ mode, gdb integration, etags, loads of addons to get class browsers and the like.  Probably not as *point and click* as traditional IDE's, but once you get somewhat proficient with it, you'll be more productive.

just my 2 cents.

Brian
Ducking for cover.

---

