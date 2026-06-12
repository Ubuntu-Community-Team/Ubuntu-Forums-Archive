---
title: "HOWTO Linmodems Winmodems softmodems"
date: 2004-11-27
forum: Outdated Tutorials &amp; Tips
---

### Post by az on 2004-11-27
**This is not completely finished yet.  I am editing it regularly***

Many software modems work under linux.  To check yours, download this

[http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)
 
 gunzip scanModem.gz
 chmod +x scanModem
 sudo ./scanModem

read the /scan/ModemData.txt file created.

With most winmodems, you will need to compile the driver (make a kernel module) You will need to get the source (or just your kernel's headers) and unpack it.
 You will need to install the packages necessary for compiling stuff
 
 sudo apt-get install build essential
 sudo apt-get install linux-headers-2.6-386 kernel-kbuild-2.6-3
 
 Since I am using the default 386 kernel, I got the 386 kernel-headers. When asked during the configuration of the source for the driver where the kernel-source is, I will tell it to use:
 /usr/src/linux-headers-2.6.8.1-3-386
 
 The difference between Ubuntu and debian is that Ubuntu names the packages linux-headers and not kernel-headers. The Linuxant debian package,for example, tells you to install the kernel-headers-3.6.8-1-386 package (which does not exist in Ubuntu - you must use linux-headers-2.6-386
 

CONEXANT MODEM
The Conexant drivers are sold by a company.  Find them on the net.  Try to get them to work.  Ask them questions.  It is detailed in the forums how to get their driver to work with Ubuntu.  I bought a Lucent winmodem on ebay for less than half the price of their driver.  That is neither here nor there.

PCTEL MODEM
The pctel chipsets work with the 2.4 linux kernel, but not the newer 2.6 (Ubuntu) kernel.  Pctel sold themselves to conexant and probably will not release any new drivers for linux.
When I have the time, I'll install a debian 2.4 kernel on an Ubuntu system to see how things go.  Maybe this would be a viable alternative for you...

Motorola also is lacking in new drivers for linux.  Perhaps in the future they will release a 2.6 kernel driver.
Please send them an email asking for current linux drivers.  Ask for generic drivers which can be used in every linux distribution:
[email]softmodem@motorola.com[/email]  (Send them a message, seriously.  They will never release drivers unless asked...)


Lucent has wonderful drivers available.
Here are some prebuilt modules for the default Warty kernel.
(2.6 kernel drivers seem broken at the moment... Send me a private message if they *do* work for you.  I am emailing the maintainers)
[http://www.vif.com/users/mzajac/ltmodem-2.6.8.1-3-386_8.31a8_i386.deb](http://www.vif.com/users/mzajac/ltmodem-2.6.8.1-3-386_8.31a8_i386.deb)

dpkg -i ltmodem*.deb

souce:
[http://www.sfu.ca/~cth/ltmodem/ltmodem-8.31a10.tar.gz](http://www.sfu.ca/~cth/ltmodem/ltmodem-8.31a10.tar.gz)
[http://www.heby.de/ltmodem](http://www.heby.de/ltmodem)

tar xvzf ltmodem*
cd ltmodem*
./build_deb
Then, install the debian package,.


Smartlink

Put these two packages on a floppy:
[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.9-1_i386.deb)

Try the two sl-modem packages (daemon and source) first.  By default, it will try to use the GPL alsa driver (already in the Ubuntu kernel) for the intel chipset since the smartlink modules are not compiled yet.) 
 sudo dpkg -i sl-modem*.deb
 It will complain about missing dependancies. (build-essential and so forth)
 You then do:
 sudo apt-get -f install 
 and eveything else needed is found on your cd. (build-essential...)
 
 Try to connect to the net.
 You may need to edit /etc/default/sl-modem-daemon to specify the device if 'auto' fails.
 
 SLMODEMD_DEVICE=hw:0 #(or hw:1depends on your soundcard, I guess)
 
If it still don't work, download and install the modules (or make them youself...)

[http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb](http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb)

Then reconfigure sl-modem-daemon to use the slarm modules instead of the snd_intel8x0m module...

sudo dpkg-reconfigure sl-modem-daemon
 
To make the modules yourself, unpack the sl-modem.tar.bz2 in /usr/src
tar xvjf sl-modem*
cd /usr/src/modules/sl-modem/debian
edit control.modules.in
Depends: linux-image-_KVERS_
This is because Ubuntu uses different package names for the kernel-headers.
Then do:
cd ..
debian/rules kdist KVERS=$(uname -r) KSRC=/usr/src/linux-headers-$(uname -r)

then install the modules by installing the package you just made:
dpkg -i sl-modem-modules*

***To be completed....

Intel

If the sl-modem driver did not work for your intel chipset, there are Intel drivers available.

---

### Post by paulozzzz on 2005-11-24
How do I get gcc working?  Whenever I type any gcc command the shell reports that the command can not be found.

---

### Post by towsonu2003 on 2005-11-25
just a quick note: 

for slmodems, they may not need to compile. instead, they can use the precompiled drivers. that's what I am doing right now. also, try modem:0 and modem:1 if hw:0 doesnt work... 

Also, they may find nice help from linmodems.org's mailng list if they are stuck. those people are really helpful...

---

### Post by az on 2005-11-25
This howto is old.  There is newer stuff on the wiki.  If you cannot find your answer there, when you do, add it there so that everyone can find it:

wiki.ubuntu.com/UserDocumentation


paulozzzz:  You need to install build-essential.  But, the compiler that was used to build the kernel is not included.  You need gcc-3.4, which is available from the online repositories, and not your cd.

---

### Post by paulozzzz on 2005-11-26
"You need to install build-essential. But, the compiler that was used to build the kernel is not included. You need gcc-3.4, which is available from the online repositories, and not your cd."

How do I do this?  Is it an apt-get command?  I am a Windows user trying to migrate to Linux, but in order to accomplish that I do need my modem working.  In Windows I install things by downloading some setup.exe file and executing it.  Please, help.

---

### Post by paulozzzz on 2005-11-26
"for slmodems, they may not need to compile. instead, they can use the precompiled drivers. that's what I am doing right now."

That would be good, I think.

"Also, they may find nice help from linmodems'org's mailng list if they are stuck. those people are really helpful..."

Thanks for the hint.

---

### Post by towsonu2003 on 2005-12-10
I though this ( [http://ubuntuforums.org/showthread.php?t=82608](http://ubuntuforums.org/showthread.php?t=82608) ) might be relevant here?

---

### Post by paulozzzz on 2005-12-15
[QUOTE=towsonu2003]I though this ( [http://ubuntuforums.org/showthread.php?t=82608](http://ubuntuforums.org/showthread.php?t=82608) ) might be relevant here?[/QUOTE]

Thanks very much, towsonu2003.  The Linmodems.org people helped me with the problem and everything is OK now.

Here is the walktrough:

1) Download alsa-driver-1.0.10.tar.bz2 (2,194,644 bytes) from
[http://www.alsa-project.org/](http://www.alsa-project.org/) ("driver" link) into your home folder.

2) Download alsa-lib-1.0.10.tar.bz2 (706,777 bytes) from
[http://www.alsa-project.org/](http://www.alsa-project.org/) ("library" link) into your home folder.

3) Verify the presence of the kernel-headers needed for compilation:
   $ ls -d /usr/src/linux*
   The following files must appear in the listing:
   /usr/src/linux-headers-2.6.10-5
   /usr/src/linux-headers-2.6.10-5-386

4) Create the following folders
   $ sudo mkdir /usr/src/modules
   $ sudo mkdir /usr/src/modules/alsa

5) Extract the contents of the downloaded archives into the recently created
folders:
   $ cd /usr/src/modules/alsa
   $ sudo tar jxf /home/<your user name>/alsa-driver-1.0.10.tar.bz2
   $ sudo tar jxf /home/<your user name>/alsa-lib-1.0.10.tar.bz2

6) Verify the presence of the following folders in /usr/src/modules/alsa:
   $ ls -l
   drwxr-xr-x (...) alsa-driver-1.0.10
   drwxr-xr-x (...) alsa-lib-1.0.10

7) Go to the drivers' folder:
   $ cd alsa-driver-1.0.11

8) Compile the driver:
   $ sudo make clean
   The command above can end up with error[1], no problem.
   $ sudo ./configure --with-kernel=/usr/scr/linux-headers-2.6.10-5-386
--with-build=/usr/src/linux-headers-2.6.10-5-386 --with-cards=ali5451
   The command above checks for needed resources and then makes some
configuration
files.
   Its output should be similar to this:
   checking for PC9800 support in kernel... "no"
   checking for parallel port support... "yes"
   checking for which soundcards to compile driver for... ali5451
   configure: creating ./config.status
   config.status: creating version
   config.status: creating Makefile.conf
   config.status: creating snddevices
   config.status: creating utils/alsa-driver.spec
   config.status: creating utils/buildrpm
   config.status: creating toplevel.config
   config.status: creating utils/alsasound
   config.status: creating utils/alsasound.posix
   config.status: creating include/pci_ids_compat.h
   config.status: creating include/config.h
   config.status: creating include/config1.h
   config.status: creating include/version.h
   config.status: include/version.h is unchanged
   config.status: creating include/autoconf-extra.h
   config.status: include/autoconf-extra.h is unchanged
   Hacking autoconf.h...

9) The snd-ali5451.ko driver and others it is dependent on assembled by command:
   $ sudo make
   The output should be similar to this:

   The created modules have symbolic links in the modules/  folder
   snd-ac97-bus.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/pci/ac97/snd-ac97-bus.ko
   snd-ac97-codec.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/pci/ac97/snd-ac97-codec.ko
   snd-ali5451.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/pci/ali5451/snd-ali5451.ko
   snd-mixer-oss.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/acore/oss/snd-mixer-oss.ko
   snd-mpu401-uart.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/drivers/mpu401/snd-mpu401-uart.ko
   snd-page-alloc.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/acore/snd-page-alloc.ko
   snd-pcm-oss.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/acore/oss/snd-pcm-oss.ko
   snd-pcm.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/acore/snd-pcm.ko
   snd-rawmidi.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/acore/snd-rawmidi.ko
   snd-seq-device.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/acore/seq/snd-seq-device.ko
   snd-seq-midi-event.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/acore/seq/snd-seq-midi-event.ko
   snd-seq-midi.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/acore/seq/snd-seq-midi.ko
   snd-seq-oss.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/acore/seq/oss/snd-seq-oss.ko
   snd-seq.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/acore/seq/snd-seq.ko
   snd-timer.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/acore/snd-timer.ko
   snd.ko -> /usr/src/modules/alsa/alsa-driver-1.0.10/acore/snd.ko

10) This driver set could be installed with:
   $ sudo make install

11) Update the system to recalculate the module dependencies with:
   $ sudo depmod -a

12) Activate de module:
   $ sudo modprobe snd-ali5451

13) Whenever you need to activate the modem port, run:
   $ sudo  slmodemd -c BRAZIL -s --alsa hw:0,1
   SmartLink Soft Modem: version 2.9.9e-pre1 Sep 24 2005 14:47:19
   symbolic link `/dev/ttySL0' -> `/dev/pts/1' created.
   modem `hw:0,1' created. TTY is `/dev/pts/1'
   Use `/dev/ttySL0' as modem device, Ctrl+C for termination.

14) Configure the modem application to use the /dev/ttySL0 port.

:KS

---

