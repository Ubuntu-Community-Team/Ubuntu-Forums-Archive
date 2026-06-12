---
title: "HOWTO:  Install any Intel OS in VMWare Player"
date: 2006-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by yensidetlaw on 2006-04-15
This guide will expalin the process to use a couple of free tools to allow you to run almost an OS within VMWare Player.  This guide is an extension of the fabulous guide originally posted by **dryandplain** and **BLTicklemonster**.  The original thread can be found here:  [GNOME - HOWTO: Install Windows XP/2000 in VMWare Player]("http://ubuntuforums.org/showthread.php?t=84275&highlight=cd+rom+drive").

To catch everyone up, VMPlayer is a free application that allows users to run virtual copies of differnent operating systems.  However, VMWare player does not allow you to create these virtual machines.  Using QEMU and a text editor, we will create the files needed to be able to run any Intel based OS within a virtual machine.

One side note:  The Mac OS is still not supported, even though it is Intel based now.  Hopefully this will change, but I'm not holdin gmy breath.

Installing VM Player is more time consuming than complicated.  First, we need to lay the ground work:

```

apt-get install build-essential
uname -r
apt-get install linux-headers-'kernel version'
apt-get install gcc-3.4
apt-get install g++-3.4

```

You can download the linux binaries from [VMWare Player]("http://www.vmware.com/download/player/") and it comes with a CLI installer that is pretty easy.

To install:

```

tar xvzf VMware-player-1.0.0-16981.tar.gz
cd vmware-player-distrib
CC=/usr/bin/gcc-3.4
export CC=/usr/bin/gcc-3.4
sudo ./vmware-install.pl

```

The next parts are taken dirrectly from dryandplain's install guide:

[I]The installer has an unusually high number of prompts, all of which can be answered the default "yes" to by hitting enter. After hitting enter a few dozen times and agreeing to the license, everything should install successfully. If you're having problems installing the actual player, that other guy might be more qualified to diagnose it than I am. Moving along...

There are two components to a virtual machine, the hard drive image and a text file that VMWare interprets. First, we'll create an image with QEMU.

I know this sounds a little odd, but I couldn't get the QEMU command used to generate the disk working from the Linux port. Fortunately, the utility works fine with the Windows port under Wine. I can't really bothered to delve into the specifics of installing Wine other than suggesting:[/I]

```
sudo apt-get install wine
```

