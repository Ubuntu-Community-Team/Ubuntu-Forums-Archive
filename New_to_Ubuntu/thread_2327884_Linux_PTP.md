---
title: "Linux PTP"
date: 2016-06-15
forum: New to Ubuntu
---

### Post by Lector41 on 2016-06-15
I am pretty new to Ubuntu but recently I had to sync the clocks of multiple machines in a LAN.  I chose Linux PTP due to the fact that while all machines were different, they were all running either Ubuntu or Lubuntu as their OS and Linux PTP was free.  When trying to implement IEEE 1588 protocol on all of these machines I ran into lots of problems and what documentation I did find was either over my head due to the fact I am a novice, or incomplete.  What follows are the steps I found worked for me.  You'll have to excuse me if any of the information or terminology is incorrect, like I said I'm pretty new to this.  Hope it helps!  

**IEEE1588 Linux PTP**

    Linux PTP is a software implementation of PrecisionTime Protocol (PTP) that is in accordance with the IEEE 1588standard.  Linux PTP makes use of the Linux kernel, this allowed usto take advantage of the flexibility that is inherent to LinuxApplication Programming Interfaces (API).  Another very practicalreason for our choice was cost.  Linux PTP is free and readilyavailable for download.  
    Some useful features of Linux PTP are as follows.

[LIST]
[*]
[*]    Supports    hardware and software time stamping via the Linux SO_TIMESTAMPING    socket option.
[*]    Supports    the Linux PTP Hardware Clock (PHC) subsystem by using the    clock_gettime family of calls, including the new clock_adjtimex    system call.
[*]    Implements    Boundary Clock (BC) and Ordinary Clock (OC).
[*]    Transport    over UDP/IPv4, UDP/IPv6, and raw Ethernet (Layer 2).
[*]    Supports    IEEE 802.1AS-2011 in the role of end station.
[*]    Modular    design allowing painless addition of new transports and clock    servos.
[/LIST]
    [www.linuxptp.sourceforge.net]("http://www.linuxptp.sourceforge.net/")

**PTP Prerequisites **   

    The machine requirements for Linux PTP implementation 
[LIST]
[*]
[*]    Linux kernel version 3.0 or newer
[*]    Kernel headers available at compile time
[*]    A supported Ethernet MAC device
[*]    A supported PHY device paired with a MAC that allows    time stamping in the PHY
[/LIST]

[www.linuxptp.sourceforge.net]("http://www.linuxptp.sourceforge.net/")

    Beforestarting the process of implementing Linux PTP it was imperative tosee if the machines at our disposal had the capabilities listeddirectly above by using the 'ethtool'.

    $ethtool -T <network interface>

    This command will list the time stamping capabilitiesof the chosen network interface.  In our case only software timestamping is available.  Another advantage of the ethtool ioctl isthat while running the ptp4l program (ptp4l does the heavy liftingfor clock syncronization), it will use ethtool in order to discoverthe proper PHC device.

    Some other tools that will be needed in order tomanipulate, compile, and build the appropriate kernel are 
[LIST]
[*]
[*]    fakeroot
[*]    build-essential
[*]    crash
[*]    kexec-tools (when prompted do not let kexec    handle reboots)
[*]    makedumpfile
[*]    kernel-wedge
[/LIST]

    All of these tools can be obtained with the apt-getinstall command.

**Linux Kernel Manipulation**

    The most difficult part of Linux PTP implementation(for novices to Linux like me) is the reconfiguration of the LinuxKernel.  In order to sync the clocks of two or more machines threekernel configuration options are needed. 
[LIST]
[*]
[*]    CONFIG_PPS
[*]    CONFIG_NETWORK_PHY_TIMESTAMPING
[*]    PTP_1588_CLOCK
[/LIST]
    The environment I worked to synchronize was anon-homogeneous one in that the machines were both physicallydifferent and the operating systems (along with the kernels) varied. By looking at the .config file for each kernel it was evident that inall cases the CONFIG_NETWORK_PHY_TIMESTAMPING option was set to 'n'(not available).  In most cases the other two options were set to 'm'(modular).  It has been my experience that either 'y' (on) or 'm' areacceptable states for these options.  
    What follows will be generalized script of commands andactions I have taken in order to get the Linux kernel in anacceptable state for the implementation of IEEE 1588.  These steps(with slight variations) are able to build a working kernel in bothUbuntu and Lubuntu.
[B]
Kernel Configuration Set Up[/B]
[LIST]
[*]
[*]    $sudo apt-get update 
[*]    $sudo apt-get -f upgrade    These    two steps make sure all of the software installed on the machine is    the latest.  It should also fix any potential dependency issues.
[*]    $cd /usr/src    Changes    to the directory where the kernels reside
[*]    $sudo apt-get source linux-image-$(uname -r)
[*]    $sudo apt-get build-dep linux-image-$(uname    -r)    These last two steps place    a copy of the latest version of the currently running kernel in the    /usr/src directory.  It also places the correct debian files needed    for the kernel build in the /usr/src directory
[*]    $cd <to newest version of the kernel>    
[*]    $cd debian
[*]    $sudo chmod a+x scripts/
[*]    $cd scripts a+x misc/    These    steps alter the permissions to the debian scripts which will do the    heavy lifting in building the kernel
[*]    $cd<to newest version of the kernel>
[*]    $sudo fakeroot debian/rules clean
[*]    $sudo fakeroot debian/rules editconfigs    These    steps bring up a GUI for the configuration file of the kernel
[/LIST]

**KernelReconfiguration (While in Menu-Config)**

