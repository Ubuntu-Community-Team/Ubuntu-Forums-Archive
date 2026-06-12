---
title: "Edgy Howto: Intel 536ep modem"
date: 2006-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2006-11-19
Hi,
    I have updated my old Dapper howto and posted it in a new thread so as to not Bloat the dapper one. If anyone finds any changes please post and I will try to amend.

                                          **[B]_[COLOR=#000000][SIZE=2][FONT=Arial, sans-serif]Modems supported by the Intel536EP driver for Ubuntu Edgy Eft[/FONT][/SIZE][/COLOR]_**[/B]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]This page describes how to install the driver for the Intel 536EP internal modem on Ubuntu Edgy for i386 systems. Some of these are sold as Cnet modems and have Ambient chips on board. The process below is quick easy and works quite well. For other older ubuntu versions before Dapper you will additionally require gcc 3.4 to also be installed. [/SIZE][/FONT][/COLOR] 
 [B] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2][B]
Install required Ubuntu packages[/B][/SIZE][/FONT][/COLOR][/B]

 [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]In a terminal type [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]uname -r[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000], which should give you your kernel version ARCH[/COLOR][/FONT][/SIZE]
 [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]You will need to install the [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]build-essential[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000] and [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]linux-headers-ARCH[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000] packages. They are normally on the install CD and can most easily be installed with Synaptic or downloaded if your PC is on a connected lan or using a serial modem, which does not require drivers.[/COLOR][/FONT][/SIZE]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
Download the latest drivers for the Intel536ep modem here: [/SIZE][/FONT][/COLOR] 
                                             [COLOR=#000080]_[[SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-536EP-2.56.76.0_21_09_2006.tgz[/COLOR][/FONT][/SIZE]]("http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-536EP-2.56.76.0_21_09_2006.tgz")_[/COLOR] 
 
 [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]Save the file, which is named i[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]ntel-536EP-2.56.76.0_21_09_2006.tgz[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000] on your Desktop. [/COLOR][/FONT][/SIZE] 
 [B] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2][B]
Compiling the driver[/B][/SIZE][/FONT][/COLOR][/B]

 [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]Right click on the file and select &#8220;Extract to here&#8221; This will create directory [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]intel-536EP-2.56.76.0[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]  on your Desktop. Open a terminal window and type: [/COLOR][/FONT][/SIZE] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]cd Desktop/intel-536EP-2.56.76.0[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]make clean[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
This should produce output looking like this: [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]make[1]: Entering directory `/home/<usename>/Desktop/intel-536EP-2.56.76.0/coredrv'[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
rm -f *.ko .*.o.cmd *.mod.c .*.ko.cmd *.o *~ core Modules.symvers[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]rm -rf .tmp_versions[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]make[1]: Leaving directory `/home/<username>/Desktop/intel-536EP-2.56.76.0/coredrv'[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
rm -f *.o *.ko[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

make 536[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]This will result in many lines of output, the final lines should look like this: [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000]   [SIZE=2][FONT=Arial, sans-serif]CC      /home/<username>/Desktop/intel-536EP-2.56.76.0/coredrv/Intel536.mod.o[/FONT][/SIZE][/COLOR] 
[COLOR=#000000]  [SIZE=2][FONT=Arial, sans-serif]LD [M]  /home/<username>/Desktop/intel-536EP-2.56.76.0/coredrv/Intel536.ko[/FONT][/SIZE][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]make[1]: Leaving directory `/home/<username>/Desktop/intel-536EP-2.56.76.0/coredrv'[/SIZE][/FONT][/COLOR]  [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]

There should be an [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]Intel536.ko[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000] file in the directory now; test this by typing[/COLOR][/FONT][/SIZE]
 [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]ls -l Intel536.ko [/COLOR][/FONT][/SIZE] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]The output should look like:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000] [SIZE=2][FONT=Arial, sans-serif]--rw-r--r-- 1 <username> <username> 1099788 2006-11-13 19:50 Intel536.ko[/FONT][/SIZE][/COLOR] 

[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**Installing the driver**[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]There are two steps to installing the driver. The first is to copy the Intel536.ko file created above to an appropriate directory, and the second is to have the driver loaded every time the PC boots. [/SIZE][/FONT][/COLOR] 
 *[SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]To install the Intel536.ko file, c[/COLOR][/FONT][/SIZE]*[SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]opy the file to the modules directory with this command: [/COLOR][/FONT][/SIZE] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]sudo cp Intel536.ko /lib/modules/$(uname -r)/kernel/drivers/char[/SIZE][/FONT][/COLOR] 
[SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]Make your system aware of this module with [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]depmod[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]: [/COLOR][/FONT][/SIZE] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]sudo depmod -a[/SIZE][/FONT][/COLOR] 
[SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]Finally, load the driver with the [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]modprobe[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000] command: [/COLOR][/FONT][/SIZE] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]sudo modprobe Intel536[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]This command should not print a response; if it prints something like this: [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000] [SIZE=2][FONT=Arial, sans-serif]FATAL: Module Intel536 not found.[/FONT][/SIZE][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]you have made an error; most likely you have copied the file to the wrong place. If you see a different error message, there may be an error in the module, or your modem, or you may not have a Intel 536-based modem. [/SIZE][/FONT][/COLOR] 
 [I][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]
Loading the driver at boot time[/COLOR][/FONT][/SIZE][/I] 
 [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]To load the module at boot time, we need to add a line "[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]Intel536[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]" to the file /etc/modules. Right click on the file, actions, Edit as Root and enter a line at the end:[/COLOR][/FONT][/SIZE]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Intel536[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2][B]
Using the modem[/B][/SIZE][/FONT][/COLOR]
 [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]The name of your modem device is [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]/dev/536ep0[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]. To use Kppp you will need to create a symlink be able to link the /dev/536ep0 to /dev/modem. Udev rewrites the /dev on each reboot and you thus have to create a new file with kwrite, kate or gedit in /etc/udev/rules.d/60-symlink.rules and find the following lines and put the last line in it: 

