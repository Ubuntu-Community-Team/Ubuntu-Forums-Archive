---
title: "how to do profiling for linux kernel or current kernel?"
date: 2015-07-10
forum: Programming Talk
---

### Post by zerop2 on 2015-07-10
how to do profiling for linux kernel?
how to search which part of code in kernel code running the top 10 frequently and top 10 time consuming?


i search oprofile, how to use them to show?


    [http://homepages.cwi.nl/~aeb/linux/profile.html](http://homepages.cwi.nl/~aeb/linux/profile.html)


after ./configure, make, sudo make install, opcontrol command not found

do it need to make install the new kernel in order to use oprofile


can it do profile for current kernel without installing new kernel

---

### Post by kerry_s on 2015-07-10
use your editor as root & edit /etc/default/grub
i don't know what *ubuntu version your using so i'm going to assume standard ubuntu.

in terminal:
gksudo gedit /etc/default/grub

change line 11:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash profile"

save & close

still in terminal run:
sudo update-grub

reboot your computer, boot might take longer than normal.

---

### Post by zerop2 on 2015-07-10
i mean that i would like to edit kernel code, this method seems automatically fasten the boot times
is there any output or report to show where in the kernel code?

---

### Post by kerry_s on 2015-07-10
you mean you want to compile your own kernel.
[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

---

### Post by tgalati4 on 2015-07-10
To find out where *opcontrol* is located:

```
which opcontrol
```

To start the profiling daemon (background process):

```
sudo opcontrol --start-daemon
```

It appears that *opcontrol* simply reads a device file /proc/profile, so you can enable profiling on several kernels on your system and whatever kernel that you are currently running, the /proc/profile will be for that current session.  It gets rewritten for each boot.  It is up to you to save the statistics during each session.  So, boot up, select a profile-enabled kernel, run the oprofile configuration for the data that you want to collect, start the opcontrol daemon (above), run a standard workload, then print out the results.  The tutorial is straight forward.

Yes, you need to install a new, instrumented (profiled) kernel alongside your existing kernel.  Boot into GRUB2 and select the instrumented kernel.

---

