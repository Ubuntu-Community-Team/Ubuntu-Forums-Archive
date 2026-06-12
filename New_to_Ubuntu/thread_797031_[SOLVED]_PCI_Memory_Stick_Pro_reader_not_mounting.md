---
title: "[SOLVED] PCI Memory Stick Pro reader not mounting"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by BandD on 2008-05-16
I'm running Hardy and I have a built in memory card reader in a Vaio FS620:

```
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
```

that does not automatically mount when I insert a memory stick.  It worked in Gutsy, so I know it is possible to get this reader working under Linux.

It's as if the system just doesn't respond in any way to the presnse of the card.  But it does show up in dmsg:

```
[  444.127132] tifm_core: MemoryStick card detected in socket 0:1
[  444.059432] tifm0 : demand removing card from socket 0:1
```

I can't find the device in /dev or /media.  Something is lost in translation and the event is not passed onto the OS somewhere along the line.

Any help is greatly appreciated!

---

### Post by BandD on 2008-05-16
After more poking around, I came across this link [http://hardware4linux.info/component/16042/]("http://hardware4linux.info/component/16042/") which addresses my card reader.  It states that the tifm_7xx1 module supports this card.

I did lsmod | grep tifm* and got this:

```
bandd@bandd-laptop:~$ lsmod | grep tifm*
tifm_sd                12936  0 
mmc_core               51460  1 tifm_sd
tifm_7xx1               8576  0 
tifm_core              11012  2 tifm_sd,tifm_7xx1
```

So it looks like the modules are there.  What is going on?

I also noticed that going to System--> Preferences--> Removable Drives and Media doesn't have a "Storage" tab in Hardy, but did in Gutsy.

---

### Post by BandD on 2008-05-17
I found this info on the [tifm wiki]("http://openfacts.berlios.de/index-en.phtml?title=TI%20FlashMedia%20xx12%2Fxx21%20driver"):

> Progress
Version 0.6 of the driver is included with stock 2.6.19 release of the linux kernel. Version 0.8 is available in two subversions for 2.6.20 and 2.6.21 kernels and should be used as a replacement for the shipped (and quite unfortunately, buggy) one. It is merged into main kernel, as of version 2.6.22.

Get them here: [http://developer.berlios.de/project/showfiles.php?group_id=5510](http://developer.berlios.de/project/showfiles.php?group_id=5510).

Alternatively, you may consider looking at project's SVN: (alpha quality - [http://svn.berlios.de/wsvn/tifmxx/trunk/driver/?rev=0&sc=0](http://svn.berlios.de/wsvn/tifmxx/trunk/driver/?rev=0&sc=0)).

Driver is implemented using several modules:

    * tifm_core - serves as "bus" driver for the adapters and cards
    * tifm_7xx1 - "host" adapter for the pci device in question
    * tifm_sd - driver for MMC/SD cards (registers itself as mmc_host under kernel's mmc subsystem) 

Currently in development:

    * tifm_ms - driver for MemoryStick cards (beta). This driver is not very useful without higher level MemoryStick protocol drivers. These are found in the same svn repository. Their current status:
          o memstick - card identification driver (beta)
          o ms_block - legacy MemoryStick storage support (alpha)
          o mspro_block - MemoryStick Pro storage support (beta, has some problems)

The main page can be found [here.]("http://developer.berlios.de/projects/tifmxx")
Perhaps this is the issue.  Though I don't understand why it worked in Gutsy...

---

### Post by BandD on 2008-05-17
After a day of searching through posts, bug reports, and blogs, I found a fix!

It comes from this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557")


Type these commands into the terminal one at a time:
```
svn co -r155 http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/
cd driver/
wget http://www.tu-chemnitz.de/~sweh/tifm_ms.patch
patch -p0 < tifm_ms.patch
make
sudo make install
```

It automounts fine and is fully accessible.

---

### Post by brianpeiris on 2008-06-29
Your instructions worked perfectly on my Gateway CX2724 tablet.

```
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Gateway 2000 Unknown device 0281

```

Thank you!

---

### Post by Llewxam on 2008-07-17
well i attempted this on my hp dv6748us and i couldn't get the patch. gave me a 404 not found error. is there any other way to get this? please? been trying FOREVER to get the card reader to mount pro duo cards.

---

### Post by Llewxam on 2008-07-17
> **Llewxam said:**
> well i attempted this on my hp dv6748us and i couldn't get the patch. gave me a 404 not found error. is there any other way to get this? please? been trying FOREVER to get the card reader to mount pro duo cards.

to correct, the error i had was with this: 

```
wget http://www.tu-chemnitz.de/~sweh/tifm_ms.patch
```

says it's not available. anyone know where else i can get that?

---

### Post by clarembutler on 2008-07-19
[http://www.tu-chemnitz.de/~sweh/tifm_ms.patch](http://www.tu-chemnitz.de/~sweh/tifm_ms.patch)  still unavailable.  Anybody know where it has moved to?

---

### Post by BandD on 2008-07-20
I still have it saved on my computer so I'll attach it here.  Note: This is not my patch...it is the patch originally found at [http://www.tu-chemnitz.de/~sweh/tifm_ms.patch](http://www.tu-chemnitz.de/~sweh/tifm_ms.patch)

Also, you will need to change the file name from **tifm_ms.txt** to **tifm_ms.patch** (I couldn't upload a .patch file).  It should work...follow the steps a explained above.  Copy this the attached file into the **driver** folder you made earlier.  Then proceed.

---

### Post by Llewxam on 2008-07-20
thanks so much. installed. sadly it didn't help. still won't mount the card. unless i gotta restart or do something with the modules which i haven't yet it still won't mount. :(

---

### Post by m.rooch on 2008-09-17
I installed the driver mentioned above. but device name (DEVNAME) is not appear inside /dev. i don't see tifm0 or memstick0.

please help me.

---

### Post by MissingLink on 2008-10-04
Tried BandD's solution. Everything installed but still doesn't show up :( I've been looking for a fix for ages :( Any suggestions?

---

### Post by tonsai on 2009-05-08
I'm running Ubuntu 9.04 - the Jaunty Jackalope on a HPNC6320 and I'm having the same problems as you guys.
 
I've tried to install the patch but not haveing much luck. What I am doing is copying the tifm_ms.patch file to my desktop and then running the patch command from the terminal prompt. Which in turn brings up an error saying it cannot find file to patch! 
 
Now I'm guessing it is becuase I am in the wrong folder to run the patch. Can anyone tell which folder I should run the patch in. I've tried doing a search of the filesystem for tifm_ms.c but cannot find it anywhere.

---

### Post by sikemo on 2009-05-11
I copied the file to /home/(username)/driver and it appeared to patch ok.

Then when I typed "make", I got the following:

echo /home/sikemo/driver
/home/sikemo/driver
make -C /lib/modules/2.6.28-11-generic/build M=/home/sikemo/driver
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  LD      /home/sikemo/driver/built-in.o
  CC [M]  /home/sikemo/driver/memstick.o
In file included from /home/sikemo/driver/memstick.c:15:
/home/sikemo/driver/linux/memstick.h:279: error: field ‘cdev’ has incomplete type
/home/sikemo/driver/memstick.c: In function ‘memstick_uevent’:
/home/sikemo/driver/memstick.c:71: warning: passing argument 1 of ‘add_uevent_var’ from incompatible pointer type
/home/sikemo/driver/memstick.c:71: warning: passing argument 2 of ‘add_uevent_var’ makes pointer from integer without a cast
/home/sikemo/driver/memstick.c:74: warning: passing argument 1 of ‘add_uevent_var’ from incompatible pointer type
/home/sikemo/driver/memstick.c:74: warning: passing argument 2 of ‘add_uevent_var’ makes pointer from integer without a cast
/home/sikemo/driver/memstick.c:77: warning: passing argument 1 of ‘add_uevent_var’ from incompatible pointer type
/home/sikemo/driver/memstick.c:77: warning: passing argument 2 of ‘add_uevent_var’ makes pointer from integer without a cast
/home/sikemo/driver/memstick.c: At top level:
/home/sikemo/driver/memstick.c:195: warning: initialization from incompatible pointer type
/home/sikemo/driver/memstick.c: In function ‘memstick_free’:
/home/sikemo/driver/memstick.c:204: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/sikemo/driver/memstick.c:204: warning: initialization from incompatible pointer type
/home/sikemo/driver/memstick.c: At top level:
/home/sikemo/driver/memstick.c:211: error: unknown field ‘release’ specified in initializer
/home/sikemo/driver/memstick.c:212: warning: initialization from incompatible pointer type
/home/sikemo/driver/memstick.c: In function ‘memstick_alloc_host’:
/home/sikemo/driver/memstick.c:509: error: implicit declaration of function ‘class_device_initialize’
/home/sikemo/driver/memstick.c: In function ‘memstick_add_host’:
/home/sikemo/driver/memstick.c:535: error: implicit declaration of function ‘class_device_add’
/home/sikemo/driver/memstick.c: In function ‘memstick_remove_host’:
/home/sikemo/driver/memstick.c:566: error: implicit declaration of function ‘class_device_del’
/home/sikemo/driver/memstick.c: In function ‘memstick_free_host’:
/home/sikemo/driver/memstick.c:577: error: implicit declaration of function ‘class_device_put’
make[2]: *** [/home/sikemo/driver/memstick.o] Error 1
make[1]: *** [_module_/home/sikemo/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2
sikemo@Mike-Laptop:~/driver$ sudo make install
mkdir -p /lib/modules/2.6.28-11-generic
install -c -m 644 tifm_ms.ko memstick.ko mspro_block.ko /lib/modules/2.6.28-11-generic/kernel/drivers/misc/
install: cannot stat `tifm_ms.ko': No such file or directory
install: cannot stat `memstick.ko': No such file or directory
install: cannot stat `mspro_block.ko': No such file or directory
make: *** [install] Error 1

Still no luck. I am also using Jaunty...

---

### Post by pulpo88 on 2009-05-11
Last year I was able to get this working under Hardy with the instructions described here.  I have a Vaio PCG-7L1L.  However it does not work under Jaunty.

It's because the source we're downloading here (not the patch) relies on a deprecated struct "class_device" which was removed from the kernel some time between 2.6.24 and 2.6.28.

So it seems the thing to do is find the latest source for the memorystick driver, i.e. source that works on 2.6.28-11, then update the patch as needed.

---

### Post by pulpo88 on 2009-05-11
Ok, I've got this working in Jaunty 9.04, kernel 2.6.28-11-generic.  Vaio PCG-7L1L, MS Pro Duo.

Good news is you don't need a patch.  Bad news is you still have to do a compile.

What happened is that the driver linked to in this thread has been merged into the kernel (under drivers/memstick).  The old driver source is unmaintained and no longer compiles against the latest kernels.  BUT, the new driver source is not enabled in the default Jaunty kernel build!  Why?  Perhaps because it's tagged in the Linux kernel (upstream) as EXPERIMENTAL so the Ubuntu folks didn't want to include it.  (Maybe they should since this is not obscure hardware, but that's a separate conversation.)

To fix this,

1. Download the latest linux kernel source:
 sudo apt-get build-dep linux-image-`uname -r`
 sudo apt-get source linux-image-`uname -r`
 cd linux-`uname -r`
2. Add "CONFIG_MEMSTICK=m" to debian/config/i386/config
3. Build it (this builds the whole kernel actually):
 AUTOBUILD=1 NOEXTRAS=1 skipabi=true fakeroot debian/rules binary-generic
4. Install the whole kernel if you want, or just copy what you need:
 sudo cp -r debian/linux-image-`uname -r`/lib/modules/`uname-r`/kernel/drivers/memstick /lib/modules/`uname -r`/kernel/drivers/
5. sudo depmod -a

Insert your card and it should mount automatically.  No reboot needed.

dmesg says:
 tifm_core: MemoryStick card detected in socket 0:1
 mspblk0: p1

---

### Post by decaren on 2009-05-11
I can't get past the

```
sudo apt-get source linux-image-`uname -r`
```

I get the following output

```
sudo: cannot get working directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'linux' packaging is maintained in the 'Git' version control system at:
http://kernel.ubuntu.com/git-repos/ubuntu/ubuntu-jaunty.git
Need to get 74.0MB of source archives.
Err http://archive.ubuntu.com jaunty/main linux 2.6.28-11.42 (dsc)
  Could not open file linux_2.6.28-11.42.dsc - open (2 No such file or directory) [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com jaunty/main linux 2.6.28-11.42 (tar)
  Could not open file linux_2.6.28.orig.tar.gz - open (2 No such file or directory) [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com jaunty/main linux 2.6.28-11.42 (diff)
  Could not open file linux_2.6.28-11.42.diff.gz - open (2 No such file or directory) [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.28-11.42.dsc  Could not open file linux_2.6.28-11.42.dsc - open (2 No such file or directory) [IP: 91.189.88.40 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.28.orig.tar.gz  Could not open file linux_2.6.28.orig.tar.gz - open (2 No such file or directory) [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.28-11.42.diff.gz  Could not open file linux_2.6.28-11.42.diff.gz - open (2 No such file or directory) [IP: 91.189.88.45 80]
E: Failed to fetch some archives.
```

Do I need to add a repo or something.  I've activated the source repo in Synaptic Package Manager and reload plus did a sudo apt-get update.  Please help

---

### Post by sikemo on 2009-05-12
pulpo88: could you elaborate further on steps 2 and 3?

Thanks!

---

### Post by decaren on 2009-05-12
For some reason it's working now.  Nevermind :)

---

### Post by decaren on 2009-05-12
Wow, I just totally didn't pay attention.  I compiled the kernel after modifying the config file...under i386.  I'm running amd64.  And here we go again.  News to come in about an hour.

---

### Post by decaren on 2009-05-12
Works great!!!  I did have to reboot even after the depmod -a command, but hey.  It works.  Thanks much pulp.:guitar:

---

### Post by tonsai on 2009-05-12
-

---

### Post by tonsai on 2009-05-13
ok, followed your instruction but now all i get is :
 
tifm_core: MemoryStick card detected in socket 0:0
 
any help, much appreciated

---

### Post by sikemo on 2009-05-13
tonsai,

Can you help me with regards to how you completed steps 2 and 3 of the above instructions?

Thanks!

---

### Post by tonsai on 2009-05-14
hi sikemo,
 
Step 2
====
I added this line:
     
CONFIG_MEMSTICK=m
 
to
     /home/tonsai/linnux-2.6.28/debian/config/i386/config
 
Step3
====
then opened a terminal and entered at the command line
 
AUTOBUILD=1 NOEXTRAS=1 skipabi=true fakeroot debian/rules binary-generic
 
Hope that helps.

---

### Post by tonsai on 2009-05-14
> **pulpo88 said:**
> 3. Build it (this builds the whole kernel actually):
AUTOBUILD=1 NOEXTRAS=1 skipabi=true fakeroot debian/rules binary-generic
4. Install the whole kernel if you want, or just copy what you need:
sudo cp -r debian/linux-image-`uname -r`/lib/modules/`uname-r`/kernel/drivers/memstick /lib/modules/`uname -r`/kernel/drivers/

 
Hi puplo88, in step 4 you mention:
 
     'Install the whole kernel if you want, or just copy what you need'
 
if you just copy what you need, does that mean you can skip step 3?

---

### Post by sikemo on 2009-05-14
Thanks tonsai,

Now when I attempt to compile I get:

debian/rules binary-generic
/usr/bin/fakeroot: line 176: debian/rules: No such file or directory

Additionally, I can't change directories to linux-'uname -r'

?

---

### Post by tonsai on 2009-05-15
make sure when you type linux-'uname - r' you use the sloping single apostrophe near the number 1 on your key board (top left)
 
so `uname -r` and not 'uname -r'
 
you can test by typing:
 
```
echo `uname -r` 
```
 
at the terminal prompt.

---

### Post by sikemo on 2009-05-15
that's it... I never would have seen that!

---

### Post by taz2781 on 2009-05-25
Can someone be more specific whit the instructions....

---

### Post by BandD on 2009-05-25
So will we have to do this everytime there is a kernel update shipped in 9.04?

---

### Post by taz2781 on 2009-05-27
when i go to the 4 step look what happen...

```
amoulier@Anonimo:~/linux-2.6.28-11-generic$ sudo cp -r debian/linux-image-`uname -r`/lib/modules/`uname-r`/kernel/drivers/memstick /lib/modules/`uname -r`/kernel/drivers/
bash: uname-r: command not found
cp: cannot stat `debian/linux-image-2.6.28-11-generic/lib/modules//kernel/drivers/memstick': No such file or directory

```

---

### Post by sapmemailek on 2009-05-29
> **taz2781 said:**
> when i go to the 4 step look what happen...

```
amoulier@Anonimo:~/linux-2.6.28-11-generic$ sudo cp -r debian/linux-image-`uname -r`/lib/modules/`uname-r`/kernel/drivers/memstick /lib/modules/`uname -r`/kernel/drivers/
bash: uname-r: command not found
cp: cannot stat `debian/linux-image-2.6.28-11-generic/lib/modules//kernel/drivers/memstick': No such file or directory

```

It is just a mistype in the guide.
Correct `uname-r` to `uname -r` and it will work!

---

### Post by taz2781 on 2009-05-30
Thanks for the help... and all. Now i got my PCI Memory Stick Pro working like a dream..

---

### Post by sapmemailek on 2009-06-01
Hi everyone!

I've just made a little shell script, that will set up everything:
(Before you run it you should have fakeroot installed:$ sudo apt-get install fakeroot)
```
#!/bin/sh
if [ "$1" = "" ]; then
echo "You haven't give me the computer's architecture name e.g. for Intel: i386 , for AMD64: amd64"
return
fi
cd tmp_kernel_files && echo "I need to be runned in a directory where is no tmp_kernel_files named subdirectory" && return
echo "Creating temporary directory: ./tmp_kernel_files"
#0.) Creating temporary directory: ./tmp_kernel_files
mkdir tmp_kernel_files
cd tmp_kernel_files
#1.) Download the latest linux kernel source:
apt-get build-dep linux-image-`uname -r`
apt-get source linux-image-`uname -r`
cd linux-`uname -r` || cd linux-`eval "uname -r" | cut -f1 -d-`
#2.) Add "CONFIG_MEMSTICK=m" to debian/config/i386/config
echo CONFIG_MEMSTICK=m >> debian/config/$1/config || return
#3.) Build the whole kernel actually:
AUTOBUILD=1 NOEXTRAS=1 skipabi=true fakeroot debian/rules binary-generic
#4.) Copy the generated Memory Stick driver to the system kernel:
cp -r debian/linux-image-`uname -r`/lib/modules/`uname -r`/kernel/drivers/memstick /lib/modules/`uname -r`/kernel/drivers/
#5.) Apply changes to the system:
depmod -a
#6.) Clean up temporary files
cd ..
cd ..
rm -r -f tmp_kernel_files
echo "Temporary directory: ./tmp_kernel_files deleted"

```You should just copy and paste it to a blank text file, then save it as MemoryStick.sh
After that you should give runnable permissions for it:$ chmod 755 MemoryStick.sh
Now you can run it:$ sudo ./MemoryStick.sh i386 
(If you use AMD based system just write amd64 instead of i386)

This script will create a temporary directory (tmp_kernel_files) where you've started it from.
Then will download the recent kernel's source (about 70 MB), and configure it for the Memory Stick driver. 
After that you will be asked about additional settings on which parts of the driver should be installed.
Now it will compile the whole kernel - it will take about 1 hour on a typical computer.
Finally will copy the compiled driver into the system kernel, apply changes to your system and clean up temporary files.

Voila - your Memory Stick reader is working. (No restart needed.)

Note: If the script don't seem to work, you should enable "Source code" at System \ Administration \ Software Sources

---

### Post by baucha_linux on 2009-06-10
I confirm that the instructions mentioned here worked for me. Now my memory stick is detected in Vaio VGN-NR160E.. thanks a lot guys.. great job...:D

---

### Post by baucha_linux on 2009-06-11
I updated my kernel to 2.6.30 today and again my memory stick is not detected :(

anyone tried this solution with 2.6.30 kernel?? will it work?

---

### Post by metalgamer on 2009-06-11
> **pulpo88 said:**
> 
To fix this,

1. Download the latest linux kernel source:
 sudo apt-get build-dep linux-image-`uname -r`
 sudo apt-get source linux-image-`uname -r`
 cd linux-`uname -r`

I have run both the apt-get's successfully but after completed, I am unable to change directory. I have copy and pasted directly from this thread. I get a "file or directory not found" error.

Any ideas?

---

### Post by BandD on 2009-06-12
can you run the command
```
ls ~
```

---

### Post by sapmemailek on 2009-06-14
> **metalgamer said:**
> I have run both the apt-get's successfully but after completed, I am unable to change directory. I have copy and pasted directly from this thread. I get a "file or directory not found" error.

Any ideas?

Just try my script ;-)

Othervise use: cd linux-`eval "uname -r" | cut -f1 -d-`

I think it should work for newer kernel versions also, until they finalize this driver, then no more patch will be needed!

---

### Post by Adriaan S on 2009-07-20
Hi

I tried the script but it doesn't work for me. I get next output:

```

adriaan@adriaan-laptop ~/Bureaublad $ sudo ./MemoryStick.sh i386
cd: 6: can't cd to tmp_kernel_files
Creating temporary directory: ./tmp_kernel_files
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
E: Uw bronnenlijst (/etc/apt/sources.list) dient minstens 1 bron-URI te bevatten
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
E: Uw bronnenlijst (/etc/apt/sources.list) dient minstens 1 bron-URI te bevatten
cd: 14: can't cd to linux-2.6.28-11-generic
cd: 14: can't cd to linux-2.6.28
./MemoryStick.sh: 16: cannot create debian/config/i386/config: Directory nonexistent
```

any clues?

---

### Post by baucha_linux on 2009-09-15
I have a new and easier solution for anyone wanting to solve the problem mentioned in this thread.

What I did was compiled 'memory stick' driver module in 2.6.28.11-15.49 kernel and used it in 2.6.31 kernel and it worked :) So the easier solution I think is just to extract and copy the module I have attached below to /lib/modules/`uname -r`/kernel/drivers/ (`uname -r` = your kernel number). [the whole 'memstick' folder has to be copied].

Please note that I use amd64 (64 bit) kernel. So I dont think this attached file will work for i386 (32 bit) kernel. Anyone who use 32 bit kernel can post the driver module here so that others with 32 bit kernel can use them.

I hope this will save a whole lot of time and trouble to anyone wishing to enable memorystick driver module as you dont need to compile the whole kernel. All you hav to do is just extract and copy.

Cheers!!

---

### Post by softnavigator on 2009-10-04
> **Adriaan S said:**
> Hi

I tried the script but it doesn't work for me. I get next output:

```

adriaan@adriaan-laptop ~/Bureaublad $ sudo ./MemoryStick.sh i386
cd: 6: can't cd to tmp_kernel_files
Creating temporary directory: ./tmp_kernel_files
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
E: Uw bronnenlijst (/etc/apt/sources.list) dient minstens 1 bron-URI te bevatten
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
E: Uw bronnenlijst (/etc/apt/sources.list) dient minstens 1 bron-URI te bevatten
cd: 14: can't cd to linux-2.6.28-11-generic
cd: 14: can't cd to linux-2.6.28
./MemoryStick.sh: 16: cannot create debian/config/i386/config: Directory nonexistent
```

any clues?

Sorry my English. :)
I have this output too, but i find solution.
You must do next step by step
```

sudo apt-get build-dep linux-image-`uname -r`

```
```

sudo apt-get source linux-image-`uname -r`

```
```

cd linux-`uname -r`

```
or if it get you error
```

cd linux-`eval "uname -r" | cut -f1 -d-`

```
if you have architecture i386 
```

sudo gedit debian.master/config/i386/config

```
or if you have architecture amd64
```

sudo gedit debian.master/config/amd64/config

```
you must find next line:

# CONFIG_MEMSTICK is not set

erase it and past next line:

CONFIG_MEMSTICK=m

save and close gedit

after it do next
```

sudo AUTOBUILD=1 NOEXTRAS=1 skipabi=true fakeroot debian/rules binary-generic

```

you must answer for some questions, answer "m" or "y"(if you can)

after it kernel is compiled (about 1 hour)

after end of process
```

sudo cp -r debian/linux-image-`uname -r`/lib/modules/`uname -r`/kernel/drivers/memstick /lib/modules/`uname -r`/kernel/drivers/

```
and
```

sudo depmod -a

```

It's work for my VAIO VGN-CR25S
I hope this help somebody

---

### Post by sapmemailek on 2009-10-09
> **baucha_linux said:**
> I have a new and easier solution for anyone wanting to solve the problem mentioned in this thread.

What I did was compiled 'memory stick' driver module in 2.6.28.11-15.49 kernel and used it in 2.6.31 kernel and it worked :) So the easier solution I think is just to extract and copy the module I have attached below to /lib/modules/`uname -r`/kernel/drivers/ (`uname -r` = your kernel number). [the whole 'memstick' folder has to be copied].

Please note that I use amd64 (64 bit) kernel. So I dont think this attached file will work for i386 (32 bit) kernel. Anyone who use 32 bit kernel can post the driver module here so that others with 32 bit kernel can use them.

I hope this will save a whole lot of time and trouble to anyone wishing to enable memorystick driver module as you dont need to compile the whole kernel. All you hav to do is just extract and copy.

Cheers!!

Here is my i386 (32 bit) version of the memstick kernel module!
Hope it also works! 
Somebody who has i386 architecture, please tell me if succeed or not!

---

### Post by btechcs on 2009-10-24
working with the 32 bit files. Many thanks.

Details:

$ uname -r;date;pwd
2.6.28-15-generic
Sat Oct 24 17:44:08 IST 2009
/lib/modules/2.6.28-15-generic/kernel/drivers

---

### Post by LewRockwell on 2009-10-25
We will be starting a dedicated thread in the Absolute Beginner Talk area regarding flash media but thought you could start with this:

[http://wiki.laptop.org/go/How_to_Damage_a_FLASH_Storage_Device](http://wiki.laptop.org/go/How_to_Damage_a_FLASH_Storage_Device)

[http://elm-chan.org/docs/mmc/mmc_e.html](http://elm-chan.org/docs/mmc/mmc_e.html)

[http://en.wikipedia.org/wiki/Secure_Digital](http://en.wikipedia.org/wiki/Secure_Digital)



Not sure yet what title and tag combination will produce the most effective search results but we'll probably use a tag of mmcblk0 at least


Here's the new thread:

[http://ubuntuforums.org/showthread.php?t=1300716](http://ubuntuforums.org/showthread.php?t=1300716)

.

---

### Post by Guilo on 2009-10-25
Tried 64 bit files from baucha_linux and it works great. 

What have you done : have you patched the module or just used older ones meaning there culd be a regression in the kernel ?

However, I hope this will be included in 9.10.

Thank you

EDIT : Not working perfectly in fact. After removing the card, reinserting won't make a dev to be mounted.

---

### Post by Sunships on 2009-10-31
Softnavigator's fix worked for me. Sony Vaio FS550, running 9.04. Thanks dude!

---

### Post by btechcs on 2009-11-01
It works by default in karmic. Cheers. :popcorn:

---

### Post by chingis on 2010-07-10
**sapmemailek**, works great on 10.04
kernel - 2.6.32-23-generic (I have Sony Vaio VGN-N31ZR)
thx everybody

---

### Post by patelch.rn on 2010-09-21
I am extremely new to ubuntu and have 10.0.4  installed as of this morning. Going through this thread, I have tried and tried, with no success. I am trying to copy some files into the memstick drivers folder but it tells me :error: permission denied." How do I fix this and allow myself to copy the files to the location? I have made myself the administrator on my logon account. Any help would be appreciated.

---

### Post by woofti on 2011-03-12
Thank you BandD, very helpful of you.

That's the second Ubuntu peripheral success I've had in one day.

Linux Rocks! Ubuntu Forums Rock! You all rock! That's Ubuntu.

---

