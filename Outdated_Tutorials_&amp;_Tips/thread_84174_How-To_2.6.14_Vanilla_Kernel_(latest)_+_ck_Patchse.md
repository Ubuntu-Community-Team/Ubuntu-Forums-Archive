---
title: "How-To: 2.6.14 Vanilla Kernel (latest) + ck Patchset (Enhanced Performance kernel)"
date: 2005-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by RubenGonc on 2005-10-30
This How-To will guide you through the compilation/installation of the 2.6.14 Vanilla Kernel (more recent than the one distribuited with Ubuntu 5.10) with the performance patchset by Kon Colivas.

1-Download what is needed:

Type in the command line:

> sudo apt-get install build-essential bin86 kernel-package

sudo apt-get install libqt3-headers libqt3-mt-dev (needed for make xconfig)

Then download the following files to your Home directory:

[http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.14.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.14.tar.bz2)

[http://ck.kolivas.org/patches/2.6/2.6.14/2.6.14-ck1/patch-2.6.14-ck1.bz2](http://ck.kolivas.org/patches/2.6/2.6.14/2.6.14-ck1/patch-2.6.14-ck1.bz2)

2-Now, lets unpack the kernel source to /usr/src:

*Copy the source to /usr/src:

```
sudo cp linux-2.6.14.tar.bz2 /usr/src
```

*Change to /usr/src:

```
cd /usr/src
```

*Unpack it:

```
sudo tar -xvjf linux-2.6.14.tar.bz2
```

*Now lets change the created directory name:

```
sudo mv linux-2.6.14/ linux-2.6.14cK1
```

*Remove the symlink if there is one directory called linux:

```
sudo rm -rf linux
```

*Make the new symlink pointing for our 2.6.14 kernel source:

```
sudo ln -s /usr/src/linux-2.6.14cK1 linux
```

3-Now it's time to patch the kernel:

*Change to /usr/src/linux:

```
cd /usr/src/linux
```

*Switch to root user:

```
sudo -s -H
Password: <specify user password>
```

*Apply the patch:

```
sudo bzcat /home/username/patch-2.6.14-ck1.bz2| patch -p1
```

4-Kernel configuration:

*Import the configuration of the running kernel:

```
uname -r  
```  To see what kernel are you running (in my case it is 2.6.12-9-686).

```
sudo cp /boot/config-2.6.12-9-686 .config 
```   To copy the config file and use it as base for the new kernel configuration (Don't forget to choose the correct config file).

*Configure the kernel:

```
sudo make xconfig
```   

*While you may tweak your kernel configuration to your needs I will sugest you some tweaks:

In "General Setup" activate:

-Support for paging of anonymous memory (swap)
--Support for prefetching swapped memory

In "Processor type and features":

-Processor family     Choose the model of your processor.

Activate:

-Preemption Model
--Voluntary Kernel Preemption (Desktop)

-High Memory Support
--off                     -if you have less than 1 GB of RAM
--1GB Low Memory Support  -if you have 1GB of RAM
--4GB                     -if you have more than 1GB of RAM

-Timer frequency
--1000 Hz

In "Device drivers" go to "Block devices" and in "IO Schedulers" leave only the "CFQ I/O scheduler" activated, which provides the best performance.

In "Kernel hacking" uncheck "Kernel debugging".

Ctrl+S to save the kernel configuration and then close the window.

5-Let's build the kernel:

*In a terminal make sure you are in /usr/src/linux with full root access.

We will build a ".deb" file that can be installed in our Ubuntu system, using make-kpkg.

*In a terminal type:

```
make-kpkg clean

make-kpkg -initrd --revision=ck1 kernel_image
```

If there wasn't errors this will build the kernel and a ".deb" file will be created at /usr/src.
*To install it:

```
sudo dpkg -i kernel-image-2.6.14*.deb
```


6-Reboot and everything should be running ok! 
*Try:

```
uname -r   
```

to see that you are running the new kernel.


7-Nvidia graphic cards users:

To install Nvidia driver follow the guide (no need to install linux-headers as we have the source in /usr/src/linux:

[http://www.ubuntuforums.org/showthread.php?t=57368&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=57368&highlight=nvidia)


If you have any problem ask here.

Hope you like it!

R&#250;ben Gon&#231;alves:p

---

### Post by 23meg on 2005-10-30
Shall we retain the Ubuntu devs' patches to the 2.6.12 kernel (found in the linux-patch-ubuntu-2.6.12 package) by using this kernel? Are Ubuntu's kernel patches sent upstream and merged, or do they have to be applied manually?

---

### Post by XDevHald on 2005-10-30
If you're not sure of it's changes please see here: [http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.14](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.14)

And also other news here: [http://linuxdevices.com/news/NS7213494018.html4](http://linuxdevices.com/news/NS7213494018.html4)

---

### Post by RubenGonc on 2005-10-30
[QUOTE=23meg]Shall we retain the Ubuntu devs' patches to the 2.6.12 kernel (found in the linux-patch-ubuntu-2.6.12 package) by using this kernel? Are Ubuntu's kernel patches sent upstream and merged, or do they have to be applied manually?[/QUOTE]


I think that it isn't needed. I haven't applied them and everything is alright:)

---

### Post by crypto178 on 2005-10-30
Nice guide, worked flawlessy for me, thanks :D

---

### Post by Dracontopes on 2005-10-30
```

root@ubuntu:/usr/src/linux# sudo make xconfig
*
* Unable to find the QT installation. Please make sure that the
* QT development package is correctly installed and the QTDIR
* environment variable is set to the correct location.
*
make[1]: *** [scripts/kconfig/.tmp_qtcheck] Fout 1
make: *** [xconfig] Fout 2

```

and

```

root@ubuntu:/usr/src/linux# sudo apt-get install libqt3-headers
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
libqt3-headers is reeds de nieuwste versie.
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.

```
(it says libqt3-headers is already the newest version.)

---

### Post by Rob2687 on 2005-10-30
Is pentium-m strictly for the newer mobile chips or can I use that option with my PIII-M?

---

### Post by berserker on 2005-10-30
[QUOTE=Dracontopes]```

root@ubuntu:/usr/src/linux# sudo make xconfig
*
* Unable to find the QT installation. Please make sure that the
* QT development package is correctly installed and the QTDIR
* environment variable is set to the correct location.
*
make[1]: *** [scripts/kconfig/.tmp_qtcheck] Fout 1
make: *** [xconfig] Fout 2

```

and

```

root@ubuntu:/usr/src/linux# sudo apt-get install libqt3-headers
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
libqt3-headers is reeds de nieuwste versie.
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.

```
(it says libqt3-headers is already the newest version.)[/QUOTE]

Try installing the libqt3-mt-dev package.

---

### Post by crypto178 on 2005-10-30
[QUOTE=Dracontopes]```

root@ubuntu:/usr/src/linux# sudo make xconfig
*
* Unable to find the QT installation. Please make sure that the
* QT development package is correctly installed and the QTDIR
* environment variable is set to the correct location.
*
make[1]: *** [scripts/kconfig/.tmp_qtcheck] Fout 1
make: *** [xconfig] Fout 2

```

and

```

root@ubuntu:/usr/src/linux# sudo apt-get install libqt3-headers
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
libqt3-headers is reeds de nieuwste versie.
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.

```
(it says libqt3-headers is already the newest version.)[/QUOTE]
a simple workaround would be to use 'make menuconfig' instead (text-based), but maybe there's a more proper way.

---

### Post by RubenGonc on 2005-10-30
[QUOTE=Dracontopes]```

root@ubuntu:/usr/src/linux# sudo make xconfig
*
* Unable to find the QT installation. Please make sure that the
* QT development package is correctly installed and the QTDIR
* environment variable is set to the correct location.
*
make[1]: *** [scripts/kconfig/.tmp_qtcheck] Fout 1
make: *** [xconfig] Fout 2

```

and

```

root@ubuntu:/usr/src/linux# sudo apt-get install libqt3-headers
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
libqt3-headers is reeds de nieuwste versie.
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.

```
(it says libqt3-headers is already the newest version.)[/QUOTE]


Yes, I forgot to mention to install libqt3-mt-dev. How-To updated. Or you can use "sudo make menuconfig" or "sudo make gconfig" (you need gtk+-2.0, glib-2.0 and libglade-2.0) instead.

---

### Post by berserker on 2005-10-30
My Logitech MX1000 laser mouse works in 2.6.13.4 but not in 2.6.14 (with or without the patch). Here's my xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option "Protocol" 	"evdev"
	Option "Dev Name" 	"Logitech USB RECEIVER" #cat /proc/bus/input/devices
	Option "Dev Phys" 	"usb-0000:02:0c.2-2.2/input0" #cat /proc/bus/input/devices
	Option "Buttons" 	"12"
	Option "ZAxisMapping" 	"11 12 10 9"
	Option "Resolution" 	"800"
	Option "Emulate3Buttons"    "false"
EndSection
```

Here's the output of /var/log/Xorg.0.log:

```
(**) Configured Mouse: Protocol: evdev
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Buttons" "12"
(**) Option "Emulate3Buttons" "false"
(**) Option "ZAxisMapping" "11 12 10 9"
(**) Configured Mouse: ZAxisMapping: buttons 11, 12, 10 and 9
(**) Configured Mouse: Buttons: 12
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Dev Name" "Logitech USB RECEIVER"
(**) Option "Dev Phys" "usb-0000:02:0c.2-2.2/input0"
(EE) Configured Mouse: cannot open input device
(**) Option "Dev Name" "Logitech USB RECEIVER"
(**) Option "Dev Phys" "usb-0000:02:0c.2-2.2/input0"
(EE) Configured Mouse: cannot open input device
No core pointer

Fatal server error:
failed to initialize core devices
```

I changed nothing in xorg.conf and used the config file from 2.6.13.4.

The difference between "cat /proc/bus/input/devices" is that there's no "event1" associated with the 2.6.14 kernel:

```
I: Bus=0003 Vendor=046d Product=c50e Version=2510
N: Name="Logitech USB RECEIVER"
P: Phys=usb-0000:02:0c.2-2.2/input0
H: Handlers=event1 mouse0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

```

Any ideas?

---

### Post by RubenGonc on 2005-10-30
[QUOTE=berserker]My Logitech MX1000 laser mouse works in 2.6.13.4 but not in 2.6.14 (with or without the patch). Here's my xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option "Protocol" 	"evdev"
	Option "Dev Name" 	"Logitech USB RECEIVER" #cat /proc/bus/input/devices
	Option "Dev Phys" 	"usb-0000:02:0c.2-2.2/input0" #cat /proc/bus/input/devices
	Option "Buttons" 	"12"
	Option "ZAxisMapping" 	"11 12 10 9"
	Option "Resolution" 	"800"
	Option "Emulate3Buttons"    "false"
EndSection
```

Here's the output of /var/log/Xorg.0.log:

```
(**) Configured Mouse: Protocol: evdev
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Buttons" "12"
(**) Option "Emulate3Buttons" "false"
(**) Option "ZAxisMapping" "11 12 10 9"
(**) Configured Mouse: ZAxisMapping: buttons 11, 12, 10 and 9
(**) Configured Mouse: Buttons: 12
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Dev Name" "Logitech USB RECEIVER"
(**) Option "Dev Phys" "usb-0000:02:0c.2-2.2/input0"
(EE) Configured Mouse: cannot open input device
(**) Option "Dev Name" "Logitech USB RECEIVER"
(**) Option "Dev Phys" "usb-0000:02:0c.2-2.2/input0"
(EE) Configured Mouse: cannot open input device
No core pointer

Fatal server error:
failed to initialize core devices
```

I changed nothing in xorg.conf and used the config file from 2.6.13.4.

The difference between "cat /proc/bus/input/devices" is that there's no "event1" associated with the 2.6.14 kernel:

```
I: Bus=0003 Vendor=046d Product=c50e Version=2510
N: Name="Logitech USB RECEIVER"
P: Phys=usb-0000:02:0c.2-2.2/input0
H: Handlers=event1 mouse0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

```

Any ideas?[/QUOTE]


Go to [http://blog.blackdown.de/page/2/](http://blog.blackdown.de/page/2/) and then search for the topic "Logitech MX1000 Configuration". Hope it helps you:)

---

### Post by berserker on 2005-10-30
[QUOTE=RubenGonc]Go to [http://blog.blackdown.de/page/2/](http://blog.blackdown.de/page/2/) and then search for the topic "Logitech MX1000 Configuration". Hope it helps you:)[/QUOTE]

Thank you for the suggestion.  I tried that but no luck.  I think it's either that the new kernel handles USB mice differently or the NVIDIA drivers (I've tried both 7667 and 7676) aren't compatible with the new kernel.

---

### Post by Poul on 2005-10-30
can someone tell us or link to information about it?
Why/when should i bother?
What is so good about and what is changed comparing to the current one?
THX in advance.

---

### Post by Rob2687 on 2005-10-30
Got it working but as usuall with compiling a new kernel like this a lot of things stop working or need fixing after this. 

I really hope they put this in the repositories soon.

---

### Post by Dracontopes on 2005-10-31
[quote=RubenGonc]Yes, I forgot to mention to install libqt3-mt-dev. How-To updated. Or you can use "sudo make menuconfig" or "sudo make gconfig" (you need gtk+-2.0, glib-2.0 and libglade-2.0) instead.[/quote]

Thanks, I'm now happily compiling the kernel. :D

---

### Post by Hyun on 2005-10-31
[QUOTE=RubenGonc]
*In a terminal make sure you are in /usr/src/linux with full root access.
[/QUOTE]
tss tss... 
[QUOTE=Linus Torvas]
No need to be root to compile the kernel. You need to be root
to _install_ the kernel, but that's different.
[/quote] ;)

just add your user to src group
```
sudo addsuer username src
```
logout/login, and start How To. :razz:

---

### Post by Tomasz on 2005-10-31
All went fine here. Only thing that stopped working is usplash (completely blank screen), not that I care, it's probably due to my problematic LCD screen... Ubuntu seems to boot faster now, or maybe it's just my imagination. Anyway, thanks for the guide, that was my first kernel compilation!

PS How do I switch the root account off now?

---

### Post by HotShot on 2005-10-31
I have some errors during the patch and I´m unsure what to do

Sample:

```
can't find file to patch at input line 853
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: linux-2.6.14-ck1/kernel/exit.c
|===================================================================
|--- linux-2.6.14-ck1.orig/kernel/exit.c        2005-10-28 13:03:05.000000000 +1                                                                                       000
|+++ linux-2.6.14-ck1/kernel/exit.c     2005-10-28 13:06:03.000000000 +1000
--------------------------
File to patch:

```

just copy and paste the commands from the how-to and get some of these messages.

Edit: **problem solved**. the kernel-achive was corrupt :)

---

### Post by Tomasz on 2005-10-31
Does anyone else have problems with pmount? Removable drives and cdroms are only accessible through /media/cdrom0 (and so on), they don't appear on the desktop.

I'll try to translate the warning messeges when I click the icons in "Computer":
```

Warning: device /dev/hdc is already taken care of by /etc/fstab, given label has been ignored
mount: block device /dev/hdc is write-protected, mounting read-only
mount: /dev/hdc already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hdc is already mounted on /media/cdrom0
Error: cannot run pmount

```

Please, can anyone help me with this?

---

### Post by RubenGonc on 2005-10-31
[QUOTE=Hyun]tss tss... 
 ;)

just add your user to src group
```
sudo addsuer username src
```
logout/login, and start How To. :razz:[/QUOTE]


Yes...and you think that is more easy to add the user to the src group,logout,login or to gain full root access?...
And I am not so sure if that will work because the deb file will be created at /usr/src... but I don't know... What I posted work..I didn't say that there aren't more ways of doing this:P But I will try it later!Thanks;)

---

### Post by RubenGonc on 2005-10-31
[QUOTE=Poul]can someone tell us or link to information about it?
Why/when should i bother?
What is so good about and what is changed comparing to the current one?
THX in advance.[/QUOTE]


[http://www.internetnews.com/dev-news/article.php/3560061](http://www.internetnews.com/dev-news/article.php/3560061)

[http://wiki.kernelnewbies.org/LinuxChanges](http://wiki.kernelnewbies.org/LinuxChanges)

[http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.14](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.14)

---

### Post by theh0g on 2005-10-31
Cool, it worked...had problems with Nvidia (of course) but after second reinstall of drivers it worked fine. All I have to do now is get my other disk to work, it says it's either already mounted or busy. Nice HOWTO! :)

---

### Post by johannes on 2005-10-31
Thanks for this guide. :)  All worked flawlessly exept for installing the ATI drivers afterwards... Has anybody had any success with this? If so, did you need to do anything exept the things included in this how-to?

---

### Post by crypto178 on 2005-10-31
[QUOTE=Tomasz]Does anyone else have problems with pmount? Removable drives and cdroms are only accessible through /media/cdrom0 (and so on), they don't appear on the desktop.

I'll try to translate the warning messeges when I click the icons in "Computer":
```

Warning: device /dev/hdc is already taken care of by /etc/fstab, given label has been ignored
mount: block device /dev/hdc is write-protected, mounting read-only
mount: /dev/hdc already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hdc is already mounted on /media/cdrom0
Error: cannot run pmount

```

Please, can anyone help me with this?[/QUOTE]
Same problem here, slightly annoying, but a temporary fix is to run sudo umount '/media/drivename' and then double clicking the icon again. I have to do it every time I plug in the removable media again.

---

### Post by kaamos on 2005-10-31
Same here, pmount isn't working.

Also, I can't use the virtual terminals(?). Meaning that pressing ctrl+alt+f1 - f6 all show just a gray screen. When booting the screen is blank until gdm is started..

Any ideas how to fix these problems?

---

### Post by Capilano on 2005-10-31
:confused: Thank you for a well made Howto. It installed perfectly on my system with one annoyance: On the splash menu it says that the system failed to load local filesystems. I have no acces to partition that were previously accessible with breezy. Yhe fstab is the same as before; same for mtab. help please !

---

### Post by suRoot on 2005-10-31
[QUOTE=crypto178]Same problem here, slightly annoying, but a temporary fix is to run sudo umount '/media/drivename' and then double clicking the icon again. I have to do it every time I plug in the removable media again.[/QUOTE]


Same problem here.  Same fix / hack.

---

### Post by Dracontopes on 2005-10-31
Same problem here. Shame, back to 2.6.12 kernel for now untill there is a simple fix :)

---

### Post by Technoviking on 2005-10-31
[QUOTE=Dracontopes]Same problem here. Shame, back to 2.6.12 kernel for now untill there is a simple fix :)[/QUOTE]
Same here. 

I have been trying to add the ck performance patch to the Linux source (2.6.12) w/ Ubuntu patch added and tweak more for my Pentium M, but no luck yet.

---

### Post by TakisX on 2005-10-31
It compiled easily but when i install the nvidia drivers with tseliots how to as 100 times before it says everything ok but gnome does not start .What to do ?

I got back 2.6.12 and reinstalled nvidia drivers and it works
Maybe the new kernel does not like nvidia drivers

---

### Post by berserker on 2005-10-31
[QUOTE=TakisX]It compiled easily but when i install the nvidia drivers with tseliots how to as 100 times before it says everything ok but gnome does not start .What to do ?

I got back 2.6.12 and reinstalled nvidia drivers and it works
Maybe the new kernel does not like nvidia drivers[/QUOTE]

What does your /var/log/Xorg.0.log say?

KDE wouldn't start for me because the USB mouse couldn't be found.

---

### Post by suRoot on 2005-11-01
I somehow managed to get pmount to work.  I went back and recompiled the kernel again, this time making some changes to the config based on a config I'd used before, optimized for my thinkpad t40p.  After rebooting, I see that pmount works again.  Not sure why - I made quite a few changes to the config file - but my intent wasn't to fix pmount :-).

Anyways, I'm attaching my config in case someone smarter than I wants to compare the stock config to see what's missing.

My only problem now is that usplash, or whatever it's called, (I like Ubuntu, but I've spent a lot of time in the RedHat world) doesn't seem to work.  I just get text when booting, but that's okay.

---

### Post by GoA on 2005-11-01
Logitech MX700 USB-mouse and couldn't get x running. 

here's log

