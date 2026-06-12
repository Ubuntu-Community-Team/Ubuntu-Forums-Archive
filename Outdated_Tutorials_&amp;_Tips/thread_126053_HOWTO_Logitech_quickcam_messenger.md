---
title: "HOWTO: Logitech quickcam messenger"
date: 2006-02-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Yoriko on 2006-02-05
[b][u]Installing Logitech Quickcam Messenger
Ubuntu Breezy 5.10[/u][/b]

There was an old post by my [Here](http://www.ubuntuforums.org/showthread.php?t=111225).

That wasn't very organised, and I left a few days later for Australia to visit my girlfriend where I was using a windows box and couldn't update, but thats beside the point.

I'll start off with my lsusb + uname -sr;
> zack@penor:~$ uname -sr && lsusb
Linux 2.6.12-10-386
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID **[color=red]046d:08f0[/color]** Logitech, Inc.
Bus 001 Device 002: ID 1690:0215 Askey Computer Corp. [hex]
Bus 001 Device 001: ID 0000:0000

That is my version of the qc messenger. If you have that my instructions should work for you, I don't know about other versions.


**1.** Plug in your logitech quickcam messenger.

**2.** Get the latest driver sources from **[here](http://home.mag.cx/messenger/)** and unpack them somewhere.

**3.** Get the required dependancies (These were all needed from a fresh Breezy install)
```
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install xawtv gcc-3.4
```

**4.** Type into your terminal
```
export CC=gcc-3.4
```
This tells the driver to compile using gcc-3.4 the same as the kernel was compiled with (2.6.12 anyway).

**[color=red]5. This is the only way I know to do this; Potentially unsafe. If there is another way please tell me**[/color]
```
sudo passwd
```
to change the root password (you will need this during install).

**6.** cd to the directory you extracted the driver source too (in the same terminal you did #4 with) and run quickcam.sh.
```
./quickcam.sh
```
Type in the root password when it asks, and ignore all error messages. **Even the one about not finding a camera!**

**7.** When its done compiling, and the script has finished executing run
```
sudo modprobe quickcam
```
Now check your camera out in camorama, or gnomemeeting or something similar.

If all has gone well, continue;

*Credits to [Maol62](http://www.ubuntuforums.org/member.php?u=31754)*

This will set the camera to run during startup of your system.

**8.** run
```
sudo touch /etc/init.d/quickcam && sudo chmod 755 /etc/init.d/quickcam
```

**9.** If in gnome:
```
sudo gedit /etc/init.d/quickcam
```
If in KDE:
```
sudo kate /etc/init.d/quickcam
```
paste into the file.
```
#! /bin/sh 
# /etc/init.d/quickcam: reload the Logitech Quickcam Messenger driver. rmmod quickcam
modprobe quickcam
```
Save and close.

**10.** Create a symbolic link so the script is launched at boot;
```
sudo ln -s /etc/init.d/quickcam /etc/rcS.d/S99quickcam
```

**11. Done! Enjoy using your quickcam messenger!**


--------------------------------------------------------
I hope this is easier to understand than previous thread. Credits to Maol62 and emcompass for thier help. (and anyone i forgot :P).

footnote: I recently got gaim 2.0beta2 CVS to compile with --enable-vv. Yet i can't find vv anywhere within it, I've read on the forums that it works with msn for beta2 when compiled with --enable-vv. Any idea? (I hate tk, so wish(lol pun maybe <_<) amsn didn't use it).

---

### Post by desperado666 on 2006-02-06
What to do if my Latop Monitor is going black when compiling??

---

### Post by Yoriko on 2006-02-06
[QUOTE=desperado666]What to do if my Latop Monitor is going black when compiling??[/QUOTE]

I don't know, I don't use a laptop - Desktop PC. 
Does it go black when compiling any other programs?

---

### Post by desperado666 on 2006-02-06
No.
It does go black while "compiling" Step 6.(Something i could see was patching kernel)
If i press CTRL ALT Backspace and do my login i can work again.

---

### Post by Yoriko on 2006-02-06
I don't know what it could be, What kernel version are you using?

---

### Post by desperado666 on 2006-02-06
2.6.12-10-386

---

### Post by Yoriko on 2006-02-06
Hmm then i don't know why it isn't working;

let's try it without the script.
make sure you have everything needed before continuing;

Enter the directory in the terminal and;
```
make clean && make all
```
If your screen doesn't blank during this compile, then when its done;
```
modprobe videodev
	modprobe usb-uhci
	insmod ./quickcam.ko compatible=3
```
then test if the camera works.

(I based this off the readme, so I don't know if it is right.)

---

### Post by desperado666 on 2006-02-06
Doesnt help me.

After running quickcam.sh my screen goes black again,so i guess it has something to do with the script.

Your described way does not compile something dont know why.

---

### Post by Whoopie on 2006-02-07
Hi,

instead of the init.d script, you could do the following:

Create a file /etc/modprobe.d/quickcam and insert this line:

```
install quickcam modprobe --ignore-install quickcam; rmmod quickcam; modprobe --ignore-install quickcam
```


Best regards,
Whoopie

---

### Post by Princey on 2006-03-08
> Installing Logitech Quickcam Messenger
Ubuntu Breezy 5.10[/u][/b]

There was an old post by my [Here](http://www.ubuntuforums.org/showthread.php?t=111225).

That wasn't very organised, and I left a few days later for Australia to visit my girlfriend where I was using a windows box and couldn't update, but thats beside the point.

I'll start off with my lsusb + uname -sr;

That is my version of the qc messenger. If you have that my instructions should work for you, I don't know about other versions.


**1.** Plug in your logitech quickcam messenger.

**2.** Get the latest driver sources from **[here](http://home.mag.cx/messenger/)** and unpack them somewhere.

**3.** Get the required dependancies (These were all needed from a fresh Breezy install)
```
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install xawtv gcc-3.4
```

I've followed every step of what you said. I indeed have the exact camera that you have and I'm running Kubuntu Breezy. When I reach the "sudo apt-get install xawtv gcc-3.4" line I get the following error:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xawtv

Where do I find xawtv? I've checked in adept, even installed synaptic and both register it as installed. Do I skip that step or what? I'm stuck :-k [-(

---

### Post by ProNoblem on 2006-03-08
[QUOTE=Princey]
[..]
[/QUOTE]
Do you have the universe repository enabled? (because it's in universe)

---

### Post by Princey on 2006-03-08
[QUOTE=ProNoblem]Do you have the universe repository enabled? (because it's in universe)[/QUOTE]


Yes, it is enabled. Here's my sources.list in case I'm wrong:

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main 

# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

# Ubuntu backports project (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

#kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main 

#kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main 

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) breezy main 

# kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) breezy main

---

### Post by i3dmaster on 2006-03-08
I got this error:
```
xawtv -device /dev/video0
This is xawtv-3.94, running on Linux/i686 (2.6.15-17-386)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  63

```

---

### Post by Princey on 2006-03-09
Ok guys, I'm really lost here. I would appreciate if someone read my previous post on the Logitech Webcam issue and give me some guidance. I'm stuck at installing xawtv. Without this I can't go any further. I hate to have to boot to windows or use a windows machine just to use my webcam.

---

### Post by Princey on 2006-03-11
I finally got past that stage but I'm stuck at the step of ./quickcam.sh. Here's what it says:

Using specified C compiler from environment CC=gcc-3.4
./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc-3.4
Warning: gcc missing
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
[!] Some important programs can not be found on default path.
Probably they aren't installed.
You should install them, for example, by using apt-get or rpm.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> 

If I continue hitting enter, to continue at the end, I still don't get anything showing save camorama giving me the error message : "Could not connect to video device (/dev/video0)". I'm pretty certain my camera is working and plugged in. Any ideas?

-------------------------------------------------------------
I re-installed gcc and the error message disappeared but came up with another:

gcc-3.4 version: gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)
gcc version: gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Make version: GNU Make 3.80
Linker version: GNU ld version 2.16.1 Debian GNU/Linux
Kernel compiler: gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)
[!] Kernel compiler and gcc-3.4 seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
        export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> 
______________________________________________________________
I'm certain that I did the export CC=gcc-3.4 command. Is it because of the two gcc versions? What if I remove the version 4, will it affect my system? Any reply would be appreciated.

---

### Post by Princey on 2006-03-11
Success!!!:KS :) After doing modprobe several times and trying the instructions all over again, I finally got it to work. For those wanting my lsusb, here's it:

princey@MCES:~$ lsusb
Bus 002 Device 003: ID 0458:2014 KYE Systems Corp. (Mouse Systems)
Bus 002 Device 002: ID 03f0:0604 Hewlett-Packard DeskJet 840c
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:08f0 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

Now, my next task is to see if I can get my Genius (KYE) scanner to work. That would make me kiss Windows good bye forever. \\:D/

---

### Post by Princey on 2006-03-18
My camera worked fine until this morning. I ran a system upgrade and I noticed that the kernel version went up one number to 2.6.12.18. Ever since then, I get the error message > unable to capture image. I tried unplugging and re-plugging the camera. Rebooted, all without success. Do I need to re-do the entire installation over again or is there something I need to modify to get it working?:confused:

---

### Post by tomtom_in_eire on 2006-03-25
Hi,

Thanks for thi HOWTO, works fine for me!

However, I need to say that on a fresh Dapper install, I needed to install the package build-essential:

```
sudo apt-get install build-essential
```

without it, the driver will simply not compile....

enjoy!

---

### Post by gymsmoke on 2006-04-01
Yoriko~
Thanks for the how to!
I've got a slightly different setup and would love to get this resolved.  If you can point me somewhere to start, I'd really appreciate it.

~$ uname -sr
Linux 2.6.12-10-386

~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:08b0 Logitech, Inc. QuickCam 3000 Pro [pwc]
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 043d:0072 Lexmark International, Inc. X6170 Printer
Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Since the webcam has audio and video, I also show 2 sound cards installed (which has caused me some confusion with getting apps like skype to run).

I'd really like to get the cam working at this point just to test it and see what it can do under Linux.

---

### Post by ottoshafer on 2006-04-11
heres what i have:
kernel version : 2.6.16.1

lsusb:
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:0920 Logitech, Inc. QuickCam Express
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:08a0 Logitech, Inc. QuickCam IM
Bus 001 Device 001: ID 0000:0000

keep in mind that these are 2 different webcams.  I only need to get one of them to work though 

and when i run the quickcam.sh file, i get the following statement:
 
Testing if  is correct.
ls: : No such file or directory
./quickcam.sh: line 699: [: too many arguments
ls: : No such file or directory
ls: : No such file or directory
[!]  major number is .
Usually it should be 81, so there are problems ahead.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->
 
i also get this when i run debug.sh:
FATAL: Module usb not found.
FATAL: Module usb_uhci not found.
FATAL: Module usb_ohci not found.
FATAL: Module modprobe not found.


When i get done, the camera is still undetected.  Any help would be appreciated

---

### Post by Princey on 2006-04-12
[QUOTE=ottoshafer]heres what i have:
kernel version : 2.6.16.1

lsusb:
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:0920 Logitech, Inc. QuickCam Express
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:08a0 Logitech, Inc. QuickCam IM
Bus 001 Device 001: ID 0000:0000

keep in mind that these are 2 different webcams.  I only need to get one of them to work though 

and when i run the quickcam.sh file, i get the following statement:
 
Testing if  is correct.
ls: : No such file or directory
./quickcam.sh: line 699: [: too many arguments
ls: : No such file or directory
ls: : No such file or directory
[!]  major number is .
Usually it should be 81, so there are problems ahead.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->
 
i also get this when i run debug.sh:
FATAL: Module usb not found.
FATAL: Module usb_uhci not found.
FATAL: Module usb_ohci not found.
FATAL: Module modprobe not found.


When i get done, the camera is still undetected.  Any help would be appreciated[/QUOTE]


I'm not the original author of the How To but having had mine set up with a few hitches, I think I have some basic understanding of how things work. You're trying to set up two webcams at the same time, both using the same chipset. Try unplugging one, and run the setup again. Something I've noticed that at times, instead of typing > ./quickcam.sh typing > sudo ./quickcam.sh brings about a better result. I'm not a programmer but at times, I think you need sudo priviledges to compile. (subject to correction). Try the above and let us know what happened.

---

### Post by ottoshafer on 2006-04-12
I was trying one at a time, i was just hoping someone could confirm that one of them worked with the driver.  I think the error is coming when its compiling the driver

---

### Post by Lotherian on 2006-04-14
Ok, I know I am a newbie but I think I am missing some fundamental...

I have followed the giude to point 6. Every step before that one works perfect.

I am trying to write:

./quickcam.sh

And I get this error message:

me@JMyComputer:~/Desktop/gspy-0.1.7$ ./quickcam.sh
bash: ./quickcam.sh: No such file or directory

Can someone point me in the correct direction?

Thanks in advance!

---

### Post by Princey on 2006-04-16
[QUOTE=Lotherian]Ok, I know I am a newbie but I think I am missing some fundamental...

I have followed the giude to point 6. Every step before that one works perfect.

I am trying to write:

./quickcam.sh

And I get this error message:

me@JMyComputer:~/Desktop/gspy-0.1.7$ ./quickcam.sh
bash: ./quickcam.sh: No such file or directory

Can someone point me in the correct direction?

Thanks in advance![/QUOTE]

Did you try > ./quickcam.sh?

---

### Post by Lotherian on 2006-04-17
I manage to fix the problem... downloaded the wrong files...

But now I have a new problem for you experts out there.

If I follow the guide to it´s completion the camera work perfect, in gnommeeting for example. So far so good!

But if I restart the computer the camera stops working. I have to run the entire guide again too make it work. So anyone who can point me in the right direction ones again?

Thanks in advance!

---

### Post by ottoshafer on 2006-04-17
this is the error message i get when trying to compile the driver:

Another round done. Let's now compile the driver, it takes a while.
This step will also clear old unnecessary files from the directory.
Press Ctrl+C to quit, Enter to continue --->

rm -f *.o qcset show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
make -C "/lib/modules/2.6.16.1-num2/build" SUBDIRS="/home/otto/Desktop/qc-expres s" modules V=1 USER_OPT=""
make[1]: Entering directory `/usr/src/linux-2.6.16.1'
mkdir -p /home/otto/Desktop/qc-express/.tmp_versions
make -f scripts/Makefile.build obj=/home/otto/Desktop/qc-express
  gcc -m32 -Wp,-MD,/home/otto/Desktop/qc-express/.qc-driver.o.d  -nostdinc -isys tem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KERNEL__ -Iinclude  -include i nclude/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-st rict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -mso ft-float -mpreferred-stack-boundary=2  -march=athlon -Iinclude/asm-i386/mach-def ault -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL   -DMODULE -D"KB UILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBU ILD_STR(quickcam)" -c -o /home/otto/Desktop/qc-express/.tmp_qc-driver.o /home/ot to/Desktop/qc-express/qc-driver.c
/home/otto/Desktop/qc-express/qc-driver.c:3031: error: unknown field &#8216;owner&#8217; spe cified in initializer
/home/otto/Desktop/qc-express/qc-driver.c:3031: warning: initialization from inc ompatible pointer type
make[2]: *** [/home/otto/Desktop/qc-express/qc-driver.o] Error 1
make[1]: *** [_module_/home/otto/Desktop/qc-express] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.16.1'
make: *** [quickcam.ko] Error 2
ls: quickcam.ko: No such file or directory
[!] Looks like the driver compilation failed.

---

### Post by Princey on 2006-04-18
[QUOTE=Lotherian]I manage to fix the problem... downloaded the wrong files...

But now I have a new problem for you experts out there.

If I follow the guide to it´s completion the camera work perfect, in gnommeeting for example. So far so good!

But if I restart the computer the camera stops working. I have to run the entire guide again too make it work. So anyone who can point me in the right direction ones again?

Thanks in advance![/QUOTE]

Did you follow the two last steps of the guide towards the end (steps #8,9,10) after you tested to see the cam works? These steps enable the cam to work after rebooting.

---

### Post by Princey on 2006-04-18
> **ottoshafer]this is the error message i get when trying to compile the driver:

Another round done. Let's now compile the driver, it takes a while.
This step will also clear old unnecessary files from the directory.
Press Ctrl+C to quit, Enter to continue --->

rm -f *.o qcset show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
make -C "/lib/modules/2.6.16.1-num2/build" SUBDIRS="/home/otto/Desktop/qc-expres s" modules V=1 USER_OPT=""
make[1]: Entering directory `/usr/src/linux-2.6.16.1'
mkdir -p /home/otto/Desktop/qc-express/.tmp_versions
make -f scripts/Makefile.build obj=/home/otto/Desktop/qc-express
  gcc -m32 -Wp,-MD,/home/otto/Desktop/qc-express/.qc-driver.o.d  -nostdinc -isys tem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KERNEL__ -Iinclude  -include i nclude/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-st rict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -mso ft-float -mpreferred-stack-boundary=2  -march=athlon -Iinclude/asm-i386/mach-def ault -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL   -DMODULE -D"KB UILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBU ILD_STR(quickcam)" -c -o /home/otto/Desktop/qc-express/.tmp_qc-driver.o /home/ot to/Desktop/qc-express/qc-driver.c
/home/otto/Desktop/qc-express/qc-driver.c:3031: error: unknown field &#8216 said:**
> : *** [/home/otto/Desktop/qc-express/qc-driver.o] Error 1
make[1]: *** [_module_/home/otto/Desktop/qc-express] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.16.1'
make: *** [quickcam.ko] Error 2
ls: quickcam.ko: No such file or directory
[!] Looks like the driver compilation failed.

Did you follow step 4? > export CC=gcc-3.4. From what I'm reading from your output > /usr/lib/gcc/i486-linux-gnu/4.0.2/include  it's using gcc 4.0.2 and not 3.4. That could be the source of your problem.

---

### Post by ottoshafer on 2006-04-19
i get this after the camera driver is compiled now.

Right now driver is loaded and should be ready to run.
Let's test if user applications can see it, starting with qcset.
Press Ctrl+C to quit, Enter to continue ---> ^[[DTesting if  is correct.
ls: : No such file or directory
./quickcam.sh: line 699: [: too many arguments
ls: : No such file or directory
ls: : No such file or directory
[!]  major number is .
Usually it should be 81, so there are problems ahead.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

any idea what this means?
i also need to know how to change the kernel compiler to gcc 3.4, help with this would be appreciated too

---

### Post by rajan on 2006-04-21
great howto! I've been at this problem for a long time and this finally fixed it. thanks! =D>

---

### Post by galotzas on 2006-04-21
NO works fr me :(

---

### Post by encompass on 2006-04-21
[QUOTE=galotzas]NO works fr me :([/QUOTE]
What is your output from lsusb?

---

### Post by encompass on 2006-04-21
[QUOTE=gymsmoke]Yoriko~
Thanks for the how to!
I've got a slightly different setup and would love to get this resolved.  If you can point me somewhere to start, I'd really appreciate it.

~$ uname -sr
Linux 2.6.12-10-386

~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:08b0 Logitech, Inc. QuickCam 3000 Pro [pwc]
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 043d:0072 Lexmark International, Inc. X6170 Printer
Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Since the webcam has audio and video, I also show 2 sound cards installed (which has caused me some confusion with getting apps like skype to run).

I'd really like to get the cam working at this point just to test it and see what it can do under Linux.[/QUOTE]
if you have tryied this drive and it did not work... I hate to burst your bubble, but the thread is not for you. Sorry, only for messenger.
I have a growing list of lsusb's here...[http://www.slicehaven.com/ubuntu/main_page.html]("http://www.slicehaven.com/ubuntu/main_page.html")
I would keep looking elsewhere in the forums... seems they have gotten alot of success with it.  Mine two has a mic I use the QC Messenger.

---

### Post by ottoshafer on 2006-04-23
How do you change the kernel compilation version?

---

### Post by rajan on 2006-04-24
i'm having the same problem as Lotherian... i rebooted and then i lost the ability to use my webcam. what a tease.... i've rebooted 2x now and it's still not working, and i've done step 8,9,10 as Princey suggested, so i don't know if i need to recompile something every time i use start the comp or not. everything else is the same (webcam, distro, common architecture), but i just get a green screen in gnome meeting. i've even "touched" the /etc/init.d/quickcam file and nothing seems to work. 

EDIT: problem fixed, see solution below.

---

### Post by rajan on 2006-04-24
silly me didn't notice this parallel thread: [http://ubuntuforums.org/showthread.php?t=111225&highlight=logitech](http://ubuntuforums.org/showthread.php?t=111225&highlight=logitech)

it may help some of the problems, but i haven't tried it yet since i'm at work and i don't have root here and my comp at home is off (no sense warming the planet just so i can access the internet in 5 seconds after coming home).

---

### Post by rajan on 2006-04-25
[QUOTE=Yoriko][b][u]Installing Logitech Quickcam Messenger
Ubuntu Breezy 5.10[/u][/b]

**9.** If in gnome:
```
sudo gedit /etc/init.d/quickcam
```
If in KDE:
```
sudo kate /etc/init.d/quickcam
```
paste into the file.
```
#! /bin/sh 
# /etc/init.d/quickcam: reload the Logitech Quickcam Messenger driver. rmmod quickcam
modprobe quickcam
```
Save and close.

[/QUOTE]

as i thought, i hadn't hit "return" between ".... Quickcam Messenger driver." and "rmmod quickcam..." . how i had it previously, the "rmmod quickcam" was commented out and that's why i was getting the green screen. Yoriko, i suggest you change this on the howto so other mistake prone people don't get so confused after they reboot. i repeat my previous acclaim for this howto, and i'd put the hand clappy guy on again, but i don't see him and i don't remember the code. just imagine me clapping if you really want to.

---

### Post by ottoshafer on 2006-04-25
Ok, here is the complete output of my running of the quickcam.sh file. Any help would be greatly appreciated. 

-=- Logitech QuickCam USB camera driver installer -=-
Hello! I am the (hopefully) easy-to-use, fully automated
qc-usb driver installation script.
At the moment, this is experimental, and if it doesn't work,
don't hesitate to quit this with Ctrl+C and install the
driver manually.

The driver is provided in source code form, so it has to be
compiled. This should happen automatically, but it does mean
that there are some steps required before installation.

You also need to know "root" user password to test and
install the driver.

Basically you need only to keep hitting Enter whenever you
see this prompt: --->. Sometimes you're asked root password.
Pay special attention to lines beginning with [!].
It means that some trouble has been detected.

To most important location is the path to your kernel source
or headers. This can be guessed, but you can specify it by
giving it as an argument to this script like this:
./quickcam.sh LINUX_DIR=/usr/src/linux

If you haven't done it yet, now it would be a good moment to
take a look at file README.

Next I'm going to check if you have some important programs installed
and if they and the kernel are of suitable version.
Press Ctrl+C to quit, Enter to continue --->

Using specified C compiler from environment CC=gcc-3.4
./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc-3.4
/usr/bin/gcc
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
/bin/readlink
gcc-3.4 version: gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)
gcc version: gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Make version: GNU Make 3.80
Linker version: GNU ld version 2.16.1 Debian GNU/Linux
Kernel compiler: gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)[!] Kernel compiler and gcc-3.4 seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

Looking for more necessary programs...
Found program /sbin/depmod
Found program /sbin/insmod
Found program /sbin/rmmod
Found program /sbin/modprobe
Found program /bin/mount
Found program /usr/sbin/lsusb
depmod version: module-init-tools 3.2-pre7
insmod version: module-init-tools version 3.2-pre7
rmmod version: module-init-tools version 3.2-pre7
modprobe version: module-init-tools version 3.2-pre7
Checking whether we're root... root
[!] Running script as root.
You shouldn't run this script as root. It should work,
but is unsafe. Please run this as an ordinary user.
When root access is really needed, you will be prompted
for the root password.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

Checking for driver source code...
Checking for write permission...

Previous round done. Now checking if you have kernel source installed.
Press Ctrl+C to quit, Enter to continue --->

Kernel source directory: /lib/modules/2.6.16.1-num2/build
Detected kernel version is 2.6.x.
Kernel version name: 2.6.16.1-num2
Kernel source version code: 132624
Driver file name: quickcam.ko
Module install directory: /lib/modules/2.6.16.1-num2
Driver source directory (PWD): /home/otto/Desktop/qc-usb-messenger-1.2
Kernel source directory (LINUX_DIR): /lib/modules/2.6.16.1-num2/build
Module install directory (MODULE_DIR): /lib/modules/2.6.16.1-num2
Utility install directory (PREFIX): /usr/local
User options (USER_OPT):
Driver file name (use with insmod): quickcam.ko
Kernel version code: 132624

The QuickCam driver requires other drivers from kernel.
I'll now check if those seem to be loaded.
Press Ctrl+C to quit, Enter to continue --->

Modules loaded into the kernel:
videodev uhci_hcd rfcomm l2cap pcmcia firmware_class container ipv6 af_packet pcspkr rtc yenta_socket rsrc_nonstatic pcmcia_core snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc shpchp pci_hotplug amd64_agp sis_agp agpgart nls_cp437 ntfs joydev dm_mod psmouse mousedev parport_pc lp parport md_mod ext3 jbd sis900 mii ehci_hcd ohci_hcd usbcore ide_cd cdrom ide_disk ide_generic sis5513 generic ide_core unix vga16fb vgastate cfbimgblt cfbfillrect cfbcopyarea tileblit font

Next round: let's see if you have a supported QuickCam.
Please plug in your USB camera before continuing.
Press Ctrl+C to quit, Enter to continue --->

I can find the following probably compatible devices:
Bus 001 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express

Another round done. Let's now compile the driver, it takes a while.
This step will also clear old unnecessary files from the directory.
Press Ctrl+C to quit, Enter to continue --->
rm -f *.o qcset input_read show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
cd testquickcam ; make clean
make[1]: Entering directory `/home/otto/Desktop/qc-usb-messenger-1.2/testquickcam'
rm -f testquickcam *~ pic.ppm pic.gif
make[1]: Leaving directory `/home/otto/Desktop/qc-usb-messenger-1.2/testquickcam'
make -C "/lib/modules/2.6.16.1-num2/build" SUBDIRS="/home/otto/Desktop/qc-usb-messenger-1.2" modules V=1 USER_OPT=""
make[1]: Entering directory `/usr/src/linux-2.6.16.1'
mkdir -p /home/otto/Desktop/qc-usb-messenger-1.2/.tmp_versions
make -f scripts/Makefile.build obj=/home/otto/Desktop/qc-usb-messenger-1.2
gcc -m32 -Wp,-MD,/home/otto/Desktop/qc-usb-messenger-1.2/.qc-driver.o.d -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KERNEL__ -Iinclude -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -march=athlon -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)" -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/otto/Desktop/qc-usb-messenger-1.2/.tmp_qc-driver.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-driver.c
/home/otto/Desktop/qc-usb-messenger-1.2/qc-driver.c: In function &#8216;qc_capt_get&#8217;:
/home/otto/Desktop/qc-usb-messenger-1.2/qc-driver.c:2378: warning: &#8216;gn&#8217; may be used uninitialized in this function
/home/otto/Desktop/qc-usb-messenger-1.2/qc-driver.c:2378: warning: &#8216;ex&#8217; may be used uninitialized in this function
gcc -m32 -Wp,-MD,/home/otto/Desktop/qc-usb-messenger-1.2/.qc-vv6450.o.d -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KERNEL__ -Iinclude -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -march=athlon -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_vv6450)" -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/otto/Desktop/qc-usb-messenger-1.2/.tmp_qc-vv6450.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-vv6450.c
gcc -m32 -Wp,-MD,/home/otto/Desktop/qc-usb-messenger-1.2/.qc-formats.o.d -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KERNEL__ -Iinclude -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -march=athlon -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_formats)" -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/otto/Desktop/qc-usb-messenger-1.2/.tmp_qc-formats.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-formats.c
gcc -m32 -Wp,-MD,/home/otto/Desktop/qc-usb-messenger-1.2/.qc-memory.o.d -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KERNEL__ -Iinclude -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -march=athlon -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_memory)" -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/otto/Desktop/qc-usb-messenger-1.2/.tmp_qc-memory.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-memory.c
ld -m elf_i386 -m elf_i386 -r -o /home/otto/Desktop/qc-usb-messenger-1.2/quickcam.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-driver.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-vv6450.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-formats.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-memory.o
Building modules, stage 2.
make -rR -f /usr/src/linux-2.6.16.1/scripts/Makefile.modpost
scripts/mod/modpost -m -a -i /usr/src/linux-2.6.16.1/Module.symvers vmlinux /home/otto/Desktop/qc-usb-messenger-1.2/quickcam.o
gcc -m32 -Wp,-MD,/home/otto/Desktop/qc-usb-messenger-1.2/.quickcam.mod.o.d -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KERNEL__ -Iinclude -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -march=athlon -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(quickcam)" -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -DMODULE -c -o /home/otto/Desktop/qc-usb-messenger-1.2/quickcam.mod.o /home/otto/Desktop/qc-usb-messenger-1.2/quickcam.mod.c
ld -m elf_i386 -m elf_i386 -r -o /home/otto/Desktop/qc-usb-messenger-1.2/quickcam.ko /home/otto/Desktop/qc-usb-messenger-1.2/quickcam.o /home/otto/Desktop/qc-usb-messenger-1.2/quickcam.mod.o
make[1]: Leaving directory `/usr/src/linux-2.6.16.1'
gcc -Wall -O2 -s qcset.c -o qcset -lm
qcset.c: In function &#8216;pnm_open&#8217;:
qcset.c:383: warning: pointer targets in passing argument 1 of &#8216;fopen&#8217; differ in signedness
qcset.c: In function &#8216;main&#8217;:
qcset.c:640: warning: pointer targets in passing argument 1 of &#8216;pnm_open&#8217; differ in signedness
gcc -Wall -O2 -s input_read.c -o input_read
-rw-r--r-- 1 root root 120899 2006-04-24 13:55 quickcam.ko

Now everything should be well and the driver compiled.
Let's then try actually loading the fresh driver and testing
if it works.
Press Ctrl+C to quit, Enter to continue --->

To load the driver, I need to know the root password.
=== Entering root mode ===

I will now try to enable the SysRq key.
If your computer crashes, you can try pressing:
Alt + SysRq + S: Emergency Sync (write everything on hard disk)
Alt + SysRq + U: Unmount all harddisks
Alt + SysRq + B: Reboot system immediately
Press Ctrl+C to quit, Enter to continue --->

Now I finally will try to load the module.
If you're unlucky, your computer might crash right now!!!!
Consider long if you really want to continue.
Press Ctrl+C to quit, Enter to continue --->

You decided to do it, here we go...
=== Leaving root mode ===
The driver detected the following supported cameras:
[!] No cameras detected.
Try unloading and reloading the driver manually with
rmmod quickcam; insmod ./quickcam.ko debug=-1
and then checking whether there are any messages indicating
problems with command
dmesg
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

I will be using , if there are more cameras I'll not test them.
Press Ctrl+C to quit, Enter to continue --->

Testing if is correct.
ls: : No such file or directory
./quickcam.sh: line 699: [: too many arguments
ls: : No such file or directory
ls: : No such file or directory
[!] major number is .
Usually it should be 81, so there are problems ahead.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->


Right now driver is loaded and should be ready to run.
Let's test if user applications can see it, starting with qcset.
Press Ctrl+C to quit, Enter to continue --->

./qcset: can not open /dev/video0 (No such device)
[!] qcset did not found the QuickCam camera
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

If you like, you can quit now and start using the camera -
you have good chances that it works, if no problems were detected.
If you have X Window System running and xawtv installed,
I can now run it automatically for you.
You will then also have opportunity to install the driver permanently.
Press Ctrl+C to quit, Enter to continue --->

Launching xawtv (press q on xawtv window to quit it)...
If the image is not sharp, try focusing it by turning the
wheel around the camera lens.
xawtv -noscale -noxv -c ""
This is xawtv-3.94, running on Linux/i686 (2.6.16.1-num2)
v4l-conf: option requires an argument -- c
usage: v4l-conf [ options ]

options:
-q quiet
-d <dpy> X11 Display [:0.0]
-c <dev> video device [/dev/video0]
-b <n> displays color depth is <n> bpp
-s <n> shift display by <n> bytes
-f query frame buffer device for info
-a <addr> set framebuffer address to <addr>
(in hex, root only, successful autodetect
will overwrite this address)
-1 force v4l API
-2 force v4l2 API
v4l-conf had some trouble, trying to continue anyway
v4l2: open : No such file or directory
v4l2: open : No such file or directory
v4l: open : No such file or directory
no video grabber device available

Well, did it work, did you get a picture?
If you did, you might now want to install the driver
permanently. Just proceed to do that...
Press Ctrl+C to quit, Enter to continue --->

Just an extra warning: the driver (quickcam.ko) and
the utility (qcset) will be now copied into system
directories. If you have already other versions,
they will be overwritten. Verify by giving root password.
=== Entering root mode ===
/usr/bin/install -c -D -m 644 quickcam.ko /lib/modules/2.6.16.1-num2/misc/quickcam.ko
/usr/bin/install -c -D -m 755 qcset /usr/local/bin/qcset
/sbin/depmod -a

=== Leaving root mode ===
Hopefully the driver is now installed and can be loaded
with command
modprobe quickcam
as root. You can put this command into some startup
script to do it always automatically at boot.
The exact location depends on distribution, and this
script is yet too dumb to do this automatically.
Press Ctrl+C to quit, Enter to continue --->
Goodbye...

---

### Post by juicybananahead on 2006-05-13
Thanks very much, I got it working as soon as I was smart enough to realise that I couldn't run it through my USB hub! Here's my lsusb for everyone else's reference:

```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:08f6 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 046d:c03e Logitech, Inc.
Bus 001 Device 003: ID 059f:0621 LaCie, Ltd
Bus 001 Device 002: ID 050d:0237 Belkin Components
Bus 001 Device 001: ID 0000:0000

```

//juicy

---

### Post by encompass on 2006-05-14
Yeah the USB extensions can have a pile of issues.  Not sure why, perhaps it is a power reason, cause my mouse doesn't lightup when it is connected to a hub.
Good job and I will, when exams are over, add your lsusb to my list on the page.  And hey, if you have pictures of the cam, throw them over too. :)

---

### Post by MetalMusicAddict on 2006-05-29
So am I right in thinking that if I go through all this Ill just to have to do it again if I update my kernel?

I just bought a QC Messenger thinking it would work with all the info I'd seen. I'd like a out-of-the-box cam but I dont mind a little work if it will be a final solution.

---

### Post by encompass on 2006-05-29
That's the one disadvantage I see in linux.  Because you will always get a better kernel and your computer will always be improving.  You will have to setup this comstume setting in your kernel every time.
You could do what windows does... and not upgrade the kernel.  Just keep it the same all the time so people that need better hardware support can't do wnything about it.
Lastly, if you don't want to, you don't have to... you don't have to upgrade your kernel.  Some very smart linux people find a stable and powerful kernel they like and don't want to change.
Good question....

---

### Post by MetalMusicAddict on 2006-05-29
Hmm... Then with that could/can you recommend a out-of-the-box webcam? With Dapper I might pin the kernel a little after final if I cant get a cam I like.

---

### Post by simms on 2006-06-05
excellent howto -- thank you!
i can confirm that your directions work perfectly on Dapper Drake (Ubuntu 6.06) as well.  **quickcam.sh** returns many errors, but in the end the driver is compiled and installed correctly.

---

### Post by desperado666 on 2006-06-05
possible to build a nice shiny deb out of it??? I hate recompiling only because i use a new kernel

---

### Post by Rackerz on 2006-06-05
Just amazing, I've tried the howto at least 6 times, and it's finally worked! Thankyou!

---

### Post by sporniket on 2006-06-06
Thank you for the Howto, it worked like a charm for me.

I have a few notes to complement it.

> **Yoriko]lsusb + uname -sr said:**
> 

Check that the corresponding linux-headers package is installed (I installed linux-headers-<kernel version> and linux-headers-<kernel version>-<architecture>)

[QUOTE=Yoriko]
This will set the camera to run during startup of your system. (8, 9, ...)

I put the quickcam module in my /etc/modules file instead of creating an init script, and it works too.

---

### Post by encompass on 2006-06-06
[QUOTE=sporniket]Thank you for the Howto, it worked like a charm for me.
I have a few notes to complement it.
Check that the corresponding linux-headers package is installed (I installed linux-headers-<kernel version> and linux-headers-<kernel version>-<architecture>)
I put the quickcam module in my /etc/modules file instead of creating an init script, and it works too.[/QUOTE]
Thanks for the information... that should help me alot...

---

### Post by _Graven on 2006-06-06
Hey all,

i'm having problems with my quickcam again. It was probably due to the dapper upgrade. Has anyone tried this HOWTO on dapper with success?

EDIT: After running quickcam.sh again it complains about the kernel being compiled with gcc-4. If I set CC=gcc-4.0 the script seems to run "normally", but ```
modprobe quickcam
```
I get...
```
FATAL: Error inserting quickcam (/lib/modules/2.6.15-23-686/misc/quickcam.ko): Invalid module format

```

---

### Post by Rackerz on 2006-06-06
Can somebody help me? The driver installs successfully for me each time, but it just doesn't start the webcam at boot. I added the lines and files so it should start, but it doesn't. Can someone help?

---

### Post by Rackerz on 2006-06-06
Nobody?

---

### Post by terminatorkobold on 2006-06-07
> **Yoriko][b][u]Installing Logitech Quickcam Messenger


**[color=red]5. This is the only way I know to do this said:**
> 
```
sudo passwd
```
to change the root password (you will need this during install).



Hello Yoriko,

I looked at the quickcam.sh file and constated that the command su was used to obtain the administrator privilege when needed. I replaced every instance of su by sudo in the script and saved it. Afterwards when run, the script asked me once my sudo password and then executed nicely without needing to be run in a root account.

Hope it helps.

---

### Post by terminatorkobold on 2006-06-07
[QUOTE=Rackerz]Can somebody help me? The driver installs successfully for me each time, but it just doesn't start the webcam at boot. I added the lines and files so it should start, but it doesn't. Can someone help?[/QUOTE]

Hello Rackerz,

Did you upgrade your kernel after your first installation?
If it is the case you probably need to rerun the script after changing the kernel. Doing this I still had the problem and saw that the script did not replace my old quickcam.ko file with the newly compiled one. I had to delete the /lib/modules/2.6.15-23-386/kernel/drivers/usb/media/quickcam/quickcam.ko file by myself and replace it with the newly created quickcam.ko file. Afterwards everything worked without problems.

---

### Post by Rackerz on 2006-06-07
[QUOTE=terminatorkobold]Hello Rackerz,

Did you upgrade your kernel after your first installation?
If it is the case you probably need to rerun the script after changing the kernel. Doing this I still had the problem and saw that the script did not replace my old quickcam.ko file with the newly compiled one. I had to delete the /lib/modules/2.6.15-23-386/kernel/drivers/usb/media/quickcam/quickcam.ko file by myself and replace it with the newly created quickcam.ko file. Afterwards everything worked without problems.[/QUOTE]

I didn't install a new kernel but I saw a problem in the installer saying it couldn't replace that file. Were would I find the newly created one?

---

### Post by encompass on 2006-06-07
I am making a howto as we speak...
[QUOTE=_Graven]Hey all,

i'm having problems with my quickcam again. It was probably due to the dapper upgrade. Has anyone tried this HOWTO on dapper with success?

EDIT: After running quickcam.sh again it complains about the kernel being compiled with gcc-4. If I set CC=gcc-4.0 the script seems to run "normally", but ```
modprobe quickcam
```
I get...
```
FATAL: Error inserting quickcam (/lib/modules/2.6.15-23-686/misc/quickcam.ko): Invalid module format

```[/QUOTE]

---

### Post by terminatorkobold on 2006-06-09
[QUOTE=Rackerz]I didn't install a new kernel but I saw a problem in the installer saying it couldn't replace that file. Were would I find the newly created one?[/QUOTE]

The new quickcam.ko file is in the same folder as the quickcam.sh file. You have to use sudo to delete the /lib/modules/2.6.15-23-386/kernel/drivers/usb/media/quickcam/quickcam.ko file and then copy the new file to that place. Notice that the 2.6.15-23-386 part oft the file path should be the name of the kernel that you are using. (it comes in the grub booting manager as you start your system)

For the startup part, it is better to add quickcam in your /etc/modules file as indicated by sporniket rather than to use the script given by Yoriko.

---

### Post by encompass on 2006-06-09
> 5. This is the only way I know to do this; Potentially unsafe. If there is another way please tell me
Have you tried
'sudo su'
?

---

### Post by puterboy on 2006-06-16
Well, i tried it the way in the guide, no dice. did a lil research, and all u need to do is

sudo make
sudo make install

let it compile, then

sudo insmod ./quickcam.ko

then it's good. worked for me right away. found it on the [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/) site. i'm using a quickcam messenger

edit: make sure to load it in autoload, cuz it resets after every reboot

---

### Post by _Graven on 2006-06-16
Kudos for the HOWTO!!!!

---

### Post by Rackerz on 2006-07-03
Can somebody help me get the driver to work on boot up?

---

### Post by _Graven on 2006-07-09
> **_Graven said:**
> Hey all,

i'm having problems with my quickcam again. It was probably due to the dapper upgrade. Has anyone tried this HOWTO on dapper with success?

EDIT: After running quickcam.sh again it complains about the kernel being compiled with gcc-4. If I set CC=gcc-4.0 the script seems to run "normally", but ```
modprobe quickcam
```
I get...
```
FATAL: Error inserting quickcam (/lib/modules/2.6.15-23-686/misc/quickcam.ko): Invalid module format

```

Workaround for this one... just use the force switch after running the install script.

```
sudo modprobe -f quickcam
```

I added the same switch to the startup script. xawTV won't start, but camorama will. I've tried using video on aMsn and kopete successfully.

---

### Post by encompass on 2006-07-09
you may want to try the howto made for dapper... not this one for breezy

---

### Post by Rackerz on 2006-07-10
> **encompass said:**
> you may want to try the howto made for dapper... not this one for breezy

I highly recommend you use what encompass posted for Dapper, it works.

---

### Post by detter on 2006-07-13
Im very new to ubuntu and Im trying to get my logitech
to work.  I find the directions a little confusing because
I dont know if they are step by step or they assume that I know
what Im diong.

Thanks  Detter.](*,)

---

### Post by encompass on 2006-07-14
> **detter said:**
> Im very new to ubuntu and Im trying to get my logitech
to work.  I find the directions a little confusing because
I dont know if they are step by step or they assume that I know
what Im diong.

Thanks  Detter.](*,)

Well, I can help you... feel free to use any of my messengers... and I can help you there....
But the steps are pretty strait forward... I tried not leaving anything out to guessing.
The one big mistake everyone makes is they don't check if the camera they REALLY have is the quickcam Messenger.  This howto is only for that.
Hope to help you.

---

### Post by Cris987 on 2006-08-20
rm -f *.o qcset input_read show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
cd testquickcam ; make clean
make[1]: Entering directory `/home/gilbert/Desktop/Installers:Drivers/qc-usb-messenger-1.3/testquickcam'
rm -f testquickcam *~ pic.ppm pic.gif
make[1]: Leaving directory `/home/gilbert/Desktop/Installers:Drivers/qc-usb-messenger-1.3/testquickcam'
make -C "/lib/modules/2.6.17.8/build" SUBDIRS="/home/gilbert/Desktop/Installers:Drivers/qc-usb-messenger-1.3" modules V=1 USER_OPT=""
make[1]: Entering directory `/usr/src/linux-2.6.17.8'
Makefile:1100: *** target pattern contains no `%'.  Stop.
make[1]: Leaving directory `/usr/src/linux-2.6.17.8'
make: *** [quickcam.ko] Error 2
ls: quickcam.ko: No such file or directory
[!] Looks like the driver compilation failed.



Anyone have any idea what's wrong? Thanks.

---

### Post by MissG on 2007-09-01
In case anyone still needs this, here's a debian package that worked for me on kubuntu feisty:
[http://www.mediafire.com/?74udxttccq6](http://www.mediafire.com/?74udxttccq6)

---

### Post by Phophos on 2007-09-14
The following worked for me on Edgy - [http://blog.preshweb.co.uk/2007/05/logitech-quickcam-messenger-under-linux/](http://blog.preshweb.co.uk/2007/05/logitech-quickcam-messenger-under-linux/)

---

### Post by nicjasno on 2007-09-25
Phophos, I get the following error when trying the method in this link:

```
FATAL: Error inserting gspca (/lib/modules/2.6.17-12-386/kernel/drivers/usb/media/gspca.ko): Invalid module format

```

---

### Post by Derviansoul on 2008-03-04
> **Yoriko said:**
> Hmm then i don't know why it isn't working;

let's try it without the script.
make sure you have everything needed before continuing;

Enter the directory in the terminal and;
```
make clean && make all
```
If your screen doesn't blank during this compile, then when its done;
```
modprobe videodev
	modprobe usb-uhci
	insmod ./quickcam.ko compatible=3
```
then test if the camera works.

(I based this off the readme, so I don't know if it is right.)

It was giving me a black screen and i haven't got a laptop!!but using this steps it works now!!
thanks allot:D
But everytime that i restart i have to run to follow the 3 steps above or otherwise i cannot start the webcam, if i follow the steps from 7 to 9 when i restart the computer i can make modprobe quickcam but the camera wont start!!
i have to remove mobprobe quickcam from the /etc/init.d/quickcam or otherwise i cannot even follow the steps above can anyone help me please!!

---

### Post by Plasma_NZ on 2008-03-05
Ok, another novice here...

Am running "Hardy Heron 64bit"

Tried the "make clean && make all " and got the following results..

> rm -f *.o qcset show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
make -C "/lib/modules/2.6.24-11-generic/build" SUBDIRS="/home/nodified/Desktop/qc-usb-0.6.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-11-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (           \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/nodified/Desktop/qc-usb-0.6.6/.tmp_versions ; rm -f /home/nodified/Desktop/qc-usb-0.6.6/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/nodified/Desktop/qc-usb-0.6.6
  gcc -Wp,-MD,/home/nodified/Desktop/qc-usb-0.6.6/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2  -mtune=generic -m64 -mno-red-zone -mcmodel=kernel -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a-time -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -maccumulate-outgoing-args   -fstack-protector -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/nodified/Desktop/qc-usb-0.6.6/.tmp_qc-driver.o /home/nodified/Desktop/qc-usb-0.6.6/qc-driver.c
In file included from /home/nodified/Desktop/qc-usb-0.6.6/qc-driver.c:47:
/home/nodified/Desktop/qc-usb-0.6.6/quickcam.h:129:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:59,
                 from include/linux/videodev.h:15,
                 from /home/nodified/Desktop/qc-usb-0.6.6/quickcam.h:95,
                 from /home/nodified/Desktop/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/nodified/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/home/nodified/Desktop/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/nodified/Desktop/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/nodified/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/nodified/Desktop/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/nodified/Desktop/qc-usb-0.6.6/qc-driver.c: At top level:
/home/nodified/Desktop/qc-usb-0.6.6/qc-driver.c:2998: warning: initialization from incompatible pointer type
/home/nodified/Desktop/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initializer
make[2]: *** [/home/nodified/Desktop/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/nodified/Desktop/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-11-generic'
make: *** [quickcam.ko] Error 2


Any help would be appreciated...

---

### Post by Derviansoul on 2008-03-05
Hello

I tried to use this tutorial but i was getting black screens and i had to restart X after, i managed to make the camera to work following this steps from 

> **Yoriko said:**
> 
```
make clean && make all
```

```
modprobe videodev
	modprobe usb-uhci
	insmod ./quickcam.ko compatible=3
```


but everytime that i restarted the pc the camera wouldn't work if i done all the steps from Yoriko from 7 till 10 yoriko advises us to use sudo all the time but instead of that i use 

```
su
``` and in the quickcam directory i runned
```
 sh quickcam.sh 
``` 
Some of us will say that it's unsafe but the website it self advises to follow this steps logged as root.
this time it didn't ask for any password and i never got any black screen, and i could do all the steps till 10 now the webcam works even i restart the pc.
Sorry if i said something not completly right, but i managed to make it working and i though to explain to other people with the same problem hoping that would work with them aswell!!
regards

---

### Post by c0kit0_2oo7 on 2008-03-18
Oooooh yeeeeahh!! XDD, i dont know what i did wrong the last time xD, but now i have the cam working out :D, thanku :p, this post goes to my bookmarks :P

---

### Post by SATA on 2008-03-30
> **Plasma_NZ said:**
> Ok, another novice here...

Am running "Hardy Heron 64bit"

Tried the "make clean && make all " and got the following results..



Any help would be appreciated...

Im having the exact same problem. But on Hardy 32 bit.

```

rm -f *.o qcset input_read show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
cd testquickcam ; make clean
make[1]: Entering directory `/root/qc-usb-messenger-1.7/testquickcam'
rm -f testquickcam *~ pic.ppm pic.gif
make[1]: Leaving directory `/root/qc-usb-messenger-1.7/testquickcam'
make -C "/lib/modules/2.6.24-12-server/build" SUBDIRS="/root/qc-usb-messenger-1.7" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-12-server'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (            \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /root/qc-usb-messenger-1.7/.tmp_versions ; rm -f /root/qc-usb-messenger-1.7/.tmp_versions/*
make -f scripts/Makefile.build obj=/root/qc-usb-messenger-1.7
  gcc -m32 -Wp,-MD,/root/qc-usb-messenger-1.7/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i686 -mtune=generic -ffreestanding -maccumulate-outgoing-args -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /root/qc-usb-messenger-1.7/.tmp_qc-driver.o /root/qc-usb-messenger-1.7/qc-driver.c
/root/qc-usb-messenger-1.7/qc-driver.c: In function 'qc_int_init':
/root/qc-usb-messenger-1.7/qc-driver.c:850: warning: passing argument 6 of 'usb_fill_int_urb' from incompatible pointer type
/root/qc-usb-messenger-1.7/qc-driver.c: In function 'qc_isoc_start':
/root/qc-usb-messenger-1.7/qc-driver.c:2209: warning: assignment from incompatible pointer type
/root/qc-usb-messenger-1.7/qc-driver.c: At top level:
/root/qc-usb-messenger-1.7/qc-driver.c:3484: error: unknown field 'hardware' specified in initializer
/root/qc-usb-messenger-1.7/qc-driver.c: In function 'qc_usb_init':
/root/qc-usb-messenger-1.7/qc-driver.c:3661: error: implicit declaration of function 'LONG'
/root/qc-usb-messenger-1.7/qc-driver.c:3661: warning: left shift count >= width of type
make[2]: *** [/root/qc-usb-messenger-1.7/qc-driver.o] Error 1
make[1]: *** [_module_/root/qc-usb-messenger-1.7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-12-server'
make: *** [quickcam.ko] Error 2
```Any help would be appreciated

---

### Post by Whoopie on 2008-03-30
Hi,

apply the attached patch. This should make it work again.

Best regards,
Whoopie

---

### Post by SATA on 2008-03-30
> **Whoopie said:**
> Hi,

apply the attached patch. This should make it work again.

Best regards,
Whoopie


Applied the supplied patch. Same error, Different line number

---

### Post by SATA on 2008-03-30
kick me if im stupid.

But after applying the patch, it still wouldnt build.

so I changed this line from
```
hardware:     VID_HARDWARE_QCAM_USB,
```to

```
//hardware:     VID_HARDWARE_QCAM_USB,
```Aftert that, the Driver: Built, Loaded and it works

I have built two deb packages with checkinstall for anyone who is interested.
They were built for the 2.6.24-12-generic and 2.6.24-12-server kernel's

You can download either one from here:
Generic Kernel: [http://files.i-owns-u.net/qc-usb-messenger/qc-usb-messenger_1.7-hardy_generic1_i386.deb](http://files.i-owns-u.net/qc-usb-messenger/qc-usb-messenger_1.7-hardy_generic1_i386.deb)
Server Kernel: [http://files.i-owns-u.net/qc-usb-messenger/qc-usb-messenger_1.7-hardy_server1_i386.deb](http://files.i-owns-u.net/qc-usb-messenger/qc-usb-messenger_1.7-hardy_server1_i386.deb)

---

### Post by Plasma_NZ on 2008-04-07
yeah ok - how do u applie the patch ? im new to all this..?? i think i've tried and it's spat errors at me about a line number etc..

little help.?

---

### Post by TameLion on 2008-04-15
Plazma_NZ, try here: [http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html) ;)

Whoopie/SATA: Excellent patch and extra fix! Thanks guys.

Jimi.

---

### Post by izac on 2008-04-18
well i have errors too trying to install a quickam messenger... any help would be apriciated :) here is the output : ("i aplied the patch provided above)....


[I] make clean && make allrm -f *.o qcset input_read show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
cd testquickcam ; make clean
make[1]: Entering directory `/home/zac/Desktop/qc-usb-messenger-1.7/testquickcam'
rm -f testquickcam *~ pic.ppm pic.gif
make[1]: Leaving directory `/home/zac/Desktop/qc-usb-messenger-1.7/testquickcam'
make -C "/lib/modules/2.6.24-12-generic/build" SUBDIRS="/home/zac/Desktop/qc-usb-messenger-1.7" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-12-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/zac/Desktop/qc-usb-messenger-1.7/.tmp_versions ; rm -f /home/zac/Desktop/qc-usb-messenger-1.7/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/zac/Desktop/qc-usb-messenger-1.7
  gcc -Wp,-MD,/home/zac/Desktop/qc-usb-messenger-1.7/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2  -mtune=generic -m64 -mno-red-zone -mcmodel=kernel -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a-time -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -maccumulate-outgoing-args   -fstack-protector -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/zac/Desktop/qc-usb-messenger-1.7/.tmp_qc-driver.o /home/zac/Desktop/qc-usb-messenger-1.7/qc-driver.c
/home/zac/Desktop/qc-usb-messenger-1.7/qc-driver.c: In function &#8216;qc_int_init&#8217;:
/home/zac/Desktop/qc-usb-messenger-1.7/qc-driver.c:850: warning: passing argument 6 of &#8216;usb_fill_int_urb&#8217; from incompatible pointer type
/home/zac/Desktop/qc-usb-messenger-1.7/qc-driver.c: In function &#8216;qc_isoc_start&#8217;:
/home/zac/Desktop/qc-usb-messenger-1.7/qc-driver.c:2209: warning: assignment from incompatible pointer type
/home/zac/Desktop/qc-usb-messenger-1.7/qc-driver.c: At top level:
/home/zac/Desktop/qc-usb-messenger-1.7/qc-driver.c:3473: warning: initialization from incompatible pointer type
/home/zac/Desktop/qc-usb-messenger-1.7/qc-driver.c:3484: error: unknown field &#8216;hardware&#8217; specified in initializer
make[2]: *** [/home/zac/Desktop/qc-usb-messenger-1.7/qc-driver.o] Error 1
make[1]: *** [_module_/home/zac/Desktop/qc-usb-messenger-1.7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-12-generic'
make: *** [quickcam.ko] Error 2[/I]

---

### Post by Papou on 2008-04-22
Hello,

I apply the patch and got the following : 


famille@hp:~/Serge/Installations/qc-usb-messenger-1.7$ sudo make all
make -C "/lib/modules/2.6.24-16-generic/build" SUBDIRS="/home/famille/Serge/Installations/qc-usb-messenger-1.7" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/famille/Serge/Installations/qc-usb-messenger-1.7/.tmp_versions ; rm -f /home/famille/Serge/Installations/qc-usb-messenger-1.7/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/famille/Serge/Installations/qc-usb-messenger-1.7
  gcc -m32 -Wp,-MD,/home/famille/Serge/Installations/qc-usb-messenger-1.7/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/famille/Serge/Installations/qc-usb-messenger-1.7/.tmp_qc-driver.o /home/famille/Serge/Installations/qc-usb-messenger-1.7/qc-driver.c
/home/famille/Serge/Installations/qc-usb-messenger-1.7/qc-driver.c: In function ‘qc_int_init’:
/home/famille/Serge/Installations/qc-usb-messenger-1.7/qc-driver.c:850: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/famille/Serge/Installations/qc-usb-messenger-1.7/qc-driver.c: In function ‘qc_isoc_start’:
/home/famille/Serge/Installations/qc-usb-messenger-1.7/qc-driver.c:2209: warning: assignment from incompatible pointer type
/home/famille/Serge/Installations/qc-usb-messenger-1.7/qc-driver.c:3649:1: error: unterminated #ifdef
make[2]: *** [/home/famille/Serge/Installations/qc-usb-messenger-1.7/qc-driver.o] Error 1
make[1]: *** [_module_/home/famille/Serge/Installations/qc-usb-messenger-1.7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [quickcam.ko] Error 2
famille@hp:~/Serge/Installations/qc-usb-messenger-1.7$ 

Any suggestion will be welcomed.

---

### Post by c4pp4 on 2008-04-26
> **SATA said:**
> 
You can download either one from here:
Generic Kernel: [http://files.i-owns-u.net/qc-usb-messenger/qc-usb-messenger_1.7-hardy_generic1_i386.deb](http://files.i-owns-u.net/qc-usb-messenger/qc-usb-messenger_1.7-hardy_generic1_i386.deb)
[/URL]

Thanks a lot! I installed your package and had to use this command:
sudo cp /lib/modules/2.6.24-12-generic/misc/quickcam.ko /lib/modules/2.6.24-16-generic/ubuntu/media/quickcam

because of 2.6.24-16 kernel.
Now it works like a charm :D

---

### Post by MemoryDump on 2008-04-30
> **c4pp4 said:**
> Thanks a lot! I installed your package and had to use this command:
sudo cp /lib/modules/2.6.24-12-generic/misc/quickcam.ko /lib/modules/2.6.24-16-generic/ubuntu/media/quickcam

because of 2.6.24-16 kernel.
Now it works like a charm :D
what else did you have to do to make this work? 
reboot? modprob?
when I run Camorama I get a "Could not connect to video device (/dev/video0). Please check connection"

I have quickcam home.
Bus 005 Device 005: ID 046d:0801 Logitech, Inc. QuickCam Home

thxs
-MD

---

### Post by c4pp4 on 2008-04-30
> **MemoryDump said:**
> what else did you have to do to make this work? 
reboot? modprob?
when I run Camorama I get a "Could not connect to video device (/dev/video0). Please check connection"

I have quickcam home.
Bus 005 Device 005: ID 046d:0801 Logitech, Inc. QuickCam Home

thxs
-MD

**quickcam messenger 046d:08f0**
modprobe quickcam
quickcam to /etc/modules
that's all
for skype i followed this:
[http://ubuntuforums.org/showthread.php?p=3856516#post3856516/](http://ubuntuforums.org/showthread.php?p=3856516#post3856516/)
with module parameter: quickcam video_nr=1

---

### Post by MemoryDump on 2008-04-30
> **c4pp4 said:**
> **quickcam messenger 046d:08f0**
modprobe quickcam
quickcam to /etc/modules
that's all
for skype i followed this:
[http://ubuntuforums.org/showthread.php?p=3856516#post3856516/](http://ubuntuforums.org/showthread.php?p=3856516#post3856516/)
with module parameter: quickcam video_nr=1
I don't fully understand your reply.
is "quickcam messenger 046d:08f0" a command I should be running?
"quickcam to /etc/modules" is that copying a file some somewhere?

little confusing :)

---

### Post by c4pp4 on 2008-05-03
> **MemoryDump said:**
> I don't fully understand your reply.
is "quickcam messenger 046d:08f0" a command I should be running?
"quickcam to /etc/modules" is that copying a file some somewhere?

little confusing :)

My fault...

"Quickcam Messenger 046d:08f0" is the webcam I talk about.

"quickcam to /etc/modules" I meant that you have to edit /etc/modules file and add a new line with "quickcam" to load the driver on every boot.

---

### Post by Lothas on 2008-05-05
Hey, I have the Lego Mindstorms Vision Command camera:
Bus 001 Device 004: ID 046d:0850 Logitech, Inc. QuickCam Web

and it doesn't work properly, not even in Hardy. Since 7.10 the built-in mic works ok (little down on gain) but the camera is still not working. This is one of the only things keeping me from moving completely to Ubuntu.

I've tried compiling the qc-usb driver without much luck. This is the output:

make all
```
make -C "/lib/modules/2.6.24-16-generic/build" SUBDIRS="/home/lothas/Desktop/qc-usb-0.6.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/lothas/Desktop/qc-usb-0.6.6/.tmp_versions ; rm -f /home/lothas/Desktop/qc-usb-0.6.6/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/lothas/Desktop/qc-usb-0.6.6
  gcc -m32 -Wp,-MD,/home/lothas/Desktop/qc-usb-0.6.6/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/lothas/Desktop/qc-usb-0.6.6/.tmp_qc-driver.o /home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c
In file included from /home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c:47:
/home/lothas/Desktop/qc-usb-0.6.6/quickcam.h:129:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:59,
                 from include/linux/videodev.h:15,
                 from /home/lothas/Desktop/qc-usb-0.6.6/quickcam.h:95,
                 from /home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c: At top level:
/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initializer
make[2]: *** [/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/lothas/Desktop/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [quickcam.ko] Error 2

```

---

### Post by MemoryDump on 2008-05-06
my cam just doesn't want to work :(
I've tried compiling the driver/module and it fails.. *sigh*

---

### Post by nilpill on 2008-05-08
> **c4pp4 said:**
> Thanks a lot! I installed your package and had to use this command:
sudo cp /lib/modules/2.6.24-12-generic/misc/quickcam.ko /lib/modules/2.6.24-16-generic/ubuntu/media/quickcam

because of 2.6.24-16 kernel.
Now it works like a charm :D

Thanks a lot for that! I've got it working in the 2.6.24-16 kernel now. However, if I try to get do the same thing for the 2.6.24-17 kernel with 
```
sudo cp /lib/modules/2.6.24-12-generic/misc/quickcam.ko /lib/modules/2.6.24-17-generic/ubuntu/media/quickcam

``` it doesn't work. Why might that be?

---

### Post by LexingtonKW on 2008-05-18
Ugggh! I've tried ALL of this (on Hardy 32bit) and it STILL won't work...

---

### Post by Csomby on 2008-05-26
Yesterday a new driver came out( qc-usb-messenger-1.8.tar.gz). The problem that everyone told (quickcam.ko) is repaired, but now the qcset has problems.:) i have a 64bit system, so i can use the .deb that someone sent. If somebody can solve the problem, please share with us,thanks

---

### Post by Muchacho_Gasolino on 2008-05-28
Yo Csomby,

Where can I get me one of those 1.8s? I think I'm looking on the maintainer's page ([http://home.mag.cx/messenger/](http://home.mag.cx/messenger/)) and there is no mention of it. Also, a google search for "qc-usb-messenger-1.8.tar.gz" turns up absolutely nothing...


@SATA:

Where is that "hardware: ..." line that you changed? I can't find it in either the patch or quickcam.h.


> **nilpill said:**
> Thanks a lot for that! I've got it working in the 2.6.24-16 kernel now. However, if I try to get do the same thing for the 2.6.24-17 kernel with "..." it doesn't work. Why might that be?

Same thing for me; I get 

```
FATAL: Error inserting quickcam (/lib/modules/2.6.24-17-generic/ubuntu/media/quickcam/quickcam.ko): Invalid module format
```

---

### Post by Csomby on 2008-05-29
At [http://home.mag.cx/messenger/](http://home.mag.cx/messenger/) you click on qc-usb-messenger-1.7.tar.gz (2007-09-02), and that take you here: [http://home.mag.cx/messenger/source/](http://home.mag.cx/messenger/source/). you can find there.

But i wrote mail to the maker of the driver.and he replied this: 
"
Does qcset compile if you add “–I/usr/include”  manually?
gcc -Wall -O2 -s -I/usr/include qcset.c -o qcset –lm
"

But i cant understand what i should do. i'm not an experienced linux user yet:S any ideas?

---

### Post by Muchacho_Gasolino on 2008-05-31
Hey Csomby,

I think you can fix that by doing

```
sudo apt-get install build-essential
```

For some reason gcc on ubuntu doesn't come with the standard c library...

---

### Post by Muchacho_Gasolino on 2008-05-31
Damn; so close..

Everything seems to go great until the line where it tries to load xawtv. Then my screen goes black and I can't do anything except for ctrl-alt-backspace out. The driver compiles, loads, finds the video device fine. I do get

```
Right now driver is loaded and should be ready to run.
Let's test if user applications can see it, starting with qcset.
Press Ctrl+C to quit, Enter to continue --->

[!] qcset did not found the QuickCam camera
```

Is that a big deal? Apparently...

If i try to run the install script over again, it says the quickcam driver is loaded already, but cheese can't see anything and xawtv just turns my screen black. Anybody know what the deal is?

---

### Post by Csomby on 2008-06-01
i found the camera, but it cant load the driver... it is so funny:D

---

### Post by Limulus on 2008-06-24
> **Csomby said:**
> Yesterday a new driver came out( qc-usb-messenger-1.8.tar.gz)

I can't seem to load [http://home.mag.cx/messenger/source/](http://home.mag.cx/messenger/source/) (I get a timeout error)

Does anyone know of an alternate download link or have a copy of 1.8 they can post?

Thanks!

---

### Post by Limulus on 2008-06-24
> **Limulus said:**
> I can't seem to load [http://home.mag.cx/messenger/source/](http://home.mag.cx/messenger/source/) (I get a timeout error)

Does anyone know of an alternate download link or have a copy of 1.8 they can post?

Thanks!

Looks like the website is working now; got it :)

---

### Post by t35t0r on 2008-06-28
I have:

```

Bus 001 Device 011: ID 046d:08f0 Logitech, Inc. QuickCam Messenger

```

downloaded v1.8 ([http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz)), compiled, and installed:

```

# lsmod | grep qc
qcmessenger           112584  0 
videodev               29440  2 qcmessenger,usbvideo
usbcore               146028  9 qcmessenger,quickcam_messenger,usbvideo,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd

```

the ./quickcam.sh script messes up when it tries to test the camera saying it can't find some (device) file so I quit with ctrl+c and tried ./qcset -i but it doesn't look like it's working properly either:

> 
8$ qcset -i
Name          : @&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;h&#65533;&#65533;&#65533;/&#65533;.N=
Type          : 
Channels      : 0
Audio devices : 0
Maxsize       : 0,0
Minsize       : 0,0

Overlay coords: 17,8
Capture size  : -1208421272,1
Chromakey     : -1208422400
Flags         : 

Channel       : 0
Name          : 
Tuners        : -1081309400
Flags         : 
Type          : (unknown)
Norm          : 47093

Brightness    : 0
Hue           : 33708
Color         : 49036
Contrast      : 61536
Whiteness     : 47097
Depth         : 0
Palette       : (unknown)


```

$ ls -l /dev/video*
lrwxrwxrwx 1 root root      6 2008-06-28 12:48 /dev/video -> video0
crw-rw---- 1 root video 81, 0 2008-06-28 12:55 /dev/video0

```

```

$ groups
myuser adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin

```

xawtv and gqcam aren't showing anything. I've gotten this camera to work before in gentoo (2.6.22 kernel I think) and older version of the qc-usb-messenger drivers. I just grabbed the webcam from my windows box on which I tested as working with the logitech utilities.

---

### Post by t35t0r on 2008-07-01
I'm not sure what the problem was, but it started working in xawtv and gqcam after I rebooted the system.

---

### Post by SpEcIeS on 2008-07-01
Personally, the only way I found that worked on my system was using the qc-messenger-1.8 and installing using direct ROOT -> su not sudo. 

Enable the ROOT TERMINAL in your menu and away you go. Well, as long as you have all the prerequisites installed. :)

---

### Post by c4pp4 on 2008-07-02
It works with this attached file ( version 1.8 )
```
sudo cp quickcam.ko /lib/modules/2.6.24-19-generic/ubuntu/media/quickcam
```

---

### Post by spezifanta on 2008-10-19
This worked for me (2.6.26):

- get [http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz)
- apply this patch: [http://bugs.gentoo.org/attachment.cgi?id=167504](http://bugs.gentoo.org/attachment.cgi?id=167504)
- continue installing qc-usb-messenger-1.8

How to patch:
[http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html)

---

### Post by derek7 on 2008-10-19
i tried the patch, with kernel 2.6.27

but i recive:

/home/enrico/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_ioctl’:
/home/enrico/Desktop/qc-usb-messenger-1.8/qc-driver.c:2898: error: ‘struct video_device’ has no member named ‘type’
/home/enrico/Desktop/qc-usb-messenger-1.8/qc-driver.c: At top level:
/home/enrico/Desktop/qc-usb-messenger-1.8/qc-driver.c:3487: error: unknown field ‘type’ specified in initializer
make[2]: *** [/home/enrico/Desktop/qc-usb-messenger-1.8/qc-driver.o] Error 1
make[1]: *** [_module_/home/enrico/Desktop/qc-usb-messenger-1.8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [qcmessenger.ko] Error 2
ls: cannot access qcmessenger.ko: No such file or directory
[!] Looks like the driver compilation failed.
Did you get any error messages above?
If asking for help, show what error messages you got.

---

### Post by spezifanta on 2008-10-19
Try this:

```
wget http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz
wget http://bugs.gentoo.org/attachment.cgi?id=167504 -O patch.txt
tar xzvf qc-usb-messenger-1.8.tar.gz
patch -p0 < patch.txt
cd qc-usb-messenger-1.8
make
sudo make install
sudo insmod ./qcmessanger.ko
```

---

### Post by SATA on 2008-10-25
i tried the above, and im getting:

```
/home/ryan/Desktop/qc-usb-messenger-1.8/qc-driver.c: In function 'qc_v4l_ioctl':
/home/ryan/Desktop/qc-usb-messenger-1.8/qc-driver.c:2898: error: 'struct video_device' has no member named 'type'
/home/ryan/Desktop/qc-usb-messenger-1.8/qc-driver.c: At top level:
/home/ryan/Desktop/qc-usb-messenger-1.8/qc-driver.c:3487: error: unknown field 'type' specified in initializer
make[2]: *** [/home/ryan/Desktop/qc-usb-messenger-1.8/qc-driver.o] Error 1
make[1]: *** [_module_/home/ryan/Desktop/qc-usb-messenger-1.8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [qcmessenger.ko] Error 2
```
If i comment out the offending lines, the module builds, loads, but the cam image is just black. No video seems to come through

---

### Post by SATA on 2008-10-25
Heres the output from dmesg regarding the qcmessenger module
```

[24150.664902] qcmessenger [57.719607]: ----------LOADING QUICKCAM MODULE------------
[24150.664922] qcmessenger [57.719634]: struct quickcam size: 4424
[24150.665056] usbcore: registered new interface driver qcmessenger
[24202.232435] qcmessenger: QuickCam USB camera found (driver version QuickCam Messenger/Communicate USB 1.8 $Date: 2008/05/26 00:00:00 $)
[24202.232451] qcmessenger: Kernel:2.6.27-7-generic bus:3 class:FF subclass:FF vendor:046D product:08F6
[24202.238340] qcmessenger [49.293049]: poisoning qc in qc_usb_init
[24202.243108] qcmessenger [49.297815]: E00A contains 08F6
[24202.243119] qcmessenger: Sensor VV6450 detected
[24202.250135] qcmessenger [49.304843]: Quickcam snapshot button registered on usb-0000:00:13.1-1/input0
[24202.252676] qcmessenger: Registered device: /dev/video0
[24250.925668] qcmessenger [37.980375]: open users=1
[24250.990113] qcmessenger [38.044820]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24250.992242] qcmessenger [38.046950]: set sensor=324x248 vwin=324x248
[24251.014136] qcmessenger [38.068843]: failed qc_v4l_ioctl()=-515
[24251.040912] qcmessenger [38.095620]: close users=0
[24251.042997] qcmessenger [38.097706]: open users=1
[24251.107115] qcmessenger [38.161823]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24251.109115] qcmessenger [38.163825]: set sensor=324x248 vwin=324x248
[24251.131159] qcmessenger [38.185865]: close users=0
[24251.314466] qcmessenger [38.369172]: open users=1
[24251.379120] qcmessenger [38.433826]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24251.381111] qcmessenger [38.435821]: set sensor=324x248 vwin=324x248
[24251.403141] qcmessenger [38.457848]: failed qc_v4l_ioctl()=-515
[24251.405002] qcmessenger [38.459712]: close users=0
[24251.406237] qcmessenger [38.460948]: open users=1
[24251.471116] qcmessenger [38.525823]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24251.473353] qcmessenger [38.528061]: set sensor=324x248 vwin=324x248
[24251.495148] qcmessenger [38.549855]: close users=0
[24251.507853] qcmessenger [38.562558]: open users=1
[24251.572130] qcmessenger [38.626835]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24251.574120] qcmessenger [38.628830]: set sensor=324x248 vwin=324x248
[24251.596236] qcmessenger [38.650943]: failed qc_v4l_ioctl()=-515
[24251.598064] qcmessenger [38.652775]: close users=0
[24251.599316] qcmessenger [38.654028]: open users=1
[24251.663117] qcmessenger [38.717824]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24251.665239] qcmessenger [38.719946]: set sensor=324x248 vwin=324x248
[24251.687149] qcmessenger [38.741856]: close users=0
[24251.688556] qcmessenger [38.743266]: open users=1
[24251.753116] qcmessenger [38.807823]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24251.755117] qcmessenger [38.809827]: set sensor=324x248 vwin=324x248
[24251.777140] qcmessenger [38.831847]: failed qc_v4l_ioctl()=-515
[24251.778992] qcmessenger [38.833702]: close users=0
[24251.780258] qcmessenger [38.834968]: open users=1
[24251.844243] qcmessenger [38.898948]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24251.846116] qcmessenger [38.900828]: set sensor=324x248 vwin=324x248
[24251.868227] qcmessenger [38.922935]: failed qc_v4l_ioctl()=-515
[24251.868267] qcmessenger [38.922978]: close users=0
[24251.874434] qcmessenger [38.929141]: open users=1
[24251.938124] qcmessenger [38.992831]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24251.940120] qcmessenger [38.994830]: set sensor=324x248 vwin=324x248
[24251.962139] qcmessenger [39.016846]: failed qc_v4l_ioctl()=-515
[24251.964028] qcmessenger [39.018738]: close users=0
[24251.964139] qcmessenger [39.018849]: open users=1
[24252.027117] qcmessenger [39.081824]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24252.029118] qcmessenger [39.083827]: set sensor=324x248 vwin=324x248
[24252.051215] qcmessenger [39.105922]: failed qc_v4l_ioctl()=-515
[24252.051253] qcmessenger [39.105962]: close users=0
[24255.680580] qcmessenger [42.735285]: open users=1
[24255.745120] qcmessenger [42.799826]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24255.747119] qcmessenger [42.801829]: set sensor=324x248 vwin=324x248
[24255.769136] qcmessenger [42.823844]: failed qc_v4l_ioctl()=-515
[24255.770974] qcmessenger [42.825685]: close users=0
[24255.772623] qcmessenger [42.827330]: open users=1
[24255.837123] qcmessenger [42.891830]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24255.839116] qcmessenger [42.893826]: set sensor=324x248 vwin=324x248
[24255.861163] qcmessenger [42.915870]: close users=0
[24255.862610] qcmessenger [42.917319]: open users=1
[24255.927118] qcmessenger [42.981825]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24255.929200] qcmessenger [42.983910]: set sensor=324x248 vwin=324x248
[24255.951353] qcmessenger [43.006060]: failed qc_v4l_ioctl()=-515
[24255.953463] qcmessenger [43.008172]: close users=0
[24255.954712] qcmessenger [43.009424]: open users=1
[24256.019123] qcmessenger [43.073830]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24256.021112] qcmessenger [43.075822]: set sensor=324x248 vwin=324x248
[24256.043212] qcmessenger [43.097918]: failed qc_v4l_ioctl()=-515
[24256.044740] qcmessenger [43.099450]: close users=0
[24256.081595] qcmessenger [43.136300]: open users=1
[24256.146124] qcmessenger [43.200829]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24256.148116] qcmessenger [43.202826]: set sensor=324x248 vwin=324x248
[24256.170142] qcmessenger [43.224849]: failed qc_v4l_ioctl()=-515
[24256.172432] qcmessenger [43.227138]: close users=0
[24256.172546] qcmessenger [43.227256]: open users=1
[24256.236122] qcmessenger [43.290828]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24256.238119] qcmessenger [43.292829]: set sensor=324x248 vwin=324x248
[24256.260213] qcmessenger [43.314918]: failed qc_v4l_ioctl()=-515
[24256.260250] qcmessenger [43.314959]: close users=0
[24256.925177] qcmessenger [43.979882]: open users=1
[24256.989115] qcmessenger [44.043822]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24256.991118] qcmessenger [44.045828]: set sensor=324x248 vwin=324x248
[24257.013147] qcmessenger [44.067854]: failed qc_v4l_ioctl()=-515
[24257.014972] qcmessenger [44.069682]: close users=0
[24257.016236] qcmessenger [44.070946]: open users=1
[24257.080122] qcmessenger [44.134828]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24257.082119] qcmessenger [44.136829]: set sensor=324x248 vwin=324x248
[24257.104213] qcmessenger [44.158921]: failed qc_v4l_ioctl()=-515
[24257.105687] qcmessenger [44.160398]: close users=0
[24258.061101] qcmessenger [45.115808]: open users=1
[24258.126118] qcmessenger [45.180826]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24258.128127] qcmessenger [45.182838]: set sensor=324x248 vwin=324x248
[24258.150134] qcmessenger [45.204842]: failed qc_v4l_ioctl()=-515
[24258.152309] qcmessenger [45.207017]: close users=0
[24258.153619] qcmessenger [45.208329]: open users=1
[24258.218121] qcmessenger [45.272826]: qc_sensor_init: call qc_sensor_setsize0 (324,248)
[24258.220119] qcmessenger [45.274829]: set sensor=324x248 vwin=324x248
[24258.242212] qcmessenger [45.296919]: failed qc_v4l_ioctl()=-515
[24258.242251] qcmessenger [45.296962]: close users=0
[24281.412123] qcmessenger [ 8.466829]: Unhandled INT URB error -62
[24281.412135] qcmessenger [ 8.466846]: INT URB error status=-62 tb_length=1 act_length=0 interval=16 frame=-1 data=00
[24281.460122] qcmessenger [ 8.514827]: Unhandled INT URB error -62
[24281.460133] qcmessenger [ 8.514844]: INT URB error status=-62 tb_length=1 act_length=0 interval=16 frame=-1 data=00
[24281.508122] qcmessenger [ 8.562829]: Unhandled INT URB error -62
[24281.508133] qcmessenger [ 8.562844]: INT URB error status=-62 tb_length=1 act_length=0 interval=16 frame=-1 data=00
[24281.556120] qcmessenger [ 8.610828]: Unhandled INT URB error -62
[24281.556132] qcmessenger [ 8.610843]: INT URB error status=-62 tb_length=1 act_length=0 interval=16 frame=-1 data=00
[24281.611531] qcmessenger [ 8.666240]: poisoning qc in qc_usb_exit

