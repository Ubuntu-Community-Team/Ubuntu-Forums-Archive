---
title: "[SOLVED] synaptic package manager run and install problem"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-19
hi
synaptic is playing a little game with me where:
first try greys out and has to force quit
second try does not appear at all
third try kind of works

I am trying to install UIM and anthy but have tried several times and nothing happens

---

### Post by philinux on 2008-08-19
Try disabling compiz if you got it enabled. What are your specs?

---

### Post by LTFC2020 on 2008-08-19
richard@richard-laptop:~$ aptitude install uim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
richard@richard-laptop:~$ sudo aptitude install uim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
richard@richard-laptop:~$ sudo aptitude install anthy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
richard@richard-laptop:~$ 

I tried it in the terminal as show above and there was no install for either uim or anthy which must mean they are installed (don't think so can't find them) or there is a bigger issue

how do I disable compiz?

---

### Post by LTFC2020 on 2008-08-19
oh sorry specs:

a fairly old toshiba dynabook (japanese model)

---

### Post by Kevbert on 2008-08-19
You check whether the packages are installed with Synaptic (just perform a search).  There is an anthy plug-in for uim (uim-anthy).  It may be worth (re-)installing from there.  You can turn off compiz temporarily with compiz-switch (it's currently unavailable!!!).

---

### Post by philinux on 2008-08-19
uim might be a command line utility. Try typing uim in the terminal.

---

### Post by LTFC2020 on 2008-08-19
richard@richard-laptop:~$ uim
bash: uim: command not found
richard@richard-laptop:~$ 

I've tried reinstalling after search 4 or 5 times no result

---

### Post by philinux on 2008-08-19
To disable compiz, if you have it enabled/installed then system>prefs>appearance>desktop effects choose none.

In the terminal use 

locate uim

---

### Post by philinux on 2008-08-19
This might help.

[http://iamacat.wordpress.com/2008/07/07/more-japanese-on-linux-anthy-uim-and-ubuntu-among-others/](http://iamacat.wordpress.com/2008/07/07/more-japanese-on-linux-anthy-uim-and-ubuntu-among-others/)

---

### Post by LTFC2020 on 2008-08-19
richard@richard-laptop:~$ locate uim
/usr/share/app-install/desktop/uim.desktop
richard@richard-laptop:~$ 

I've open to that location but cannot see a folder for it

but there is a uim folder at usr/share/uim

but when I open it there doesn't seem to be an archive or anything just lots of source code files

I had already turned off the desktop effects

---

### Post by unutbu on 2008-08-19
Perhaps try
```
sudo aptitude remove uim
sudo aptitude install uim
```

---

### Post by LTFC2020 on 2008-08-19
I removed anthy and then uim
then installed anthy (as recomended by the uim site) and then uim
still nothing in the system tray however...:confused:


richard@richard-laptop:~$ sudo aptitude remove anthy
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Reading extended state information 
Initialising package states... Done
Building tag database... Done 
The following packages will be REMOVED:
anthy 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 13.2MB will be freed.
Writing extended state information... Done
(Reading database ... 106774 files and directories currently installed.)
Removing anthy ...
Reading package lists... Done 
Building dependency tree 
Reading state information... Done
Reading extended state information 
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done 
richard@richard-laptop:~$ sudo aptitude remove uim
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Reading extended state information 
Initialising package states... Done
Building tag database... Done 
The following packages are unused and will be REMOVED:
libanthy0 libcanna1g libgcroots0 libuim-data libuim5 uim-common uim-fep 
uim-gtk2.0 uim-utils uim-xim 
The following packages will be REMOVED:
uim 
0 packages upgraded, 0 newly installed, 11 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 4624kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 106723 files and directories currently installed.)
Removing uim ...
Removing uim-gtk2.0 ...
Removing libanthy0 ...
Removing libcanna1g ...
Removing uim-xim ...
Removing uim-fep ...
Removing uim-utils ...
Removing libuim5 ...
Removing libgcroots0 ...
Removing libuim-data ...
Removing uim-common ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done 
Building dependency tree 
Reading state information... Done
Reading extended state information 
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done 
richard@richard-laptop:~$ sudo aptitude install anthy
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Reading extended state information 
Initialising package states... Done
Building tag database... Done 
The following NEW packages will be automatically installed:
libanthy0 
The following NEW packages will be installed:
anthy libanthy0 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3504kB of archives. After unpacking 13.6MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package libanthy0.
(Reading database ... 106507 files and directories currently installed.)
Unpacking libanthy0 (from .../libanthy0_9100d-1_i386.deb) ...
Selecting previously deselected package anthy.
Unpacking anthy (from .../anthy_9100d-1_i386.deb) ...
Setting up libanthy0 (9100d-1) ...

Setting up anthy (9100d-1) ...
Updating anthy.dic...file name prefix=[./] you can change this by -p option.
copying .///mkworddic/anthy.wdic (word_dic)
copying .///depgraph/anthy.dep (dep_dic)
copying .///calctrans/anthy.trans_info (trans_info)
copying .///calctrans/anthy.cand_info (cand_info)
copying .///calctrans/anthy.weak_words (weak_words)
copying .///calctrans/anthy.corpus_bucket (corpus_bucket)
copying .///calctrans/anthy.corpus_array (corpus_array)
/usr/bin/mkfiledic done.
done.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done 
Building dependency tree 
Reading state information... Done
Reading extended state information 
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done 
richard@richard-laptop:~$ sudo aptitude install uim
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Reading extended state information 
Initialising package states... Done
Building tag database... Done 
The following NEW packages will be automatically installed:
libcanna1g libgcroots0 libuim-data libuim5 uim-common uim-fep uim-gtk2.0 
uim-utils uim-xim 
The following NEW packages will be installed:
libcanna1g libgcroots0 libuim-data libuim5 uim uim-common uim-fep 
uim-gtk2.0 uim-utils uim-xim 
0 packages upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1707kB of archives. After unpacking 4182kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package libcanna1g.
(Reading database ... 106568 files and directories currently installed.)
Unpacking libcanna1g (from .../libcanna1g_3.7p3-6_i386.deb) ...
Selecting previously deselected package libgcroots0.
Unpacking libgcroots0 (from .../libgcroots0_0.8.0-5ubuntu0.1_i386.deb) ...
Selecting previously deselected package libuim-data.
Unpacking libuim-data (from .../libuim-data_1%3a1.4.1-5_i386.deb) ...
Selecting previously deselected package libuim5.
Unpacking libuim5 (from .../libuim5_1%3a1.4.1-5_i386.deb) ...
Selecting previously deselected package uim-common.
Unpacking uim-common (from .../uim-common_1%3a1.4.1-5_all.deb) ...
Selecting previously deselected package uim-utils.
Unpacking uim-utils (from .../uim-utils_1%3a1.4.1-5_i386.deb) ...
Selecting previously deselected package uim-gtk2.0.
Unpacking uim-gtk2.0 (from .../uim-gtk2.0_1%3a1.4.1-5_i386.deb) ...
Selecting previously deselected package uim-xim.
Unpacking uim-xim (from .../uim-xim_1%3a1.4.1-5_i386.deb) ...
Selecting previously deselected package uim-fep.
Unpacking uim-fep (from .../uim-fep_1%3a1.4.1-5_i386.deb) ...
Selecting previously deselected package uim.
Unpacking uim (from .../uim_1%3a1.4.1-5_all.deb) ...
Setting up libcanna1g (3.7p3-6) ...

Setting up libgcroots0 (0.8.0-5ubuntu0.1) ...

Setting up libuim-data (1:1.4.1-5) ...
Setting up libuim5 (1:1.4.1-5) ...

Setting up uim-common (1:1.4.1-5) ...

Setting up uim-utils (1:1.4.1-5) ...

Setting up uim-gtk2.0 (1:1.4.1-5) ...

Setting up uim-xim (1:1.4.1-5) ...

Setting up uim-fep (1:1.4.1-5) ...
Setting up uim (1:1.4.1-5) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done 
Building dependency tree 
Reading state information... Done
Reading extended state information 
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done 
richard@richard-laptop:~$

---

### Post by unutbu on 2008-08-19
It looks like uim and anthy were successfully installed. To get uim working, have you tried this:

[http://code.google.com/p/uim/wiki/OfficialUserDocument](http://code.google.com/p/uim/wiki/OfficialUserDocument)

In particular:
[http://code.google.com/p/uim/wiki/UIMSystemConfiguration](http://code.google.com/p/uim/wiki/UIMSystemConfiguration)
[http://code.google.com/p/uim/wiki/Tools](http://code.google.com/p/uim/wiki/Tools)
[http://anthy.sourceforge.jp/cgi-bin/hikien/hiki.cgi?uim-anthy](http://anthy.sourceforge.jp/cgi-bin/hikien/hiki.cgi?uim-anthy)

---

### Post by LTFC2020 on 2008-08-19
thanks
I had seen one of those links but the rest look really complicated, will need a while to go through them.
I think the problem is with 8.04, as when I set up UIM and anthy on 7.10 the whole process took 5 minutes, compared with SCIM on my other laptop which took 2 days and multiple posts to sort out, which is the reason I have been trying to avoid installing it.
Didn't think setting up Japanese on my laptop would be nearly as difficult as learning it in the first place:rolleyes:

---

### Post by LTFC2020 on 2008-08-19
thanks to everyone for their help
am marking this as solved because I installed SCIM (as opposed to UIM) with anthy and had it up and running within an hour
strange that this SCIM/ UIM experience is the exact opposite with 8.04 than 7.10
the hardy SCIM documentation seems much more straight forwards than with 7.10 while UIM needs more configuration

---

