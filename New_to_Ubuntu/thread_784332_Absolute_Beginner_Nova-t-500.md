---
title: "Absolute Beginner Nova-t-500"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by vapd on 2008-05-06
I feel like a bit of a silly person but if I dont ask I guess I wont find out!

I am trying to build a media centre type unit using my old rig (Athlon 2900, Abit AN7, 1.5Gb DDR400, 9800SE, SATA1 HDD). Just got a Nova-T-500. Its the type with only one aerial connector so should work.

I installed Hardy a few days ago, no problems. But that dosnt mean I know what I am doing! Much of Linux terminology is lost on me but I am willing to learn and hope you dont mind teaching me!

When I stuck the card in a PCI slot and turned on I was kind of hoping that Hardy would let me know it had new hardware but it didnt. Fair enough, so I looked around and one of the things I found was that I should drop dvb-usb-dib0700-01.fw into /lib/fireware. So I DL'd it and it wont let me copy and paste it in, the paste option just isnt available? What am I doing wrong!?

Many thanks!

---

### Post by Tatty on 2008-05-06
You need to open an instance of nautilus with superuser powers to write to that folder, open a terminal and type:

```
gksu nautilus
```

Is this the dual tuner version of the card? ( I think yours is the right version as it only has one areal)  I have the dual tuner version and found an excellent wiki page with complete step by step instructions to get this card working.

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

Before you do that though, have a check to see if there is anything for it in the hardware drivers manager (system->administration->hardware drivers) - I have not installed this card in hardy yet so i dont know if this may have been added.

**Edit:** The Hardy kernel number you need for one of the steps is 2.6.24

---

### Post by vapd on 2008-05-06
Hi and thanks!

I did as you said and pasted the .fw file into the folder. Is that it? Should I see some message? Or do I need to restart?

---

### Post by Tatty on 2008-05-06
I recommend taking that file back out of the folder and trying the guide in the link i posted first.  It worked fine for me.

If you need any help with the guide feel free to post back.

---

### Post by vapd on 2008-05-07
Hi,
I decided to install Hardy from scratch as I hoped that would then negate the need to go through the card installation. The first time I installed was without the Nova card.

I am not sure about which point I should pick up the guide after this?

And I am not sure about how to find out if the card is installed in the first place.

lsusb gives me a mention of Hauppauge and Askey Computer Corp but I do not understand what I should do next.

Any help appreciated!

---

### Post by Kouki on 2008-07-17
I've had the Hauppauge t-500 for 7 months now and can't get it to work outside of windows.

I followed the helpful guide posted above but as usually happens when I follow guides on ubuntu, I copy and paste the instructions by the book and end up getting an error.

I can see problems cropping up all the way through installation but just don't have a clue what causes them or how to fix them.  I only know about 5 different words in ubuntu so far despite using it for almost 2 years!  Sudo, gedit, mount, make, mkdir.

I would be extremely grateful if someone could have a look at my terminal input and output and tell me where it's all going wrong and why.

> stuart@stuart-desktop:~$ wget [http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-1.10.fw](http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-1.10.fw)
--21:14:56--  [http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-1.10.fw](http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-1.10.fw)
           => `dvb-usb-dib0700-1.10.fw.2'
Resolving [www.wi-bw.tfh-wildau.de](www.wi-bw.tfh-wildau.de)... 194.95.44.33
Connecting to [www.wi-bw.tfh-wildau.de|194.95.44.33|:80](www.wi-bw.tfh-wildau.de|194.95.44.33|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34,306 (34K) [text/plain]

100%[====================================>] 34,306       123.34K/s             

21:14:57 (123.05 KB/s) - `dvb-usb-dib0700-1.10.fw.2' saved [34306/34306]

stuart@stuart-desktop:~$ sudo cp dvb-usb-dib0700-1.10.fw /lib/firmware
[sudo] password for stuart: 
stuart@stuart-desktop:~$ sudo apt-get install linux-headers-$(uname -r) build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.22-14-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.22-14-generic has no installation candidate
stuart@stuart-desktop:~$ sudo apt-get install mercurial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mercurial is already the newest version.
The following packages were automatically installed and are no longer required:
  libswt3.2-gtk-java libaccess-bridge-java libseda-java libswt3.2-gtk-jni
  linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
stuart@stuart-desktop:~$ sudo apt-get install linux-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswt3.2-gtk-java libaccess-bridge-java libseda-java libswt3.2-gtk-jni
  linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-source-2.6.24
Suggested packages:
  kernel-package libqt3-dev
