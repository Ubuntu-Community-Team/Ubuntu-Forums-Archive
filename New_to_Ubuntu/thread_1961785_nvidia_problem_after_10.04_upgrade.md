---
title: "nvidia problem after 10.04 upgrade"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by alcla on 2012-04-19
I upgraded from a lower version to 10.04. I got the following error message:
Ubuntu is running in low-graphic mode.(you may need to upgrade your configuration to solve this)
(EE)Nvidia(0) Failed to load the nvidia kernel module!
(EE)nvidia: ***aborting***
(EE)Screens found, but none have a usable configuration.
 
I uninstalled the nvidia driver, and reinstalled it. 
 
I blacklisted the following: (1) nouveau; (2) vga16fb; (3) vgastate; (4) fb_ddc
 
After I rebooted, Ubuntu started up slightly 
differently, but the same error message was there. What do you suppose I should do next?
 
Thanks in advance
Alfred L. Clark

---

### Post by ammofreak on 2012-04-19
Hi ):P
This might work:
 sudo apt-get install --reinstall nvidia-current

If not, here is an interesting post regarding the same problem: _[http://ubuntuforums.org/showthread.php?t=1480660](http://ubuntuforums.org/showthread.php?t=1480660)_

---

### Post by bogan on 2012-04-20
Hi!, **alcla**,

If reinstall nvidia-current does not work, check out Post #280 on MAFoElffen's Blank Screen Sticky above the Installations & Upgrades Forum.

There is also a full index on Post #2 and a step-by-step Trouble-shooter on Post #1.
[http://ubuntuforums.org/showthread.php?t=1743535&page=71](http://ubuntuforums.org/showthread.php?t=1743535&page=71)

Chao!, **bogan**.

---

### Post by alcla on 2012-04-22
I tried the command, and the error still remains. Here is what happened:

alfred@alfred-desktop:~$ sudo apt-get install --reinstall nvidia-current
[sudo] password for alfred: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavutil1d gimp-help-en libgcj-bc xulrunner-1.9 libregexp-java
  liblog4j1.2-java libpostproc1d gimp-help-common libbcel-java gij liblzo2-2
  cabextract libdb4.6 libpt-1.10.10-plugins-v4l openoffice.org-help-en-gb
  libmx4j-java
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nvidia-current
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.3MB of archives.
After this operation, 72.6MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted nvidia-current 195.36.24-0ubuntu1~10.04.2 [23.3MB]
Fetched 23.3MB in 58s (402kB/s)                                                
Selecting previously deselected package nvidia-current.
(Reading database ... 175486 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_195.36.24-0ubuntu1~10.04.2_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (195.36.24-0ubuntu1~10.04.2) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-195.36.24 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-40-386
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-40-generic
Processing triggers for python-support ...
alfred@alfred-desktop:~$ 

thank you for the suggestion .

---

### Post by anewguy on 2012-04-22
Try installing the build-essential package, then try it again.

There is also a command to reconfigure xorg in that release - I just need to try to find it again!

---

### Post by 23dornot23d on 2012-04-22
Two threads to check the first were some steps we went through to find the cause of
a problem ...... as the 295.33 driver worked partially for one user but the 295,40 did
not

You could try to follow through the thread as we had a slightly worse scenario as we initially only had the console
to work from .....

[http://ubuntuforums.org/showthread.php?p=11832511#post11832511](http://ubuntuforums.org/showthread.php?p=11832511#post11832511)

First try to work out which driver and Graphics card is installed ...... some commands that can be used from the command line help ..... LSPCI in lowecase can be used here and it gives a list of pci devices ...... this is a listing from mine to show where the graphics
card is identified in the list .....

```
[COLOR=Blue]**lspci**[/COLOR]

[keith2@keith-aspire-7730zg ~]$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
[COLOR=Red]**01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300M GS] (rev a1)**[/COLOR]
06:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
[keith2@keith-aspire-7730zg ~]$ 
```But to find the modules used too ..... the following will give more information - again this is from my machine .... yours
may be different ....

> 
keith@keith-Aspire-7730ZG:~/Downloads$ [COLOR=Blue]**lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'**[/COLOR]
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300M GS] (rev a1) (prog-if 00 [VGA controller])
        [COLOR=Red][B]Kernel driver in use: nouveau
        Kernel modules: nouveau, nvidiafb[/B][/COLOR]
keith@keith-Aspire-7730ZG:~/Downloads$                      
This seems related to some older Nvidia GT type cards from what I have read .....

Here is a post explaining some concern .....

[http://ubuntuforums.org/showthread.php?p=11859812#post11859812](http://ubuntuforums.org/showthread.php?p=11859812#post11859812)

---

### Post by alcla on 2012-04-22
I installed the build-essential package using the Ubuntu Software Center. then I ran the reinstall command on the terminal, and got the following:

alfred@alfred-desktop:~$ sudo apt-get install --reinstall nvidia-current
[sudo] password for alfred: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavutil1d gimp-help-en libgcj-bc xulrunner-1.9 libregexp-java
  liblog4j1.2-java libpostproc1d gimp-help-common libbcel-java gij liblzo2-2
  cabextract libdb4.6 libpt-1.10.10-plugins-v4l openoffice.org-help-en-gb
  libmx4j-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/23.3MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 175895 files and directories currently installed.)
Preparing to replace nvidia-current 195.36.24-0ubuntu1~10.04.2 (using .../nvidia-current_195.36.24-0ubuntu1~10.04.2_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
Processing triggers for man-db ...
Setting up nvidia-current (195.36.24-0ubuntu1~10.04.2) ...
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-195.36.24 DKMS files...
Building only for 2.6.32-40-386
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-40-generic
Processing triggers for python-support ...
alfred@alfred-desktop:~$ 

I rebooted, and the error message was still there. After the first time I ran the reinstall command, the error message was still there, but there seemed to be a bit more functionality, that is Ubuntu did a disk check when I rebooted. Do I need to reconfigure?

Any more suggestions

---

### Post by alcla on 2012-04-22
Is the reconfigure command : sudo nvidia-xconfig?

---

### Post by SeijiSensei on 2012-04-22
> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.


To build the driver from source, as is the case here, you need both the build-essential package to get the compiler and related files, and the linux-headers package that matches your current kernel.

```
sudo apt-get install linux-headers-$(uname -r)
```

That uses the uname command to get your current kernel version and downloads the compatible headers.

I would reboot before running this just in case the kernel version has changed.  That way you'll be sure everything is compatible.  Once you install linux-headers, it will be updated if the kernel is updated, and any required kernel modules will be re-compiled against the new headers.

---

### Post by 23dornot23d on 2012-04-22
As said above .... this is the main error

> 
[COLOR=Red][B]Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.[/B][/COLOR]


Nvidia Graphics Cards sometimes purging and re-installing resolves a problem

[B]sudo apt-get update 

sudo apt-get install linux-headers-`uname -r`  [/B] [B]

sudo apt-get remove --purge nvidia-* [/B] [B]

sudo apt-get install nvidia-current [/B] 

__________________________________________________  _____

  only needed if  coming from a desktop ( **sudo service gdm restart** )

__________________________________________________  _____
 

The header files are needed for your version and the commands above
will pull them in for you .....

---

### Post by alcla on 2012-04-22
> **23dornot23d said:**
> As said above .... this is the main error



Nvidia Graphics Cards sometimes purging and re-installing resolves a problem

[B]sudo apt-get update 

sudo apt-get install linux-headers-`uname -r`  [/B] [B]

sudo apt-get remove --purge nvidia-* [/B] [B]

sudo apt-get install nvidia-current [/B] 

.__________________________________________________  _____

  only needed if  coming from a desktop ( **sudo service gdm restart** ) 



__________________________________________________  _____
 

The header files are needed for your version and the commands above
will pull them in for you .....

I gave the above commands in the terminal, and rebooted. I still got the same error message
 

I didnt understand what you ment by this statement."only needed if  coming from a desktop ( **sudo service gdm restart** ) "

---

### Post by 23dornot23d on 2012-04-22
Only a quicker command to restart the Gnome Desktop Manager (GDM) 

A reboot is the same .....

But obviously there are still some problems ...

______________________________________________________________________

Lets do a safe-upgrade and make sure the computer is uptodate ....

[B]sudo apt-get update

sudo apt-get install aptitude

sudo aptitude update

sudo aptitude safe-upgrade[/B]

There may be a long list here ..... ( let me know what it wants to remove ( if anything )

otherwise .... if there is nothing to remove ..... carry on .... answer y

reboot after it has finished ....

---

### Post by mikechant on 2012-04-24
Does anyone agree that there's something wrong here not directly related to the nvidia drivers? I ask because I would expect that the relevant Linux headers package should be installed by default.
Possibly some issue relating to the upgrade?

---

### Post by alcla on 2012-04-26
My origial installation of Ubuntu was version 6.06. Later on I upgraded to version 8.06, and there didn't seem to be a problem. Recently, I upgraded to version 10.04. Can 6.06 be upgraded to 10.04 without difficulty?

---

### Post by 23dornot23d on 2012-04-27
@[mikechant]("http://ubuntuforums.org/member.php?u=721760")

> 
Does anyone agree that there's something wrong here not directly related  to the nvidia drivers? I ask because I would expect that the relevant  Linux headers package should be installed by default.
Possibly some issue relating to the upgrade?


It would be good if for every kernel and graphics card the headers could be automatically pulled in ..... 
I think that most things that are needed for the graphics to work are pulled in if they can be - but there
are occasions where they are not and a warning is given in the text ..... often a red FAIL comes up against the
part that cannot be completed in my experience with this ..... then it is a metter of seeing exactly what is missing
and what it failed on - and then rectifying the situation ......

_______________________________________________

@alcla

Upgrading can be done .... as I have gone up the ladder of versions from 8.04 ... to see what happens ..... 

But there is always a risk of problems occuring if the older versions were not free of problems and also fully uptodate before the upgrade ..... 

Usually at some point a clean install seems to be better .... 
( if problems have occured that stop you getting any further )

If it has reported any errors back ..... post them ..... or explain what they are

( graphics cards are the main problem that I come across ...... although the upgraded system can be loaded on the computer ok ..... often people see a black screen at start up and think that it is not working ...... but once the graphics are set correctly all can be ok )

Let us know what the situation is at the moment ...... as you can upgrade .....

But you are the first person I have come across on here going through 4 years worth of
upgrades ...... from 6.06 ..... to 10.04 - as it is a big upgrade step to 10.04

What computer is it and what graphics card is in the computer do this in a terminal
as I asked earlier ..... as it gives us more information to work with

**lspci**

---

### Post by bogan on 2012-05-04
Hi!,** All,**  There is a new driver, 295.49 available from nvidia downloads
 [http://www.nvidia.co.uk/object/linux-display-ia32-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.49-driver-uk.html)

 Noon Friday May 4th; ```
nvidia-installer --latest 
``` now   returns: v295.49 and     ```
nvidia-installer -f 
``` will install   295.49 after un-installing the previous version.

 NVNews says of version295.49:> **Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**
Chao!, **bogan**

---