[/COLOR][/FONT][/SIZE]   [COLOR=#000000] [SIZE=2][FONT=Arial, sans-serif]    # Create /dev/modem symlink[/FONT][/SIZE][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
KERNEL=="ttyLTM[0-9]*",            SYMLINK+="modem"[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
KERNEL=="536ep0",                   SYMLINK+="modem"[/SIZE][/FONT][/COLOR]  

[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Now reboot and you can use Kppp to query the modem as this is a quick check if all is well before dialling out. Configure Kppp or Gnome-ppp for your ISP connection. These Intel modems are found to be quite stable.[/SIZE][/FONT][/COLOR]

---

### Post by luvinit on 2006-12-01
OK I am having serious problems. I have checked out loads of threads about how to do this but it doesn't help. When I get to the make 536 stage I get the "please install kernel source message". I have installed a whole bunch of things which have no effect. I cannot find this ARCH thing that you mention. Does anyone know what I am supposed to install to get past this stage ans exactly where I find it? By the way, I only want yo install my modem for faxes, my Internet connection is on cable.

---

### Post by Matchless on 2006-12-03
Hi,
    What needs to be installed is linux-headers-2.6.17-10-generic (yours may differ) which are Linux kernel headers for version 2.6.17 on x86/x86_64. If you type uname -r in the konsole/terminal it will give you the exact version you are using. A quick way is to search for linux-headers in Synaptic and you will see if it is installed or not, in your case select it and install.

---

### Post by luvinit on 2006-12-03
Thanks a lot, my modem is now working. I have checked a huge number of guides to modem installation and on the whole they aren't clear enough for newbies like me (I didn't have clue about what the term linux headers meant). My first instinct was to use synaptic but what I chose and installed was incorrect. Useful commands I have found for the installation of linux headers  are:
 
sudo apt-get install linux-headers-386

and 

sudo apt-get install build-essential

When people are trying to test their modem use minicom and follow this guide

[http://www.tldp.org/HOWTO/Modem-HOWTO-11.html](http://www.tldp.org/HOWTO/Modem-HOWTO-11.html)

the serial port you need to put in it is the name of your device, in this case 
/dev/536ep0

the offical guide is fine other than not telling you about how to get the linux headers

[https://help.ubuntu.com/community/DialupModemHowto/Intel536EP](https://help.ubuntu.com/community/DialupModemHowto/Intel536EP)

I take it the above guide was written by matchless due to its similarity? Thanks to all who to take the time to do this stuff.

---

### Post by Matchless on 2006-12-03
Hi,
     Glad you got it going. Yes,  I recall these exact same frustrations myself. You see, Linux uses "dependancies" mostly installed seperately or called up automatically when installing an application. Unlike windows the package you install is very small and usually does not contain all the other packages it is dependant on.
The howto's follow a very similar pattern and also cannot contain all the steps that are needed and thus not directly related to the package install. There are usually seperate howto's for enabling repositories and preparing your pc to allow you to compile your own packages or such as installing codecs to make a multimedia package work properly on all formats.
This is what drives a newcomer nuts, but if one would try to overcome this, the howto's could become a couple of pages (some are already) long, be difficult and maybe too much work for people (read community) to write and be be very cumbersome to wade through as many of the users on the other hand also know certain basics and hate heavy long winded instructions . Then we also have the howtos written in command style or on doing it from the gui and so on...
Basically there are arguments for keeping them brief AND for including all the detail, as we have beginners, experienced users and fundi's or there.

---

### Post by kozimodo on 2006-12-04
For some reason my compile is failing.  This is my "make 536" output:
```
   Module precompile check
   Current running kernel is: 2.6.15-27-k7
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
        cd coredrv && make 536core_26 && \
        cp Intel536.ko .. && cd .. && \
        strip --strip-debug Intel536.ko && \
        exit; \
        ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed to build driver" && exit; \
        if [  ]; then \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        else \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname -r`/build/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
        cp Intel536.o .. ; \
        if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/version.h;\
        fi
2.6.15-27-k7
make[1]: Entering directory `/home/<username>/intel-536EP-2.56.76.0/coredrv'
make -C /lib/modules/2.6.15-27-k7/build SUBDIRS=/home/<username>/intel-536EP-2.56.76.0/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-27-k7'
  CC [M]  /home/<username>/intel-536EP-2.56.76.0/coredrv/coredrv.o
/home/<username>/intel-536EP-2.56.76.0/coredrv/coredrv.c: In function &#8216;send_data_to_user&#8217;:
/home/<username>/intel-536EP-2.56.76.0/coredrv/coredrv.c:608: warning: implicit declaration of function &#8216;tty_buffer_request_room&#8217;
/home/<username>/intel-536EP-2.56.76.0/coredrv/coredrv.c:609: error: void value not ignored as it ought to be
make[3]: *** [/home/<username>/intel-536EP-2.56.76.0/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/home/<username>/intel-536EP-2.56.76.0/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-27-k7'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/<username>/intel-536EP-2.56.76.0/coredrv'
2.6.15-27-k7
Failed to build driver
```
Any ideas/suggestions?

---

### Post by diesel1 on 2006-12-09
Hi all,

I have tried several times to compile this driver but it never compiles, I followed the howtos very carefully.

This is the output from my attempts.....

kath@kath-desktop:~/Desktop/Intel-536$ make 536
   Module precompile check
   Current running kernel is: 2.6.17-10-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
        cd coredrv && make 536core_26 && \
        cp Intel536.ko .. && cd .. && \
        strip --strip-debug Intel536.ko && \
        exit; \
        ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed to build driver" && exit; \
        if [  ]; then \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        else \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname -r`/build/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
        cp Intel536.o .. ; \
        if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/version.h;\
        fi
2.6.17-10-generic
make[1]: Entering directory `/home/kath/Desktop/Intel-536/coredrv'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/kath/Desktop/Intel-536/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/kath/Desktop/Intel-536/coredrv/coredrv.o
/home/kath/Desktop/Intel-536/coredrv/coredrv.c:73: warning: data definition has no type or storage class
/home/kath/Desktop/Intel-536/coredrv/coredrv.c:73: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL_NOVERS&#8217;
/home/kath/Desktop/Intel-536/coredrv/coredrv.c:73: warning: parameter names (without types) in function declaration
/home/kath/Desktop/Intel-536/coredrv/coredrv.c: In function &#8216;softcore_init_struct&#8217;:
/home/kath/Desktop/Intel-536/coredrv/coredrv.c:339: warning: assignment from incompatible pointer type
/home/kath/Desktop/Intel-536/coredrv/coredrv.c: In function &#8216;close&#8217;:
/home/kath/Desktop/Intel-536/coredrv/coredrv.c:439: warning: implicit declaration of function &#8216;pm_unregister&#8217;
/home/kath/Desktop/Intel-536/coredrv/coredrv.c: In function &#8216;send_data_to_user&#8217;:
/home/kath/Desktop/Intel-536/coredrv/coredrv.c:587: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/home/kath/Desktop/Intel-536/coredrv/coredrv.c:592: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/home/kath/Desktop/Intel-536/coredrv/coredrv.c:593: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/home/kath/Desktop/Intel-536/coredrv/coredrv.c:595: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/home/kath/Desktop/Intel-536/coredrv/coredrv.c:596: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/home/kath/Desktop/Intel-536/coredrv/coredrv.c:597: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/home/kath/Desktop/Intel-536/coredrv/coredrv.c: At top level:
/home/kath/Desktop/Intel-536/coredrv/coredrv.c:665: error: expected &#8216;)&#8217; before string constant
/home/kath/Desktop/Intel-536/coredrv/coredrv.c: In function &#8216;hamproc_write&#8217;:
/home/kath/Desktop/Intel-536/coredrv/coredrv.c:684: warning: ignoring return value of &#8216;copy_from_user&#8217;, declared with attribute warn_unused_result
/home/kath/Desktop/Intel-536/coredrv/coredrv.c: At top level:
/home/kath/Desktop/Intel-536/coredrv/coredrv.c:880: warning: initialization makes integer from pointer without a cast
make[3]: *** [/home/kath/Desktop/Intel-536/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/home/kath/Desktop/Intel-536/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/kath/Desktop/Intel-536/coredrv'
2.6.17-10-generic
Failed to build driver

I have tried being root but it makes no difference.  The modem is being sold as GNU/Linux compatible, the box even has Linux and TUX on it!

I must get this working, this machine is for my mother, to get her off Windows XP.

Please help if you can.

Thanks in advance,
Diesel1.

---

### Post by Matchless on 2006-12-10
Hi,
    Kozimodo I am not sure if I can help here, as I have never tried on the k7 kernel and only on the generic one.

diesel1 just a few comments, but you may have already done that. You must have the linux-header installed. Then always use a cleanly extracted folder from the intel-536-2.56.76.0.21 09 2006.tgz. If it fails and you want to redo delete and use a new one. In actual fact at this moment I am on Edgy logged in via the Intel536ep, so it does work.

---

### Post by diesel1 on 2006-12-12
Hi Matchless,

I do have the prerequisites installed.

I just noticed this thread....

[http://www.ubuntuforums.org/showthread.php?t=284222&highlight=intel+536](http://www.ubuntuforums.org/showthread.php?t=284222&highlight=intel+536)

which also points to the driver package you mention, I believe it is patched for 536EP or Ubuntu kernel (?), this should surely be done already by Ubuntu developers.

Anyhow, thanks for the reply and hopefully it will solve my problem!


Diesel1.

---

### Post by pellgarlic on 2006-12-14
hi matchless, thanks for your guide.

i had previously installed my intel 536ep modem in breezy and dapper, having had to edit a file that prevented the boot scripts being created correctly, but have so far been unsuccessful in getting it to work with edgy. i have been getting similar errors to  kozimodo and diesel1, ending with "failed to build driver". i'm pretty sure i've got everything installed that i need, but i'll double-check when i get home.

i have a question though - the link you provided for the modem drivers appears ostensibly to be for a file on technion's site, but the hyperlink actually goes to intel's site. is this intentional? if not, which driver do you recommend? the intel one? (Intel-536EP-4.71.tgz - which i have tried and can't get to work) or the technion one? (intel-536EP-2.56.76.0_21_09_2006.tgz - which i have downloaded to test out)?

cheers, pellgarlic.

---

### Post by Matchless on 2006-12-15
> **pellgarlic said:**
> 
i have a question though - the link you provided for the modem drivers appears ostensibly to be for a file on technion's site, but the hyperlink actually goes to intel's site. is this intentional? if not, which driver do you recommend? the intel one? (Intel-536EP-4.71.tgz - which i have tried and can't get to work) or the technion one? (intel-536EP-2.56.76.0_21_09_2006.tgz - which i have downloaded to test out)?

Thanks for pointing this out. The link to the Intel site was the old one for the drivers that worked right up to Dapper, but the link on the linmodem site is the correct driver for Edgy. I have fixed this now and hope no-one was inconvenienced by my error.

---

### Post by diesel1 on 2006-12-17
Hi Matchless,

Can I just add this...
# Create /dev/modem symlink 
 KERNEL=="ttyLTM[0-9]*", SYMLINK+="modem" 
 KERNEL=="536ep0", SYMLINK+="modem" 

to /etc/udev/rules.d/60-symlinks.rules, under the bit about modem links?

BTW my driver has built now. :)

Thanks again,
Diesel1.

---

### Post by pellgarlic on 2006-12-18
at last! got my modem working using the driver from the technion site. although it wouldn't detect the distribution correctly, and was refusing to install the boot scripts, until i edited the boot_inst file to get around it :)

---

### Post by Matchless on 2006-12-23
> **diesel1 said:**
> Hi Matchless,

Can I just add this...
# Create /dev/modem symlink 
 KERNEL=="ttyLTM[0-9]*", SYMLINK+="modem" 
 KERNEL=="536ep0", SYMLINK+="modem" 

to /etc/udev/rules.d/60-symlinks.rules, under the bit about modem links?

BTW my driver has built now. :)

Thanks again,
Diesel1.
Diesel1,
           Yes, that is the correct way to do it in edgy and should work. Sorry my typo again, 20-symlinks.rules should be 60-symlinks.rules. Have fixed the howto - Thanks for the pointer

---

### Post by diesel1 on 2006-12-23
Hi all,

I have the modem recognized in kppp, and can query it etc. but the only response is 'NO DIALTONE'.

I have trawled through the threads but can't see an answer.

Thanks in advance, Diesel1.

---

### Post by Matchless on 2006-12-24
Hi diesel1,
              A couple of things you can try here. Firstly uncheck "Wait for dial tone" under the modem tab in Kppp and try again. Then as per my own personal experience, Kppp is a complicated and very unstable program to get going at times and can really frustrate you. Rather configure wvdial and test it. Then install gnome-ppp (yes it works in Kubuntu and you can rename it!) It uses wvdial as a backend and is much more stable, but lacks some of Kppp's features
I am presently writing this, logged in on Kubuntu latest upgrades and Intel536ep using gnome-ppp as dialler.
Good luck you are on the verge.

---

### Post by diesel1 on 2006-12-24
Hi Matchless,

I did set-up wvdial as per the wiki, including not waiting for a dial tone but then I get 'NO CARRIER'.

KPPP seems to work just fine.

I can hear some kind of clicking in the modem, so it seems like it is opening the line.

What init string do you use for your modem Matchless?


Thanks for the help, Diesel1.

---

### Post by Matchless on 2006-12-24
Hi,
    Have a look at this it should have all you need: [http://www.ubuntuforums.org/showthread.php?t=307155](http://www.ubuntuforums.org/showthread.php?t=307155)

---

### Post by diesel1 on 2006-12-24
Hi Matchless, that is what I followed lastnight, I will try it again tonight.

Diesel1.

---

### Post by diesel1 on 2006-12-25
Hi Matchless, I tried the thread you wrote, but nothing has changed.

When I  do sudo wvdial this is what I get......

--> wvdial: inter.....
--> Initializing modem
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized
--> Sending: ATDT0845........
ATDT0845.......
NO DIALTONE
--> No dial tone
--> Disconnecting....

This happens with or without 'Carrier Check = no' commented.


Diesel1.

---

### Post by Matchless on 2006-12-29
Hi,
    This is always something that is difficult to solve from a distance and i can only suggest the following and you may already have tried it:
1) make sure there is actually dialtone on the modem, plug a phone in the other port and check.
2) Remove the modem drivers completely and reinstall from scratch
3) Test you modem from a Windows PC, just to prove that it is not faulty.

If the modem is working and dialtone is present i.e. a line is available for the modem to dial out then the drivers are not correct and they should work.
Hope this helps.

---

### Post by diesel1 on 2006-12-29
Thanks for the pointers Matchless, those are the things I already thought to check.

I will start again and see what happens.

Diesel1.

---

### Post by diesel1 on 2007-02-02
Hi, I tried to get the 536ep going but it was a failure.

I did get a Creative Modem Blaster V.92 serial modem which is just fine.

It was also cheaper than the intel pci card which is being sold as a hardware modem when it clearly isn't!.

Anyhow all's well that ends well, just got to train my Mother in using Gnu/Linux now!!!

Simon.

---

### Post by Matchless on 2007-02-03
Glad you got it sorted. Actually an external serial modem is the best way to go. Funny about the intel winmodem, maybe your one is different to the ones I am using. I keep an external as a backup, whenever I upgrade and if/when I get the internal to work I switch over.

---

### Post by directcharitycontribution on 2007-02-05
might want to check this [http://ubuntuforums.org/showthread.php?t=210405&page=6]("http://ubuntuforums.org/showthread.php?t=210405&page=6")

2. Now am I right if I replace "537" instead of "537EP" in the step: "export MODEM_TYPE=537EP" ? because If I enter 537EP, command "make install" fails and it succeeds, if I write only 537.

3. Do I have to follow the initial steps as-it-is (On the first page) or any editing is needed? I have Ubuntu 6.10.

---

### Post by DarkW0lf on 2007-02-14
Matchless:

I have the driver compiled and installed but still not able to use the modem.
In this thread you say to use 60-symlink.rules but the howto says to use 10-local.rules
What should I add to which ?

After that, what do I due to test the driver to make sure it is functioning right.
The only utility I know of to use is the Networking app in the admin menu which I get no response from the modem. What command is issued when I click on those little check boxes ?

I have gotten this modem to work in Breezy/Dapper before (some help from PellGarlic).

---

### Post by pellgarlic on 2007-02-15
someone say my name? :)

i got my 536ep to work in edgy fairly easily - didn't have to do any symlinking or anything. basically, this is what i did:

(first of all, i had all linux-headers and gcc installed already)

i downloaded the technion drivers from [http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-536EP-2.56.76.0_21_09_2006.tgz]("http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-536EP-2.56.76.0_21_09_2006.tgz")
then i extracted the files, then edited the one called "intel536_inst":

where it originally said 

```
# determine distribution:
D=`ls /etc/*-release 2>/dev/null | tr [:upper:] [:lower:]`;

#case $D in
#   *lsb*) D=`sed '/ID=/!d' /etc/lsb-release | tr [:upper:] [:lower:]`;;
#esac

case $D in
   *mandrake*)	DISTRIB_ID=MANDRAKE;;
   *suse*)	DISTRIB_ID=SUSE;;
   *redhat*)	DISTRIB_ID=REDHAT;;
   *redflag*)	DISTRIB_ID=REDFLAG;;
   *conectiva*)	DISTRIB_ID=CONECTIVA;;
   *ubuntu*)	DISTRIB_ID=UBUNTU;;
   *debian*)	DISTRIB_ID=DEBIAN;;
   *slackware*)	DISTRIB_ID=SLACKWARE;;
   *gentoo*)	DISTRIB_ID=GENTOO;;
   *knoppix*)   DISTRIB_ID=KNOPPIX;;
