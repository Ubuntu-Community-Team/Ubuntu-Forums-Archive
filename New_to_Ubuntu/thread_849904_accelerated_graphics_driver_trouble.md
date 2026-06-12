---
title: "accelerated graphics driver trouble"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by mcd144 on 2008-07-05
Hi,

I'm new to Ubuntu and just installed 8.04 - the Hardy Heron.  Everything is working great and I can't wait to start learning more.  The only problem I seem to be having is when I enable the restricted driver for my NVIDIA Geforce FX 5200.  After doing this and after rebooting, my monitor says it's out of range and I can't see anything.  However, I was able to reverse the driver.

So I thought maybe to install the latest driver manually (have it downloaded) but have no clue where to start.  But if there is something simple I can do to enable the restricted driver and make it work, that would be great.  Thanks  O:)

---

### Post by overdrank on 2008-07-05
> **mcd144 said:**
> Hi,

I'm new to Ubuntu and just installed 8.04 - the Hardy Heron.  Everything is working great and I can't wait to start learning more.  The only problem I seem to be having is when I enable the restricted driver for my NVIDIA Geforce FX 5200.  After doing this and after rebooting, my monitor says it's out of range and I can't see anything.  However, I was able to reverse the driver.

So I thought maybe to install the latest driver manually (have it downloaded) but have no clue where to start.  But if there is something simple I can do to enable the restricted driver and make it work, that would be great.  Thanks  O:)

Hi and welcome, when you receive the out of range error you may try and use the ctr, alt, F1 keys to reach command line. Then you can login and try and reconfigure your xorg and this may solve the issue. Use the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` or you may try and boot into recovery mode and use the xfix to correct the issue.
 if you would like to try and install the nvidia driver you have downloaded then you can use the keys alt, ctrl, F1 keys at the same time and this will bring you to the command prompt and login.
The use this command to stop X
```
sudo /etc/init.d/gdm stop
```
Then change to the directory that you downloaded the driver to
```
cd ~/Desktop
```
Then you can use the command to install the nvidia drivers 
```
sudo sh NVIDIA-Linux-x86-173.14.09-pkg1.run
```
If that is the name of the driver you have downloaded.
Then you should be able to start x again 
```
sudo /etc/init.d/gdm start
```
If all works as plan then you should have the new driver installed.

---

### Post by bumanie on 2008-07-05
> sudo dpkg-reconfigure -phigh xserver-xorg Ovedrdank, just to let you know that since hardy, that code has been superseded by the simple > sudo xfix as per this [article]("http://ubuntulinuxtipstricks.blogspot.com/2008/04/faq-hardy-upgrade.html"). No.13

---

### Post by overdrank on 2008-07-05
> **bumanie said:**
> Ovedrdank, just to let you know that since hardy, that code has been superseded by the simple  as per this [article]("http://ubuntulinuxtipstricks.blogspot.com/2008/04/faq-hardy-upgrade.html"). No.13

HI and yes as I mention in the reply but I find it still useful to a degree. :)

---

### Post by bumanie on 2008-07-05
> **overdrank said:**
> HI and yes as I mention in the reply but I find it still useful to a degree. :)

Sorry missed that bit -see it now:)

---

### Post by mcd144 on 2008-07-05
I'm getting an error when trying to install the driver manually.

Here's the log:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Jul  5 09:33:50 2008
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 173.14.09.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

Thanks for the help

---

### Post by mcd144 on 2008-07-05
Does anyone know us Suse 11.0 would be easier to use than Ubuntu?

---

### Post by overdrank on 2008-07-05
> **mcd144 said:**
> Does anyone know us Suse 11.0 would be easier to use than Ubuntu?

HI and I use suse 10.3 on intel graphics and IMO it was not easier. 
But you can always try suse
Have you tried the restricted drivers and then reconfigure the xorg?

---