(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "fi"
(**) Generic Keyboard: XkbLayout: "fi"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "evdev"
(**) Configured Mouse: Protocol: evdev
(**) Option "Buttons" "10"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 10
(**) Configured Mouse: Protocol: evdev
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Buttons" "10"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 10
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Dev Name" "Logitech USB Receiver"
(**) Option "Dev Phys" "usb-*/input0"
(EE) Configured Mouse: cannot open input device
(**) Option "Dev Name" "Logitech USB Receiver"
(**) Option "Dev Phys" "usb-*/input0"
(EE) Configured Mouse: cannot open input device
No core pointer

Fatal server error:
failed to initialize core devices

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

### Post by RubenGonc on 2005-11-01
[QUOTE=Capilano]:confused: Thank you for a well made Howto. It installed perfectly on my system with one annoyance: On the splash menu it says that the system failed to load local filesystems. I have no acces to partition that were previously accessible with breezy. Yhe fstab is the same as before; same for mtab. help please ![/QUOTE]

You forgot to activate the kernel support for your filesystem (ext3, reiserfs). Try to recompile with support for your filesystem enabled.

---

### Post by RubenGonc on 2005-11-01
For people experimenting problems with the Nvidia drivers:

The drivers worked for me! What I did was remove the "nvidia-glx" package. Then I installed the ".run" nvidia drivers installer (you may have to change xorg.conf as described in [http://www.ubuntuforums.org/showthre...ghlight=nvidia).Then](http://www.ubuntuforums.org/showthre...ghlight=nvidia).Then) you restart X and everything shoul work.

Sorry but I can't help with ATI.

---

### Post by crypto178 on 2005-11-01
[QUOTE=suRoot]I somehow managed to get pmount to work.  I went back and recompiled the kernel again, this time making some changes to the config based on a config I'd used before, optimized for my thinkpad t40p.  After rebooting, I see that pmount works again.  Not sure why - I made quite a few changes to the config file - but my intent wasn't to fix pmount :-).

Anyways, I'm attaching my config in case someone smarter than I wants to compare the stock config to see what's missing.

My only problem now is that usplash, or whatever it's called, (I like Ubuntu, but I've spent a lot of time in the RedHat world) doesn't seem to work.  I just get text when booting, but that's okay.[/QUOTE]
Thanks for the attachment, I've generated a difference chart between my config and yours (using this site : [http://www.ranks.nl/cgi-bin/ranksnl/tools/difference.cgi](http://www.ranks.nl/cgi-bin/ranksnl/tools/difference.cgi) ). I'll investigate tomorrow which setting might be behind this mystery.
You can see the differences list here : [http://hlqg.free.fr/autres/diffs.html](http://hlqg.free.fr/autres/diffs.html) (mine is on the left, changes are marked with a | )
Upsplash works here :confused:

---

### Post by berserker on 2005-11-01
[QUOTE=GoA]Logitech MX700 USB-mouse and couldn't get x running.[/QUOTE]

I had the same problem with a Logitech MX1000 USB mouse.

---

### Post by nastya on 2005-11-01
[QUOTE=RubenGonc]You forgot to activate the kernel support for your filesystem (ext3, reiserfs). Try to recompile with support for your filesystem enabled.[/QUOTE]

I had recieved the same error on boot. However I know that I have fat32 support enabled. It's only my other hard drive that is affected as I have a fat32 partition on my drive with ubuntu and it mounts just fine. I tried to mount the partitions on the offending drive in terminal, but I recieve an error stating that it is already mounted or busy. I then tried to unmount it and it tells me that neither partition is mounted. I hope that I just overlooked something, as I don't want to go back to not having dri support for my video card (via unichrome).

---

### Post by Drifter on 2005-11-02
I see Linux.org a new kernel released:  2.6.14-git4, is this the new Vanilla kernel if so where is the patchset.  I need the new one in hopes that freeze ups while online will be taken care of.  Please inform me if this is so and how to get the info.

---

### Post by Drifter on 2005-11-02
[QUOTE=RubenGonc]This How-To will guide you through the compilation/installation of the 2.6.14 Vanilla Kernel (more recent than the one distribuited with Ubuntu 5.10) with the performance patchset by Kon Colivas.

1-Download what is needed:

Type in the command line:



Then download the following files to your Home directory:

[http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.14.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.14.tar.bz2)

[http://ck.kolivas.org/patches/2.6/2.6.14/2.6.14-ck1/patch-2.6.14-ck1.bz2](http://ck.kolivas.org/patches/2.6/2.6.14/2.6.14-ck1/patch-2.6.14-ck1.bz2)

2-Now, lets unpack the kernel source to /usr/src:

*Copy the source to /usr/src:

```
sudo cp linux-2.6.14.tar.bz2 /usr/src
```

*Change to /usr/src:

```
cd /usr/src
```

*Unpack it:

```
sudo tar -xvjf linux-2.6.14.tar.bz2
```

*Now lets change the created directory name:

```
sudo mv linux-2.6.14/ linux-2.6.14cK1
```

*Remove the symlink if there is one directory called linux:

```
sudo rm -rf linux
```

*Make the new symlink pointing for our 2.6.14 kernel source:

```
sudo ln -s /usr/src/linux-2.6.14cK1 linux
```

3-Now it's time to patch the kernel:

*Change to /usr/src/linux:

```
cd /usr/src/linux
```

*Switch to root user:

```
sudo -s -H
Password: <specify user password>
```

*Apply the patch:

```
sudo bzcat /home/username/patch-2.6.14-ck1.bz2| patch -p1
```

4-Kernel configuration:

*Import the configuration of the running kernel:

```
uname -r  
```  To see what kernel are you running (in my case it is 2.6.12-9-686).

```
sudo cp /boot/config-2.6.12-9-686 .config 
```   To copy the config file and use it as base for the new kernel configuration (Don't forget to choose the correct config file).

*Configure the kernel:

```
sudo make xconfig
```   

*While you may tweak your kernel configuration to your needs I will sugest you some tweaks:

In "General Setup" activate:

-Support for paging of anonymous memory (swap)
--Support for prefetching swapped memory

In "Processor type and features":

-Processor family     Choose the model of your processor.

Activate:

-Preemption Model
--Voluntary Kernel Preemption (Desktop)

-High Memory Support
--off                     -if you have less than 1 GB of RAM
--1GB Low Memory Support  -if you have 1GB of RAM
--4GB                     -if you have more than 1GB of RAM

-Timer frequency
--1000 Hz

In "Device drivers" go to "Block devices" and in "IO Schedulers" leave only the "CFQ I/O scheduler" activated, which provides the best performance.

In "Kernel hacking" uncheck "Kernel debugging".

Ctrl+S to save the kernel configuration and then close the window.

5-Let's build the kernel:

*In a terminal make sure you are in /usr/src/linux with full root access.

We will build a ".deb" file that can be installed in our Ubuntu system, using make-kpkg.

*In a terminal type:

```
make-kpkg clean

make-kpkg -initrd --revision=ck1 kernel_image
```

If there wasn't errors this will build the kernel and a ".deb" file will be created at /usr/src.
*To install it:

```
sudo dpkg -i kernel-image-2.6.14*.deb
```


6-Reboot and everything should be running ok! 
*Try:

```
uname -r   
```

to see that you are running the new kernel.


7-Nvidia graphic cards users:

To install Nvidia driver follow the guide (no need to install linux-headers as we have the source in /usr/src/linux:

[http://www.ubuntuforums.org/showthread.php?t=57368&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=57368&highlight=nvidia)


If you have any problem ask here.

Hope you like it!

Rúben Gonçalves:p[/QUOTE]

I did everything just like the guide said it all worked, but when I checked to see if I was using the new kernel, it said I was using 2.6.12-9-386.  I rebooted aftwards and then it said this.

---

### Post by RubenGonc on 2005-11-02
There is a new version of ck patchset.I will try it today...maybe it solves the pmount problem:???:
Anyone tried it?

---

### Post by RubenGonc on 2005-11-02
No:( It doesn't solves the pmount problem. Did anybody found the solution for this??? 
crypto178 did you realize what was the option to activate in the kernel config?

---

### Post by RubenGonc on 2005-11-02
Very easy solution:D 

Download [http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.6-1_i386.deb](http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.6-1_i386.deb)

Install doing
```
 sudo dpkg -i pmount_0.9.6-1_i386.deb

```

I think it will work!:D

---

### Post by btarlinian on 2005-11-03
I'm a newb, so forgive me for my ignorance.
What exactly is the ck Patchset. Is it necessary, or does it just improve performance?

---

### Post by crypto178 on 2005-11-03
[QUOTE=RubenGonc]Very easy solution:D 

Download [http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.6-1_i386.deb](http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.6-1_i386.deb)

Install doing
```
 sudo dpkg -i pmount_0.9.6-1_i386.deb

```

I think it will work!:D[/QUOTE]
It's working !
Thanks :)

---

### Post by _Pete_ on 2005-11-03
I did according to this how-to and everyrthing went well. There's a little problem:

In X/gnome if I don't move the mouse for a while the pointer freezes. Only way to get it move again is to go to the text console by pressing alt-Fx and then come back to X ...

Any ideas what might be causing this ? It's a bit annoying ...

---

### Post by nszabolcs on 2005-11-03
[QUOTE=btarlinian]What exactly is the ck Patchset. Is it necessary, or does it just improve performance?[/QUOTE]
Not necessary.
[http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)

---

### Post by _Pete_ on 2005-11-03
[QUOTE=nszabolcs]Not necessary.
[http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)[/QUOTE]


Btw, how are you supposed to notice this the boost to the performance that's caused by this patch? At least I didn't (yet) notice any difference. Maybe the difference can be noticed better with low end machines? I'm running P4@2.6GHz / 1G mem / nvidia6600 gt machine...

And any hints to that mouse problem ? :)

---

### Post by techstop on 2005-11-03
[QUOTE=RubenGonc]You forgot to activate the kernel support for your filesystem (ext3, reiserfs). Try to recompile with support for your filesystem enabled.[/QUOTE]

At what step do I need to start again to recompile? I tried starting from

"sudo make xconfig"

but I got this error;

make: *** No rule to make target `xconfig'.  Stop.

Do I need to start the whole process again? I have rebooted into my old kernel because the new one wouldn't let X start, and also have the problem of the filesystems failing to load. Cheers.

---

### Post by RubenGonc on 2005-11-03
[QUOTE=techstop]At what step do I need to start again to recompile? I tried starting from

"sudo make xconfig"

but I got this error;

make: *** No rule to make target `xconfig'.  Stop.

Do I need to start the whole process again? I have rebooted into my old kernel because the new one wouldn't let X start, and also have the problem of the filesystems failing to load. Cheers.[/QUOTE]

Go to /usr/src/linux (cd /usr/src/linux) and then:

```
sudo -s -H 
<password>
make clean
make xconfig
```

---

### Post by Hitman1 on 2005-11-03
The compile finishes with no errors but there is no .deb package generated. here is what I get last:

make[1]: Leaving directory `/usr/src/linux-2.6.14'
/usr/bin/make    \
                                ARCH=i386 prepare
make[1]: Entering directory `/usr/src/linux-2.6.14'
  CHK     include/linux/version.h
  SPLIT   include/linux/autoconf.h -> include/config/*
make[1]: Leaving directory `/usr/src/linux-2.6.14'
echo done >  stamp-kernel-configure
echo done >  stamp-configure

Anyone know what could the problem for not building the .deb file? I searched the whole filesystem for it incase it was placed somewhere else, but it is not there.

---

### Post by Wally68 on 2005-11-03
Thanks, Ruben for this how-to. The instructions led me down a path of errorless compilation and a headache free kernel upgrade. It's not the first kernel I've compiled, but it is the first time it worked for me on the first try. Now that I've got that far, I'll do it again, but try removing a few things (such as old cdrom support, extra network drivers, etc). Very clear, concise, and to the point. Thanks again.
Wally

---

### Post by nastya on 2005-11-03
If anyone who's compiled this kernel with the via unichrome support is reading this and you have recieved no errors, would you be willing to email me the deb? I cannot escape my mounting filesystems error with any of the debs I have compiled myself and would really like to have support for my video card.

---

### Post by Dany on 2005-11-03
[QUOTE=Capilano]:confused: Thank you for a well made Howto. It installed perfectly on my system with one annoyance: On the splash menu it says that the system failed to load local filesystems. I have no acces to partition that were previously accessible with breezy. Yhe fstab is the same as before; same for mtab. help please ![/QUOTE]

I have the same problem, my SATA drive dissapeared after the install, but I dont get the "system failed to load local filesystem" message. ex If I create a ext3 filsystem on the drive and mount it only root has access to the mounted dir...and when I reboot its not mounted anymore... and when I try to umount it, it says " /dev/sda1 not mounted". Then I try and mount it again and it says "busy or allready mounted".
So if somebody could please paste a correct config-file (x config)of the kernel compilation , so that all disks SATA,IDE or whatever works properly I and many other n00bs would be greatful :) other then this exelent guide ;)

---

### Post by sk545 on 2005-11-03
Keep in mind people, that just going to kernel 2.6.14 all of a sudden, will make things not work even if you copy over the config from the old kernel.

---

### Post by techstop on 2005-11-04
[QUOTE=RubenGonc]Go to /usr/src/linux (cd /usr/src/linux) and then:

```
sudo -s -H 
<password>
make clean
make xconfig
```[/QUOTE]

Many thanks!

OK. one more question. I'm not confident in getting this thing working at my current level of knowledge, how do I "uninstall" the broken kernel? ie. so that my old kernel is the default in grub etc. Cheers

---

### Post by desht on 2005-11-04
[QUOTE=Dany]I have the same problem, my SATA drive dissapeared after the install, but I dont get the "system failed to load local filesystem" message. ex If I create a ext3 filsystem on the drive and mount it only root has access to the mounted dir...and when I reboot its not mounted anymore... and when I try to umount it, it says " /dev/sda1 not mounted". Then I try and mount it again and it says "busy or allready mounted".
So if somebody could please paste a correct config-file (x config)of the kernel compilation , so that all disks SATA,IDE or whatever works properly I and many other n00bs would be greatful :) other then this exelent guide ;)[/QUOTE]

I also have this problem, and the system I'm using doesn't have SATA - just a pair of IDE drives.  There's obviously some more general problem here.

I have my /boot, /, /home & swap partititions on /dev/hdb, and I have a Windows partition & a reiserfs data partition on /dev/hda.  2.6.12 (i.e. stock with 5.10) works fine.  I've tried to build both 2.6.13.4 and 2.6.14 kernels, and both have the same problem: the /dev/hdb* partitions mount OK, but /dev/hda* partitions won't mount, failing with the "busy or already mounted" error.

I definitely have the right filesystem support; /home is also reiserfs and it mounts fine.  Loopback device mounting (e.g. mkisofs and "mount -o loop ...") also works fine.

New kernel config is based on /boot/config-2.6.12-9-386 + "make oldconfig".

---

### Post by Saiboogu on 2005-11-04
[QUOTE=techstop]Many thanks!

OK. one more question. I'm not confident in getting this thing working at my current level of knowledge, how do I "uninstall" the broken kernel? ie. so that my old kernel is the default in grub etc. Cheers[/QUOTE]

The kernel should be installed as "kernel-image-2.6.14-ck1" but just to make sure, search for it first...

```
saiboogu@GREEN:~$ dpkg --list | grep 2.6.14
ii  kernel-image-2.6.14-ck1   ck1    Linux kernel binary image for version 2.6.14
saiboogu@GREEN:~$ sudo apt-get remove kernel-image-2.6.14-ck1
```

That should take care of it.

Unfortunately I've had to do the same a few times now. :( Only my ext3 / partition will mount, my Reiser "data" disk won't mount, or my Samba shares.  Haven't done a lot in terms of troubleshooting yet - Anyone had any luck with this? The pmount .deb that was shared here was just supposed to fix problems with automounting removable devices, right? Seems my problem is more with the core "mount" command.

And yes, I made sure I enabled reiserfs support in my config.. Going to go back through the config again this evening to make sure I did not miss anything obvious.

---

### Post by darknuala on 2005-11-04
When I did this, I followed the instructions to a "T".  I had no errors whatsoever.  It worked like a charm.  Until I rebooted and tried to log in.  It said that my user id was navyn, but my home directory no longer existed.  I tried logging in anyways, because it gave me that option, and threw me to an .xsession error, saying that it could not find .gnome2lib and kicked me back to the login screen.  I logged in to failsafe, and it threw me to the root directory as my home directory.  When I browsed to see what was in /home, it was completely empty. I logged out, and logged into kde and I get an error about dcop something or other, then that $HOME/.drmc had the wrong file permissions, and should belong to the users group.

---

### Post by jg123 on 2005-11-04
I have a similar problem in that my external usb drive won't mount after installing 2.6.14-cks2. It works fine if I reload my 2.6.12 kernel. I am using autofs4 to mount the drive and automatically unmount it after a minute of activity. I get these errors in my log:

26 localhost automount: >> mount: /dev/sda1 already mounted or /misc/usbmaxtor busy
26 localhost automount: mount(generic): failed to mount /dev/sda1 (type vfat) on /misc/usbmaxtor
26 localhost automount: failed to mount /misc/usbmaxtor

I'm also getting these:
1 localhost kernel: [154356.036678] device-mapper: dm-linear: Device lookup failed

---

### Post by techstop on 2005-11-04
[QUOTE=Saiboogu]The kernel should be installed as "kernel-image-2.6.14-ck1" but just to make sure, search for it first...

```
saiboogu@GREEN:~$ dpkg --list | grep 2.6.14
ii  kernel-image-2.6.14-ck1   ck1    Linux kernel binary image for version 2.6.14
saiboogu@GREEN:~$ sudo apt-get remove kernel-image-2.6.14-ck1
```

That should take care of it.

Unfortunately I've had to do the same a few times now. :( Only my ext3 / partition will mount, my Reiser "data" disk won't mount, or my Samba shares.  Haven't done a lot in terms of troubleshooting yet - Anyone had any luck with this? The pmount .deb that was shared here was just supposed to fix problems with automounting removable devices, right? Seems my problem is more with the core "mount" command.

And yes, I made sure I enabled reiserfs support in my config.. Going to go back through the config again this evening to make sure I did not miss anything obvious.[/QUOTE]

That worked perfectly, thanks for your help. I'm just going to stick with my 2.6.12-9-k7 kernel for now.

---

### Post by kashms on 2005-11-05
I followed the instructions and succeeded in installing the new kernel with the patch. I even was able to build a nvidia module deb to install. However a couple of things, showstoppers in fact, did not work. So far I discovered that the side scolling on my touchpad is not working, and more importantly suspend stopped working as well. I'm just going to stick with 2.6.12-9-686 for now.

---

### Post by z!cHz@cH on 2005-11-05
This howto worked great for me:p 

People with notebooks:

This kernel wil stop cooking ur CPU. It handels CPU stepping a lot better now.

Thanks.

---

### Post by sfabel on 2005-11-05
Using the above method, my centrino notebook stopped its wireless support. There's always an error "unknown device" when I try to activate my wlan interface.

Any thoughts? Maybe these offical patches should be applied after all?

Thanks,
Stephan

---

### Post by tseliot on 2005-11-05
[QUOTE=sfabel]Using the above method, my centrino notebook stopped its wireless support. There's always an error "unknown device" when I try to activate my wlan interface.

Any thoughts? Maybe these offical patches should be applied after all?

Thanks,
Stephan[/QUOTE]
Perhaps you need ndiswrapper (I'm not sure though). If you need it here is a way to compile its modules [http://www.ubuntuforums.org/showthread.php?t=85064]("http://www.ubuntuforums.org/showthread.php?t=85064").

---

### Post by timczer on 2005-11-05
I followed this guide and everything for the most part seems to work.  I have an external hard drive that isn't mounted but so far that appears to be it.  

my question is, once completed, what can be removed from the /usr/src folder.  I have 432mb in that folder after the compiling.  Can any of this be removed?  That is a lot of memory to give up.

---

### Post by prasys on 2005-11-06
It really works , thanks for the superb guide

the .deb file is located in the /usr/src folder

---

### Post by shartrec on 2005-11-06
[QUOTE=Tomasz]All went fine here. Only thing that stopped working is usplash (completely blank screen), not that I care, it's probably due to my problematic LCD screen... Ubuntu seems to boot faster now, or maybe it's just my imagination. Anyway, thanks for the guide, that was my first kernel compilation!

PS How do I switch the root account off now?[/QUOTE]

This and the problem mentioned by another post about the tty consoles being blank are both related to the same problem.  Easy fix is remove any vga=nnn bootparam from your grub menu.lst file.  

The source of the problem is that the CONFIG_FB_VESA option becomes deselected when you start xconfig.   You need to manually select the option in xconfig.  I think this occurs because in the standard ubuntu config this is set ot 'm' and I think this is not supported, at least not in xconfig. It needs to be 'y'.

---

### Post by FiggyG on 2005-11-07
It worked for me :D  Just gotta iron out a few things as usual, like choosing the correct drivers to get my SATA drive workin :lol: This is the first kernel I've compiled on this machine and on Ubuntu. I've done kernels on basically every distro besides Ubuntu. I was pretty damn slick at it with Gentoo... ahhh good old days :)

Oh, forgot, it busted direct rendering with the ATI drivers. Nothing I can't fix ;)

---

### Post by fukusayo on 2005-11-07
[QUOTE=FiggyG]It worked for me :D  Just gotta iron out a few things as usual, like choosing the correct drivers to get my SATA drive workin :lol: This is the first kernel I've compiled on this machine and on Ubuntu. I've done kernels on basically every distro besides Ubuntu. I was pretty damn slick at it with Gentoo... ahhh good old days :)

Oh, forgot, it busted direct rendering with the ATI drivers. Nothing I can't fix ;)[/QUOTE]
I also lost 3D with my ATI card. However, I was unable to fix it. When you are successful, perhaps you could help a newbie out? Thanks in advance.

---

### Post by blakken on 2005-11-07
[QUOTE=sfabel]Using the above method, my centrino notebook stopped its wireless support. There's always an error "unknown device" when I try to activate my wlan interface.

Any thoughts? Maybe these offical patches should be applied after all?

Thanks,
Stephan[/QUOTE]
I downloaded the debian package for the kernel and let's say 2 things (and this without any kernel compilation matters as it is already compiled !) :
-first on my laptop my eth1(wireless device) stopped working
-second the scrolling isn't working with my mouse(and I didn't change my xorg though!!)

but for a change when mounting devices such as external hard drive or bluetooth key both of them are working!Didn't check the sound or my cd yet!
By the way anybody have any idea what's new about pocketpc stuff(synce) kernel adds and how to use it,and what is suppose the patch suppose to do theoritically for the pentium m?

---

### Post by BIGtrouble77 on 2005-11-07
When I try to install the ATI drivers this is what I get:

```
bob@bobbyhotep:/lib/modules/fglrx$ sudo sh make_install.sh
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
FATAL: Error inserting fglrx (/lib/modules/2.6.14-ck1/kernel/drivers/char/drm/fglrx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
failed.

```
Hopefully someone knows what to do about this.

---

### Post by zarathustra on 2005-11-07
I get this error when trying to compile the new kernel:

> drivers/built-in.o: In function `init_nandsim':
nandsim.c:(.text+0x7bca8): undefined reference to `nand_flash_ids'
drivers/built-in.o: In function `ns_init_module':
: undefined reference to `nand_scan'
drivers/built-in.o: In function `ns_init_module':
: undefined reference to `nand_default_bbt'
drivers/built-in.o: In function `ns_cleanup_module':
nandsim.c:(.exit.text+0x35e): undefined reference to `nand_release'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.14cK1'
make: *** [stamp-build] Error 2

---

### Post by StefanoCole on 2005-11-08
I just wanted to know the meaning of the term "Vanilla" used for a Kernel.

Thanks, Stefano

---

### Post by Lifesteeler on 2005-11-08
My wlan stopped working with this kernel. What can I do about it? Also, should I use the "Pentium M" choice with my Celeron M?

---

### Post by tare on 2005-11-08
[QUOTE=GoA]Logitech MX700 USB-mouse and couldn't get x running. 
[/QUOTE]

First of all, thanks for a great HowTo!
I got finally my MX700 to work. I had configured evdev as loadable module but could not see it with
```
lsmod | grep evdev
```
and /proc/bus/input/devices had no "eventx" as a mouse handler. So I changed kernel .config to look like this:
```

#
# Userland interfaces
#
CONFIG_INPUT_MOUSEDEV=y
CONFIG_INPUT_MOUSEDEV_PSAUX=y
CONFIG_INPUT_MOUSEDEV_SCREEN_X=1024
CONFIG_INPUT_MOUSEDEV_SCREEN_Y=768
CONFIG_INPUT_JOYDEV=m
CONFIG_INPUT_TSDEV=m
CONFIG_INPUT_TSDEV_SCREEN_X=240
CONFIG_INPUT_TSDEV_SCREEN_Y=320
[COLOR="Red"]CONFIG_INPUT_EVDEV=y[/COLOR]
# CONFIG_INPUT_EVBUG is not set

```

Recompile and voila! I can define evdev as Protocol and all my buttons and wheel work! :lol:

---

### Post by tseliot on 2005-11-08
[QUOTE=StefanoCole]I just wanted to know the meaning of the term "Vanilla" used for a Kernel.

Thanks, Stefano[/QUOTE]

Vanilla means "plain and simple" and it means that it has no specific features (i.e. it is not adapted to any distro in particular) and it is not patched (at least in theory) and of course it is the source code made by Linux Torvalds & colleagues.

Somebody correct me if I'm wrong, please.

---

### Post by benplaut on 2005-11-09
anyone know how to get restricted modules working? atheros based wireless, not being found by ifconfig :(

<<edit>>

this thread:
[http://ubuntuforums.org/showthread.php?t=75451](http://ubuntuforums.org/showthread.php?t=75451)
totally rocks

---

### Post by GoA on 2005-11-09
[QUOTE=tare]First of all, thanks for a great HowTo!
I got finally my MX700 to work. I had configured evdev as loadable module but could not see it with
```
lsmod | grep evdev
```
and /proc/bus/input/devices had no "eventx" as a mouse handler. So I changed kernel .config to look like this:
```

#
# Userland interfaces
#
CONFIG_INPUT_MOUSEDEV=y
CONFIG_INPUT_MOUSEDEV_PSAUX=y
CONFIG_INPUT_MOUSEDEV_SCREEN_X=1024
CONFIG_INPUT_MOUSEDEV_SCREEN_Y=768
CONFIG_INPUT_JOYDEV=m
CONFIG_INPUT_TSDEV=m
CONFIG_INPUT_TSDEV_SCREEN_X=240
CONFIG_INPUT_TSDEV_SCREEN_Y=320
[COLOR="Red"]CONFIG_INPUT_EVDEV=y[/COLOR]
# CONFIG_INPUT_EVBUG is not set

```

Recompile and voila! I can define evdev as Protocol and all my buttons and wheel work! :lol:[/QUOTE]

Could I get more specific details about the how did you do that. :D I'm a noob you know. :)

---

### Post by Lifesteeler on 2005-11-09
My network card is Intel Pro Wireless 2200BG, i found out that i should use ndiswrapper, but how do i do this? Should i include it in the kernel when building or what? Need help, cause i want my speedy kernel to work...

---

### Post by tare on 2005-11-09
[QUOTE=GoA]Could I get more specific details about the how did you do that. :D I'm a noob you know. :)[/QUOTE]

Just do your normal make xconfig and go to "Input device support - Generic input layer" and select "Event interface" to be built in, not as module.
And recompile!

---

### Post by jewelz on 2005-11-09
What about conexant usb adsl modems? There seems to be built-in drivers, but i don't know how to make them work!

---

### Post by quintok on 2005-11-09
hi, is there anything in this how-to that could/is disabiling ntfs support? I can mount the device fine on the ubuntu 5.1 livecd but following this I cannot load ntfs even if it's built into the kernel (not as a module)

---

### Post by Maverick911 on 2005-11-09
[QUOTE=tseliot]Vanilla means "plain and simple" and it means that it has no specific features (i.e. it is not adapted to any distro in particular) and it is not patched (at least in theory) and of course it is the source code made by Linux Torvalds & colleagues.

Somebody correct me if I'm wrong, please.[/QUOTE]

So does that mean that I'm really not running ubuntu anymore with this kernel?

Wish You Were Here - Pink Floyd

---

### Post by quintok on 2005-11-09
no, it's still ubuntu.

---

### Post by allans on 2005-11-10
Just wanted to say thanks for the great how to, everything fine here and definitely a little faster!

Allan

---

### Post by berserker on 2005-11-10
[QUOTE=tare]I got finally my MX700 to work.[/QUOTE]

Thank you!  I couldn't figure out what was going on with my MX1000.  For some reason the new 2.6.14 and 2.6.14.1 kernels need EVDEV compiled into the kernel.

---

### Post by spoilerhead on 2005-11-10
if someone would like a try:

[http://stud3.tuwien.ac.at/~e0326004/kernel/kernel-headers-2.6.14-sph1-686_2_i386.deb](http://stud3.tuwien.ac.at/~e0326004/kernel/kernel-headers-2.6.14-sph1-686_2_i386.deb)
[http://stud3.tuwien.ac.at/~e0326004/kernel/kernel-image-2.6.14-sph1-686_2_i386.deb](http://stud3.tuwien.ac.at/~e0326004/kernel/kernel-image-2.6.14-sph1-686_2_i386.deb)

read more at:
[http://www.ubuntuusers.de/viewtopic.php?t=14688&start=30](http://www.ubuntuusers.de/viewtopic.php?t=14688&start=30) (in german)

ck3 patchset included, vesa-tng, speedstep fix for pentium M (Dothan)

for feedback
spoilerhead_remove_m3_(at)_brennercom.net

---

### Post by Eazy© on 2005-11-11
Has anyone found a solution to the "mount problem"?
I cant mount my ntfs partition though I think ntfs support its activated as a module (If I run menuconfig I see that its activated).
If I try to mount it it says that its already mounted or busy.

---

### Post by tseliot on 2005-11-11
[QUOTE=Maverick911]So does that mean that I'm really not running ubuntu anymore with this kernel?

Wish You Were Here - Pink Floyd[/QUOTE]

It's just that you're not using a kernel with Ubuntu patches. Ubuntu is more than kernel patches, it's an entire OS

---

### Post by ibanez88 on 2005-11-11
ipw2200 should be built as a module by default.  You need to download the firmware from sourceforge (use version 2.2) and extract the tarball into /usr/lib/hotplug/firmware.  Worked for me.  Don't keep the tarball itself in that folder.

I can boot from this new kernel but I'm getting errors on bootup related to my Realtek 8139 ethernet.  Also my SD slot not working (nothing new there, but I thought the new Winbond SD support might help).. I probably don't have the right devices / fstab; nothing shows up in dmesg.  Nonetheless  any pointers related to this or my Realtek 8139 are appreciated.

THANKS for the how-to!

---

### Post by ColdWind on 2005-11-12
Thanks!
I compiled it with cK5 Patchset and works fine in my laptop (at the moment).

---

### Post by adamb10 on 2005-11-12
How big of a performance boost does this kernel provide?

---

### Post by curtis on 2005-11-12
Hi,
I am using 2.6.14.1-cK1 fine here.
That is on a Dell Inspiron 5150.
Just having an issue with the nvidia module.
I end up needing to re-install it every boot up.
It is in /etc/modules though, and modprobing nvidia does not work.
I have a feeling it could be InitNG possibily, will check now.

Any one else running the 2.6.14.x kernel with a Nvidia graphics card?
Even better if they are using InitNG.

---

### Post by tseliot on 2005-11-12
[QUOTE=curtis]Hi,
I am using 2.6.14.1-cK1 fine here.
That is on a Dell Inspiron 5150.
Just having an issue with the nvidia module.
I end up needing to re-install it every boot up.
It is in /etc/modules though, and modprobing nvidia does not work.
I have a feeling it could be InitNG possibily, will check now.

Any one else running the 2.6.14.x kernel with a Nvidia graphics card?
Even better if they are using InitNG.[/QUOTE]
Have a look at Point 7 of my guide:
[http://www.ubuntuforums.org/showthread.php?t=85064]("http://www.ubuntuforums.org/showthread.php?t=85064")
it explains how to compile the nvidia modules together with your kernel (as packages, just like Ubuntu's restricted modules)

---

### Post by quintok on 2005-11-12
[QUOTE=Eazy©]Has anyone found a solution to the "mount problem"?
I cant mount my ntfs partition though I think ntfs support its activated as a module (If I run menuconfig I see that its activated).
If I try to mount it it says that its already mounted or busy.[/QUOTE]

I'm glad I'm not the only one in this boat :)

---

### Post by nastya on 2005-11-12
[QUOTE=quintok]I'm glad I'm not the only one in this boat :)[/QUOTE]

There's definately a few of us with that problem, but no one seems to know what is going on. I've even had 3 or 4 others take a look at my .config, but none of them could find anything wrong.

---

### Post by synd7 on 2005-11-13
Cheers for the guide
2.6.14-ck4 is running fine. Except that i no longer have fglrx working. does anyone know how to get it up and running? ive tried the method in the 'kernel compilation for newbies' thread but I end up tith a .deb that requires the fglrx-kernel-common package which is not in the repositories.

Is there some way to build the source for the xorg-driver-fglrx package? I really hate having to reboot to a different kernel when i want 3d accelearation.

---

### Post by daenforcer on 2005-11-13
[QUOTE=synd7]Cheers for the guide
2.6.14-ck4 is running fine. Except that i no longer have fglrx working. does anyone know how to get it up and running? ive tried the method in the 'kernel compilation for newbies' thread but I end up tith a .deb that requires the fglrx-kernel-common package which is not in the repositories.

Is there some way to build the source for the xorg-driver-fglrx package? I really hate having to reboot to a different kernel when i want 3d accelearation.[/QUOTE]

:D I got the latest ATI driver (8.18.10) to work with 2.6.14+ck5 just fine.  Follow the instructions located in the below 2 threads:

[http://ubuntuforums.org/showthread.php?t=78466](http://ubuntuforums.org/showthread.php?t=78466)

[http://ubuntuforums.org/showthread.php?t=76116&page=26](http://ubuntuforums.org/showthread.php?t=76116&page=26)

Let me know if you need any assistance.

---

### Post by richardh on 2005-11-13
Brilliant. Its fixed the slow boot problem on my Toshiba. 

BUT I cant get Suspend (hibernate) from the System->Logout->hibernate menu

The computer switches off but then does not completely power down.

I would like to instal suspend2, but the patches given elsewhere in the forum are for the 6.12 ubuntu kernel

---

### Post by Zed on 2005-11-13
After doing all this, hddtemp didn't work anymore. Following these instructions:

[http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux) 

I found the right patch for 2.6.14 to fix it.

Thanks for the howto -- it was easier than it looked.

---

### Post by gar on 2005-11-13
hi ,
with , my msi S270 notebook , i have some sound with the new kernel , great , thanks
however , the USB did'nt work ... i havn't change anything in the menuconfig , should i ?
is there a patch ? i just begin in kernel compilation , so i don't understand everything ,sorry
if someone could help ...

---

### Post by curtis on 2005-11-13
[QUOTE=tseliot]Have a look at Point 7 of my guide:
[http://www.ubuntuforums.org/showthread.php?t=85064]("http://www.ubuntuforums.org/showthread.php?t=85064")
it explains how to compile the nvidia modules together with your kernel (as packages, just like Ubuntu's restricted modules)[/QUOTE]

Hi,
I managed to fix it by unistalling the current driver and re-installing it.
Wierd that just doing the installer did not work (Does show uninstalling)
I did already have the modules done.
Thank you for suggesting I read through that guide though.

---

### Post by LPK on 2005-11-13
With this kernel 2.6.14 dont work my fat32 disc in Breezy. With defoult kernel 2.6.12-9 is OK.
?????????

---

### Post by Eazy© on 2005-11-15
> **Eazy&#169 said:**
> Has anyone found a solution to the "mount problem"?
I cant mount my ntfs partition though I think ntfs support its activated as a module (If I run menuconfig I see that its activated).
If I try to mount it it says that its already mounted or busy.

[QUOTE=quintok]I'm glad I'm not the only one in this boat :)[/QUOTE]

I think I maybe have found a solution to the mount problem I have. If I try to mount my ntfs partition on hda with: "sudo mount -o loop /media/windows" I can access my ntfs partiton. I'm going to once again (5:th time :P ) compile the kernel and remove "Loopback device support" (located under "Device Drivers") and see if that does the trick. I'm also using the latest ck5-patch instead 

I see myselfe still after 2 years with linux (off and on) as a newbee as only thing I do is to test things in guides, but I always seems to forget every thing afterwards and not lerning anything :P

Edit: Nope that didnt work to remove "Loopback device support" . Now I cant mount it even with: "sudo mount -o loop /media/windows" (offcourse...stupid me). Anyone knows how the line should look in fstab with the "-o loop" command in it? 

"/dev/hda1       /media/windows  -o loop ntfs    nls=utf8,umask=0222 0       0"  dont work. 

I dont get the error mesage when "mouting local filesystem" when it boot with that line, but its not mounted when gnome starts. Perhaps the line in fstab should look different?

Going to compile 1 last time now and not leaving out "Loopback device support"

Edit2: Ok, I have now compiled for the last time (wont do it again) exactly as the guide, with the only diffrence that I selected write support for ntfs (dont think it makes anny difference). I edited my fstab to look like this: 

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222,[COLOR="Red"]loop[/COLOR] 0       0

Changes in red

This makes my ntfs partition to load at startup. Hope someone else than me have some use of it...

---

### Post by lmandrake on 2005-11-15
@richardh: I'm just trying to follow this guide [on the suspend2 Website]("http://wiki.suspend2.net/DistroAndHardwareSetup/Ubuntu_Breezy_Badger?highlight=(ubuntu)") with 2.6.14-2. Sadly it's not working yet. But i'll post an update when it's hopefully working.

One question: How is ck working with 2.6.14-2? When I try to apply the ck patch it complains about nearly ervery file...

---

### Post by curtis on 2005-11-15
[QUOTE=lmandrake]@richardh: I'm just trying to follow this guide [on the suspend2 Website]("http://wiki.suspend2.net/DistroAndHardwareSetup/Ubuntu_Breezy_Badger?highlight=(ubuntu)") with 2.6.14-2. Sadly it's not working yet. But i'll post an update when it's hopefully working.

One question: How is ck working with 2.6.14-2? When I try to apply the ck patch it complains about nearly ervery file...[/QUOTE]

What cK patchset are you using?
I am using the cK1 one perfect with the 2.6.14.2 GNU/Linux kernel.

---

### Post by kaamos on 2005-11-15
[QUOTE=lmandrake]One question: How is ck working with 2.6.14-2? When I try to apply the ck patch it complains about nearly ervery file...[/QUOTE]

ck5 includes 2.6.14-2 patches, so you have to patch the 2.6.14-1 source. Linux-militia also offers pre-ck-patched kernel sources so you could try one of those.

[http://www.linux-militia.net/kernel/ck/](http://www.linux-militia.net/kernel/ck/)

---

### Post by nastya on 2005-11-15
[QUOTE=Eazy©]/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222,[COLOR="Red"]loop[/COLOR] 0       0

Changes in red

This makes my ntfs partition to load at startup. Hope someone else than me have some use of it...[/QUOTE]

Yay, now my partitons on my other drive will mount! Now I can play planet penguin racer at fullspeed AND access my other drive with my data. Thank you so much! :)

---

### Post by RedDragon on 2005-11-16
Kernel update: ok

Only problem is that it doesn 't detect my 'WMP54G' wifi adapter anymore. Is there an explanation. Did i forget an option during kernel compilation??

---

### Post by lmandrake on 2005-11-16
@curtis: Thanks. I now applied ck1 too 2.4.16-2 without errors.

Kernel compiles and installs fine now. But I can't boot it because root seems not to be mountable.

```
mount: mounting /dev/root on /root failed: Device or resource busy
...
mount: Mounting /root/dev on /dev/.static/dev failed: No such device or directory
mount: Mounting /dev on /root/dev failed: No such device or directory
```

I included my ide chipset driver, sata, all filetypes into the from the original ubuntu kernel inheritated kernel config. Don't know if it's related to the initrd scripts or if I'm missing something important in my config (see attached file).

---

### Post by timczer on 2005-11-16
I asked this question earlier, but was unable to get a response.  I am new to compiling a kernel, and this went really well.  My question is, once done, what can I remove fromthe source folder I built the kernel in?  It is using a lot of memory that I would like to free up.  Thanks.

---

### Post by lmandrake on 2005-11-16
You could remove the whole folder /usr/src/linux, don't forget to install kernel-headers as well, perhaps you need it later for some other kernel modules.
But creating an archive and burning it to cdr/dvdr is recommended.

---

### Post by outr on 2005-11-17
Tried this how-to with the current ck5 patch.
Compiled ok and everything seems to work. 
A few quirks though:
iwconfig gives the following warning: 
Driver for device eth1 has been compiled with version 19 of Wireless Extension, while this program supports up to version 18.
Some things may be broken...

it works ok still. waproamd seems to have some problems, will have to look into that.

Even the boot-up splash screen works, but now it's displaying xubuntu instead of ubuntu ? not a big problem but wtf?

---

### Post by LeTon on 2005-11-18
Hi, 
After installation of new  kernel ( which went flawlesly, and I finally got SOUND with Intel ICH 6) , Firofox would not launch:(
I was messing around with the browser befor new kernel...so that must be it...just don't know how to fix it. Please...
In terminal it returns:

INTERNAL ERROR on Browser End: Expected version > 5! Version = 4

System error?: : No such file or directory

Tried  reinstallation already.
Thank you in advance

---

### Post by domino on 2005-11-18
Reading through the 12 pages I was able to gather almost all the information I need to compile this myself. I just need some more info though.

ATI drivers: Solved
Mount ntfs: Solved
Mount FAT32: ?
Mount HFS+: ?

Please comment on the last 2.

---

### Post by tasca on 2005-11-18
I compiled kernel 2.6.15 and now it usplash does not work and vmware has that to configure all time to load ("runme.pl"), and no reboot (halt ok).
I am use patch-2.6.15-rc1-ck1.bz2.

somebody can help?

---

### Post by beeldings on 2005-11-18
I followed this guide on two different machines, and it worked flawlessly on both occassions. On the one machine, I followed your guide, step-by-step, and it worked perfectly. On the second machine, I took my time and tweaked the kernel to suit this machine, removing all unnecessary modules and drivers, and wow, there was a very noticeable increase in the overall performance of this machine (PII 400 Mhz, 128 MB SDRAM).

---

### Post by waydaws on 2005-11-21
One question I have is that when I go to configure my kernel options, everything is already selected.  For instance, where it says, 

[INDENT]...*While you may tweak your kernel configuration to your needs I will sugest you some tweaks:

In "General Setup" activate:

-Support for paging of anonymous memory (swap)
--Support for prefetching swapped memory

In "Processor type and features":

-Processor family Choose the model of your processor.[/INDENT]

In my config everything in general setup is already selected.  Am I supposet to deselect everything but the above.

And...

For processor type, I'm not sure what to use.  In my case it is running in VMWare.  The processor type is listed as unknown in device manager.  I'm not sure if I should just use 386 or the chose Pentium 4 (what the host is).

Anyone done this in vmware?

---

### Post by redlaw28 on 2005-11-23
Hi
nice guide 
i followed it when i compiled my nitro2 kernel it worked flawless

thx!

---

### Post by Locutus on 2005-11-23
I compiled the kernel but there are some errors. Is there a way for me to uninstall it so that I can give it a second go?

I get the following when I try and uninstall:

root@ubuntu:/usr/src# dpkg -r kernel-image-2.6.14-ck5_ck1_i386.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
root@ubuntu:/usr/src#

Any ideas?

Thanks for any help you can give me.

---

### Post by Rob2687 on 2005-11-23
You can search for it in synaptic and remove it from there.

---

### Post by Locutus on 2005-11-23
That worked like a charm. Thank you.

---

### Post by mistergq on 2005-11-27
I built the kernel, and then get this error when I try to install it.


dpkg: status database area is locked by another process

I am the root user in the terminal window.  Any other suggestions?
------------------------------
never mind, I had the Synaptic opened.

---

### Post by Raoul Duke on 2005-11-27
Is there a list of patches used to produce the default Ubuntu kernels? I would like to apply them selectively...
Thanks

---

### Post by henriquemaia on 2005-11-28
Nice howto.

Worked flawlessly. Nothing like our own kernels!

---

### Post by devanb on 2005-11-28
I just want to thank you for the great guide.  I've tried to install my wireless drivers using Fedora and Gentoo, but unsuccessfully when trying to recompile my kernel.

Your guide was excellent and helped me get Ubuntu working.

Thanks again,

Devan

---

### Post by obscenic on 2005-11-28
When I tried to do my apt-getting, I got this:
```

mark@susty:~$ sudo apt-get install libqt3-headers libqt3-mt-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: xlibs-static-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libxext-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libxrandr-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libsm-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libxmu-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libice-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libx11-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libxt-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libmng-dev (>= 1.0.3) but it is not going to be installed
                 Depends: libpng12-0-dev
                 Depends: libjpeg62-dev but it is not going to be installed
                 Depends: libfreetype6-dev but it is not going to be installed
                 Depends: xlibmesa-gl-dev but it is not going to be installed or
                          libgl-dev
                 Depends: xlibmesa-glu-dev but it is not going to be installed or
                          libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
                 Depends: libxft-dev but it is not going to be installed
                 Depends: libxrender-dev but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxinerama-dev but it is not going to be installed
E: Broken packages

```

---

### Post by mistergq on 2005-11-28
Is there way to get have this kernel built with Alsa 1.0.10?  If so how?

Thanks

---

### Post by shaggydoo on 2005-11-29
Hi, I was wondering, how long should this take? I've been waiting a couple of hours now, but it's still building the kernel. (Duron 800mhz, 256mb RAM)

---

### Post by Rob2687 on 2005-11-29
Probably atleast an hour...depending on how much stuff you have left in to compile and stuff. It takes over an hour on my 1Ghz PIII and I probably have a lot of useless crap that could probably be disabled since my PC doesn't need it.

---

### Post by shaggydoo on 2005-11-29
Oh, I see. Great, thanks Rob!

---

### Post by sswords on 2005-11-30
[QUOTE=curtis]Hi,
I am using 2.6.14.1-cK1 fine here.
That is on a Dell Inspiron 5150.
Just having an issue with the nvidia module.
I end up needing to re-install it every boot up.
It is in /etc/modules though, and modprobing nvidia does not work.
I have a feeling it could be InitNG possibily, will check now.

Any one else running the 2.6.14.x kernel with a Nvidia graphics card?
Even better if they are using InitNG.[/QUOTE]

I'm not using InitNG, but I am having a similar problem where I can't start gdm or x on reboot without first running the nvidia installer.  I've tried a number of things I thought sure would work - uninstalled all other nvidia packages including linux-restricted-modules for the other kernels I have, turned off the nvidia-glx service.  I even made a debian package using
sudo checkinstall --nodoc --strip=no NVIDIA-Linux-x86-1.0-7174-pkg1.run
 -- then next time I rebooted, x wouldn't start.  I extracted the package to its own directory and checked the differences between what was in that folder and what was installed ("sudo diff -qr . / | grep -v 'Only in /'") and everything was the same.  Once I ran the installer again, everything worked, but there were several changes evident when I ran that diff again, including the nvidia.ko module and several numbered files in /var/lib/nvidia.

The specific error that occurs is (in /var/log/Xorg.0.log)
```
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.
```
However, the nvidia module is in fact loaded according to lsmod, (it's listed in /etc/modules), and doing "rmmod nvidia; modprobe nvidia" doesn't give any sort of error.  (I've tried "insmod [actual path to nvidia.ko]" just in case it was somehow loading a different nvidia module, too.)

Any ideas?  At this point I'm tempted to make an init script that runs the nvidia installer every time I reboot.

I have a Geforce2 GTS so I use an older version of the installer (and the nvidia-legacy packages when using an official kernel), but it doesn't seem like that's any problem because it does work; just requires a reinstall every boot.

---

### Post by curtis on 2005-11-30
I got it working by adding modules_install to the build line.
Then installing the deb created by that...

---

### Post by taciturn on 2005-11-30
I just gave this a shot and everything went great, with the exception of one problem. My samba shares are no longer automounted at boot, I can still mount them after I log into gnome, but they're no longer mounted automatically.

I cant figure out why this is, anyone have any suggestions?

---

### Post by sswords on 2005-11-30
I figured out why I need to reinstall the nvidia drivers every time I reboot: the nodes /dev/nvidia[0-9] and /dev/nvidiactl don't appear when the module is loaded, but get created by the installer.  I suppose there's probably some problem with my udev configuration (though I haven't changed anything.)  Does anyone know how to make them appear?

---

### Post by xUmaRix on 2005-12-02
hi guys.
I already compile kernel 2.6.14.3 with ck-6 patch on hoary
but got error on bootup can't mount to devfs maybe i didn't config it on kernel and device-mapper:dm-linear:Device lookup fail.My orinoco gold driver also not load automatically.The worst part is i can't load my fluxbox. I read the xorg.log and it shows like font error coz i use artwiz font.I also can't boot to blackbox.
Izzit this patch not suitable for hoary or is there any extra setting or step i should add.

---

### Post by coaxx on 2005-12-05
2.6.14 worked well, thank You very much, this is a usefull HowTo!

some problems here with 2.6.15 / rc2 /rc5, I tried w/ and w/o cK Patch!

("Fehler" is "error" in english :)
```

  CC      kernel/irq/handle.o
In file included from include/asm/fixmap.h:27,
                 from include/asm/smp.h:16,
                 from include/linux/irq.h:13,
                 from kernel/irq/handle.c:9:
include/asm/acpi.h: In Funktion »__acpi_acquire_global_lock«:
include/asm/acpi.h:67: Fehler: »boot_cpu_data« nicht deklariert (erste Benutzung in dieser Funktion)
include/asm/acpi.h:67: Fehler: (Jeder nicht deklarierte Bezeichner wird nur einmal aufgeführt
include/asm/acpi.h:67: Fehler: für jede Funktion in der er auftritt.)
include/asm/acpi.h: In Funktion »__acpi_release_global_lock«:
include/asm/acpi.h:79: Fehler: »boot_cpu_data« nicht deklariert (erste Benutzung in dieser Funktion)
make[3]: *** [kernel/irq/handle.o] Fehler 1
make[2]: *** [kernel/irq] Fehler 2
make[1]: *** [kernel] Fehler 2
make[1]: Verlasse Verzeichnis »/usr/src/linux-2.6.15-rc5«
make: *** [stamp-build] Fehler 2

```

Anybody?

---

### Post by limit223 on 2005-12-05
> **coaxx]2.6.14 worked well, thank You very much, this is a usefull HowTo!

some problems here with 2.6.15 / rc2 /rc5, I tried w/ and w/o cK Patch!

("Fehler" is "error" in english :)
```

  CC      kernel/irq/handle.o
In file included from include/asm/fixmap.h:27,
                 from include/asm/smp.h:16,
                 from include/linux/irq.h:13,
                 from kernel/irq/handle.c:9:
include/asm/acpi.h: In Funktion &#187 said:**
> : *** [kernel/irq/handle.o] Fehler 1
make[2]: *** [kernel/irq] Fehler 2
make[1]: *** [kernel] Fehler 2
make[1]: Verlasse Verzeichnis &#187;/usr/src/linux-2.6.15-rc5&#171;
make: *** [stamp-build] Fehler 2

```

Anybody?


I've got my 2.6.15-rc1-ck1 patched from here, a week or two ago,  I copiled without any error you have above...you may find the latest kernel as well ...already patched it.
[http://www.linux-militia.net/modules/news/](http://www.linux-militia.net/modules/news/)

---

### Post by coaxx on 2005-12-05
thanks for the hint. Meanwhile I have dist-upgraded to dapper :cool: 2.6.15-x compiles now easily.

---

### Post by ZedLord on 2005-12-09
I Followed the Guide upto **5-Lets Build the kernel:**

I'm Trying to compile kernel 2.6.14.3 along with patch-2.6.14-ck6

when i type-in : **sudo make-kpkg -initrd --revision=ck6 kernel_image**

i get the Following error after sometime and return to the shell

>   CC      kernel/time.o
  CC      kernel/softirq.o
  CC      kernel/resource.o
kernel/resource.c:480: warning: â€˜__check_regionâ€™ is deprecated (declared at kernel/resource.c:468)
  CC      kernel/sysctl.o
kernel/sysctl.c:671: error: redefinition of â€˜one_hundredâ€™
kernel/sysctl.c:665: error: previous definition of â€˜one_hundredâ€™ was here
kernel/sysctl.c:748: error: â€˜vm_swappinessâ€™ undeclared here (not in a function)
make[2]: *** [kernel/sysctl.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.14.3cK6'
make: *** [stamp-build] Error 2


What am I Doing Wrong, please help Me!

---

### Post by curtis on 2005-12-09
[QUOTE=ZedLord]I Followed the Guide upto **5-Lets Build the kernel:**

I'm Trying to compile kernel 2.6.14.3 along with patch-2.6.14-ck6

when i type-in : **sudo make-kpkg -initrd --revision=ck6 kernel_image**

i get the Following error after sometime and return to the shell



What am I Doing Wrong, please help Me![/QUOTE]
Hi,
Patch the 2.6.14 kernel with the 2.6.14-ck6 patchset.
As it includes the patches in 2.6.14.1, 2.6.14.2, 2.6.14.3

---

### Post by windowsrefund on 2005-12-10
[QUOTE=RubenGonc]

-High Memory Support
--off                     -if you have less than 1 GB of RAM
--1GB Low Memory Support  -if you have 1GB of RAM
--4GB                     -if you have more than 1GB of RAM


Rúben Gonçalves:p[/QUOTE]


I don't see this option in 2.6.14. Anyone else?

---

### Post by interzoneuk on 2005-12-10
Hi people.

What is the correct procedure for installing the latest kernel and latest ck patchset?

I tried using the guide in the original post but used kernel 2.6.14.3 and patch-2.6.14-ck6.bz2.

I used the command     

sudo bzcat /home/username/patch-2.6.14-ck6.bz2| patch -p1

and answered 'y' to all.

When i tried the recompile the kernel it errored (i did not record the error).

However I then wiped the /usr/src/linux directory and started again.

This time I used the 2.6.14.3 kernel and the patch-2.6.14-ck1.bz2, it patched ok.

I then patched the source with these updates

2.6.14-ck1_to_2.6.14-ck2.patch.bz2
2.6.14-ck2_to_2.6.14-ck3.patch.bz2
2.6.14-ck3_to_2.6.14-ck4.patch.bz2
2.6.14-ck4_to_2.6.14-ck5.patch.bz2 
2.6.14-ck5_to_2.6.14-ck6.patch.bz2 

I used this command (is this correct)

sudo bzcat /home/username/2.6.14-ck1_to_2.6.14-ck2.patch.bz2| patch -p1

This time I could recompile (nvidia and nforce driver are also running fine)

Is there a way to patch the ck6 without having to upgrade from 1 - 6?

Cheers

---

### Post by Bloot on 2005-12-10
[QUOTE=windowsrefund]I don't see this option in 2.6.14. Anyone else?[/QUOTE]

Yes, me too. Maybe on x86-64 they are not avaliable.

---

### Post by hoodwink on 2005-12-10
[QUOTE=interzoneuk]Hi people.

What is the correct procedure for installing the latest kernel and latest ck patchset?

. . .

Is there a way to patch the ck6 without having to upgrade from 1 - 6?
[/QUOTE]
I, too, would like to know the answer.

As an aside, this HOWTO leaves out a lot of preparatory work for building a kernel on Ubuntu. I could not get make xconfig to work; not surprising, since that has been problematic on other distros. So I switched to the old standby make menuconfig only to discover that ncurses-devel is required. Considerable searching to find that this is really the libncurses5-dev package.

make-kpkg clean and make-kpkg -initrd --revision=ck1 kernel_image were uneventful, but dpkg -i kernel-image-2.6.14*.deb died because a boatload of dependencies around mkinitrd-tools were not present. After tracking this down, the kernel .deb installed ok.

Reboot brought a few more surprises. The standard bootscripts (I haven't changed any) try to setup raid devices, and this failed. Also errors stating that udev was already started, and something called dirmgr failed.

Net result: I'm running from the kernel, but either the .config loaded from /boot doesn't describe everything that's required, or some of the support packages needed for the bootscripts have hidden kernel dependancies, or ???

So, I doubt that this kernel is a keeper, but it's been a learning experience.

---

### Post by kaamos on 2005-12-11
[QUOTE=interzoneuk]Hi people.

What is the correct procedure for installing the latest kernel and latest ck patchset?

I tried using the guide in the original post but used kernel 2.6.14.3 and patch-2.6.14-ck6.bz2.
[...]
Is there a way to patch the ck6 without having to upgrade from 1 - 6?
[/QUOTE]

You just apply the ck6 patch to the 2.6.14 sources. Note that **not** to the sources of 2.6.14.3 as the ck patch includes the patches from 2.6.14.1 to 2.6.14.3.

---

### Post by coaxx on 2005-12-11
maybe you shouldt also tell 'em to install

```

sudo apt-get install kernel-package g++  

```

Otherwise the "make" command is not known.

---

### Post by coaxx on 2005-12-11
-deleted-

---

### Post by coaxx on 2005-12-11
[QUOTE=limit223]I've got my 2.6.15-rc1-ck1 patched from here, a week or two ago,  I copiled without any error you have above...you may find the latest kernel as well ...already patched it.
[http://www.linux-militia.net/modules/news/](http://www.linux-militia.net/modules/news/)[/QUOTE]

Now I know what the problem was. It only happens if 386 is chosen for CPU model. With Pentium-M everything works well here compiling the 2.6.15rc5!

---

### Post by Mizzou_Engineer on 2005-12-11
I think that you should pick the PIII normal processor type for a PIII-M as even though the P-M is based on the PIII's architecture, the P-M has things like SSE2 that your PIII-M does not.

I have a P4-M and use the Pentium 4 type as my P4-M is basically a Pentium 4 with the multiplier able to be dropped from 22x to 12x (and lower-power transistors.) Your PIII-M is the same to a PIII desktop chip as mine is to a P4 Northwood desktop chip.

---

### Post by jeffreyvergara.NET on 2005-12-11
anyone got their automount working after update to 2.6.14 kernel? I tried using pmount but it wont work either. I have this problem before and fixed by editing HAL users & groups but it seems I can't find it anymore... or just forgot what I typed.. Y_Y

---

### Post by dk_pa on 2005-12-12
Hmm...what should I do now for Linux Headers?  I would assume i would need a new package.  Just looking at the other ones for 2.6.12-10 they seem to just be certain folders from the kernel package?  Are these available from a Debian repository?

EDIT::  Sorry, Checked over at the Documentation project.  Answer seems to be here [http://doc.gwos.org/index.php/Kernel_Compilation](http://doc.gwos.org/index.php/Kernel_Compilation).  Just have to wait 45 minz, looks like it's going to be okay.  Maybe the headers should be added to the how to?  I read through it again and didn't see it.  Thanks for the how to btw, got my ITE8212 ATA RAID adapter working and made my day =)  Another edit, I'm a little slow.  I guess you dont need "headers" when you have the source.  I just didn't know how that all worked.  Or maybe I will need the headers?  Anyone have answer on that...haha.  I love learning =)

---

### Post by Bloot on 2005-12-12
[QUOTE=jeffreyvergara.NET]anyone got their automount working after update to 2.6.14 kernel? I tried using pmount but it wont work either. I have this problem before and fixed by editing HAL users & groups but it seems I can't find it anymore... or just forgot what I typed.. Y_Y[/QUOTE]

Yes automount won't work anymore, and pmount doesn't work either. If I can't fix it I'll probably turn back soon to 2.6.12-10.

---

### Post by jeffreyvergara.NET on 2005-12-12
how do you uninstall the kernel(2.6.14) together with it's files?

---

### Post by just-hatched on 2005-12-12
Am new to the world of kernel compiles, have successfully compiled and installed 2.6.14.3 from the sticky instructions in this thread, but cannot get 2.6.15-rc5 to actually compile, and I havent a clue how to troubleshoot this problem or even where to start. Used exact same commands for this compile as the 2.6.14.3

The reason am looking to build2.6.15-rc5 is to be able to use a Leadtek DVT 1000 DVB-T card, which according to another forum(whirlpool), support for this card has been built into 2.6.15-rc5. If I can get to work, then I dont need to go and buy something with drivers...

The compile error, not the whole output, just the end before it blows up:
CC kernel/sched.o
CC kernel/fork.o
CC kernel/exec_domain.o
CC kernel/panic.o
CC kernel/printk.o
CC kernel/profile.o
CC kernel/exit.o
CC kernel/itimer.o
CC kernel/time.o
CC kernel/softirq.o
CC kernel/resource.o
kernel/resource.c:480: warning: ‘__check_region’ is deprecated (declared at kernel/resource.c:468)
CC kernel/sysctl.o
CC kernel/capability.o
CC kernel/ptrace.o
CC kernel/timer.o
CC kernel/user.o
CC kernel/signal.o
CC kernel/sys.o
CC kernel/kmod.o
CC kernel/workqueue.o
CC kernel/pid.o
CC kernel/rcupdate.o
CC kernel/intermodule.o
kernel/intermodule.c:178: warning: ‘inter_module_register’ is deprecated (declared at kernel/intermodule.c:38)
kernel/intermodule.c:179: warning: ‘inter_module_unregister’ is deprecated (declared at kernel/intermodule.c:78)
kernel/intermodule.c:181: warning: ‘inter_module_put’ is deprecated (declared at kernel/intermodule.c:159)
CC kernel/extable.o
CC kernel/params.o
CC kernel/posix-timers.o
CC kernel/kthread.o
CC kernel/wait.o
CC kernel/kfifo.o
CC kernel/sys_ni.o
CC kernel/posix-cpu-timers.o
CC kernel/futex.o
CC kernel/dma.o
CC kernel/uid16.o
CC kernel/module.o
CC kernel/kallsyms.o
CC kernel/irq/handle.o
In file included from include/asm/fixmap.h:27,
from include/asm/smp.h:16,
from include/linux/irq.h:13,
from kernel/irq/handle.c:9:
include/asm/acpi.h: In function ‘__acpi_acquire_global_lock’:
include/asm/acpi.h:67: error: ‘boot_cpu_data’ undeclared (first use in this function)
include/asm/acpi.h:67: error: (Each undeclared identifier is reported only once
include/asm/acpi.h:67: error: for each function it appears in.)
include/asm/acpi.h: In function ‘__acpi_release_global_lock’:
include/asm/acpi.h:79: error: ‘boot_cpu_data’ undeclared (first use in this function)
make[3]: *** [kernel/irq/handle.o] Error 1
make[2]: *** [kernel/irq] Error 2
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/home/flip/linuxbuild'
make: *** [stamp-build] Error 2

Where do i start looking, the .config file didnt make much sense, had a few goes trying to turn unnecessary items off without any change in the result...

helpless kernel newbie, any suggestions?

---

### Post by Bloot on 2005-12-12
[QUOTE=jeffreyvergara.NET]how do you uninstall the kernel(2.6.14) together with it's files?[/QUOTE]

That's what I did:

```
sudo aptitude remove linux-image-2.6.14-ck6
```

where ck6 is the patchset I applied.

Then removed linux from /usr/src and all the 2.6.14 files and folders.

---

### Post by just-hatched on 2005-12-12
[QUOTE=coaxx]thanks for the hint. Meanwhile I have dist-upgraded to dapper :cool: 2.6.15-x compiles now easily.[/QUOTE]

So did you find out the cause of the problem?

---

### Post by luminoso on 2005-12-12
Everything ok.. but

i am getting this:

kernel-image-2.6.14-ck1_ck1_i386.deb 

what about i686+sse2+O3 optimizations?!

---

### Post by coaxx on 2005-12-13
[QUOTE=just-hatched]So did you find out the cause of the problem?[/QUOTE]


hi yea just look ahead, I did reply to my own problem (use threaded view in this forum to have a better discussion overview): Sulution for me: Chose a ** different ** CPU in kernel config (not 386)

---

### Post by interzoneuk on 2005-12-14
kaamos. Thank you very much.

I used 2.6.14 kernel (not 2.6.14.3) and the ck6 patch works fine, it installed o.k and runs really nice.

...however it is not running quite as fast as the Supersuse kernel...

Cheers

---

### Post by tud on 2005-12-15
I generated my own kernel using your guide and adding support for ndiswrapper and last ati drivers. Everything is ok but now I need to install VmWare workstation and when I run vmware-config.pl I have an error
```
The path "/usr/src/linux/include" is a kernel header file directory, but it does
not contain the file "linux/version.h" as expected.  This can happen if the
kernel has never been built, or if you have invoked the "make mrproper" command
in your kernel directory.  In any case, you may want to rebuild your kernel.

```
How can I generate linux-headers-2.6.14-ck1 package?
Thanks for your work :KS

EDIT: solved after recompiling the kernel with:
```
sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers modules_image
```

---

### Post by hubbadub on 2005-12-15
Thanks, this worked perfectly the 1st time on both my friends Ubuntu box, and my Kubuntu one.

---

### Post by interzoneuk on 2005-12-16
Hi everybody.

For the people who have been following the thread there is now ck7 patch out.

[http://ck.kolivas.org/patches/2.6/2.6.14/2.6.14-ck7/](http://ck.kolivas.org/patches/2.6/2.6.14/2.6.14-ck7/)


cheers.

---

### Post by getaceres on 2005-12-22
I've compiled the 2.6.14 kernel with the ck7 patch but I've got the pmount bug (Device /dev/something is already mounted on /media/somepoint). The problem is that this file: [http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.6-1_i386.deb](http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.6-1_i386.deb) that solves this isn't there anymore, and this file [http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.6-1~breezy1_i386.deb](http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.6-1~breezy1_i386.deb) doesn't solve the problem (the file [http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.7-1ubuntu1_i386.deb](http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.7-1ubuntu1_i386.deb) gives me unresolved dependencies)
Anyone knows how to solve this?

---

### Post by Bloot on 2005-12-22
[QUOTE=getaceres]I've compiled the 2.6.14 kernel with the ck7 patch but I've got the pmount bug (Device /dev/something is already mounted on /media/somepoint). The problem is that this file: [http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.6-1_i386.deb](http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.6-1_i386.deb) that solves this isn't there anymore, and this file [http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.6-1~breezy1_i386.deb](http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.6-1~breezy1_i386.deb) doesn't solve the problem (the file [http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.7-1ubuntu1_i386.deb](http://darkstar.ist.utl.pt/ubuntu/archive/pool/main/p/pmount/pmount_0.9.7-1ubuntu1_i386.deb) gives me unresolved dependencies)
Anyone knows how to solve this?[/QUOTE]

Yeah, I'd really like to solve the pmount problem on my 64bit ubuntu too.

---

### Post by getaceres on 2005-12-22
For the moment I'm back to 2.6.12-10 kernel.
It's a shame, the 2.6.14-ck7 kernel resolved a couple of bugs I have right now with kernels greater than 2.6.10.

---

### Post by yoshic on 2005-12-22
:p Thanks for the How-to, it worked perfect for me :razz::razz::razz::razz:

---

### Post by Tomasz on 2005-12-23
Yeah, pmount 0.9.6 does not fix the problem. 0.9.7 gives dependency issues. This is open source software, there *surely* must be a fix to this problem somewhere. Come on, it's the only problem with the 2.6.14 series. Anyone knows pmount enough to hack up a working version for breezy?

---

### Post by medivh on 2005-12-23
I followed the instructions and compiled the kernel correctly it works fine but i want to see splash screen in higher resolution and also the console.How can i make it appear like it.It turns into a blank screen when i write vga=0x318 at the and of the menu.lst Is there any other way to do it?

and it says its i386 in its name i am on a laptop and i think i need i686 am i wrong how can i optimize it for pentium M (centrino 1.5)

---

### Post by limit223 on 2005-12-25
A day ago I compiled a new kernel 2.6.15-rc6-ck1 with smp/smt modules enabled for my HT Cpu. I made kernel-image, kernel-headers, fglrx-kernel .deb's and everything went fine without errors.
 Kernel boot was fine, speed really impressing, modules loaded fine...

  Though, I've got a problem which I really do not have any idea about: Conky shows me in the cpu1, cpu2 loading values of over 100% ( sometimes over 500% :eek: ). I tried using that sensor=cpu in sperkaramba applet and it shows me as well big values in cpu loading... Everything seems ok...the applications open without  problems , the fan of cpu which for values of loading more than 20% usually starts, doesn't sound much as for over 100%.... 
 Is anyone can enlighten me what's all about?



P.S. Merry Christmas, Everyone!!

---

### Post by limit223 on 2005-12-26
No one has any clue for me why this big loading values in cpu1, cpu2 ?
The only real values that I belive are right are shown in #top command but doesn't help much ...

I've been searching all over the net for this kind abnormal cpu monitoring...no luck...:(

---

### Post by tseliot on 2005-12-27
[QUOTE=limit223]No one has any clue for me why this big loading values in cpu1, cpu2 ?
The only real values that I belive are right are shown in #top command but doesn't help much ...

I've been searching all over the net for this kind abnormal cpu monitoring...no luck...:([/QUOTE]
Perhaps you should wait for the stable version to be released.

EDIT: kernel 2.6.15 stable is already out!!!

---

### Post by limit223 on 2005-12-27
[QUOTE=tseliot]Perhaps you should wait for the stable version to be released.

EDIT: kernel 2.6.15 stable is already out!!![/QUOTE]

Cool...:)
Is it out already???? ....I haven't seen it on kernel.org, yet...Is there any other places where new vanilla versions are found?...

I've got also 2.6.15-rc1-ck1 which I'm very happy with it...that's why I tried another unstable ver. 2.6.15-rc6-ck1..

---

### Post by tseliot on 2005-12-27
[QUOTE=limit223]Cool...:)
Is it out already???? ....I haven't seen it on kernel.org, yet...Is there any other places where new vanilla versions are found?...

I've got also 2.6.15-rc1-ck1 which I'm very happy with it...that's why I tried another unstable ver. 2.6.15-rc6-ck1..[/QUOTE]
No, I was wrong and out of my mind :p .
Unfortunately only 2.6.14.5 is out :(

---

### Post by atlas95 on 2005-12-27
thx for this guide, 
i have a little problem...after compiling this kernel, my ntfs partitions on s-ata work correctly, but my 5 ntfs partitions on other disk which are in ata133 don't work :s, the mount failed...

can you say me what i have forgot in config?
thanks, sorry for my english

---

### Post by MighMoS on 2005-12-28
[QUOTE=RubenGonc]This How-To will guide you through the compilation/installation of the 2.6.14 Vanilla Kernel (more recent than the one distribuited with Ubuntu 5.10) with the performance patchset by Kon Colivas.[/QUOTE]
I think you mispelled his name.  Isn't it "Con Kolivas"?

---

### Post by SirKillalot on 2005-12-29
I cannot mount partitions from my second HDD anymore!
It says:
/dev/hdb7 already mounted or /mount/point already in use

---

### Post by muchmusic on 2005-12-29
yes it is Con Kolivas

CK patchset thus named =)

[http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)

---

### Post by limit223 on 2005-12-29
New compilation of 2.6.15-rc7-ck1 vanished my problems... Found some bugs in kernel mail list archive for 2.6.15-rc4, rc5 and rc6 ..just for those who want to try prereleased versions.

---

### Post by theh0g on 2005-12-30
[QUOTE=SirKillalot]I cannot mount partitions from my second HDD anymore!
It says:
/dev/hdb7 already mounted or /mount/point already in use[/QUOTE]

You have to remove EVMS, I had the same problem and this fixed it.

---

### Post by AntiMattR on 2005-12-30
Awesome!

I have a Mini-ITX system that I have been trying to turn into a MythTV box.  Is there anything special I need to do to optimize this kernel for the EPIA?

This board also has a Unichrome graphics accelerator and needs patches to the kernel (as referenced in [https://wiki.ubuntu.com/ViaEpiaDriHowto](https://wiki.ubuntu.com/ViaEpiaDriHowto)) - could I apply these patches and compile without any problems?

Thanks!

---

### Post by juantxorena on 2006-01-01
I've found a lot of people, like me, with mounting local system problems after compiling and installing cK patched kernel. I've found this post with a solution for the problem: [http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10)
which few people have visited, but it worked for me.

---

### Post by juantxorena on 2006-01-02
I've just installed the 2.6.14 kernel with ck7 patch. The first attemp I got the pmount error. Then I configured the kernel again, but not compiling neither as a module) some options, like tape, PCMCIA, all laptop-related things, etc. Also I patched the kernel as I said above. And then installed the newest NVIDIA drivers, 8178 (the first time I got the refresh rate at maximun possible)

Now I've got pmount working, and everything (for now) working flawlessly.

I don't know what this patch do in the kernel, but now my computer flies.

---

### Post by mach on 2006-01-02
Very nice howto! First time poster here, but allow me to make a couple points..

I had to remove the linux-restricted-modules a second time, to no surprise, to get ati's fglrx drivers working again.

CK1 is an old version of Kon Colivas's patches. CK8 is now out (includes patches from linux 2.6.14.5). I realize the how-to was made a couple months ago, just letting other peeps know about CK8. ;) (link: [http://ck.kolivas.org/patches/2.6/2.6.14/2.6.14-ck8/](http://ck.kolivas.org/patches/2.6/2.6.14/2.6.14-ck8/))

once again, thanks for the how-to.

---

### Post by newuser111 on 2006-01-03
after compiling 2.6.14 with ck8 patch the blackscreen bug when logging out is fixed!  SMP support is enabled also

---

### Post by drfalkor on 2006-01-03
EDIT: nevermind

---

### Post by Gandalf on 2006-01-03
kernel 2.6.15 released, download [here](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.15.tar.bz2)
also colin kalivas released his fist patch today, download [here](http://ck.kolivas.org/patches/2.6/2.6.15/2.6.15-ck1/patch-2.6.15-ck1.bz2)

I'm currently installing it, i'll report if any problems occured...

---

### Post by Gandalf on 2006-01-03
sadly usplash did not work, plus there are multiple modules that won't boot, i'm trying ck8 with 2.6.14 now

---

### Post by mach on 2006-01-03
Sadly, 2.6.15 doesn't fix pmount/mount issues.

---

### Post by imranj on 2006-01-03
Yup the Usplash doesnt work, dont know why can some one please check into ti and tell me why isnt it working please?

sound intially was dead, but i tweaking a button and bang on my face
ahahahah

---

### Post by imranj on 2006-01-03
Which IO scheduler should i use?

CFQ or Anticpatory?

i have desktop but i am thinking about Anticipatory?

should or shouldnt and why?

urgently pls

---

### Post by limit223 on 2006-01-03
I do not have any problem with the new final release; compiled with smp, patched with new driver from SysKonnect for one of my network card, reinstalled Radeon ati 8.20.8 driver...everything went smooth without any error.
This is my hardware configuration:

P4HT 915ExpressChipset@3Ghz|ASUS P5GD1 LGA775 IT8212 chipset|Intel-PRO/100 + Yukon Gigabit Ethernet 10/100/1000Base-T Adapter|512MB DDR@400Mhz|160SATA+120PATA both WD|ATI Radeon X600Pro(RV380 3E50) PCI 128MB|Leadtek Winfast 2000XP TV-tuner|

Usplash absence wouldn't bother me too much...

---

### Post by Gandalf on 2006-01-03
i tried dapper upslash which suppose to work with 2.6.15 but nothing!!! once i saw there is an error , insmod /lib/modules/...../vga.. don't quite remember it and i didn't find where it suppose to be in the logs, i searched all /var dir but couldn't find it, this error will be written right after grub uncompress the kernel... i think that's why upslash ain't working

---

### Post by Ainvar on 2006-01-03
[QUOTE=juantxorena]I've just installed the 2.6.14 kernel with ck7 patch. The first attemp I got the pmount error. Then I configured the kernel again, but not compiling neither as a module) some options, like tape, PCMCIA, all laptop-related things, etc. Also I patched the kernel as I said above. And then installed the newest NVIDIA drivers, 8178 (the first time I got the refresh rate at maximun possible)

Now I've got pmount working, and everything (for now) working flawlessly.

I don't know what this patch do in the kernel, but now my computer flies.[/QUOTE]

Can you list what you did not compile this time around? I am getting the pmount issue. I have also tried the evms patch.

---

### Post by TecnoVM64 on 2006-01-04
Hello people, I've been trying to compile the recent linux kernel 2.6.15 but i have the following problem:

root@h4x:/usr/src/linux# make xconfig
HOSTCC scripts/basic/fixdep
In file included from /usr/include/sys/socket.h:35,
from /usr/include/netinet/in.h:24,
from /usr/include/arpa/inet.h:23,
from scripts/basic/fixdep.c:115:
/usr/include/bits/socket.h:304:24: error: asm/socket.h: No such file or directory
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2

Any ideas?

(I can do it with the 2.6.14ck3 source that still have somewhere) :(

---

### Post by limit223 on 2006-01-04
From my short experience in Debian system, loading X as root will never work!
 I had the same error trying to do that as well.
 Exit root and do:
sudo make xconfig

---

### Post by juantxorena on 2006-01-04
[quote=Ainvar]Can you list what you did not compile this time around? I am getting the pmount issue. I have also tried the evms patch.[/quote] Now I'm using ck8 patch, not ck7. I attach my config file. Maybe you can use it without modifying it (k7 processor).

---

### Post by goombah88 on 2006-01-04
[QUOTE=kashms]I followed the instructions and succeeded in installing the new kernel with the patch. I even was able to build a nvidia module deb to install. However a couple of things, showstoppers in fact, did not work. So far I discovered that the side scolling on my touchpad is not working, and more importantly suspend stopped working as well. I'm just going to stick with 2.6.12-9-686 for now.[/QUOTE]
i have a similar problem.  last night i installed the 2.6.14 kernel with the ck8 patch and now whenever i try to use the scroll buttons next to the synaptic touchpad on my gateway laptop nothing happens.  on the desktop i get what looks like a switch desktop dialog popup and in firefox it won't scroll at all.  very annoying to not be able to scroll.

if anyone knows a way around this or how to make it work again please let me know.  otherwise i may have to go back to the 2.6.12-10-686-smp kernel i was using b4 this.

thanks in advance.

---

### Post by imranj on 2006-01-04
Well instead of root , be in normal command prompt and type this

xhost + 

the su <<passwprd>>

u are redy to go

;)



[QUOTE=limit223]From my short experience in Debian system, loading X as root will never work!
 I had the same error trying to do that as well.
 Exit root and do:
sudo make xconfig[/QUOTE]

---

### Post by imranj on 2006-01-04
when you complie the kernel, select automout v3 and 4,

and also check out the some VMS thing, ok, some file needs to be edited yeah.

good luck.

[QUOTE=mach]Sadly, 2.6.15 doesn't fix pmount/mount issues.[/QUOTE]

---

### Post by imranj on 2006-01-04
Well at least i should know,whts happening, what is wroking or has failed hmm, and with out the boot screen, uff.

not good.


[QUOTE=limit223]I do not have any problem with the new final release; compiled with smp, patched with new driver from SysKonnect for one of my network card, reinstalled Radeon ati 8.20.8 driver...everything went smooth without any error.
This is my hardware configuration:

P4HT 915ExpressChipset@3Ghz|ASUS P5GD1 LGA775 IT8212 chipset|Intel-PRO/100 + Yukon Gigabit Ethernet 10/100/1000Base-T Adapter|512MB DDR@400Mhz|160SATA+120PATA both WD|ATI Radeon X600Pro(RV380 3E50) PCI 128MB|Leadtek Winfast 2000XP TV-tuner|

Usplash absence wouldn't bother me too much...[/QUOTE]

---

### Post by Ainvar on 2006-01-04
[QUOTE=juantxorena]Now I'm using ck8 patch, not ck7. I attach my config file. Maybe you can use it without modifying it (k7 processor).[/QUOTE]


Thanks, I will look at the config and compare it to mine, unfortunately I am on a laptop with a Pent M class cpu. So a few changes will need to be made.

I remember on aone of the first few pages of this thread a link that will compare the configs to one another, I think I will give that a shot also.

---

### Post by limit223 on 2006-01-04
[QUOTE=imranj]Well at least i should know,whts happening, what is wroking or has failed hmm, and with out the boot screen, uff.

not good.[/QUOTE]


You are able to see every module at boot time without usplash (this is just a eyecandy of boot time). Go to /boot/grub/menu.lst and delete "splash" word from the end of the line:
kernel		/boot/vmlinuz-2.6.15-ck1-smp root=/dev/hdb10 ro quiet **splash**

PS This setting could be disable in writing menu.lst at every kernel compilation by deleting the same word in the line:
# nonaltoptions=quiet **splash**

---

### Post by limit223 on 2006-01-04
[QUOTE=imranj]Well instead of root , be in normal command prompt and type this

xhost + 

the su <<passwprd>>

u are redy to go

;)[/QUOTE]

Typing "xhost +" I've got this message:

access control disabled, clients can connect from any host

OK I've got it...it works...Thanks!

---

### Post by ZedLord on 2006-01-04
I Want the USplash Back!!!!, Is There any How-to of sorts which helps in bringing it back!,

EDIT: Even the Font (the startup and shutdown text) Seems to be messed!, I Looks kinda big.

---

### Post by limit223 on 2006-01-04
There is another option to have a splash ...
 A couple of days ago Upower was lake of one package depency...Now  a new version is released and you may find in this repo: 
deb [http://repo.nanofreesoft.org](http://repo.nanofreesoft.org) breezy main

More info [here]("http://nanofreesoft.org/index.php?module=subjects&func=viewpage&pageid=1").

I just installed it and it works in my new kernel...now I try to figure out how to customize its theme.

---

### Post by Gandalf on 2006-01-04
hmmmm This didn't even work with breezy kernel for me :o :o

---

### Post by limit223 on 2006-01-04
Gandalf,
I may say that original kernel from breezy lived just a week in my system( I have my own config file that I use it in compilation)...I really do not have any ideea why things do not work to you...but I found something probably would help you figure out something:
[http://www.ubuntuforums.org/showpost.php?p=287946&postcount=208](http://www.ubuntuforums.org/showpost.php?p=287946&postcount=208)

---

### Post by Rob2687 on 2006-01-04
upower doesn't uninstall :( 

```
Removing upower ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.15-ck1
Found kernel: /boot/vmlinuz-2.6.12-10-686
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

update-rc.d: /etc/init.d/upower exists during rc.d purge (use -f to force)
update-rc.d: /etc/init.d/upower10 exists during rc.d purge (use -f to force)
update-rc.d: /etc/init.d/upower20 exists during rc.d purge (use -f to force)
update-rc.d: /etc/init.d/upower30 exists during rc.d purge (use -f to force)
update-rc.d: /etc/init.d/upower40 exists during rc.d purge (use -f to force)
update-rc.d: /etc/init.d/upower50 exists during rc.d purge (use -f to force)
update-rc.d: /etc/init.d/upower60 exists during rc.d purge (use -f to force)
dpkg: error processing upower (--remove):
 subprocess post-removal script returned error exit status 1
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.15-ck1
Found kernel: /boot/vmlinuz-2.6.12-10-686
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 upower
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by TheAnonymousx on 2006-01-04
So, I've compiled the new kernel with no real problems and all and then I restarted my machine.
However, upon restarting I notice an error message and then get dumped back to the command line. I try "startx" but get an error message, so I peruse the forums here and install the libqt3 packages and then run "make clean" and "make xconfig." Both (eventually) worked with no problems but I still can't start X. Anyone got ideas?
I'm using an OLD amptron motherboard with everything on board if that helps.
**edit**
Now doing startx gives me the error message:
fatal IO error 104 (connection reset by peer) on xserver 0:0
after 0 request...

---

### Post by Rob2687 on 2006-01-04
What is the error message?

---

### Post by TheAnonymousx on 2006-01-05
[QUOTE=Rob2687]What is the error message?[/QUOTE]

Same as the one above, but I think that error message stems from this one...
I do
sudo make clean (from /usr/src/linux)
sudo make xconfig

I get the error message

qconf cannot connect to Xserver
make[1]: [xconfig] Error1
make: ***[xconfig] Error2

The other error I was getting is stated in the earlier comment.
w00t!
Man is this always this involved or am I this dumbtarded?

---

### Post by Gandalf on 2006-01-05
[QUOTE=Rob2687]upower doesn't uninstall :( 

```
Removing upower ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.15-ck1
Found kernel: /boot/vmlinuz-2.6.12-10-686
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

update-rc.d: /etc/init.d/upower exists during rc.d purge (use -f to force)
update-rc.d: /etc/init.d/upower10 exists during rc.d purge (use -f to force)
update-rc.d: /etc/init.d/upower20 exists during rc.d purge (use -f to force)
update-rc.d: /etc/init.d/upower30 exists during rc.d purge (use -f to force)
update-rc.d: /etc/init.d/upower40 exists during rc.d purge (use -f to force)
update-rc.d: /etc/init.d/upower50 exists during rc.d purge (use -f to force)
update-rc.d: /etc/init.d/upower60 exists during rc.d purge (use -f to force)
dpkg: error processing upower (--remove):
 subprocess post-removal script returned error exit status 1
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.15-ck1
Found kernel: /boot/vmlinuz-2.6.12-10-686
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 upower
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)

```[/QUOTE]
that's not a problem, do the following
```

sudo rm /etc/init.d/upower*
sudo apt-get remove --purge upower

```

@limit223 actually me neither i've been using 2.6.14 since ck2 was out, and i didn't get what was said in that post, but vga=number work for me as suse boot like this so my card support it

---

### Post by newuser111 on 2006-01-05
[QUOTE=TheAnonymousx]Same as the one above, but I think that error message stems from this one...
I do
sudo make clean (from /usr/src/linux)
sudo make xconfig

I get the error message

qconf cannot connect to Xserver
make[1]: [xconfig] Error1
make: ***[xconfig] Error2

The other error I was getting is stated in the earlier comment.
w00t!
Man is this always this involved or am I this dumbtarded?[/QUOTE]


i had the same problem i have no idea what causes it but use

**sudo make menuconfig** instead of sudo make xconfig which worked for me

---

### Post by TheAnonymousx on 2006-01-05
[QUOTE=newuser111]i had the same problem i have no idea what causes it but use

**sudo make menuconfig** instead of sudo make xconfig which worked for me[/QUOTE]

Okay so that seems to have worked (had to install some base fonts for X), but now GNOME won't freakin' launch (even though I was allowed to start Xwindows).
I get the login screen, enter my password, and even have the system ATTEMPT to load gnome, then I get this error message:

Error restarting gnome settings daemon
last error message:
Failed to execute /usr/lib/control-center/gnome-settings : daemon 2 (no such file or directory)

Then I'm informed the system will attempt to attempt to reload gnome on the next logon (this is the third attempt though).

Any ideas guys? Maybe I have to interrupt gnome's loading and jump to a command-line interface (however that's done) when it's loading to grab some package or change some setting?

---

### Post by madchicken on 2006-01-05
Sorry guys, I'm lost in this thread :confused: 
Anyone has resolved the pmount issue?
I just compiled a 2.6.15+ck+suspend2 with success, but I can't get pmount working.

Any help is appreciated.

Bye

---

### Post by limit223 on 2006-01-05
Ok..so far was this case: my compilation was fine with upower except I couldn't get in console, meaning that the splash with the image and the bar from upower theme loaded but F2 and Ctrl+Alt+F2/7 didn't...and of course I went forward to see the what happens.
 I recompiled another vanilla 2.6.15-ck1 kernel with using different .config file and upower didn't work at all.
I tried a test:
I installed linux-686-smp with the linux-headers-2.6.12-10 and Upower worked perfectly in my computer with all things: switch in console, splash image, splash bar.... I found some differences of modules loaded and used in lsmod between this kernels(mine and the from the repo) especially regarding those modules suffixed by fb: *fb  - tileblit, fbcon, cfbcopyarea... I tried to identify them in repo's kernel .config file to see what I am missing in my compiled kernels.
 So far I've got 3 kernels in test: one with fully upower function, one with partial function, one without any response...
 Conclusion:I'm pretty sure that usplash or upower are bounded to be supported by some of this modules and they differ from video card to video card Now probably the question are: New kernel 2.6.15 contains all this modules? Do we need extra patches in it? Which are actually they?

My mind of 2 cents...:p

---

### Post by juantxorena on 2006-01-05
[quote=madchicken]Sorry guys, I'm lost in this thread :confused: 
Anyone has resolved the pmount issue?
I just compiled a 2.6.15+ck+suspend2 with success, but I can't get pmount working.

Any help is appreciated.

Bye[/quote]
I've found, in 4 or 5 compilations I've made, that the resolution of pmount is completly aleatory. Upper in this post I attached a conf file with the pmount solved. You can try it, modifying it the lesser as possible.

---

### Post by rjwood on 2006-01-05
I compiled the new 2.6.15-ck kernel and when I reboot I get
"kernel panic-not syncing: VFS: Unable to mount root fs on unknown-block (0,0)"    I know it's not mounting the root file system--but- I don't know what I did wrong. I thought I was very careful as this was my second go-round with it. Thanks in advance.

BTW I want to thank you and tselliott for the great 'How-To's"

---

### Post by fergus.b on 2006-01-05
[QUOTE=nastya]Yay, now my partitons on my other drive will mount! Now I can play planet penguin racer at fullspeed AND access my other drive with my data. Thank you so much! :)[/QUOTE]
Did you manage to get your Unichrome working mate? If so what was the procedure or did you just do the new kernel + patch?

---

### Post by madchicken on 2006-01-06
[QUOTE=juantxorena]I've found, in 4 or 5 compilations I've made, that the resolution of pmount is completly aleatory. Upper in this post I attached a conf file with the pmount solved. You can try it, modifying it the lesser as possible.[/QUOTE]

Thaks, I already tryed your config file, but using it with suspend2 patch (I need it because I can't suspend with suspsw) I get an error at compile time. I'll try to diff my config with your's to see if there are "big" differences.

Thanks

---

### Post by tseliot on 2006-01-06
[QUOTE=rjwood]I compiled the new 2.6.15-ck kernel and when I reboot I get
"kernel panic-not syncing: VFS: Unable to mount root fs on unknown-block (0,0)"    I know it's not mounting the root file system--but- I don't know what I did wrong. I thought I was very careful as this was my second go-round with it. Thanks in advance.

BTW I want to thank you and tselliott for the great 'How-To's"[/QUOTE]
I have some questions for you:
1) What's the model of your motherboard?
2) Did you compile the support for ext3 filesystem in the kernel (NOT as a module)?

I'm asking you those questions because I can't compile any vanilla kernel (well I can but it doesn't boot). Even Dapper's kernels won't boot. It says it doesn't find the kernel. I have filed a bug in the Ubuntu Bugzilla. I hope they solve the bug otherwise there will be no Dapper for me :( 

I hope your case is different from mine.

---

### Post by rjwood on 2006-01-06
[quote=tseliot]I have some questions for you:
1) What's the model of your motherboard?
2) Did you compile the support for ext3 filesystem in the kernel (NOT as a module)?

I'm asking you those questions because I can't compile any vanilla kernel (well I can but it doesn't boot). Even Dapper's kernels won't boot. It says it doesn't find the kernel. I have filed a bug in the Ubuntu Bugzilla. I hope they solve the bug otherwise there will be no Dapper for me :( 

I hope your case is different from mine.[/quote]

1) * Manufacturer's name - ASUS A7N8X-LA
2)I thought I was real careful. I am almost positve I compiled it for ext3. Is there a way for me to check and be sure? I hope it was my mistake and my motherboard is not too old.

---

### Post by tseliot on 2006-01-06
[QUOTE=rjwood]1) * Manufacturer's name - ASUS A7N8X-LA
2)I thought I was real careful. I am almost positve I compiled it for ext3. Is there a way for me to check and be sure? I hope it was my mistake and my motherboard is not too old.[/QUOTE]

you can find the config file of your bios under /boot
you will find files such as config-name_of_your_kernel , etc.

Open the file as a text and use the Find function. Search "ext3".

BTW my motherboard is not old it's just an Ubuntu bug (I wonder if it's the same in Debian but I guess not since Kanotix works). It works great in Fedora Core 4 which uses kernel 2.6.14.1.

---

### Post by rjwood on 2006-01-06
Thanks for the help tseliot do this look correct?

#
# File systems
#
# CONFIG_EXT2_FS is not set
CONFIG_EXT3_FS=y
CONFIG_EXT3_FS_XATTR=y
CONFIG_EXT3_FS_POSIX_ACL=y
CONFIG_EXT3_FS_SECURITY=y
CONFIG_JBD=y
CONFIG_JBD_DEBUG=y
CONFIG_FS_MBCACHE=y
CONFIG_REISERFS_FS=m
# CONFIG_REISERFS_CHECK is not set
# CONFIG_REISERFS_PROC_INFO is not set
CONFIG_REISERFS_FS_XATTR=y
CONFIG_REISERFS_FS_POSIX_ACL=y
CONFIG_REISERFS_FS_SECURITY=y
CONFIG_JFS_FS=m
CONFIG_JFS_POSIX_ACL=y
CONFIG_JFS_SECURITY=y
# CONFIG_JFS_DEBUG is not set
CONFIG_JFS_STATISTICS=y
CONFIG_FS_POSIX_ACL=y
CONFIG_XFS_FS=m
CONFIG_XFS_EXPORT=y
CONFIG_XFS_QUOTA=y
CONFIG_XFS_SECURITY=y
CONFIG_XFS_POSIX_ACL=y
CONFIG_MINIX_FS=m
CONFIG_ROMFS_FS=m
CONFIG_INOTIFY=y
CONFIG_QUOTA=y
CONFIG_QFMT_V1=m
CONFIG_QFMT_V2=m
CONFIG_QUOTACTL=y
CONFIG_DNOTIFY=y
CONFIG_AUTOFS_FS=m
CONFIG_AUTOFS4_FS=m
# CONFIG_FUSE_FS is not set

#
# CD-ROM/DVD Filesystems
#
CONFIG_ISO9660_FS=m
CONFIG_JOLIET=y
CONFIG_ZISOFS=y
CONFIG_ZISOFS_FS=m
CONFIG_UDF_FS=m
CONFIG_UDF_NLS=y

#
# DOS/FAT/NT Filesystems
#
# CONFIG_MSDOS_FS is not set
# CONFIG_VFAT_FS is not set
# CONFIG_NTFS_FS is not set

#
# Pseudo filesystems
#
CONFIG_PROC_FS=y
CONFIG_PROC_KCORE=y
CONFIG_SYSFS=y
CONFIG_TMPFS=y
# CONFIG_HUGETLBFS is not set
# CONFIG_HUGETLB_PAGE is not set
CONFIG_RAMFS=y
# CONFIG_RELAYFS_FS is not set

#
# Miscellaneous filesystems
#
# CONFIG_HFSPLUS_FS is not set
# CONFIG_CRAMFS is not set
# CONFIG_VXFS_FS is not set
# CONFIG_HPFS_FS is not set
# CONFIG_QNX4FS_FS is not set
# CONFIG_SYSV_FS is not set
# CONFIG_UFS_FS is not set

---

### Post by limit223 on 2006-01-06
I've got Upower full working with cute console in my machine !! I did, I did...happpy:)

Comparing and searching I found those modules important for console are: vesafb and fbcon. In .config file making xconfig I checked:
Graphics support:
-VGA 16-color graphics support - module (m)
-VESA VGA graphics support - build in kernel(y)
-
Console display driver support:
-VGA text console and Video mode selection support- build in kernel (y)
-MDA text console-module (m)
-Framebuffer Console and Framebuffer Console Rotation support-build in kernel (y)
-Select compiled-in fonts with VGA 8x8 fonts, VGA 8x16 font - build in kernel(y)
-Sparc console 12x12 font- build in kernel (y)


Some referrence you may find here:
[http://www.icewalkers.com/Linux/Howto/Framebuffer-HOWTO-5.html](http://www.icewalkers.com/Linux/Howto/Framebuffer-HOWTO-5.html)
[http://gentoo-wiki.com/HOWTO_Framebuffer:Bootsplash:Grubsplash#Smaller_fonts_on_framebuffer_for_greater_area](http://gentoo-wiki.com/HOWTO_Framebuffer:Bootsplash:Grubsplash#Smaller_fonts_on_framebuffer_for_greater_area)
[http://ubuntuforums.org/showthread.php?t=90689](http://ubuntuforums.org/showthread.php?t=90689)

 For the only thing I was afraid was enabling 3D accel side effect. Reading goodchild and heftigrat's posts from here [http://ubuntuforums.org/showthread.php?t=76116&page=56](http://ubuntuforums.org/showthread.php?t=76116&page=56) remind me of my console problems. But after this new compilation, installing fglrx-kernel*.deb generated from compilation, enabling 3D(by doing 
cd /lib/modules/fglrx/build_mod
sudo ./make.sh
cd ..
sudo ./make_install.sh 
Reboot)

I was amazed to see that I've got them both: switching in a cute console without any problem in boot splash time and 3D accel in X time.

A Simple Reflection:
Compiling a new ver or even different build of the same vanilla kernel is not really as simple to copy .config file from an old ver and pass it to new one. Every time you should stay tuned to new changes that are made especially regarding headers that support your hardware components. I do not suggest to anyone to copy and paste that .config file in every compilation without seeing exactly what headers are configured in it to be build in or as module. If things changed and there are bugs for a certain module you may go see if some of patch providers would already issue a patch that may solve the problem.
 For sure I'm not an expert but I really enjoy trying new things in open source starting with first layer in my machine: the kernel.

---

### Post by tseliot on 2006-01-06
[QUOTE=rjwood]Thanks for the help tseliot do this look correct?[/QUOTE]
Yes, it is.

Do you have that problem only with kernel 2.6.15? Did you try other vanilla kernels?

I didn't have kernel panic, just a GRUB error  kernel not found therefore your problem might be different from mine.
Have a look at the bug I filed: [http://bugzilla.ubuntu.com/show_bug.cgi?id=21652]("http://bugzilla.ubuntu.com/show_bug.cgi?id=21652")

Another thing you could do is to try Dapper's livecd (it uses kernel 2.6.15) and see if it works.

---

### Post by rjwood on 2006-01-06
comparing file system choices in this new kernel and my other one. My 2.6.12-10k7 kernel has all the file systems as modules and the subsys choices are set to yes. Could that be a problem? how do I go back in and make changes??

---

### Post by tseliot on 2006-01-06
[QUOTE=rjwood]...My 2.6.12-10k7 kernel has all the file systems as modules...[/QUOTE]
That's absolutely normal for Ubuntu kernels. On the other hand if you use vanilla kernels if you leave the filesystem of the partition with your OS as a module the result is kernel panic.

---

### Post by rjwood on 2006-01-06
I think I may know what my problem is.
In block devices, there is box for "config_blk_dev_initrd" I am not able to check that device and the kernel message I get on boot seems to indicate a similarity to this options description. I see that other people who have shared their config file have this checked. Can anyone help me here. I tried doing it as root and with sudo.

---

### Post by macsimski on 2006-01-07
Hello all,

i've tried to build my first kernel but i got a kernel panic during boot. must be something i set incorrect in xconfig. 

so i want ot go back to my previous kernel, the default breezy kernel. boots up fine, albeit slow, but it boots. then i get to the login screen and i type my pass. screen turns black, a grey screen comes up with a watch cursor and bang, i'm back at the login screen. 

but when i switch to a virtual terminal and log in with my own account and then do sudo -s and startx my session starts and am in my beloved xfce again.

I think that there must be something wrong with the permissions, but what?

-is there a program to check permissions like in Mac OS X?
-is there a way to revert to the standard kernel installed by Kunbuntu without a complete reinstall??

[edit] found the problem. somewhere during the described building process i did'nt use sudo but in stead used sudo -s -H so i actually became root. some rights in my home folder got th owner of root.root. when i changed them to to myself everything works as before. Phew!

maybe i will try builing a kernel later...

---

### Post by moment on 2006-01-07
The only problem that I had was that I had to modprobe "evdev" module in order to get my alps touchpad to work again. Thanks!

---

### Post by Brando569 on 2006-01-08
[QUOTE=TheAnonymousx]Same as the one above, but I think that error message stems from this one...
I do
sudo make clean (from /usr/src/linux)
sudo make xconfig

I get the error message

qconf cannot connect to Xserver
make[1]: [xconfig] Error1
make: ***[xconfig] Error2

The other error I was getting is stated in the earlier comment.
w00t!
Man is this always this involved or am I this dumbtarded?[/QUOTE]

i believe its because in the terminal session your logged in as root but in your X session your logged in as your username and the terminal tries to connect to the root X session and cant. a simple fix it to SU back to your username and use this: sudo make xconfig

---

### Post by rjwood on 2006-01-08
Took me 5 attempts but I got going flawlessly. Thanks everyone especially tseliott (your the best).

---

### Post by firecat53 on 2006-01-08
Hey...successfully compiled the 2.6.15 kernel with ck1 patch using gcc-4.0.

I initially had trouble with the cardbus PCMCIA cards being detected, but a second reboot cured that problem. Now I just have to figure out the splash screen issue and fix the touchpad scroll feature. Already recompiled madwifi and wpa_supplicant.

Good how-to :)

Thanks, Scott

[edit]Does anyone have any suggestions for fixing the touchpad vertical scroll feature? I've been looking and I'm getting stumped.  All features of the touchpad work fine except the vertical scroll area. Here's the output from "cat /var/log/Xorg.0.log|grep synaptics"

(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
Synaptics Touchpad no synaptics event device found (checked 1 nodes)
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(II) UnloadModule: "synaptics"

Hmmm...so why would the touchpad not be detected but it all works except for one feature??
[/edit]

---

### Post by tseliot on 2006-01-09
[QUOTE=rjwood]Took me 5 attempts but I got going flawlessly. Thanks everyone especially tseliott (your the best).[/QUOTE]
I'm happy it worked in the end :)

---

### Post by TheAnonymousx on 2006-01-09
Alright, so anyone got some ideas for the problem I posted previously? Basically, with the make menuconfig I can load far enough to get past the splash screen, but right after that I get an error message that says gnome doesn't have any default setting to load. 
Anyone got a suggestion?
Also, I should know this, but how DO I bring up the command line when the machine first boots?

---

### Post by nevienc on 2006-01-11
> root@nn:/usr/src/linux# sudo make-kpkg -initrd --revision=ck1 kernel_image
test -f stamp-configure || /usr/bin/make -f /usr/share/kernel-package/rules configure
/usr/bin/make    ARCH=i386 \
                     bzImage
make[1]: Entering directory `/usr/src/linux-2.6.14.6cK1'
  CHK     include/linux/version.h
  CHK     include/linux/compile.h
  CHK     usr/initramfs_list
Kernel: arch/i386/boot/bzImage is ready  (#1)
make[1]: Leaving directory `/usr/src/linux-2.6.14.6cK1'
/usr/bin/make    ARCH=i386 \
                     modules
make[1]: Entering directory `/usr/src/linux-2.6.14.6cK1'
  CHK     include/linux/version.h
  CC [M]  drivers/net/bonding/bond_main.o
drivers/net/bonding/bond_main.c: In function &#8216;bond_compute_features&#8217;:
drivers/net/bonding/bond_main.c:1617: error: &#8216;struct bonding&#8217; has no member named &#8216;bond_features&#8217;
drivers/net/bonding/bond_main.c: In function &#8216;bond_init&#8217;:
drivers/net/bonding/bond_main.c:4511: error: &#8216;struct bonding&#8217; has no member named &#8216;bond_features&#8217;
make[4]: *** [drivers/net/bonding/bond_main.o] Error 1
make[3]: *** [drivers/net/bonding] Error 2
make[2]: *** [drivers/net] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.14.6cK1'
make: *** [stamp-build] Error 2
help please!

---

### Post by LightStruck on 2006-01-11
[QUOTE=nevienc]help please![/QUOTE]

Ok if its the problem I had then the ck1 patch wasn't playing nicely with my kernel.  Because the patches are supposed to be applied to a simple 2.6.14 kernel.  And it seems to me you're trying to compile a 2.6.14.6 kernel?  Correct me if I misunderstood your message.  But simply if you want to use the ck1 patch you need to use a regular 2.6.14 vanilla kernel from kernel.org

---

### Post by LightStruck on 2006-01-11
Also, I responded to his post but I've been having a really really tough time getting a working kernel config going.  I used a 2.6.14 and patched it to ck3 and the results were gorgeous.  I was amazed how fast it was.  I was like "OK! Tune more!"  And things fell apart.  I was suffering from the pmount support I believe early on because it wasn't loading my local filesystems but every compile since has installed fine I choose the 2.6.14 in my grub menu and the "Uncompressing Linux" comes up and then all the font on the screen just shifts and freezes.  No real loading just stops at a font shift.  I've recompiled around 12 times with one success.  Anyone got any tips?  I've been using the .config file from the 2.6.12-10-686-smp and changed it to my p4 processor and used the tweaks that were suggested at the beginning but no go.  Just seeing if anyone had this problem and cured it.  Thanks for your time.

---

### Post by nastya on 2006-01-11
[QUOTE=fergus.b]Did you manage to get your Unichrome working mate? If so what was the procedure or did you just do the new kernel + patch?[/QUOTE]

Yup it worked just fine. I had to recomplile my kernel to do it though. In case anyone else had trouble finding where the option was located, here's what I did.  In the configuration under device drivers -> character devices, go to direct rendering manager, and  under that is the option to add support for via unichrome video cards. After that, configure everything else the way you'd like, and compilie and it should work. :)

---

### Post by kaamos on 2006-01-12
Just upgraded to 2.6.15cK1. Works great otherwise, but couldn't still get pmount working. :(

---

### Post by Bloot on 2006-01-12
[QUOTE=kaamos]Just upgraded to 2.6.15cK1. Works great otherwise, but couldn't still get pmount working. :([/QUOTE]

It's really annoying, I'd like to use new kernels but that way it's not possible. I guess we'll have to wait to a newer and fixed version of pmount...

Greetings.

---

### Post by kaamos on 2006-01-12
Just noticed that the tty terminals (ctrl+alt+F1 - F6) are empty. I have "CONFIG_FB_VESA=y" the .config, and I thought that this fixes the problem. Usplash works though.. Does anyone know what config option would fix the terminals?

---

### Post by rulppa on 2006-01-12
deleted.

---

### Post by newuser111 on 2006-01-20
ive had good results compiling a kernel with the archck (based on ck) patchset

[http://iphitus.loudas.com/archck.php](http://iphitus.loudas.com/archck.php)

btw i recommend ati users stick to 2.14 kernels until ati fixes some serious system instability caused by using 2.15 with ati fglrx

---

### Post by ErikTheRed on 2006-01-21
I followed the guide to compile and install the 2.6.15.1 kernel, but I've run into a few oddities. I ended up omitting the cK patches, because I would get a hunk failure when I tried to patch (I tried both cK1 and cK2). Also for some reason the pretty kubuntu splash screen does not show up like usual, I just have a blank screen while the kernel, modules, etc load up. Everything else works fine though.

---

### Post by newuser111 on 2006-01-22
try the archck patch instead, it includes the bootsplash patches

[http://iphitus.loudas.com/archck.php](http://iphitus.loudas.com/archck.php)

---

### Post by Brando569 on 2006-01-24
sweet, even better patch set :) im downloading .14 , .15 and their respective patches now. i compiled .14 with ck7 on my dads computer and it worked fine. hopefully ill have the same luck with mine.

---

### Post by getaceres on 2006-01-24
Didn't you had the pmount bug? How did you solve it?

---

### Post by Bloot on 2006-01-24
[QUOTE=getaceres]Didn't you had the pmount bug? How did you solve it?[/QUOTE]

I'd like to know too.

---

### Post by the_maassk on 2006-01-26
After debating a kernel compile and install for over 3 weeks (I did not want to accidentally wreak my laptop!)..I just did a compile and install. Went flawless! Thanks for the wonderful guide. I used the ArchCK7 patch on mine...and as of now, nothing seems to be broken (except for the scroll zone on my touchpad). I'll check more later today and report if anything is broken.

I can see some obvious improvements - glxgears got another 60 FPS (760 now), HDD response seems to have improved. Overall, it feels better. Keepin' my fingers crossed!

Ciao'

---

### Post by the_maassk on 2006-01-26
Quick question - Seem to have lost a considerable amount of HDD space after I compiled the new .14 ArchcK7 kernel and installed it. Uninstalling the previous .12 kernel gives me around 56 MB back. Where is the rest? How do I clean whatever I did in the /usr/src ? What should I backup from there?

---

### Post by Rob2687 on 2006-01-26
You can delete /usr/src/linux and whatever directory you extracted the kernel tar.bz2 file to in the /usr/src directory.

---

### Post by agapito on 2006-01-27
I've just compiled and installed kernel 2.6.14 with the ArchCK7 patchset. Everything is working perfectly! After some bad experiences in an old Mandrade distro (8, i think) some time ago I stoped trying to compile the kernel, but now with your howto it was really easy. I'm compiling my own kernels from now on! :D  I loved the way the kernel is installed as a deb using dpkg.

Thank you for the great howto!

---

### Post by the_maassk on 2006-01-27
Thanks Rob. I backed up my .deb and deleted the stuff I thought I could generate again...like the extracted folder.

My broken touch pad scroll zone does not seem to have an answer to it. My USB scroll mouse works though...with the scroll wheel. I have a Compaq Presario.  Did try to work with the Synaptics app back when I was on Mandrake. I don't remember if it worked though ;).

Also discovered another broken - Hibernate seems to have stopped working. Suspend to RAM works fine...but a hibernate blanks the screen, mutes the sound, stops the hard disk...but does not power the lappy off! Any ideas?

Ciao'

---

### Post by Micro Rotors on 2006-01-27
OK I am trying to do this and I get this message after this command entry:
> sudo bzcat /home/username/patch-2.6.14-ck1.bz2| patch -p1

What is a bad flag?


[PHP]root@micro:/usr/src/linux# sudo bzcat /home/username/patch-2.6.14-ck1.bz2 patch -p1
bzcat: Bad flag `-p1'
bzip2, a block-sorting file compressor.  Version 1.0.2, 30-Dec-2001.

   usage: bzcat [flags and input files in any order]

   -h --help           print this message
   -d --decompress     force decompression
   -z --compress       force compression
   -k --keep           keep (don't delete) input files
   -f --force          overwrite existing output files
   -t --test           test compressed file integrity
   -c --stdout         output to standard out
   -q --quiet          suppress noncritical error messages
   -v --verbose        be verbose (a 2nd -v gives more)
   -L --license        display software version & license
   -V --version        display software version & license
   -s --small          use less memory (at most 2500k)
   -1 .. -9            set block size to 100k .. 900k
   --fast              alias for -1
   --best              alias for -9

   If invoked as `bzip2', default action is to compress.
              as `bunzip2',  default action is to decompress.
              as `bzcat', default action is to decompress to stdout.

   If no file names are given, bzip2 compresses or decompresses
   from standard input to standard output.  You can combine
   short flags, so `-v -4' means the same as -v4 or -4v, &c.

root@micro:/usr/src/linux#
[/PHP]

---

### Post by the_maassk on 2006-01-27
I hope you are using your username in place of the word 'username' in the commandline while patching! - Just thinking out loud :)

---

### Post by Micro Rotors on 2006-01-27
opps,,, my mistake, but it still says the same when I add my user name.

ok,,, Has anyone really done this like the thread tells you at the beginning? Also 3 attempts have chewed up a gig of my drive that I want back somehow. Is there a way to abort this stuff without leaving stuff in who knows were?

---

### Post by newuser111 on 2006-01-30
just in case anyone is curious, i managed to install the archck7 patched 2.6.14 kernel with EVMS patch

from the EVMS website download the latest tar.gz (at time of writing evms-2.5.4.tar.gz) and in the kernel subdirectory in this file there are 2 files, bd-claim.patch, dm-bbr.patch, copy them to usr/src/2.6.14archck7/linux

patch -p1 < bd-claim.patch
patch -p1 < dm-bbr.patch

that will apply them to the vanilla kernel, then you can apply archck7 or ck patch without issue like i did, then when you boot with the new kernel it shouldnt produce any evms errors

[http://evms.sourceforge.net/](http://evms.sourceforge.net/)

---

### Post by the_maassk on 2006-01-30
Weekend update - I wanted to make Ubuntu my full time Linux OS. So I decided to get rid of Mandriva 2006 which was taking up a lot of space. I wanted to dedicate that space to Breezy.

As luck would have it - I used the GParted Live CD to mess around with the partitions and ended up messing things up completely (I had a /home backup though). Reinstalled Breezy from scratch and forgot to boot into 'expert' mode - ended up with a .9-386 kernel :( (dead Suspend/ Hibernate..I need those desperately on my laptop). Went through a steep learning curve to reinstall my preferred desktop settings and other applications.

Don't care about the .10-686 from Ubuntu repos.

Just downloaded 2.6.15.1 vanilla and three patchsets - PP3 (only for 2.6.14 right now), 2.6.15_ArchcK2.1 and 2.6.15_Nitro3.

My options are:
2.6.14 with PP3 ([http://royy.net/~snaj/](http://royy.net/~snaj/))
2.6.15.1 with ArchcK2.1
2.6.15.1 with Nitro3

Any recommendations are welcome! :-D 

Ready to compile in 8 hrs. from now.....send in your recommendations and I'll update you with my results.

---

### Post by christhemonkey on 2006-02-01
How blinking long does it take to compile a kernel!
2 hours and counting.....

---

### Post by juantxorena on 2006-02-01
[quote=christhemonkey]How blinking long does it take to compile a kernel!
2 hours and counting.....[/quote]
A lot. It depends on how many things are being compiled as a module and as a part of the kernel. In my case, with an AMD 2600+ overclocked at 2600MHz (equivalent to an AMD 2800+), and with a stardard kernel configuration, without things like PCMCIAor tape support, about 2 hours and 30 minutes.

Get a cup of coffe.

---

### Post by christhemonkey on 2006-02-01
O dear... could be hear a while then!
Using PII 600mhz and lots of unnecesary kernel things :(
Can anyone think of some script or something i could write that would switch the pc off after its compiled?
(because im tired an its 20 past 10 already!)

---

### Post by juantxorena on 2006-02-01
Yes, you can write the compilation and building commands in a single line like this:
```
 make-kpkg clean && make-kpkg -initrd --revision=ck1 kernel_image && shutdown 
```
The "&&"  means that the terminal will execute the next command when the preceding command finishes. Just make sure you have SU privileges to shutdown. You can write ```
sudo -s
``` before doing things, so you will be an administrator until you write "exit", log out, reboot or shutdown.

---

### Post by christhemonkey on 2006-02-01
Hmm, someway i can get it to do that even thought it looks like getting towards nearly done?

---

### Post by juantxorena on 2006-02-01
When compiling, you will see a lot of lines starting with [CC] or [LD] (and some warnings). When finishing, you will see pairs of lines, first one starting with [CC] (or some other letters, I can't remember) and second one starting with some blank spaces. Also, the lines scroll faster.

---

### Post by christhemonkey on 2006-02-01
ok maybe i have a while left then!
still doing 
CC (M)

---

### Post by BeachBum on 2006-02-01
Hello,

Wonderful how-to, I was able to get it working nicely however I wiped my harddrive clean for a fresh start, and now when I attempt to install this kernel as outlined here, something happens at the make-kpkg.  I get errors that my filesystem was mounted read-only.  When I try to do anything after running make-kpkg, I recieve an error that nothing could be written to my harddrive because it was mounted read-only.  When I reboot, everything works fine.  Only until I run make-kpkg does anything go haywire.  Can anyone help me?  Running Breezy with the Ubuntu 2.6.10-686 kernel on an IBM Thinkpad T42.

Thanks!

---

### Post by nehalem on 2006-02-03
Ok, followed your directions and everything worked great except when I started to boot up on the new kernel.  Immediatly it spits out this and won't go further:

PCI: Cannot allocate recourse region 7 of bridge 0000:00:1c:1
PCI: Cannot allocate recourse region 8 of bridge 0000:00:1c:1
PCI: Cannot allocate recourse region 9 of bridge 0000:00:1c:1

Then it won't go further.  Can anyone help?  

I should mention I changed two things, the hz to 100 and the processor to pentium M (centrino)

I'm recompiling with 1000 and pentium pro (default).  I get the feeling that this has nothing to do with it.



Ok, that did nothing.  Did they change the drivers or something with 2.6.14?

I should also mention that I have an HP Compaq nc8230 laptop with the Pentium M 2Ghz processor and the x600 processor.  The current kernel locks up every now and again (maybe my video?) and it whines when idle and on battery, supposedly because of the hz stuff.

Fixed it by adding acpi=noirq on mnu.lst
My wireless does not work anymore however.
ipw2200 shows when doing lsmod, anyone have some ideas?

---

### Post by goombah88 on 2006-02-04
[QUOTE=Micro Rotors]opps,,, my mistake, but it still says the same when I add my user name.

ok,,, Has anyone really done this like the thread tells you at the beginning? Also 3 attempts have chewed up a gig of my drive that I want back somehow. Is there a way to abort this stuff without leaving stuff in who knows were?[/QUOTE]


the flag it's referring to is the -p1 part.  it's a one, not the letter "L" after the p.  i made the same mistake once before.  hopefully that will help you out.

---

### Post by goombah88 on 2006-02-04
[QUOTE=firecat53]Hey...successfully compiled the 2.6.15 kernel with ck1 patch using gcc-4.0.

I initially had trouble with the cardbus PCMCIA cards being detected, but a second reboot cured that problem. Now I just have to figure out the splash screen issue and fix the touchpad scroll feature. Already recompiled madwifi and wpa_supplicant.

Good how-to :)

Thanks, Scott

[edit]Does anyone have any suggestions for fixing the touchpad vertical scroll feature? I've been looking and I'm getting stumped.  All features of the touchpad work fine except the vertical scroll area. Here's the output from "cat /var/log/Xorg.0.log|grep synaptics"

(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
Synaptics Touchpad no synaptics event device found (checked 1 nodes)
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(II) UnloadModule: "synaptics"

Hmmm...so why would the touchpad not be detected but it all works except for one feature??
[/edit][/QUOTE]


refer to post #234 in this thread.  you have to compile into the kernel the option for "event interface".  the info section in qconf will show that it will be compile as module 'evdev'.  compiling that into my kernel (i'm running right now on a 2.6.14-ck9 kernel on a gateway laptop with the scrolling working in my touchpad) and not as a module is what got my touchpad working again.  hope this helps.

---

### Post by ErikTheRed on 2006-02-05
I'm still having problems compiling the latest vanilla kernel with the archck patchset. When I try to patch the kernel I still get the "Reversed (or previously applied) patch detected! Assume -R? [n]" error code at several places during the patching process. I encountered this while compiling the 2.6.15.2 kernel with the 2.6.15.2-archck3 patch.

I created a thread with the errors [here]("http://ubuntuforums.org/showthread.php?t=125995")

---

### Post by merc on 2006-02-07
Hey. I'm running an amd64 machine with 64bit breezy. I tried your instructions, but I used the 2.6.15 kernel and the archck patch. Ran into a nasty bug which wouldn't let me compile. Something about "undefined reference: cfb_fillrect cfb_copyarea cfb_imageblt". Google helped me out, I changed a Makefile, and now it compiles perfectly.

The thing is, I've compiled the kernel around 10 times since, and everytime something or the other gets messed up. Boot time errors about USB, inability to mount external ext3 partitions, etc. I've built off of the default ubuntu 2.6.12 .config file, and it still does that.

Does anyone have a nicely working kernel (2.6.14 or 2.6.15) that they want to share the .config file for? I can redo the device drivers to match my system.

I also read about how the 2.6.15 uses new stuff that requires updated udev and other such. So I'll try the 2.6.14 kernel with the archck patch tonight, see if that remedies my situation.

---

### Post by merc on 2006-02-07
[QUOTE=juantxorena]A lot. It depends on how many things are being compiled as a module and as a part of the kernel. In my case, with an AMD 2600+ overclocked at 2600MHz (equivalent to an AMD 2800+), and with a stardard kernel configuration, without things like PCMCIAor tape support, about 2 hours and 30 minutes.

Get a cup of coffe.[/QUOTE]

Something seems *really* off. I have an Athlon64 clocked at 2.0Ghz, and a standard compile (not including scsi tape and pcmcia support and such) of the 2.6.15 takes ~20 minutes. It's never taken more than 30 minutes (of the dozen or so times I've compiled it). I can't imagine why your system takes that long...

---

### Post by priam on 2006-02-09
Great guide, i followed it through and had few problems (the ones i did have were of my own doing ; ).  This has been my first attempt at compiling a kernel; i generally just go with the stock kernel of the distro i am using at the time.  

After i finished, however, i went to boot the kernel and i get no splash, which i read back and found is included in the archCK patchset. Also the way it boots looks like it does when i boot into rescue mode (i can't describe it any other way, and i don't know where to get the info to post here).  It gets to a certain point and then does nothing, and for awhile it just shows nothing at all, just a blank screen).

My suspicion is the problem comes from my kernel config, but i even went back and used the config from my old kernel.  Nothing.  Any recommendations? My specs are below:

What i am using:
Kernel 2.6.15
CK3 2.6.15
Old Kernel: (Ubuntu stock 2.6.12 k7)

Hardware:
AMD Athlon XP 1800+
512 PC3200
ati radeon 9600XT 256mb
yamaha waveforce soundcard
ECI k7s5a Motherboard

priam

---

### Post by firecat53 on 2006-02-10
For those of you trying to use the archck patchsets, you need to patch the plain kernel:  2.6.15.  Not 2.6.15.4, etc.  The various updates to the latest version are included in the patch.  That little fact is actually on the archck website...but sorta buried in all the words :)

Good luck, Scott

Oh, and the evdev module (with a reboot) did fix the touchpad!

---

### Post by priam on 2006-02-11
Ok, i managed to get out where it fails on boot.

```

[4294693.260000] ./hotplug.functions: line 168: 6050 segmentation fault $ hsfmc97sis: can't be loaded
Missing kernel or user mode driver hsf97sis
sis900: already loaded

```

My drivers for my modem work fine in my k7 kernel, but don't work in my new config (tried it with archck3.2 now) .  I've installed uninstalled successfully a few times and tried building the modules in the new kernel in emergency mode, but nothing works.

*using a US robotics v.92 56k modem, with HSF Conexant drivers from linuxant.com

priam

---

### Post by morphyno on 2006-02-15
My Intel wireless controller works fine for 2.6.12-10 but not 2.6.14 w/ patch.

controller are as follows

0000:02:01.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

Should i attempt to install the driver from Intel's website? When i boot in 2.6.14 it sees the card via "lspci" but when i ran "ifconfig" it doesnt display any interfaces for the wireless controller.

I'm using a Dell Inspiring 700m laptop, if anyone already found a solution to this, that will be very helpful.

---

### Post by aslocum on 2006-02-15
did you compile support for it into the kernel?
make sure you have following options in the kernel:
Networking: all of the IEEE822 stuff
Networking->Networking Options: Packet Socket
Device Drivers->Network device Support->Wireless Lan->Intel PRO/Wireless 2200BG and 2915ABG Network Connection 

if you compiled it as module make sure you have ipw2200 in your /etc/modules

---

### Post by Subbu.exe on 2006-02-15
I Compiled 2.6.15 with CK4 Patch.
It Compiled Well, But I Cannot see My Loading-Splash Screen!!!
and I Get some "Could not execute pmount" errors When I Access my CDRom
I Hafta Access it from /cdrom/ Manually! Is it Just Me Who's Getting these Errors?

---

### Post by curtis on 2006-02-15
[QUOTE=Subbu.exe]I Compiled 2.6.15 with CK4 Patch.
It Compiled Well, But I Cannot see My Loading-Splash Screen!!!
and I Get some "Could not execute pmount" errors When I Access my CDRom
I Hafta Access it from /cdrom/ Manually! Is it Just Me Who's Getting these Errors?[/QUOTE]
You won't see your splash screen as you don't have the patches for Usplash.
Not sure about your CD drive issues though, sorry.

---

### Post by John.Michael.Kane on 2006-02-15
@curtis so this kernel is not completely patched then is that what your saying?, and does this also pertain to the OP listed kernel  2.6.14. they are just performance kernels? if so how does one get a complete kernel including the ubuntu splash?

---

### Post by John.Michael.Kane on 2006-02-17
@RubenGonc can the deb file made be applied to new installs using just 
```
sudo dpkg -i kernel-image-2.6.14*.deb
``` or is there other files that need to be installed? it would a shame to have to complie the kernel over again, If a user should have to reinstall. also does the deb file have to be put in certain folder for the listed code to work?

---

### Post by imrumpf on 2006-02-17
@ **SD-Plissken**

The deb file can be archived to a CD and reinstalled later. When compiling and made into the deb file, it knows where everything should be put. Much like a program deb file that you download off the internet, it doesn't matter what directory it is dpkg'd from.

@ Everybody

I have updated the [BreezyCust]("http://doc.gwos.org/index.php/BreezyCust") page to use the archck7-bootsplash patch instead of the ck1 patch. Go to power tweaking, Kernels, and the HOWTO there. I have done it on 3 computers now and everything worked great, plus my uplash worked great. Hopefully the newest patch with usplash will fix some people's problems.

Edit: I'm not sure if it works, but the website SAYS the ck7 patch has Suspend2 as well as other neat features in it. Perhaps this tutorial can be used for laptop users as well to get Suspend2 on their systems?

---

### Post by John.Michael.Kane on 2006-02-17
@imrumpf used your archck7, and no boot splash i'm running ubuntu on a laptop 15.4"screen. any ideas?

Also Those who do have the boot splash showing using the exact methods in the guide, if you can post your .deb files for the versions your using. ie: 686 k7 or 64bit kern..

---

### Post by John.Michael.Kane on 2006-02-18
Found that theres a section in the list of things you can do, during the edit part of the krenel build. that allows you choose the ck patched bootsplash. will see if this brings the splash back..

---

### Post by imrumpf on 2006-02-18
Good somebody was making progress...I was completly stumped. I have a deb file of the one i installed which works perectly...is there someplace I could host it for others to download?

---

### Post by John.Michael.Kane on 2006-02-19
imrumpf if that kernel you got is for a k7 amd. i sure do hope you can find hosting. or maybe just email to those who need it.

on a side not the boot splash options so far have still left a black screen. will keep trying till someone can post their fully working kernel.deb

---

### Post by newuser111 on 2006-02-19
you should use the archck patch which contains the fbsplash patch, this is confirmed to work by multiple posters including me

I actually didn't have to check anything related to the splash in the kernel config, it autodetected the splash when installing the deb file

i just compiled the archck4 (2.6.15) patch the other day and the boot splash is working

---

### Post by imrumpf on 2006-02-19
@SD-Plissken

I have a P4 sorry :( but what I CAN do for you is compile an AMD version for you, install it and see if my bootsplash works. I'm not sure e-mailing will be a good idea, as (if i remember correctly) the deb file is in the range of around 50 MB.

@newuser111

duh! i should have thought about that. See the archck patchset changed from using bootsplash to fbsplash in the archck7 update. Try [this patch link]("http://iphitus.loudas.com/arch/ck/2.6.14/patch-2.6.14-archck7.bz2") (which uses fbsplash, not bootsplash) and see what results you get. The file is named **archck7** instead of **archck7-bootsplash**, so please review and change the instrustions accordingly to make sure there are no errors.

---

### Post by SubtleAggression on 2006-02-19
I am completely new to all of this so im diving in head first. < best way to learn > so this morning i started with the kernal upgrade however just before compiling i got this error.

[B]
[COLOR="DarkOliveGreen"]drivers/isdn/icn/icn.c: In function ‘icn_pollbchan_send’:
drivers/isdn/icn/icn.c:373: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[4]: *** [drivers/isdn/icn/icn.o] Error 1
make[3]: *** [drivers/isdn/icn] Error 2
make[2]: *** [drivers/isdn] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.14cK1'
make: *** [stamp-build] Error 2
root@PuzzleBox:/usr/src/linux# sudo dpkg -i kernel-image-2.6.14*.deb
dpkg: error processing kernel-image-2.6.14*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kernel-image-2.6.14*.deb
root@PuzzleBox:/usr/src/linux#
[/COLOR][/B]

what did i do wrong? and ideas? i was so close to being finished! anyway if someone could help out a newbie in need who just put his XP CDs on a shelf and swore them off, id very much apreciate it!

---

### Post by newuser111 on 2006-02-19
in the kernel config "sudo make xconfig" or whatever you used, uncheck the ISDN drivers, because this is what is causing the error, as long as you don't use ISDN, this shouldn't be an issue, I don't know why they aren't compiling for you

---

### Post by SubtleAggression on 2006-02-19
[QUOTE=newuser111]in the kernel config "sudo make xconfig" or whatever you used, uncheck the ISDN drivers, because this is what is causing the error, as long as you don't use ISDN, this shouldn't be an issue, I don't know why they aren't compiling for you[/QUOTE]
 kewl, i will try that thanks for the quick reply! :)

---

### Post by SubtleAggression on 2006-02-19
ok, new problem. i just removed all the ISDN options, saved and closed and it gave this error.

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
#
# using defaults found in .config
#
 any ideas?

feel free to instant message if its easier. 
thanks again!

---

### Post by newuser111 on 2006-02-19
[QUOTE=SD-Plissken]imrumpf if that kernel you got is for a k7 amd. i sure do hope you can find hosting. or maybe just email to those who need it.

on a side not the boot splash options so far have still left a black screen. will keep trying till someone can post their fully working kernel.deb[/QUOTE]

here is a k7/duron/athlon kernel i compiled with the 2.6.14 archck7 patch +EVMS patch

[http://rapidshare.de/files/13634643/kernel-image-2.6.14-archck7_archck7_i386.deb.html](http://rapidshare.de/files/13634643/kernel-image-2.6.14-archck7_archck7_i386.deb.html)


there is a downside however, you wont have the kernel headers (source) if you need it to compile ati or nvidia video card drivers, although if you unpack the 2.6.14 kernel source from kernel.org to /usr/src and rename it linux-2.6.14archck7 it should work, not tested by me however

---

### Post by SubtleAggression on 2006-02-19
kewl, i will try it out. shouldnt be too hard to swap em out. thanks!

---

### Post by Rizado on 2006-02-19
usplash is supposed to work without any kernelpatch, not bootsplash or fbsplash. But fbsplash is quite cool. I got it working right now, but only in verbose mode. Silent doesn't work, but that's probably because i haven't installed any scripts yet.

---

### Post by Eazy© on 2006-02-19
Hi all!

I have compiled the 2.6.14 kernel and applied the ck9 patch. I also applied the 2.6-bd-claim patch to sort the mounting problem. 
I now have a problem with the sound in UT2004. I have compiled my own openal.so from this: [http://www.lost.org.uk/openal.html](http://www.lost.org.uk/openal.html) so I get hardware sound in UT2004. This worked very well with orginal ubuntu kernel (2.6.10-k7), but with the 2.6.14 kernel I have no sound at all in UT2004 (sound works with for example amaroK) If I use original openal.so sound works, but not very well. Cant get ambient sound level lower whatever I do.

Is there something I might have missed when running menuconfig, like something with the sound card the have to be built in and not as a module?

This is a big issue for me as I play UT2004 alot, and I'm tired to boot to winxp whenever I want to play. So if anyone have an idea, please help!!

Edit: My soundcard is a Soundblaster live 5.1 digital

Best regards
Eazy

---

### Post by flummoxed on 2006-02-19
When you install the kernel, it asks you a million questions about what to install, and what not to install. How are you supposed to tell? Can you just keep pressing enter until the end? Or should you look at each thing carefully, and try determine whether you need it or not? Because a lot of the things came with cryptic descriptions that didn't help me at all.

What's the easiest route to weave your way through the questions?

---

### Post by imrumpf on 2006-02-19
The reason for the million options is because you did sudo make config instead of sudo make xconfig, at least thats what happened to me when I did it. for some reason when doing it on a fresh install of Kubuntu the xconfig command failed, yet worked fine on Ubuntu. I was forced to do what was mentioned above by doing the config command instead of xconfig.

---

### Post by pestilence on 2006-02-23
[QUOTE=flummoxed]When you install the kernel, it asks you a million questions about what to install, and what not to install. How are you supposed to tell? Can you just keep pressing enter until the end? Or should you look at each thing carefully, and try determine whether you need it or not? Because a lot of the things came with cryptic descriptions that didn't help me at all.

What's the easiest route to weave your way through the questions?[/QUOTE]

Well actually from console just issue **make menuconfig** but i strongly recommend you do actually read and understand kernel options, your systems performance / stabillity and hardware support depend on this options.

---

### Post by pestilence on 2006-02-23
[QUOTE=Rizado]usplash is supposed to work without any kernelpatch, not bootsplash or fbsplash. But fbsplash is quite cool. I got it working right now, but only in verbose mode. Silent doesn't work, but that's probably because i haven't installed any scripts yet.[/QUOTE]

Thats because you haven't installed any theme files ;) just fetch a nice themed tarball and follow the instructions :)

---

### Post by souled on 2006-02-24
[QUOTE=theh0g]You have to remove EVMS, I had the same problem and this fixed it.[/QUOTE]

Does this mean I have to patch the kernel with the EVMS patch and then compile?

---

### Post by elektronaut on 2006-02-24
[QUOTE=souled]Does this mean I have to patch the kernel with the EVMS patch and then compile?[/QUOTE]

I also have some problem connected to evms. After the compilation, during installation I get this error:
```

evms_open_engine() failed with error code 13: Permission denied

```
May I just ignore this, or what should I do? I don't know much about evms, just read about an evms patch. Shall I patch the kernel somehow, or can I disable evms during the configuration? But
```

less .configure|grep evms

```
didn't give me any results. I don't remember having it activated anywhere. 
(I compiled a 2.6.15 kernel with archck4 patch applied)

---

### Post by elektronaut on 2006-02-24
Oh no, I just tried to reboot and got kernel panic with vanilla. And strangely and frighteningly none of the other kernels wants to boot. Not even in recovery mode. I get
```

hdc: request sense failure: error+0x20 ...

```
and then, after a while
```

atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.

```
What can I do? I should mention that root and home are logical volumes (see LVM), formatted with XFS.

---

### Post by clemcat on 2006-02-25
Did I do something wrong, or is the "building" of the deb package supposed to take forever?

---

### Post by clemcat on 2006-02-25
Well, it took and hour and a half to build the package, but right now everything worked like a champ!

---

### Post by elektronaut on 2006-02-25
Is there nobody with an idea what I should do, or might it be better to start a new thread?

---

### Post by fezzik on 2006-02-26
Ok everybody.  Tomorrow after church sometime I am coming home to recompile.  I have to since scroll doesn't work because of the missing event thing in there.  A few questions.  First would it be better to go with the newest one out there or just recompile 2.6.14-ck1?  I have a compaq laptop.  It seems that the new Kernel actually improved my screen resolution somehow.  Or atleast it appears sharper.  Will I have to download and install Ndiswrapper everytime I compile a kernel?  How do you do that thing to put event back in so you can make your touchscreen work again?  Is there a Kernal and or patch with the ALPS drivers?  Do these other Kernels help Newbie's much or do you have to know what you are doing in Linux?  I am learning and rather enjoying this Linux thing and the new Kernal helped my computer's performance it seems but is that all these are or is there something much more significant to it?  What is the best Kernel for me to compile on my PIV laptop with Hyperthreading ATI Radeon 9000IGP Graphics ALPS touchscreen mouse thingy sd/mmc card reader Broadcom WiFi?  Most of the stuff is easy to figure but if there is a Kernel out there better than another for some reason.  I would love to use it instead.  Where is the best place to look for Kernels?  I went to Kernel.org and they didn't have a lot of the ones that have been talked about on here.

---

### Post by Zubzub on 2006-02-26
I compiled and installed the kernel from the how-to several weeks ago, no probs, everything ran fine and stable. Then I did a format (RIP WIN XP) reinstalled kubuntu, installed this kernel and all seemed to work fine after I rebooted the new kernel. Little later I reboot again and my terminal wouldn't recognise random simple commands :-k  So I rebooted again and nothing (not even the stable ubuntu provided kernel) would boot, I got root mounting, tty and sh stuff errors :confused:

strange shit dude...

---

### Post by elektronaut on 2006-02-26
[QUOTE=elektronaut]Is there nobody with an idea what I should do, or might it be better to start a new thread?[/QUOTE]
O.K., gladly I found a way to recover the data on my laptop: I burnt a [SystemRescueCd]("http://www.sysresccd.org/"), booted and mounted the partitions doing this:
> 
root@slack:~# vgscan
root@slack:~# vgchange -ay

And you'll see the VG in the "/dev", likes "/dev/vg_main".
Than you make the mount point, like:
root@slack:~# mkdir /mnt/LVM_images

And, finally mount it!!
root@slack:~# mount /dev/vg_main/lv_data /mnt/LVM_images

I found the advice [here]("http://www.sysresccd.org/forums/viewtopic.php?t=598"). I can only advice everybody to backup the whole system with an image tool BEFORE playing around with a new kernel. Which is what I'll do now after setting up the system again ;)

---

### Post by pestilence on 2006-02-26
```

pestilence@odin:~$ uname -a
Linux odin 2.6.15-pestilence-2b #1 PREEMPT Sun Feb 26 16:07:57 EET 2006 i686 GNU/Linux

```

2.6.15 +CK patches + DSDT patchset + Latest ATI drivers working like a charm

```

pestilence@odin:~$ glxgears
21359 frames in 5.0 seconds = 4271.780 FPS
21713 frames in 5.0 seconds = 4342.471 FPS
21704 frames in 5.0 seconds = 4340.663 FPS

```

They score +1000 higher than previous scores.

---

### Post by elektronaut on 2006-02-27
[QUOTE=elektronaut]O.K., gladly I found a way to recover the data on my laptop: I burnt a [SystemRescueCd]("http://www.sysresccd.org/"), booted and mounted the partitions doing this:

I found the advice [here]("http://www.sysresccd.org/forums/viewtopic.php?t=598"). I can only advice everybody to backup the whole system with an image tool BEFORE playing around with a new kernel. Which is what I'll do now after setting up the system again ;)[/QUOTE]
Funny: These actions seem to have repaired what the compiled kernel fucked up, now I could boot with one of the older kernels :D

---

### Post by fezzik on 2006-02-27
Ok so I have no idea how or from where you get the patches you all have talked about but Yesterday I compiled 2.6.15.4 and what Kernal.org had was just 2.6.15.4 and 2.6.15.4patch.  SO I did that.  It seems to work great on my laptop.  I checked the event thing so my touchscreen thing works the way I am used to again and my wireless is up due to downloading and installing the newest Ndiswrapper and getting everything up and running again.  Maybe if and when I learn how to find all these patches and which ones might be best for my laptop then I may do this again.  It wasn't that bad just took a while.  The second time wasn't that bad but I think that is because now it knows that I have a PIV processor before it was thinking I had a Pentium Pro whatever that is.  So it seems to be working a lot better now.  Thanks for the help.  Hey if yall can point me toward these patches and something telling me what they are I would really appreciate it.  But for now I think I am good.  Right now I experiment to learn and some of these changes are just for changes sake so I can learn and hopefully improve the computers performance while also improving my understanding.  

Peace.

---

### Post by elektronaut on 2006-02-27
[QUOTE=fezzik]Hey if yall can point me toward these patches and something telling me what they are I would really appreciate it. [/QUOTE]
If you read the posts in this thread you'll find the links. It's even mentioned in the HowTo on the first page. There are the [ck]("http://ck.kolivas.org/patches/2.6/") and the [archck]("http://iphitus.loudas.com/archck.php") patches. I'm also still a linux newbie, apparently the archck patches come with more features and are built upon the ck patches. If you patch a kernel, the kernel mustn't have the corresponding minor version number (e.g. patch kernel 2.6.15 with archck4.1, not kernel 2.6.15.4). 2.6.15 gave me nothing but trouble (see my posts above). You can read elsewhere in the forum that 2.6.15 doesn't fit to Breezy because Breezy expects the kernel to support hotplug, but with 2.6.15 the kernel guys changed to udev. A solution seems to be if you install the Dapper packages (with dependencies) for udev. But I didn't try this. I prefer to check out 2.6.14. 
Can somebody tell me what I should prefer: Regular kernel 2.6.14.7 or a patched 2.6.14 (ck or archck)? And will it work with my LVM? No evms error?

---

### Post by souled on 2006-02-27
I compiled kernel 2.6.15 with ck patch 4. I got the mounting problem, so I when to the evms site and followed the directions to patch the kernel and install the program. This fixed my mounting error. I don't notice any other problems.

---

### Post by John.Michael.Kane on 2006-02-27
Has any figured out the splash problems. last time i tried this i the kern compile turned out fine, however the boot screen was black.

---

### Post by elektronaut on 2006-02-27
[QUOTE=souled]I compiled kernel 2.6.15 with ck patch 4. I got the mounting problem, so I when to the evms site and followed the directions to patch the kernel and install the program. This fixed my mounting error. I don't notice any other problems.[/QUOTE]
Can you give me a link to this patch, please? I was on the site but don't know which patch to choose and how to proceed. Do you apply it after the archck patch? What about hotplug problems? Are you using LVM or EVMS? (I don't have any idea yet what EVMS is and if I need it. Just started to use LVM.)

---

### Post by souled on 2006-02-28
For the 2.6.15 kernel, just replace the 4 in the link with a 5

For ck patch 4 (for kernel 2.6.15) [http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)

Follow the HOWTO, but whenever you see 2.6.14, replace it with 2.6.15. Whenever you see ck1, replace that with ck4. 

Regarding hotplug, I'm not sure what that is. If you can give me some commands, I can paste the results that I get. 

I am using EVMS. Start [here]("http://evms.sourceforge.net/install/"). When I compiled 2.6.15, I got that "/dev/hdb5 is busy..." message thing. I just followed those steps, and I got everything working. I can mount all of my file systems perfectly. 

I do have a black screen where usplash is supposed to be, but I don't really care about that.

The only major problem I'm having is configuring my Logitech mx700 mouse. I just tried to use my same settings in Xorg as I've been using before (followed the Logitech howto), but it induces a kernel panic. Haven't investigated much further than that so far.

---

### Post by obe1kenobi on 2006-02-28
Is this going to be a standard update for Breezy or is it only going to be available through this method?

---

### Post by elektronaut on 2006-02-28
[QUOTE=souled]
Regarding hotplug, I'm not sure what that is. If you can give me some commands, I can paste the results that I get. [/QUOTE]
Hotplug is AFAIK the automatic recognition of peripheral devices that you connect while the system is running.
[QUOTE=souled]
I am using EVMS. Start [here]("http://evms.sourceforge.net/install/"). When I compiled 2.6.15, I got that "/dev/hdb5 is busy..." message thing. I just followed those steps, and I got everything working. I can mount all of my file systems perfectly. [/QUOTE]
I guess I have to read more about it to understand the difference between LVM and EVMS. But I got another error than you: 
```

evms_open_engine() failed with error code 13: Permission denied

```
[QUOTE=souled]
I do have a black screen where usplash is supposed to be, but I don't really care about that.
[/QUOTE]
This seems to be resolved if you apply the [archck patch]("http://iphitus.loudas.com/arch/ck/2.6.15/patch-2.6.15-archck4.1.bz2") instead of the ck patch. It's called the fbsplash feature. 
[QUOTE=souled]
The only major problem I'm having is configuring my Logitech mx700 mouse. I just tried to use my same settings in Xorg as I've been using before (followed the Logitech howto), but it induces a kernel panic. Haven't investigated much further than that so far.[/QUOTE] 
I guess this is a hotplug problem (see above, udev installation of Dapper packages), or?

---

### Post by elektronaut on 2006-02-28
[QUOTE=obe1kenobi]Is this going to be a standard update for Breezy or is it only going to be available through this method?[/QUOTE]
Breezy kernel version is frozen. No feature update, only security updates.

---

### Post by pestilence on 2006-02-28
[QUOTE=SD-Plissken]Has any figured out the splash problems. last time i tried this i the kern compile turned out fine, however the boot screen was black.[/QUOTE]

Appart from compiling bootplash (if you are meaning bootsplash) into the kernel you need also to install the bootsplash package and create a theme ([http://www.bootsplash.org)](http://www.bootsplash.org)).
If you mean **usplash** which is not a kernel package, you just need to modify the file bellow:
```

/usr/share/initramfs-tools/scripts/init-top/usplash

```

And change the line:
```

if [ $VESA = "true" ]; then
        insmod /lib/modules/`uname -r`/kernel/drivers/video/vesafb.ko
    else

```

The line above is the corrected version, since you are changing the kernel you need also to change the location of your vesafb module.

---

### Post by pestilence on 2006-02-28
[QUOTE=obe1kenobi]Is this going to be a standard update for Breezy or is it only going to be available through this method?[/QUOTE]

I am thinking of following a Gentoo-ish like way of patching kernels and releasing them as deb source packages, but yet again this is just an initial thought, i am new to Ubuntu and as an ex-Gentoo user i need to get comfy with the apt and deb and make-pkgk tools ;)

---

### Post by newuser111 on 2006-02-28
interesting post pestilence

when i found out about archck i compiled it and the splash screen worked fine, and ive done this several times, and the splash screen still works after rebooting and completely uninstalling the old kernel, I only assumed it was the fbsplash but it probably is not

i also dont have the lines you say to edit in /usr/share/initramfs-tools/scripts/init-top/usplash

> #!/bin/sh

PREREQ=""
prereqs()
{
	echo "$PREREQ"
}
case $1 in
# get pre-requisites
prereqs)
	prereqs
	exit 0
	;;
esac

SPLASH=false;
VESA=false;

for x in $(cat /proc/cmdline); do
	case $x in
	splash*)
		SPLASH=true;
		;;
	vga=*)
		VESA=true;
		;;
	esac
done

if [ $SPLASH = "true" ]; then
	depmod -a
	modprobe fbcon
	if [ $VESA = "true" ]; then
		modprobe vesafb
	else
		modprobe vga16fb
	fi
	mknod /dev/fb0 c 29 0
	for i in 0 1 2 3 4 5 6 7 8; do
		mknod /dev/tty$i c 4 $i
	done
	/sbin/usplash -c &
	sleep 1
fi

---

### Post by souled on 2006-02-28
[QUOTE=elektronaut]Hotplug is AFAIK the automatic recognition of peripheral devices that you connect while the system is running.

I guess I have to read more about it to understand the difference between LVM and EVMS. But I got another error than you: 
```

evms_open_engine() failed with error code 13: Permission denied

```

This seems to be resolved if you apply the [archck patch]("http://iphitus.loudas.com/arch/ck/2.6.15/patch-2.6.15-archck4.1.bz2") instead of the ck patch. It's called the fbsplash feature. 
 
I guess this is a hotplug problem (see above, udev installation of Dapper packages), or?[/QUOTE]

I can connect my phone via USB, and it is automatically mounted. Does this mean hotplug is functioning?

When you get that 'permission denied,' don't you just have to run as root? Usually when you get a permission denied error, it's because you aren't root.

---

### Post by John.Michael.Kane on 2006-02-28
@newuser111 is your kernel complied for k7, 686 or 64bit version of ubuntu. i have tried both the 14 and 15 versionsof the kern and both work just fine, however the org ubuntu splash screen is replaced a black screen. if you have a working kern for k7 with splash. could i take a look at it. provided it was saved in .deb format.

---

### Post by newuser111 on 2006-02-28
plissken check the past posts, i already posted a k7 kernel when you asked for it

---

### Post by John.Michael.Kane on 2006-02-28
newuser111 i seen the deb you posted. it is 386 based. just like the normal kern you get on a fresh install. did not think the k7 kern was 386 based...

Side note tested it, and it depends on initramfs-tools (>= 0.36ubuntu6) which my install does not have, and it is not listed in synaptic. so will have to pass on your deb file. thanks though..

---

### Post by obe1kenobi on 2006-02-28
What are the links to the most recent kernel and patches?

---

### Post by elektronaut on 2006-02-28
[QUOTE=souled]I can connect my phone via USB, and it is automatically mounted. Does this mean hotplug is functioning?[/QUOTE]
Well, I'm really not an expert on this. I don't know if the phone counts, just read about problems with external storage devices.
[QUOTE=souled]
When you get that 'permission denied,' don't you just have to run as root? Usually when you get a permission denied error, it's because you aren't root.[/QUOTE]
I sure was root - otherwise the whole compilation wouldn't have worked (e.g. writing the .deb file to /usr/src). It's strange though that I seem to be the only one who got this message.

---

### Post by souled on 2006-02-28
Well, my phone is pretty much an external storage device. It has a 512 Mb flash card, and I can put whatever I want on it.

---

### Post by elektronaut on 2006-02-28
Regarding the EVMS patch, I found a link to [an easy patch procedure ]("http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10") in an older post of this thread. I'm trying this out right now with 2.6.14 and archck7 and will post the results later.

---

### Post by Posessor on 2006-02-28
I did a clean install of Ubuntu and installed a new kernel (2.6.15 with Archck 4.1) right after installation was complete to avoid any problems with already installed programs. So when rebooted everything was spectacular except that I can't mount my two sata vfat hard drives any more. Please help cause all my files are on those drives they're two 300GB drives so you can imagine how much files I have on there!!

thx in advance

---

### Post by elektronaut on 2006-02-28
[QUOTE=Posessor]I did a clean install of Ubuntu and installed a new kernel (2.6.15 with Archck 4.1) right after installation was complete to avoid any problems with already installed programs. So when rebooted everything was spectacular except that I can't mount my two sata vfat hard drives any more. [/QUOTE]
Sounds a bit like my problem (see my posts these last days). Can you boot from an older kernel? If not, I would advice you to use a live linux cd to access your drives. For example SystemRescueCd. Then you can either save everything to some other storage media or try to repair stuff.

---

### Post by Posessor on 2006-02-28
[QUOTE=elektronaut]Sounds a bit like my problem (see my posts these last days). Can you boot from an older kernel? If not, I would advice you to use a live linux cd to access your drives. For example SystemRescueCd. Then you can either save everything to some other storage media or try to repair stuff.[/QUOTE]

yes, I can perfectly boot from an older kernel but I just wanted this to work because the install kernel I'm using is a bit older than this one and this one is just feels faster. And I had some issues with my bt848 card that I hoped this kernel would solve.

---

### Post by newuser111 on 2006-02-28
the problem is that you did not apply the EVMS patch, which is not mentioned in the howto, but is required since it is used by ubuntu

two options you have are to uninstall evms from synaptic or recompile the kernel with the evms patch applied, check past posts since I posted how to do it

---

### Post by newuser111 on 2006-02-28
[QUOTE=SD-Plissken]newuser111 i seen the deb you posted. it is 386 based. just like the normal kern you get on a fresh install. did not think the k7 kern was 386 based...

Side note tested it, and it depends on initramfs-tools (>= 0.36ubuntu6) which my install does not have, and it is not listed in synaptic. so will have to pass on your deb file. thanks though..[/QUOTE]


no, it is a k7 kernel, it wont work on non amd systems, the 386 refers to the machine arch not the specific cpu optimization

i think the intramfs-tools error you get is because i am using dapper and hence a different version of intrafms tools than you

---

### Post by phreaky- on 2006-03-01
Very nice tutorial I managed to get 2.6.14 Vanilla up and running

---

### Post by elektronaut on 2006-03-01
[QUOTE=newuser111]the problem is that you did not apply the EVMS patch, which is not mentioned in the howto, but is required since it is used by ubuntu

two options you have are to uninstall evms from synaptic or recompile the kernel with the evms patch applied, check past posts since I posted how to do it[/QUOTE]
But he only wanted to mount vfat partitions. Does EVMS interfere in this case? 

And another question: Like I already posted, I compiled 2.6.15 without EVMS patch, booted, after kernel panic I couldn't boot even from the original kernels. Then I used SystemRescueCd which somehow fixed the problem, so I could boot again with an old kernel afterwards. Yesterday I enabled boot logging, and now the system again didn't boot (with original kernel). It said something like "bootlog daemon [failed]" and then tried to load EVMS module, where it stopped. I didn't try to boot the vanilla kernel since the first try, so that really surprises me. After fixing with SystemRescueCd and disabling boot logging now everything seems to be o.k. Can somebody explain me this behaviour?
[EDIT]*Hmm, I'm not so sure anymore that the boot problems with older kernels are related to LVM. It seems that my laptop sometimes doesn't recognize the DVD drive.*

---

### Post by elektronaut on 2006-03-01
I got two more questions:

1. How do I remove the malfunctioning 2.6.15 kernel? The debian package is in /usr/src and dpkg doesn't seem to notice it.
```

me@home:/usr/src$ sudo apt-get remove --purge kernel-image-2.6.15-archck4.1_ck4_i386.deb
...
E: Couldn't find package kernel-image-2.6.15-archck4.1_ck4_i386.deb
*/*I translated this from german*/*

```
Somewhere in the forum I found the advice to use synaptic and set the filter for uninstallable packages. I found the kernel and removed it using synaptic. I don't find any traces left in /boot, but the package is still in /usr/src. May I safely remove it?

2. What about the compiler version used for kernel compilation? I read [here]("http://www.ubuntuforums.org/showthread.php?t=85064&page=23") that 2.6.14 needs gcc 4.0. I once entered "export CC=/usr/bin/gcc-3.4" for VMWare compilation. Is this permanent or automatically overwritten with gcc 4.0 afterwards?
[EDIT]*O.K, I found the answer to the second question myself. If you use the export command it'll set the environment variable only for the session. You can check by typing "echo $CC".*

---

### Post by fezzik on 2006-03-03
Ok everyone.  I have 2.6.15.4 on there and running.  I will probably change back to 2.6.15 with an Arch patch just cause some of the arch patch features looked cool.  The question I have is the only problem I found so far is that when I put a cd in my drive it didn't automatically recognize it.  I had to go into the file system and open it manually.  I don't really have a huge problem with that except that the way it was running I could burn stuff really easily from desktop.    I don't know if it is that easy from the file system.  I haven't really tried.  Does this Evms thing y'all are talking about help that?  In other words make it automatically recognize it and put it on my desktop?

---

### Post by monkeyface on 2006-03-03
[QUOTE=fezzik]Ok everyone.  I have 2.6.15.4 on there and running.  I will probably change back to 2.6.15 with an Arch patch just cause some of the arch patch features looked cool.  The question I have is the only problem I found so far is that when I put a cd in my drive it didn't automatically recognize it.  I had to go into the file system and open it manually.  I don't really have a huge problem with that except that the way it was running I could burn stuff really easily from desktop.    I don't know if it is that easy from the file system.  I haven't really tried.  Does this Evms thing y'all are talking about help that?  In other words make it automatically recognize it and put it on my desktop?[/QUOTE]
I would like to know that too... =)

---

### Post by firecat53 on 2006-03-03
The arch patches also includes the 2.6.15.x updates (e.g. archck3 includes 2.6.15.3). That's why you have to start with the vanilla 2.6.15 kernel before applying the 2.6.15 patches.

Scott

---

### Post by madchicken on 2006-03-04
[QUOTE=fezzik]... Does this Evms thing y'all are talking about help that?  In other words make it automatically recognize it and put it on my desktop?[/QUOTE]

No. It's the problem with pmount...someone seems to have resolved it, but most of us in this thread are suffering of the same problem. I think we've to wait for Dapper before using a 2.6.15 kernel :???: .

Bye

---

### Post by GregaS on 2006-03-04
I have a problem with step 4.

Atfer this:

> sudo make xconfig

I get this errors:

> root@Blender:/usr/src/linux# sudo make xconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  SHIPPED scripts/kconfig/zconf.tab.h
  HOSTCC  scripts/kconfig/conf.o
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  HOSTCC  scripts/kconfig/zconf.tab.o
/usr/share/qt3/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
scripts/kconfig/qconf arch/i386/Kconfig
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

qconf: cannot connect to X server :0.0
make[1]: *** [xconfig] Error 1
make: *** [xconfig] Error 2

Help me please.

---

### Post by monkeyface on 2006-03-13
[QUOTE=madchicken]No. It's the problem with pmount...someone seems to have resolved it, but most of us in this thread are suffering of the same problem. I think we've to wait for Dapper before using a 2.6.15 kernel :???: .[/QUOTE]
But WHO has resolved it? I have completely stopped using Ubuntu because of this, and I soon have to set up a family pc, and Ubuntu would be nice to use. :mad:
Does it work when using an older kernel version, or?

Also, does usplash work with kernel 2.6.14 (can't remember)?

---

### Post by kaamos on 2006-03-14
[QUOTE=monkeyface]Also, does usplash work with kernel 2.6.14 (can't remember)?[/QUOTE]
Works fine with both 2.6.14 and 2.6.15

---

### Post by blackant on 2006-03-14
I couldn't get the usplash to work for me. :(

---

### Post by GregaS on 2006-03-14
Someone help me please :(

---

### Post by p47 on 2006-03-21
Hello everybody.

I have some problems with this tutorial I think that all is ok but when I want make this "make-kpkg clean"
I'm in usr/src/linux i root mode but...
When I do make-kpkg clean I got this error !...

[make1] leaving directory '/usr/src/linuc-ck1'
What can I do ?
Thank's a lot
kind regards

---

### Post by shinygerbil on 2006-03-25
@GregaS: I got the same error when I tried to use YaKuake to do this whole compilation thing. (it's just so *natural* to use it ;P )

You could try using Konsole, if this is the case. Otherwise I don't know..

Steve

---

### Post by syklitengutt on 2006-03-28
ok... Im now in the new kernel, but at startup, after selecting what kernel to boot up, the screen goes black until I get the login screen.
I cant see any information about whats starting up.

And I have 2 HDD and hdb1 isnt mounted anymore, and I cant mount it.
Its listed in fstab to mount in /mnt/hdb. But if I go to system-admin-disks
it finds the hdd but it sais that the partision is inaccessable and it isnt possible 
to mount it.

fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /boot           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1	/mnt/hdb	ext3	defaults	0	0


---

### Post by Jeff Eklund on 2006-03-29
I tried compiling the 2.6.14-kernel and applying the ck-patch. Iw all worked flawlessly. Booting went fine, I had usplash and everything. Only thing that stopped working were my quickscroll buttons on my touchpad (I'm using a laptop). I then tried compiling the 2.6.16 kernel with the corresponding ck patch and everything seemed to work fine. However, when I boot, usplash is gone and when I try to log in, using gdm, gdm tells me that my x-sessions crashes and xsessions_errors tells me this:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jeff"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: No space left on device

```
However, when I once more rebooted and tried starting with the 2.6.14-kernel that worked before, I get the same results with that kernel. Could someone help me out a little with this? :) 
Why doesn't the .14-kernel work anymore? what could I have done wrong?

---

### Post by zgerrz on 2006-03-29
Can someone assist me?

I started a thread here [http://www.ubuntuforums.org/showthread.php?t=151824](http://www.ubuntuforums.org/showthread.php?t=151824) but I haven't received any help.

I compiled a 2.6.16 kernel with archck patch support, but now iptables is blocking all internet traffic whenever I enable firestarter. It never had this behavior with the old kernel. I'm not sure what option I compiled or didn't compile to generate this problem.

---

### Post by zgerrz on 2006-03-29
Nevermind, I seemed to have managed to solve it after a lot of reading and trial and error.

By the way, excellent guide. Very simple, and I am now very comfortable with kernel compiling. Thanks!

---

### Post by Noahod on 2006-03-31
Hey, I'm having a problem with make xconfig which I wasn't having before:

> sudo make xconfig
Password:
  HOSTCC  scripts/basic/fixdep
In file included from /usr/include/sys/socket.h:35,
                 from /usr/include/netinet/in.h:24,
                 from /usr/include/arpa/inet.h:23,
                 from scripts/basic/fixdep.c:115:
/usr/include/bits/socket.h:304:24: error: asm/socket.h: No such file or directory
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2


I'm trying to get 2.6.16 with archck going, but I'm having the same error with my previously good 2.6.14 source directories, and am quite obviously missing a passage, just what I can't figure out?

Only thing I've done of significance is install kde 3.5, does anyone have any ideas? 

Thanks

---

### Post by Noahod on 2006-04-02
kernel headers went missing somehow, reinstalled the packages, working now.

---

### Post by instant on 2006-04-02
For some reason my wlan doesn't work in this kernel, but when
I boot into the old 2.6.12-9 it works like a charm. Any ideas how to fix it?

I seems like it is ndiswrapper which is causing the problem.
When i try: sudo modprobe ndiswrapper

It says it can't find the module. :( 

/instant

---

### Post by dpicker on 2006-04-04
[QUOTE=instant]For some reason my wlan doesn't work in this kernel, but when
I boot into the old 2.6.12-9 it works like a charm. Any ideas how to fix it?

I seems like it is ndiswrapper which is causing the problem.
When i try: sudo modprobe ndiswrapper

It says it can't find the module. :( 

/instant[/QUOTE]

You will need to recompile ndiswrapper for your new kernel.

Just download the latest ndiswrapper source and compile it whist you are using the new kernel. Only takes a few seconds and then you can do modprobe ndiswrapper again.

---

### Post by kleeman on 2006-04-05
Thanks for your clear howto. I have used it a lot to compile custom kernel debs. I installed the 2.6.17-rc1 kernel on dapper recently and solved a nasty scsi hardware problem I was having with the standard dapper kernel.

---

### Post by dpicker on 2006-04-06
The how to worked for me and I managed to get usplash even when using vga=0x31b in grub but what bugged me was that I never got tty consoles :(

And the archck patch seems to solve these problems. So i downloaded 2.6.16-archck2 and patched against 2.6.16 vanilla.

Shortly after starting to compile, there was an error relating to suspend2. I googled a bit and read that suspend2 doesnt work on amd64.. So i disabled it and started compiling again, but this time I get another error:

```
make[1]: Entering directory `/usr/src/linux-2.6.16archck2'
  CHK     include/linux/version.h
  CHK     include/linux/compile.h
  CHK     usr/initramfs_list
  GEN     .version
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
kernel/built-in.o: In function `swsusp_save':
: undefined reference to `suspend_post_context_save'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.16archck2'
make: *** [stamp-build] Error 2
root@mesh:/usr/src/linux#
```

Anyone know what to do?

---

### Post by demessmaker on 2006-04-10
Error MSG at step 5 of guide.

I keep getting error the following after I issue  "make-kpkg clean"

root@LGC-P004:/usr/src/linux# make-kpkg clean
    Could not locate the rules file (Normally found at the location
 /usr/share/kernel-package/rules), which would seem an
 impossibility. I give up.
Could not find rules file


Any help would be greatly appreciated.

Thanks

---

### Post by xyz on 2006-04-12
Hi-first, thank you for all the work you put into this HowTo.
All seemed to have gone well until I ran:
```
sudo dpkg -i kernel-image-2.6.14*.deb
```


And I got this:
> root@meander:/home/th#  sudo dpkg -i kernel-image-2.6.14*.deb
dpkg: error processing kernel-image-2.6.14*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kernel-image-2.6.14*.deb

Can anyone help me out? Thanks in adv.
noob here!

Well it works now!
I opened "File Browser" as root and went to /usr/src and made " kernel-image-2.6.14_ck7_i386.deb" Executable! And this one too "linux-2.6.14.tar.bz2"
Then I ran:

```
 sudo dpkg -i kernel-image-2.6.14_ck7_i386.deb

```

AND NOT:
```
sudo dpkg -i kernel-image-2.6.14*.deb

```
N00b making his way...

I am visually impaired and,believe it or not, LCD's too bright for what's left of my eyes.
Kernel .386 and/or .686 was good to me because I could run this to lower brightness on my Toshiba Satellite A40:
```
sudo echo "brightness:1" > /proc/acpi/toshiba/lcd

```

This command helped me a lot but now it does not work anymore:

> root@meander:~# sudo echo "brightness:1" > /proc/acpi/toshiba/lcd
bash: /proc/acpi/toshiba/lcd: No such file or directory

If you had any ideas about this, it would be great help to me.
Thanks again for this great howto.

---

### Post by xXx 0wn3d xXx on 2006-04-12
[QUOTE=xyz]Hi-first, thank you for all the work you put into this HowTo.
All seemed to have gone well until I ran:
```
sudo dpkg -i kernel-image-2.6.14*.deb
```


And I got this:

Can anyone help me out? Thanks in adv.
noob here!

Well it works now!
I opened "File Browser" as root and went to /usr/src and made " kernel-image-2.6.14_ck7_i386.deb" Executable! And this one too "linux-2.6.14.tar.bz2"
Then I ran:

```
 sudo dpkg -i kernel-image-2.6.14_ck7_i386.deb

```

AND NOT:
```
sudo dpkg -i kernel-image-2.6.14*.deb

```
N00b making his way...

I am visually impaired and,believe it or not, LCD's too bright for what's left of my eyes.
Kernel .386 and/or .686 was good to me because I could run this to lower brightness on my Toshiba Satellite A40:
```
sudo echo "brightness:1" > /proc/acpi/toshiba/lcd

```

This command helped me a lot but now it does not work anymore:



If you had any ideas about this, it would be great help to me.
Thanks again for this great howto.[/QUOTE]

The star (asterisk) means that you put the name of the image in there...he wrote the tutorial right.

---

### Post by xyz on 2006-04-13
Thanks MasterChief1234!I have lots to learn!Coming along,I guess,little by little.
It * is so obvious now.I was a 100% sure his tutorial was right.

---

### Post by Skarjoko on 2006-04-13
Does anyone know why my laptop keeps shutting down automatically, when its close to completing the last step? (making the .deb package)

---

### Post by xXx 0wn3d xXx on 2006-04-13
[QUOTE=Skarjoko]Does anyone know why my laptop keeps shutting down automatically, when its close to completing the last step? (making the .deb package)[/QUOTE]
Do you have it set to shutdown when battery reaches a certain point/a certain time of inactivity. Go under System > Administration > Screen Saver and then click on advanced and make sure everything is long enough.

---

### Post by xyz on 2006-04-14
This may or may not have anything to do with it but, while you're not 'on the move' all the time, you might not need your battery all the time. Here is how to take care of it. If you're rather broke like me, you'll find it interesting in the long run:
[http://www.batteryuniversity.com/parttwo-34.htm](http://www.batteryuniversity.com/parttwo-34.htm)

---

### Post by SomeoneWhoIsntMe on 2006-04-14
Compiled 2.6.17-rc1 with the ck patch, and it's much much faster. However, the display doesn't work when X is not running (boot, ctrl+alt+F*, and shutdown), which is bothersome because I need to install the NVIDIA drivers. Anyone got any ideas?

---

### Post by berserker on 2006-04-15
Applying the cks patch to the 2.6.16 kernel results in the system hanging during shutdown and the keyboard and mouse freezing.  I have no problems with a vanilla kernel (currently using 2.6.16.5).

EDIT:  This problem does not appear with the ck patch.

---

### Post by Skarjoko on 2006-04-15
[QUOTE=MasterChief1234]Do you have it set to shutdown when battery reaches a certain point/a certain time of inactivity. Go under System > Administration > Screen Saver and then click on advanced and make sure everything is long enough.[/QUOTE]

Thanks, will try compiling it again...hopefully it'll work this time. Will edit post once i'm done with results.

And xyz, thanks for that tip, i'll keep it bookmarked.

---

### Post by oofnik on 2006-04-17
I got mine compiled and it's running great. FINALLY fixed the problem I was having with the nvidia driver basically halting my system when X was closed. However, some new problems have cropped up (like it was unexpected, hah). My CDROM drives (one CD-RW, one DVD-RW) don't work, and nothing appears at boot up. Other minor problems are my USB drive doesn't want to automount, but that's ok, I can just use pmount. Kind of annoying though. I have been digging through my system and google searching for answers but I'm coming up empty handed..
Here's some relevant output from dmesg regarding the cdrom issue:
```

[4294671.792000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.792000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.800000] SCSI subsystem initialized
[4294671.803000] libata version 1.20 loaded.
[4294671.804000] ata_piix 0000:00:1f.2: version 1.05
[4294671.804000] ata_piix 0000:00:1f.2: combined mode detected (p=1, s=0)
[4294671.804000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 16
[4294671.804000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294671.804000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xF000 irq 14[4294672.013000] ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:207f
[4294672.013000] ata1: dev 0 ATA-6, max UDMA/133, 312581808 sectors: LBA48
[4294672.014000] ata1: dev 0 configured for UDMA/133
[4294672.014000] scsi0 : ata_piix
[4294672.014000]   Vendor: ATA       Model: ST3160023AS       Rev: 3.05
[4294672.014000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294672.014000] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xF008 irq 15[4294672.423000] ata2: dev 0 cfg 49:0b00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407
[4294672.423000] ata2: dev 0 ATAPI, max UDMA/33
[4294672.577000] ata2: dev 1 cfg 49:0b00 82:0210 83:1000 84:0000 85:0000 86:0000 87:0000 88:101f
[4294672.577000] ata2: dev 1 ATAPI, max UDMA/66
[4294672.578000] ata2: dev 0 configured for UDMA/33
[4294672.578000] ata2: dev 1 configured for UDMA/33
[4294672.578000] scsi1 : ata_piix
[COLOR="Red"][4294672.578000] ata2(0): WARNING: ATAPI is disabled, device ignored.
[4294672.578000] ata2(1): WARNING: ATAPI is disabled, device ignored.[/COLOR]
[4294672.585000] ide0: I/O resource 0x1F0-0x1F7 not free.
[4294672.585000] ide0: ports already in use, skipping probe
[4294672.585000] ide1: I/O resource 0x170-0x177 not free.
[4294672.585000] ide1: ports already in use, skipping probe
[4294672.589000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[4294672.589000] sda: Write Protect is off
[4294672.589000] sda: Mode Sense: 00 3a 00 00
[4294672.589000] SCSI device sda: drive cache: write back
[4294672.590000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[4294672.590000] sda: Write Protect is off
[4294672.590000] sda: Mode Sense: 00 3a 00 00
[4294672.590000] SCSI device sda: drive cache: write back
[4294672.590000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[4294672.634000] sd 0:0:0:0: Attached scsi disk sda

```
Those two lines saying ATAPI is disabled sound like the culprit.. but I have no idea what to do about that. Any help?

Second issue, with usplash not working, seems to be fairly common. But it really kind of bothers me. I don't know if my system froze up or if it's still booting. So I did some poking around, and found out there is no vesafb.ko module in /lib/modules/`uname -r`/kernel/drivers/ . Not in initrd either. The initrd folder doesn't even exist, unlike the rest of the kernels on my system. What's up with that? I compiled with the -initrd flag? 
I tried looking up how to compile kernel modules, so I could try to compile vesafb.ko myself, and it seemed a bit out there (although doable), so I don't know if that would even work or not. I don't like kernel panics much..

Well I'm new at all this kernel stuff, but I'm learning fast (or would like to think so :D). I'd like to fix this without having to recompile the whole kernel again, but if that's what needs to be done, so be it. I just like learning how to do things instead of just redoing it all differently.

---

### Post by xXx 0wn3d xXx on 2006-04-17
> **oofnik]I got mine compiled and it's running great. FINALLY fixed the problem I was having with the nvidia driver basically halting my system when X was closed. However, some new problems have cropped up (like it was unexpected, hah). My CDROM drives (one CD-RW, one DVD-RW) don't work, and nothing appears at boot up. Other minor problems are my USB drive doesn't want to automount, but that's ok, I can just use pmount. Kind of annoying though. I have been digging through my system and google searching for answers but I'm coming up empty handed..
Here's some relevant output from dmesg regarding the cdrom issue:
```

[4294671.792000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.792000] ide: Assuming 33MHz system bus speed for PIO modes said:**
>  SCSI subsystem initialized
[4294671.803000] libata version 1.20 loaded.
[4294671.804000] ata_piix 0000:00:1f.2: version 1.05
[4294671.804000] ata_piix 0000:00:1f.2: combined mode detected (p=1, s=0)
[4294671.804000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 16
[4294671.804000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294671.804000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xF000 irq 14[4294672.013000] ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:207f
[4294672.013000] ata1: dev 0 ATA-6, max UDMA/133, 312581808 sectors: LBA48
[4294672.014000] ata1: dev 0 configured for UDMA/133
[4294672.014000] scsi0 : ata_piix
[4294672.014000]   Vendor: ATA       Model: ST3160023AS       Rev: 3.05
[4294672.014000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294672.014000] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xF008 irq 15[4294672.423000] ata2: dev 0 cfg 49:0b00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407
[4294672.423000] ata2: dev 0 ATAPI, max UDMA/33
[4294672.577000] ata2: dev 1 cfg 49:0b00 82:0210 83:1000 84:0000 85:0000 86:0000 87:0000 88:101f
[4294672.577000] ata2: dev 1 ATAPI, max UDMA/66
[4294672.578000] ata2: dev 0 configured for UDMA/33
[4294672.578000] ata2: dev 1 configured for UDMA/33
[4294672.578000] scsi1 : ata_piix
[COLOR="Red"][4294672.578000] ata2(0): WARNING: ATAPI is disabled, device ignored.
[4294672.578000] ata2(1): WARNING: ATAPI is disabled, device ignored.[/COLOR]
[4294672.585000] ide0: I/O resource 0x1F0-0x1F7 not free.
[4294672.585000] ide0: ports already in use, skipping probe
[4294672.585000] ide1: I/O resource 0x170-0x177 not free.
[4294672.585000] ide1: ports already in use, skipping probe
[4294672.589000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[4294672.589000] sda: Write Protect is off
[4294672.589000] sda: Mode Sense: 00 3a 00 00
[4294672.589000] SCSI device sda: drive cache: write back
[4294672.590000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[4294672.590000] sda: Write Protect is off
[4294672.590000] sda: Mode Sense: 00 3a 00 00
[4294672.590000] SCSI device sda: drive cache: write back
[4294672.590000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[4294672.634000] sd 0:0:0:0: Attached scsi disk sda

```
Those two lines saying ATAPI is disabled sound like the culprit.. but I have no idea what to do about that. Any help?

Second issue, with usplash not working, seems to be fairly common. But it really kind of bothers me. I don't know if my system froze up or if it's still booting. So I did some poking around, and found out there is no vesafb.ko module in /lib/modules/`uname -r`/kernel/drivers/ . Not in initrd either. The initrd folder doesn't even exist, unlike the rest of the kernels on my system. What's up with that? I compiled with the -initrd flag? 
I tried looking up how to compile kernel modules, so I could try to compile vesafb.ko myself, and it seemed a bit out there (although doable), so I don't know if that would even work or not. I don't like kernel panics much..

Well I'm new at all this kernel stuff, but I'm learning fast (or would like to think so :D). I'd like to fix this without having to recompile the whole kernel again, but if that's what needs to be done, so be it. I just like learning how to do things instead of just redoing it all differently.

Maybe you could try compiling a newer kernel ? You compilied 2.6.14 while the newest version is 2.6.16.7. The problem you are having is most likely fixed.

---

### Post by oofnik on 2006-04-17
Oh actually it was version 2.6.16, which I patched with cks4. Maybe I should try to compile just the vanilla kernel first? So many configurations, so many patch sets, so much to learn.. ahh!

edit: Well I compiled another one... 2.6.16-ck5.. it's no better. And now mplayer, xmms, anything that requires the sound system I guess segfaults. Maybe it had to do with the OSS settings in the .config. Oh, and now usb-storage won't shut up in dmesg, it's eating cpu resources and repeating the same message over and over, many times a second:
```

[4297549.391000] usb-storage: queuecommand called
[4297549.391000] usb-storage: *** thread awakened.
[4297549.391000] usb-storage: Command TEST_UNIT_READY (6 bytes)
[4297549.392000] usb-storage:  00 40 00 00 00 00
[4297549.392000] usb-storage: Bulk Command S 0x43425355 T 0x3a4a L 0 F 0 Trg 0 LUN 2 CL 6
[4297549.392000] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[4297549.392000] usb-storage: Status code 0; transferred 31/31
[4297549.392000] usb-storage: -- transfer complete
[4297549.392000] usb-storage: Bulk command transfer result=0
[4297549.392000] usb-storage: Attempting to get CSW...
[4297549.392000] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[4297549.392000] usb-storage: Status code 0; transferred 13/13
[4297549.392000] usb-storage: -- transfer complete
[4297549.392000] usb-storage: Bulk status result = 0
[4297549.392000] usb-storage: Bulk Status S 0x53425355 T 0x3a4a R 0 Stat 0x1
[4297549.392000] usb-storage: -- transport indicates command failure
[4297549.392000] usb-storage: Issuing auto-REQUEST_SENSE
[4297549.392000] usb-storage: Bulk Command S 0x43425355 T 0x3a4b L 18 F 128 Trg 0 LUN 2 CL 6
[4297549.392000] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[4297549.392000] usb-storage: Status code 0; transferred 31/31
[4297549.392000] usb-storage: -- transfer complete
[4297549.392000] usb-storage: Bulk command transfer result=0
[4297549.392000] usb-storage: usb_stor_bulk_transfer_buf: xfer 18 bytes
[4297549.393000] usb-storage: Status code 0; transferred 18/18
[4297549.393000] usb-storage: -- transfer complete
[4297549.393000] usb-storage: Bulk data transfer result 0x0
[4297549.393000] usb-storage: Attempting to get CSW...
[4297549.393000] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[4297549.393000] usb-storage: Status code 0; transferred 13/13
[4297549.393000] usb-storage: -- transfer complete
[4297549.393000] usb-storage: Bulk status result = 0
[4297549.393000] usb-storage: Bulk Status S 0x53425355 T 0x3a4b R 0 Stat 0x0
[4297549.393000] usb-storage: -- Result from auto-sense is 0
[4297549.393000] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x0
[4297549.393000] usb-storage: Not Ready: Medium not present
[4297549.393000] usb-storage: scsi cmd done, result=0x2
[4297549.393000] usb-storage: *** thread sleeping.

```

.Here is my .config for the kernel, maybe someone can figure out where I screwed up somewhere in these 2000 lines:
[http://pastebin.com/666615](http://pastebin.com/666615)

Thanks for any help!

---

### Post by dolny on 2006-04-18
:( 

I'm trying to install 2.6.16 + ck6 patch but I get this:

```
root@lunatic:/usr/src# sudo bzcat /home/neurolunatic/Desktop/patch-2.6.16-ck6.bz2 | patch -pl
patch: **** strip count l is not a number
```

What the hell? Can anybody help me with this?

Edit: OK. I wrote l instead of 1.

---

### Post by dolny on 2006-04-18
DAMN :( I get an error after patching and starting to compile:

```
JFS filesystem support (JFS_FS) [M/n/y/?] m
  JFS POSIX Access Control Lists (JFS_POSIX_ACL) [Y/n/?] y
  JFS Security Labels (JFS_SECURITY) [Y/n/?] y
  JFS debugging (JFS_DEBUG) [N/y/?] n
  JFS statistics (JFS_STATISTICS) [Y/n/?] y
XFS filesystem support (XFS_FS) [M/n/y/?] m
  XFS Quota support (XFS_QUOTA) [Y/n/?] y
  XFS Security Label support (XFS_SECURITY) [Y/n/?] y
  XFS POSIX ACL support (XFS_POSIX_ACL) [Y/n/?] y
  XFS Realtime support (EXPERIMENTAL) (XFS_RT) [Y/n/?] y
OCFS2 file system support (EXPERIMENTAL) (OCFS2_FS) [N/m/y/?] n
Minix fs support (MINIX_FS) [M/n/y/?] m
ROM file system support (ROMFS_FS) [M/n/y/?] m
Inotify file change notification support (INOTIFY) [Y/n/?] y
Quota support (QUOTA) [Y/n/?] y
  Old quota format support (QFMT_V1) [M/n/y/?] m
  Quota format v2 support (QFMT_V2) [M/n/y/?] m
Kernel automounter support (AUTOFS_FS) [M/n/y/?] m
Kernel automounter version 4 support (also supports v3) (AUTOFS4_FS) [M/n/y/?] m
Filesystem in Userspace support (FUSE_FS) [M/n/y/?] m
*
* CD-ROM/DVD Filesystems
*
ISO 9660 CDROM file system support (ISO9660_FS) [M/n/y/?] m
  Microsoft Joliet CDROM extensions (JOLIET) [Y/n/?] y
  Transparent decompression extension (ZISOFS) [Y/n/?] y
UDF file system support (UDF_FS) [M/n/y/?] m
*
* DOS/FAT/NT Filesystems
*
MSDOS fs support (MSDOS_FS) [M/n/y/?] m
VFAT (Windows-95) fs support (VFAT_FS) [M/n/y/?] m
  Default codepage for FAT (FAT_DEFAULT_CODEPAGE) [437] 437
  Default iocharset for FAT (FAT_DEFAULT_IOCHARSET) [iso8859-1] iso8859-1
NTFS file system support (NTFS_FS) [M/n/y/?] m
  NTFS debugging support (NTFS_DEBUG) [N/y/?] n
  NTFS write support (NTFS_RW) [N/y/?] n
*
* Pseudo filesystems
*
/proc file system support (PROC_FS) [Y/n/?] y
  /proc/kcore support (PROC_KCORE) [Y/n] y
Virtual memory file system support (former shm fs) (TMPFS) [Y/n/?] y
HugeTLB file system support (HUGETLBFS) [N/y] n
Relayfs file system support (RELAYFS_FS) [M/n/y/?] m
Userspace-driven configuration filesystem (EXPERIMENTAL) (CONFIGFS_FS) [M/n/y/?] m
*
* Miscellaneous filesystems
*
ADFS file system support (EXPERIMENTAL) (ADFS_FS) [M/n/y/?] m
  ADFS write support (DANGEROUS) (ADFS_FS_RW) [N/y/?] n
Amiga FFS file system support (EXPERIMENTAL) (AFFS_FS) [M/n/y/?] m
Apple Macintosh file system support (EXPERIMENTAL) (HFS_FS) [M/n/y/?] m
Apple Extended HFS file system support (HFSPLUS_FS) [M/n/y/?] m
BeOS file system (BeFS) support (read only) (EXPERIMENTAL) (BEFS_FS) [M/n/y/?] m
  Debug BeFS (BEFS_DEBUG) [N/y/?] n
BFS file system support (EXPERIMENTAL) (BFS_FS) [M/n/y/?] m
EFS file system support (read only) (EXPERIMENTAL) (EFS_FS) [M/n/y/?] m
Journalling Flash File System (JFFS) support (JFFS_FS) [M/n/?] m
  JFFS debugging verbosity (0 = quiet, 3 = noisy) (JFFS_FS_VERBOSE) [0] 0
  JFFS stats available in /proc filesystem (JFFS_PROC_FS) [Y/n/?] y
Journalling Flash File System v2 (JFFS2) support (JFFS2_FS) [M/n/?] m
  JFFS2 debugging verbosity (0 = quiet, 2 = noisy) (JFFS2_FS_DEBUG) [0] 0
  JFFS2 write-buffering support (JFFS2_FS_WRITEBUFFER) [Y/n/?] y
  JFFS2 summary support (EXPERIMENTAL) (JFFS2_SUMMARY) [N/y/?] n
  Advanced compression options for JFFS2 (JFFS2_COMPRESSION_OPTIONS) [N/y/?] n
Compressed ROM file system support (cramfs) (CRAMFS) [Y/n/m/?] y
FreeVxFS file system support (VERITAS VxFS(TM) compatible) (VXFS_FS) [M/n/y/?] m
OS/2 HPFS file system support (HPFS_FS) [M/n/y/?] m
QNX4 file system support (read only) (QNX4FS_FS) [M/n/y/?] m
System V/Xenix/V7/Coherent file system support (SYSV_FS) [M/n/y/?] m
UFS file system support (read only) (UFS_FS) [M/n/y/?] m
*
* Network File Systems
*
NFS file system support (NFS_FS) [M/n/y/?] m
  Provide NFSv3 client support (NFS_V3) [Y/n/?] y
    Provide client support for the NFSv3 ACL protocol extension (NFS_V3_ACL) [N/y/?] n
  Provide NFSv4 client support (EXPERIMENTAL) (NFS_V4) [Y/n/?] y
  Allow direct I/O on NFS files (EXPERIMENTAL) (NFS_DIRECTIO) [Y/n/?] y
NFS server support (NFSD) [M/n/y/?] m
  Provide NFSv3 server support (NFSD_V3) [Y/n/?] y
    Provide server support for the NFSv3 ACL protocol extension (NFSD_V3_ACL) [N/y/?] n
    Provide NFSv4 server support (EXPERIMENTAL) (NFSD_V4) [Y/n/?] y
  Provide NFS server over TCP support (NFSD_TCP) [Y/?] y
Secure RPC: Kerberos V mechanism (EXPERIMENTAL) (RPCSEC_GSS_KRB5) [M/?] m
Secure RPC: SPKM3 mechanism (EXPERIMENTAL) (RPCSEC_GSS_SPKM3) [M/n/?] m
SMB file system support (to mount Windows shares etc.) (SMB_FS) [M/n/y/?] m
  Use a default NLS (SMB_NLS_DEFAULT) [N/y/?] n
CIFS support (advanced network filesystem for Samba, Window and other CIFS compliant servers) (CIFS) [M/n/y/?] m
  CIFS statistics (CIFS_STATS) [N/y/?] n
  CIFS extended attributes (CIFS_XATTR) [N/y/?] n
  CIFS Experimental Features (EXPERIMENTAL) (CIFS_EXPERIMENTAL) [N/y/?] n
NCP file system support (to mount NetWare volumes) (NCP_FS) [M/n/y/?] m
  Packet signatures (NCPFS_PACKET_SIGNING) [Y/n/?] y
  Proprietary file locking (NCPFS_IOCTL_LOCKING) [Y/n/?] y
  Clear remove/delete inhibit when needed (NCPFS_STRONG) [Y/n/?] y
  Use NFS namespace if available (NCPFS_NFS_NS) [Y/n/?] y
  Use LONG (OS/2) namespace if available (NCPFS_OS2_NS) [Y/n/?] y
  Lowercase DOS filenames (NCPFS_SMALLDOS) [N/y/?] n
  Use Native Language Support (NCPFS_NLS) [Y/n/?] y
  Enable symbolic links and execute flags (NCPFS_EXTRAS) [Y/n/?] y
Coda file system support (advanced network fs) (CODA_FS) [M/n/y/?] m
  Use 96-bit Coda file identifiers (CODA_FS_OLD_API) [N/y/?] n
Andrew File System support (AFS) (Experimental) (AFS_FS) [M/n/y/?] m
Plan 9 Resource Sharing Support (9P2000) (Experimental) (9P_FS) [M/n/y/?] m
*
* Partition Types
*
Advanced partition selection (PARTITION_ADVANCED) [Y/n/?] y
  Acorn partition support (ACORN_PARTITION) [Y/n/?] y
    Cumana partition support (ACORN_PARTITION_CUMANA) [N/y/?] n
    EESOX partition support (ACORN_PARTITION_EESOX) [N/y] n
    ICS partition support (ACORN_PARTITION_ICS) [Y/n/?] y
    Native filecore partition support (ACORN_PARTITION_ADFS) [N/y/?] n
    PowerTec partition support (ACORN_PARTITION_POWERTEC) [N/y/?] n
    RISCiX partition support (ACORN_PARTITION_RISCIX) [Y/n/?] y
  Alpha OSF partition support (OSF_PARTITION) [Y/n/?] y
  Amiga partition table support (AMIGA_PARTITION) [Y/n/?] y
  Atari partition table support (ATARI_PARTITION) [Y/n/?] y
  Macintosh partition map support (MAC_PARTITION) [Y/n/?] y
  PC BIOS (MSDOS partition tables) support (MSDOS_PARTITION) [Y/n/?] y
    BSD disklabel (FreeBSD partition tables) support (BSD_DISKLABEL) [Y/n/?] y
    Minix subpartition support (MINIX_SUBPARTITION) [Y/n/?] y
    Solaris (x86) partition table support (SOLARIS_X86_PARTITION) [Y/n/?] y
    Unixware slices support (UNIXWARE_DISKLABEL) [Y/n/?] y
  Windows Logical Disk Manager (Dynamic Disk) support (LDM_PARTITION) [Y/n/?] y
    Windows LDM extra logging (LDM_DEBUG) [N/y/?] n
  SGI partition support (SGI_PARTITION) [Y/n/?] y
  Ultrix partition table support (ULTRIX_PARTITION) [Y/n/?] y
  Sun partition tables support (SUN_PARTITION) [Y/n/?] y
  Karma Partition support (KARMA_PARTITION) [N/y/?] n
  EFI GUID Partition support (EFI_PARTITION) [Y/n/?] y
*
* Native Language Support
*
Base native language support (NLS) [Y/m/?] y
  Default NLS Option (NLS_DEFAULT) [cp437] cp437
  Codepage 437 (United States, Canada) (NLS_CODEPAGE_437) [M/n/y/?] m
  Codepage 737 (Greek) (NLS_CODEPAGE_737) [M/n/y/?] m
  Codepage 775 (Baltic Rim) (NLS_CODEPAGE_775) [M/n/y/?] m
  Codepage 850 (Europe) (NLS_CODEPAGE_850) [M/n/y/?] m
  Codepage 852 (Central/Eastern Europe) (NLS_CODEPAGE_852) [M/n/y/?] m
  Codepage 855 (Cyrillic) (NLS_CODEPAGE_855) [M/n/y/?] m
  Codepage 857 (Turkish) (NLS_CODEPAGE_857) [M/n/y/?] m
  Codepage 860 (Portuguese) (NLS_CODEPAGE_860) [M/n/y/?] m
  Codepage 861 (Icelandic) (NLS_CODEPAGE_861) [M/n/y/?] m
  Codepage 862 (Hebrew) (NLS_CODEPAGE_862) [M/n/y/?] m
  Codepage 863 (Canadian French) (NLS_CODEPAGE_863) [M/n/y/?] m
  Codepage 864 (Arabic) (NLS_CODEPAGE_864) [M/n/y/?] m
  Codepage 865 (Norwegian, Danish) (NLS_CODEPAGE_865) [M/n/y/?] m
  Codepage 866 (Cyrillic/Russian) (NLS_CODEPAGE_866) [M/n/y/?] m
  Codepage 869 (Greek) (NLS_CODEPAGE_869) [M/n/y/?] m
  Simplified Chinese charset (CP936, GB2312) (NLS_CODEPAGE_936) [M/n/y/?] m
  Traditional Chinese charset (Big5) (NLS_CODEPAGE_950) [M/n/y/?] m
  Japanese charsets (Shift-JIS, EUC-JP) (NLS_CODEPAGE_932) [M/n/y/?] m
  Korean charset (CP949, EUC-KR) (NLS_CODEPAGE_949) [M/n/y/?] m
  Thai charset (CP874, TIS-620) (NLS_CODEPAGE_874) [M/n/y/?] m
  Hebrew charsets (ISO-8859-8, CP1255) (NLS_ISO8859_8) [M/n/y/?] m
  Windows CP1250 (Slavic/Central European Languages) (NLS_CODEPAGE_1250) [M/n/y/?] m
  Windows CP1251 (Bulgarian, Belarusian) (NLS_CODEPAGE_1251) [M/n/y/?] m
  ASCII (United States) (NLS_ASCII) [M/n/y/?] m
  NLS ISO 8859-1  (Latin 1; Western European Languages) (NLS_ISO8859_1) [M/n/y/?] m
  NLS ISO 8859-2  (Latin 2; Slavic/Central European Languages) (NLS_ISO8859_2) [M/n/y/?] m
  NLS ISO 8859-3  (Latin 3; Esperanto, Galician, Maltese, Turkish) (NLS_ISO8859_3) [M/n/y/?] m
  NLS ISO 8859-4  (Latin 4; old Baltic charset) (NLS_ISO8859_4) [M/n/y/?] m
  NLS ISO 8859-5  (Cyrillic) (NLS_ISO8859_5) [M/n/y/?] m
  NLS ISO 8859-6  (Arabic) (NLS_ISO8859_6) [M/n/y/?] m
  NLS ISO 8859-7  (Modern Greek) (NLS_ISO8859_7) [M/n/y/?] m
  NLS ISO 8859-9  (Latin 5; Turkish) (NLS_ISO8859_9) [M/n/y/?] m
  NLS ISO 8859-13 (Latin 7; Baltic) (NLS_ISO8859_13) [M/n/y/?] m
  NLS ISO 8859-14 (Latin 8; Celtic) (NLS_ISO8859_14) [M/n/y/?] m
  NLS ISO 8859-15 (Latin 9; Western European Languages with Euro) (NLS_ISO8859_15) [M/n/y/?] m
  NLS KOI8-R (Russian) (NLS_KOI8_R) [M/n/y/?] m
  NLS KOI8-U/RU (Ukrainian, Belarusian) (NLS_KOI8_U) [M/n/y/?] m
  NLS UTF8 (NLS_UTF8) [M/y/?] m
*
* Instrumentation Support
*
Profiling support (EXPERIMENTAL) (PROFILING) [Y/n/?] y
  OProfile system profiling (EXPERIMENTAL) (OPROFILE) [M/n/y/?] m
Kprobes (EXPERIMENTAL) (KPROBES) [N/y/?] n
*
* Kernel hacking
*
Show timing information on printks (PRINTK_TIME) [Y/n/?] y
Magic SysRq key (MAGIC_SYSRQ) [Y/n/?] y
Kernel debugging (DEBUG_KERNEL) [N/y/?] n
*
* Security options
*
Enable access key retention support (KEYS) [Y/n/?] y
  Enable the /proc/keys file by which all keys may be viewed (KEYS_DEBUG_PROC_KEYS) [N/y/?] n
Enable different security models (SECURITY) [Y/n/?] y
  Socket and Networking Security Hooks (SECURITY_NETWORK) [Y/n/?] y
    XFRM (IPSec) Networking Security Hooks (SECURITY_NETWORK_XFRM) [N/y/?] n
  Default Linux Capabilities (SECURITY_CAPABILITIES) [M/n/y/?] m
  Root Plug Support (SECURITY_ROOTPLUG) [M/n/?] m
  BSD Secure Levels (SECURITY_SECLVL) [M/n/y/?] m
NSA SELinux Support (SECURITY_SELINUX) [Y/n/?] y
  NSA SELinux boot parameter (SECURITY_SELINUX_BOOTPARAM) [Y/n/?] y
    NSA SELinux boot parameter default value (SECURITY_SELINUX_BOOTPARAM_VALUE) [0] 0
  NSA SELinux runtime disable (SECURITY_SELINUX_DISABLE) [Y/n/?] y
  NSA SELinux Development Support (SECURITY_SELINUX_DEVELOP) [Y/n/?] y
  NSA SELinux AVC Statistics (SECURITY_SELINUX_AVC_STATS) [Y/n/?] y
  NSA SELinux checkreqprot default value (SECURITY_SELINUX_CHECKREQPROT_VALUE) [1] 1
*
* Cryptographic options
*
Cryptographic API (CRYPTO) [Y/?] y
  HMAC support (CRYPTO_HMAC) [Y/?] y
  Null algorithms (CRYPTO_NULL) [M/n/y/?] m
  MD4 digest algorithm (CRYPTO_MD4) [M/n/y/?] m
  MD5 digest algorithm (CRYPTO_MD5) [Y/?] y
  SHA1 digest algorithm (CRYPTO_SHA1) [M/y/?] m
  SHA256 digest algorithm (CRYPTO_SHA256) [M/n/y/?] m
  SHA384 and SHA512 digest algorithms (CRYPTO_SHA512) [M/n/y/?] m
  Whirlpool digest algorithms (CRYPTO_WP512) [M/n/y/?] m
  Tiger digest algorithms (CRYPTO_TGR192) [M/n/y/?] m
  DES and Triple DES EDE cipher algorithms (CRYPTO_DES) [M/y/?] m
  Blowfish cipher algorithm (CRYPTO_BLOWFISH) [M/n/y/?] m
  Twofish cipher algorithm (CRYPTO_TWOFISH) [M/n/y/?] m
  Serpent cipher algorithm (CRYPTO_SERPENT) [M/n/y/?] m
  AES cipher algorithms (CRYPTO_AES) [M/y/?] m
  AES cipher algorithms (i586) (CRYPTO_AES_586) [M/n/y/?] m
  CAST5 (CAST-128) cipher algorithm (CRYPTO_CAST5) [M/n/y/?] m
  CAST6 (CAST-256) cipher algorithm (CRYPTO_CAST6) [M/n/y/?] m
  TEA, XTEA and XETA cipher algorithms (CRYPTO_TEA) [M/n/y/?] m
  ARC4 cipher algorithm (CRYPTO_ARC4) [M/y/?] m
  Khazad cipher algorithm (CRYPTO_KHAZAD) [M/n/y/?] m
  Anubis cipher algorithm (CRYPTO_ANUBIS) [M/n/y/?] m
  Deflate compression algorithm (CRYPTO_DEFLATE) [M/y/?] m
  Michael MIC keyed digest algorithm (CRYPTO_MICHAEL_MIC) [M/y/?] m
  CRC32c CRC algorithm (CRYPTO_CRC32C) [M/y/?] m
  Testing module (CRYPTO_TEST) [M/n/y/?] m
*
* Hardware crypto devices
*
Support for VIA PadLock ACE (CRYPTO_DEV_PADLOCK) [M/n/y/?] m
  Support for AES in VIA PadLock (CRYPTO_DEV_PADLOCK_AES) [Y/n/?] y
*
* Library routines
*
CRC-CCITT functions (CRC_CCITT) [M/y/?] m
CRC16 functions (CRC16) [M/y/?] m
CRC32 functions (CRC32) [Y/?] y
CRC32c (Castagnoli, et al) Cyclic Redundancy-Check (LIBCRC32C) [M/y/?] m
make[1]: Opuszczenie katalogu `/usr/src/linux-2.6.16cK6'
/usr/bin/make    \
                                ARCH=i386 prepare
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-2.6.16cK6'
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  SYMLINK include/asm -> include/asm-i386
  SPLIT   include/linux/autoconf.h -> include/config/*
  CC      arch/i386/kernel/asm-offsets.s
  GEN     include/asm-i386/asm-offsets.h
make[1]: Opuszczenie katalogu `/usr/src/linux-2.6.16cK6'
echo done >  stamp-kernel-configure
echo done >  stamp-configure
if [ -f include/linux/version.h ]; then                                          \
             uts_ver=$(grep 'define UTS_RELEASE' include/linux/version.h | perl -nle  'm/^\s*\#define\s+UTS_RELEASE\s+("?)(\S+)\1/g && print $2;'); \
            if [ "X$uts_ver" != "X2.6.16-ck6" ]; then              \
                echo "The UTS Release version in include/linux/version.h";                \
                echo "     \"$uts_ver\" ";                                               \
                echo "does not match current version " ;                                  \
                echo "     \"2.6.16-ck6\" " ;                                    \
                echo "Reconfiguring." ;                                                   \
                touch Makefile;                                                           \
             fi;                                                                          \
        fi
test -f stamp-configure || /usr/bin/make -f /usr/share/kernel-package/rules configure
/usr/bin/make    ARCH=i386 \
                             bzImage
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-2.6.16cK6'
  CHK     include/linux/version.h
  HOSTCC  scripts/genksyms/genksyms.o
  SHIPPED scripts/genksyms/lex.c
  SHIPPED scripts/genksyms/parse.h
  SHIPPED scripts/genksyms/keywords.c
  HOSTCC  scripts/genksyms/lex.o
  SHIPPED scripts/genksyms/parse.c
  HOSTCC  scripts/genksyms/parse.o
  HOSTLD  scripts/genksyms/genksyms
  CC      scripts/mod/empty.o
  HOSTCC  scripts/mod/mk_elfconfig
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
  HOSTCC  scripts/kallsyms
  HOSTCC  scripts/conmakehash
  CC      init/main.o
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  CC      init/do_mounts.o
  CC      init/do_mounts_rd.o
  CC      init/do_mounts_initrd.o
  LD      init/mounts.o
  CC      init/initramfs.o
  CC      init/calibrate.o
  LD      init/built-in.o
  HOSTCC  usr/gen_init_cpio
  CHK     usr/initramfs_list
  UPD     usr/initramfs_list
  CPIO    usr/initramfs_data.cpio
  GZIP    usr/initramfs_data.cpio.gz
  AS      usr/initramfs_data.o
  LD      usr/built-in.o
  CC      arch/i386/kernel/process.o
  CC      arch/i386/kernel/semaphore.o
  CC      arch/i386/kernel/signal.o
  AS      arch/i386/kernel/entry.o
  CC      arch/i386/kernel/traps.o
  CC      arch/i386/kernel/irq.o
  CC      arch/i386/kernel/ptrace.o
  CC      arch/i386/kernel/time.o
  CC      arch/i386/kernel/ioport.o
  CC      arch/i386/kernel/ldt.o
  CC      arch/i386/kernel/setup.o
  CC      arch/i386/kernel/i8259.o
  CC      arch/i386/kernel/sys_i386.o
  CC      arch/i386/kernel/pci-dma.o
  CC      arch/i386/kernel/i386_ksyms.o
  CC      arch/i386/kernel/i387.o
  CC      arch/i386/kernel/dmi_scan.o
  CC      arch/i386/kernel/bootflag.o
  CC      arch/i386/kernel/quirks.o
  CC      arch/i386/kernel/i8237.o
  CC      arch/i386/kernel/topology.o
  CC      arch/i386/kernel/acpi/boot.o
  CC      arch/i386/kernel/acpi/earlyquirk.o
  CC      arch/i386/kernel/acpi/sleep.o
  AS      arch/i386/kernel/acpi/wakeup.o
  CC      arch/i386/kernel/acpi/cstate.o
  CC      arch/i386/kernel/acpi/processor.o
  LD      arch/i386/kernel/acpi/built-in.o
  CC      arch/i386/kernel/cpu/common.o
  CC      arch/i386/kernel/cpu/proc.o
  CC      arch/i386/kernel/cpu/amd.o
  CC      arch/i386/kernel/cpu/cyrix.o
  CC      arch/i386/kernel/cpu/centaur.o
  CC      arch/i386/kernel/cpu/transmeta.o
arch/i386/kernel/cpu/transmeta.c: In function ‘init_transmeta’:
arch/i386/kernel/cpu/transmeta.c:12: warning: ‘cpu_freq’ may be used uninitialized in this function
  CC      arch/i386/kernel/cpu/intel.o
  CC      arch/i386/kernel/cpu/intel_cacheinfo.o
  CC      arch/i386/kernel/cpu/rise.o
  CC      arch/i386/kernel/cpu/nexgen.o
  CC      arch/i386/kernel/cpu/umc.o
  LD      arch/i386/kernel/cpu/cpufreq/built-in.o
  CC      arch/i386/kernel/cpu/mtrr/main.o
  CC      arch/i386/kernel/cpu/mtrr/if.o
  CC      arch/i386/kernel/cpu/mtrr/generic.o
  CC      arch/i386/kernel/cpu/mtrr/state.o
  CC      arch/i386/kernel/cpu/mtrr/amd.o
  CC      arch/i386/kernel/cpu/mtrr/cyrix.o
  CC      arch/i386/kernel/cpu/mtrr/centaur.o
  LD      arch/i386/kernel/cpu/mtrr/built-in.o
  LD      arch/i386/kernel/cpu/built-in.o
  CC      arch/i386/kernel/timers/timer.o
  CC      arch/i386/kernel/timers/timer_none.o
  CC      arch/i386/kernel/timers/timer_tsc.o
  CC      arch/i386/kernel/timers/timer_pit.o
  CC      arch/i386/kernel/timers/common.o
  CC      arch/i386/kernel/timers/timer_hpet.o
  CC      arch/i386/kernel/timers/timer_pm.o
  LD      arch/i386/kernel/timers/built-in.o
  CC      arch/i386/kernel/reboot.o
  CC      arch/i386/kernel/mca.o
  CC      arch/i386/kernel/mpparse.o
  CC      arch/i386/kernel/apic.o
  CC      arch/i386/kernel/nmi.o
arch/i386/kernel/nmi.c: In function ‘check_nmi_watchdog’:
arch/i386/kernel/nmi.c:139: warning: statement with no effect
  CC      arch/i386/kernel/io_apic.o
  CC      arch/i386/kernel/reboot_fixups.o
  CC      arch/i386/kernel/module.o
  CC      arch/i386/kernel/sysenter.o
  LDS     arch/i386/kernel/vsyscall.lds
  AS      arch/i386/kernel/vsyscall-int80.o
  AS      arch/i386/kernel/vsyscall-note.o
  SYSCALL arch/i386/kernel/vsyscall-int80.so
  AS      arch/i386/kernel/vsyscall-sysenter.o
  SYSCALL arch/i386/kernel/vsyscall-sysenter.so
  AS      arch/i386/kernel/vsyscall.o
  CC      arch/i386/kernel/time_hpet.o
  CC      arch/i386/kernel/efi.o
arch/i386/kernel/efi.c: In function ‘efi_call_phys_epilog’:
arch/i386/kernel/efi.c:118: warning: assignment makes integer from pointer without a cast
arch/i386/kernel/efi.c: In function ‘efi_memmap_walk’:
arch/i386/kernel/efi.c:275: warning: ‘prev.start’ may be used uninitialized in this function
arch/i386/kernel/efi.c:275: warning: ‘prev.end’ may be used uninitialized in this function
  AS      arch/i386/kernel/efi_stub.o
  CC      arch/i386/kernel/doublefault.o
  CC      arch/i386/kernel/vm86.o
  CC      arch/i386/kernel/early_printk.o
  SYSCALL arch/i386/kernel/vsyscall-syms.o
  LD      arch/i386/kernel/built-in.o
  AS      arch/i386/kernel/head.o
  CC      arch/i386/kernel/init_task.o
  LDS     arch/i386/kernel/vmlinux.lds
  CC      arch/i386/mm/init.o
  CC      arch/i386/mm/pgtable.o
  CC      arch/i386/mm/fault.o
  CC      arch/i386/mm/ioremap.o
  CC      arch/i386/mm/extable.o
  CC      arch/i386/mm/pageattr.o
  CC      arch/i386/mm/mmap.o
  CC      arch/i386/mm/boot_ioremap.o
  LD      arch/i386/mm/built-in.o
  CC      arch/i386/mach-default/setup.o
  LD      arch/i386/mach-default/built-in.o
  LD      arch/i386/crypto/built-in.o
  CC      kernel/sched.o
  CC      kernel/fork.o
  CC      kernel/exec_domain.o
  CC      kernel/panic.o
  CC      kernel/printk.o
  CC      kernel/profile.o
  CC      kernel/exit.o
  CC      kernel/itimer.o
  CC      kernel/time.o
  CC      kernel/softirq.o
  CC      kernel/resource.o
  CC      kernel/sysctl.o
  CC      kernel/capability.o
  CC      kernel/ptrace.o
  CC      kernel/timer.o
  CC      kernel/user.o
  CC      kernel/signal.o
  CC      kernel/sys.o
  CC      kernel/kmod.o
  CC      kernel/workqueue.o
  CC      kernel/pid.o
  CC      kernel/rcupdate.o
  CC      kernel/extable.o
  CC      kernel/params.o
  CC      kernel/posix-timers.o
  CC      kernel/kthread.o
  CC      kernel/wait.o
  CC      kernel/kfifo.o
  CC      kernel/sys_ni.o
  CC      kernel/posix-cpu-timers.o
  CC      kernel/mutex.o
  CC      kernel/hrtimer.o
  CC      kernel/futex.o
  CC      kernel/dma.o
  CC      kernel/uid16.o
  CC      kernel/module.o
  CC      kernel/kallsyms.o
  CC      kernel/irq/handle.o
  CC      kernel/irq/manage.o
  CC      kernel/irq/spurious.o
  CC      kernel/irq/autoprobe.o
  CC      kernel/irq/proc.o
  LD      kernel/irq/built-in.o
  CC      kernel/power/main.o
  CC      kernel/power/process.o
  CC      kernel/power/console.o
  CC      kernel/power/pm.o
kernel/power/pm.c:259: warning: ‘pm_register’ is deprecated (declared at kernel/power/pm.c:63)
kernel/power/pm.c:260: warning: ‘pm_unregister’ is deprecated (declared at kernel/power/pm.c:86)
kernel/power/pm.c:261: warning: ‘pm_unregister_all’ is deprecated (declared at kernel/power/pm.c:115)
kernel/power/pm.c:262: warning: ‘pm_send_all’ is deprecated (declared at kernel/power/pm.c:234)
  CC      kernel/power/swsusp.o
  CC      kernel/power/disk.o
  CC      kernel/power/snapshot.o
  CC      kernel/power/poweroff.o
  LD      kernel/power/built-in.o
  CC      kernel/acct.o
  CC      kernel/audit.o
kernel/audit.c: In function ‘audit_log_start’:
kernel/audit.c:656: warning: ‘t.tv_nsec’ may be used uninitialized in this function
kernel/audit.c:656: warning: ‘t.tv_sec’ may be used uninitialized in this function
kernel/audit.c:657: warning: ‘serial’ may be used uninitialized in this function
  CC      kernel/ksysfs.o
  CC      kernel/seccomp.o
  LD      kernel/built-in.o
  CC      mm/bootmem.o
  CC      mm/filemap.o
  CC      mm/mempool.o
  CC      mm/oom_kill.o
  CC      mm/fadvise.o
  CC      mm/page_alloc.o
  CC      mm/page-writeback.o
  CC      mm/pdflush.o
  CC      mm/readahead.o
  CC      mm/swap.o
In file included from mm/swap.c:26:
include/linux/mm_inline.h:25: error: redefinition of ‘add_page_to_inactive_list_tail’
include/linux/mm_inline.h:18: error: previous definition of ‘add_page_to_inactive_list_tail’ was here
make[2]: *** [mm/swap.o] B&#322;&#261;d 1
make[1]: *** [mm] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/usr/src/linux-2.6.16cK6'
make: *** [stamp-build] B&#322;&#261;d 2

```

Please help :(

---

### Post by oofnik on 2006-04-18
dolny, what compiler are you using?

---

### Post by dolny on 2006-04-18
How can I check that in details :) ?

---

### Post by dolny on 2006-04-18
How can I check that in details :) ?
gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu4)

---

### Post by nismohasan on 2006-06-22
if one wanted to install say the latest kernel (linux-2.6.17.1)

which CK performance patch would he use? i noticed theres 2 (patch-2.6.17-ck1.bz2 & patch-2.6.17-cks1.bz2) and it got me kind of confused?

help would be appreciated. 

cheers

---

### Post by xXx 0wn3d xXx on 2006-06-22
[QUOTE=nismohasan]if one wanted to install say the latest kernel (linux-2.6.17.1)

which CK performance patch would he use? i noticed theres 2 (patch-2.6.17-ck1.bz2 & patch-2.6.17-cks1.bz2) and it got me kind of confused?

help would be appreciated. 

cheers[/QUOTE]
You should use the regular ck patch. The cks is for servers.

---

### Post by Brando569 on 2006-06-24
under the latest patchset whats the difference between 2.6.17-ck1-broken-out.tar.bz2 and patch-2.6.17-ck1.bz2?

---

### Post by galactus51 on 2006-07-23
Ok Guys, very good tutorial. Really great. The compilation works fine, the system is very fast. But I'm having two problems (untill now): I can't access my USB card and my other two HDs. Ubuntu says that they're already mounted or busy.

I'm sure that I have not changed anything about USB and file systems supports. Any ideas?

I'm using kernel 2.6.17.6 .

---

### Post by madchicken on 2006-07-24
You have, like me and many others here, the pmount problem. No way for me to resolve it. Keep your "old" 2.6.15 kernel from dapper repository.

Bye

---

### Post by galactus51 on 2006-07-24
> **madchicken said:**
> You have, like me and many others here, the pmount problem. No way for me to resolve it. Keep your "old" 2.6.15 kernel from dapper repository.

Bye


So, pmount doesn't work with kernel 2.6.17?

---

### Post by madchicken on 2006-07-24
> **galactus51 said:**
> So, pmount doesn't work with kernel 2.6.17?

No, it isn't a kernel problem, it's a problem with the ubuntu patches: the vanilla kernel 2.6.15 that you can download from the repository is patched by the ubuntu team (try to download the source package, you will see the kernel and a set of patches). To use a 2.6.17 kernel you need to modify these patches to run against the new kernel, otherwise the pmount on ubuntu will not work for you.

Bye

---

### Post by konan on 2006-08-20
Hello!

I followd the howto and sucessfuly compiled latest stable kernel, but at boot I always end up with error;
at boot time, kernel reports -> 
> WARNING: Could not open directory /lib/modules/2.6.17.9 No such file or directory
FATAL: Could not open /lib/modules/2.6.17.9/modules.dep.temp for writing: No such file or directory

System then boots up, but I cant modprobe any of the modules in /lib/modules
> 
modprobe /lib/modules/2.6.17.9/kernel/crypto/des.ko
FATAL: Module /lib/modules/2.6.17.9/kernel/crypto/des.ko not found

If I use modinfo /lib/modules/2.6.17.9/kernel/crypto/des.ko it prints info about module.

Don't know what else to do!!

Help appriciated... :)

---

### Post by bcalder01 on 2006-08-20
Gaah! This is really frustrating!

I decided to compile a new kernel following the procedures in this thread. I've downloaded & patched a vanilla 2.6.15 kernel. When I recieved the following error, I tried it with the vanilla 2.6.17 kernel, with the same result. Using either **make xconfig** or make **menuconfig**, I am getting the same error:

================================================== ================
bcalder@stitch:/usr/src/linux$ sudo make menuconfig
Password:
HOSTCC scripts/basic/fixdep
In file included from /usr/include/sys/socket.h:35,
from /usr/include/netinet/in.h:24,
from /usr/include/arpa/inet.h:23,
from scripts/basic/fixdep.c:115:
/usr/include/bits/socket.h:304:24: error: asm/socket.h: No such file or directory
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2

================================================== ================

I'm going nuts, because I don't know what I'm looking for!! **linuxinfo** shows I'm running the latest glibc, 2.3.6 (which I thought might be the prob), which makes sense since I've dist-upgraded. Any help appreciated!!

---

### Post by VMC on 2008-09-07
<removed>

---

### Post by RubenGonc on 2008-09-09
Wow, now he will be good to compile his kernel. After 2 years. :)

---

