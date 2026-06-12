---
title: "how to install a webcam?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by luisfer4525 on 2008-05-17
Hey,
I have a lot of trouble to install my webcam in my PC. I have the latest version of Ubuntu but still it doesn't work, it seems not to recognize it at all. I am using a Genius Messenger 310 webcam that has incorporated mic, and usually I use Pidgin as chat client. Can somebody please tell me how to:

1. Install my webcam in my PC?
2. Make Pidgin work with it?
3. Suggest other chat clients that work properly with webcams as mine?

Thanks,
L

---

### Post by y-lee on 2008-05-17
If the operating system does not recognize them, Webcams can be be hard if not impossible to get to work with linux.

You might want to see the advice given here: [Web Cams]("https://help.ubuntu.com/community/Webcam"). If that advice does not work: with the web cam plugged in  please post the output of typing the code below into the terminal. 

```
 lsusb
```

Edit: And btw Pidgin doesn't support video but   aMSN,  kopete,  ekiga and  Skype 2.0 and some other programs do.

---

### Post by luisfer4525 on 2008-05-18
Thank you! Well, it recognizes the webcam, it appears connected to the computer after I try the lsusb command... but it does not give any sign. I will keep on trying.

---

### Post by Taras on 2008-05-18
|Have you tried add or remove and install a webcam viewer ? it should automatically configure ur cam

---

### Post by HisEm on 2008-05-19
> **Taras said:**
> |Have you tried add or remove and install a webcam viewer ? it should automatically configure ur cam

I need help too:( 
I tried reinstalling Camorama with webcam plugged in and on and that did not work. When I 'lsusb' It says I have a :
Microdia U-CAM PC Camera NE878
How do I make it work??? I don't know anything so if you can tell me what to do step by step I'd be eternally grateful.
:)

---

### Post by y-lee on 2008-05-19
> **HisEm said:**
> I need help too:( 
I tried reinstalling Camorama with webcam plugged in and on and that did not work. When I 'lsusb' It says I have a :
Microdia U-CAM PC Camera NE878
How do I make it work??? I don't know anything so if you can tell me what to do step by step I'd be eternally grateful.
:)


AS near as I can tell from google that camera is not supported in Linux. I can find people asking the same question but no answers. Sorry.

---

### Post by yaidiot! on 2008-06-11
There are two projects for this webcam --

