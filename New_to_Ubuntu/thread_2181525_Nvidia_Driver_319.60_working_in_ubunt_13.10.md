---
title: "Nvidia Driver 319.60 working in ubunt 13.10?"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by anandharaja2 on 2013-10-18
hi
today i installed ubuntu 13.10 after that i try to install nvidia driver 319.60 downloaded from nvidia site, i got the "Unable to compile Nvidia Kernels" error, so i try to install 319.23 version got the same error.

How to install the nvidia driver?
any one insalled succesfully?

---

### Post by hX7GbTG on 2013-10-18
I am also having this same problem.

---

### Post by Frogs Hair on 2013-10-18
Hello and Welcome 

I have that driver installed via Software & Updates > Additional Drivers 319 - updates . That is what nVidia x-server settings and synaptic are displaying. I have never installed from the nVidia site though.

Edit: I am using Ubuntu and settings may vary.

[http://askubuntu.com/questions/197110/enable-drivers-on-lubuntu](http://askubuntu.com/questions/197110/enable-drivers-on-lubuntu)

---

### Post by Samurai336 on 2013-10-18
I am having the same issue. I am using the *.run from nvidia's website since current repositories only have 319.32. Also installing from the repositories wont also install the 32-bit GL files needed to make steam run nicely.

---

### Post by Samurai336 on 2013-10-18
If you want to just get things working again I suggest installing the nvidia-319 (which is version 319.32) from the repositories via aptitude or apt-get for now. My guess is that its an issue in the nvidia installer building against the 3.11 kernel headers. So will twiddle our thumbs for now while nvidia gets its act together. 

Though in the mean time if someone has a solution I am open to it.

---

### Post by GWBouge on 2013-10-18
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

319.60 is available by using nvidia-319-updates from the X-swat raring repo.  They're not packaged for Saucy yet, but I've had them installed for a while in 13.10 without any issues.

---

### Post by Samurai336 on 2013-10-18
Thanks! 

Know anything about the 32-bit GL for my steam install?

---

### Post by GWBouge on 2013-10-18
I do not, sorry  =o(

Might want to try asking in the Gaming and Leisure section or in the Steam forums with some more details if you can't figure it out.

---

### Post by bertan2 on 2013-10-19
Was having endless problems with Nvidia drivers and my 24" Dell display not being recognized by Ubuntu, using a suboptimal resolution, displaying off center, and so on. That was even after installing the proprietary driver rather than the open driver.

I solved the problems for good by bypassing the Nvidia card altogether. 

The ASUS desktop has two VGA display connections on the back, one from the Nvidia card and one direct from the CPU motherboard. I plugged the monitor into the direct connection rather than the Nvidia card connection. Then I tapped DEL during boot to enter the ASUS UEFI. Go to Advanced mode. Change the graphics setting from "Auto" to "iGPU" (i.e. use only the Intel CPU's integrated graphics processing unit, never the Nvidia PCI card). Saved the settings and continued with boot.

Now have a perfect 1920 x 1080 display, recognized as such by Ubuntu.

---

### Post by jos-digiplace on 2013-10-19
Before you install the driver you have to do the following actions:

[COLOR=#000000]sudo apt-get install linux-source[/COLOR][COLOR=#000000][FONT=Georgia][SIZE=1][COLOR=#111111]
[/COLOR][/SIZE][/FONT][/COLOR][COLOR=#000000]sudo apt-get install linux-headers-$(uname -r)[/COLOR]

[COLOR=#000000]The important thing is that you first blacklist the nouveau driver:[/COLOR]

[COLOR=#000000]A simple way to prevent Nouveau from loading and performing a kernel modeset is to add configuration directives for the module loader to a file in /etc/modprobe.d/. These configuration directives can technically be added to any file in /etc/modprobe.d/, but many of the existing files in that directory are provided and maintained by your distributor, which may from time to time provide updated configuration files which could conflict with your changes. Therefore, it is recommended to create a new file, for example, /etc/modprobe.d/disable-nouveau.conf, rather than editing one of the existing files, such as the popular /etc/modprobe.d/blacklist.conf. Note that some module loaders will only look for configuration directives in files whose names end with .conf, so if you are creating a new file, make sure its name ends with .conf.[/COLOR]
[COLOR=#000000]
Whether you choose to create a new file (It's my preferred configuration) or edit an existing one, the following two lines will need to be added:[/COLOR]


[COLOR=#000000]blacklist nouveau[/COLOR]
[COLOR=#000000]options nouveau modeset=0[/COLOR]

[COLOR=#000000]Then you install the nvidia driver with your prefered configuration ( x-swat, nvidia of the distributed drivers from Ubuntu). [/COLOR]

---

### Post by Z3t4 on 2013-10-22
Hi,
I have the same problem trying to install nvidia driver 331.17 after upgrading to 13.10, the nvidia kernel module build fails:

> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Oct 22 17:38:01 2013
installer version: 331.17

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 331.17.
-> There appears to already be a driver installed on your system (version: 331.17).  As part of installing this driver (version: 331.17), the existing driver will be uninstalled.  Are you sure you want to continue? ('no' will abort installation) (Answer: Yes)
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation anyway? (Answer: Yes)
-> Would you like to register the kernel module sources with DKMS? This will allow DKMS to automatically build a new module, if you install a different kernel later. (Answer: Yes)
-> Installing both new and classic TLS OpenGL libraries.
-> Installing both new and classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32-bit compatibility libraries? (Answer: Yes)
-> Parsing log file:
-> done.
-> Validating previous installation:
-> The previously installed file '/usr/lib/xorg/modules/drivers/nvidia_drv.so' seems to have changed, but `prelink -u` failed; unable to restore '/usr/lib/xorg/modules/drivers/nvidia_drv.so' to an un-prelinked state.
-> Un-prelinking unsuccessful: '/usr/lib/xorg/modules/drivers/nvidia_drv.so' will not be uninstalled.
-> The previously installed file '/usr/bin/nvidia-smi' seems to have changed, but `prelink -u` failed; unable to restore '/usr/bin/nvidia-smi' to an un-prelinked state.
-> Un-prelinking unsuccessful: '/usr/bin/nvidia-smi' will not be uninstalled.
-> The previously installed file '/usr/share/man/man1/nvidia-smi.1.gz' seems to have changed, but `prelink -u` failed; unable to restore '/usr/share/man/man1/nvidia-smi.1.gz' to an un-prelinked state.
-> Un-prelinking unsuccessful: '/usr/share/man/man1/nvidia-smi.1.gz' will not be uninstalled.
-> The previously installed file '/usr/bin/nvidia-xconfig' seems to have changed, but `prelink -u` failed; unable to restore '/usr/bin/nvidia-xconfig' to an un-prelinked state.
-> Un-prelinking unsuccessful: '/usr/bin/nvidia-xconfig' will not be uninstalled.
-> The previously installed file '/usr/share/man/man1/nvidia-xconfig.1.gz' seems to have changed, but `prelink -u` failed; unable to restore '/usr/share/man/man1/nvidia-xconfig.1.gz' to an un-prelinked state.
-> Un-prelinking unsuccessful: '/usr/share/man/man1/nvidia-xconfig.1.gz' will not be uninstalled.
-> The previously installed file '/usr/bin/nvidia-settings' seems to have changed, but `prelink -u` failed; unable to restore '/usr/bin/nvidia-settings' to an un-prelinked state.
-> Un-prelinking unsuccessful: '/usr/bin/nvidia-settings' will not be uninstalled.
-> The previously installed file '/usr/share/man/man1/nvidia-settings.1.gz' seems to have changed, but `prelink -u` failed; unable to restore '/usr/share/man/man1/nvidia-settings.1.gz' to an un-prelinked state.
-> Un-prelinking unsuccessful: '/usr/share/man/man1/nvidia-settings.1.gz' will not be uninstalled.
-> The previously installed file '/usr/bin/nvidia-bug-report.sh' seems to have changed, but `prelink -u` failed; unable to restore '/usr/bin/nvidia-bug-report.sh' to an un-prelinked state.
-> Un-prelinking unsuccessful: '/usr/bin/nvidia-bug-report.sh' will not be uninstalled.
-> The previously installed symlink '/usr/lib/libOpenCL.so' has target '/etc/alternatives/x86_64-linux-gnu_libOpenCL.so', but it was installed with target 'libOpenCL.so.1'.  /usr/lib/libOpenCL.so will not be uninstalled.
-> The previously installed symlink '/usr/lib/vdpau/libvdpau_nvidia.so.1' has target '/etc/alternatives/x86_64-linux-gnu_libvdpau_nvidia.so.1', but it was installed with target 'libvdpau_nvidia.so.331.17'.  /usr/lib/vdpau/libvdpau_nvidia.so.1 will not be uninstalled.
-> The previously installed symlink '/usr/lib/libvdpau_nvidia.so' has target '/etc/alternatives/x86_64-linux-gnu_libvdpau_nvidia.so', but it was installed with target 'vdpau/libvdpau_nvidia.so.331.17'.  /usr/lib/libvdpau_nvidia.so will not be uninstalled.
-> The previously installed symlink '/usr/lib32/libOpenCL.so' has target '/etc/alternatives/x86_64-linux-gnu_libOpenCL.so_lib32', but it was installed with target 'libOpenCL.so.1'.  /usr/lib32/libOpenCL.so will not be uninstalled.
-> The previously installed symlink '/usr/lib32/libvdpau_nvidia.so' has target '/etc/alternatives/x86_64-linux-gnu_libvdpau_nvidia.so_lib32', but it was installed with target 'vdpau/libvdpau_nvidia.so.331.17'.  /usr/lib32/libvdpau_nvidia.so will not be uninstalled.
-> The previously installed symlink '/usr/lib32/vdpau/libvdpau_nvidia.so.1' has target '/etc/alternatives/x86_64-linux-gnu_libvdpau_nvidia.so.1_lib32', but it was installed with target 'libvdpau_nvidia.so.331.17'.  /usr/lib32/vdpau/libvdpau_nvidia.so.1 will not be uninstalled.
-> done.
WARNING: Your driver installation has been altered since it was initially installed; this may happen, for example, if you have since installed the NVIDIA driver through a mechanism other than nvidia-installer (such as your distribution's native package management system).  nvidia-installer will attempt to uninstall as best it can.  Please see the file '/var/log/nvidia-installer.log' for details.
-> Uninstalling NVIDIA Accelerated Graphics Driver for Linux-x86_64 (1.0-33117 (331.17)):
-> DKMS module detected; removing...
-> Unable to restore symbolic link /usr/lib/xorg/modules/drivers/nvidia_drv.so -> /etc/alternatives/x86_64-linux-gnu_nvidia_drv (File exists).
-> Unable to restore symbolic link /usr/bin/nvidia-smi -> /etc/alternatives/x86_64-linux-gnu_nvidia_smi (File exists).
-> Unable to restore symbolic link /usr/share/man/man1/nvidia-smi.1.gz -> /etc/alternatives/x86_64-linux-gnu_nvidia-smi.1.gz (File exists).
-> Unable to restore symbolic link /usr/bin/nvidia-xconfig -> /etc/alternatives/x86_64-linux-gnu_nvidia_xconfig (File exists).
-> Unable to restore symbolic link /usr/share/man/man1/nvidia-xconfig.1.gz -> /etc/alternatives/x86_64-linux-gnu_man_nvidiaxconfig.gz (File exists).
-> Unable to restore symbolic link /usr/bin/nvidia-settings -> /etc/alternatives/nvidia_settings (File exists).
-> Unable to restore symbolic link /usr/share/man/man1/nvidia-settings.1.gz -> /etc/alternatives/man_nvidiasettings.gz (File exists).
-> Unable to restore symbolic link /usr/bin/nvidia-bug-report.sh -> /etc/alternatives/x86_64-linux-gnu_nvidia_bug_report (File exists).
-> Unable to delete directories created by previous installation.
-> done.
-> Uninstallation of existing driver: NVIDIA Accelerated Graphics Driver for Linux-x86_64 (331.17) is complete.
-> Skipping installation of the libvdpau wrapper library.
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64' (331.17):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
   ignored deprecated option -q
-> done.
-> Driver file installation is complete.
-> Installing DKMS kernel module:
ERROR: Failed to run `/usr/sbin/dkms build -m nvidia -v 331.17 -k 3.11.0-12-generic`: 
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.11.0-12-generic module KERNEL_UNAME=3.11.0-12-generic; make -C uvm module KERNEL_UNAME=3.11.0-12-generic KBUILD_EXTMOD=/var/lib/dkms/nvidia/331.17/build/uvm...........(bad exit status: 2)
ERROR (dkms apport): binary package for nvidia: 331.17 not found
Error! Bad return status for module build on kernel: 3.11.0-12-generic (x86_64)
Consult /var/lib/dkms/nvidia/331.17/build/make.log for more information.
-> error.
ERROR: Failed to install the kernel module through DKMS. No kernel module was installed; please try installing again without DKMS, or check the DKMS logs for more information.
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).


I installed 331.13 via xorg-edgers PPA without problems, but it lacks the 32-bit libs that steam needs.

Kind regards.

---

### Post by Z3t4 on 2013-10-22
Hi,
I managed to propperly install nvidia driver 331.17, seems that there is a problem with newer kernels:

[https://devtalk.nvidia.com/default/topic/625212/linux/-331-17-beta-drivers-feedback-thread/](https://devtalk.nvidia.com/default/topic/625212/linux/-331-17-beta-drivers-feedback-thread/)

You can fix it patching the /kernel/nv-linux.h file in the driver source, the path for 325.15 seems to work fine:

[ATTACH]247171[/ATTACH]

First, I uncompressed the driver "./NVIDIA-Linux-x86_64-331.17.run -x"
Extracted the patch: "unzip nv-325.15_kernel-3.11.patch.zip -d ./NVIDIA-Linux-x86_64-331.17/kernel/"
Apply the patch: "patch < ./NVIDIA-Linux-x86_64-331.17/kernel/nv-325.15_kernel-3.11.patch -d ./NVIDIA-Linux-x86_64-331.17/kernel/"

then install the beta driver as ussual:

Open a console with ctrl+alt+f1
stop lightdm service "sudo service lightdm stop"
install driver with "sudo ./NVIDIA-Linux-x86_64-331.17/nvidia-installer"
start lightdm service "sudo service lightdm start"

Kind regards.

---

### Post by Samurai336 on 2013-10-25
Z3t4: 

Made the install work successfully, however all my graphics stopped working :/.

---

### Post by Z3t4 on 2013-10-26
> **Samurai336 said:**
> Z3t4: 

Made the install work successfully, however all my graphics stopped working :/.

I'm not a pro, but i think you can go back to stock nvidia driver by booting in recovery mode, choose "Network" to enable networking and mout all fs in rw mode, after that choose "Root" to open a root shell, delete all nvidia drivers with "apt-get remove --purge nvidia-*" (make sure that there are only NVIDIa packages on the list before entering yes, apt commands with wildcards are dangerous), after that install the stock driver with "apt-get install nvidia-common" (or you can retry to install the beta one).

Regards.

---

### Post by Samurai336 on 2013-10-26
Oh I got everything back to working I was just letting you know what happened when I tried your patch. 
Thanks Though.

---

### Post by adec2 on 2013-10-26
Very odd I'm using 13.10 and installing the nvidia drivers from xorg/edgers ppa has been working fine just gone to 331.17 myself and everything is fine

---

### Post by Z3t4 on 2013-10-27
> **Samurai336 said:**
> Oh I got everything back to working I was just letting you know what happened when I tried your patch. 
Thanks Though.
No problem xD
> **adec2 said:**
> Very odd I'm using 13.10 and installing the nvidia drivers from xorg/edgers ppa has been working fine just gone to 331.17 myself and everything is fine
The only problem I had was that steam do not work in my x64 installation with that PPA's driver; when you install the beta drivers asks you if you want the 32-bit compatibility libs also, those aren't included in xorg/edgers package, I think. The've just upladed the 331.17 package by the way.

---

### Post by adec2 on 2013-10-27
Using xorg/edgers ppa all my 32/64 bit libs are installed fine and running steam fine. something wicked going on here :)

---