esac
```

i made it say

```
# determine distribution:
D=UBUNTU;

#case $D in
#   *lsb*) D=`sed '/ID=/!d' /etc/lsb-release | tr [:upper:] [:lower:]`;;
#esac

case $D in
   *mandrake*)	DISTRIB_ID=MANDRAKE;;
   *suse*)	DISTRIB_ID=SUSE;;
   *redhat*)	DISTRIB_ID=REDHAT;;
   *redflag*)	DISTRIB_ID=REDFLAG;;
   *conectiva*)	DISTRIB_ID=CONECTIVA;;
   *ubuntu*)	DISTRIB_ID=UBUNTU;;
   *debian*)	DISTRIB_ID=DEBIAN;;
   *slackware*)	DISTRIB_ID=SLACKWARE;;
   *gentoo*)	DISTRIB_ID=GENTOO;;
   *knoppix*)   DISTRIB_ID=KNOPPIX;;
esac
```

i did this because it was giving me errors about not being able to detect the distribution, and i couldn't figure out a more elegant way to fix it :)

then i did:

```
sudo make clean
sudo make 536
sudo make install
```

and i could use "modem0" to connect.

maybe i was just lucky...

---

### Post by DarkW0lf on 2007-02-16
What ? Who's there ?

Did you get a warning about no boot scripts installed at the end of the 'sudo make install' output ?
What is the last four lines of the output that you get from 'sudo make install' ?

What did you do after 'sudo make install' to setup the modem ?

I am not getting any sort of response from that little check box in the Networking dialog. And I am not suree how to use wvdial or pppconfig to check if the driver is installed correctly. What sort of checks do I do now ?

---

### Post by Matchless on 2007-02-17
Try running it with Gnome-ppp. Have a look here:
ttp://ubuntuforums.org/showthread.php?t=307155&highlight=kppp

---

### Post by DarkW0lf on 2007-02-17
That works...

And wvdial is terminated by CTRL+C correct ?
What does the networking dialog use by default if not ppp ?
Just wondering why those dinky little checkboxes don't activate the modem as the help docs say they would, what are they linked to anyway ?

Looks like gnome-ppp is a small download with no deoendency ( or at least the base install has the dependencies covered already ), yeah those are the kind of downloads I like.  :)

I am going to have to get a second 536ep and gnome-ppp for my other machine.
Now if only my ISP supported Linux a little better, it works but they don't much effort into it.

I hope in the next release I don't have to through this rigmarole again  :(

---

### Post by Matchless on 2007-02-18
Glad that worked. I am on edgy kubuntu and use the gnome-ppp full time and some times online for 12 to 24 hours without. The smartlink and lucent winmodems as well as the conexant can be made to work as well. External serial modems work right out of the box without driver installation.

---

### Post by pellgarlic on 2007-02-19
> **Matchless said:**
> Try running it with Gnome-ppp. Have a look here:
ttp://ubuntuforums.org/showthread.php?t=307155&highlight=kppp

second that :) gnome-ppp is what i use too - i always had problems with other methods... sorry, maybe i should have mentioned that in my previous post :)

---

### Post by DarkW0lf on 2007-03-02
Yeah pell that could have helped :P
Something I'll have to keep in mind for future releases.
I kept a copy of the driver packageg and gnome-ppp on my usb bangle.
Will be real handy 'when' I ween my relatives off Windows :)

---

### Post by DarkW0lf on 2007-05-06
Anyone still here :)

Do I need to recompile or re-'install' the module for feisty ?
Or will the existing build still work. help.ubunutu dialup howto doesn't mention 7.04

---

### Post by jdogzilla on 2007-05-07
Hello, I'm trying to compile the 537EP secure driver in feisty and am getting the error below.  ANy suggestions on what I can do to fix this? 

   Module precompile check
   Current running kernel is: 2.6.20-15-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.20-15-generic
make[1]: Entering directory `/tmp/intel-537EP_secure-2.60.80.1/coredrv'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/tmp/intel-537EP_secure-2.60.80.1/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/intel-537EP_secure-2.60.80.1/coredrv/coredrv.o
/tmp/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:842:39: error: macro "DECLARE_WORK" passed 3 arguments, but takes just 2
/tmp/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:842: warning: data definition has no type or storage class
/tmp/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:842: warning: type defaults to âintâ in declaration of âDECLARE_WORKâ
/tmp/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:843:37: error: macro "DECLARE_WORK" passed 3 arguments, but takes just 2
/tmp/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:843: warning: data definition has no type or storage class
/tmp/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:843: warning: type defaults to âintâ in declaration of âDECLARE_WORKâ
/tmp/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function âwake_up_interruptible_persistReadQâ:
/tmp/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:857: error: âwait_wqâ undeclared (first use in this function)
/tmp/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:857: error: (Each undeclared identifier is reported only once
/tmp/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:857: error: for each function it appears in.)
/tmp/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function âinterruptible_sleep_on_timeout_persistReadQâ:
/tmp/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:891: error: âwait_wq2â undeclared (first use in this function)
make[3]: *** [/tmp/intel-537EP_secure-2.60.80.1/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/tmp/intel-537EP_secure-2.60.80.1/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [537core_26] Error 2
make[1]: Leaving directory `/tmp/intel-537EP_secure-2.60.80.1/coredrv'
2.6.20-15-generic
Failed to build driver

---

### Post by pellgarlic on 2007-05-07
@darkwolf - any time you install a new kernel (i.e. like when you upgrade to feisty, you'll get a new kernel) you'll have to recompile the driver - the previous one was compiled against a different kernel, so won't work (at least in my experience).

@jdogzilla - are you running the compile as "sudo" ?

---

### Post by jdogzilla on 2007-05-08
Yes, I am compiling as root

---

### Post by Matchless on 2007-05-08
> **jdogzilla said:**
> Hello, I'm trying to compile the 537EP secure driver in feisty and am getting the error below.  ANy suggestions on what I can do to fix this? 

Hi,
   I have not used the intel modem and have since upgraded to Feisty. There seems to be a new driver at [http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.0_07_05_2007.tgz](http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.0_07_05_2007.tgz) 
See if this works and let us know
Thanks

---

### Post by DarkW0lf on 2007-05-09
Thanks Pell I didn't know feisty had a new kernel, guess I should have figured.
But there isn't a new package right ? The same package can be used it just needs to be recompiled right ?

---

### Post by jdogzilla on 2007-05-10
Nope ... compiling as root with the new driver fails with the following:

2.6.20-15-generic
make[1]: Entering directory `/intel-537EP_secure-2.60.80.0/coredrv'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/intel-537EP_secure-2.60.80.0/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /intel-537EP_secure-2.60.80.0/coredrv/coredrv.o
  CC [M]  /intel-537EP_secure-2.60.80.0/coredrv/clmmain.o
/intel-537EP_secure-2.60.80.0/coredrv/clmmain.c:86: error: expected &#8216;)&#8217; before &#8216;(&#8217; token
make[3]: *** [/intel-537EP_secure-2.60.80.0/coredrv/clmmain.o] Error 1
make[2]: *** [_module_/intel-537EP_secure-2.60.80.0/coredrv] Error 2
....

2.6.20-15-generic
Failed to build drive

---

### Post by Matchless on 2007-05-11
Have a look at this [https://bugs.launchpad.net/ubuntu/+bug/98756](https://bugs.launchpad.net/ubuntu/+bug/98756) it may be bad news. Also search for any threads/posts by Chuckman on the Intel 537ep, I recall him doing quite a bit of problem solving, but not sure if any was on Feisty. I unfortunately cannot test as I 
have moved to another modem that is the same as my laptop on feisty. Please keep the thread alive with the outcome as others will be interested as well. 
Also have a look at this [http://www.goitexpert.com/entry.cfm?entry=Windows-Vista-Hardware-Compatibility-List](http://www.goitexpert.com/entry.cfm?entry=Windows-Vista-Hardware-Compatibility-List)
**56K  Modems **[LIST]
[*]Intel 537EP - No Vista drivers available from Intel. Can manually force installation of an XP driver for this modem and modem will function, however, the blue screen of death will appear on every shutdown of Vista as there is an error with IntelC52.sys.[/LIST]Thanks in advance.
Edit: This looks promising, see chuckmans thread: [http://ubuntuforums.org/showthread.php?t=210405&page=8](http://ubuntuforums.org/showthread.php?t=210405&page=8)

---

### Post by DarkW0lf on 2007-05-12
[http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/](http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/)

Has drivers with recent dates but I have no knowledge if these are the correctly needed packages.
Anyone seen any sort of 'official' statement as to which packages contain the correct driver.

I have the 536 chipset, the bug report you posted mentions 537 instead. Is it the same issue with both ?

---

### Post by DarkW0lf on 2007-05-20
intel-536EP-2.56.76.0_23_02_2007.tgz

I have downloaded and built this package on a feisty machine and didn't have a problem with the steps as there are currently with the HOWTO. However that machine doesn't have the modem installed in it, I only tried building the package to make sure it would build and install.

I don't know if that is the latest, most up to date package or not but it does mean that at least one of them works from the linmodem site.

I don't know if I'll update this machine to feisty yet and try. I want to get my widescreen monitor correct and I don't want to lose modem functionality before then. Though these packages may work.

---

### Post by Sepero on 2007-06-12
PrePackaged Binary Driver for Intel 536:
[http://ubuntuforums.org/showthread.php?t=471503](http://ubuntuforums.org/showthread.php?t=471503)

---

### Post by Matchless on 2007-06-14
Thanks, if anyone tries the packaged drivers please post results so that others can take note as I am not using the Intel at the moment and cannot test.
Thanks again.

---

### Post by Sepero on 2007-06-14
> **Matchless said:**
> Thanks, if anyone tries the packaged drivers please post results so that others can take note as I am not using the Intel at the moment and cannot test.
Thanks again.Absolutely, and please yes.
Currently I have tested it on my system, but that is obviously not enough testing for wide use.
I'm also considering putting out a driver for Ubuntu 6.06 (dapper?). (And possibly in the future for gutsy.)

In the case anything might go wrong, I have included a quite few help files in the package.
/usr/share/doc/intel536ep-feisty

---

### Post by DarkW0lf on 2008-06-15
Has anyone compiled or used prepackaged binaries in Hardy ?

I can't get the driver to build or use the last one I built in Fiesty (I think I don't recall rebuilding for Gutsy).

-- 
Well I see new code at the linmodems site, so I'll try again and rebuild.

---

### Post by DarkW0lf on 2008-06-28
Well the issue was with sudo getting screwed up.

All is good and can compile new code.

---

