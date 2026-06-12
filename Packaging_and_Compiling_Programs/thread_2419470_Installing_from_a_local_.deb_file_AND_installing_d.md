---
title: "Installing from a local .deb file AND installing dependencies?"
date: 2019-05-22
forum: Packaging and Compiling Programs
---

### Post by ken35 on 2019-05-22
I am in the process of installing the latest gnome-commander (1.10.2) on Ubuntu Mate 18.04.  The package is not in the repos and due to some older library concerns it is my understanding that it will not be added to the repos. That said, I have downloaded the tarball, unpacked it, installed the necessary development libraries then configure; make; sudo make install and it runs great.  Next I ran checkinstall to create a quick and dirty .deb file to install on a couple of my other machines. Again this worked fine.

I installed the .deb package on another Ubuntu Mate 18.04 machine ```
ken@ubuntu:~/Desktop$ sudo gdebi gnome-commander_1.10.2-1_amd64.deb 
[sudo] password for ken: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done

gnome-commander
Do you want to install the software package? [y/N]:y
Selecting previously unselected package gnome-commander.
(Reading database ... 200107 files and directories currently installed.)
Preparing to unpack gnome-commander_1.10.2-1_amd64.deb ...
Unpacking gnome-commander (1.10.2-1) ...
Setting up gnome-commander (1.10.2-1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
ken@ubuntu:~/Desktop$ gnome-commander
gnome-commander: error while loading shared libraries: libgnomeui-2.so.0: cannot open shared object file: No such file or directory
```However, it does not run due to a dependency issue.  The .spec file clearly states ```

Requires:      libgnomeui >= 2.4.0
```and if I install libgnomeui-0 the problem is fixed and gnome-commander runs.

My question is... How do I install from a package from a local .deb file AND cause any dependencies to be installed at the same time?  In CentOS 7 I can use yum install my_local_package.rpm and the local package and its dependencies will be installed.  I have looked at the man pages for gdebi, dpkg, apt, aptitude, apt-get and synaptic. I see information about how to IGNORE dependencies but nothing to cover the situation at hand.

TIA.

Ken

---

### Post by TheFu on 2019-05-22
Have the .deb file add a PPA to the system APT sources.d/ directory and use normal package management techniques going forward.

---

### Post by again? on 2019-05-22
> glen@Bionic:~$ apt show libgnomeui
N: Unable to locate package libgnomeui       N: Unable to locate package libgnomeui       E: No package found

glen@Bionic:~$ apt show libgnomeui-0
Package: libgnomeui-0
Version: 2.24.5-3.2
 
You said if you install libgnomeui-0 the problem is fixed.
Your checkinstall --requires option should be libgnomeui-0 not libgnomeui.

P.S. This is an easy to follow tutorial on creating deb packages that I have used to create my own custom debs.
[https://blog.heckel.xyz/2015/10/18/how-to-create-debian-package-and-debian-repository/](https://blog.heckel.xyz/2015/10/18/how-to-create-debian-package-and-debian-repository/)

---

### Post by ken35 on 2019-05-23
Thanks TheFu but I think that is a bit of overkill for the objective of this exercise. More about that in a minute.

Thanks guber2. I changed the spec file and rebuilt the package. gdebi did NOT install the desired libraries. That is an excellent tutorial if I wanted to build MY own .deb package and I have bookmarked it for future reference.

Here is a little background on what I am trying to do and why.

gnome-commander relies on some older libraries (I think having to do with gvfs) and the Debian maintainers have kicked it out of their official repositories. It is therefore not available in Ubuntu either except for a rather ancient version. I am working with the maintainer of g-c to come up with a simple How To to assist uses of Debian derived distros to use the newest version of g-c.

I have identified the development packages which are required to compile g-c from source. I have documented this part and it is quite straight forward. Personally I do not install development environments on my "production" PCs. Too much overhead and wasted space. My approach is to build a development environment on a virtual machine (VMware, Virtual box etc.), install an package the application on the VM and then use the .rpm or .deb package to install on my other machines. 

This approach works great on CentOS - just a couple of steps.  The approach on Ubuntu using checkinstall is also very simple. The problem is, I think, with the installation of the packaged application on the target machine. In the RHEL, CentOS, Scientific Linux world the yum package manager will to a "localinstall" now depreciated to just install and will fetch any unmet dependencies.  I would hope that there is a way to do something similar and simple in Ubuntu.

Ken

---

### Post by TheFu on 2019-05-23
Seems like this application would be a perfect use-case for a snap or flatpak then.

---

### Post by ken35 on 2019-05-23
Thanks again TheFu,

The maintainer of g-c is looking into a flatpack solution. But until then...

Ken

---

### Post by TheFu on 2019-05-23
> **ken35 said:**
> Thanks again TheFu,

The maintainer of g-c is looking into a flatpack solution. But until then...

Ken

Well, the only solution is to manually determine the dependencies.  If you want to make it quick to install, then make a little script.

There is another option.  Join the maintainer team and help them move to a version of the underlying libs that ARE currently in the repos.  I don't want to downplay that effort. I worked for many years porting software before we had package managers across over 10 different platforms.  I don't put up with projects that don't stay current, unless it is work related and mandatory. Package management and dependency management is a key reason why I choose Linux over other OSes.  If you've ever been in setup-hell on other platforms, and hopefully you haven't, it is hard to explain how bad they are at it and how great APT really is.  APT is freakin' awesome!

---

