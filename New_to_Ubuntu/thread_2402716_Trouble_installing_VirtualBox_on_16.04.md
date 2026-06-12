---
title: "Trouble installing VirtualBox on 16.04"
date: 2018-10-03
forum: New to Ubuntu
---

### Post by vysero on 2018-10-03
I was following a guide to install VirtualBox: [https://websiteforstudents.com/install-virtualbox-latest-on-ubuntu-16-04-lts-17-04-17-10/](https://websiteforstudents.com/install-virtualbox-latest-on-ubuntu-16-04-lts-17-04-17-10/)

On the last step my computer errors:

```
rob@linux038:~$ sudo apt-get install virtualbox-5.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 virtualbox-5.2 : Recommends: libsdl-ttf2.0-0 but it is not going to be installed
                  Conflicts: virtualbox-5.2:i386 but 5.2.18-124319~Ubuntu~xenial is to be installed
 virtualbox-5.2:i386 : Depends: libgl1-mesa-glx:i386 but it is not going to be installed or
                                libgl1:i386
                       Recommends: libsdl-ttf2.0-0:i386 but it is not going to be installed
                       Recommends: linux-headers-generic:i386 but it is not going to be installed or
                                   linux-headers-generic-pae:i386 but it is not installable or
                                   linux-headers-686-pae:i386 but it is not installable or
                                   linux-headers-amd64:i386 but it is not installable or
                                   linux-headers-2.6-686:i386 but it is not installable or
                                   linux-headers-2.6-amd64:i386 but it is not installable or
                                   linux-headers:i386
                       Recommends: linux-image:i386
                       Recommends: gcc:i386 but it is not going to be installed
                       Recommends: binutils:i386 but it is not going to be installed
                       Recommends: pdf-viewer:i386
                       Recommends: libgl1:i386
                       Conflicts: virtualbox-5.2 but 5.2.18-124319~Ubuntu~xenial is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

So I ran that and when I started the virtualbox I get:

WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (4.15.0-36-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /sbin/vboxconfig

         You will not be able to start VMs until this problem is fixed.


Not sure what's wrong here...

---

### Post by deadflowr on 2018-10-03
What do
```
sudo apt update
sudo apt install -f
```
do and show?

---

### Post by vysero on 2018-10-03
```
rob@linux038:~$ sudo apt update
[sudo] password for murchrob: 
Hit:1 [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                                             
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]                            
Hit:4 [http://ppa.launchpad.net/dominik-stadler/dsta-xenial-ppa/ubuntu](http://ppa.launchpad.net/dominik-stadler/dsta-xenial-ppa/ubuntu) xenial InRelease
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease [107 kB]                                   
Hit:6 [http://ppa.launchpad.net/openjdk-r/ppa/ubuntu](http://ppa.launchpad.net/openjdk-r/ppa/ubuntu) xenial InRelease              
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease [107 kB]                                    
Hit:8 [http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu](http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu) xenial InRelease                               
Hit:9 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease       
Fetched 323 kB in 1s (242 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
8 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Translations (contrib/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Translations (contrib/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/virtualbox.list:1
rob@linux038:~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libreadline5 linux-headers-4.15.0-33 linux-headers-4.15.0-33-generic linux-image-4.15.0-33-generic
  linux-modules-4.15.0-33-generic linux-modules-extra-4.15.0-33-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
```

---

### Post by deadflowr on 2018-10-03
Now what does
```
apt list --upgradable 
```
show?

---

### Post by vysero on 2018-10-03
```
rob@linux038:~$ apt list --upgradable
Listing... Done
firefox/xenial-updates,xenial-security 62.0.3+build1-0ubuntu0.16.04.2 amd64 [upgradable from: 62.0+build2-0ubuntu0.16.04.5]
firefox-locale-en/xenial-updates,xenial-security 62.0.3+build1-0ubuntu0.16.04.2 amd64 [upgradable from: 62.0+build2-0ubuntu0.16.04.5]
liblouis-data/xenial-updates,xenial-updates,xenial-security,xenial-security 2.6.4-2ubuntu0.4 all [upgradable from: 2.6.4-2ubuntu0.3]
liblouis9/xenial-updates,xenial-security 2.6.4-2ubuntu0.4 amd64 [upgradable from: 2.6.4-2ubuntu0.3]
python3-louis/xenial-updates,xenial-updates,xenial-security,xenial-security 2.6.4-2ubuntu0.4 all [upgradable from: 2.6.4-2ubuntu0.3]
python3-update-manager/xenial-updates,xenial-updates 1:16.04.14 all [upgradable from: 1:16.04.13]
update-manager/xenial-updates,xenial-updates 1:16.04.14 all [upgradable from: 1:16.04.13]
update-manager-core/xenial-updates,xenial-updates 1:16.04.14 all [upgradable from: 1:16.04.13]

```

---

### Post by deadflowr on 2018-10-03
And if you run
```
sudo apt upgrade
```
also, double check virtualbox is indeed properly installed with
```
dpkg -i | grep virtualbox
```
The first command will at least bring the system to full update status, in line with Ubuntu as a whole.
(Always best to try to figure things out if the system is fully up-to-date)

The second command will output what the current status is for any installed packages on your system.
(Piping the command thought the the grep command will output only packages with the virtualbox name)

---

### Post by vysero on 2018-10-03
Sorry it took me a minuet to get back to you I went to lunch.

```
rob@linux038:~$ sudo apt upgrade
[sudo] password for rob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libreadline5 linux-headers-4.15.0-33 linux-headers-4.15.0-33-generic linux-image-4.15.0-33-generic
  linux-modules-4.15.0-33-generic linux-modules-extra-4.15.0-33-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  firefox firefox-locale-en liblouis-data liblouis9 python3-louis python3-update-manager update-manager
  update-manager-core
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.3 MB of archives.
After this operation, 32.8 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 python3-update-manager all 1:16.04.14 [33.1 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 update-manager-core all 1:16.04.14 [5,504 B]
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 update-manager all 1:16.04.14 [543 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 firefox amd64 62.0.3+build1-0ubuntu0.16.04.2 [44.7 MB]
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 firefox-locale-en amd64 62.0.3+build1-0ubuntu0.16.04.2 [942 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 liblouis-data all 2.6.4-2ubuntu0.4 [1,077 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 liblouis9 amd64 2.6.4-2ubuntu0.4 [59.6 kB]  
Get:8 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 python3-louis all 2.6.4-2ubuntu0.4 [7,328 B]
Fetched 47.3 MB in 34s (1,360 kB/s)                                                                          
(Reading database ... 421814 files and directories currently installed.)
Preparing to unpack .../python3-update-manager_1%3a16.04.14_all.deb ...
Unpacking python3-update-manager (1:16.04.14) over (1:16.04.13) ...
Preparing to unpack .../update-manager-core_1%3a16.04.14_all.deb ...
Unpacking update-manager-core (1:16.04.14) over (1:16.04.13) ...
Preparing to unpack .../update-manager_1%3a16.04.14_all.deb ...
Unpacking update-manager (1:16.04.14) over (1:16.04.13) ...
Preparing to unpack .../firefox_62.0.3+build1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking firefox (62.0.3+build1-0ubuntu0.16.04.2) over (62.0+build2-0ubuntu0.16.04.5) ...
Preparing to unpack .../firefox-locale-en_62.0.3+build1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking firefox-locale-en (62.0.3+build1-0ubuntu0.16.04.2) over (62.0+build2-0ubuntu0.16.04.5) ...
Preparing to unpack .../liblouis-data_2.6.4-2ubuntu0.4_all.deb ...
Unpacking liblouis-data (2.6.4-2ubuntu0.4) over (2.6.4-2ubuntu0.3) ...
Preparing to unpack .../liblouis9_2.6.4-2ubuntu0.4_amd64.deb ...
Unpacking liblouis9:amd64 (2.6.4-2ubuntu0.4) over (2.6.4-2ubuntu0.3) ...
Preparing to unpack .../python3-louis_2.6.4-2ubuntu0.4_all.deb ...
Unpacking python3-louis (2.6.4-2ubuntu0.4) over (2.6.4-2ubuntu0.3) ...
Processing triggers for libglib2.0-0:i386 (2.48.2-0ubuntu4.1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.2-0ubuntu4.1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.2) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20180209-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1.1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Setting up python3-update-manager (1:16.04.14) ...
Setting up update-manager-core (1:16.04.14) ...
Setting up update-manager (1:16.04.14) ...
Setting up firefox (62.0.3+build1-0ubuntu0.16.04.2) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-locale-en (62.0.3+build1-0ubuntu0.16.04.2) ...
Setting up liblouis-data (2.6.4-2ubuntu0.4) ...
Setting up liblouis9:amd64 (2.6.4-2ubuntu0.4) ...
Setting up python3-louis (2.6.4-2ubuntu0.4) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...

```

For the second command (as is) it asked me for sudo privileges:

```
rob@linux038:~$ sudo dpkg -i | grep virtualbox
dpkg: error: --install needs at least one package archive file argument

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !

```

should I not be using -i?

---

### Post by deadflowr on 2018-10-03
No need for sudo, oh, yes -l (small L)
my bad. sorry.

---

### Post by vysero on 2018-10-03
```
rob@linux038:~$ dpkg -l | grep virtualbox
ii  unity-scope-virtualbox                                      0.1+13.10.20130723-0ubuntu1                  all          VirtualBox scope for Unity
ii  virtualbox-5.2:i386                                         5.2.18-124319~Ubuntu~xenial                  i386         Oracle VM VirtualBox

```

---

### Post by deadflowr on 2018-10-03
So far all looks fine
(though, any reason as to why you are running 32-bit instead of 64-bit?
My mind drifted to that)

Anyway, have you run the suggested command again (or yet)?
```
sudo /sbin/vboxconfig
```

---

### Post by vysero on 2018-10-03
I was not aware that I was running 32-bit tbh. I did run the suggested command but it just sort of loops:

```
rob@linux038:~$ sudo /sbin/vboxconfig
[sudo] password for murchrob: 
vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Starting VirtualBox services.
vboxdrv.sh: Building VirtualBox kernel modules.
vboxdrv.sh: failed: Look at /var/log/vbox-setup.log to find out what went wrong.

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.

```

The log file:

```
Building the main VirtualBox module.
Error building the module:
make V=1 CONFIG_MODULE_SIG= -C /lib/modules/4.15.0-36-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 -j8 modules
make[1]: warning: -jN forced in submake: disabling jobserver mode.
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f ./scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.8/include  -I./arch/x86/include -I./arch/x86/include/generated  -I./include -I./arch/x86/include/uapi -I./arch/x86/include/generated/uapi -I./include/uapi -I./include/generated/uapi -include ./include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fshort-wchar -Werror-implicit-function-declaration -Wno-format-security -std=gnu89 -fno-PIE -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -m64 -falign-jumps=1 -falign-loops=1 -mno-80387 -mno-fp-ret-in-387 -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_SSSE3=1 -DCONFIG_AS_CRC32=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mindirect-branch=thunk-extern -mindirect-branch-register -DRETPOLINE -fno-delete-null-pointer-checks -O2 -Wno-maybe-uninitialized --param=allow-store-data-races=0 -DCC_HAVE_ASM_GOTO -Wframe-larger-than=1024 -fstack-protector-strong -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -include /tmp/vbox.0/include/VBox/SUPDrvMangling.h -fno-omit-frame-pointer -fno-pie -I/lib/modules/4.15.0-36-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DVBOX_WITH_HARDENING -DSUPDRV_WITH_RELEASE_LOGGER -Wno-declaration-after-statement -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_AMD64 -DVBOX_WITH_64_BITS_GUESTS  -DMODULE  -DKBUILD_BASENAME='"SUPDrv_linux"'  -DKBUILD_MODNAME='"vboxdrv"' -c -o /tmp/vbox.0/linux/SUPDrv-linux.o /tmp/vbox.0/linux/SUPDrv-linux.c
gcc: error: unrecognized command line option &#8216;-fstack-protector-strong&#8217;
scripts/Makefile.build:332: recipe for target '/tmp/vbox.0/linux/SUPDrv-linux.o' failed
make[2]: *** [/tmp/vbox.0/linux/SUPDrv-linux.o] Error 1
Makefile:1551: recipe for target '_module_/tmp/vbox.0' failed
make[1]: *** [_module_/tmp/vbox.0] Error 2
/tmp/vbox.0/Makefile.include.footer:101: recipe for target 'vboxdrv' failed
make: *** [vboxdrv] Error 2
```

---

### Post by deadflowr on 2018-10-03
Hmm, gcc error huh.

Maybe, just maybe, try reinstalling virtualbox again and see if that builds correctly.
Long shot, probably:
```
sudo apt-get install --reinstall virtualbox-5.2
```

---

### Post by vysero on 2018-10-03
Well I gave it a shot but still got the same error. Do you think installing as a PPA would work? Something like: [https://linuxpropaganda.wordpress.com/2016/07/07/install-virtualbox-from-ppa-in-xubuntu-16-04/](https://linuxpropaganda.wordpress.com/2016/07/07/install-virtualbox-from-ppa-in-xubuntu-16-04/)

What's the best way for me to clean the currently installed version?

I don't think its necessary to have virtualbox to get a virtual machine running. I have never used one before and this was the most suggested method.

Edit:

I do have gcc 4.8, 5, 6, 7, and 8 installed maybe I could force it to use a different version of gcc?

---

### Post by vysero on 2018-10-03
Yeah that did it lol apparently I forgot to change gcc from 4 to 8. Once I did that and I re-installed the app it worked!

---

### Post by fjgaude on 2018-10-10
Hello deadflowr!

I'm have the same issue as the title and have followed you help to now where the thread stops. (Now I see it extended to page 2!)

I done all you have suggested already and all is updated. When I run VirtusalBox I get this error msg:

```
The VM session was closed before any attempt to power it on.
```

When I run this:

```
root@flash:~# /sbin/vboxconfig
```

```
bash: /sbin/vboxconfig: No such file or directory
```

Please, do you have any suggestions?

---

### Post by fjgaude on 2018-10-10
Hello deadflowr!

I followed and performed all the suggestions given. I have a fully updated system.

When I load virtualbox with a WinXP I get this:

```
The VM session was closed before any attempt to power it on.
```

When I run this:

```
bash: /sbin/vboxconfig: No such file or directory
```

I've looked in /sbin and there is no vboxconfig. I did earlier the virtualbox-dkms install and ran it.

Do you have any suggestions, please. Thank you!

---

### Post by deadflowr on 2018-10-10
> The VM session was closed before any attempt to power it on.
I've only ever seen reference to this when someone has tried and failed to open a virtual machine.

Is this happening when you open virtualbox's machine manager interface?

If it happens with the former does this give you any hints:
[https://forums.virtualbox.org/viewtopic.php?f=2&t=86402]("https://forums.virtualbox.org/viewtopic.php?f=2&t=86402")

If it happens with the latter, I'm not sure where to go.
As I've never seen that error message being related to the virtualbox manager itself.
??

---

### Post by fjgaude on 2018-10-10
Thanks for returning!

VBox manager opens fine, QT version latest. The error occurs when I click to load the appliance. The manager shows no log. The system seems not to like WinXP which I've used on other boxes without issue.

What next... start and reload a new OS and then try to use this manager with the same WinXP?

---

### Post by deadflowr on 2018-10-10
What does the winxp state show?
(the state will show in the manager in the listing panel where the vms are listed, under the vm name usually with something like powered off or saved or running)

Logs can be found in the Virtualbox Vms's's(?) virtual-machine specific folders in your Home folder, usually somewhere  like Home > Virtualbox Vms > WinXP > logs.

---

### Post by fjgaude on 2018-10-10
It shows 'saved'. I took it from another running VBox on another drive.

Since the last post I've gone over the three drives I have on this one box, an Intel i7 CPU with 32 gigs of RAM. They each do about the same thing... they all say no 'vboxdrv'. And on checking it is true, no drv. I've run dkms but still same issures, even with a Win 10 appliance, 64-bit. WinXP is the only 32-bit thing I have.

---

### Post by deadflowr on 2018-10-10
Up on the top toolbar where it show New Settings Start there should be an option for Discard.
You highlight the vm and press discard and it should reset the vm to the powered off state.
(alternatively, right clicking on the vm should bring up a menu and a listing in there will be for Discard Saved State)

That should reset the vm to off and allow it to start normally.
Unfortunately this wipes any settings made during that saved state.

(it'll also most likely run a chkdsk on startup, since the vm losing that saved state status is like a power failure shutdown.
But it should still run normal after that)

Sadly, I do not know of any other way to fix it.

---

### Post by saytotarsach2018 on 2018-10-12
Thank you people, this thread was really helpful!

---

