---
title: "Driver installation failing"
date: 2024-07-17
forum: New to Ubuntu
---

### Post by slimkix on 2024-07-17
Hello everyone,

So im new to ubuntu and linux in general and i've been trying to install the nvidia 550 driver or at least the 545. I tried adding the ppa repsitory and installing it it from there but whenever i do that, it automatically selects the nouveau driver although i chose to install the 545 one. When i saw that, i looked up online and read that i can install the driver from the Software 11 Update application and when i did that before,i was getting an error but now for some reason i'm not getting it anymore. It says the propietary driver has been installed but after i reboot the system and try the nvidia-smi command, i get an error saying "NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running."

Since that didn't work, i decided i'll just download the driver from the official nvidia site. I did that and purged nvidia from the system then rebooted. After that, i installed the build essantial kdms. Then after, i blacklisted the nouveau and updated the initramfs. Then i rebooted again. I then disabled the display manager and went to the text based terminal. From there, navigated to the downloaded driver directory and made it executable and then executed it. I then followed the on-screen instructions and finished the installation. When i re-enabled the display manager, i still wasn't able to use full screen resolution. I figured id need to reboot first and so i did but it's still the same. I still get the same error as before saying"NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA  driver. Make sure that the latest NVIDIA driver is installed and  running." 

I'm sure im doing something wrong but at the same time i think im not. I followed the instructions exactly how i saw online and tried mutliple methods. I even had to reinstall ubuntu multiple times so i can follow the instructions from the start again. 

If you know the solution to any of the 2 issues, either the proprietary driver or from the official site, please let me know.

Thank you in advance!!

---

### Post by #&amp;thj^% on 2024-07-17
nVidia drivers not properly removed or purged will leave you in bad place.
Also installing the nVidia binary from nVdia is not recommended on Ubuntu.
```
apt list --installed|grep nvidia

```
Might help you and us to find a solution.

---

### Post by slimkix on 2024-07-17
[HTML][HTML]```
[CODE][CODE][CODE]WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

libnvidia-cfg1-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-common-535-server/noble-updates,noble-updates,noble-security,noble-security,now 535.183.01-0ubuntu0.24.04.1 all [installed,automatic]
libnvidia-compute-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-compute-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed,automatic]
libnvidia-decode-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-decode-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed,automatic]
libnvidia-encode-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-encode-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed,automatic]
libnvidia-extra-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-fbc1-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-fbc1-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed,automatic]
libnvidia-gl-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-gl-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed,automatic]
linux-modules-nvidia-535-server-open-6.8.0-38-generic/noble-updates,noble-security,now 6.8.0-38.38+1 amd64 [installed,automatic]
linux-modules-nvidia-535-server-open-generic-hwe-24.04/noble-updates,noble-security,now 6.8.0-38.38+1 amd64 [installed]
linux-objects-nvidia-535-6.8.0-38-generic/noble-updates,noble-security,now 6.8.0-38.38+1 amd64 [installed,automatic]
linux-signatures-nvidia-6.8.0-38-generic/noble-updates,noble-security,now 6.8.0-38.38+1 amd64 [installed,automatic]
nvidia-compute-utils-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
nvidia-driver-535-server-open/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed]
nvidia-firmware-535-server-535.183.01/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
nvidia-kernel-common-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
nvidia-kernel-source-535-server-open/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
nvidia-prime/noble,noble,now 0.8.17.2 all [installed,automatic]
nvidia-settings/noble,now 510.47.03-0ubuntu4 amd64 [installed,automatic]
nvidia-utils-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
xserver-xorg-video-nvidia-535-server/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]

```[/CODE][/CODE][/HTML][/HTML]
[/CODE]

Thats what it shows. I don't know how there are so many. I tried [HTML]dpkg -l | grep nvidia-driver[/HTML] before and it showed that nothing was installed before i installed any driver. Do you know of a way perhaps to make sure all installations are completely removed?

---

### Post by grahammechanical on 2024-07-19
For those who do not know: When we install Ubuntu and tick to install third party software the installer will find and install a proprietary video driver. If the video adapter if Nvidia the driver then it will be an Nvidia proprietary video driver. Otherwise, the install will finish and use an open source video driver which in many cases is sufficient for the user's need.

Another way to install a proprietary video driver is to open Software & Updates>Additional Drivers tab. If the machine is connected to the internet the utility will look for and offer to install proprietary video drivers. It will also uninstall proprietary video drivers. A reboot will load the operating system using an open source video driver.

There is a third way to install and remove proprietary video drivers. It is to use the command line to run ubuntu-drivers. This link explains its commands. It is a recent wen page.

[https://ubuntu.com/server/docs/nvidia-drivers-installation](https://ubuntu.com/server/docs/nvidia-drivers-installation)

My laptop users Intel UHD graphics. There are no Intel drivers. The system uses the very good open source video drivers.

Regards

---

### Post by #&amp;thj^% on 2024-07-19
> **slimkix said:**
> [
. Do you know of a way perhaps to make sure all installations are completely removed?
Yep I'm working with another user now here: [https://ubuntuforums.org/showthread.php?t=2499093&p=14197835#post14197835](https://ubuntuforums.org/showthread.php?t=2499093&p=14197835#post14197835)
You may want to look there first.
I will include steps to remove all and start fresh, I'm not a fan of ubuntu-drivers leaves too much cruft that will break your system with driver changes.
```
apt policy ubuntu-drivers-common
ubuntu-drivers-common:
  Installed: (none)
  Candidate: 1:0.9.7.6ubuntu3
  Version table:
     1:0.9.7.6ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status

```
Please Note, I'm not suggesting to remove ubuntu-drivers, I'm kind of a rebel. ;)
See this:
```
 apt depends ubuntu-drivers-common
ubuntu-drivers-common
  PreDepends: dpkg (>= 1.15.7.2)
  Depends: <python3:any> (>= 3.2~)
    python3
 |Depends: debconf (>= 0.5.00)
  Depends: <debconf-2.0>
    cdebconf
    debconf
  Depends: libc6 (>= 2.38)
  Depends: libdrm2 (>= 2.3.1)
  Depends: libkmod2 (>= 5~)
  Depends: libpci3 (>= 1:3.8.0)
  Depends: python3-apt
  Depends: python3-xkit
  Depends: python3-click
  Depends: udev (>= 204-0ubuntu4~)
  Depends: pciutils
  Depends: usbutils
 |Depends: kmod
  Depends: <module-init-tools>
  Conflicts: <jockey-common>
  Conflicts: <jockey-gtk>
  Conflicts: <jockey-kde>
  Conflicts: nvidia-common (<< 1:0.2.46)
  Breaks: nvidia-prime (<< 0.6)
  Suggests: <python3-aptdaemon.pkcompat>
  Replaces: <jockey-common>
    ubuntu-drivers-common
  Replaces: <jockey-gtk>
    ubuntu-drivers-common
  Replaces: <jockey-kde>
    ubuntu-drivers-common
  Replaces: nvidia-common (<< 1:0.2.46)

```
```
 nvidia-smi|grep NVIDIA-SMI
| NVIDIA-SMI 535.171.04             Driver Version: 535.171.04   CUDA Version: 12.2     |

```

---

