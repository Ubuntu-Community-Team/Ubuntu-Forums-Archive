---
title: "Belgian Banksoftware - Missing libraries?"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Belgatom on 2008-05-22
My experience: Up to now, I have installed previous versions of Ubuntu but always as experiment never as my main computer. I have a laptop which I have been using for a year running 7.04. I waited untill the next LTS version came out to migrate from XP to Hardy Heron. Installation went as smoothly as expected. Drivers were no problem. But now, I am confronted with a bit of a problem. I use software to access my bankaccount. I am lucky enough to be customer in a bank that has a Linux version of the security module. I have installed it previously on 7.04 without too much trouble but I am having problems installing it on Hardy. 

You can find the installation information [here]("http://www.ing.be/cms/idc_cgi_isapi.dll?IdcService=GET_DYNAMIC_CONVERSIONPAGE&conversionTemplate=022262_NL&dDocName=118119_EN"). 

I followed everything perfectly and up to installing, everything went fine. But when I wanted to run the module, I got confronted with some errors. 

First error: > error while loading shared libraries: libtiff.so.3 : cannot open shared object file: No such file or directory


Solution offered by faq:
> The error is related to a missing/corrupt library, namely libtiff.

The security module requires the libtiff package version 3. Some distributions provide version 3, others provide a more recent version (4).

check if there are libtiff files in the directory /usr/lib :

> ls /usr/lib/libtiff* -l

1. ) If you find a file libtiff.so.4 :

Create a link to libtiff.so.4. You need to perform following command as root, or using "sudo"

> sudo ln -s libtiff.so.4 libtiff.so.3

Which I solved by following the FAQ. I did however had to make the link in /usr/lib and not in the /opt/HomeBank directory. 

After that I tried running the module again.

Second error: > Error while loading shared libraries: libexpat.so.0 : cannot open shared object file: No such file or directory

Solution suggested by the FAQ: 
> The library package "compat-expat1" or just "expat1" is missing. Install the package "compat-expat1" using the package manager of your distribution

I couldn't find these library packages in Synaptic. But I did a search and I did see someone linking libexpat.so.O to libexpat.so.1. I had a link to libexpat.so.1.5.2 which was called libexpat.so.1 so I tried to make a link to the same file but this time libexpat.so.0. 

I tried to run the module again, and got a new error. No idea if what I did was correct or not but at least the error didn't come back. 
Instead, I got a new one.

Third error: 
> libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

Solution suggested by the faq:> The error is related to a missing/corrupt library, namely libstdc++2.10-glibc2.2.
Install the libstdc++2.10-glibc2.2 package using the package manager of your distribution.

I couldn't find that either in synaptic and I couldn't figure out to which file I should link it. 

Here come the questions. 

Anyway to solve this last one? 
Does all this mean that this module might not be compatible with Hardy? 
Help...?

---

### Post by nowshining on 2008-05-22
in the terminal run the following command after installing libraries.

sudo ldconfig

yes the l is a lowercase L and then retry ur request again.

---

### Post by ubupdh on 2010-01-02
Hi,

I'm very late on this but here is how I did on Ubuntu 8.10 Intrepid to make it work:

1/ For the libtiff.so.3 missing library I used your trick:
$ cd /usr/lib
$ sudo ln -s libtiff.so.4 libtiff.so.3

2/ For the libexpat.so.0 missing library:
I found it in the wink package by searching on the <http://packages.ubuntu.com/> page. I installed it from Synaptic as usual but, as the library goes into /usr/lib/wink/libexpat.so.0, I had to add a link for HBSecGUI to find it:
$ cd /usr/lib
$ sudo ln -s wink/libexpat.so.0 libexpat.so.0

3/ For the libstdc++libc6.2-2.so.3 missing library:
I found it again by searching for the libstdc++2.10-glibc2.2 package on the <http://packages.ubuntu.com/> page in "any" release. Dapper has it:  <http://packages.ubuntu.com/dapper/libstdc++2.10-glibc2.2>. I downloaded and installed that small old package as it contains only 2 libraries.

4/ A last check showed that all libraries were available now:
$ cd /opt/HomeBank
$ ldd HBSecGUI
    -> no more "not found" entries.

I started the software and it worked like a charm. Thank you for your initial work. I hope my additional findings will help others.

Cheers.

---