The following NEW packages will be installed
  linux-source linux-source-2.6.24
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 47.0MB of archives.
After this operation, 47.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
stuart@stuart-desktop:~$ cd ~/
stuart@stuart-desktop:~$ hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
destination directory: v4l-dvb
abort: destination 'v4l-dvb' already exists
stuart@stuart-desktop:~$ cd v4l-dvb
stuart@stuart-desktop:~/v4l-dvb$ 
stuart@stuart-desktop:~/v4l-dvb$ sudo apt-get install ncurses-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libncurses5-dev for regex ‘ncurses-dev’
libncurses5-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libswt3.2-gtk-java libaccess-bridge-java libseda-java libswt3.2-gtk-jni
  linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
stuart@stuart-desktop:~/v4l-dvb$ sudo make menuconfig
make -C /home/stuart/v4l-dvb/v4l menuconfig
make[1]: Entering directory `/home/stuart/v4l-dvb/v4l'
make -C /lib/modules/2.6.22-14-generic/build -f /home/stuart/v4l-dvb/v4l/Makefile.kernel config-targets=1 mixed-targets=0 dot-config=0 SRCDIR=/lib/modules/2.6.22-14-generic/build v4l-mconf
make: Entering an unknown directory
make: *** /lib/modules/2.6.22-14-generic/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [/lib/modules/2.6.22-14-generic/build/scripts/kconfig/mconf] Error 2
make[1]: Leaving directory `/home/stuart/v4l-dvb/v4l'
make: *** [menuconfig] Error 2
stuart@stuart-desktop:~/v4l-dvb$ make
make -C /home/stuart/v4l-dvb/v4l 
make[1]: Entering directory `/home/stuart/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.22
File not found: /lib/modules/2.6.22-14-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'. Stop.
make[1]: Leaving directory `/home/stuart/v4l-dvb/v4l'
make: *** [all] Error 2
stuart@stuart-desktop:~/v4l-dvb$ sudo make install
make -C /home/stuart/v4l-dvb/v4l install
make[1]: Entering directory `/home/stuart/v4l-dvb/v4l'
Stripping debug info from files
Usage: strip <option(s)> in-file(s)
 Removes symbols and sections from files
 The options are:
  -I --input-target=<bfdname>      Assume input file is in format <bfdname>
  -O --output-target=<bfdname>     Create an output file in format <bfdname>
  -F --target=<bfdname>            Set both input and output format to <bfdname>
  -p --preserve-dates              Copy modified/access timestamps to the output
  -R --remove-section=<name>       Remove section <name> from the output
  -s --strip-all                   Remove all symbol and relocation information
  -g -S -d --strip-debug           Remove all debugging symbols & sections
     --strip-unneeded              Remove all symbols not needed by relocations
     --only-keep-debug             Strip everything but the debug information
  -N --strip-symbol=<name>         Do not copy symbol <name>
  -K --keep-symbol=<name>          Do not strip symbol <name>
     --keep-file-symbols           Do not strip file symbol(s)
  -w --wildcard                    Permit wildcard in symbol comparison
  -x --discard-all                 Remove all non-global symbols
  -X --discard-locals              Remove any compiler-generated symbols
  -v --verbose                     List all object files modified
  -V --version                     Display this program's version number
  -h --help                        Display this output
     --info                        List object formats & architectures supported
  -o <file>                        Place stripped output into <file>
strip: supported targets: elf32-i386 a.out-i386-linux efi-app-ia32 elf32-little elf32-big elf64-x86-64 efi-app-x86_64 elf64-little elf64-big srec symbolsrec tekhex binary ihex trad-core
make[1]: *** [media-install] Error 1
make[1]: Leaving directory `/home/stuart/v4l-dvb/v4l'
make: *** [install] Error 2
stuart@stuart-desktop:~/v4l-dvb$ sudo gedit /etc/modprobe.d/options
stuart@stuart-desktop:~/v4l-dvb$ sudo make load
make -C /home/stuart/v4l-dvb/v4l load
make[1]: Entering directory `/home/stuart/v4l-dvb/v4l'
scripts/rmmod.pl load
found 0 modules
make[1]: Leaving directory `/home/stuart/v4l-dvb/v4l'
stuart@stuart-desktop:~/v4l-dvb$ sudo modprobe dvb-usb-dib0700
stuart@stuart-desktop:~/v4l-dvb$ dmesg | grep -i dvb
[   42.324507] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   43.072701] dvb-usb: did not find the firmware file. (dvb-usb-dib0700-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[   43.072742] usbcore: registered new interface driver dvb_usb_dib0700
stuart@stuart-desktop:~/v4l-dvb$ 


Help much appreciated!

---

