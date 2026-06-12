---
title: "Kernel Compilation Script"
date: 2006-11-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Brando569 on 2006-11-18
a little while ago i created a shell script that would do everything involved in building a custom kernel automatically except select the modules u wanted and didnt want, but i had to change it to reflect the kernel and patches i was using and that got annoying after awhile. so i modded it a little and heres the final product for all of you to enjoy. feel free to mod it some more i could care less ;) 

echo "what kernel version are you using? linux-2.6.what?"
read kernel_version

echo "what patch are you using? patch-2.6.[kernel version].what? 
read patch_version

##get necessary stuff from the repositories
sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget 

#copying kernel source and patches
cd /usr/src
sudo cp ~/kernel/kernels/linux-2.6.$kernel_version.tar.bz2 /usr/src
sudo cp ~/kernel/patches/patch-2.6.$kernel_version-$patch_version.bz2 /usr/src

#extracting kernel
sudo tar -xvjf linux-2.6.$kernel_version.tar.bz2
sudo rm -rf linux && sudo ln -s /usr/src/linux-2.6.$kernel_version linux
cd linux

#patching kernel
sudo bzcat ../patch-2.6.$kernel_version-$patch_version.bz2 | patch -p1
sudo cp ~/kernel/speed_hacked.config .config

#making kernel
sudo make xconfig
sudo make-kpkg clean
sudo make-kpkg --initrd kernel_image kernel_headers

#installing kernel and headers
cd ..
sudo dpkg -i kernel-image-2.6.$kernel_version-$patch_version_10.00.Custom_i386.deb
sudo dpkg -i kernel-headers-2.6.$kernel_version-$patch_version_10.00.Custom_i386.deb

and these are the "speed hacks" ive used (i got them somewhere on this forum): U means unselect and S means select

Loadable Module Support:

  U: Module Versioning Support
  U: Source checksum for all modules
--------------------------------------------------------------------
Block Layer:

  U: Large Block Devices (Uncheck all if possible)
--------------------------------------------------------------------
/IO Schedulers:

  U: Anticipatory I/O Schedulers
  U: Deadline I/O Schedulers
---------------------------------------------------------------------
Processor type and features:

  U: Symmetric processing support 
  S: Voluntary Kernel Preemption (Desktop) (Under Preemption Model)
  S: Local APIC support on uniprocessors
  S: IO-APCI support on uniprocessors (Under Local APIC support)
  S: Off (Under High Memory support if you have under 1 gig of ram)
  S: Sparse Memory 
  S: Use register arguements
  S: 1000hz (Under Timer Frequency)
--------------------------------------------------------------------
/Firmware Drivers:

  U: Anything that you don't need.

--------------------------------------------------------------------
Network:

  U: Anything/Everything in Amateur Radio, IrDA, and Bluetooth
--------------------------------------------------------------------
/Raid and LVM

  U: Unselect if you do not need it.
--------------------------------------------------------------------
/I2O support:

  U: Unselect if you do not need it. Most people do not.
--------------------------------------------------------------------
Network Device support: 

  U: EQL support
  U: Universial TUN/TAP device driver support
  U: FDDI Driver support
  U: HIPPI driver support
  U: SLIP (serial line) support
  U: Traffic Shaper
  U: Network console loggin support
---------------------------------------------------------------------
/ARCnet support:

  U: Unselect if you do not require/need it.
---------------------------------------------------------------------
/Ethernet Support (1000 MB):

  U: Uselect the cards that you don't have.
---------------------------------------------------------------------
/Ethernet Support (10000 MB):

  U: Unselect what you do not need.
---------------------------------------------------------------------
/Token Ring Devices:

  U: Unselect if you are not connected to a Token ring network.
---------------------------------------------------------------------
/WAN interfaces support:

  U: Unselect the some cards/the whole thing if you do not need it.
---------------------------------------------------------------------
ISDN subsystem:

  U: ISDN support (If you do not require it)
---------------------------------------------------------------------
Input device support:

  U: Touchscreen interface
  U Touchscreens (Under the TouchScreens subcatergory)
---------------------------------------------------------------------
Character Devices:

  U: Any video cards that you do not need.
---------------------------------------------------------------------
/Watchdog cards:

  U: Watch Dog Timer support
---------------------------------------------------------------------
Misc Devices:

  U: Device driver for IBM/RSA service drivers
---------------------------------------------------------------------
Video Capture Adapters:

  U: Unselect anything that you don't need.
---------------------------------------------------------------------
/Radio Adapters:

  U: Unselect anything that you don't need.
---------------------------------------------------------------------
/Digital Video Broadcasting Devices:

  U: DVB for Linux
---------------------------------------------------------------------
Graphics support:

  U: Unselect any graphics cards that you don't have.
---------------------------------------------------------------------
/Logo Configuration:

  S: Bootup Logo (and anything under it)
---------------------------------------------------------------------
File systems:

  U: Unselect any file systems that you are NOT going to use. 
----------------------------------------------------------------------
/DOS/FAT/NT Filesystems:

  S: NTFS write support
----------------------------------------------------------------------
/Network File Systems:

  U: NFS file system support
  U: NFS server support
  U: NCP file system support
  U: Coda file system support
  U: Andrew file system support
  U: Plan 9 resource sharing support
-----------------------------------------------------------------------
/Partition Types:

  U: Advanced partition selection
-----------------------------------------------------------------------
/Native Language Support:

  U: Unselect all but your native language:
  S: Codepage 437 (United States. Canada), ACII (United States), NLS UTF-8 (select these for the us language)
-----------------------------------------------------------------------
Instrumentation Support:

  U: Profiling Support
------------------------------------------------------------------------
Kernel Hacking:

  U: Show timing information on printks
  U: Magic SysRq Key
  U: Kernel Hacking
  U: Debug Filesustem
  U: Compile the kernel with frame unwind information

---

### Post by xabbott on 2006-11-24
thanks

---