[http://groups.google.com/group/microdia](http://groups.google.com/group/microdia)
[http://www.linux-projects.org/](http://www.linux-projects.org/)

You may want to take a look at them.

---

### Post by aktiwers on 2008-06-11
This is a good link as well
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Skype and aMsn er pretty good with cams IMO

---

### Post by yaidiot! on 2008-06-11
I just got mine working actually -- not too hard. Try:

```
sudo aptitude install kernel-package linux-source build-essential git-core exuberant-ctags cheese
git clone http://repo.or.cz/r/microdia.git
cd microdia
make
sudo insmod ./microdia.ko
cheese
```

If all goes well, you'll be using your webcam in no time.

This is the device id: 

Bus 002 Device 005: ID 0c45:6270 Microdia U-CAM PC Camera NE878

 -- Funny this one works in linux but i couldn't get it working with windows!

---

### Post by intel on 2008-06-15
for windows drivers go here
[http://www.sonix.com.tw/sonix/download.do?d=2049,2](http://www.sonix.com.tw/sonix/download.do?d=2049,2)

for MAC drivers go here
[http://www.sonix.com.tw/sonix/download.do?d=1988,2](http://www.sonix.com.tw/sonix/download.do?d=1988,2)

Also remember to join this mailing list
[https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

join the list to help us get a better driver under linux

---

### Post by dannyb37 on 2008-06-19
> **yaidiot! said:**
> I just got mine working actually -- not too hard. Try:

```
sudo aptitude install kernel-package linux-source build-essential git-core exuberant-ctags cheese
git clone http://repo.or.cz/r/microdia.git
cd microdia
make
sudo insmod ./microdia.ko
cheese
```

If all goes well, you'll be using your webcam in no time.

This is the device id: 

Bus 002 Device 005: ID 0c45:6270 Microdia U-CAM PC Camera NE878

 -- Funny this one works in linux but i couldn't get it working with windows!

> daniel@daniel-desktop:~/microdia$ sudo insmod ./microdia.ko
insmod: error inserting './microdia.ko': -1 Unknown symbol in module

Any ideas?

---

### Post by yaidiot! on 2008-06-23
After making try:
sudo modprobe videodev
sudo modprobe compat-ioctl32
then
sudo insmod ./microdia.ko

I found everything I needed here: [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

---

### Post by deathvalleyjoker on 2008-09-11
> **yaidiot! said:**
> After making try:
sudo modprobe videodev
sudo modprobe compat-ioctl32
then
sudo insmod ./microdia.ko

I found everything I needed here: [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

I had hte same problem and this worked perfectly!!! thanks you!!!!

---

### Post by Crafty Kisses on 2008-09-11
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by ErikDeBruijn on 2008-10-02
Worked great. I wrote this script that will handle it. You can run it every time a kernel is upgraded:
#!/bin/bash

set -x

# More info, see [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?pli=1](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?pli=1)

# First make sure the system itself is up-to-date
sudo apt-get update
sudo apt-get upgrade

# Then install everything we need to build the camera driver
sudo aptitude install kernel-package linux-source build-essential git-core exuberant-ctags cheese
cd /tmp

# Get latest release of kernel driver
git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
cd microdia*
make
sudo modprobe videodev
sudo modprobe compat-ioctl32
sudo modprobe ./microdia.ko

# install it
strip -g microdia.ko
sudo cp microdia.ko /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
sudo depmod -a

# Now, unplug the camera if you had it plugged in. Then plug it in again

---

### Post by vlatko175 on 2008-10-08
> **ErikDeBruijn said:**
> Worked great. I wrote this script that will handle it. You can run it every time a kernel is upgraded:
#!/bin/bash

set -x

# More info, see [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?pli=1](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?pli=1)

# First make sure the system itself is up-to-date
sudo apt-get update
sudo apt-get upgrade

# Then install everything we need to build the camera driver
sudo aptitude install kernel-package linux-source build-essential git-core exuberant-ctags cheese
cd /tmp

# Get latest release of kernel driver
git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
cd microdia*
make
sudo modprobe videodev
sudo modprobe compat-ioctl32
sudo modprobe ./microdia.ko

# install it
strip -g microdia.ko
sudo cp microdia.ko /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
sudo depmod -a

# Now, unplug the camera if you had it plugged in. Then plug it in again
thank's man :)=D>

---

### Post by djallalnamri on 2008-10-13
*hello
*this is what i get when i type lsusb:
 Bus 004 Device 001: ID 0000:0000  
 Bus 003 Device 001: ID 0000:0000  
 Bus 002 Device 004: ID 0c45:627b Microdia 
 Bus 002 Device 003: ID 03eb:0902 Atmel Corp. 
 Bus 002 Device 002: ID 04fc:0005 Sunplus Technology Co., Ltd 
 Bus 002 Device 001: ID 0000:0000  
 Bus 001 Device 001: ID 0000:0000  
*so i have followed this procedure to install a webcam:
 sudo aptitude install kernel-package linux-source build-essential git-core exuberant-ctags cheese
git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
cd microdia
make
sudo insmod ./microdia.ko
cheese
*well now at least the webcam reacts a i see its light green light turning on whenever i try to use cheese or ekiga although on both i still have no image
*camorama says:could not connect to video device(/dev/video0).please check connection.
*any help 
*thanks in advance

---

### Post by intel on 2008-10-15
use the software given here
[http://groups.google.com/group/microdia/t/ba72dcf40ac481a8](http://groups.google.com/group/microdia/t/ba72dcf40ac481a8)


to increase the exposure of your webcam, don't forget to register at the above site for further help

---

### Post by arysar on 2008-10-27
I've got a Genius Messenger 310 webcam that has incorporated mic, I can make it works under ubuntu 8.04, I've tried the advice given in [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) but didn't help, the  lsusb output is

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 093a:2624 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000  

Thanks!

---

### Post by Crafty Kisses on 2008-10-27
It looks like it's detected, I think it's the Pixart Imaging.

---

### Post by Falconmauro on 2008-12-08
Hello Im new to this still, I have a web cam and my ubuntu recognizes it, its a Microdia U-CAM PC Camera NE878 just like one of the previous posts, the problem is, when I go to cd microdia and the make, I get 

```
	
make-C / lib/modules/2.6.27-9-generic/build subdirs = / home / david / modules microdia
make [1]: it enters the directory `/ usr/src/linux-headers-2.6.27-9-generic '
   CC [M] / home / david / microdia / microdia-usb.o
In the file included in include / linux / gfp.h: 4
                  from include / linux / kmod.h: 22,
                  from include / linux / module.h: 13
                  from / home / david / microdia / microdia-usb.c: 27:
include / linux / mmzone.h: 18:26: error: linux / bounds.h: No such file or directory
include / linux / mmzone.h: 197:5: warning: "MAX_NR_ZONES" is not defined
In file included from include / linux / gfp.h: 4
                  from include / linux / kmod.h: 22,
                  from include / linux / module.h: 13
                  from / home / david / microdia / microdia-usb.c: 27:
include / linux / mmzone.h: 218: error: 'MAX_NR_ZONES' is not declared here (not in a function)
make [2]: *** [/ home / david / microdia / microdia-usb.o] Error 1
make [1]: *** [_module_ / home / david / microdia] Error 2
make [1]: exits the directory `/ usr/src/linux-headers-2.6.27-9-generic '
make: *** [drivers] Error 2
```

My ubuntu is in spanish, but I think that is what it says in english, I dont know what to do, can someone help me? :(

---

### Post by aL3xandar on 2008-12-29
Yup... my Ubuntu, though, is English, but it still puts out the same error:

> 
mandalic@gryphon:~/Desktop/microdia$ make
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/mandalic/Desktop/microdia modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/mandalic/Desktop/microdia/microdia-usb.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/mandalic/Desktop/microdia/microdia-usb.c:27:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:197:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/mandalic/Desktop/microdia/microdia-usb.c:27:
include/linux/mmzone.h:218: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
make[2]: *** [/home/mandalic/Desktop/microdia/microdia-usb.o] Error 1
make[1]: *** [_module_/home/mandalic/Desktop/microdia] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [driver] Error 2


**lsusb** prints out next info:

> 
mandalic@gryphon:~$ lsusb
**Bus 006 Device 004: ID 0c45:627b Microdia PC Camera (SN9C201)**
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 069a:4501 Askey Computer Corp. Scientific-Atlanta WebSTAR 2000 series Cable Modem
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04fc:0801 Sunplus Technology Co., Ltd 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


So, I guess no one's about to get up with this one...
:(

---

### Post by yaidiot! on 2009-02-22
@falcon, alex,

try removing the headers:
```
sudo aptitude remove linux-headers-`uname -r`
```

then reinstalling:
```
sudo aptitude install linux-headers-`uname -r` 
```

remove the microdia directory and try again from git-clone.

One other note, seems the module name is sn9c20x.ko

See [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

---

### Post by galv on 2009-02-27
> **djallalnamri said:**
> 
 Bus 002 Device 004: ID 0c45:627b Microdia 


> **arysar said:**
> 
Bus 001 Device 004: ID 093a:2624 Pixart Imaging, Inc. 


Does the microdia driver work with both? I have the Pixart one and I can't seem to get it to work :(

---

### Post by steelbloo on 2009-03-03
Hi Everybody !

How difficult can it be to install a webcam ??  If anyone can help me that would be great, but please be gentle with me as the new LINUX lingo is very new to me!!
So much so, I realise I have been posting in the wrong part of the forum for help previously!

Ok, here goes:
Running a old PC with ubuntu 8.10 via ethernet.
Skype2 is running fine.
When I click to test webcam the screen is just a load of fuzz.
Does this mean ubuntu knows the webcam is there, but not installed correctly?  or have I just got it all wrong?

The webcam is a Phillips SPC 300NC

Thanking you in advance for any help
Vicky (prev. XP user !)   ;)

---

### Post by afrodeity on 2009-03-07
afrodeity@afrodeity-desktop:~$ git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git) microdia4
Initialized empty Git repository in /home/afrodeity/microdia4/.git/
Cannot get remote repository information.
Perhaps git-update-server-info needs to be run there?

How do I do this? Is the git source available? I've heard support might be included in Jaunty?

---

### Post by yaidiot! on 2009-03-09
@steelbloo,

The first step is to find out which camera you have. In the terminal:
> lsusb |grep Microdia

@afrodiety, your git command worked fine for me. Perhaps the repo was temporarily offline.

---

### Post by okamishadow on 2009-03-10
I follow the steps in the 1st page. I'm troubleshooting a HP pavilion dv9000 with AMD64 and NVIDIA card. Has web cam integrated, I follow the steps to install cheese and works perfectly for take pictures and video recording ;), but my main interest is get a video conference with my IM application, I try upgrade from Pidgin 2.5.2 to 2.5.5 but the proccess is very tedious and I feel tired at least. So I will try installing another IM application and tell you later... If someone has some idea please...}

Ah, I'm using Intrepid... :D

---

### Post by marciovinicius on 2009-03-15
```
vinicius@ubuntu-doido:~/microdia$ sudo make
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS= modules
make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.27-11-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function ‘conf_askvalue’:
scripts/kconfig/conf.c:104: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function ‘conf_choice’:
scripts/kconfig/conf.c:306: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
In file included from scripts/kconfig/zconf.tab.c:2486:
scripts/kconfig/confdata.c: In function ‘conf_write’:
scripts/kconfig/confdata.c:501: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
scripts/kconfig/confdata.c: In function ‘conf_write_autoconf’:
scripts/kconfig/confdata.c:739: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
scripts/kconfig/confdata.c:740: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
In file included from scripts/kconfig/zconf.tab.c:2487:
scripts/kconfig/expr.c: In function ‘expr_print_file_helper’:
scripts/kconfig/expr.c:1090: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.27-11-generic'
make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.27-11-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
make[2]: *** Sem regra para processar o alvo `kernel/bounds.c', necessário por `kernel/bounds.s'.  Pare.
make[1]: ** [prepare0] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.27-11-generic'
make: ** [driver] Erro 2
vinicius@ubuntu-doido:~/microdia$ make
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/vinicius/microdia modules
make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/vinicius/microdia/sn9c20x-usb.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/vinicius/microdia/sn9c20x-usb.c:27:
include/linux/mmzone.h:18:26: error: linux/bounds.h: Arquivo ou diretório inexistente
include/linux/mmzone.h:197:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/vinicius/microdia/sn9c20x-usb.c:27:
include/linux/mmzone.h:218: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
make[2]: ** [/home/vinicius/microdia/sn9c20x-usb.o] Erro 1
make[1]: ** [_module_/home/vinicius/microdia] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.27-11-generic'
make: ** [driver] Erro 2
vinicius@ubuntu-doido:~/microdia$ sudo insmod ./microdia.ko
insmod: can't read './microdia.ko': No such file or directory

```I gave up. I thought USB devices were plug-and-play... :( It can't be that hard to make a simple webcam work.

---

### Post by Flymo on 2009-03-28
Thanks to **Yaidiot**  for the script in post #9, which did the job after one change.

I was getting a 'file/directory not found' from *insmod* after executing 

```
sudo insmod ./microdia.ko
```

Had a look around, and found [[COLOR="Red"]this link[/COLOR]]("https://groups.google.com/group/microdia/web/testing-microdia-driver-draft")

which suggests this:

```
# insmod ./sn9c20x.ko
```

Aha!  we **do** have that file in  ~/microdia 
*insmod*  then worked (using sudo) and '*cheese*' delivered a picture! Yay! :guitar:

Think that there has been some renaming of files since the script was posted.  No harm done, all working now.

Machine is an Acer 5684 laptop running Ubuntu 810 on Core 2 duo T5600 and we are getting this from *lsusb* :-

```
ID 0c45:6270 Microdia U-CAM PC Camera NE878
```

---

### Post by Flymo on 2009-03-29
Ok, this was not as easy as the Acer (previous post), but it all worked after following **all** the directions for debugging on [[COLOR="Red"]this page[/COLOR]]("https://groups.google.com/group/microdia/web/testing-microdia-driver-draft")

....and making one alteration in this line:

```
# apt-get install kernel-package linux-headers build-essential libv4l
```

our installation did not have  *libv4l* installed
...but it did have *libv4l-0*

so we tried:

```
# apt-get install kernel-package linux-headers build-essential libv4l-0
```

and all was well after a couple of debugging steps.
Once running reliably, went to step 7, did a permanent install, and tried Skype..... No pix!

Found something  [[COLOR="Red"]here[/COLOR]]("http://www.mail-archive.com/microdia@googlegroups.com/msg00768.html")

which suggested: 

```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

Popping this into a one-line script called by the Xubuntu startup and we had Skype auto-loading on boot as before, with Video! Yay! :guitar:

Thanks to all who have helped with this, my wife is most grateful ;)

---

### Post by x58 on 2009-03-31
Pidgin don't have web cam support.):P

---

### Post by stephenrees on 2009-04-05
I read through this thread and tried the codes provided by Flymo

I am using Ubuntu 8.10 (and Skype worked in 8.04)

My web cam (Ezonics USB Cam IV) is detected by Skype as 
SNC9C1xx PC camera (/dev/video0) but pressing the "test" button in the Options menu produces no image

The use of the linux headers command was not too helpful 
I tried adding 2.6.27-11-generic to the apt get instruction but that produced the same result

But the PRELOAD did work 

(I would have liked to provide the output of the terminal window but the on line input thing sill not allow "more than eight images" - since all I was doing as cut and pasting text that baffles me too!)

Please do not just say "install" - provide me with something I can cut and paste into terminal. I have no idea how to "explicitly select" other than what I did

And the command lsusb produces

> Bus 003 Device 003: ID 0c45:613c Microdia PC Camera (SN9C120)

---

### Post by stephenrees on 2009-04-05
I forgot to subscribe to the thread

here is my attempt to install headers

stephen@stephen-desktop:~$ sudo apt-get install kernel-package linux-headers build-essential libv4l-0 linux-headers-2.6.27-11-generic 2.6.27-11.27

---

### Post by stephenrees on 2009-04-05
UPDATE

~$  sudo apt-get install kernel-package linux-headers-2.6.27-11-generic 2.6.27-1 build-essential libv4l-0
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-11-generic is already the newest version.

so it's not that!

---

### Post by jmadero on 2009-05-19
This is great! One problem, has anyone had any luck getting the mic to work correctly? I can't get anything out of it system wide (I need it for skype). I'm running Intrepid. Thanks all

---

### Post by millspaw on 2009-06-14
I followed the instructions from the following website, which uses *skype-stat*.

 [http://www.lockergnome.com/linux/2009/06/01/the-final-skype-on-ubuntu-904-solution/](http://www.lockergnome.com/linux/2009/06/01/the-final-skype-on-ubuntu-904-solution/))

I installed a Winbook WB-6120 WebCam (lusb;  ID: 093a:2621 Pixart Imaging,Inc)

The WB-6120 from Winbook is $12.00, has 1.3MP, SVGA 30fps.

Works in Skype and Ubuntu 9.04

---

### Post by kapitanbar on 2009-06-14
I have a Genius iLook 300 on Hardy (for AMD 64) and I can't get it to work

> lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 093a:2628 Pixart Imaging, Inc.
Bus 001 Device 001: ID 0000:0000
> lsmod |grep gspca
gspca                 657872  0
compat_ioctl32         11136  1 gspca
videodev               30720  1 gspca
usbcore               170288  5 gspca,usblp,ehci_hcd,ohci_hcd
Any help is welcomed

---

### Post by kapitanbar on 2009-06-15
> **kapitanbar said:**
> I have a Genius iLook 300 on Hardy (for AMD 64) and I can't get it to work

Any help is welcomed

Now I have too webcams, the one above mentioned and a rather old Genius Video Cam NB that works ok for kopete, but doesn't for anything else

> lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 002 Device 002: ID 093a:2628 Pixart Imaging, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0c45:6001 Microdia Genius VideoCAM NB
Bus 001 Device 001: ID 0000:0000


> lsmod |grep gspca
gspca_sonixb           13824  1
gspca_main             29568  2 gspca_sonixb
videodev               45088  3 compat_ioctl32,gspca_main
usbcore               170288  6 gspca_sonixb,gspca_main,usblp,ehci_hcd,ohci_hcd


any hint, advice or reccomendation will be welcomed!

Ubuntu is a great linux distro, but still it's not easy with webcams, and dunno why.

---

### Post by jhahoneyk on 2009-08-06
> **kapitanbar said:**
> Now I have too webcams, the one above mentioned and a rather old Genius Video Cam NB that works ok for kopete, but doesn't for anything else





any hint, advice or reccomendation will be welcomed!

Ubuntu is a great linux distro, but still it's not easy with webcams, and dunno why.

This is not a solution to your problem, but an answer to your question.
As you "dunno why", here is the explanation- because some hardware manufacturers are "great" enough to not to provide drivers for non-Windows systems. So, don't blame it to Ubuntu or any GNU/Linux distro, its entirely the manufacturers' fault. As I've learned from these things, always buy hardware which are known to be compatible with Linux (lists are available in ubuntu community help), normally Logitech ones work fine.

Cheers!!

---

### Post by drabbit on 2009-10-07
guys, im kinda new in ubuntu, i have my sounds already and graphics i salready fine, the only problem that im encountering is the webcam, i typed "lsusb" in the terminal and the attachment is the result, after that i dont know what to do..
im using a laptop ASUS x80ne

any reply is greatly appreciated..thanks!

---

### Post by Amr_not_Amr on 2010-04-24
Finally I got my Genius iLook 300 to work on karmic ..
You can follow the steps explain here [http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/](http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/) and your webcam will work...

---

