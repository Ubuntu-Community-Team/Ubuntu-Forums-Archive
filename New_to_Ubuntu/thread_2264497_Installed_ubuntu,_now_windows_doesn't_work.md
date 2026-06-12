---
title: "Installed ubuntu, now windows doesn't work"
date: 2015-02-07
forum: New to Ubuntu
---

### Post by ugur2 on 2015-02-07
I have installed ubuntu, now windows doesn't work. help me please?

---

### Post by sandyd on 2015-02-07
> **ugur2 said:**
> I have installed ubuntu, now windows doesn't work. help me please?

Please post the file that the following commands creates.
```

wget http://hivelocity.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz
tar xvf bootinfoscript-061.tar.gz
./bootinfoscript
```

Thanks!

---

### Post by NunoLava1998 on 2015-02-10
You may installed in the wrong way, Linux can corrupt windows if it is installed incorrectly.

---

### Post by DavidSr on 2015-02-12
My two cents, don't install to dual boot.  See the option that was posted in another posting.  I have my VirtualBox setup and installing Ubuntu right now.  

 					[IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **SeijiSensei** 					[[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=13226886#post13226886") 				
 				I just bought a new machine with Win7 and wanted to have Kubuntu as well.  I used***[SIZE=4][COLOR=#ff0000] VirtualBox [/COLOR][/SIZE]***to  create a "virtual machine" into which I installed Kubuntu.  If you have  a computer with a decent amount of memory, say 4 GB or more, this is  the simplest way to run both Windows and Linux.

1)  First, download an Ubuntu ISO disk image like [Ubuntu]("http://cdimage.ubuntu.com/releases/14.04.1/release/") or [Kubuntu]("http://cdimage.ubuntu.com/kubuntu/releases/14.04.1/release/")
2)  Next, download and install the VirtualBox software for Windows from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
3)  After it installs, press the New button in the VB application to create new virtual machine.
4)  I usually give Ubuntu 1-2 GB of memory depending on amount  available. On this machine with 8 GB, I allocated 2 GB to Ubuntu and  left the rest for Windows.  Then you'll be asked to create a "virtual  disk" to contain the Ubuntu installation.  On the large disks available  today, I usually go for something in the 32-64 GB range.
5)  VB will then ask for the installation medium.  Point to the ISO you downloaded.

---

