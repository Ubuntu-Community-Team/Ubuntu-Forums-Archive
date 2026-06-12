---
title: "How-to? Install Apps/Packages No Physical Internet Linkup on One Computer."
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Banacek on 2008-06-28
Okay, I do have the internet hooked up to the computer that I'm using to post this from. However, I have another computer at another location where there is no physical connection possible to the internet. We have not as yet (and not sure when) signed up for any internet service at the other location. I have installed Xubuntu Hardy Heron on my other computer there. My computer with internet access is running Ubuntu Gusty.

When I click "Add/Remove Programs" I see some cool games and other applications listed there. Of course, without the internet I can't access the repositories on my other computer. However, if I could just download the applications themselves without installing, I could save them to CD or USB memory stick and transport them to my other computer. How do I get such downloads from the repositories and install them from a memory stick or CD?

---

### Post by PmDematagoda on 2008-06-28
If you aren't using Ubuntu on the PC that is connected to the net, then you will have to use [Ubuntu Packages]("http://packages.ubuntu.com/"), but keep in mind that there maybe quite a lot of dependencies for certain packages, so your job would be very much simplified if you got an internet connection on your Hardy install.

---

### Post by Banacek on 2008-06-28
Very true. It would be very much simplified, if an internet connection was available for my other computer with the Xubuntu Hardy install. However, that is just entirely not possible for now. Hence, I need to know how to do it another way. I suppose I'll need a dependencies listing for everything I want to install also.

---

### Post by Banacek on 2008-06-29
So what do I do?

---

### Post by cariboo on 2008-06-29
One way to do it is in System-->Aministration-->Synaptic Package Manager. Select the packages you want and then click apply, in the summary windows there is a check box in the lower left corner to download files only click this and click apply, then you can use aptoncd to transfer the files to CD.

AptonCd is availabe in the repositories and you can use sysnaptic to install it.

Jim

---

### Post by Hagalmir on 2008-07-01
The trouble is that without access to a full repository you will run
into dependency problems sooner or later. I use apt-mirror to download
the full i386 binary 8.04 distribution on a USB disk, this needs about
23 GB, including hardy main, restricted, universe, and multiverse, no 
sources. Then I carry the disk home, and I can install whatever I want
without any troubles. Here is my /etc/apt/mirror.list 
(use your nearest mirror, at. is for Austria):

############# config ##################
#
set base_path    /media/disk/apt-mirror
#
# if you change the base path you must create the directories below with write privlages
#
set mirror_path  $base_path/mirror
set skel_path    $base_path/skel
set var_path     $base_path/var
set cleanscript $var_path/clean.sh
set defaultarch  i386
set nthreads     20
# set _tilde 0

deb [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse
deb [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

clean [http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu)

This assumes that the USB disk is mounted in /media/disk and contains
a directory apt-mirror. It took me about an hour to download everything.
In the offline /etc/apt/sources.list use file:/// to point the mirror
directories. Once a month or so pack the disk and use apt-mirror 
to bring your mirror up to date.

sudo apt-get install apt-mirror
man apt-mirror
man apt-get

-Hagalmir

---

