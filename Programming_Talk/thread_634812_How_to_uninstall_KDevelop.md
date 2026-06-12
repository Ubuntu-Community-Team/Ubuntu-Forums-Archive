---
title: "How to uninstall KDevelop"
date: 2007-12-08
forum: Programming Talk
---

### Post by tjpren on 2007-12-08
Hi,

I've been trolling the internet looking for a good IDE GUI development environment (new to Linux, from MS VStudio).

I downloaded and installed KDevelop (KDevelop Assistant, Kdevelop C/C++ etc).

I got a sample or two to work, but couldn't for the life of me, figure how to do it on my own, so I'm wanting to unintstal it - any ideas how ?

I installed it via
sudo aptitude install kdevelop build-essential libtool automake libx11-dev xlibs-dev libqt3-mt-dev libqt4-dev kdelibs4-dev kdebase-dev

Is the reverse, uninstall a valid command in linux ?

---

### Post by Compyx on 2007-12-08
```

sudo apt-get remove kdevelop

```
should do the trick, perhaps followed by
```

sudo apt-get autoremove
```
to remove any dependencies of kdevelop that are no longer needed.

By the way, the apt-get command is specific to Debian and Debian-derived distributions (such as Ubuntu). There are many different package-managers, depending on the distribution. For example, Gentoo uses 'emerge' while Red Hat and many others use rpm-packages which are usually managed through 'yum' or such.

Linux is actually just the kernel, most of the software running on top of the kernel comes from the GNU project, making the 'GNU/Linux' operating system. Add specific ways of handling init-scripts, package-management and file-system structures and you get a 'distribution', or 'distro'.

---

### Post by Kadrus on 2007-12-08
Or you can go to synaptic package manager..and search for Kdevelop...and mark it to uninstall it..

---

### Post by Noob64 on 2010-02-15
Hi 'm new to this thread and i tried everything stated here. Ubuntu removed the program but, when i put my mouse of applications and move to programs its shows the kdevelop icons, how do i remvoe those icons the programs menu. I cant use them but their their its annoying.

---

