---
title: "Qemu with: Bridged networking, kqemu accelorator, qemu-launcher."
date: 2005-09-18
forum: Outdated Tutorials &amp; Tips
---

### Post by zigford on 2005-09-18
[FONT=Arial][B][SIZE=5]Qemu with kqemu accelorator, tun networking, and qemu-launcher for Ubuntu.
Version 1.0 – Please leave comments.[/SIZE][/B]

[SIZE=4]**1  Introduction**[/SIZE]

[SIZE=3]A lot of information in this guide was borrowed from other helpful threads in the ubuntu forums, I will give credit where I can, but if I have lost the name of the original post then sorry, you can send me an email if it is you and I will update.[/SIZE]

[SIZE=4]**2  About this documentation**
[/SIZE]
[SIZE=3]Throughout this document commands that you have to type are shown in [COLOR=Red]red[/COLOR] and text that must be typed into a text file is shown in [COLOR=Green]green[/COLOR].

All text files have been edited with “vi” if you don't feel confident with vi, you can substiture it with “gedit” or “nano -w”[/SIZE]

[SIZE=4]**3  Downloading the packages**[/SIZE]
[SIZE=3]
If you already have qemu installed we need to remove it.

[COLOR=Red]  sudo apt-get remove qemu[/COLOR]

Make a source directory in your home folder.
[COLOR=Red]  cd
  mkdir src[/COLOR]