[I]
Then download and install the Windows version of QEMU if that does now work, then get it here (make sure you install it . Create a folder in /home/yourname and name it either WindowsXPPro or Windows2000Pro, and in the terminal go to it:[/I]

```
cd /home/yourname/folder you created
```

*Then execute qemu from a command line as follows:*

```
wine "c:\Program Files\Qemu\qemu-img.exe" create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk
```

OK, a couple of my own comments:  This creates a 320kb file that is designed to be the virtual hard drive your virtual machine will use.  In this case, it's a 2GB hard drive.  I typically make 5GB or 10GB drives by changing the 2G to 5G or 10G (or whatever you need).  ONCE THIS IS SET, IT CAN NOT BE CHANGED.  Choose your size wisely, just in case size does truely matter.

Also, the name of the file is not *really* important.  I created 2 stock VMDK drive files for my own use (5gb-stock.vmdk and 10gb-stock.vmdk).  I keep all my OS's in seperate folders, so this way works for me.  You can name them all based on the OS, as in the code above.  To change the name, simply modify both instances of *WindowsXPPro.vmdk* to whatever name you want.

Now that we've created the "hard drive," we need to create the file that makes VMWare Player work.  You can use either an ISO file or a physical CD to install the guest OS.

Either way, the file you need to create is a .vmx file.  This file can be named however you want.  I name them based on the OS it controls (for example, my WindowsXP Pro file is WindowsXPPro.vmx and my Ubuntu Dapper file is dapper_flight6.vmx).

For CD installs:
```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "atapi-cdrom"
ide1:0.autodetect = "TRUE"
floppy0.startConnected = "False"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 86 fc d2 c6 27 b7-7d 0a dc c4 9f 36 b9 3f"
uuid.bios = "56 4d 86 fc d2 c6 27 b7-7d 0a dc c4 9f 36 b9 3f"
ethernet0.generatedAddress = "00:0c:29:36:b9:3f"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "WindowsXPPro.vmss"
tools.remindInstall = "TRUE"
```

And for ISO installs:
```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "WindowsXPPro.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
floppy0.startConnected = "False"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
uuid.bios = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
ethernet0.generatedAddress = "00:0c:29:4c:23:7b"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "WindowsXPPro.vmss"
tools.remindInstall = "TRUE"
```

Here are the important parts of these nearly identical files:

**ide0:0.filename = "WindowsXPPro.vmdk"** - This is the file name of the virtual hard drive file you created earlier.
**ide1:0.fileName = "WindowsXPPro.iso"** - (for ISO installs only) This is the name of the OS ISO file.
**displayName = "Windows XP Pro"** - This is the display name.  It's largely unimportant and can be changed to anything.
**nvram = "WindowsXPPro.nvram"** - This is the virtual machine RAM file.  I recomend you rename this file to match the name of the .vmx file for your OS.
**checkpoint.vmState = "WindowsXPPro.vmss"** - I'm not sure what this is for, but as above I recomend that you change it to match the name of the .vmx file for your OS.

Lastly, and most importantly, there is **guestOS = "winxppro"**.  This setting allows you to use any Intel based OS.  The importance of this is that VMWare Player has specifc application level optimization based on the listed guestOS.  Here is the list of values for the guestOS field:

**_Windows - 32bit_**
    * winVista = Windows Vista (experimental)
    * longhorn = Windows Longhorn (experimental)
    * winNetBusiness = Windows 2003 Small Business Server
    * winNetEnterprise = Windows 2003 Enterprise Server
    * winNetStandard = Windows 2003 Server
    * winNetWeb = Windows 2003 Web Server Edition
    * winXPPro = Windows XP Professional Edition
    * winXPHome = Windows XP Home Edition
    * win2000AdvServ = Windows 2000 Advanced Server
    * win2000Serv = Windows 2000 Server
    * win2000Pro = Windows 2000 Professional
    * winNT = Windows NT
    * winMe = Windows Me
    * win98 = Windows 98
    * win95 = Windows 95
    * win31 = Windows 3.1 / Windows 3.11
    * windows = Other Windows

**_Windows - 64bit_**
    * winVista-64 = Windows Vista x64 Edition (experimental)
    * longhorn-64 = Windows Longhorn x64 Edition (experimental)
    * winNetEnterprise-64 = Windows 2003 Enterprise Server x64 Edition
    * winNetStandard-64 = Windows 2003 Server x64 Edition
    * winXPPro-64 = Windows XP Professional x64 Edition

**_Linux - 32bit_**
    * ubuntu = Ubuntu Linux
    * redhat = Red Hat Linux
    * rhel4 = Red Hat Enterprise Linux 4
    * rhel3 = Red Hat Enterprise Linux 3
    * rhel2 = Red Hat Enterprise Linux 2
    * suse = SuSE Linux
    * sles = SuSE Linux Enterprise Server
    * mandrake = Mandrake Linux
    * nld9 = Novell Linux Desktop 9
    * sjds = Sun Java Desktop System
    * turbolinux = Turbo Linux
    * other26xlinux = Other Linux on a 2.6.x kernel
    * other24xlinux = Other Linux on a 2.4.x kernel
    * linux = Other Linux

**_Linux - 64bit_**
    * ubuntu-64 = Ubuntu Linux 64-bit
    * rhel4-64 = Red Hat Enterprise Linux 4 64-bit
    * rhel3-64 = Red Hat Enterprise Linux 3 64-bit
    * sles-64 = SuSE Linux Enterprise Server 64-bit
    * suse-64 = SuSE Linux 64-bit
    * other26xlinux-64 = Other Linux 2.6.x 64-bit
    * other24xlinux-64 = Other Linux 2.4.x 64-bit
    * otherlinux-64 = Other Linux 64-bit

**_Sun, Novel, FreeBSD, other_**
    * solaris10-64 = Solaris 10 64-bit
    * solaris10 = Solaris 10
    * solaris9 = Solaris 9
    * solaris8 = Solaris 8
    * solaris7 = Solaris 7
    * solaris6 = Solaris 6
    * solaris = Other Solaris
    * netware6 = Netware 6.x
    * netware5 = Netware 5.x
    * netware4 = Netware 4.x
    * netware = Other Netware
    * freeBSD-64 = FreeBSD 64-bit
    * freeBSD = FreeBSD
    * other = Other OS
    * other-64 = Other 64-bit OS

Once you get this file configured and created, launching the virtual machine is  as simple as double clicking on the .vmx file.  For a fresh install, this baically creates a new computer for you, and after that the installation of the os is pretty much identical to how you would install an OS on a new real computer.

I have used this HowTo steps to install ~15 different OS's have haven't had any problems with any of them and wrote this HowTo using my Ubuntu Dapper_Flight6 virtual machine.  However, I'll admit I'm no expert at VMWare, and I still reference the post by **dryandplain** and **BLTicklemonster** if I get stuck.  They, and the others who have been on that thread, really are the experts.

Enjoy the wide world of virtualization!

---

### Post by heikkijh on 2006-06-13
How about Win98 in VMware Player? What is needed in vmx-file for it?
I already have Player running in my Kubuntu 6.06 and qemu made win98.vmdk file.
I only need win98.vdx file or some advice how to build it.

---

### Post by nzgreen on 2006-06-14
Thanks yensidetlaw.  I just tried this on dapper and it worked fine.  I used vmware-player from multiverse and qemu from universe.  I found the following commandline worked fine without needing to resort to the Windows version of qemu:
```
qemu-img create -f vmdk WindowsXPPro.vmdk 4G
```

---

### Post by mjm115 on 2006-06-14
Thanks a lot!

---

### Post by M@dMerC on 2006-06-15
this is the code i use for a win 98SE
```
#!/usr/bin/vmplayer

config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "Windows98SE.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "atapi-cdrom"
ide1:0.autodetect = "TRUE"

floppy0.startConnected = "False"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows 98SE"
guestOS = "win98"
nvram = "Windows98SE.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 50 59 9c df 58 f1-c0 44 ea 5d 73 e6 6c 18"
uuid.bios = "56 4d 50 59 9c df 58 f1-c0 44 ea 5d 73 e6 6c 18"
ethernet0.generatedAddress = "00:0c:29:e6:6c:18"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "Windows98SE.vmss"
tools.remindInstall = "TRUE"
```
that will make it to boot from a cd-rom

---

### Post by Brokenrgv on 2006-06-15
just installed VM server and put xp in it but havnt got any usb support for things like printers and mp3 players, i think linux still has these bound to itself and is stopping xp using them any way that i could use these devices in a virtual xp enviroment? anyhelp much appreciated.

---

### Post by M@dMerC on 2006-06-16
apparently if you change the usb.present value in the .vmx file to false instead of true that will let windows detect the usb and will allow you to use usb with it hope this helps

---

### Post by horatzica on 2006-06-16
You can also create a virtual machine (the .vmx file) at [http://www.easyvmx.com/](http://www.easyvmx.com/)

---

### Post by Brokenrgv on 2006-06-16
where is this .vmx file? in vmware folder ?

---

### Post by Roderik on 2006-06-16
If you want to enjoy any sort of good perfomance in your guest OS, you have to install the vmware-tools. Player doesn't have this option, but here is waht i found on the following website: [http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html](http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html)

> Installing VMware Tools with VMware Player
As other sites have demonstrated, it is possible to create a VMware disk image using free tools and install a full-fledged virtual operating system using the free VMware Player. However, VMware Player does not provide VMware Tools, a set of programs that considerably improve VMware performance.

The following procedure shows how to extract and install the VMware Tools image from the VMware Workstation "tarball" (.tar.gz file). In this example, my guest system is Windows XP Professional, and my host system is Fedora Core 4.

1. Download the latest "Archived Version" of VMware Workstation in ".tar.gz" format at [http://www.vmware.com/download/ws/](http://www.vmware.com/download/ws/). You do not need to be registered nor have a VMware Workstation license key to download this version.

Example:
wget [http://download3.vmware.com/software/wkst/VMware-workstation-5.5.0-18463.tar.gz](http://download3.vmware.com/software/wkst/VMware-workstation-5.5.0-18463.tar.gz)

2. Locate and extract the windows.iso VMware Tools image from the tarball.

Locate the windows.iso file (example):
$ tar ztvf VMware-workstation-5.5.0-18463.tar.gz | grep windows.iso
vmware-distrib/lib/isoimages/windows.iso

Extract the windows.iso file (example):
$ tar zxvf VMware-workstation-5.5.0-18463.tar.gz vmware-distrib/lib/isoimages/windows.iso

3. Mount the windows.iso file as a loopback file system, and either share the loopback file system with Samba, or copy the VMware Tools files to a location accessible by your guest system.

$ mkdir /tmp/vmware_tools
# mount -o loop vmware-distrib/lib/isoimages/windows.iso /tmp/vmware_tools

4. In your guest system, run setup.exe from the VMware Tools directory.

---

### Post by pellgarlic on 2006-06-22
FYI - vmware server beta is free for download - look at this thread: [http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209) for installation instructions. vmware player is excellent, but vmware server has built-in functions to create virtual machines, making the manual editing of the files unnecessary. it's a more complicated setup however - there is no package in the repos yet, so it needs to be compiled manually.

---

### Post by carverj on 2007-02-14
Am getting following error:-

```
Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.
```

---

### Post by stansaraczewski on 2007-04-13
My copy of Solaris 10 arrived yesterday and I am anxious to get started with VMplayer. This is a great thread, but it is showing me that the file that qemu creates may have to get tweaked a bit. Is there a sample .vmx file available for Ubuntu hosting a Solaris 10 installation ?

---

### Post by digg1980 on 2009-09-09
> **heikkijh said:**
> How about Win98 in VMware Player? What is needed in vmx-file for it?
I already have Player running in my Kubuntu 6.06 and qemu made win98.vmdk file.
I only need win98.vdx file or some advice how to build it.

Check out the article on building VMX files at: **[VMX Builder for VMware Player ]("http://www.virtualizationteam.com/virtualization-vmware/vmx-builder.html")**

In direct words it show you how to use VMX Builder to build the file. Check it out & hope it resolve your demand.

Enjoy,
Erick

---

