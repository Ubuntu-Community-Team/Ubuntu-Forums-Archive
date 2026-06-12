---
title: "Cant install NVIDIA driver ??"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by spencer218 on 2008-07-03
I downloaded the NVIDIA driver for Geforce ( 200 series ) and was following the directions for installation on this web page   [http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html)     in the terminal, and it says sh cant open it. This is what it looks like....


christopher@ubuntu:~$ sh NVIDIA-Linux-x86-177.13-pkg1.run
sh: Can't open NVIDIA-Linux-x86-177.13-pkg1.run
christopher@ubuntu:~$ sudo sh NVIDIA-Linux-x86-177.13-pkg1.run
[sudo] password for christopher: 
sh: Can't open NVIDIA-Linux-x86-177.13-pkg1.run
christopher@ubuntu:~$ sh NVIDIA-Linux-x86-177.13-pkg1.run
sh: Can't open NVIDIA-Linux-x86-177.13-pkg1.run


I even tried to use sudo before sh and didnt work. I should mention I have no root password so I cant log in as root if that is required. Am I doing this wrong ? Is there another way to install the latest NVIDIA drivers ?

---

### Post by syczu on 2008-07-03
Root is required to install drivers.

---

### Post by Sef on 2008-07-03
> Root is required to install drivers.

Sudo gives one temporary access to root.


Check out [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/#script").

You may not have the [permission,]("http://monkeyblog.org/ubuntu/installing/#permissions") so you need to change it.

---

### Post by Inxsible on 2008-07-03
Are you trying to do that under X ?

I think that package requires you to go to tty. Login to your tty and then try to run the package. 

See if that helps.

---

### Post by RomeReactor on 2008-07-03
Hi. Just to add: Make sure the file is in your home folder; otherwise, navigate to where it is. Also, make it executable first:
```
chmod +x NVIDIA-Linux-x86-177.13-pkg1.run
```
Make sure the name of the file is correct; you can start typing it and then press TAB to autocomplete it. As Inxsible said, you need to get out of the graphical desktop (by pressing CTRL+ALT+F1), then run:
```
sudo /etc/init.d/gdm stop
```
to stop the display, then run the installer.

---

### Post by sisco311 on 2008-07-03
1.) You can install the driver for the video card from Applications -> System -> Hardware Drivers

2) If you want to install the run package:

i) stop the X server
press Ctrl+Alt+F2 and login
type:
```
sudo /etc/init.d/gdm stop
```ii.) install the driver:
```
sudo sh ~/Desktop/NVIDIA-Linux-x86-177.13-pkg1.run
```assuming the file is downloaded to the Desktop

iii) restart the x server:
```
sudo /etc/init.d/gdm start
```Note: When you execute a file you need to specify the full path.
ex.: /home/user/file-name
./ = current directory
~/ = home directory
pwd = print name of current directory

Note2: You don't need execute permission on the file if you specify the interpreter(bash, sh...)
ex.: sh /path/to/file/file-name

---

### Post by crtlbreak on 2008-07-03
and for 
sudo command option destination
you should be using your christopher password - not the root password - as the root account and password are locked by default on a new ubuntu installation - till you manually unlock it if you want to of course! but it is better not to though!

---

