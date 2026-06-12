---
title: "HOWTO: Syncing Smartphones with SynCE &amp; Multisync"
date: 2005-11-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Stormx on 2005-11-04
[SIZE="7"]**NOTICE:**[/SIZE]
This thread is **rubbish**. It won't work with any kernel version other than the one I used here. Its only of historical interest. Theres a 99% chance it won't work if you follow it. 

Since I wrote this, an excellent wiki has been started. Use it instead:

[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)















**Notes:** This is my first How-To, and I do hope it helps people struggling with SynCE / Multisync and devices that are troublesome. The guide comes from a few places. Firstly, the [Pocket PC Syncing Guide](http://ubuntuforums.org/showthread.php?t=30936), [Kernel Compilation Guide](http://ubuntuforums.org/showthread.php?t=85064), [SynCE How-To](http://synce.sourceforge.net/synce/howto.php) and of course the fantastic Ubuntu support channel! The guide is aimed at 2.6 kernels (it won't work otherwise)! Throughout the How-To I will use the term "device". This can refer to any phone or device listed below

**This guide is *very* unpredictable** because it is very hardware-dependant. You may need to take some different steps to make it work on your system. I can barely get this to work on this system alone, so this guide should only really be treated as guidelines than exact steps to take

[CENTER]**----------------------------------------------**[/CENTER]

**Works with:** Orange SPV, SPV e100 and SPV e200
**Should Work With:** i-Mate Smartphone, i-Mate Smartphone 2, Qtek 7070, Qtek 8010, Qtek 8080, Motorola MPx200, Orange c500

[CENTER]**----------------------------------------------**[/CENTER]

**Before you start:**
If you are used to using a windows program to "Sync" your phone/device and it is not listed above, have a look at the [Pocket PC Syncing Guide](http://ubuntuforums.org/showthread.php?t=30936).

[CENTER]**----------------------------------------------**[/CENTER]

**Finding out where the device is mounted**
This step is option; if you know where your device is mounted, you don't need to do this
If you don't know where your device is mounted, unplug the device (take it out its cradle) and run

```
ls /dev > /tmp/before
```
Now plug in your device
```
ls /dev > /tmp/after
diff /tmp/before /tmp/after

```

You should get an output like:

```

648a649
> ttyUSB0

```
Its the **ttyUSB0** which is important! This is where the device is mounted when plugged in. Make a note of this, and if you get problems later (for example, when installing synce or running synce-serial-configure) try using this info!

[CENTER]**----------------------------------------------**[/CENTER]

**Lets get going!**
Close down what you aren't using, including any open terminals. Unplug the device from its cradle/lead. Open Terminal!
```

sudo apt-get install librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisync-plugin synce-serial coreutils libc6 gcc-3.4 gcc linux-tree linux-headers-386

```
If prompted to install any other packages, do it! You need all of these!

**If prompted to give data for the SynCE package, stick with the default, unless you have a reason not to**

**Note: Users of PPro, Celeron, PII / III / IV should replace "linux-headers-386" with "linux-headers-686"**

```

cd /usr/src
sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
cd ~
wget http://www.dython.net/z/hosted/stormx/kernel-2.6-driver-new.tar.gz
sudo tar -xvf kernel-2.6-driver-new.tar.gz
cd kernel-2.6-driver
sudo make
sudo rmmod ipaq
modprobe usbserial
sudo insmod ./ipaq.ko

```

If you get problems in the first 3 lines, leave a post! I will try and fix!
If you get problems with the 5th line, its my fault. I've taken the file off my webserver.
If you get problems with the 6th line, make sure you have all the right untarring/gzipping packages installed
If you get problems with the 8th line, leave a post with the error/output!
If you get something like "ERROR: Module ipaq does not exist in /proc/modules" on the 9th, ignore it. It doesn't matter
If you get problems on the 10th or 11th, leave a message with the error!

[CENTER]**----------------------------------------------**[/CENTER]

**Time to test! PLUG IN YOUR DEVICE**

```

sudo synce-serial-config ttyUSB0
dccm
sudo synce-serial-start
--WAIT FOR A COUPLE OF SECONDS--
synce-pstatus

```

If you get "synce-serial-config was unable to find a character device named "ttyUSB0" ", make sure the phone lead/cradle is plugged into the first USB slot (if it isn't, try changing the 0 to 1, etc)
If you get "synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred", run "sudo synce-serial-abort", and try to repeat the process above. Try and wait between each command, it helped for me. If you still can't get it to work, leave a post!

Hopefully, you'll get an output of info on your device! If you don't, stop here. Otherwise continue. Make sure we are still in ~/kernel-2.6-driver

```

sudo make install

```

That should install the new driver for good! Now lets continue to set up multisync!

```

synce-matchmaker create 1

```

If you get an error, ignore it, so long as you have "Partnership was successfully created" at the end of the output. If you don't try changing "1" to "2"

```

multisync

```

In multisync, create a new partnership between SynCE(Top plugin) and Evolution (Bottom Plugin). Make sure you already have an account in evolution, though! Try pressing "Sync" and watch the contacts section of evolution. If nothing happens, press the "Resync" button (You may need to unhide it, look through the menus). If still nothing, something is up. Leave a comment!

[CENTER]**----------------------------------------------**[/CENTER]
**Exploring the device**

```

wget ftp://chpujol.ath.cx/pub/Ubuntu/Packages/Synce-Gnome/synce-gnomevfs_0.9.0-2_i386.deb ftp://chpujol.ath.cx/pub/Ubuntu/Packages/Synce-Gnome/synce-software-manager_0.9.0-2_i386.deb ftp://chpujol.ath.cx/pub/Ubuntu/Packages/Synce-Gnome/synce-trayicon_0.9.0-2_i386.deb 
sudo dpkg -i synce-gnomevfs_0.9.0-2_i386.deb synce-software-manager_0.9.0-2_i386.deb synce-trayicon_0.9.0-2_i386.deb
sudo ln -s /usr/lib/libgtop-2.0.so.5 /usr/lib/libgtop-2.0.so.2
synce-trayicon

```

You should be able to explore the device now! Look in your tray for the new synce icon, right click > Explore with File manager (Thanks to Jehu for this section)

[CENTER]**----------------------------------------------**[/CENTER]

**Help/Support**
[SynCE USB How-To](http://synce.sourceforge.net/synce/howto.php)
[SynCE USB Debug instructions](http://synce.sourceforge.net/synce/usb_linux_debug.php)
[HOWTO: Pocket PC Syncing with Evolution (ubuntuforums)](http://ubuntuforums.org/showthread.php?t=30936)
[HOWTO: Kernel Compilation for Newbies (ubuntuforums)](http://ubuntuforums.org/showthread.php?t=85064) (we don't actually compile the kernel, we just need it's source for the driver)

I hope this was in any way useful for people who struggled with SynCE and a device above. I know I did! If something doesn't work, please leave a comment or PM me!

---

### Post by rickmans on 2005-11-05
I got the following error:

root@rickubuntu:~/kernel-2.6-driver # synce-serial-start

synce-serial-start is now waiting for your device to connect

root@rickubuntu:~/kernel-2.6-driver # synce-pstatus
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred

---

### Post by rickmans on 2005-11-05
Okay I found out that my previous problem was due the fact to run that as root. Now I have got this problem:

sudo synce-serial-config ttyUSB0

ERROR:

synce-serial-config was unable to find a character device named "ttyUSB0"

Run "synce-serial-config --help" to get help.

---

### Post by Stormx on 2005-11-05
Make sure your device is plugged into the first USB slot, ttyUSB0 (if it isn't, try changing the "0" to the correct slot number), and also attached to the lead/cradel

**EDIT:** I've added a "Finding out where your device is mounted" section. Have a look at that

---

### Post by Jehu on 2005-12-27
Hi,

thank you for posting an solution.

I've still the problem: the USB-Device (MDA III) disconnect/reconnet every second. Output in /var/log/messages:
```
Dec 27 15:21:19 localhost kernel: [4295181.301000] usb 4-5.2: PocketPC PDA converter now attached to ttyUSB0
Dec 27 15:21:22 localhost kernel: [4295184.206000] usb 4-5.2: USB disconnect, address 15
Dec 27 15:21:22 localhost kernel: [4295184.208000] PocketPC PDA ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Dec 27 15:21:22 localhost kernel: [4295184.209000] ipaq 4-5.2:1.0: device disconnected
Dec 27 15:21:25 localhost kernel: [4295187.149000] usb 4-5.2: new full speed USB device using ehci_hcd and address 16
Dec 27 15:21:25 localhost kernel: [4295187.196000] ipaq 4-5.2:1.0: PocketPC PDA converter detected
Dec 27 15:21:25 localhost kernel: [4295187.199000] usb 4-5.2: PocketPC PDA converter now attached to ttyUSB0
Dec 27 15:21:28 localhost kernel: [4295190.094000] usb 4-5.2: USB disconnect, address 16
Dec 27 15:21:28 localhost kernel: [4295190.095000] PocketPC PDA ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Dec 27 15:21:28 localhost kernel: [4295190.097000] ipaq 4-5.2:1.0: device disconnected

```

Any Ideas to resolve this?

So long
Jehu

---

### Post by Jehu on 2005-12-27
Ok, now (after very much trys) the Device is connected.
So why this dis/connect-Problem?

EDIT:
Its now possible to connect the PDA!

If you want to user the synce-trayicon and a File-Explorer, download and install the packages from:
[ftp://chpujol.ath.cx/pub/Ubuntu/Packages/Synce-Gnome/](ftp://chpujol.ath.cx/pub/Ubuntu/Packages/Synce-Gnome/)

Now set the following symlink:
sudo ln -s /usr/lib/libgtop-2.0.so.5 /usr/lib/libgtop-2.0.so.2

Start the tryicon
```
synce-tryicon
```

Now you can explore your PDA by using the new icon in the panel.

So long
Jehu

---

### Post by Stormx on 2006-01-02
>DeleteMePlease<

---

### Post by Stormx on 2006-01-02
Thanks for that. I added that to the main how-to with the wget commands. It works perfectly for me, too. I can see it all fine =)

---

### Post by jerrek71 on 2006-01-04
Trying to download the kernel-2.6-driver.tar.gz gives me the following text/html file;

Array
(
    [req] => kernel-2.6-driver-new.tar.gz
)
lol

Which I suspect is entirely not what I need to be using ;)

Presumably this file will be used to build a mod-ipaq that talks to the SPV as that's the only step that I can't do and I don't work... Which is a shame :)

If you know how to Sync a Nokia 6630 I'd be interested too - I've tried everything I can find on the web!

Cheers for the HOWTO - I've no doubt once the 'bug' is fixed on that webserver that everything will be fine.

---

### Post by Stormx on 2006-01-09
Awfully Sorry! Hang on!

**EDIT:** Sorry about that. New CMS. I switched the file to another server. Check it =)

---

### Post by Rev. Nathan on 2006-01-10
> nathan@backroom:~/kernel-2.6-driver$ sudo make install
make: *** No rule to make target `ipaq.ko', needed by `install'.  Stop.


Device is found just fine, but then this happens? Help?

---

### Post by Stormx on 2006-01-10
Have you got build-essential installed?

---

### Post by Rev. Nathan on 2006-01-10
[QUOTE=Stormx]Have you got build-essential installed?[/QUOTE]
Yes I do.

---

### Post by Stormx on 2006-01-12
Not sure, then. Sorry!

---

### Post by hbush on 2006-01-14
same case with me  and I have build-essentials installed (without I couldn't run make) I have a qtek 9090, the device is now connected but 
```

LT@LT:~/kernel-2.6-driver$ sudo insmod ./ipaq.ko
insmod: can't read './ipaq.ko': No such file or directory
LT@LT:~/kernel-2.6-driver$ sudo make install
make: *** No rule to make target `ipaq.ko', needed by `install'.  Stop.
LT@LT:~/kernel-2.6-driver$

```

regarding the linux headers I selected 686 linux headers package and installed (not sure if propper way) 
```

LT@LT:~/kernel-2.6-driver$ uname -r
2.6.12-8-386

```

please help. 
thank you guys you are doing great job.

---

### Post by Stormx on 2006-01-17
Very odd. I shall investigate further

EDIT: Its strange, because that file is definately in that directory. I think I'll do the entire how-to myself! See if I can't see whats wrong o.O

---

### Post by henshu70 on 2006-01-31
Thanks for the guide. I got to the step 5:
[B]
wget [http://www.digitaldivergence.net/stormx/kernel-2.6-driver-new.tar.gz](http://www.digitaldivergence.net/stormx/kernel-2.6-driver-new.tar.gz)[/B]

Than I received this error message:

[B]--14:28:17--http://www.digitaldivergence.net/stormx/kernel-2.6-driver-new.tar.gz
           => `kernel-2.6-driver-new.tar.gz'Resolving [www.digitaldivergence.net](www.digitaldivergence.net)... failed: Temporary failure in name resolution.[/B]

Does the link still work?

Thanks

---

### Post by dhanjel on 2006-02-01
I have the same problem with the downloading (same as above as well as the explore software). Anyone got alternative links?

---

### Post by Dandelion on 2006-02-20
We the  kernel-2.6-driver-new.tar.gz file seems to be changed. When I donwload it, I can't untar it. When viewing the file in a text editor this comes out:

> 
452 Policy violation

<!--
Server:       park-01d-sef
IP:           
Host:         
QueryString:  
Path:         
UserAgent:    Wget/1.10
-->


any body all ready found a working file?

---

### Post by Stormx on 2006-02-27
Im sorry. Let me get that file hosted.

---

### Post by Stormx on 2006-02-27
Right, the file is now hosted at:

[http://www.dython.net/z/hosted/stormx/kernel-2.6-driver-new.tar.gz](http://www.dython.net/z/hosted/stormx/kernel-2.6-driver-new.tar.gz)

Its basicly just a modified version of the one found at one of the sources I mentioned in the first post... Taking account of the new kernel directory. Meh. Im sorry. ill get it hosted in a different spot too :)

In the past location, the server got wiped, and the domain was taken by crawlers!

---

### Post by Dandelion on 2006-02-28
thanks!

let's see if i can get it to work now :)

[edit]

well obviously I can't :(

The file untars okay now, but during 

> 
sudo make


I get this error message:
```

dandelion@adam:~/kernel-2.6-driver$ sudo make
ln -sf /usr/src/linux/drivers/usb/serial/usb-serial.h usb-serial.h
ln -sf ipaq.h-2.6.13.3 ipaq.h
cp -p ipaq.c-2.6.13.3 ipaq.c
patch -N -p0 < ipaq-select-endpoints.diff
patching file ipaq.c
Hunk #3 succeeded at 944 (offset 384 lines).
Hunk #4 succeeded at 979 (offset 384 lines).
patch -N -p0 < ipaq-version.diff
patching file ipaq.c
Hunk #1 succeeded at 74 (offset 9 lines).
patch -N -p4 < ipaq-psion-teklogix.diff
patching file ipaq.c
Hunk #1 succeeded at 102 (offset 10 lines).
Hunk #2 succeeded at 118 (offset 10 lines).
Hunk #3 succeeded at 250 (offset 10 lines).
Hunk #4 succeeded at 485 (offset 10 lines).
patch -N -p4 < ipaq-smartphones.diff
patching file ipaq.c
Hunk #1 succeeded at 926 (offset 14 lines).
touch .patched
make -C /lib/modules/2.6.12-10-k7/build SUBDIRS=/home/dandelion/kernel-2.6-driver modules
make: *** /lib/modules/2.6.12-10-k7/build: No such file or directory.  Stop.
make: *** [default] Error 2

```

So there seems to be a problem. 

The next steps:
> 
sudo rmmod ipaq
modprobe usbserial

are no problem, but in the last I get an error:

```

dandelion@adam:~/kernel-2.6-driver$ sudo insmod ./ipaq.ko
insmod: can't read './ipaq.ko': No such file or directory

```

any thoughts on what's happening?

---

### Post by Stormx on 2006-03-04
Strange, because that file *should* be there... hmmm...Try 

sudo insmod ipaq.ko

Im not sure if its a permissions problem... but it shouldn't be. Ack... I am so confused. If you ls -l in that directory, does it show an ipaq.ko file?

---

### Post by bioinfo_dude on 2006-03-04
I tried downloading the from the new site ([http://www.dython.net/z/hosted/storm...ver-new.tar.gz](http://www.dython.net/z/hosted/storm...ver-new.tar.gz)) and found the same problem as Dandelion. :-? 

Stormx thanks for helping out with this: I tried ls -l and ipaq.ko is not in the directory. 

Any suggestions?

---

### Post by Dandelion on 2006-03-05
nope the file is not in the directory.

---

### Post by tseliot on 2006-03-07
This guide has been ported to the Ubuntu Storage Document Facility (UDSF):

[http://doc.gwos.org/index.php/HOWTO:Syncing_Smartphones]("http://doc.gwos.org/index.php/HOWTO:Syncing_Smartphones")

---

### Post by puccaso on 2006-03-13
this is my error outputt
> 
root@jt:/tmp/kernel-2.6-driver# sudo make
ln -sf /usr/src/linux/drivers/usb/serial/usb-serial.h usb-serial.h
ln -sf ipaq.h-2.6.13.3 ipaq.h
cp -p ipaq.c-2.6.13.3 ipaq.c
patch -N -p0 < ipaq-select-endpoints.diff
patching file ipaq.c
Hunk #3 succeeded at 944 (offset 384 lines).
Hunk #4 succeeded at 979 (offset 384 lines).
patch -N -p0 < ipaq-version.diff
patching file ipaq.c
Hunk #1 succeeded at 74 (offset 9 lines).
patch -N -p4 < ipaq-psion-teklogix.diff
patching file ipaq.c
Hunk #1 succeeded at 102 (offset 10 lines).
Hunk #2 succeeded at 118 (offset 10 lines).
Hunk #3 succeeded at 250 (offset 10 lines).
Hunk #4 succeeded at 485 (offset 10 lines).
patch -N -p4 < ipaq-smartphones.diff
patching file ipaq.c
Hunk #1 succeeded at 926 (offset 14 lines).
touch .patched
make -C /lib/modules/2.6.15-18-686/build SUBDIRS=/tmp/kernel-2.6-driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-18-686'
  CC [M]  /tmp/kernel-2.6-driver/ipaq.o
/tmp/kernel-2.6-driver/ipaq.c:564: error: variable ‘ipaq_device’ has initializer but incomplete type
/tmp/kernel-2.6-driver/ipaq.c:565: error: unknown field ‘owner’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:565: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:565: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:566: error: unknown field ‘name’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:566: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:566: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:567: error: unknown field ‘id_table’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:567: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:567: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:568: error: unknown field ‘num_interrupt_in’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:568: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:568: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:569: error: unknown field ‘num_bulk_in’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:569: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:569: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:570: error: unknown field ‘num_bulk_out’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:570: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:570: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:571: error: unknown field ‘num_ports’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:571: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:571: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:572: error: unknown field ‘open’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:572: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:572: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:573: error: unknown field ‘close’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:573: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:573: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:574: error: unknown field ‘attach’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:574: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:574: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:575: error: unknown field ‘shutdown’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:575: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:575: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:576: error: unknown field ‘write’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:576: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:576: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:577: error: unknown field ‘write_room’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:577: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:577: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:578: error: unknown field ‘chars_in_buffer’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:578: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:578: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:579: error: unknown field ‘read_bulk_callback’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:579: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:579: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c:580: error: unknown field ‘write_bulk_callback’ specified in initializer
/tmp/kernel-2.6-driver/ipaq.c:580: warning: excess elements in struct initializer
/tmp/kernel-2.6-driver/ipaq.c:580: warning: (near initialization for ‘ipaq_device’)
/tmp/kernel-2.6-driver/ipaq.c: In function ‘ipaq_init’:
/tmp/kernel-2.6-driver/ipaq.c:941: warning: passing argument 1 of ‘usb_serial_register’ from incompatible pointer type
/tmp/kernel-2.6-driver/ipaq.c:950: error: invalid use of undefined type ‘struct usb_serial_device_type’
/tmp/kernel-2.6-driver/ipaq.c:951: error: invalid use of undefined type ‘struct usb_serial_device_type’
/tmp/kernel-2.6-driver/ipaq.c:952: error: invalid use of undefined type ‘struct usb_serial_device_type’
/tmp/kernel-2.6-driver/ipaq.c:961: warning: passing argument 1 of ‘usb_serial_deregister’ from incompatible pointer type
/tmp/kernel-2.6-driver/ipaq.c: In function ‘ipaq_exit’:
/tmp/kernel-2.6-driver/ipaq.c:970: warning: passing argument 1 of ‘usb_serial_deregister’ from incompatible pointer type
make[2]: *** [/tmp/kernel-2.6-driver/ipaq.o] Error 1
make[1]: *** [_module_/tmp/kernel-2.6-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-18-686'
make: *** [default] Error 2
root@jt:/tmp/kernel-2.6-driver#

---

### Post by diacono on 2006-03-17
Well, first of all many thanks for this thread as I eventually managed to get some files of an SPV C500. I did have some issues though. 

This specific machine is used by 100% newbies, I replaced their owned Windows XP box with ubuntu and the above only works with my login (as a sudoer).

How can I know set it up so that all four users can plugin their phones (two C500's) and automatically mount the device to browse the files? Not really interested on sync at the moment...

Is this possible?

---

### Post by disturbedsaint on 2006-04-17
[QUOTE=puccaso]this is my error outputt[/QUOTE]
For kernels > 2.6.15 you have to use the SVN version of kernel-2.6-module, see:
[http://www.mail-archive.com/synce-devel@lists.sourceforge.net/msg00231.html](http://www.mail-archive.com/synce-devel@lists.sourceforge.net/msg00231.html)

I've just tried it, but unfortunately I didn't get to work.
I still get the error mentioned [here]("http://synce.sourceforge.net/synce/howto.php") (kernel: ipaq.c: ipaq_read_bulk_callback - nonzero read bulk status received: -2). Note it doesn't say -84, but -2.

Maybe we have to use the synce-programs from SVN too?

---

### Post by Bone Down on 2006-04-25
I am getting the following error: 

```
insmod: can't read './ipaq.ko': No such file or directory

```

I will subscribe to this thread in the meantime.

---

### Post by cloakable on 2006-04-26
synce-serial-config wasn't able to find just ttyUSB0, but a direct path (/dev/.static/dev/ttyUSB0) resulted in no error messages.

synce-serial-start went well.

synce-pstatus kept giving me the error "synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred"

Any help?

---

### Post by nrune on 2006-04-30
Well let me add my woes to the list. 

Okay as far as I can tell everything works, except it won't sync/connect.

Output from /var/log/messages
```
Apr 30 20:44:10 localhost kernel: [4432709.501000] usb 1-1: new full speed USB device using uhci_hcd and address 19
Apr 30 20:44:10 localhost kernel: [4432709.643000] usb 1-1: new full speed USB device using uhci_hcd and address 20
Apr 30 20:44:10 localhost kernel: [4432709.785000] usb 1-1: new full speed USB device using uhci_hcd and address 21
Apr 30 20:44:11 localhost kernel: [4432709.990000] ipaq 1-1:1.0: PocketPC PDA converter detected
Apr 30 20:44:11 localhost kernel: [4432709.993000] usb 1-1: PocketPC PDA converter now attached to ttyUSB0
Apr 30 20:44:11 localhost usb.agent[5827]:      ipaq: already loaded
Apr 30 20:44:11 localhost synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Apr 30 20:44:17 localhost synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Apr 30 20:44:17 localhost pppd[5921]: pppd 2.4.3 started by root, uid 0
Apr 30 20:44:18 localhost pppd[5921]: Exit.
```

I see the pocket pc try to connect on the pocket pc screen, but I get nada on the laptop.
 
```
nrune@nrune:/var/log$ synce-pstatus -d3
[synce_info_new:31] unable to open file: /home/nrune/.synce/active_connection
[synce_info_new:31] unable to open file: /home/nrune/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred

```

---

### Post by Stormx on 2006-05-03
Guys I seriously have absolutely *no* clue about this entire thing. All I can say is just take pauses between steps if you get synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred, as for the file not found stuff, i have absolutely no idea, as the file should be there.

I'm about to try and follow my own guide here, actually, after I reinstalled ubuntu.

---

### Post by teejcee on 2006-05-04
I have just got my Xphone_II connected & working....again.  'Lost the first set-up when my system went pear-shaped & had to do a fresh install.
Having gleaned all my knowledge from the excellent how-to's, feedback, etc from within the many threads, it's time for me to give back..............so..........

....How can I help? 

I'm running Breezy on what I believe is a pretty bog-standard Compaq Evo 510 SFF.
I've got the synce-trayicon working with the hotplug system - this is a bit strange though, as when the system boots, it pauses for about 10 seconds at the "starting hotplug" message before proceeding with the remaining boot process without displaying "ok".
I've got Multisync running ok against Evolution, however, I am only interested in syncing my contacts at this stage.

As a starter, a couple of things I've found.....
1.
The "unable to initialize RAPI" etc message.    
The slots available on PDAs have a unique identifier for each. If you do a fresh install of ubuntu, the old slot identifier will be invalid for your new install and you will get that message. 
Do this...  sudo synce-matchmaker replace INDEX ,  where INDEX is the slot number you want to connect to.

2. 
I found it puzzling that my synce log showed that my device was connected when I plugged it in, however the tray icon remained that sinister dark colour that has angered us all...ie it wasn't really connected.
I checked my synce script over & over again and it was fine. Despite everything, the only way to connect was to key in the "sudo synce-serial-start" command. It turned out to be a very simple fix....wrong permissions on my script! Gave it executable, plugged in the phone & Bingo! , the icon turns blue & we're connected. One minor - at this point- change from my first install is that 
I originally had the option to Add/Remove programs enabled on the tray-icon but this time it's not available to me. Maybe someone else has the answer to this one.

So fire away with questions & let's see if I can help others get somewhere.

---

### Post by teejcee on 2006-05-05
[QUOTE=nrune]Well let me add my woes to the list. 

Okay as far as I can tell everything works, except it won't sync/connect.

Output from /var/log/messages
```
Apr 30 20:44:10 localhost kernel: [4432709.501000] usb 1-1: new full speed USB device using uhci_hcd and address 19
Apr 30 20:44:10 localhost kernel: [4432709.643000] usb 1-1: new full speed USB device using uhci_hcd and address 20
Apr 30 20:44:10 localhost kernel: [4432709.785000] usb 1-1: new full speed USB device using uhci_hcd and address 21
Apr 30 20:44:11 localhost kernel: [4432709.990000] ipaq 1-1:1.0: PocketPC PDA converter detected
Apr 30 20:44:11 localhost kernel: [4432709.993000] usb 1-1: PocketPC PDA converter now attached to ttyUSB0
Apr 30 20:44:11 localhost usb.agent[5827]:      ipaq: already loaded
Apr 30 20:44:11 localhost synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Apr 30 20:44:17 localhost synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Apr 30 20:44:17 localhost pppd[5921]: pppd 2.4.3 started by root, uid 0
Apr 30 20:44:18 localhost pppd[5921]: Exit.
```

I see the pocket pc try to connect on the pocket pc screen, but I get nada on the laptop.
 
```
nrune@nrune:/var/log$ synce-pstatus -d3
[synce_info_new:31] unable to open file: /home/nrune/.synce/active_connection
[synce_info_new:31] unable to open file: /home/nrune/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred

```[/QUOTE]


After posting how well I had this running last night, the above problem reared it's ugly head on my system about 4 hours ago!!!

As it turns out it is - somehow - related to the unique identifier I talked about on my previous post...at least it was in my case. 

I found the way around it is to rename your directory ~/.multisync to "whatever" - I chose multisync_old - and re-start the Multisync app.  Of course you'll have lost your synchronization pair/s  but that shouldn't be to much of a problem.

A tip for those sync'ing Evolution contacts.  Create extra folder/s to back up the contact folder/s you're working with.
Select All contacts from the folder you are going to sync with & copy them all to your backup folder. This can save you much pain & frustration.
In case you haven't already noticed, the sync process with Evo is at best, flacky. Sometimes characters are dropped from names and sometimes it will only sync a few contacts, sometimes it even works....so don't take it for granted that because it did ***something***, that all is well...check the data.

---

### Post by raydekok on 2006-05-08
hello i have a ipaq hw6515 and i want it to sync with my dapper kubuntu.
but when i do al the thinks in the howto i get still this

```
raymond@detempel:~$ sudo synce-serial-start
/usr/share/synce/synce-serial-common: line 52: kill: (13450) - Onbekend proces

Error!

synce-serial-start could not find the serial port /dev/ttyUSB0.
Is your Windows CE device really connected?

```

what to do?

---

### Post by teejcee on 2006-05-09
[QUOTE=raydekok]hello i have a ipaq hw6515 and i want it to sync with my dapper kubuntu.
but when i do al the thinks in the howto i get still this

```
raymond@detempel:~$ sudo synce-serial-start
/usr/share/synce/synce-serial-common: line 52: kill: (13450) - Onbekend proces

Error!

synce-serial-start could not find the serial port /dev/ttyUSB0.
Is your Windows CE device really connected?

```

what to do?[/QUOTE]

The first thing I've noticed is that you're running dapper. 
I stand corrected but I believe this thread is aimed at breezy and I have not tried any of this on dapper so I'm not sure of it's relevance.

However, if "sudo synce-serial-start" is not finding /dev/ttyUSB0, what response are you getting if you enter 
"sudo synce-serial-config ttyUSB0"   ????

If you've followed the steps correctly & you're sure ttyUSB0 is the device you are connecting to, you should have returned to you ..
"You can now run synce-serial-start to start a serial connection."

---

### Post by Stormx on 2006-06-13
Thats correct, I haven't tried it in dapper either. I may do sometime.

---

### Post by Ghost|BTFH on 2006-09-03
I too have had massive issues with this. Until I turned off my firewall...

Yeah... ](*,)  don't know how many people this will help, but it made a big difference for me. :)

Cheers,
Ghost|BTFH

---

### Post by flipfone on 2006-09-21
Problem with Line 8 heres the error/output:

jim@jim-desktop:~/kernel-2.6-driver$ sudo make
ln -sf /usr/src/linux/drivers/usb/serial/usb-serial.h usb-serial.h
ln -sf ipaq.h-2.6.13.3 ipaq.h
cp -p ipaq.c-2.6.13.3 ipaq.c
patch -N -p0 < ipaq-select-endpoints.diff
patching file ipaq.c
Hunk #3 succeeded at 944 (offset 384 lines).
Hunk #4 succeeded at 979 (offset 384 lines).
patch -N -p0 < ipaq-version.diff
patching file ipaq.c
Hunk #1 succeeded at 74 (offset 9 lines).
patch -N -p4 < ipaq-psion-teklogix.diff
patching file ipaq.c
Hunk #1 succeeded at 102 (offset 10 lines).
Hunk #2 succeeded at 118 (offset 10 lines).
Hunk #3 succeeded at 250 (offset 10 lines).
Hunk #4 succeeded at 485 (offset 10 lines).
patch -N -p4 < ipaq-smartphones.diff
patching file ipaq.c
Hunk #1 succeeded at 926 (offset 14 lines).
touch .patched
make -C /lib/modules/2.6.15-27-k7/build SUBDIRS=/home/jim/kernel-2.6-driver module                                    s
make: *** /lib/modules/2.6.15-27-k7/build: No such file or directory.  Stop.
make: *** [default] Error 2
jim@jim-desktop:~/kernel-2.6-driver$

---

### Post by jack frost on 2006-10-01
i get as far as.. ack@linux-laptop:~/kernel-2.6-driver$ synce-pstatus
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
jack@linux-laptop:~/kernel-2.6-driver$    

did you find a fix.. i have a mpx200.. I thought the program was Raki..not rapi???

---

### Post by Voyageur on 2006-10-26
I get this error
kingy@SagraT23:/usr/src$ sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2
tar: linux-source-2.6.12.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Any help appreciated

---

### Post by Stormx on 2006-10-26
Probably a different kernel version. Do a ls -l to find it. I HUGELY need to re-write this howto. I'm so sorry everyone who's had this failed. Its such a tricky business getting smartphones to sync...

---

### Post by Voyageur on 2006-10-26
Here we go
kingy@SagraT23:/usr/src$ ls -l
total 8
drwxr-xr-x 19 root root 4096 2006-10-26 23:05 linux-headers-2.6.15-27
drwxr-xr-x  4 root root 4096 2006-10-26 23:05 linux-headers-2.6.15-27-686

---

### Post by dimeotane on 2006-10-28
I was always getting the error: 
synce-pstatus: Unable to initialize RAPI

Couldn't figure it out.... it's because you have to run dccm as the same user synce-serial-start.  None of the examples have included this

the howtos should show

> sudo dccm
> sudo sudo synce-serial-start


also if you have a password set then you need to use

>sudo dccm -p yourpassword

I sure hope the pocketpc support improves.  this was brutal!

---

### Post by cleonII on 2006-12-10
Hi! 
when i connect my device, no /dev/ttyUSBx file is created..
any advice?

thanks!

---

### Post by Blond on 2007-03-15
I'm trying to get this working on Kubuntu

I get the following error:

sudo make
ln -sf /usr/src/linux/drivers/usb/serial/usb-serial.h usb-serial.h
ln -sf ipaq.h-2.6.13.3 ipaq.h
cp -p ipaq.c-2.6.13.3 ipaq.c
patch -N -p0 < ipaq-select-endpoints.diff
patching file ipaq.c
Hunk #3 succeeded at 944 (offset 384 lines).
Hunk #4 succeeded at 979 (offset 384 lines).
patch -N -p0 < ipaq-version.diff
patching file ipaq.c
Hunk #1 succeeded at 74 (offset 9 lines).
patch -N -p4 < ipaq-psion-teklogix.diff
patching file ipaq.c
Hunk #1 succeeded at 102 (offset 10 lines).
Hunk #2 succeeded at 118 (offset 10 lines).
Hunk #3 succeeded at 250 (offset 10 lines).
Hunk #4 succeeded at 485 (offset 10 lines).
patch -N -p4 < ipaq-smartphones.diff
patching file ipaq.c
Hunk #1 succeeded at 926 (offset 14 lines).
touch .patched
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/kernel-2.6-driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /kernel-2.6-driver/ipaq.o
/kernel-2.6-driver/ipaq.c:555: error: unknown field &#8216;owner&#8217; specified in initializer
/kernel-2.6-driver/ipaq.c:555: warning: initialization from incompatible pointer type
/kernel-2.6-driver/ipaq.c:564: error: variable &#8216;ipaq_device&#8217; has initializer but incomplete type
/kernel-2.6-driver/ipaq.c:565: error: unknown field &#8216;owner&#8217; specified in initializer
...
:confused: 

What can I do about this?

---

### Post by eudemus on 2007-04-17
I'm struggling to get my IPAQ to connect.
But I'm not quite sure what the problem is and how far I have succeeded (i.e. which part of the process is failing).

When I do synce-pstatus, I get the good ol':
Unable to initialize RAPI: An unspecified failure has occurred

But when I look in /var/log/messages I find the following, which sounds a bit more encouraging:
Apr 17 21:29:34 localhost kernel: [17186279.088000] usb 1-1: USB disconnect, address 5
Apr 17 21:29:34 localhost kernel: [17186279.088000] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Apr 17 21:29:34 localhost kernel: [17186279.088000] ipaq 1-1:1.0: device disconnected
Apr 17 21:29:35 localhost kernel: [17186280.652000] usb 1-1: new full speed USB device using ohci_hcd and address 6
Apr 17 21:29:35 localhost kernel: [17186280.864000] ipaq 1-1:1.0: PocketPC PDA converter detected
Apr 17 21:29:35 localhost kernel: [17186280.868000] usb 1-1: PocketPC PDA converter now attached to ttyUSB0
Apr 17 21:30:58 localhost synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Apr 17 21:30:58 localhost pppd[8608]: pppd 2.4.4b1 started by root, uid 0
Apr 17 21:30:58 localhost pppd[8608]: Serial connection established.
Apr 17 21:30:58 localhost pppd[8608]: Using interface ppp0
Apr 17 21:30:58 localhost pppd[8608]: Connect: ppp0 <--> /dev/ttyUSB0

So, what am I missing, such that synce-pstatus doesn't report the kind of connection I need?
Help, please?

(I'm running Dapper, and I've an IPAQ HX2750 running Windows Mobile 2003 Premium.)
Cheers
Eudemus

---

### Post by MarkusBE on 2007-04-22
My MPX200 doesen't seem to work as I would like it to.
When I try sudo make, I get the following:

```
sudo make
make: *** No rule to make target `/usr/src/linux/drivers/usb/serial/usb-serial.h', needed by `usb-serial.h'.  Stop.
```

That file is indeed missing in that directory, any advice where to find it?

Thanks!

---

### Post by digitalslave on 2007-05-29
recieve this error:
synce-pstatus: Could not find configuration at path '(Default)'

device is on ttyUSB0
menus come up on the phone showing the connection and it does say authenticated
then it disconnects

cant seem to keep the connection open :(

anyone else with this problem

also on edgy when i plugged my phone in it would open multisynce even though the same thing would happen... after installing the new version pluggin in the phone does nothing with the same connection results :(

---