```

---

### Post by TheDebugger on 2008-11-05
I made a patch available here [http://www.geocities.com/hvansteenhuyse/index.html]("http://www.geocities.com/hvansteenhuyse/index.html").
So there are 2 patches to install:
- The first one is mentioned above cfr. #105
- The second one is this one
After installing both the patches I compiled the driver and my cam was working.

HowTo apply the patches:
   wget [http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz)
   wget [http://bugs.gentoo.org/attachment.cgi?id=167504](http://bugs.gentoo.org/attachment.cgi?id=167504) -O patch.txt
   Download the second patch [here]("http://www.geocities.com/hvansteenhuyse/index.html") and put it in the same directory as the other downloads
   tar xzvf qc-usb-messenger-1.8.tar.gz
   patch -p0 < patch.txt
   patch -p0 < qc.patch.2.txt
   cd qc-usb-messenger-1.8
   ./quickcam.sh

The script quickcam.sh does literally everything (software dependency checks, compilation and installation of the driver), all you have to do is press ENTER several times until the scripts ends.
Or you could just execute the steps explained in # 105 (item above) supra adding my patch of course.

After installing both the patches I compiled the driver and my cam was working.
Have fun!

---

### Post by thommy on 2008-11-09
Hi TheDebugger, please, can you tell me, how to install the patch. I got the same error messages as SATA and spezifanta. Thanks for help. Thommy
PS I use Kubuntu 8.10

---

### Post by thommy on 2008-11-09
Hi TheDebugger, thanks a lot for your answer, i'll try it later and give you a report, how and if it works.  Thommy

---

### Post by thommy on 2008-11-09
Hi TheDebugger, the installation ran without any error messages. But if I use camorama, there is an error message: Could not capture image. In the image window are only some stripes with pixels. Similar happens using skype, if I want to use video transmission. Using cheese, I get a perfect image. Do you have an idea, what is going wrong? Some days before I installed the driver for a dvb-t stick, as described here: [http://www.imhorst.net/digittrade-dvb-t-stick-unter-linux-nutzen/]("http://www.imhorst.net/digittrade-dvb-t-stick-unter-linux-nutzen/") I used the ubuntu script. May this be the reason, why camorama and skype-video don't work?
Thommy:-?
Starting camorama in a terminal this message appears: (camorama:19003): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

---

### Post by Johnny Golden on 2008-12-26
Thanks TheDebugger, made some real progress, although like SpEcIeS I had to run the script as root for it to complete.  Can now get an image in xawtv and camorama (although not cheese - haven't tested anything else) but only after running modprobe qcmessenger as root (sudo -s).

So my questions are:
- How do I get the webcam working as a non-root user (e.g. using sudo)?
- More importantly, how do I get it to load at startup (adding qcmessenger to /etc/modules doesn't seem to do the trick)?

Any help would be much appreciated...

---

### Post by el_chupacabra on 2008-12-31
> **TheDebugger said:**
> I made a patch available here [http://www.geocities.com/hvansteenhuyse/index.html]("http://www.geocities.com/hvansteenhuyse/index.html").
So there are 2 patches to install:
- The first one is mentioned above cfr. #105
- The second one is this one
After installing both the patches I compiled the driver and my cam was working.

HowTo apply the patches:
   wget [http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz)
   wget [http://bugs.gentoo.org/attachment.cgi?id=167504](http://bugs.gentoo.org/attachment.cgi?id=167504) -O patch.txt
   Download the second patch [here]("http://www.geocities.com/hvansteenhuyse/index.html") and put it in the same directory as the other downloads
   tar xzvf qc-usb-messenger-1.8.tar.gz
   patch -p0 < patch.txt
   patch -p0 < qc.patch.2.txt
   cd qc-usb-messenger-1.8
   ./quickcam.sh

The script quickcam.sh does literally everything (software dependency checks, compilation and installation of the driver), all you have to do is press ENTER several times until the scripts ends.
Or you could just execute the steps explained in # 105 (item above) supra adding my patch of course.

After installing both the patches I compiled the driver and my cam was working.
Have fun!

This worked for my "Logitech QuickCam Messenger Communicate" webcam. 

```
Bus 005 Device 003: ID 046d:08f5 Logitech, Inc. QuickCam Messenger Communicate
```

Thanks a lot. :D

---

### Post by el_chupacabra on 2009-01-01
If anybody is interested, I created a short guide on what I did here: [http://balla.knows.it](http://balla.knows.it) :popcorn:

---

### Post by venky80 on 2009-02-26
> **el_chupacabra said:**
> If anybody is interested, I created a short guide on what I did here: [http://balla.knows.it](http://balla.knows.it) :popcorn:

Is there a deb file for this I am using jaunty and have a quickcam messenger 08F0 which does not work with skype or cheese

---

### Post by adambh on 2009-03-11
> **desperado666 said:**
> No.
It does go black while "compiling" Step 6.(Something i could see was patching kernel)
If i press CTRL ALT Backspace and do my login i can work again.

I have exactly the same problem, (kernel 2.6.27-11-generic).
Also running a laptop, though I don´t see  how that would affect anything.

---

### Post by pgg1959 on 2009-03-17
> **TheDebugger said:**
> I made a patch available here [http://www.geocities.com/hvansteenhuyse/index.html]("http://www.geocities.com/hvansteenhuyse/index.html").
So there are 2 patches to install:
- The first one is mentioned above cfr. #105
- The second one is this one
After installing both the patches I compiled the driver and my cam was working.

HowTo apply the patches:
   wget [http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz)
   wget [http://bugs.gentoo.org/attachment.cgi?id=167504](http://bugs.gentoo.org/attachment.cgi?id=167504) -O patch.txt
   Download the second patch [here]("http://www.geocities.com/hvansteenhuyse/index.html") and put it in the same directory as the other downloads
   tar xzvf qc-usb-messenger-1.8.tar.gz
   patch -p0 < patch.txt
   patch -p0 < qc.patch.2.txt
   cd qc-usb-messenger-1.8
   ./quickcam.sh

The script quickcam.sh does literally everything (software dependency checks, compilation and installation of the driver), all you have to do is press ENTER several times until the scripts ends.
Or you could just execute the steps explained in # 105 (item above) supra adding my patch of course.

After installing both the patches I compiled the driver and my cam was working.
Have fun!

Thanks **TheDebugger**. Following your recipe helped this complete newbie to get the Logitech quickcam messenger working in xawtv. I just set the system up about 3 days ago and had no clue about Ubuntu before. Dabbled a bit with linux in 1995 (when it came on floppies!!) but have not really kept any contact with it since. I have to say I am impressed.

Looking forward to playing some more and then eventually I will be able to get rid of the Windows box. Next project is loading Windows in a Virtual Machine.

Talk to you all soon.:KS

---

### Post by cisneros on 2009-03-25
I am having the same problem, have tried running the quickcam.sh script with the patches but to no avail.

I would like to work out where actually the problem is: I tried compiling the gspca module (which claims to support the camera i have (046d:08da)), but it came up with, at the end, 

  /usr/src/modules/gspca/gspca_core.c: In function ‘spca5xx_probe’:          &#9618;
  /usr/src/modules/gspca/gspca_core.c:4301: error: incompatible types in     &#9618;
  assignment                                                                 &#9618;
  make[4]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1                 &#9618;
  make[3]: *** [_module_/usr/src/modules/gspca] Error 2                      &#9618;
  make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'      &#9618;
  make[2]: *** [default] Error 2                                             &#9618;
  make[2]: Leaving directory `/usr/src/modules/gspca'                        &#9618;
  make[1]: *** [binary-modules] Error 2                                      &#9618;
  make[1]: Leaving directory `/usr/src/modules/gspca'                        &#9646;
  make: *** [kdist_build] Error 2  

Does anyone knows what is causing the incompatible types in the script, and how I can solve it?

thanks

---

### Post by el_chupacabra on 2009-04-02
> **venky80 said:**
> Is there a deb file for this I am using jaunty and have a quickcam messenger 08F0 which does not work with skype or cheese

Did you try the guide? 08F0 needs the same driver as my 08F5 version.

---

### Post by PRDR on 2009-04-26
Hi,

I had the 08F6 QC camera working just fine with intrepid's kernels using the excellent directions and patches found in this thread. But now, with jaunty, the driver fails to compile again :confused:.

Anybody knows of a patch working with jaunty's kernel?

Thanks in advance!

---

### Post by diehardlinux on 2009-06-18
> **Yoriko said:**
> [b][u]Installing Logitech Quickcam Messenger
Ubuntu Breezy 5.10[/u][/b]

There was an old post by my [Here](http://www.ubuntuforums.org/showthread.php?t=111225).

That wasn't very organised, and I left a few days later for Australia to visit my girlfriend where I was using a windows box and couldn't update, but thats beside the point.

I'll start off with my lsusb + uname -sr;

That is my version of the qc messenger. If you have that my instructions should work for you, I don't know about other versions.


**1.** Plug in your logitech quickcam messenger.

**2.** Get the latest driver sources from **[here](http://home.mag.cx/messenger/)** and unpack them somewhere.

**3.** Get the required dependancies (These were all needed from a fresh Breezy install)
```
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install xawtv gcc-3.4
```

**4.** Type into your terminal
```
export CC=gcc-3.4
```
This tells the driver to compile using gcc-3.4 the same as the kernel was compiled with (2.6.12 anyway).

**[color=red]5. This is the only way I know to do this; Potentially unsafe. If there is another way please tell me**[/color]
```
sudo passwd
```
to change the root password (you will need this during install).

**6.** cd to the directory you extracted the driver source too (in the same terminal you did #4 with) and run quickcam.sh.
```
./quickcam.sh
```
Type in the root password when it asks, and ignore all error messages. **Even the one about not finding a camera!**

**7.** When its done compiling, and the script has finished executing run
```
sudo modprobe quickcam
```
Now check your camera out in camorama, or gnomemeeting or something similar.

If all has gone well, continue;

*Credits to [Maol62](http://www.ubuntuforums.org/member.php?u=31754)*

This will set the camera to run during startup of your system.

**8.** run
```
sudo touch /etc/init.d/quickcam && sudo chmod 755 /etc/init.d/quickcam
```

**9.** If in gnome:
```
sudo gedit /etc/init.d/quickcam
```
If in KDE:
```
sudo kate /etc/init.d/quickcam
```
paste into the file.
```
#! /bin/sh 
# /etc/init.d/quickcam: reload the Logitech Quickcam Messenger driver. rmmod quickcam
modprobe quickcam
```
Save and close.

**10.** Create a symbolic link so the script is launched at boot;
```
sudo ln -s /etc/init.d/quickcam /etc/rcS.d/S99quickcam
```

**11. Done! Enjoy using your quickcam messenger!**


--------------------------------------------------------
I hope this is easier to understand than previous thread. Credits to Maol62 and emcompass for thier help. (and anyone i forgot :P).

footnote: I recently got gaim 2.0beta2 CVS to compile with --enable-vv. Yet i can't find vv anywhere within it, I've read on the forums that it works with msn for beta2 when compiled with --enable-vv. Any idea? (I hate tk, so wish(lol pun maybe <_<) amsn didn't use it).


Your post worked like a charm for mine Logitech E 3500, thanks a bunch for your post. Long live the Linux community!:popcorn:

---

### Post by kevalacious on 2009-08-04
**6.** cd to the directory you extracted the driver source too (in the same terminal you did #4 with) and run quickcam.sh.
```
./quickcam.sh
```Type in the root password when it asks, and ignore all error messages. **Even the one about not finding a camera!**

**7.** When its done compiling, and the script has finished executing run
```
sudo modprobe quickcam
```Now check your camera out in camorama, or gnomemeeting or something similar.

   I am stuck here.  What do you mean "cd to the directory?"  i put in .quicktime.sh and nothing happens....at all.    

My skype actuelly detects a camera now,  but when i look at it its just a bunch of green fuzzy lines.  Can any one help me?:confused:

---

### Post by diehardlinux on 2009-11-23
One quick side note: script can be ran as sudo user (sudo ./quickcam.sh) VS. running as root (sudo su instead of sudo passwd).

---

### Post by diehardlinux on 2009-11-23
kevalacious: You should be starting at the begging of post: Download source code package from here: [http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz) (gun zip file) , Then cd in terminal (change directory to where you downloaded it to (via wget or browser download).

"i put in .quicktime.sh and nothing happens". see my other post, should be ran as sudo user (worked for me). 
side notes: research how to run shell scripts: [http://www.cyberciti.biz/faq/run-execute-sh-shell-script/](http://www.cyberciti.biz/faq/run-execute-sh-shell-script/)

---

### Post by jhobdell on 2009-12-15
Hello all

Completely new guy  here. I've had Ubuntu on my machine for a few weeks now and it's going OK (still loads to learn).  My main problem at the moment is my webcam.  I've already spent several hours trying to get it to work and still nothing.

Like many others, I think, I have the problem of "quickcam.ko Error 2" (i.e. no such file or directory).  The main response to this seems to be the compiler, requiring an install of GCC 3.4 but most of the posts relating to it are at least a year old and unless I'm missing something it's now impossible to get or install this - my system doesn't seem to want to allow it anyway.  Dependency conflicts and all sorts.

That seems to be the main thing as far as I can tell.  If anyone has any pointers I'd be delighted to hear them.

Thanks guys!

---

### Post by jhobdell on 2009-12-15
Sorry to bother again.  I've carried on trawling through stuff and apparently this webcam should work "automatically" on Karmic with this driver: gspca stv06xx

I've no idea how to get it though or about the kernel updates that keep being mentioned.  Any answer or signposting would be great.

Thanks again.

---

### Post by Whoopie on 2009-12-15
I guess, you need to blacklist the quickcam_messenger module. Create the file "/etc/modprobe.d/blacklist-custom.conf" with the following content:

```

blacklist quickcam_messenger

```That's how I succeeded to get the webcam working.

---

### Post by Erik Andrén on 2009-12-23
> **Whoopie said:**
> I guess, you need to blacklist the quickcam_messenger module. Create the file "/etc/modprobe.d/blacklist-custom.conf" with the following content:

```

backlist quickcam_messenger

```

That's how I succeeded to get the webcam working.


I believe it should be:
blacklist, not backlist

---

### Post by madwoollything on 2010-07-31
I'm running 10.04 and have been keenly awaiting each kernel update so I can get my webcam working again (used to work with no problems out of the box with 8.04)

I've tried running this script with no success and suspect the problem is that one of the packages is no longer available in step 3:

E: Couldn't find package gcc-3.4

Anyone got any suggestions other than go back to 8.04 or buy a new webcam??

---

