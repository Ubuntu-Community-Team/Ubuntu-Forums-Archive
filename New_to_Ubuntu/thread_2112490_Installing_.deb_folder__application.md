---
title: "Installing .deb folder / application"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by Dagwood on 2013-02-04
Hello
I've downloaded an application (fcc-10.014-Linux.i686.deb) that I'd like to install but am confused as to do it. When I right click and try to use "Ubuntu Software Centre" I get an error message; " Dependency is not satisfiable: libqt3-mt|libqt3c102-mt". How do I go about getting these dependencys and installing them? I can also use application manager and navigate to a file that lists the dependency requirements, but doesn't give instructions on installing. Which should I be using; Software Centre or Applications Manager?
Thanks:p

---

### Post by whatthefunk on 2013-02-04
What about when you just double click on it?  Dependencies should be resolved automatically if the packages are in the repositories.  If the packages arent in the repositories, then the .deb package was probably not made well and Id maybe look for an alternative program.

---

### Post by Filipek on 2013-02-05
> **Dagwood said:**
> Hello
I've downloaded an application (fcc-10.014-Linux.i686.deb) that I'd like to install but am confused as to do it. When I right click and try to use "Ubuntu Software Centre" I get an error message; " Dependency is not satisfiable: libqt3-mt|libqt3c102-mt". How do I go about getting these dependencys and installing them? I can also use application manager and navigate to a file that lists the dependency requirements, but doesn't give instructions on installing. Which should I be using; Software Centre or Applications Manager?
Thanks:p

Open the Terminal (Ctrl+Alt+T or simply from within the Unity hud) and change the directory to the location of the DEB file.

Then I would suggest the following:

```

sudo dpkg -i fcc-10.014-Linux.i686.deb

```

I throuws the error you have mentioned. Then:

```
sudo apt-get install -f
```

Which should resolve problems (install the packages that other installations were depending on).

Then repeat the direct DEB installation.

If that does not help, post the output here.

---

### Post by Dagwood on 2013-02-05
> **Filipek said:**
> Open the Terminal (Ctrl+Alt+T or simply from within the Unity hud) and change the directory to the location of the DEB file.

Then I would suggest the following:

```

sudo dpkg -i fcc-10.014-Linux.i686.deb

```

I throuws the error you have mentioned. Then:

```
sudo apt-get install -f
```

Which should resolve problems (install the packages that other installations were depending on).

Then repeat the direct DEB installation.

If that does not help, post the output here.

Follow - up
Thanks for the response. Here is the error message from sudo apt-get install -f

king@king-HP-d530-SFF-DG058A:~/Desktop$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
king@king-HP-d530-SFF-DG058A:~/Desktop$


And ...
Here is the response from sudo dpkg -i fcc-10.014-Linux.i686.deb

king@king-HP-d530-SFF-DG058A:~/Desktop$ sudo dpkg -i fcc-10.014-Linux.i686.deb
dpkg: error processing fcc-10.014-Linux.i686.deb (--install):
 unable to open file '/var/lib/dpkg/tmp.ci//.svn': Is a directory
Errors were encountered while processing:
 fcc-10.014-Linux.i686.deb
king@king-HP-d530-SFF-DG058A:~/Desktop$ 

Any advice / help?

---

### Post by Dagwood on 2013-02-06
> **Dagwood said:**
> Follow - up
Thanks for the response. Here is the error message from sudo apt-get install -f

king@king-HP-d530-SFF-DG058A:~/Desktop$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
king@king-HP-d530-SFF-DG058A:~/Desktop$


And ...
Here is the response from sudo dpkg -i fcc-10.014-Linux.i686.deb

king@king-HP-d530-SFF-DG058A:~/Desktop$ sudo dpkg -i fcc-10.014-Linux.i686.deb
dpkg: error processing fcc-10.014-Linux.i686.deb (--install):
 unable to open file '/var/lib/dpkg/tmp.ci//.svn': Is a directory
Errors were encountered while processing:
 fcc-10.014-Linux.i686.deb
king@king-HP-d530-SFF-DG058A:~/Desktop$ 

Any advice / help?


Update:
I've been snooping around the forums and there is mention of "getlib". I believe this is a repository that may contain missing files I need in order to install the software. Can someone direct me to the getlib and how I install it?
Thanks

---

### Post by GordThompson on 2013-02-07
When I did a Google search on the .deb filename I found another similar thread [here]("http://ubuntuforums.org/showthread.php?t=1904371") with a reply that said

> **mcduck said:**
> Based on the information on the web site, the .deb package is made for Debian, not for Ubuntu.

Even though the two distributions have a lot in common, including the package manager, they aren't actually fully compatible and the names of various packages etc. things are different between Debian and Ubuntu.

You'll probably have to use the .tar.gz instead.

---

### Post by Dagwood on 2013-02-07
Hello
I've resolved my issue. Thanks to all those that offered advice. I found this other post and used it to resolve the issue:
[http://www.f1done.com/2011/04/firstclass-on-linux.html](http://www.f1done.com/2011/04/firstclass-on-linux.html)
This article provides a work around using "wine",so I didn't manage to install a linux version of the FirstClass Client. 

Note: you may need to locate a FirstClass settings file from another computer. Try doing a search on *.fc. Copy those files into a USB stick and upload to the settings folder on your Linex machine.

---

