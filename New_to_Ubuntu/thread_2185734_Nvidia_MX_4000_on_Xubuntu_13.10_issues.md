---
title: "Nvidia MX 4000 on Xubuntu 13.10 issues"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by zaiker on 2013-11-04
Hello all,

I am a rather new user to Xubuntu. I want to get my Nvidia MX 4000 PCI video card to work properly in my system. I have been working on this for awhile attempting many ideas I have seen all over the net. 

I have the driver from Nvidia

I have managed to stop my X- server via the sudo stop lightdm.

I have made the .run file executable via the chmod +x on the file name

I have purged the nvidia software via sudo apt-get purge nvidia-*

I then attempt to run the file sudo ./NVIDIA-Linux-x86_64-96.43.23-pkg2.run

Then after I accept the agreement, it says "The distribution-provided pre-install script failed! Continue installation anyway?" Which I say yes to

I then get and error
ERROR: The kernel head file '/lib/modules/3.11.0-12-generic/build-include-linux-version.h' does not exist. The most likely reason for this is that the kernel source files in '/lib/modules/3.11.0-12-generic/build' have not been configured.

I am not sure what to do next here.
I installed the essential linux headers via sudo apt-get install build-essential linux-headers-3.11.0-12-generic
I have installed the source files using sudo apt-get install linux-source

I just am not sure what to follow next as most of the steps I find are for ubuntu, which don't always seem to have the same commands for xubuntu

Any help would be awesome

Thanks everyone

---

### Post by farrinux on 2013-11-04
It sounds like you are close.  Try this link and read it all. [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html]("http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html") Make sure you install the packages he discusses in the beginning.

---

### Post by zaiker on 2013-11-04
I should have put in my first post that I have done the steps in Method 1 and 2 before. Additional drivers doesn't find anything, and I am sure the current driver doesn't work with my older video card.

As for ensuring all the packages are installed he said, I did follow that, but it didn't help.

