---
title: "Reabuild, repack, restore package (deb) from already installed files"
date: 2006-06-21
forum: Outdated Tutorials &amp; Tips
---

### Post by kostus1974 on 2006-06-21
If you installed package from deb, and then you lost your installation's deb file, you can restore the original or modified deb using package 'dpkg-repack'.

"dpkg-repack creates a .deb file out of a debian package that has already been installed. If any changes have been made to the package while it was unpacked (ie, files in /etc were modified), the new package will inherit the changes.

This utility can make it easy to copy packages from one computer to another, or to recreate packages that are installed on your system, but no longer available elsewhere, or to store the current state of a package before you upgrade it."

Also you can start to build your own distribution with customized debs with this package (see also 'DebianInstaller').

---

### Post by bhuvi on 2008-12-07
how to create .deb package for all the installed files using single command or how do i find the dependencies for the software?

---

### Post by Kopachris on 2008-12-21
> **bhuvi said:**
> how to create .deb package for all the installed files using single command or how do i find the dependencies for the software?
I'm guessing that would probably have something to do with some bash-style terminal magicky stuff.  In other words, I don't know, but dpkg-repack doesn't have that feature built-in.

---

### Post by InfinityCircuit on 2008-12-21
> **bhuvi said:**
> how to create .deb package for all the installed files using single command or how do i find the dependencies for the software?

```
man aptitude-create-state-bundle
```

---

### Post by Kopachris on 2008-12-21
Here's what to do if you want to customize which packages you want to make (such as if you were making a distro, but don't want *all* the packages you have installed) (this would be a very tedious process, searching through the many packages you have installed).  Note: There might be an easier way, but I don't know about it at the moment.

First, go into a terminal by going to Applications > Accessories > Terminal.
Then, make a directory for all of your packages:
```
mkdir packages
```And change directory into it:
```
cd packages
```Output a list of all your currently installed packages:
```
dpkg --get-selections > filelist.txt
```Now edit the list:
```
gedit filelist.txt
```In the main toolbar, click on "Replace".  On "Search for" enter "install" (w/o quotes) and make sure "Replace with" is blank (not even any spaces) and click "Replace all".  Now replace the "Search for" field with "\t" (again, w/o quotes) and click "Replace all" again.  Now is probably the time that you'd want to go through the package list to make sure it only has what you want.
Once you're done making sure you've got the packages you want, go to Replace again and replace all instances of "\n" with a single space.
Now hit ctrl-a to select all and ctrl-c to copy. Exit Gedit to go back to your terminal and type:
```
sudo dpkg-repack 
```Before you hit enter, right-click and select "paste".  Go get yourself a cup of coffee while you wait for the many names to be pasted.  After it's done pasting, just hit enter and sip your coffee while it builds the packages.

NOTE: To make your editing process a little easier, you could do 
```
dpkg -l > filedescriptions.txt
```
in addition to the other stuff to give you a brief description of each package with its name.  That way, you know what is really necessary so you don't accidentally remove it.

---

### Post by bhuvi on 2008-12-23
whenever i attempt to dpkg-repack it gives out one warning.for example,if i give
sudo dpkg-repack
it says:
warning, `./dpkg-repack-8320/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `uptimed' in `./uptimed_0.3.12-1_i386.deb'.
dpkg-deb: ignoring 1 warnings about the control file(s)

what does this warning mean?

---