Go to [http://fabrice.bellard.free.fr/qemu/download.html](http://fabrice.bellard.free.fr/qemu/download.html) 

Download qemu source (At the time of writing I used qemu-0.7.2.tar.gz)
Download kqemu binary  (At the time of writing I used kqemu-0.7.2.tar.gz)

Save these downloaded files into your newly created src directory.

Install your kernel headers.
[COLOR=Red]  sudo apt-get install linux-headers-$(uname -r)[/COLOR]

Install building packages
[COLOR=Red]  sudo apt-get install libsdl1.2-dev
  sudo apt-get install zlib1g-dev
  sudo apt-get install checkinstall
  sudo apt-get build-dep qemu[/COLOR]

There are more packages to get, but we should get these later.[/SIZE]
  
[SIZE=4]**4  Extract and Build Qemu**[/SIZE]
[SIZE=3]
Extract qemu and kqemu

Make sure you substitute the x for your version number.
[COLOR=Red]cd $HOME/src
tar zxvf qemu-0.7.x.tar.gz
cd qemu-0.7.x
tar zxvf ../kqemu-0.7.x.tar.gz
sudo ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux-headers
cd qemu-0.7.x
[/COLOR]

Edit the configure file

[COLOR=Red]vi configure[/COLOR]

change this line:

kernel_path=""

To this

[COLOR=Green]kernel_path="/usr/src/linux-headers"[/COLOR]

After you save and quit, run:
[COLOR=Red]./configure[/COLOR]

You should see something similar to the following:

harrisj@brightstar:~/src/qemu-0.7.2$ ./configure
Install prefix    /usr/local
BIOS directory    /usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /home/harrisj/src/qemu-0.7.2
C compiler        gcc
Host C compiler   gcc
make              make
host CPU          i386
host big endian   no
target list       i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu mips-softmmu
gprof enabled     no
static build      no
SDL support       yes
SDL static link   yes
mingw32 support   no
Adlib support     no
FMOD support      no
kqemu support     yes

KQEMU Linux module configuration:
kernel sources    /usr/src/linux-headers
kbuild type       2.6
harrisj@brightstar:~/src/qemu-0.7.2$

If everything has gone as planned, you should have yes next to kqemu.

Now type

[COLOR=Red]make[/COLOR]
[/SIZE]
[SIZE=4]**5  Creating a Debian/Ubuntu package**[/SIZE]
[SIZE=3]
When you install a package from source there is usually no way to uninstall that package.  This can cause problems down the track when you want to upgrade a program, there is no way to uninstall the old package safely.

This is where “checkinstall” steps in.  Checkinstall creates a .deb package for you, which is easy to remove later.

Create the deb package.

[COLOR=Red]sudo checkinstall -D[/COLOR]

At this point checkinstall will ask you some questions.

1st question:  Answer = default y
2nd question:  Answer = Any description you like about qemu

You can safely leave the next menu alone and just press enter

Next, checkinstall will build the .deb package and install it.  For me and other checkinstall reports that it fails and asks if you want to view the output.

Do not worry about this.  Qemu did install successfully.
[/SIZE]
**[SIZE=4]6  Make the modules start on boot[/SIZE]**
[SIZE=3]
[COLOR=Red]sudo vi /etc/modules[/COLOR]

Add to the bottom:
[COLOR=Green]kqemu
tun[/COLOR]

Load them manually for now:
[COLOR=Red]sudo modprobe kqemu
sudo modprobe tun[/COLOR]
[/SIZE]
[SIZE=4]**7  Creating the network bridge**[/SIZE]
[SIZE=3]
This section is the hardest section but it brings great rewards.  If you want the virtual machine to be accessible by any other computer on the network this section is necessary.

Other wise you can use “user mode” networking and skip to “Section 10 – Qemu-launcher”

Install bridge utilities and user mode utilities

[COLOR=Red]sudo apt-get install bridge
sudo apt-get install uml-utilities[/COLOR]

A network bridge is a virtual network interface that contains one or more real/virtual interfaces.  Basically what this does is:

Create a bridge device
Add our eth0 (or other LAN device) to the bridge.
Modify security permissions to allow qemu to add a Virtual interface to the bridge.

This will allow your virtual ip address of your virtual pc to have a real ip address on your internal LAN.  Get it?

[B]*Note – During this section you will lose network connectivity.
**Note – Please substitute eth0 for the name of your LAN interface.[/B]

Create the bridge interface
[COLOR=RED]sudo brctl addbr br0[/COLOR]
Give the LAN interface a neutral IP
[COLOR=RED]sudo ifconfig eth0 0.0.0.0[/COLOR]
Add the LAN interface to the bridge
[COLOR=RED]sudo brctl addif br0 eth0[/COLOR]

Next we have to modify the file /etc/network/interfaces to allow your bridge to obtain an ip address automatically.  For static IP, check further below.

[COLOR=RED]sudo vi /etc/network/interfaces[/COLOR]

For Dynamic IP

Change these lines from this:

mapping hotplug
        script grep
        map eth0
To this:

[COLOR=GREEN]#mapping hotplug
#       script grep
#        map eth0[/COLOR]

From This:
# The primary network interface
iface eth0 inet dhcp

To this:

[COLOR=GREEN]# The primary network interface
auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 1
bridge_hello 1
bridge_stp off[/COLOR]

For Static IP

*Note – Substitute all IP addresses in bold for LAN address specific to your setup.

Change these lines from this:

mapping hotplug
        script grep
        map eth0
To this:

[COLOR=GREEN]#mapping hotplug
#        script grep
#        map eth0[/COLOR]

From This:

iface eth0 inet static 
address 192.168.1.2 
network 192.168.1.0 
netmask 255.255.255.0 
broadcast 192.168.1.255
gateway 192.168.1.1 

To This:

[COLOR=GREEN]auto br0
iface br0 inet static 
address 192.168.1.2 
network 192.168.1.0 
netmask 255.255.255.0 
broadcast 192.168.1.255 
gateway 192.168.1.1 
bridge_ports eth0 
bridge_fd 1 
bridge_hello 1 
bridge_stp off[/COLOR]

Now its time to restart the Network and restore network connectivty.

[COLOR=RED]sudo /etc/init.d/hotplug restart
sudo /etc/init.d/network restart[/COLOR]

To check if everything went well type ifconfig and check to see if the device br0 listed has an IP address.

Eg

br0     Link encap:Ethernet  HWaddr 00:0C:6E:74:41:62
          inet addr:192.168.0.77  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe74:4162/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3826802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3899124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2844083685 (2.6 GiB)  TX bytes:3126628692 (2.9 GiB)

Wow you just created a network bridge in linux Good Job!
[/SIZE]
[SIZE=4]**8  Setting up the Virtual interface and permissions.**[/SIZE]
[SIZE=3]
Now you have created a bridge and added your LAN interface, you can create the virtual interface for Qemu to use.

Create the tun interface – Be sure to substitute **“harrisj”** for your username.

[COLOR=RED]sudo tunctl -u 'harrisj' -t tun0
sudo chgrp admin /dev/net/tun
sudo chmod g+w /dev/net/tun

sudo vi /etc/qemu-ifup[/COLOR]

Change the file to the following:
[COLOR=GREEN]#!/bin/sh
echo "Executing /etc/qemu-ifup"
echo "Bringing up $1 for bridged mode..."
sudo /sbin/ifconfig $1 0.0.0.0 promisc up
echo "Adding $1 to br0..."
sudo /usr/sbin/brctl addif br0 $1
sleep 2[/COLOR]

[COLOR=RED]sudo chmod ug0+x /etc/qemu-if [/COLOR]

[SIZE=4]**9  Setting up sudoers.**[/SIZE]

Later on you will probably want to install qemu-launcher to launch your Virtual Machines from a nice graphical interface.  In the previous section we created/edited a script called /etc/qemu-ifup.  This script contains “sudo” commands.  Sudo commands do not like being run within a script when you don't run qemu from a terminal.  To fix this, we have to make sudo not require a password when issued certain commands.

[COLOR=RED]sudo visudo[/COLOR]
***Note - visudo will warn you when you make a syntax mistake in sudoers file.**

From this:
# Cmnd alias specification

To This:
[COLOR=GREEN]# Cmnd alias specification
Cmnd_Alias      QEMU=/sbin/ifconfig,/usr/sbin/brctl[/COLOR]

And From this:
# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

To This:

[COLOR=GREEN]# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
%admin  ALL=NOPASSWD:QEMU[/COLOR]

Save by pressing “Control x”, y

If visudo exits cleanly then all is well.
Restart sudo

[COLOR=RED]sudo init.d/sudo restart[/COLOR]

To test your sudo modifications do the following:

[COLOR=RED]sudo -K
sudo ifconfig[/COLOR]

If you were not requested to type a password on the second command, then you have success.
[/SIZE]
[SIZE=4]**10  Qemu Launcher – You are almost there.**[/SIZE]
[SIZE=3]
I discovered that if you launch a qemu vm from a terminal and then close that terminal my qemu vm disappeard.  Not happy Jan.

There is a great little gtk2 application out there called qemu-launcher.  It has some incompatibility issues with the latest version of qemu, but I worked out a hack around it.

Install qemu-launcher

**Note - Erik Meitner Wrote this little gem.**
[COLOR=RED]
sudo vi /etc/apt/sources.list[/COLOR]

Add
[COLOR=GREEN]deb [http://emeitner.f2o.org/debian/](http://emeitner.f2o.org/debian/) ./[/COLOR]

[COLOR=RED]sudo apt-get update
sudo apt-get install qemu-launcher[/COLOR]

Note – At the time of writing qemu-launcher was at version 1.3.2.  If you obtain a newer version you may not need to make the following changes.

For some reason qemu-launcher-1.3.2 gives a command line option –keyboard, which is now obsolete.

[COLOR=RED]sudo vi /usr/bin/qemu-launcher[/COLOR]

In this file, search for every instance of **“keyboard”** And put a [COLOR=GREEN]#[/COLOR] at the front of every line.

For this make sure you comment out the entire section.

[COLOR=GREEN]#       if( $config->{'keyboard'}  ) {
#               push @parts,'-keyboard';
#               push @parts,lc($config->{'keyboard'});
#       }[/COLOR]

Launch qemu-launcher
Application=>System Tools=>Qemu Launcher
[/SIZE]
[SIZE=4]**11  Using qemu-launcher**[/SIZE]
[SIZE=3]
Qemu-launcher is fairly straight forward.  Once loaded:

Name:  ie [COLOR=Green]“WindowsXP”[/COLOR]  Change this to create a new VM Profile  (This is all your settings for a particular VM

Boot disk: If you need to boot from a cdrom (Install Disk), change the “Boot Disk” drop down box to [COLOR=Green]“cdrom”[/COLOR]

Floppy A:  Who even uses these anymore?

IDE disk 0: If this is a new VM you can create a new Virtual Hard disk by clicking “Create Image” next to the corresponding IDE disk.  If you don't know what to choose it is best to use the default.

CDROM:  The first cdrom device is /dev/cdrom

RAM size:  If you have a gig of ram, its pretty safe to allocate up to 512mb.  For windowsXP you should not have less than 128mb

“Network” Tab

If you performed steps 6,7 and 8 then select “Tun/Tap”.  There is no need to specify a script as we have already set up the default script.

If you skipped steps 6,7 and 8, you can choose “User mode”  This option will give you network connectivity, but you will not be able to access the VM from other devices on your LAN.

“Launcher Setings”

“Default data directory” [COLOR=Green]$HOME/qemu-dir[/COLOR]	#You can create a dir for this.

“Path to Qemu” =[COLOR=Green] /usr/local/bin/qemu[/COLOR]
[/SIZE][SIZE=4]
**12 Credits and why**
[/SIZE]
[SIZE=3]Over my years of stuffing around with linux, I have read hundreds of howtos and learnt heaps.  The community has given a lot to me and I thought it about time to give some back.  This is my first guide.  I know there are other guides around for qemu (Thanks, they helped me write this one)  But I couldn't find anything that gave me a bridged network.  So thats the main focus of this.  Please leave comments.

Thanks to:
Lunde, for his handy ubuntu guide

A fair chunk of the proceedure comes from Lunde.  I hope he doesn't get mad that I used it.

There were some debian specific guides about Bridgeing networks in Linux, and I can't remember where/who made them.  The bridge-utils sourceforge site was helpful

[http://bridge.sourceforge.net/howto.html](http://bridge.sourceforge.net/howto.html)

I have tested this setup by installing
Windows XP with SP2
Ubuntu Hoary

I have also tested this guide on a brand new copy of Ubuntu.  Worked like a charm.  Within a VM btw.

Cheers
Jesse Harris
[/SIZE][/FONT]

---

### Post by pjstadig on 2005-10-21
Thanks, Jesse, for the detailed HOWTO. I followed the instructions and everything was fine until the make. My output of ./configure was exactly the same as yours, but make died with

```
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -mpreferred-stack-boundary=2 -falign-functions=0 -fno-gcse -fno-reorder-blocks -fno-optimize-sibling-calls -I. -I/home/paul/src/qemu-0.7.2/target-i386 -I/home/paul/src/qemu-0.7.2 -I/home/paul/src/qemu-0.7.2/linux-user -I/home/paul/src/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/paul/src/qemu-0.7.2/fpu -I/home/paul/src/qemu-0.7.2/slirp -c -o op.o /home/paul/src/qemu-0.7.2/target-i386/op.c
/home/paul/src/qemu-0.7.2/target-i386/ops_sse.h: In function ‘op_pshufw_mmx’:
/home/paul/src/qemu-0.7.2/target-i386/ops_sse.h:574: error: unable to find a register to spill in class ‘GENERAL_REGS’
/home/paul/src/qemu-0.7.2/target-i386/ops_sse.h:574: error: this is the insn:
(insn:HI 18 17 19 0 /home/paul/src/qemu-0.7.2/target-i386/ops_sse.h:569 (set (strict_low_part (subreg:HI (reg/v:DI 63 [ r ]) 0))
        (mem/s/j:HI (plus:SI (mult:SI (reg:SI 64)
                    (const_int 2 [0x2]))
                (reg/v/f:SI 59 [ s ])) [0 <variable>._w S2 A16])) 52 {*movstricthi_1} (insn_list:REG_DEP_TRUE 16 (insn_list:REG_DEP_TRUE 12 (insn_list:REG_DEP_TRUE 53 (nil))))
    (expr_list:REG_DEAD (reg:SI 64)
        (nil)))
/home/paul/src/qemu-0.7.2/target-i386/ops_sse.h:574: confused by earlier errors, bailing out
make[1]: *** [op.o] Error 1
make[1]: Leaving directory `/home/paul/src/qemu-0.7.2/i386-user'
make: *** [all] Error 1

```

Any suggestions?

By the way, in the extraction block I think the last "cd qemu-0.7.x" is a typo, since we should already be in the qemu-0.7.x dir.

Thanks again for the HOWTO.

Paul

---

### Post by pjstadig on 2005-10-21
I found a HOWTO in the wiki [https://wiki.ubuntu.com/WindowsXPUnderQemuHowTo]("https://wiki.ubuntu.com/WindowsXPUnderQemuHowTo") and it mentions setting the target list as a parameter to the configure. I also noticed that my configure output wasn't exactly the same as yours. configure was probing and detecting the linux headers elsewhere, so I figured maybe that was making a difference. So I tried 

```
./configure --target-list=i386-softmmu --kernel-path=/usr/src/linux-headers
```

but make still died trying to compile op.c. Then I tried to follow the instructions in the wiki and download the latest code from CVS, but I still got the same problem trying to compile op.c.

Too bad, I'd like to see what kind of performance the accelerator gets.

BTW, I'm using breezy, qemu and kqemu 0.7.2 and linux 2.6.12-9-386.


Paul

---

### Post by cron0 on 2005-10-21
[QUOTE=pjstadig]Thanks, Jesse, for the detailed HOWTO. I followed the instructions and everything was fine until the make. My output of ./configure was exactly the same as yours, but make died with

```
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -mpreferred-stack-boundary=2 -falign-functions=0 -fno-gcse -fno-reorder-blocks -fno-optimize-sibling-calls -I. -I/home/paul/src/qemu-0.7.2/target-i386 -I/home/paul/src/qemu-0.7.2 -I/home/paul/src/qemu-0.7.2/linux-user -I/home/paul/src/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/paul/src/qemu-0.7.2/fpu -I/home/paul/src/qemu-0.7.2/slirp -c -o op.o /home/paul/src/qemu-0.7.2/target-i386/op.c
/home/paul/src/qemu-0.7.2/target-i386/ops_sse.h: In function ‘op_pshufw_mmx’:
/home/paul/src/qemu-0.7.2/target-i386/ops_sse.h:574: error: unable to find a register to spill in class ‘GENERAL_REGS’
/home/paul/src/qemu-0.7.2/target-i386/ops_sse.h:574: error: this is the insn:
(insn:HI 18 17 19 0 /home/paul/src/qemu-0.7.2/target-i386/ops_sse.h:569 (set (strict_low_part (subreg:HI (reg/v:DI 63 [ r ]) 0))
        (mem/s/j:HI (plus:SI (mult:SI (reg:SI 64)
                    (const_int 2 [0x2]))
                (reg/v/f:SI 59 [ s ])) [0 <variable>._w S2 A16])) 52 {*movstricthi_1} (insn_list:REG_DEP_TRUE 16 (insn_list:REG_DEP_TRUE 12 (insn_list:REG_DEP_TRUE 53 (nil))))
    (expr_list:REG_DEAD (reg:SI 64)
        (nil)))
/home/paul/src/qemu-0.7.2/target-i386/ops_sse.h:574: confused by earlier errors, bailing out
make[1]: *** [op.o] Error 1
make[1]: Leaving directory `/home/paul/src/qemu-0.7.2/i386-user'
make: *** [all] Error 1

```

Any suggestions?

By the way, in the extraction block I think the last "cd qemu-0.7.x" is a typo, since we should already be in the qemu-0.7.x dir.

Thanks again for the HOWTO.

Paul[/QUOTE]

Same error here too.... kernel 2.6.12-8-686-smp

Any ideas?

cron0

---

### Post by cron0 on 2005-10-21
Found it!
Edit the 'configure' file and change these:
> cc="gcc"
host_cc="gcc"

to

> cc="gcc-3.4"
host_cc="gcc-3.4"

Good luck! :-)

---

### Post by pjstadig on 2005-10-21
Yeah, thanks, cron0.  I came to the same conclusion myself. Here is my final config command

```
./configure --target-list=i386-softmmu --cc=gcc-3.4 --host-cc=gcc-3.4

```

I got qemu compiled and running with the accelerator, but I'm trying to figure out if it helps at all. I booted from the Ubuntu Live CD and it was still pretty slow. I don't know what I should expect. It would be nice to have a really fast F/OSS virtual machine to run Windows, and qemu is certainly a good start, but it looks like VMWare is still faster. Unless I'm not configuring something right. I'll keep playing with it...


Paul

---

### Post by kotatsu on 2005-10-22
Thanks a lot for the HOWTO - rather than spending the day trying to figure out how to get it up and running, I spent the day playing with Qemu itself. Very helpful guide.

My SuSE Live DVD is finished downloading, so I'm off to play with a new distro. =)

pjstadig:
The Hoary Live CD I tried was slow, but the Hoary installation to disk I did ran much more acceptably. You might try that instead.

---

### Post by 23meg on 2005-10-28
Anyone tried these instructions in Breezy?

---

### Post by Stealth on 2005-11-02
Using Breezy, here are some things that were errors in the main post:

**(1) CONFIGURE FILE**
like cron said:

in the configure file change:

> cc="gcc"
host_cc="gcc"

to

> cc="gcc-3.4"
host_cc="gcc-3.4"


**(2) BRIDGE**

Nothing huge, just that its really:

> sudo apt-get install bridge-utils

**(3) CHMOD COMMAND**

This command:
> sudo chmod ug0+x /etc/qemu-if 

should really be:
> sudo chmod ugo+x /etc/qemu-ifup 

And things I've found are that my network is now broke because of the briding thing. I keep getting disconnected and up again, but when its up it doesn't even work...I'm using a static IP.

And that qemu-launcher is buggy, freezes a lot with floating errors whenever I'm in a folder/file selection menu and then click "OK"

Other than that QEMU does work, but I gotta fix this interfaces thing :(

---

### Post by kakashi on 2005-11-02
could somebody tell me  where the .deb made checkinstall is stored.
can i i use it again when i reinstall ubuntu without installing all the header and compiling.??
thanks for your help

---

### Post by angrylittleman on 2005-11-12
I have followed this in breezy and it works well.  I having problems with qemu laucher though.  It is not appearing in my menu at all.  when I try to launch from the terminal, I get:

qemu: could not open hard disk image 'launcher'

What am I doing wrong?  I could not get the qemu-launcher repo to work, so I downloaded the newest package (well the only package) and installed it with dpkg -i.  Any suggestions?  I even got networking to work like a champ.  A gui for this beast would just be great.

Thanks!
ALM

---

### Post by theToolman on 2005-11-14
Breezy users:  implicit in the need to update the "configure" file to gcc-3.4 is the need to install gcc-3.4 ! i.e.

sudo apt-get install gcc-3.4

Took me a few minutes to realise...

---

### Post by Xappe on 2005-12-05
hmm, questions about network bridge:

I'm using qemu (running win2k) on the same box as my router (shorewall/iptables) currently using a two interface setup (eth0 = internet, eth1 = local network gateway). 

Is there a way to set up the tun0 to use my eth1 as gateway and route internet traffic and local network traffic to qemu using shorewall? (or use the tun0 as a second local area gateway)

I'm quite a newbie when it comes to advanced network setups, but I'm learning...

---

### Post by rootnt on 2006-02-05
hi dear friends
I installed qemu with kqemu in my breezy distro
How I can mount my physical hard drive (hdd) in windows2000 with qemu?
Thanks

---

### Post by simone.brunozzi on 2006-02-16
I tried to install qemu following your instructions, however, when typing "make", after some crunching, I got the following error lines:

```
make -C kqemu
make[1]: Entering directory `/home/simone/src/qemu-0.7.2/kqemu'
make -C /usr/src/linux-headers M=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-15'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-15/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/simone/src/qemu-0.7.2/kqemu/kqemu-linux.o
In file included from /home/simone/src/qemu-0.7.2/kqemu/kqemu-linux.c:9:
include/linux/mm.h: In function ‘lowmem_page_address’:
include/linux/mm.h:512: error: ‘PAGE_OFFSET_RAW’ undeclared (first use in this function)
include/linux/mm.h:512: error: (Each undeclared identifier is reported only once
include/linux/mm.h:512: error: for each function it appears in.)
In file included from /home/simone/src/qemu-0.7.2/kqemu/kqemu-linux.c:18:
include/asm/io.h: In function ‘virt_to_phys’:
include/asm/io.h:78: error: ‘PAGE_OFFSET_RAW’ undeclared (first use in this function)
include/asm/io.h: In function ‘phys_to_virt’:
include/asm/io.h:96: error: ‘PAGE_OFFSET_RAW’ undeclared (first use in this function)
/home/simone/src/qemu-0.7.2/kqemu/kqemu-linux.c: In function ‘kqemu_alloc_zeroed_page’:
/home/simone/src/qemu-0.7.2/kqemu/kqemu-linux.c:111: error: ‘PAGE_OFFSET_RAW’ undeclared (first use in this function)
make[3]: *** [/home/simone/src/qemu-0.7.2/kqemu/kqemu-linux.o] Error 1
make[2]: *** [_module_/home/simone/src/qemu-0.7.2/kqemu] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-15'
make[1]: *** [kqemu.ko] Error 2
make[1]: Leaving directory `/home/simone/src/qemu-0.7.2/kqemu'
make: *** [all] Error 2
```

Do you have any idea on how to avoid those errors???

Thanks!!

---

### Post by simone.brunozzi on 2006-02-17
Hi,
I solved the problem with "make" changing the link (I added -386 at the end of the name, it worked), but now I have another problem making the package:

```

simone@ubuntu-pc:~/src/qemu-0.8.0$ sudo checkinstall -D

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Installing with "make install"...

========================= Installation results ===========================
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.

Copying documentation directory...
/var/tmp/onZDLHCAUDcFSbBbApXT/installscript.sh: line 13: 13669 Segmentation fault      mkdir -p "/usr/share/doc/qemu-0.8.0"

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

simone@ubuntu-pc:~/src/qemu-0.8.0$

```

Any help??

Thanks!!

---

### Post by adamkane on 2006-03-09
Examine the results of:

```

uname -r
uname -m

``` 
The first line tells you which kernel you have installed. The second line tells you what kind of machine Ubuntu thinks you're running. If either of these is incorrect, then you need to install a kernel manually before proceeding.

For Pentium PCs:
```

sudo apt-get install linux-686 linux-headers-686 linux-image-686 linux-restricted-modules-686

``` 
For AMD PCs:
```

sudo apt-get install linux-k7 linux-headers-k7 linux-image-k7 linux-restricted-modules-k7

```

---

### Post by techflat on 2006-10-17
Hi there.

I found your post very usefull because I installed Minix3 on qemu.

Well here's what I did, it's in spanish, hopefully it will help somebody. If I find the time, I'll translate it.

[http://blog.civilizate.cl/page/alfa?catname=%2FEmuladores_Virtualizacion]("http://blog.civilizate.cl/page/alfa?catname=%2FEmuladores_Virtualizacion")

Cheers

---

### Post by mosestruong on 2007-01-07
When I tried to compile, I get the following error:

> qemu-0.8.2/usb-linux.c:29:28: linux/compiler.h: No such file or directory
make[1]: *** [usb-linux.o] Error 1
make[1]: Leaving directory `/home/moses/workspace/qemu/qemu-0.8.2/i386-softmmu'
make: *** [subdir-i386-softmmu] Error 2


Any idea on how to solve this?

---

### Post by maxrisc on 2007-02-11
Is this HowTo currently being maintained?  I see it was posted in September 2005 but no one has done anything to improve it with the latest Distro or QEMU.

If I don't hear an answer in a couple of days I will post my new version to include Edgy.

Thanks,
maxrisc

---

### Post by techflat on 2007-02-11
Hi there

Try this instead:
[http://ubuntuforums.org/showthread.php?t=311324]("http://ubuntuforums.org/showthread.php?t=311324")
It's an automated script to install qemu and kqemu. No networking though.

Cheers


> **maxrisc said:**
> Is this HowTo currently being maintained?  I see it was posted in September 2005 but no one has done anything to improve it with the latest Distro or QEMU.

If I don't hear an answer in a couple of days I will post my new version to include Edgy.

Thanks,
maxrisc

---

### Post by a94060 on 2008-02-17
great tutorial. If you could just add in the command so i can figure out how to add the bridge from the command line,it would be great. Thanks :)

---