I think I have made it worse though, while trying things on my own again (after the guide didn't help) I attempted to use the command for the installer to download updates, hoping it would grab any update to the drivers that are supported. Instead it looks like it grabbed the current ones, which installed and I am not sure how to uninstall them

Using 'sudo apt-get purge nvidia-*' doesn't seem to get rid of them. **Edit** I was able to uninstall using the installer's uninstall command**

I also do not have the config file that guide says to change to avoid conflicts, I could make it, but it's not already there.

It does look like, if I can get the driver I want to install to install, it will uninstall the current though. **Edit** I was able to uninstall using the installer's uninstall command**

I just am not sure on the kernel head file its looking for, or what to do to correct it.


*** Edit2***
I felt I should post the error log from the installer here


[FONT=arial]nvidia-installer log file '/var/log/nvidia-installer.[/FONT][FONT=arial]log'[/FONT]
[FONT=arial]creation time: Mon Nov  4 12:34:03 2013[/FONT]
[FONT=arial]installer version: 1.0.7[/FONT]

[FONT=arial]PATH: /usr/local/sbin:/usr/local/[/FONT][FONT=arial]bin:/usr/sbin:/usr/bin:/sbin:/[/FONT][FONT=arial]bin[/FONT]

[FONT=arial]option status:[/FONT]
[FONT=arial]  license pre-accepted               : false[/FONT]
[FONT=arial]  update                        [/FONT][FONT=arial]     : false[/FONT]
[FONT=arial]  force update                       : false[/FONT]
[FONT=arial]  expert                        [/FONT][FONT=arial]     : false[/FONT]
[FONT=arial]  uninstall                     [/FONT][FONT=arial]     : false[/FONT]
[FONT=arial]  driver info                        : false[/FONT]
[FONT=arial]  precompiled interfaces             : true[/FONT]
[FONT=arial]  no ncurses color                   : false[/FONT]
[FONT=arial]  query latest version               : false[/FONT]
[FONT=arial]  OpenGL header files                : true[/FONT]
[FONT=arial]  no questions                     [/FONT][FONT=arial]  : false[/FONT]
[FONT=arial]  silent                        [/FONT][FONT=arial]     : false[/FONT]
[FONT=arial]  no recursion                     [/FONT][FONT=arial]  : false[/FONT]
[FONT=arial]  no backup                        [/FONT][FONT=arial]  : false[/FONT]
[FONT=arial]  kernel module only                 : false[/FONT]
[FONT=arial]  sanity                        [/FONT][FONT=arial]     : false[/FONT]
[FONT=arial]  add this kernel                    : false[/FONT]
[FONT=arial]  no runlevel check                  : false[/FONT]
[FONT=arial]  no network                       [/FONT][FONT=arial]  : false[/FONT]
[FONT=arial]  no ABI note                        : false[/FONT]
[FONT=arial]  no RPMs                          [/FONT][FONT=arial]  : false[/FONT]
[FONT=arial]  no kernel module                   : false[/FONT]
[FONT=arial]  force SELinux                      : default[/FONT]
[FONT=arial]  no X server check                  : false[/FONT]
[FONT=arial]  no cc version check                : false[/FONT]
[FONT=arial]  run distro scripts                 : true[/FONT]
[FONT=arial]  no nouveau check                   : false[/FONT]
[FONT=arial]  run nvidia-xconfig                 : false[/FONT]
[FONT=arial]  sigwinch work around               : true[/FONT]
[FONT=arial]  force tls                          : (not specified)[/FONT]
[FONT=arial]  force compat32 tls                 : (not specified)[/FONT]
[FONT=arial]  X install prefix                   : (not specified)[/FONT]
[FONT=arial]  X library install path             : (not specified)[/FONT]
[FONT=arial]  X module install path              : (not specified)[/FONT]
[FONT=arial]  OpenGL install prefix              : (not specified)[/FONT]
[FONT=arial]  OpenGL install libdir              : (not specified)[/FONT]
[FONT=arial]  compat32 install chroot            : (not specified)[/FONT]
[FONT=arial]  compat32 install prefix            : (not specified)[/FONT]
[FONT=arial]  compat32 install libdir            : (not specified)[/FONT]
[FONT=arial]  utility install prefix             : (not specified)[/FONT]
[FONT=arial]  utility install libdir             : (not specified)[/FONT]
[FONT=arial]  installer prefix                   : (not specified)[/FONT]
[FONT=arial]  doc install prefix                 : (not specified)[/FONT]
[FONT=arial]  kernel name                        : (not specified)[/FONT]
[FONT=arial]  kernel include path                : (not specified)[/FONT]
[FONT=arial]  kernel source path                 : (not specified)[/FONT]
[FONT=arial]  kernel output path                 : (not specified)[/FONT]
[FONT=arial]  kernel install path                : (not specified)[/FONT]
[FONT=arial]  precompiled kernel interfaces path : (not specified)[/FONT]
[FONT=arial]  precompiled kernel interfaces url  : (not specified)[/FONT]
[FONT=arial]  proc mount point                   : /proc[/FONT]
[FONT=arial]  ui                            [/FONT][FONT=arial]     : (not specified)[/FONT]
[FONT=arial]  tmpdir                        [/FONT][FONT=arial]     : /tmp[/FONT]
[FONT=arial]  ftp mirror                         : [/FONT][ftp://download.nvidia.com]("ftp://download.nvidia.com/")
[FONT=arial]  RPM file list                      : (not specified)[/FONT]
[FONT=arial]  selinux chcon type                 : (not specified)[/FONT]

[FONT=arial]Using: nvidia-installer ncurses user interface[/FONT]
[FONT=arial]-> License accepted.[/FONT]
[FONT=arial]-> Installing NVIDIA driver version 96.43.23.[/FONT]
[FONT=arial]-> Running distribution scripts[/FONT]
[FONT=arial]   executing: '/usr/lib/nvidia/pre-install'.[/FONT][FONT=arial]..[/FONT]
[FONT=arial]-> done.[/FONT]
[FONT=arial]-> The distribution-provided pre-install script failed!  Continue installation [/FONT]
[FONT=arial]   anyway? (Answer: Yes)[/FONT]
[FONT=arial]-> Performing CC sanity check with CC="cc".[/FONT]
[FONT=arial]-> Performing CC version check with CC="cc".[/FONT]
[FONT=arial]ERROR: The kernel header file[/FONT]
[FONT=arial]       '/lib/modules/3.11.0-12-[/FONT][FONT=arial]generic/build/include/linux/[/FONT][FONT=arial]version.h' does not[/FONT]
[FONT=arial]       exist.  The most likely reason for this is that the kernel source files[/FONT]
[FONT=arial]       in '/lib/modules/3.11.0-12-[/FONT][FONT=arial]generic/build' have not been configured.[/FONT]
[FONT=arial]ERROR: Installation has failed.  Please see the file[/FONT]
[FONT=arial]       '/var/log/nvidia-installer.[/FONT][FONT=arial]log' for details.  You may find suggestions[/FONT]
[FONT=arial]       on fixing installation problems in the README available on the Linux[/FONT]
[FONT=arial]       driver download page at [/FONT][www.nvidia.com]("http://www.nvidia.com/")[FONT=arial].[/FONT]

---

### Post by zaiker on 2013-11-14
Well, even though no one else posted, I figured I would put what the real issue is.

Seems that the drivers from Nvidia will not install on the current Kernel. It works fine on the 2.6 Kernel, running Xubuntu 10.04.
Unless someone has a way to make it work in the current Kernel, I think this whole thing is done.

---

### Post by Peter_Holloway on 2014-04-04
> **zaiker said:**
> Well, even though no one else posted, I figured I would put what the real issue is.

Seems that the drivers from Nvidia will not install on the current Kernel. It works fine on the 2.6 Kernel, running Xubuntu 10.04.
Unless someone has a way to make it work in the current Kernel, I think this whole thing is done.

Any updates to this issue? I also need to install the 96.43.xx Nvidia driver on my Xubuntu 13.10 setup. Any advice greatly appreciated.

---

