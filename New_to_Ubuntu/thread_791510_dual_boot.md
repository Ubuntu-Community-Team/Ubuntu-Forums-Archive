---
title: "dual boot"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by phanipalagummi on 2008-05-12
I m very new to linux,and i want to dual boot my system,
i use      80GB hdd,512mb ram.
please give a good link for this with your suggestions,

---

### Post by mr-Kirch on 2008-05-12
first partion disk space...look that up

to dual boot you go to ubuntu.com
download 8.04
get infra-recorder or any iso burner
burn the iso (it will be on your desktop) to a disk
put disk in drive
shut down computer (with disk still in drive)
it will boot off your disk
then when you get to the part about partioning disk space check most unused disk space or something like that

---

### Post by marquee moon on 2008-05-12
The short answer is that if you have windows installed, ubuntu will create a dual boot system by default if you install ubuntu on a separate partition & don&#8217;t wipe out your existing windows partition. 

If you&#8217;ve got MS vista, there&#8217;s a partition manager included in that. Shrink your existing windows partition to free up around 10Gb of space. If you don&#8217;t have a partition manager, you can access one via the ubuntu live CD.

Once you&#8217;ve got some free, non-formatted space, install ubuntu into this using the &#8220;guided- use largest available free space&#8221; option during the ubuntu installation process. When installation is complete, you&#8217;ll have a dual boot with the &#8220;Grub&#8221; program controlling the boot procedure.

---

### Post by lswest on 2008-05-12
i find this guide very useful: [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

and i recommend at least 10GB for Linux.

---

### Post by shifty_powers on 2008-05-12
i seem to be pushing this a lot lately, but my first step for you would be to try wubi...

[http://wubi-installer.org/](http://wubi-installer.org/)

> Wubi is an officially supported Ubuntu installer for Windows users that can bring you to the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other Windows application, in a simple and safe way. Are you curious about Linux and Ubuntu? Trying them out has never been easier!

Wubi is Simple

No need to burn a CD. Just run the installer, enter a password for the new account, and click "Install", go grab a coffee, and when you are back, Ubuntu will be ready for you.

Wubi is Safe

You keep Windows as it is, Wubi only adds an extra option to boot into Ubuntu. Wubi does not require you to modify the partitions of your PC, or to use a different bootloader, and does not install special drivers. It works just like any other application. Wubi is spyware and malware free, and being open source, anyone can verify that.

Wubi is Discrete

Wubi keeps most of the files in one folder, and if you do not like it, you can simply uninstall it as any other application.

Wubi is Free

Wubi and Ubuntu cost absolutely nothing (free as in beer), but yet provide a state of the art, fully functional, operating system that does not require any activation and does not impose any restriction on its use (free as in freedom).

---