[LIST]
[*]
[*]    Navigate to CONFIG_PPS,    CONFIG_NETWORK_PHY_TIMESTAMPING, and PTP_1588_CLOCK and switch their    status to 'y'.  After this save settings and exit.
[/LIST]

**KernelBuild**
[LIST]
[*]
[*]    $sudo fakeroot debian/rules clean
[*]    $sudo fakeroot debian/rules binary-headers    binary-generic    These steps    will begin the compilation process.  Compilation will take some    time.  Due to the varying processing capabilities of the machines    used I found this can take anywhere between 2-16 hours.
[*]    $cd /usr/src
[*]    $ls *.deb    Shows    only the new .deb files
[*]    $sudo dpkg -i linux <desired verion>.deb
[*]    $sudo reboot
[/LIST]

**LinuxPTP Installation**

[LIST]
[*]
[*]    Download latest release from Source Forge            [www.linuxptp.sourceforge.net]("http://www.linuxptp.sourceforge.net/")
[*]    $cd <path to LinuxPTP>
[*]    $sudo make clean
[*]    $sudo make
[*]    $sudo make install    Linux    PTP should now be ready
[/LIST]

**Useof Linux PTP**

    After Linux PTP stack gets made and installed on thedesired machines it is possible to synchronize their clocks.  This isaccomplished by proper networking and the ptp4l command. There are two ways to utilize ptp4l.
    The first way is to specify the desired options in thecommand line.  The least specific command that will start 1588protocol is $ptp4l -i <desired networking interface>. However for the environment I was working in I needed a few extracommand options.  For our purposes $ptp4l -i <net int> -m -Swas the command used.  

[LIST]
[*]
[*]     -m was used to display the current state of the ptp4l    program to the standard out
[*]    -S was necessary to specify the use of Software    Timestamping
[/LIST]
Other options can be explored in the ptp4l manual ($manptp4l).
    The second way to get ptp4l syncing the clocks is tocreate a configuration file and run from that.  $ptp4l -f </pathto config file>.  Below is an example of a configuration file. The options laid out in the configuration file will vary dependingon what type of network interface is being used on that machine.

[LIST]
[*]
[*]    [global]
[*]    verbose             1
[*]    time_stamping        software
[*]    tx_timestamp_timeout    100
[*]    [eth0]
[*]    [tap0]
[/LIST]

    This file basically does the same thing as laying outthe options in the command line.  The one important difference isthat in a configuration file it is possible to identify multiplenetwork interfaces.  This is necessary if the machine is to be set upas a boundary clock.  Many more options are laid out in the manualfor ptp4l.

**InformationGathering**

    It is easy to tell if ptp4l is doing it's job.  Eitherthe -m in the command line or the verbose 1 option inthe configuration file will update the status of synchronization tothe standard out every second by default.  This information can bebroken down as follows
[LIST]
[*]
[*]    master offset-    Measured offset from the master in nanoseconds
[*]    s0, s1, s2-    Indicates clock servo states (0 unlocked, 1 clock-step, 2 locked)
[*]    freq value-    Frequency adjustment of the clock in parts per billion
[*]    path delay-    estimated delay of the synchronization message sent from the master    in nanoseconds
[*]    Port 0- UNIX    domain socket used for local PTP management
[*]    Port 1-    Network interface being used for synchronization
[/LIST]

---

### Post by TheFu on 2016-06-16
Generally, it is best to avoid building software from source to be installed. There are many reasons for this.
**sudo apt-get install ptp** should work.  [http://manpages.ubuntu.com/manpages/trusty/man8/ptpd.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/ptpd.8.html) There is an official ptp package in the repos.  Seems odd to build from source when it isn´t necessary. Though I suppose there are times when that is needed.

Or use NTP by running
**sudo apt-get install ntp**
and be done. No need to rebuild a kernel. The default configs are usually fine for most locations, though some parts of the world might choose to point their NTP clients to different NTP servers.

NTP isn´t perfect, but it is well supported by all platforms that have networking. Running an NTP client is trivial, just install it.  Running a local NTP server (stratum 3 or higher) isn´t much harder, then just point all the local NTP clients to that server in the /etc/ntp.conf the ¨server IP¨ line it is. The server would still need to point at multiple, quality, external, NTP servers.

BTW, almost all Unix software is not just free these days, it is open source with nice licenses like MIT, BSD, GPL, LGPL or other similar F/LOSS licenses. Don´t actually know of any NTP software that is NOT F/LOSS.  For me, being ¨free¨ is NOT sufficient.

By staying inside the official repos, we take advantage of the primary reasons Linux systems maintenance is better than the maintenance for other OSes, IMHO.  Building software from source, breaks this aspect.

---

### Post by Lector41 on 2016-06-17
It wasn't really my idea to sync up these clocks (not really my idea of a leisure activity).  I was tasked to explore the capabilities of The Linux PTP Project for work related purposes.  One of the requirements when running this is that the CONFIG_NETWORK_PHY_TIMESTAMPING option in the kernel is turned on.  I had to set this up on a network of 8 machines all running different versions of either Ubuntu or Lubuntu and when I looked at the .config files for each kernel none of them had this option turned on.  For the most part the other two required options, PTP_1588_CLOCK, and CONFIG_PPS were set up as modules but it was not always the case.  That was why it seemed a new kernel build was necessary.  I am not trying to persuade anyone to build this from the source, so if the simple sudo apt-get install ptp works for your purposes by all means go ahead.  In my case I was tasked to build from source and it was a pain ](*,).  Just trying to alleviate any future headaches for people if they find themselves in a similar situation.

---

