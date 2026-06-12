---
title: "Installing software without an internet connection"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by dhirajsuvarna on 2008-11-24
Hi all,

I have Ubuntu 8.04 installed in my home PC, which does not have any internet connection :(.

I wanted to know if the softwares available in the repository of Linux are also available in .tar files which may contain all the .deb files and their dependencies.

I have tried downloading the .deb files from packages.ubuntu.com, this procedure is very hectic.

Please help me in learning more about Linux and Ubuntu by answering my query.

---

### Post by adult swim on 2008-11-24
check this out [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by dhirajsuvarna on 2008-11-24
Thanks for the site.

I have few concerns in using APTonCD.

As this Software burns all the softwares installed in one of the PC with Ubuntu, it will not help me.

I want a software which i can install in the windows XP OS and download all the files from the repository.

---

### Post by aysiu on 2008-11-24
Here's the next best thing to do (assumes your Windows computer is connected through a wired broadband connection or has a wireless device that is Linux-compatible, and also that there's at least 512 MB of RAM... preferably 1 GB):

**Step 1**
Boot a Ubuntu live CD on the Windows computer. This must be the same version as the Ubuntu you have installed on the non-connected computer.

**Step 2**
In the live session, install whatever programs you want to install (using Applications > Add/Remove or System > Administration > Synaptic Package Manager)

**Step 3**
Insert a USB device

**Step 4**
Copy the entire contents of the /var/cache/apt/archives folder to the USB device

**Step 5**
Right-click to eject the USB device

**Step 6**
Insert the USB device into the non-internet-connected Ubuntu computer

**Step 7**
Copy everything to the desktop that you originally copied out of the /var/cache/apt/archives folder.

**Step 8**
Type these (case-sensitive) commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cd ~/Desktop
sudo dpkg -i *.deb
```

If you don't like having to do that every time, you have several other options: [list][*]Get the internet connection working on your Ubuntu computer[*]Ditch Ubuntu and use a distro like Debian or Mandriva, that actually has extra software CDs available[*]Don't install extra software[/list]

---

### Post by logos34 on 2008-11-24
there used to be a neat thing called NoNetDebs, but the project seems to have been abandoned.

[http://ubuntuforums.org/showthread.php?t=841056](http://ubuntuforums.org/showthread.php?t=841056)

---

### Post by dhirajsuvarna on 2008-11-25
Thanks 
I will try this out.

---

### Post by Tu1J4kXk8NUhMz on 2008-11-25
I had this same problem. I solved it by creating a virtual Ubuntu machine on a machine with internet. Download all the programs/DEBs/whatever you need, then use APTonCD to create a disk with all of those programs. Then open up your Ubuntu installation and transfer. When doing things this way, I usually make sure to create a "Metapackage" when making the APTonCD disk, then just run the Metapackage, which installs everything.

---

### Post by dhirajsuvarna on 2008-12-30
I have Copied the entire contents of the /var/cache/apt/archives folder into mu machine which is not connected to internet.
Now I want to install these packages one by one.

Is there any method which will populate the list of synaptic manger and allow me to install through it?

Or any other method ?

---

### Post by Keen101 on 2008-12-30
getdeb.net

---

