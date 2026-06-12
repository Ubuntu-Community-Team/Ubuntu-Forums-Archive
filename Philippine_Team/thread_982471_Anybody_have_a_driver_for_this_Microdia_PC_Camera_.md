---
title: "Anybody have a driver for this Microdia PC Camera (SN9C201) web camera?"
date: 2008-11-14
forum: Philippine Team
---

### Post by killer_d76 on 2008-11-14
This is my built-in camera on my laptop that is working fine on Window$ but not on Ubuntu!.. anybody have an idea where i could get a driver for this one?!.. TIA! :guitar:

---

### Post by wersdaluv on 2008-11-14
> **killer_d76 said:**
> This is my built-in camera on my laptop that is working fine on Window$ but not on Ubuntu!.. anybody have an idea where i could get a driver for this one?!.. TIA! :guitar:

Pa-post ng output ng ```
lsusb
```. Pag nakita mo yung line don ng webcam mo, you might want to google that.

---

### Post by killer_d76 on 2008-11-14
thanks for the quick reply bro, sige i'll post it later.. dito pa kasi ako sa work ngayon eh hehehe.. but i did tried googling around for a couple of hours last night, downloaded and tested a few .deb but still no luck.

i found this one [http://www.linuxsoft.cz/en/sw_detail.php?id_item=8781]("http://www.linuxsoft.cz/en/sw_detail.php?id_item=8781") just now perhaps i'll give this one a try!

---

### Post by wersdaluv on 2008-11-14
> **killer_d76 said:**
> thanks for the quick reply bro, sige i'll post it later.. dito pa kasi ako sa work ngayon eh hehehe.. but i did tried googling around for a couple of hours last night, downloaded and tested a few .deb but still no luck.

i found this one [http://www.linuxsoft.cz/en/sw_detail.php?id_item=8781]("http://www.linuxsoft.cz/en/sw_detail.php?id_item=8781") just now perhaps i'll give this one a try!
Yeah. Important na alam mo yung lsusb mo para alam mo yung parang "generic name" ng webcam mo. With that name, mas madali mong mahahanap ang driver.

---

### Post by killer_d76 on 2008-11-15
okey here's what i got with lsusb..

> 
Bus 005 Device 004: ID 0b27:0165 Ritek Corp. 
[COLOR="Red"]Bus 005 Device 003: ID 0c45:624f Microdia PC Camera (SN9C201)[/COLOR]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by loell on 2008-11-15
this is for mandriva, but should work on ubuntu.

[http://blog.zerodogg.org/2008/04/27/microdia-0c45624f-webcam-on-linux/]("http://blog.zerodogg.org/2008/04/27/microdia-0c45624f-webcam-on-linux/")

you might be needing these packages before compiling,

```
sudo apt-get install git ubuntu-dev
```

---

### Post by killer_d76 on 2008-11-15
thanks mga bossing!.. i'll just add it up here for others to see na din! ;)

> 
git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
cd microdia
make
sudo insmod ./microdia.ko

will this work on 32 and 64 bit as well?

---

### Post by killer_d76 on 2008-11-16
got some error..

> 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: ctags: Command not found
make: *** [ctags] Error 127
arvin@arvin-laptop:~/microdia$ sudo insmod ./microdia.ko
insmod: error inserting './microdia.ko': -1 Unknown symbol in module

---

### Post by loell on 2008-11-16
hmm, maybe install

**exuberant-ctags**  then redo the compilation.

---

### Post by killer_d76 on 2008-11-16
still getting some errors..
here's what happened when i typed: 
```
sudo apt-get install git ubuntu-dev
```

> arvin@arvin-laptop:~$ sudo apt-get install git ubuntu-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version.
E: Couldn't find package ubuntu-dev


so i did ```
sudo apt-get install git
```

install exuberant-ctags

```
sudo apt-get install exuberant-ctags
```

still got some errors.. :(

---

### Post by loell on 2008-11-16
oops, sorry, it is supposed to be **ubuntu-dev-tools** not ubuntu-dev.

install that and do the compiling, the ctag error might go away now this time.

---

### Post by killer_d76 on 2008-11-16
redid the whole thing..
```
sudo apt-get install ubuntu-dev-tools
```

then 

```
sudo apt-get install exuberant-ctags
```

tapos..

git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)

cd microdia

make

sudo insmod ./microdia.ko 

here's the error now.

> arvin@arvin-laptop:~/microdia$ sudo insmod ./microdia.ko
insmod: error inserting './microdia.ko': -1 Unknown symbol in module


---

### Post by loell on 2008-11-16
from the blog article, there was a specific comment for 8.04 x86_64

> 
On my x86_64 Ubuntu 8.04 system I had to do the following:

$ sudo modprobe videodev
$ sudo modprobe compat_ioctl32
$ sudo insmod ./microdia.ko

The compat_ioctl32 module is not needed on a 32-bit system.

An alternative is to install the microdia module into the kernel module path “manually” (because there is no “make install” yet) as follows:

$ sudo install -d /lib/modules/`uname -r`/misc
$ sudo install microdia.ko /lib/modules/`uname -r`/misc
$ sudo depmod -a

Then to load the module all you need to do is:

$ sudo modprobe microdia

In fact the module should then be autoloaded when the webcam is plugged in, or if the webcam is built-in, following a reboot.


try those steps.

---

### Post by killer_d76 on 2008-11-16
thanks loel, i'll try those steps later.. hehehe papasok na kasi ako eh.. di pa'ko naliligo hehehe... :)

---

### Post by killer_d76 on 2008-11-17
still getting errors here

> arvin@arvin-laptop:~$ sudo modprobe videodev
[sudo] password for arvin: 
arvin@arvin-laptop:~$ sudo insmod ./microdia.ko
insmod: can't read './microdia.ko': No such file or directory
arvin@arvin-laptop:~$ sudo install -d /lib/modules/`uname -r`/misc
arvin@arvin-laptop:~$ sudo install microdia.ko /lib/modules/`uname -r`/misc
install: cannot stat `microdia.ko': No such file or directory




> arvin@arvin-laptop:~$ sudo modprobe videodev
arvin@arvin-laptop:~$ sudo modprobe compat_ioctl32
arvin@arvin-laptop:~$ sudo insmod ./microdia.ko
insmod: can't read './microdia.ko': No such file or directory


---

### Post by loell on 2008-11-17
> **killer_d76 said:**
> still getting errors here

are you sure you're in the directory where **microdia.ko** file is present?

---

### Post by killer_d76 on 2008-11-17
this is the file right?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=92999&d=1226926162[/IMG]

---

### Post by loell on 2008-11-17
yeah, from that screenshot,  you should navigate first to that directory

```
cd /home/arvin/microdia
```

then do the previous commands, load / install modules etc..

---

### Post by killer_d76 on 2008-11-17
:confused: sorry loell could you clarify that a bit?.. medyo slow po ako ngayon eh hehehe[-o<

---

### Post by loell on 2008-11-17
the following commands are

```

cd /home/arvin/microdia

$ sudo install -d /lib/modules/`uname -r`/misc
$ sudo install microdia.ko /lib/modules/`uname -r`/misc
$ sudo depmod -a

Then to load the module all you need to do is:

$ sudo modprobe microdia


```

---

### Post by killer_d76 on 2008-11-17
WWOOOHHHOOO!!!... it worked Loell! :guitar::guitar::guitar:.. although the picture/video is inverted!.. (that's my daughter sitting on my shoulder!)... i still owe you my soul right?.. :lolflag:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=93003&d=1226928413[/IMG]

---

### Post by loell on 2008-11-17
you seem happy with the inversion. :)  this is hardy, right?

---

### Post by killer_d76 on 2008-11-17
i'm using intrepid ibex.. that's why the colors and the icons are still default, i have just installed it a few days ago!.. is there a way to fix the inverted video output?.. ;)

---

### Post by loell on 2008-11-18
actually, looking at the screenshot, it looks like you enable the "edge" effect in cheese? look at the the effects and check.

---

### Post by azumi on 2008-11-18
hello, i try install webcam driver on this laptop [https://wiki.ubuntu.com/LaptopTestingTeam/CompalHEL80](https://wiki.ubuntu.com/LaptopTestingTeam/CompalHEL80) and same webcamera Bus 005 Device 004: ID 0c45:624f Microdia PC Camera (SN9C201), i follow this steps here: [https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768) to install it, but function is only in mplayer .. with cheese its bad :( error - attached screenshot ... should some one help me with it ...

> 

Microdia webcam kernel driver project

There is a Microdia project working on an Open Source driver by reverse engeneering (usb sniffing mainly) and some little documentation.
The project has a google group : [http://groups.google.com/group/microdia](http://groups.google.com/group/microdia) and a launchpad PPA : [https://launchpad.net/~nickel62metal/+archive](https://launchpad.net/~nickel62metal/+archive).

You can add: 

deb [http://ppa.launchpad.net/nickel62metal/ubuntu](http://ppa.launchpad.net/nickel62metal/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/nickel62metal/ubuntu](http://ppa.launchpad.net/nickel62metal/ubuntu) intrepid main

And then install by: 
sudo apt-get install microdia-dkms

You can follow the development via git-web : [http://repo.or.cz/w/microdia.git](http://repo.or.cz/w/microdia.git) 

If you want to test the driver (still in development, use at your own risks): 

You need to install git first: 
sudo apt-get install git-core gitk git-gui git-doc curl

Then clone the "microdia" repository: 
git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git) 

Then build the driver: 
cd microdia
make

Now load some necessary modules before the microdia driver: 
sudo modprobe videodev
sudo modprobe compat-ioctl32

Finally, load the microdia driver (rmmod to unload it): 
sudo insmod microdia.ko

You can test the webcam with Ekiga, or mplayer: 
mplayer -fps 30 tv://

Do the following so you don't have to insmod everytime you wish to use your webcam after a restart: 
sudo cp microdia.ko /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
sudo depmod -a


---

### Post by killer_d76 on 2008-11-18
> **loell said:**
> actually, looking at the screenshot, it looks like you enable the "edge" effect in cheese? look at the the effects and check.

...even on ekiga, video output is inverted? :confused:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=93125&d=1227007143[/IMG]

---

### Post by killer_d76 on 2008-11-18
@azumi - i have tested my webcam with cheese and ekiga and the procedures posted here (by Loell) did fixed my webcam issue, though i haven't tried it on MPlayer or VLC yet, though it did not work with Camorama as well.

---

### Post by loell on 2008-11-18
> **killer_d76 said:**
> ...even on ekiga, video output is inverted? :confused:


i see, oh well, just try a monthly git of the latest source, perhaps the driver will improve, also try to get in touch with the developer(s) in the google group mailing list (as posted above) , i'm certain they would love some feedback of their driver. hopefully, in that way they can improve it in a more faster pace.

---

### Post by dealen on 2008-11-23
i still have problem i did all you said. And i m stuck here this codes

```
root@dealen-desktop:/home/dealen/microdia# sudo modprobe microdiaFATAL: Error inserting microdia (/lib/modules/2.6.27-7-generic/misc/microdia.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

```
[ 2560.782620] microdia: Unknown symbol video_ioctl2
[ 2560.783409] microdia: Unknown symbol video_devdata
[ 2560.784418] microdia: Unknown symbol video_unregister_device
[ 2560.784707] microdia: Unknown symbol video_device_alloc
[ 2560.784849] microdia: Unknown symbol video_register_device
[ 2560.785525] microdia: Unknown symbol video_device_release
[ 2604.019290] Linux video capture interface: v2.00
[ 2626.541559] microdia: disagrees about version of symbol video_ioctl2
[ 2626.541583] microdia: Unknown symbol video_ioctl2
[ 2626.542322] microdia: disagrees about version of symbol video_devdata
[ 2626.542325] microdia: Unknown symbol video_devdata
[ 2626.543270] microdia: disagrees about version of symbol video_unregister_device
[ 2626.543273] microdia: Unknown symbol video_unregister_device
[ 2626.543521] microdia: disagrees about version of symbol video_device_alloc
[ 2626.543524] microdia: Unknown symbol video_device_alloc
[ 2626.543626] microdia: disagrees about version of symbol video_register_device
[ 2626.543629] microdia: Unknown symbol video_register_device
[ 2626.544295] microdia: disagrees about version of symbol video_device_release
[ 2626.544298] microdia: Unknown symbol video_device_release
[ 2668.205609] microdia: disagrees about version of symbol video_ioctl2
[ 2668.205629] microdia: Unknown symbol video_ioctl2
[ 2668.206387] microdia: disagrees about version of symbol video_devdata
[ 2668.206390] microdia: Unknown symbol video_devdata
[ 2668.207361] microdia: disagrees about version of symbol video_unregister_device
[ 2668.207364] microdia: Unknown symbol video_unregister_device
[ 2668.207618] microdia: disagrees about version of symbol video_device_alloc
[ 2668.207628] microdia: Unknown symbol video_device_alloc
[ 2668.207732] microdia: disagrees about version of symbol video_register_device
[ 2668.207735] microdia: Unknown symbol video_register_device
[ 2668.208394] microdia: disagrees about version of symbol video_device_release
[ 2668.208398] microdia: Unknown symbol video_device_release
[ 2824.568811] microdia: disagrees about version of symbol video_ioctl2
[ 2824.568832] microdia: Unknown symbol video_ioctl2
[ 2824.569548] microdia: disagrees about version of symbol video_devdata
[ 2824.569551] microdia: Unknown symbol video_devdata
[ 2824.570442] microdia: disagrees about version of symbol video_unregister_device
[ 2824.570445] microdia: Unknown symbol video_unregister_device
[ 2824.570700] microdia: disagrees about version of symbol video_device_alloc
[ 2824.570703] microdia: Unknown symbol video_device_alloc
[ 2824.570805] microdia: disagrees about version of symbol video_register_device
[ 2824.570808] microdia: Unknown symbol video_register_device
[ 2824.571455] microdia: disagrees about version of symbol video_device_release
[ 2824.571458] microdia: Unknown symbol video_device_release
[ 2867.162240] microdia: disagrees about version of symbol video_ioctl2
[ 2867.162263] microdia: Unknown symbol video_ioctl2
[ 2867.163020] microdia: disagrees about version of symbol video_devdata
[ 2867.163023] microdia: Unknown symbol video_devdata
[ 2867.163992] microdia: disagrees about version of symbol video_unregister_device
[ 2867.163995] microdia: Unknown symbol video_unregister_device
[ 2867.164249] microdia: disagrees about version of symbol video_device_alloc
[ 2867.164252] microdia: Unknown symbol video_device_alloc
[ 2867.164356] microdia: disagrees about version of symbol video_register_device
[ 2867.164359] microdia: Unknown symbol video_register_device
[ 2867.165037] microdia: disagrees about version of symbol video_device_release
[ 2867.165040] microdia: Unknown symbol video_device_release
[ 2887.208629] microdia: disagrees about version of symbol video_ioctl2
[ 2887.208648] microdia: Unknown symbol video_ioctl2
[ 2887.209458] microdia: disagrees about version of symbol video_devdata
[ 2887.209462] microdia: Unknown symbol video_devdata
[ 2887.210444] microdia: disagrees about version of symbol video_unregister_device
[ 2887.210447] microdia: Unknown symbol video_unregister_device
[ 2887.210701] microdia: disagrees about version of symbol video_device_alloc
[ 2887.210704] microdia: Unknown symbol video_device_alloc
[ 2887.210808] microdia: disagrees about version of symbol video_register_device
[ 2887.210811] microdia: Unknown symbol video_register_device
[ 2887.211468] microdia: disagrees about version of symbol video_device_release
[ 2887.211471] microdia: Unknown symbol video_device_release
[ 2974.653806] microdia: disagrees about version of symbol video_ioctl2
[ 2974.653825] microdia: Unknown symbol video_ioctl2
[ 2974.654581] microdia: disagrees about version of symbol video_devdata
[ 2974.654584] microdia: Unknown symbol video_devdata
[ 2974.655551] microdia: disagrees about version of symbol video_unregister_device
[ 2974.655554] microdia: Unknown symbol video_unregister_device
[ 2974.655808] microdia: disagrees about version of symbol video_device_alloc
[ 2974.655811] microdia: Unknown symbol video_device_alloc
[ 2974.655915] microdia: disagrees about version of symbol video_register_device
[ 2974.655918] microdia: Unknown symbol video_register_device
[ 2974.656591] microdia: disagrees about version of symbol video_device_release
[ 2974.656595] microdia: Unknown symbol video_device_release
[ 3014.180919] usb 5-1: USB disconnect, address 4
[ 3017.012030] usb 5-1: new high speed USB device using ehci_hcd and address 8
[ 3017.146756] usb 5-1: configuration #1 chosen from 1 choice
[ 3017.241371] microdia: disagrees about version of symbol video_ioctl2
[ 3017.241388] microdia: Unknown symbol video_ioctl2
[ 3017.242081] microdia: disagrees about version of symbol video_devdata
[ 3017.242084] microdia: Unknown symbol video_devdata
[ 3017.242965] microdia: disagrees about version of symbol video_unregister_device
[ 3017.242969] microdia: Unknown symbol video_unregister_device
[ 3017.243200] microdia: disagrees about version of symbol video_device_alloc
[ 3017.243203] microdia: Unknown symbol video_device_alloc
[ 3017.243297] microdia: disagrees about version of symbol video_register_device
[ 3017.243300] microdia: Unknown symbol video_register_device
[ 3017.243900] microdia: disagrees about version of symbol video_device_release
[ 3017.243903] microdia: Unknown symbol video_device_release
[ 3023.690286] microdia: disagrees about version of symbol video_ioctl2
[ 3023.690305] microdia: Unknown symbol video_ioctl2
[ 3023.691069] microdia: disagrees about version of symbol video_devdata
[ 3023.691073] microdia: Unknown symbol video_devdata
[ 3023.692056] microdia: disagrees about version of symbol video_unregister_device
[ 3023.692059] microdia: Unknown symbol video_unregister_device
[ 3023.692315] microdia: disagrees about version of symbol video_device_alloc
[ 3023.692318] microdia: Unknown symbol video_device_alloc
[ 3023.692422] microdia: disagrees about version of symbol video_register_device
[ 3023.692426] microdia: Unknown symbol video_register_device
[ 3023.693070] microdia: disagrees about version of symbol video_device_release
[ 3023.693073] microdia: Unknown symbol video_device_release
[ 3032.847921] microdia: disagrees about version of symbol video_ioctl2
[ 3032.847947] microdia: Unknown symbol video_ioctl2
[ 3032.848718] microdia: disagrees about version of symbol video_devdata
[ 3032.848721] microdia: Unknown symbol video_devdata
[ 3032.849623] microdia: disagrees about version of symbol video_unregister_device
[ 3032.849626] microdia: Unknown symbol video_unregister_device
[ 3032.849862] microdia: disagrees about version of symbol video_device_alloc
[ 3032.849865] microdia: Unknown symbol video_device_alloc
[ 3032.849961] microdia: disagrees about version of symbol video_register_device
[ 3032.849964] microdia: Unknown symbol video_register_device
[ 3032.850581] microdia: disagrees about version of symbol video_device_release
[ 3032.850584] microdia: Unknown symbol video_device_release
[ 3137.974595] microdia: disagrees about version of symbol video_ioctl2
[ 3137.974619] microdia: Unknown symbol video_ioctl2
[ 3137.975365] microdia: disagrees about version of symbol video_devdata
[ 3137.975368] microdia: Unknown symbol video_devdata
[ 3137.976319] microdia: disagrees about version of symbol video_unregister_device
[ 3137.976322] microdia: Unknown symbol video_unregister_device
[ 3137.976590] microdia: disagrees about version of symbol video_device_alloc
[ 3137.976594] microdia: Unknown symbol video_device_alloc
[ 3137.976696] microdia: disagrees about version of symbol video_register_device
[ 3137.976699] microdia: Unknown symbol video_register_device
[ 3137.977345] microdia: disagrees about version of symbol video_device_release
[ 3137.977348] microdia: Unknown symbol video_device_release
[ 3215.676003] microdia: disagrees about version of symbol video_ioctl2
[ 3215.676030] microdia: Unknown symbol video_ioctl2
[ 3215.676802] microdia: disagrees about version of symbol video_devdata
[ 3215.676806] microdia: Unknown symbol video_devdata
[ 3215.677755] microdia: disagrees about version of symbol video_unregister_device
[ 3215.677758] microdia: Unknown symbol video_unregister_device
[ 3215.678006] microdia: disagrees about version of symbol video_device_alloc
[ 3215.678009] microdia: Unknown symbol video_device_alloc
[ 3215.678111] microdia: disagrees about version of symbol video_register_device
[ 3215.678114] microdia: Unknown symbol video_register_device
[ 3215.678759] microdia: disagrees about version of symbol video_device_release
[ 3215.678762] microdia: Unknown symbol video_device_release
[ 3315.559177] microdia: disagrees about version of symbol video_ioctl2
[ 3315.559203] microdia: Unknown symbol video_ioctl2
[ 3315.559949] microdia: disagrees about version of symbol video_devdata
[ 3315.559952] microdia: Unknown symbol video_devdata
[ 3315.560933] microdia: disagrees about version of symbol video_unregister_device
[ 3315.560937] microdia: Unknown symbol video_unregister_device
[ 3315.561186] microdia: disagrees about version of symbol video_device_alloc
[ 3315.561189] microdia: Unknown symbol video_device_alloc
[ 3315.561291] microdia: disagrees about version of symbol video_register_device
[ 3315.561294] microdia: Unknown symbol video_register_device
[ 3315.561941] microdia: disagrees about version of symbol video_device_release
[ 3315.561944] microdia: Unknown symbol video_device_release
[ 3343.759449] microdia: disagrees about version of symbol video_ioctl2
[ 3343.759473] microdia: Unknown symbol video_ioctl2
[ 3343.760251] microdia: disagrees about version of symbol video_devdata
[ 3343.760254] microdia: Unknown symbol video_devdata
[ 3343.761147] microdia: disagrees about version of symbol video_unregister_device
[ 3343.761150] microdia: Unknown symbol video_unregister_device
[ 3343.761381] microdia: disagrees about version of symbol video_device_alloc
[ 3343.761384] microdia: Unknown symbol video_device_alloc
[ 3343.761478] microdia: disagrees about version of symbol video_register_device
[ 3343.761481] microdia: Unknown symbol video_register_device
[ 3343.762079] microdia: disagrees about version of symbol video_device_release
[ 3343.762082] microdia: Unknown symbol video_device_release
[ 3479.163563] microdia: disagrees about version of symbol video_ioctl2
[ 3479.163582] microdia: Unknown symbol video_ioctl2
[ 3479.164344] microdia: disagrees about version of symbol video_devdata
[ 3479.164348] microdia: Unknown symbol video_devdata
[ 3479.165274] microdia: disagrees about version of symbol video_unregister_device
[ 3479.165278] microdia: Unknown symbol video_unregister_device
[ 3479.165510] microdia: disagrees about version of symbol video_device_alloc
[ 3479.165513] microdia: Unknown symbol video_device_alloc
[ 3479.165607] microdia: disagrees about version of symbol video_register_device
[ 3479.165620] microdia: Unknown symbol video_register_device
[ 3479.166217] microdia: disagrees about version of symbol video_device_release
[ 3479.166224] microdia: Unknown symbol video_device_release
[ 3547.370346] microdia: disagrees about version of symbol video_ioctl2
[ 3547.370364] microdia: Unknown symbol video_ioctl2
[ 3547.371226] microdia: disagrees about version of symbol video_devdata
[ 3547.371229] microdia: Unknown symbol video_devdata
[ 3547.372135] microdia: disagrees about version of symbol video_unregister_device
[ 3547.372138] microdia: Unknown symbol video_unregister_device
[ 3547.372370] microdia: disagrees about version of symbol video_device_alloc
[ 3547.372373] microdia: Unknown symbol video_device_alloc
[ 3547.372467] microdia: disagrees about version of symbol video_register_device
[ 3547.372470] microdia: Unknown symbol video_register_device
[ 3547.373075] microdia: disagrees about version of symbol video_device_release
[ 3547.373086] microdia: Unknown symbol video_device_release
[ 3663.181017] microdia: disagrees about version of symbol video_ioctl2
[ 3663.181036] microdia: Unknown symbol video_ioctl2
[ 3663.181795] microdia: disagrees about version of symbol video_devdata
[ 3663.181798] microdia: Unknown symbol video_devdata
[ 3663.182756] microdia: disagrees about version of symbol video_unregister_device
[ 3663.182761] microdia: Unknown symbol video_unregister_device
[ 3663.183010] microdia: disagrees about version of symbol video_device_alloc
[ 3663.183013] microdia: Unknown symbol video_device_alloc
[ 3663.183115] microdia: disagrees about version of symbol video_register_device
[ 3663.183118] microdia: Unknown symbol video_register_device
[ 3663.183764] microdia: disagrees about version of symbol video_device_release
[ 3663.183767] microdia: Unknown symbol video_device_release
[ 3721.811837] microdia: disagrees about version of symbol video_ioctl2
[ 3721.811853] microdia: Unknown symbol video_ioctl2
[ 3721.812592] microdia: disagrees about version of symbol video_devdata
[ 3721.812595] microdia: Unknown symbol video_devdata
[ 3721.813499] microdia: disagrees about version of symbol video_unregister_device
[ 3721.813502] microdia: Unknown symbol video_unregister_device
[ 3721.813739] microdia: disagrees about version of symbol video_device_alloc
[ 3721.813742] microdia: Unknown symbol video_device_alloc
[ 3721.813846] microdia: disagrees about version of symbol video_register_device
[ 3721.813849] microdia: Unknown symbol video_register_device
[ 3721.814463] microdia: disagrees about version of symbol video_device_release
[ 3721.814465] microdia: Unknown symbol video_device_release
[ 3795.868713] microdia: disagrees about version of symbol video_ioctl2
[ 3795.868795] microdia: Unknown symbol video_ioctl2
[ 3795.869487] microdia: disagrees about version of symbol video_devdata
[ 3795.869490] microdia: Unknown symbol video_devdata
[ 3795.870372] microdia: disagrees about version of symbol video_unregister_device
[ 3795.870385] microdia: Unknown symbol video_unregister_device
[ 3795.870616] microdia: disagrees about version of symbol video_device_alloc
[ 3795.870619] microdia: Unknown symbol video_device_alloc
[ 3795.870713] microdia: disagrees about version of symbol video_register_device
[ 3795.870723] microdia: Unknown symbol video_register_device
[ 3795.871320] microdia: disagrees about version of symbol video_device_release
[ 3795.871323] microdia: Unknown symbol video_device_release
[ 3837.627763] microdia: disagrees about version of symbol video_ioctl2
[ 3837.627781] microdia: Unknown symbol video_ioctl2
[ 3837.628560] microdia: disagrees about version of symbol video_devdata
[ 3837.628570] microdia: Unknown symbol video_devdata
[ 3837.629515] microdia: disagrees about version of symbol video_unregister_device
[ 3837.629518] microdia: Unknown symbol video_unregister_device
[ 3837.629766] microdia: disagrees about version of symbol video_device_alloc
[ 3837.629769] microdia: Unknown symbol video_device_alloc
[ 3837.629871] microdia: disagrees about version of symbol video_register_device
[ 3837.629880] microdia: Unknown symbol video_register_device
[ 3837.630522] microdia: disagrees about version of symbol video_device_release
[ 3837.630525] microdia: Unknown symbol video_device_release
[ 4098.087731] microdia: disagrees about version of symbol video_ioctl2
[ 4098.087756] microdia: Unknown symbol video_ioctl2
[ 4098.088536] microdia: disagrees about version of symbol video_devdata
[ 4098.088540] microdia: Unknown symbol video_devdata
[ 4098.089513] microdia: disagrees about version of symbol video_unregister_device
[ 4098.089516] microdia: Unknown symbol video_unregister_device
[ 4098.089770] microdia: disagrees about version of symbol video_device_alloc
[ 4098.089773] microdia: Unknown symbol video_device_alloc
[ 4098.089878] microdia: disagrees about version of symbol video_register_device
[ 4098.089881] microdia: Unknown symbol video_register_device
[ 4098.090542] microdia: disagrees about version of symbol video_device_release
[ 4098.090545] microdia: Unknown symbol video_device_release
[ 4293.473348] microdia: disagrees about version of symbol video_ioctl2
[ 4293.473368] microdia: Unknown symbol video_ioctl2
[ 4293.474124] microdia: disagrees about version of symbol video_devdata
[ 4293.474127] microdia: Unknown symbol video_devdata
[ 4293.475010] microdia: disagrees about version of symbol video_unregister_device
[ 4293.475013] microdia: Unknown symbol video_unregister_device
[ 4293.475243] microdia: disagrees about version of symbol video_device_alloc
[ 4293.475246] microdia: Unknown symbol video_device_alloc
[ 4293.475341] microdia: disagrees about version of symbol video_register_device
[ 4293.475343] microdia: Unknown symbol video_register_device
[ 4293.475954] microdia: disagrees about version of symbol video_device_release
[ 4293.475957] microdia: Unknown symbol video_device_release
[ 4546.991673] microdia: disagrees about version of symbol video_ioctl2
[ 4546.991693] microdia: Unknown symbol video_ioctl2
[ 4546.992465] microdia: disagrees about version of symbol video_devdata
[ 4546.992468] microdia: Unknown symbol video_devdata
[ 4546.993426] microdia: disagrees about version of symbol video_unregister_device
[ 4546.993434] microdia: Unknown symbol video_unregister_device
[ 4546.993683] microdia: disagrees about version of symbol video_device_alloc
[ 4546.993686] microdia: Unknown symbol video_device_alloc
[ 4546.993788] microdia: disagrees about version of symbol video_register_device
[ 4546.993791] microdia: Unknown symbol video_register_device
[ 4546.994437] microdia: disagrees about version of symbol video_device_release
[ 4546.994440] microdia: Unknown symbol video_device_release
[ 4589.760566] microdia: disagrees about version of symbol video_ioctl2
[ 4589.760584] microdia: Unknown symbol video_ioctl2
[ 4589.761337] microdia: disagrees about version of symbol video_devdata
[ 4589.761340] microdia: Unknown symbol video_devdata
[ 4589.762301] microdia: disagrees about version of symbol video_unregister_device
[ 4589.762304] microdia: Unknown symbol video_unregister_device
[ 4589.762555] microdia: disagrees about version of symbol video_device_alloc
[ 4589.762559] microdia: Unknown symbol video_device_alloc
[ 4589.762665] microdia: disagrees about version of symbol video_register_device
[ 4589.762668] microdia: Unknown symbol video_register_device
[ 4589.763320] microdia: disagrees about version of symbol video_device_release
[ 4589.763323] microdia: Unknown symbol video_device_release
[ 4692.701355] microdia: disagrees about version of symbol video_ioctl2
[ 4692.701367] microdia: Unknown symbol video_ioctl2
[ 4692.702081] microdia: disagrees about version of symbol video_devdata
[ 4692.702089] microdia: Unknown symbol video_devdata
[ 4692.702971] microdia: disagrees about version of symbol video_unregister_device
[ 4692.702974] microdia: Unknown symbol video_unregister_device
[ 4692.703205] microdia: disagrees about version of symbol video_device_alloc
[ 4692.703208] microdia: Unknown symbol video_device_alloc
[ 4692.703303] microdia: disagrees about version of symbol video_register_device
[ 4692.703306] microdia: Unknown symbol video_register_device
[ 4692.703903] microdia: disagrees about version of symbol video_device_release
[ 4692.703906] microdia: Unknown symbol video_device_release
[ 4726.056286] microdia: disagrees about version of symbol video_ioctl2
[ 4726.056302] microdia: Unknown symbol video_ioctl2
[ 4726.057015] microdia: disagrees about version of symbol video_devdata
[ 4726.057027] microdia: Unknown symbol video_devdata
[ 4726.057916] microdia: disagrees about version of symbol video_unregister_device
[ 4726.057919] microdia: Unknown symbol video_unregister_device
[ 4726.058152] microdia: disagrees about version of symbol video_device_alloc
[ 4726.058154] microdia: Unknown symbol video_device_alloc
[ 4726.058249] microdia: disagrees about version of symbol video_register_device
[ 4726.058252] microdia: Unknown symbol video_register_device
[ 4726.058849] microdia: disagrees about version of symbol video_device_release
[ 4726.058852] microdia: Unknown symbol video_device_release

```

```
dealen@dealen-desktop:~/microdia$ sudo insmod ./microdia.ko
insmod: error inserting './microdia.ko': -1 Unknown symbol in module

```

---

### Post by mrpurple on 2008-11-25
Dear after one year i get how install and use the microdia webcam. 
I hope now that this can help others.
I did a lsusb and i get 
> Bus 005 Device 004: ID 0c45:624f Microdia PC Camera (SN9C201)
I have ubuntu 8.10 64 bit but same for 32 i guess.
so before you have to check:
> uname -r
See the kernel version and install Install linux-headers with the same version as your kernel from synaptic or from terminal with apt-get install kernel-package linux-headers build-essential.
git have to be installed
The step by step guide from Terminal:

> git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
> cd microdia
> make
do not care to the error 127
> sudo modprobe videodev
> sudo modprobe compat-ioctl32
> sudo insmod microdia.ko

Now check if from ekiga works.
For who needs skype work with the webcam you need preload the 32 library so install from syaptic v4l2:
 then the command is in my case :
> LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so /usr/bin/skype


to let this driver charged at start up 
> strip -g microdia.ko
> sudo cp microdia.ko /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
> sudo depmod -a
then entire guide also for other microdia webcams is [http://groups.google.com/group/microdia?hl=en]("http://groups.google.com/group/microdia?hl=en")

---

### Post by killer_d76 on 2008-11-30
fix for upside down images?..

[http://ubuntuforums.org/showthread.php?t=838210&highlight=ideapad]("http://ubuntuforums.org/showthread.php?t=838210&highlight=ideapad")

will try it tonight!.. wish me luck! :guitar:

---

### Post by cjoey19 on 2008-12-14
> **dealen said:**
> i still have problem i did all you said. And i m stuck here this codes

```
root@dealen-desktop:/home/dealen/microdia# sudo modprobe microdiaFATAL: Error inserting microdia (/lib/modules/2.6.27-7-generic/misc/microdia.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

```
[ 2560.782620] microdia: Unknown symbol video_ioctl2
[ 2560.783409] microdia: Unknown symbol video_devdata
[ 2560.784418] microdia: Unknown symbol video_unregister_device
[ 2560.784707] microdia: Unknown symbol video_device_alloc
[ 2560.784849] microdia: Unknown symbol video_register_device
[ 2560.785525] microdia: Unknown symbol video_device_release
[ 2604.019290] Linux video capture interface: v2.00
[ 2626.541559] microdia: disagrees about version of symbol video_ioctl2
[ 2626.541583] microdia: Unknown symbol video_ioctl2
[ 2626.542322] microdia: disagrees about version of symbol video_devdata
[ 2626.542325] microdia: Unknown symbol video_devdata
[ 2626.543270] microdia: disagrees about version of symbol video_unregister_device
[ 2626.543273] microdia: Unknown symbol video_unregister_device
[ 2626.543521] microdia: disagrees about version of symbol video_device_alloc
[ 2626.543524] microdia: Unknown symbol video_device_alloc
[ 2626.543626] microdia: disagrees about version of symbol video_register_device
[ 2626.543629] microdia: Unknown symbol video_register_device
[ 2626.544295] microdia: disagrees about version of symbol video_device_release
[ 2626.544298] microdia: Unknown symbol video_device_release
[ 2668.205609] microdia: disagrees about version of symbol video_ioctl2
[ 2668.205629] microdia: Unknown symbol video_ioctl2
[ 2668.206387] microdia: disagrees about version of symbol video_devdata
[ 2668.206390] microdia: Unknown symbol video_devdata
[ 2668.207361] microdia: disagrees about version of symbol video_unregister_device
[ 2668.207364] microdia: Unknown symbol video_unregister_device
[ 2668.207618] microdia: disagrees about version of symbol video_device_alloc
[ 2668.207628] microdia: Unknown symbol video_device_alloc
[ 2668.207732] microdia: disagrees about version of symbol video_register_device
[ 2668.207735] microdia: Unknown symbol video_register_device
[ 2668.208394] microdia: disagrees about version of symbol video_device_release
[ 2668.208398] microdia: Unknown symbol video_device_release
[ 2824.568811] microdia: disagrees about version of symbol video_ioctl2
[ 2824.568832] microdia: Unknown symbol video_ioctl2
[ 2824.569548] microdia: disagrees about version of symbol video_devdata
[ 2824.569551] microdia: Unknown symbol video_devdata
[ 2824.570442] microdia: disagrees about version of symbol video_unregister_device
[ 2824.570445] microdia: Unknown symbol video_unregister_device
[ 2824.570700] microdia: disagrees about version of symbol video_device_alloc
[ 2824.570703] microdia: Unknown symbol video_device_alloc
[ 2824.570805] microdia: disagrees about version of symbol video_register_device
[ 2824.570808] microdia: Unknown symbol video_register_device
[ 2824.571455] microdia: disagrees about version of symbol video_device_release
[ 2824.571458] microdia: Unknown symbol video_device_release
[ 2867.162240] microdia: disagrees about version of symbol video_ioctl2
[ 2867.162263] microdia: Unknown symbol video_ioctl2
[ 2867.163020] microdia: disagrees about version of symbol video_devdata
[ 2867.163023] microdia: Unknown symbol video_devdata
[ 2867.163992] microdia: disagrees about version of symbol video_unregister_device
[ 2867.163995] microdia: Unknown symbol video_unregister_device
[ 2867.164249] microdia: disagrees about version of symbol video_device_alloc
[ 2867.164252] microdia: Unknown symbol video_device_alloc
[ 2867.164356] microdia: disagrees about version of symbol video_register_device
[ 2867.164359] microdia: Unknown symbol video_register_device
[ 2867.165037] microdia: disagrees about version of symbol video_device_release
[ 2867.165040] microdia: Unknown symbol video_device_release
[ 2887.208629] microdia: disagrees about version of symbol video_ioctl2
[ 2887.208648] microdia: Unknown symbol video_ioctl2
[ 2887.209458] microdia: disagrees about version of symbol video_devdata
[ 2887.209462] microdia: Unknown symbol video_devdata
[ 2887.210444] microdia: disagrees about version of symbol video_unregister_device
[ 2887.210447] microdia: Unknown symbol video_unregister_device
[ 2887.210701] microdia: disagrees about version of symbol video_device_alloc
[ 2887.210704] microdia: Unknown symbol video_device_alloc
[ 2887.210808] microdia: disagrees about version of symbol video_register_device
[ 2887.210811] microdia: Unknown symbol video_register_device
[ 2887.211468] microdia: disagrees about version of symbol video_device_release
[ 2887.211471] microdia: Unknown symbol video_device_release
[ 2974.653806] microdia: disagrees about version of symbol video_ioctl2
[ 2974.653825] microdia: Unknown symbol video_ioctl2
[ 2974.654581] microdia: disagrees about version of symbol video_devdata
[ 2974.654584] microdia: Unknown symbol video_devdata
[ 2974.655551] microdia: disagrees about version of symbol video_unregister_device
[ 2974.655554] microdia: Unknown symbol video_unregister_device
[ 2974.655808] microdia: disagrees about version of symbol video_device_alloc
[ 2974.655811] microdia: Unknown symbol video_device_alloc
[ 2974.655915] microdia: disagrees about version of symbol video_register_device
[ 2974.655918] microdia: Unknown symbol video_register_device
[ 2974.656591] microdia: disagrees about version of symbol video_device_release
[ 2974.656595] microdia: Unknown symbol video_device_release
[ 3014.180919] usb 5-1: USB disconnect, address 4
[ 3017.012030] usb 5-1: new high speed USB device using ehci_hcd and address 8
[ 3017.146756] usb 5-1: configuration #1 chosen from 1 choice
[ 3017.241371] microdia: disagrees about version of symbol video_ioctl2
[ 3017.241388] microdia: Unknown symbol video_ioctl2
[ 3017.242081] microdia: disagrees about version of symbol video_devdata
[ 3017.242084] microdia: Unknown symbol video_devdata
[ 3017.242965] microdia: disagrees about version of symbol video_unregister_device
[ 3017.242969] microdia: Unknown symbol video_unregister_device
[ 3017.243200] microdia: disagrees about version of symbol video_device_alloc
[ 3017.243203] microdia: Unknown symbol video_device_alloc
[ 3017.243297] microdia: disagrees about version of symbol video_register_device
[ 3017.243300] microdia: Unknown symbol video_register_device
[ 3017.243900] microdia: disagrees about version of symbol video_device_release
[ 3017.243903] microdia: Unknown symbol video_device_release
[ 3023.690286] microdia: disagrees about version of symbol video_ioctl2
[ 3023.690305] microdia: Unknown symbol video_ioctl2
[ 3023.691069] microdia: disagrees about version of symbol video_devdata
[ 3023.691073] microdia: Unknown symbol video_devdata
[ 3023.692056] microdia: disagrees about version of symbol video_unregister_device
[ 3023.692059] microdia: Unknown symbol video_unregister_device
[ 3023.692315] microdia: disagrees about version of symbol video_device_alloc
[ 3023.692318] microdia: Unknown symbol video_device_alloc
[ 3023.692422] microdia: disagrees about version of symbol video_register_device
[ 3023.692426] microdia: Unknown symbol video_register_device
[ 3023.693070] microdia: disagrees about version of symbol video_device_release
[ 3023.693073] microdia: Unknown symbol video_device_release
[ 3032.847921] microdia: disagrees about version of symbol video_ioctl2
[ 3032.847947] microdia: Unknown symbol video_ioctl2
[ 3032.848718] microdia: disagrees about version of symbol video_devdata
[ 3032.848721] microdia: Unknown symbol video_devdata
[ 3032.849623] microdia: disagrees about version of symbol video_unregister_device
[ 3032.849626] microdia: Unknown symbol video_unregister_device
[ 3032.849862] microdia: disagrees about version of symbol video_device_alloc
[ 3032.849865] microdia: Unknown symbol video_device_alloc
[ 3032.849961] microdia: disagrees about version of symbol video_register_device
[ 3032.849964] microdia: Unknown symbol video_register_device
[ 3032.850581] microdia: disagrees about version of symbol video_device_release
[ 3032.850584] microdia: Unknown symbol video_device_release
[ 3137.974595] microdia: disagrees about version of symbol video_ioctl2
[ 3137.974619] microdia: Unknown symbol video_ioctl2
[ 3137.975365] microdia: disagrees about version of symbol video_devdata
[ 3137.975368] microdia: Unknown symbol video_devdata
[ 3137.976319] microdia: disagrees about version of symbol video_unregister_device
[ 3137.976322] microdia: Unknown symbol video_unregister_device
[ 3137.976590] microdia: disagrees about version of symbol video_device_alloc
[ 3137.976594] microdia: Unknown symbol video_device_alloc
[ 3137.976696] microdia: disagrees about version of symbol video_register_device
[ 3137.976699] microdia: Unknown symbol video_register_device
[ 3137.977345] microdia: disagrees about version of symbol video_device_release
[ 3137.977348] microdia: Unknown symbol video_device_release
[ 3215.676003] microdia: disagrees about version of symbol video_ioctl2
[ 3215.676030] microdia: Unknown symbol video_ioctl2
[ 3215.676802] microdia: disagrees about version of symbol video_devdata
[ 3215.676806] microdia: Unknown symbol video_devdata
[ 3215.677755] microdia: disagrees about version of symbol video_unregister_device
[ 3215.677758] microdia: Unknown symbol video_unregister_device
[ 3215.678006] microdia: disagrees about version of symbol video_device_alloc
[ 3215.678009] microdia: Unknown symbol video_device_alloc
[ 3215.678111] microdia: disagrees about version of symbol video_register_device
[ 3215.678114] microdia: Unknown symbol video_register_device
[ 3215.678759] microdia: disagrees about version of symbol video_device_release
[ 3215.678762] microdia: Unknown symbol video_device_release
[ 3315.559177] microdia: disagrees about version of symbol video_ioctl2
[ 3315.559203] microdia: Unknown symbol video_ioctl2
[ 3315.559949] microdia: disagrees about version of symbol video_devdata
[ 3315.559952] microdia: Unknown symbol video_devdata
[ 3315.560933] microdia: disagrees about version of symbol video_unregister_device
[ 3315.560937] microdia: Unknown symbol video_unregister_device
[ 3315.561186] microdia: disagrees about version of symbol video_device_alloc
[ 3315.561189] microdia: Unknown symbol video_device_alloc
[ 3315.561291] microdia: disagrees about version of symbol video_register_device
[ 3315.561294] microdia: Unknown symbol video_register_device
[ 3315.561941] microdia: disagrees about version of symbol video_device_release
[ 3315.561944] microdia: Unknown symbol video_device_release
[ 3343.759449] microdia: disagrees about version of symbol video_ioctl2
[ 3343.759473] microdia: Unknown symbol video_ioctl2
[ 3343.760251] microdia: disagrees about version of symbol video_devdata
[ 3343.760254] microdia: Unknown symbol video_devdata
[ 3343.761147] microdia: disagrees about version of symbol video_unregister_device
[ 3343.761150] microdia: Unknown symbol video_unregister_device
[ 3343.761381] microdia: disagrees about version of symbol video_device_alloc
[ 3343.761384] microdia: Unknown symbol video_device_alloc
[ 3343.761478] microdia: disagrees about version of symbol video_register_device
[ 3343.761481] microdia: Unknown symbol video_register_device
[ 3343.762079] microdia: disagrees about version of symbol video_device_release
[ 3343.762082] microdia: Unknown symbol video_device_release
[ 3479.163563] microdia: disagrees about version of symbol video_ioctl2
[ 3479.163582] microdia: Unknown symbol video_ioctl2
[ 3479.164344] microdia: disagrees about version of symbol video_devdata
[ 3479.164348] microdia: Unknown symbol video_devdata
[ 3479.165274] microdia: disagrees about version of symbol video_unregister_device
[ 3479.165278] microdia: Unknown symbol video_unregister_device
[ 3479.165510] microdia: disagrees about version of symbol video_device_alloc
[ 3479.165513] microdia: Unknown symbol video_device_alloc
[ 3479.165607] microdia: disagrees about version of symbol video_register_device
[ 3479.165620] microdia: Unknown symbol video_register_device
[ 3479.166217] microdia: disagrees about version of symbol video_device_release
[ 3479.166224] microdia: Unknown symbol video_device_release
[ 3547.370346] microdia: disagrees about version of symbol video_ioctl2
[ 3547.370364] microdia: Unknown symbol video_ioctl2
[ 3547.371226] microdia: disagrees about version of symbol video_devdata
[ 3547.371229] microdia: Unknown symbol video_devdata
[ 3547.372135] microdia: disagrees about version of symbol video_unregister_device
[ 3547.372138] microdia: Unknown symbol video_unregister_device
[ 3547.372370] microdia: disagrees about version of symbol video_device_alloc
[ 3547.372373] microdia: Unknown symbol video_device_alloc
[ 3547.372467] microdia: disagrees about version of symbol video_register_device
[ 3547.372470] microdia: Unknown symbol video_register_device
[ 3547.373075] microdia: disagrees about version of symbol video_device_release
[ 3547.373086] microdia: Unknown symbol video_device_release
[ 3663.181017] microdia: disagrees about version of symbol video_ioctl2
[ 3663.181036] microdia: Unknown symbol video_ioctl2
[ 3663.181795] microdia: disagrees about version of symbol video_devdata
[ 3663.181798] microdia: Unknown symbol video_devdata
[ 3663.182756] microdia: disagrees about version of symbol video_unregister_device
[ 3663.182761] microdia: Unknown symbol video_unregister_device
[ 3663.183010] microdia: disagrees about version of symbol video_device_alloc
[ 3663.183013] microdia: Unknown symbol video_device_alloc
[ 3663.183115] microdia: disagrees about version of symbol video_register_device
[ 3663.183118] microdia: Unknown symbol video_register_device
[ 3663.183764] microdia: disagrees about version of symbol video_device_release
[ 3663.183767] microdia: Unknown symbol video_device_release
[ 3721.811837] microdia: disagrees about version of symbol video_ioctl2
[ 3721.811853] microdia: Unknown symbol video_ioctl2
[ 3721.812592] microdia: disagrees about version of symbol video_devdata
[ 3721.812595] microdia: Unknown symbol video_devdata
[ 3721.813499] microdia: disagrees about version of symbol video_unregister_device
[ 3721.813502] microdia: Unknown symbol video_unregister_device
[ 3721.813739] microdia: disagrees about version of symbol video_device_alloc
[ 3721.813742] microdia: Unknown symbol video_device_alloc
[ 3721.813846] microdia: disagrees about version of symbol video_register_device
[ 3721.813849] microdia: Unknown symbol video_register_device
[ 3721.814463] microdia: disagrees about version of symbol video_device_release
[ 3721.814465] microdia: Unknown symbol video_device_release
[ 3795.868713] microdia: disagrees about version of symbol video_ioctl2
[ 3795.868795] microdia: Unknown symbol video_ioctl2
[ 3795.869487] microdia: disagrees about version of symbol video_devdata
[ 3795.869490] microdia: Unknown symbol video_devdata
[ 3795.870372] microdia: disagrees about version of symbol video_unregister_device
[ 3795.870385] microdia: Unknown symbol video_unregister_device
[ 3795.870616] microdia: disagrees about version of symbol video_device_alloc
[ 3795.870619] microdia: Unknown symbol video_device_alloc
[ 3795.870713] microdia: disagrees about version of symbol video_register_device
[ 3795.870723] microdia: Unknown symbol video_register_device
[ 3795.871320] microdia: disagrees about version of symbol video_device_release
[ 3795.871323] microdia: Unknown symbol video_device_release
[ 3837.627763] microdia: disagrees about version of symbol video_ioctl2
[ 3837.627781] microdia: Unknown symbol video_ioctl2
[ 3837.628560] microdia: disagrees about version of symbol video_devdata
[ 3837.628570] microdia: Unknown symbol video_devdata
[ 3837.629515] microdia: disagrees about version of symbol video_unregister_device
[ 3837.629518] microdia: Unknown symbol video_unregister_device
[ 3837.629766] microdia: disagrees about version of symbol video_device_alloc
[ 3837.629769] microdia: Unknown symbol video_device_alloc
[ 3837.629871] microdia: disagrees about version of symbol video_register_device
[ 3837.629880] microdia: Unknown symbol video_register_device
[ 3837.630522] microdia: disagrees about version of symbol video_device_release
[ 3837.630525] microdia: Unknown symbol video_device_release
[ 4098.087731] microdia: disagrees about version of symbol video_ioctl2
[ 4098.087756] microdia: Unknown symbol video_ioctl2
[ 4098.088536] microdia: disagrees about version of symbol video_devdata
[ 4098.088540] microdia: Unknown symbol video_devdata
[ 4098.089513] microdia: disagrees about version of symbol video_unregister_device
[ 4098.089516] microdia: Unknown symbol video_unregister_device
[ 4098.089770] microdia: disagrees about version of symbol video_device_alloc
[ 4098.089773] microdia: Unknown symbol video_device_alloc
[ 4098.089878] microdia: disagrees about version of symbol video_register_device
[ 4098.089881] microdia: Unknown symbol video_register_device
[ 4098.090542] microdia: disagrees about version of symbol video_device_release
[ 4098.090545] microdia: Unknown symbol video_device_release
[ 4293.473348] microdia: disagrees about version of symbol video_ioctl2
[ 4293.473368] microdia: Unknown symbol video_ioctl2
[ 4293.474124] microdia: disagrees about version of symbol video_devdata
[ 4293.474127] microdia: Unknown symbol video_devdata
[ 4293.475010] microdia: disagrees about version of symbol video_unregister_device
[ 4293.475013] microdia: Unknown symbol video_unregister_device
[ 4293.475243] microdia: disagrees about version of symbol video_device_alloc
[ 4293.475246] microdia: Unknown symbol video_device_alloc
[ 4293.475341] microdia: disagrees about version of symbol video_register_device
[ 4293.475343] microdia: Unknown symbol video_register_device
[ 4293.475954] microdia: disagrees about version of symbol video_device_release
[ 4293.475957] microdia: Unknown symbol video_device_release
[ 4546.991673] microdia: disagrees about version of symbol video_ioctl2
[ 4546.991693] microdia: Unknown symbol video_ioctl2
[ 4546.992465] microdia: disagrees about version of symbol video_devdata
[ 4546.992468] microdia: Unknown symbol video_devdata
[ 4546.993426] microdia: disagrees about version of symbol video_unregister_device
[ 4546.993434] microdia: Unknown symbol video_unregister_device
[ 4546.993683] microdia: disagrees about version of symbol video_device_alloc
[ 4546.993686] microdia: Unknown symbol video_device_alloc
[ 4546.993788] microdia: disagrees about version of symbol video_register_device
[ 4546.993791] microdia: Unknown symbol video_register_device
[ 4546.994437] microdia: disagrees about version of symbol video_device_release
[ 4546.994440] microdia: Unknown symbol video_device_release
[ 4589.760566] microdia: disagrees about version of symbol video_ioctl2
[ 4589.760584] microdia: Unknown symbol video_ioctl2
[ 4589.761337] microdia: disagrees about version of symbol video_devdata
[ 4589.761340] microdia: Unknown symbol video_devdata
[ 4589.762301] microdia: disagrees about version of symbol video_unregister_device
[ 4589.762304] microdia: Unknown symbol video_unregister_device
[ 4589.762555] microdia: disagrees about version of symbol video_device_alloc
[ 4589.762559] microdia: Unknown symbol video_device_alloc
[ 4589.762665] microdia: disagrees about version of symbol video_register_device
[ 4589.762668] microdia: Unknown symbol video_register_device
[ 4589.763320] microdia: disagrees about version of symbol video_device_release
[ 4589.763323] microdia: Unknown symbol video_device_release
[ 4692.701355] microdia: disagrees about version of symbol video_ioctl2
[ 4692.701367] microdia: Unknown symbol video_ioctl2
[ 4692.702081] microdia: disagrees about version of symbol video_devdata
[ 4692.702089] microdia: Unknown symbol video_devdata
[ 4692.702971] microdia: disagrees about version of symbol video_unregister_device
[ 4692.702974] microdia: Unknown symbol video_unregister_device
[ 4692.703205] microdia: disagrees about version of symbol video_device_alloc
[ 4692.703208] microdia: Unknown symbol video_device_alloc
[ 4692.703303] microdia: disagrees about version of symbol video_register_device
[ 4692.703306] microdia: Unknown symbol video_register_device
[ 4692.703903] microdia: disagrees about version of symbol video_device_release
[ 4692.703906] microdia: Unknown symbol video_device_release
[ 4726.056286] microdia: disagrees about version of symbol video_ioctl2
[ 4726.056302] microdia: Unknown symbol video_ioctl2
[ 4726.057015] microdia: disagrees about version of symbol video_devdata
[ 4726.057027] microdia: Unknown symbol video_devdata
[ 4726.057916] microdia: disagrees about version of symbol video_unregister_device
[ 4726.057919] microdia: Unknown symbol video_unregister_device
[ 4726.058152] microdia: disagrees about version of symbol video_device_alloc
[ 4726.058154] microdia: Unknown symbol video_device_alloc
[ 4726.058249] microdia: disagrees about version of symbol video_register_device
[ 4726.058252] microdia: Unknown symbol video_register_device
[ 4726.058849] microdia: disagrees about version of symbol video_device_release
[ 4726.058852] microdia: Unknown symbol video_device_release

```

```
dealen@dealen-desktop:~/microdia$ sudo insmod ./microdia.ko
insmod: error inserting './microdia.ko': -1 Unknown symbol in module

```

do a reinstall of the linux image

sudo apt-get install --reinstall linux-image-`uname -r`

it worked for me :) try it!

---

### Post by localj on 2009-05-22
Ubuntu 9.04 64 bit here.

lsusb produces:
0c45:624f Microdia PC Camera (SN9C201)

Added the source:
deb [http://ppa.launchpad.net/nickel62metal/ubuntu](http://ppa.launchpad.net/nickel62metal/ubuntu) jaunty main

Installed by:
sudo apt-get install microdia-dkms

And now Skype work perfectly for video. 

Of course the question is how do I get the microphone to work :D

---

### Post by camurgo on 2009-08-10
> **localj said:**
> Ubuntu 9.04 64 bit here.

lsusb produces:
0c45:624f Microdia PC Camera (SN9C201)

Added the source:
deb [http://ppa.launchpad.net/nickel62metal/ubuntu](http://ppa.launchpad.net/nickel62metal/ubuntu) jaunty main

Installed by:
sudo apt-get install microdia-dkms

And now Skype work perfectly for video. 

Of course the question is how do I get the microphone to work :D

I'm on 9.04 32bits here and this totally worked! :P

---

### Post by bladerunnerfast on 2009-08-24
how do i undo the invert?
also my cam still won't work on skype

---

### Post by bladerunnerfast on 2009-08-25
> **Cameigons said:**
> I'm on 9.04 32bits here and this totally worked! :P

dude ive done what you wrote and my don't work at all

---

### Post by bladerunnerfast on 2009-08-25
> **loell said:**
> from the blog article, there was a specific comment for 8.04 x86_64



try those steps.

 when i tryed this git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
i got was it didnt understand the command?

---

### Post by killer_d76 on 2009-08-25
bladerunnerfast: could you post the result of > **lsusb** if you type it on the terminal?

because if you found Microdia PC Camera (SN9C201) from the result... 

using this process should fix the issue...

Add this on your software source:

deb [http://ppa.launchpad.net/nickel62metal/ubuntu](http://ppa.launchpad.net/nickel62metal/ubuntu) jaunty main

Install microdia dkms by typing

sudo apt-get install microdia-dkms


oh and don't forget to install "cheese" to test if your camera is working...

sudo apt-get install cheese

---

### Post by aljoriz on 2009-08-30
This is my 1st post but I'd like to offer some help.  

For driver sa cam try google easy cam install that for no headaches.

Now if your cam works on cheese or ekiga but not skype kindly do the following at the terminal
$ sudo gedit /usr/local/bin/skype
write your password as root
then copy paste this to the window na lalabas
******
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
******
DI KASAMA YUNG *

after saving go back to terminal
$ sudo chmod a+x /usr/local/bin/skype

hope this helped pare

---

### Post by killer_d76 on 2010-01-05
thanks aljoris!.. works perfect on my Neo Laptop running CrunchBang!

---

### Post by killer_d76 on 2010-05-16
recently upgraded to 10.04 and cheese detected my webcam out of the box!... but when I use Skype it was not working?... can someone help me?

---

### Post by killer_d76 on 2010-05-16
> **killer_d76 said:**
> recently upgraded to 10.04 and cheese detected my webcam out of the box!... but when I use Skype it was not working?... can someone help me?

guess what?... I just fixed the issue with these codes!

$ sudo gedit /usr/local/bin/skype

add this:
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype

then:

$ sudo chmod a+x /usr/local/bin/skype


that's it!

---

### Post by afrodeity on 2012-01-24
Oneiric places libv4 in a different directory for some reason

```

#!/bin/bash
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so.0 /usr/bin/skype

```

---

### Post by jonhen on 2012-03-03
Thanks very much [afrodeity]("http://ubuntuforums.org/member.php?u=626266") that fixed my problem, couldn't find where libv4 was installed to. :)

Also found that you need to add bash -c '<command>' with a couple of minor tweaks to the command when putting it in a launcher thus:


bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype'

---

