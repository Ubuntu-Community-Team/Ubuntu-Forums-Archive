---
title: "Installing help! .tar.gz"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by coubury on 2008-06-01
Iv downloaded VMware-server-1.0.6-91891.tar.gz.tar.gz and iv extracted the files to my home folder, so know i have a file called,

/home/coubury/vmware-server-distrib 

how do i go about installing this?

Thanks in advance!

---

### Post by Monicker on 2008-06-01
[http://pubs.vmware.com/server1/admin/wwhelp/wwhimpl/common/html/wwhelp.htm?context=admin&file=install_server.3.13.html]("http://pubs.vmware.com/server1/admin/wwhelp/wwhimpl/common/html/wwhelp.htm?context=admin&file=install_server.3.13.html")

There should also be documentation in the directory of the extracted archive.

---

### Post by Maestro23 on 2008-06-01
Installing Vmware Server: [https://help.ubuntu.com/community/VMware/Server?action=show&redirect=VmwareServer](https://help.ubuntu.com/community/VMware/Server?action=show&redirect=VmwareServer)

---

### Post by HotShotDJ on 2008-06-01
> **coubury said:**
> Iv downloaded VMware-server-1.0.6-91891.tar.gz.tar.gzSee: [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

It is a comprehensive "HowTo" for installing VMWare Server on Ubuntu 8.04

---

### Post by coubury on 2008-06-01
None of them links tells me what to do when iv got that folder /home/coubury/vmware-server-distrib in my home directory 

so but im a total nOOb lol

---

### Post by coubury on 2008-06-01
HotShot iv 7.10, does that matter?

---

### Post by Monicker on 2008-06-01
The initial location of the extracted files is not important. Just continue from the point where you cd into that directory.

---

### Post by coubury on 2008-06-01
ok its asking me In which directory do you want to install the binary files? 
[/usr/bin]

---

### Post by coubury on 2008-06-01
This is what im faced with:

> coubury@coubury-desktop:~$ cd /home/coubury/vmware-server-distrib
coubury@coubury-desktop:~/vmware-server-distrib$ sudo ./vmware-install.pl
[sudo] password for coubury:
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Server.

Stopping VMware services:
   Virtual machine monitor                                             done

The removal of VMware Server 1.0.6 build-91891 for Linux completed 
successfully. Thank you for having tried this software.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/home] 





I see someone here has the same problem

[http://ubuntuforums.org/archive/index.php/t-260159.html](http://ubuntuforums.org/archive/index.php/t-260159.html)

Someone called Mr T gave a solution

 > my solution for VMware-server-1.0.1-29996

in directory ./vmware-vix create symbolic link to ../bin

but how do i do this?

---

