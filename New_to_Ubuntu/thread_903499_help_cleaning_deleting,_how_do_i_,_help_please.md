---
title: "help cleaning deleting, how do i , help please"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by georgegerm on 2008-08-28
i was trying to get f prot in (yes i am aware its not really required , but i do some windows use)
i did not get it install correctly now i would like to start from point one..
how do i get all the stuff out of the system that has to do with  f prot..
ps. the errors came about as i was using old install info from older sources with older version and it created a lot of problems
.. but ubu refuses to die !!! thats why i love it vista had crashed and burned already..
viva ubu

---

### Post by loboc on 2008-08-28
in a terminal

```
apt-get remove --purge packagename
```

---

### Post by jamesrl on 2008-08-28
How did you try installing f-prot (which a google search tells me is [[an anti-virus program that works in linux]("http://www.f-prot.com/download/home_user/download_fplinux.html")])?
There are three basic methods for installing programs, and each has there own unique way to uninstall.
1). Easiest method:  Install from a repository.  When the program is in a repository, you can install it by typing:
```
sudo apt-get install packagename
```
and uninstall it by 
```
sudo apt-get remove packagename
```
Sometimes you have to add a new repository to your repository list.  Example if you wanted google gadgets you'd add:
```

deb http://ppa.launchpad.net/googlegadgets/ubuntu hardy main
deb-src http://ppa.launchpad.net/googlegadgets/ubuntu hardy main

``` to /etc/apt/sources.list, then run 
sudo apt-get update
(to reload the packages) and then the new packages will be in the repository for easy install/uninstall/upgrades.  You can also use synaptic (Gnome) or adept (kde) to manage packages graphically.

2) Download a package file and install it manually.  A package file is *.deb, and would be installed like 
```

dpkg -i some_package_name_v1.2.3_i386.deb

```
and removed through apt-get in the standard fashion.
```

sudo apt-get remove  some_package_name

```

3) Install from source.  Generally the longest method of installation (as you have to compile the binary files from source code), it is also the most difficult to uninstall (as by default you have no package manager that tells you where packages are put). 
A typical install from source method would be, download some *.tar.gz
```

tar xvfz some_source_code_v1.2.3.tar.gz  ## this "unzips" the source code
cd some_source_code_v1.2.3/  ## changes directory to the source code dir
./configure   ## configures your settings for how you want the source code installed
              ## you may need to add or take away certain flags
make          ## this "builds" the source code for you, making it into a binary file
sudo make install  ## this installs the source code 

```
Prior to the "sudo make install" step, the only place things should have changed is within the directory you just unzipped files to.  So you could if you wanted to uninstall just remove that directory (rm -r name_of_directory).  If however you got to the sudo make install step, you have to note where it installed items to and delete them manually (quite annoying).  You can use tools like "whereis", "locate", and "find" to search for where things were installed to.  In the future when installing things from source, its usually helpful to use checkinstall.  This basically replaces the "sudo make install" process, with "sudo checkinstall -D" and this will make a package file (a *.deb) that can then be installed/uninstalled via sudo dpkg -i package_name.deb

---

