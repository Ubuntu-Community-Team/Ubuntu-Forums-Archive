---
title: "Installing MudMagic.rpm in Ubuntu 6.06"
date: 2006-09-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Omnios on 2006-09-11
This is my first install How to for the MudMagic mud client. MudMagic is probably one of the best mud clients for Linux with mud sound support and lots of bells and whisltes. The project leader has stated that he is trying to make a mud client that can stand at par with other popular full featured clients.

[SIZE=5]Note:::[/SIZE]
I can not garantee that this will not break Ubuntu as it requires edgy packages!!!

 First off you can visit there homepage for the client,
[http://www.mudmagic.com/mud-client/](http://www.mudmagic.com/mud-client/)

 The download [mudmagic-1.9-1.i386.rpm]("http://www.mudmagic.com/mud-client/downloads/mudmagic-1.9-1.i386.rpm") is available here.
[http://www.mudmagic.com/mud-client/linux_download](http://www.mudmagic.com/mud-client/linux_download)
Download the rpm pacakge.

 K now the install trick. 

 First I made a link to make /usr/lib/libpcre.so.0 point to /usr/lib/libpcre.so.3
```

sudo ln -s /usr/lib/libpcre.so.3 /usr/lib/libpcre.so.0

```

 Now when I tryed to run MudMagic I git the following error

```

tom@miko:~$ mudmagic
/usr/bin/mudmagic-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/bin/mudmagic-bin)
/usr/bin/mudmagic-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libmudmagic.so.0)
/usr/bin/mudmagic-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/mudmagic/libs/libcurl.so.0)

``` 

 Now I got around these errors by downloading the edgy libc6 2.4-1 package. Also I am using the 696 kernal and has to install both the 386 libc6  and also the 686 libc6 package so counting on you kernal you will have to download and install the apropriate packages.

 Now the packages are available from.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

 The 386 package is available here
[http://packages.ubuntu.com/edgy/base/libc6](http://packages.ubuntu.com/edgy/base/libc6)

 The 686 package is here. The download package is libc6-i686_2.4-1ubuntu9_i386.deb which may be confusing because it has 386 in the name but it is and installs the 686 version of the package. Also because I have the 686 kernel I had to isntall both the 383 and 686 packages as Mud magic called for the 686 version and the 386 version is required to install the 686 version.
[http://packages.ubuntu.com/edgy/libs/libc6-i686](http://packages.ubuntu.com/edgy/libs/libc6-i686)

 Also this will break the -dev package so I got the edgy libc6-dev_2.4-1ubuntu9_i386.deb
Available here:
[http://packages.ubuntu.com/edgy/libdevel/libc6-dev](http://packages.ubuntu.com/edgy/libdevel/libc6-dev)

 which requires the linux-libc-dev_2.6.17-7.20_i386.deb package.
available here:
[http://packages.ubuntu.com/edgy/devel/linux-libc-dev](http://packages.ubuntu.com/edgy/devel/linux-libc-dev)

NOTE: The edgy linux-libc-dev_2.6.17-7.20_i386.deb package replaces a package on install so not shure if anything will break as of yet. 

```
tom@miko:~/aptget$ sudo dpkg -i linux-libc-dev_2.6.17-7.20_i386.deb
Selecting previously deselected package linux-libc-dev.
dpkg: considering removing linux-kernel-headers in favour of linux-libc-dev ...
dpkg: yes, will remove linux-kernel-headers in favour of linux-libc-dev.
(Reading database ... 173085 files and directories currently installed.)
Unpacking linux-libc-dev (from linux-libc-dev_2.6.17-7.20_i386.deb) ...
Setting up linux-libc-dev (2.6.17-7.20) ...
tom@miko:~/aptget$ ls

```

 Now you will be ready for the MudMagic rpm conversion and install.
Now find where you downloaded the mudmagic-1.9-1.i386.rpm.
Now to convert the rpm into a deb you need alien which is available in synaptic. 
```
sudo apt-get install alien
```
Also I used fakeroot to convert the package.
```
sudo apt-get install fakeroot
```

 Now to convert the package.  cd to the directory you downloaded the [mudmagic-1.9-1.i386.rpm]("http://www.mudmagic.com/mud-client/downloads/mudmagic-1.9-1.i386.rpm") package to. I used 
```

fakeroot alien -d mudmagic-1.9-1.i386.rpm

```

 This developed the .deb package for MudMagic which is nice as it makes synaptic entry undeer installed local where it can be uninstalled.

 To install the deb use.
```

sudo dpkg -i mudmagic_1.9-1_i386.deb

```

 Now you should be all ready to go. 

 Note: I will update if there is any breakerages.

---

### Post by Mystere on 2006-11-30
hrmm, after making the link my system still can't find any file. I didn't find a libpcre.so.3 to begin with though...

$ mudmagic
/usr/bin/mudmagic-bin: error while loading shared libraries: libpcre.so.0: cannot open shared object file: No such file or directory
$ sudo ln -s /usr/lib/libpcre.so.3 /usr/lib/libpcre.so.0
$ mudmagic
/usr/bin/mudmagic-bin: error while loading shared libraries: libpcre.so.0: cannot open shared object file: No such file or directory
](*,)

---

### Post by hextor on 2006-12-29
hmm same thing here but using edgy..should we do the symlink before installing?

---

### Post by Omnios on 2006-12-30
My latest Mudmagic install was done using a tarball I will have to hunt down the link for the tarball on the mudmagic site.

---

### Post by Martym on 2008-03-25
I simply made the .deb package, installed the .deb then created the link and it works fine (although I waiting for a fix for the MUD I mainly play (MCCP causes crashes))

---

