---
title: "HOWTO: See video with NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera"
date: 2007-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Pitxyoki on 2007-05-06
**[COLOR="Red"][SIZE="3"]You can see the old (deprecated) version of this HOWTO [here](http://ubuntuforums.org/showthread.php?p=9273351#post9273351). The attachments on this post are only relevant to that old version.[/SIZE][/COLOR]**

______________

If your webcam reports something similar to this:
```
$ lsusb
Bus 001 Device 005: ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera
```

Then it is now fully supported by Ubuntu (version 10.04, Lucid Lynx).

Ubuntu has, however, [a bug that needs a workaround](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255678):
```
$ sudo modprobe -rv gspca_sq905
$ sudo modprobe -v gspca_sq905

```
You have to do this after every reboot or after every time you connect the camera plug.

After this you can use XawTV or VLC to see video from your webcam:
:arrow: XawTV must not need any configuration. Just install and run it.
:arrow: With VLC, use the "Open Capture Device" (Ctrl+C) menu and point the "Video device name" to /dev/video or /dev/video0.
:arrow: aMSN must also recognise the webcam without any issues.
:arrow: [See the mentioned bugreport](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255678) for tips on making Skype work with it (I haven't tested it).


You may also be able to [download still photos](http://ubuntuforums.org/showthread.php?p=2952334#post2952334) or [record your own movies with xawtv](http://ubuntuforums.org/showthread.php?p=4269912#post4269912). Notice that these procedures were not confirmed by me on the most recent versions of Ubuntu.
Recording movies with VLC should work without any issues.

If you detect any problems with this webcam, please [check if they are already reported on Ubuntu's bug-tracker](https://launchpad.net/ubuntu/+bugs?field.searchtext=gspca). If not, feel free to submit a new ticket.


This is the full output that must be seen on the console:
```
ubuntu@ubuntu:~$ sudo modprobe -rv gspca_sq905
rmmod /lib/modules/2.6.32-21-generic/kernel/drivers/media/video/gspca/gspca_sq905.ko
rmmod /lib/modules/2.6.32-21-generic/kernel/drivers/media/video/gspca/gspca_main.ko
rmmod /lib/modules/2.6.32-21-generic/kernel/drivers/media/video/videodev.ko
rmmod /lib/modules/2.6.32-21-generic/kernel/drivers/media/video/v4l1-compat.ko

ubuntu@ubuntu:~$ sudo modprobe -v gspca_sq905
insmod /lib/modules/2.6.32-21-generic/kernel/drivers/media/video/v4l1-compat.ko
insmod /lib/modules/2.6.32-21-generic/kernel/drivers/media/video/videodev.ko
insmod /lib/modules/2.6.32-21-generic/kernel/drivers/media/video/gspca/gspca_main.ko
insmod /lib/modules/2.6.32-21-generic/kernel/drivers/media/video/gspca/gspca_sq905.ko
```


...and on /var/log/syslog:
```
May 10 12:07:24 ubuntu kernel: [ 1554.561023] usbcore: deregistering interface driver sq905
May 10 12:07:24 ubuntu kernel: [ 1554.561065] sq905: deregistered
May 10 12:07:24 ubuntu kernel: [ 1554.576046] gspca: main deregistered

May 10 12:07:39 ubuntu kernel: [ 1568.757217] Linux video capture interface: v2.00
May 10 12:07:39 ubuntu kernel: [ 1568.789711] gspca: main v2.7.0 registered
May 10 12:07:39 ubuntu kernel: [ 1568.840283] gspca: probing 2770:9120
May 10 12:07:39 ubuntu kernel: [ 1568.953414] gspca: probe ok
May 10 12:07:39 ubuntu kernel: [ 1568.953475] usbcore: registered new interface driver sq905
May 10 12:07:39 ubuntu kernel: [ 1568.954649] sq905: registered
```

---

### Post by LOCOSLAW_PL on 2007-05-14
Hello, I need help. I want to compile sqcam for Ubuntu 7.04 with kernel 2.6.20-15-generic

First i need to crate file : config.h by  ln -s autoconf.h config.h in /usr/share/linux-headers-2.6.20-15-generic/include/linux

after make makegamma and ./makegamma i write  make for sqcam and I get :

make -C /lib/modules/`uname -r`/build SUBDIRS=/home/pablo/sqcam26 modules
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/pablo/sqcam26/sq905.o
In file included from /home/pablo/sqcam26/sq905.c:65:
/home/pablo/sqcam26/usbvideo.h:203: error: field &#8216;vdev&#8217; has incomplete type
/home/pablo/sqcam26/usbvideo.h:277: error: field &#8216;vdt&#8217; has incomplete type
/home/pablo/sqcam26/sq905.c:116: error: field &#8216;vdev&#8217; has incomplete type
/home/pablo/sqcam26/sq905.c: In function &#8216;sqcam_ioctl&#8217;:
/home/pablo/sqcam26/sq905.c:358: warning: implicit declaration of function &#8216;video_devdata&#8217;
/home/pablo/sqcam26/sq905.c:358: warning: initialization makes pointer from integer without a cast
/home/pablo/sqcam26/sq905.c:359: error: dereferencing pointer to incomplete type
/home/pablo/sqcam26/sq905.c:384: warning: implicit declaration of function &#8216;copy_to_user&#8217;
/home/pablo/sqcam26/sq905.c:456: warning: implicit declaration of function &#8216;copy_from_user&#8217;
/home/pablo/sqcam26/sq905.c: In function &#8216;sqcam_open&#8217;:
/home/pablo/sqcam26/sq905.c:896: warning: initialization makes pointer from integer without a cast
/home/pablo/sqcam26/sq905.c:898: error: dereferencing pointer to incomplete type
/home/pablo/sqcam26/sq905.c:908: warning: ISO C90 forbids mixed declarations and code
/home/pablo/sqcam26/sq905.c: In function &#8216;sqcam_close&#8217;:
/home/pablo/sqcam26/sq905.c:980: warning: initialization makes pointer from integer without a cast
/home/pablo/sqcam26/sq905.c:981: error: dereferencing pointer to incomplete type
/home/pablo/sqcam26/sq905.c: In function &#8216;read_frame&#8217;:
/home/pablo/sqcam26/sq905.c:1071: warning: ISO C90 forbids mixed declarations and code
/home/pablo/sqcam26/sq905.c: In function &#8216;sqcam_read&#8217;:
/home/pablo/sqcam26/sq905.c:1104: warning: initialization makes pointer from integer without a cast
/home/pablo/sqcam26/sq905.c:1105: error: dereferencing pointer to incomplete type
/home/pablo/sqcam26/sq905.c: In function &#8216;sqcam_mmap&#8217;:
/home/pablo/sqcam26/sq905.c:1149: error: dereferencing pointer to incomplete type
/home/pablo/sqcam26/sq905.c:1150: error: dereferencing pointer to incomplete type
/home/pablo/sqcam26/sq905.c:1150: error: dereferencing pointer to incomplete type
/home/pablo/sqcam26/sq905.c:1152: warning: initialization makes pointer from integer without a cast
/home/pablo/sqcam26/sq905.c:1162: error: dereferencing pointer to incomplete type
/home/pablo/sqcam26/sq905.c:1162: warning: ISO C90 forbids mixed declarations and code
/home/pablo/sqcam26/sq905.c:1187: warning: implicit declaration of function &#8216;remap_pfn_range&#8217;
/home/pablo/sqcam26/sq905.c:1188: error: &#8216;PAGE_SHARED&#8217; undeclared (first use in this function)
/home/pablo/sqcam26/sq905.c:1188: error: (Each undeclared identifier is reported only once
/home/pablo/sqcam26/sq905.c:1188: error: for each function it appears in.)
/home/pablo/sqcam26/sq905.c: At top level:
/home/pablo/sqcam26/sq905.c:1228: error: unknown field &#8216;owner&#8217; specified in initializer
/home/pablo/sqcam26/sq905.c:1228: warning: initialization from incompatible pointer type
/home/pablo/sqcam26/sq905.c: In function &#8216;sqcam_exclusive_release&#8217;:
/home/pablo/sqcam26/sq905.c:1239: error: dereferencing pointer to incomplete type
/home/pablo/sqcam26/sq905.c:1257: error: dereferencing pointer to incomplete type
/home/pablo/sqcam26/sq905.c: At top level:
/home/pablo/sqcam26/sq905.c:1264: error: variable &#8216;sqcam_template&#8217; has initializer but incomplete type
/home/pablo/sqcam26/sq905.c:1265: error: unknown field &#8216;owner&#8217; specified in initializer
/home/pablo/sqcam26/sq905.c:1265: warning: excess elements in struct initializer
/home/pablo/sqcam26/sq905.c:1265: warning: (near initialization for &#8216;sqcam_template&#8217;)
/home/pablo/sqcam26/sq905.c:1266: error: unknown field &#8216;name&#8217; specified in initializer
/home/pablo/sqcam26/sq905.c:1266: warning: excess elements in struct initializer
/home/pablo/sqcam26/sq905.c:1266: warning: (near initialization for &#8216;sqcam_template&#8217;)
/home/pablo/sqcam26/sq905.c:1267: error: unknown field &#8216;type&#8217; specified in initializer
/home/pablo/sqcam26/sq905.c:1267: warning: excess elements in struct initializer
/home/pablo/sqcam26/sq905.c:1267: warning: (near initialization for &#8216;sqcam_template&#8217;)
/home/pablo/sqcam26/sq905.c:1268: error: unknown field &#8216;hardware&#8217; specified in initializer
/home/pablo/sqcam26/sq905.c:1268: warning: excess elements in struct initializer
/home/pablo/sqcam26/sq905.c:1268: warning: (near initialization for &#8216;sqcam_template&#8217;)
/home/pablo/sqcam26/sq905.c:1269: error: unknown field &#8216;release&#8217; specified in initializer
/home/pablo/sqcam26/sq905.c:1269: warning: excess elements in struct initializer
/home/pablo/sqcam26/sq905.c:1269: warning: (near initialization for &#8216;sqcam_template&#8217;)
/home/pablo/sqcam26/sq905.c:1270: error: unknown field &#8216;fops&#8217; specified in initializer
/home/pablo/sqcam26/sq905.c:1270: warning: excess elements in struct initializer
/home/pablo/sqcam26/sq905.c:1270: warning: (near initialization for &#8216;sqcam_template&#8217;)
/home/pablo/sqcam26/sq905.c:1271: error: unknown field &#8216;minor&#8217; specified in initializer
/home/pablo/sqcam26/sq905.c:1271: warning: excess elements in struct initializer
/home/pablo/sqcam26/sq905.c:1271: warning: (near initialization for &#8216;sqcam_template&#8217;)
/home/pablo/sqcam26/sq905.c: In function &#8216;sqcam_probe&#8217;:
/home/pablo/sqcam26/sq905.c:1331: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/home/pablo/sqcam26/sq905.c:1331: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/home/pablo/sqcam26/sq905.c:1331: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/home/pablo/sqcam26/sq905.c:1342: warning: implicit declaration of function &#8216;video_register_device&#8217;
/home/pablo/sqcam26/sq905.c:1342: error: &#8216;VFL_TYPE_GRABBER&#8217; undeclared (first use in this function)
/home/pablo/sqcam26/sq905.c: In function &#8216;sqcam_disconnect&#8217;:
/home/pablo/sqcam26/sq905.c:1367: warning: implicit declaration of function &#8216;video_unregister_device&#8217;
/home/pablo/sqcam26/sq905.c: In function &#8216;usbvideo_rvmalloc&#8217;:
/home/pablo/sqcam26/sq905.c:1708: warning: implicit declaration of function &#8216;SetPageReserved&#8217;
/home/pablo/sqcam26/sq905.c:1708: warning: implicit declaration of function &#8216;vmalloc_to_page&#8217;
/home/pablo/sqcam26/sq905.c: In function &#8216;usbvideo_rvfree&#8217;:
/home/pablo/sqcam26/sq905.c:1725: warning: implicit declaration of function &#8216;ClearPageReserved&#8217;
/home/pablo/sqcam26/sq905.c: In function &#8216;usbvideo_kvirt_to_pa&#8217;:
/home/pablo/sqcam26/sq905.c:1736: warning: implicit declaration of function &#8216;page_address&#8217;
make[2]: *** [/home/pablo/sqcam26/sq905.o] B&#322;&#261;d 1
make[1]: *** [_module_/home/pablo/sqcam26] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [module] B&#322;&#261;d 2

What I should do?
Please help me

---

### Post by Pitxyoki on 2007-05-14
LOCOSLAW_PL, I'm not sure about your problem.
Why did you have to create that symbolic link? Were you having any errors before those?
And where did you get the source from? Did you get that from my post or from the sqcam cvs?

---

### Post by LOCOSLAW_PL on 2007-05-14
I download souruces from your attached files. I create symbolic link because before that when I type make i get no linux/config.h in kernel. 

I read that 2.6.20-15 don't have config.h and it must be created. I thing that is kernel problem.

In feisty it can't be installed or I don't know how:(

---

### Post by Tzi on 2007-05-17
hey.. its great to see someone else with the same cheapo webcam.
I cant wait to get it up and running in linux, however i am having some troubles.
Maybe because i am using LinuxMint, i dont know.. but its based heavily on ubuntu, so i cant see it being a problem.

When i type make, i get the following...
```

tzi@mintbox:~/sqcam26$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/tzi/sqcam26 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/tzi/sqcam26/sq905.o
/home/tzi/sqcam26/sq905.c: In function ‘sqcam_open’:
/home/tzi/sqcam26/sq905.c:908: warning: ISO C90 forbids mixed declarations and code
/home/tzi/sqcam26/sq905.c: In function ‘read_frame’:
/home/tzi/sqcam26/sq905.c:1071: warning: ISO C90 forbids mixed declarations and code
/home/tzi/sqcam26/sq905.c: In function ‘sqcam_mmap’:
/home/tzi/sqcam26/sq905.c:1162: warning: ISO C90 forbids mixed declarations and code
/home/tzi/sqcam26/sq905.c: At top level:
/home/tzi/sqcam26/sq905.c:1228: error: unknown field ‘owner’ specified in initializer
/home/tzi/sqcam26/sq905.c:1228: warning: initialization from incompatible pointer type
make[2]: *** [/home/tzi/sqcam26/sq905.o] Error 1
make[1]: *** [_module_/home/tzi/sqcam26] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [module] Error 2
```


When i look in the folder there is no compiled file.. so its more than just warnings.
Is there something i am missing?:(

---

### Post by Pitxyoki on 2007-05-17
I'm sorry I can't help you better, but I really have not much experience on any other distro/version of linux, but I can show you the output I get so you can see where there is something different:

```
$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/luis/Downloads/Setups/Webcam/cvs/sqcam26 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-28-686'
  CC [M]  /home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sq905.o
/home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sq905.c: In function ‘sqcam_open’:
/home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sq905.c:908: warning: ISO C90 forbids mixed declarations and code
/home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sq905.c: In function ‘read_frame’:
/home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sq905.c:1071: warning: ISO C90 forbids mixed declarations and code
/home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sq905.c: In function ‘sqcam_mmap’:
/home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sq905.c:1162: warning: ISO C90 forbids mixed declarations and code
  LD [M]  /home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sqcam.o
  Building modules, stage 2.
  MODPOST
  CC      /home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sqcam.mod.o
  LD [M]  /home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sqcam.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-28-686'
$
```

It seems that the error points at line 1228...
```
/home/tzi/sqcam26/sq905.c:1228: error: unknown field ‘owner’ specified in initializer
/home/tzi/sqcam26/sq905.c:1228: warning: initialization from incompatible pointer type
make[2]: *** [/home/tzi/sqcam26/sq905.o] Error 1
make[1]: *** [_module_/home/tzi/sqcam26] Error 2
```

I absolutely can't tell you what may be the problem there, as I do not have that much deep knowledge about the Linux kernel.
This may be related to something(s?) that has(ve?) changed in the kernel and the modules may not be adapted to that, but I'm not sure... Anyway, in a few days (or weeks, depending on my work.. :-s) I'm going to try to check this on a Debian machine, which currently is running a 2.6.18 kernel.
Please tell me if you can make it to work.

**P.S.- Has anyone else been able to make this camera work?**

---

### Post by Tzi on 2007-06-02
i got it to compile my simply commenting out that line, as i have seen done with other drivers..
Works fine now... xawtv doesnt run for some reason unless its "sudo xawtv".
Either way... it works :p

--------------------------------------------------------------------

.owner = THIS_MODULE,

comment it out:

/* .owner = THIS_MODULE, */


[http://www.gossamer-threads.com/lists/mythtv/users/40136](http://www.gossamer-threads.com/lists/mythtv/users/40136)

---

### Post by Pitxyoki on 2007-06-02
To LOCOSLAW_PL and others possibily needing help: I have updated the HOWTO and I think I found a solution for your situation. Can you check that please? :)

---

### Post by LOCOSLAW_PL on 2007-06-09
You are greats!!

It Finnaly works;D

But I need to type  :** sudo touch /usr/src/linux-headers-2.6.20-16-generic/include/linux/config.h** before I make make ;)

---

### Post by DavidJames on 2007-07-02
I have a Che-ez! Snap tiny digital camera that works as a webcam on my Windows 98 system. When plugged into my linux box (running ubuntu fiesty) I get:

Bus 002 Device 004: ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera

So I downloaded your sqcam26-new.tar.gz and followed your instructions. This was my first attempt at compiling anything!

Initially the driver would not compile since it could not find linux/config.h However, I read that config.h is no longer used and so I commented it out of usbvideo.h

The driver then compiled and I installed it following your instructions.

I also installed xawtv. It shows the attached image. Each of the five vertical strips is part of the image and you can see movement. Changing the video source in xawtv gives the same layout but changes the colour.

Running xawtv -hwscan shows that the camera is mounted on /dev/video0. However, I also installed Camorama which gives the error 'Could not connect to video device (/dev/video0).' and does not start.

If I run locate sqcam.ko then I only get the line
/lib/modules/2.6.20-16-generic/kernel/drivers/usb/media/sqcam.ko

Do you have any suggestions?

---

### Post by Pitxyoki on 2007-07-02
> **Pitxyoki said:**
> Sometimes, you will need to cancel the wizard and restart it, but after two or so retries I could always get a nice picture of my room. 
Try this for xawtv. Close xawtv and run it again until you get a good picture. Sometimes I have to do this two or three times... No ideia on what causes this, though.

I haven't been able to use Camorama neither...

---

### Post by Pitxyoki on 2007-07-02
I forgot to mention, but I have been able to download still photos captured by this camera, too.
```
$ sudo apt-get install gtkam
```

This will instal a nice GUI for downloading files (photos) from your camera.
You can start it from Graphics -> gtkam. All you have to do is to go to Camera -> Add Camera, and then select "refresh". Apply/OK, and if it all goes well you're ready to go (here, it detected it as an "Argus DC-1510"). 

If you are more of a console type, you can
```
$ sudo apt-get install gphoto2
```
and then use the commands
```
$ gphoto2 -l
```
to list possible directories inside the camera and
```
$ gphoto2 -L
```
to list the files (normally, photos).

Then, you may use
```
$ gphoto2 -p
```
to download all photos in the camera.

Also, don't forget the very useful
```
$ gphoto2 --help
```
command.

Keep in mind that:
:arrow: If you don't insert any batteries on the camera, you will lose all photos it may have when you unplug it from the USB cable or when you shut down your computer;
:arrow: After you use gphoto or gtkam, the camera will no longer be usable for video. You will have to do
```
$ sudo modprobe -r sqcam
$ sudo modprobe sqcam
```
...to re-enable it's video capabilities (I'm still looking for a better way to do this, but until then, you can use that).

One more thing I found out tonight:
```
$ camorama -M
```
...and there you have camorama working. 8)
You can edit the Gnome menu entry with alacarte, to always start camorama with the "-M" argument.

________________
This has been tested under Debian *testing*, on July 2nd, 2007 and Ubuntu Dapper 6.06 on July 3rd, 2007.
Thanks once again to [crusti](http://ubuntuforums.org/showpost.php?p=2350018&postcount=10).

More info on the packages used under Debian:
```
$ gphoto2 --version
(...)
This version of gphoto2 is using the following software versions and options:
gphoto2         2.3.1          gcc, popt(m), exif, cdk, no aa, jpeg, readline
libgphoto2      2.3.1          gcc, ltdl, EXIF
libgphoto2_port 0.7.1          gcc, ltdl, USB, serial without locking
```

...and Under Ubuntu:
```
$ gphoto2 --version
(...)
This version of gphoto2 is using the following software versions and options:
gphoto2           2.1.6        gcc, no popt, exif, cdk, no aa, jpeg, readline
libgphoto2        2.1.6        gcc, EXIF, no ltdl, /proc/meminfo
libgphoto2_port   0.5.1        gcc, USB, serial without locking, no ltdl

$ gtkam --version
0.1.13

$ xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.15-28-686)
```

---

### Post by nvr2fast on 2007-07-15
Just to say that following these instructions, it works :-)

However, just running Camorama does NOT work. It says it cannot connect to /dev/video0 .

This is completely wrong. /dev/video0 is fine.

Issuing "camorama -M" does work. I am not sure why just typing camorama does not work though, perhaps a bug in camorama?

Anyway, this is GREAT stuff! Thanks for the writeup!

---

### Post by Daddo on 2007-08-05
Hello,
I try to install this driver on Ubuntu (Feisty, with KDE) too.
I have another problem :
```
~/sqcam26$ make gamma.h
gcc -std=c99 -o makegamma -lm makegamma.c
makegamma.c:1:20: erreur: stdlib.h : Aucun fichier ou répertoire de ce type
makegamma.c:2:19: erreur: stdio.h : Aucun fichier ou répertoire de ce type
makegamma.c:3:18: erreur: math.h : Aucun fichier ou répertoire de ce type
makegamma.c: In function «main":
makegamma.c:6: erreur: «FILE" undeclared (first use in this function)
makegamma.c:6: erreur: (Each undeclared identifier is reported only once
makegamma.c:6: erreur: for each function it appears in.)
makegamma.c:6: erreur: «gammafile" undeclared (first use in this function)
makegamma.c:7: attention : implicit declaration of function «fopen"
makegamma.c:7: erreur: «NULL" undeclared (first use in this function)
makegamma.c:8: attention : implicit declaration of function «fprintf"
makegamma.c:8: attention : incompatible implicit declaration of built-in function «fprintf"
makegamma.c:8: erreur: «stderr" undeclared (first use in this function)
makegamma.c:9: attention : implicit declaration of function «exit"
makegamma.c:9: attention : incompatible implicit declaration of built-in function «exit"
makegamma.c:12: attention : incompatible implicit declaration of built-in function «fprintf"
makegamma.c:17: attention : implicit declaration of function «pow"
makegamma.c:17: attention : incompatible implicit declaration of built-in function «pow"
makegamma.c:20: attention : implicit declaration of function «fputc"
makegamma.c:30: attention : implicit declaration of function «fclose"
make: *** [makegamma] Erreur 1

```

(I use a french system, an "attention" is a warning :))
With 2.6.20-16-lowlatency kernel

I have tried the attachment, there is the same problem

Can you help me ?
Thanks :)

---

### Post by Pitxyoki on 2007-08-06
> **Daddo said:**
> 
```
~/sqcam26$ make gamma.h
gcc -std=c99 -o makegamma -lm makegamma.c
makegamma.c:1:20: erreur: stdlib.h : Aucun fichier ou répertoire de ce type
makegamma.c:2:19: erreur: stdio.h : Aucun fichier ou répertoire de ce type
makegamma.c:3:18: erreur: math.h : Aucun fichier ou répertoire de ce type
makegamma.c: In function «main":
makegamma.c:6: erreur: «FILE" undeclared (first use in this function)
makegamma.c:6: erreur: (Each undeclared identifier is reported only once
makegamma.c:6: erreur: for each function it appears in.)
makegamma.c:6: erreur: «gammafile" undeclared (first use in this function)
makegamma.c:7: attention : implicit declaration of function «fopen"
makegamma.c:7: erreur: «NULL" undeclared (first use in this function)
makegamma.c:8: attention : implicit declaration of function «fprintf"
makegamma.c:8: attention : incompatible implicit declaration of built-in function «fprintf"
makegamma.c:8: erreur: «stderr" undeclared (first use in this function)
makegamma.c:9: attention : implicit declaration of function «exit"
makegamma.c:9: attention : incompatible implicit declaration of built-in function «exit"
makegamma.c:12: attention : incompatible implicit declaration of built-in function «fprintf"
makegamma.c:17: attention : implicit declaration of function «pow"
makegamma.c:17: attention : incompatible implicit declaration of built-in function «pow"
makegamma.c:20: attention : implicit declaration of function «fputc"
makegamma.c:30: attention : implicit declaration of function «fclose"
make: *** [makegamma] Erreur 1

```

(I use a french system, an "attention" is a warning :))


Oh, mais je sais... Et aussi un erreur est une "error"! :)

Did you do the first step on the HOW-TO?
```
$ sudo apt-get install gcc make cvs
```

---

### Post by GrinningNoodles on 2007-08-09
Hi, I'm new to Linux, so please forgive any stupid questions...  Like Daddo, I'm running feisty and I've had the following errors when trying make gamma.h

gcc -std=c99 -o makegamma -lm makegamma.c
makegamma.c:1:20: error: stdlib.h: No such file or directory
makegamma.c:2:19: error: stdio.h: No such file or directory
makegamma.c:3:18: error: math.h: No such file or directory
makegamma.c: In function ‘main’:
makegamma.c:6: error: ‘FILE’ undeclared (first use in this function)
makegamma.c:6: error: (Each undeclared identifier is reported only once
makegamma.c:6: error: for each function it appears in.)
makegamma.c:6: error: ‘gammafile’ undeclared (first use in this function)
makegamma.c:7: warning: implicit declaration of function ‘fopen’
makegamma.c:7: error: ‘NULL’ undeclared (first use in this function)
makegamma.c:8: warning: implicit declaration of function ‘fprintf’
makegamma.c:8: warning: incompatible implicit declaration of built-in function ‘fprintf’
makegamma.c:8: error: ‘stderr’ undeclared (first use in this function)
makegamma.c:9: warning: implicit declaration of function ‘exit’
makegamma.c:9: warning: incompatible implicit declaration of built-in function ‘exit’
makegamma.c:12: warning: incompatible implicit declaration of built-in function ‘fprintf’
makegamma.c:17: warning: implicit declaration of function ‘pow’
makegamma.c:17: warning: incompatible implicit declaration of built-in function ‘pow’
makegamma.c:20: warning: implicit declaration of function ‘fputc’
makegamma.c:30: warning: implicit declaration of function ‘fclose’
make: *** [makegamma] Error 1

I can't speak for Daddo, but I certainly did the first step - $ sudo apt-get install gcc make cvs

As I'm a newbie, I may well have missed something blindingly obvious, so please don't assume anything !
Thanks in advance for your help

---

### Post by GrinningNoodles on 2007-08-10
A friend was kind enough to help me sort this out, and my cam is now working (so courage to all who still try - it is possible !)
Unfortunately I didn't keep a record of what we did, sorry :(

---

### Post by Serax on 2007-08-13
hello this is my first post and i am an linux newbie. i am a windows power user and as some of you might have figured out we windows users are stubborn. anyway getting to the point have been working on this for a few days now and i am about to smash this little camera to bits... but i know i can because i will never find it agian un less i pay for shipping and handling on ebay and i know i would just endup trying to figure thisout down the line... any how i have been on linux about a week and i have figured some of it on my own. i understand most of it up until i get my first error when i  "make gamma.h" here is the output i got

makegamma.c:1:20: error: stdlib.h: No such file or directory
makegamma.c:2:19: error: stdio.h: No such file or directory
makegamma.c:3:18: error: math.h: No such file or directory
makegamma.c: In function ‘main’:
makegamma.c:6: error: ‘FILE’ undeclared (first use in this function)
makegamma.c:6: error: (Each undeclared identifier is reported only once
makegamma.c:6: error: for each function it appears in.)
makegamma.c:6: error: ‘gammafile’ undeclared (first use in this function)
makegamma.c:7: warning: implicit declaration of function ‘fopen’
makegamma.c:7: error: ‘NULL’ undeclared (first use in this function)
makegamma.c:8: warning: implicit declaration of function ‘fprintf’
makegamma.c:8: warning: incompatible implicit declaration of built-in function ‘fprintf’
makegamma.c:8: error: ‘stderr’ undeclared (first use in this function)
makegamma.c:9: warning: implicit declaration of function ‘exit’
makegamma.c:9: warning: incompatible implicit declaration of built-in function ‘exit’
makegamma.c:12: warning: incompatible implicit declaration of built-in function ‘fprintf’
makegamma.c:17: warning: implicit declaration of function ‘pow’
makegamma.c:17: warning: incompatible implicit declaration of built-in function ‘pow’
makegamma.c:20: warning: implicit declaration of function ‘fputc’
makegamma.c:30: warning: implicit declaration of function ‘fclose’
make: *** [makegamma] Error 1


and from there none of the instructions seem to work and all have errors if anyone out there would like to save a live from going insane please reply with some help or a push in the right direction i have no tryed easycam yet because i like to do some research before i install drivers and i heard this cam doesnt work well with easycam1/2 any help will be great

---

### Post by GrinningNoodles on 2007-08-13
I do remember that in the file usbvideo.h:

$ gedit usbvideo.h

We commented out the config.h line

//  #include <linux/config.h>
#include <linux/videodev.h>
#include <linux/usb.h>
#include <media/v4l2-dev.h>

as for the other directories, if I remember correctly we just created them, using md ?  (maybe someone who knows how to code properly could help here ?)

---

### Post by Pitxyoki on 2007-09-03
I'm sorry for the late reply, but I've been on vacation until today...
Have you tried
```
$ sudo apt-get install libc6-dev
```
?
I haven't investigated this very much yet, but something tells me this might be it. I'll be waiting for feedback. :)

---

### Post by qwer1234 on 2007-10-06
sorry! can someone halp me?
i'm stuck after the "make" command (all worked fine so far)

******Error*********
root@T23:/home/t23/sqcam26# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/t23/sqcam26 modules
make: *** /lib/modules/2.6.20-16-server/build: No such file or directory.  Stop.
make: *** [module] Error 2
**********Error**************

my system is a Ubuntu Server 7.04 with GUI :-) (windo$e newbies need gui)

***********dir
root@T23:/lib# cd modules
root@T23:/lib/modules# dir
2.6.20-15-server  2.6.20-16-generic  2.6.20-16-server
root@T23:/lib/modules# 
*************dir

can anyone help me????

thank's a lot

(i've tried hard-coding the "`uname -r`" in the sourcefile to "2.6.20-16-generic" (the only dir with a "build" folder)
but got errors with the compiled thing . .

---

### Post by Pitxyoki on 2007-10-06
Can you please show the output of:
```
$ ls -lp /lib/modules/*
```
and
```
$ ls -lp /usr/src/*
```
?

---

### Post by qwer1234 on 2007-10-06
> **Pitxyoki said:**
> Can you please show the output of:
```
$ ls -lp /lib/modules/*
```
and
```
$ ls -lp /usr/src/*
```
?

root@T23:/home/t23/sqcam26# ls -lp /lib/modules/*
/lib/modules/2.6.20-15-server:
total 1636
drwxr-xr-x  2 root root   4096 2007-10-04 21:48 initrd/
drwxr-xr-x 11 root root   4096 2007-10-04 21:48 kernel/
-rw-r--r--  1 root root 350325 2007-10-04 21:48 modules.alias
-rw-r--r--  1 root root     69 2007-10-04 21:48 modules.ccwmap
-rw-r--r--  1 root root 378063 2007-10-04 21:48 modules.dep
-rw-r--r--  1 root root    813 2007-10-04 21:48 modules.ieee1394map
-rw-r--r--  1 root root    806 2007-10-04 21:48 modules.inputmap
-rw-r--r--  1 root root  22147 2007-10-04 21:48 modules.isapnpmap
-rw-r--r--  1 root root     74 2007-10-04 21:48 modules.ofmap
-rw-r--r--  1 root root 262634 2007-10-04 21:48 modules.pcimap
-rw-r--r--  1 root root   1303 2007-10-04 21:48 modules.seriomap
-rw-r--r--  1 root root 152922 2007-10-04 21:48 modules.symbols
-rw-r--r--  1 root root 443096 2007-10-04 21:48 modules.usbmap

/lib/modules/2.6.20-16-generic:
total 0
lrwxrwxrwx 1 root root 40 2007-10-05 00:59 build -> /usr/src/linux-headers-2.6.20-16-generic/

/lib/modules/2.6.20-16-server:
total 1636
drwxr-xr-x  2 root root   4096 2007-10-05 01:44 initrd/
drwxr-xr-x 11 root root   4096 2007-10-05 01:44 kernel/
-rw-r--r--  1 root root 350810 2007-10-05 17:06 modules.alias
-rw-r--r--  1 root root     69 2007-10-05 17:06 modules.ccwmap
-rw-r--r--  1 root root 378340 2007-10-05 17:06 modules.dep
-rw-r--r--  1 root root    813 2007-10-05 17:06 modules.ieee1394map
-rw-r--r--  1 root root    806 2007-10-05 17:06 modules.inputmap
-rw-r--r--  1 root root  22147 2007-10-05 17:06 modules.isapnpmap
-rw-r--r--  1 root root     74 2007-10-05 17:06 modules.ofmap
-rw-r--r--  1 root root 262998 2007-10-05 17:06 modules.pcimap
-rw-r--r--  1 root root   1303 2007-10-05 17:06 modules.seriomap
-rw-r--r--  1 root root 152961 2007-10-05 17:06 modules.symbols
-rw-r--r--  1 root root 444001 2007-10-05 17:06 modules.usbmap

###########################################
t23@T23:~$ ls -lp /usr/src/*
/usr/src/linux-headers-2.6.20-16:
total 132
drwxr-xr-x 27 root root  4096 2007-10-05 00:59 arch/
drwxr-xr-x  2 root root  4096 2007-10-05 00:59 block/
drwxr-xr-x  2 root root  4096 2007-10-05 00:59 crypto/
drwxr-xr-x  9 root root  4096 2007-10-05 00:59 debian/
drwxr-xr-x 64 root root  4096 2007-10-05 00:59 drivers/
drwxr-xr-x 63 root root  4096 2007-10-05 00:59 fs/
drwxr-xr-x 43 root root  4096 2007-10-05 00:59 include/
drwxr-xr-x  2 root root  4096 2007-10-05 00:59 init/
drwxr-xr-x  2 root root  4096 2007-10-05 00:59 ipc/
drwxr-xr-x  5 root root  4096 2007-10-05 00:59 kernel/
drwxr-xr-x  5 root root  4096 2007-10-05 00:59 lib/
-rw-r--r--  1 root root    13 2007-09-23 22:14 linux-headers.revision
-rw-r--r--  1 root root 50528 2007-04-12 19:15 Makefile
drwxr-xr-x  2 root root  4096 2007-10-05 00:59 mm/
drwxr-xr-x 37 root root  4096 2007-10-05 00:59 net/
drwxr-xr-x  9 root root  4096 2007-10-05 00:59 scripts/
drwxr-xr-x  4 root root  4096 2007-10-05 00:59 security/
drwxr-xr-x 17 root root  4096 2007-10-05 00:59 sound/
drwxr-xr-x 13 root root  4096 2007-10-05 00:59 ubuntu/
drwxr-xr-x  2 root root  4096 2007-10-05 00:59 usr/

/usr/src/linux-headers-2.6.20-16-generic:
total 476
lrwxrwxrwx 1 root root     31 2007-10-05 00:59 arch -> ../linux-headers-2.6.20-16/arch/
lrwxrwxrwx 1 root root     32 2007-10-05 00:59 block -> ../linux-headers-2.6.20-16/block/
lrwxrwxrwx 1 root root     33 2007-10-05 00:59 crypto -> ../linux-headers-2.6.20-16/crypto/
lrwxrwxrwx 1 root root     34 2007-10-05 00:59 drivers -> ../linux-headers-2.6.20-16/drivers/
lrwxrwxrwx 1 root root     29 2007-10-05 00:59 fs -> ../linux-headers-2.6.20-16/fs/
drwxr-xr-x 4 root root   4096 2007-10-05 00:59 include/
lrwxrwxrwx 1 root root     31 2007-10-05 00:59 init -> ../linux-headers-2.6.20-16/init/
lrwxrwxrwx 1 root root     30 2007-10-05 00:59 ipc -> ../linux-headers-2.6.20-16/ipc/
lrwxrwxrwx 1 root root     33 2007-10-05 00:59 kernel -> ../linux-headers-2.6.20-16/kernel/
lrwxrwxrwx 1 root root     30 2007-10-05 00:59 lib -> ../linux-headers-2.6.20-16/lib/
-rw-r--r-- 1 root root  50527 2007-09-23 22:29 Makefile
lrwxrwxrwx 1 root root     29 2007-10-05 00:59 mm -> ../linux-headers-2.6.20-16/mm/
-rw-r--r-- 1 root root 414274 2007-09-23 22:27 Module.symvers
lrwxrwxrwx 1 root root     30 2007-10-05 00:59 net -> ../linux-headers-2.6.20-16/net/
drwxr-xr-x 9 root root   4096 2007-10-05 00:59 scripts/
lrwxrwxrwx 1 root root     35 2007-10-05 00:59 security -> ../linux-headers-2.6.20-16/security/
lrwxrwxrwx 1 root root     32 2007-10-05 00:59 sound -> ../linux-headers-2.6.20-16/sound/
lrwxrwxrwx 1 root root     33 2007-10-05 00:59 ubuntu -> ../linux-headers-2.6.20-16/ubuntu/
lrwxrwxrwx 1 root root     30 2007-10-05 00:59 usr -> ../linux-headers-2.6.20-16/usr/
t23@T23:~$ 
#######################################

---

### Post by Pitxyoki on 2007-10-06
Try to
```
# apt-get install linux-headers-2.6.20-16-server
```
...please tell me if this did it.

---

### Post by qwer1234 on 2007-10-06
> **Pitxyoki said:**
> Try to
```
# apt-get install linux-headers-2.6.20-16-server
```
...please tell me if this did it.
 thankyou for the help so far, but it didn't worked:

```

root@T23:/home/t23/sqcam26# apt-get install linux-headers-2.6.20-16-server
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Die folgenden NEUEN Pakete werden installiert:
  linux-headers-2.6.20-16-server
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen 844kB Archive geholt werden.
Nach dem Auspacken werden 7262kB Plattenplatz zusätzlich benutzt.
Hole:1 http://security.ubuntu.com feisty-security/main linux-headers-2.6.20-16-server 2.6.20-16.32 [844kB]
Es wurden 844kB in 3s geholt (280kB/s)                 
Wähle vormals abgewähltes Paket linux-headers-2.6.20-16-server.
(Lese Datenbank ... 122249 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke linux-headers-2.6.20-16-server (aus .../linux-headers-2.6.20-16-server_2.6.20-16.32_i386.deb) ...
Richte linux-headers-2.6.20-16-server ein (2.6.20-16.32) ...
root@T23:/home/t23/sqcam26# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/t23/sqcam26 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-server'
  CC [M]  /home/t23/sqcam26/sq905.o
In file included from /home/t23/sqcam26/sq905.c:65:
/home/t23/sqcam26/usbvideo.h:19:26: error: linux/config.h: No such file or directory
/home/t23/sqcam26/sq905.c: In function &#8216;sqcam_open&#8217;:
/home/t23/sqcam26/sq905.c:908: warning: ISO C90 forbids mixed declarations and code
/home/t23/sqcam26/sq905.c: In function &#8216;read_frame&#8217;:
/home/t23/sqcam26/sq905.c:1071: warning: ISO C90 forbids mixed declarations and code
/home/t23/sqcam26/sq905.c: In function &#8216;sqcam_mmap&#8217;:
/home/t23/sqcam26/sq905.c:1162: warning: ISO C90 forbids mixed declarations and code
make[2]: *** [/home/t23/sqcam26/sq905.o] Error 1
make[1]: *** [_module_/home/t23/sqcam26] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-server'
make: *** [module] Error 2

```

i used the sqcam26-new.tar.gz as source!

---

### Post by Pitxyoki on 2007-10-06
I'm seeing that I will have to update the howto...
Edit the file usbvideo.h and comment line 19:
```
// #include <linux/config.h>
```
...as suggested [here](http://ubuntuforums.org/showpost.php?p=3182631&postcount=19).

---

### Post by qwer1234 on 2007-10-07
it finaly work's!!! where's the "you are a hero!"-button? :)

:guitar:

thankyou

now i use camorama -M +filter Color Corection and all works fine!!
now i can use my camera as webcam . .  your just awesome!!!!

---

### Post by product of time on 2007-11-07
Thank you very much!!

I finally got it to work.

**NOTE:**
This also worked under Puppy 3.01 (shard).
On puppy, make sure to place the kernel_src_301.sfs in the /mnt/home/ directory;  run BootManager then add it.  Then you can restart your computer.
Get the sqcam26-new.tar.bz2.
The rest is the same procedure.

---

### Post by knap on 2007-11-14
How can I fix this error ?

```

############################################################

knap@Knap:~$ sudo xawtv
[sudo] password for knap:
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-386)
xinerama 0: 1152x864+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
knap@Knap:~$

##########################################################################

knap@Knap:~/sqcam26$ kate Makefile

# makefile for sq905 for 2.6 kernels
# 

MODULE_NAME := sqcam

#KERNEL_DIR := /usr/src/linux/
KERNEL_DIR := /lib/modules/`uname -r`/build
#KERNEL_DIR := /space/aab/build/linux-2.6.5-7.111

###########################################################################

knap@Knap:~/sqcam26$ kate sq905.c                       


 #  line 1183  

//#ifdef HAS_REMAP_PAGE_RANGE
//		if (remap_page_range(vma, start, page, PAGE_SIZE,
//                     PAGE_SHARED)) {
//#else
		if (remap_pfn_range(vma, start, page >> PAGE_SHIFT, PAGE_SIZE,
                    PAGE_SHARED)) {
//#endif
			up(&cam->busy_lock);
			return -EAGAIN;
		}

# line 1228 

//        .owner          = THIS_MODULE,

###########################################################

knap@Knap:~/sqcam26$ kate usbvideo.h


/* #include <linux/config.h> */
#include <linux/videodev.h>
#include <linux/usb.h>
#include <media/v4l2-dev.h>

###########################################################################

knap@Knap:~$ sudo modprobe -r sqcam
[sudo] password for knap:
FATAL: Module sqcam not found.
knap@Knap:~$ sudo modprobe sqcam
FATAL: Module sqcam not found.
knap@Knap:~$ camorama -M

Error : Colud not connect to video device (dev/video0). pleace check connection.

######################################################################

knap@Knap:~$ gphoto2 --version
gphoto2 2.3.1

Copyright (c) 2000-2006 Lutz Mueller and others

gphoto2 comes with NO WARRANTY, to the extent permitted by law. You may
redistribute copies of gphoto2 under the terms of the GNU General Public
License. For more information about these matters, see the files named COPYING.

This version of gphoto2 is using the following software versions and options:
gphoto2         2.3.1          gcc, popt(m), exif, cdk, no aa, jpeg, readline
libgphoto2      2.4.0          gcc, ltdl, EXIF
libgphoto2_port 0.8.0          gcc, ltdl, USB, serial without locking


knap@Knap:~$ gtkam --version
0.1.14

knap@Knap:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-386)

###########################################################################      

knap@Knap:~$ ls -lp /lib/modules/*
/lib/modules/2.6.22-14-386:
total 1580
lrwxrwxrwx  1 root root     36 2007-11-14 10:49 build -> /usr/src/linux-headers-2.6.22-14-386/
drwxr-xr-x  2 root root   4096 2007-11-12 02:01 initrd/
drwxr-xr-x 10 root root   4096 2007-11-12 02:01 kernel/
drwxr-xr-x  2 root root   4096 2007-11-14 00:32 madwifi/
-rw-r--r--  1 root root 342963 2007-11-14 00:32 modules.alias
-rw-r--r--  1 root root     69 2007-11-14 00:32 modules.ccwmap
-rw-r--r--  1 root root 360089 2007-11-14 00:32 modules.dep
-rw-r--r--  1 root root    813 2007-11-14 00:32 modules.ieee1394map
-rw-r--r--  1 root root    527 2007-11-14 00:32 modules.inputmap
-rw-r--r--  1 root root  17560 2007-11-14 00:32 modules.isapnpmap
-rw-r--r--  1 root root     74 2007-11-14 00:32 modules.ofmap
-rw-r--r--  1 root root 274373 2007-11-14 00:32 modules.pcimap
-rw-r--r--  1 root root   1345 2007-11-14 00:32 modules.seriomap
-rw-r--r--  1 root root 163544 2007-11-14 00:32 modules.symbols
-rw-r--r--  1 root root 400018 2007-11-14 00:32 modules.usbmap
drwxr-xr-x  2 root root    420 2007-11-14 17:57 volatile/

/lib/modules/2.6.22-14-generic:
total 1740
lrwxrwxrwx  1 root root     40 2007-10-27 09:25 build -> /usr/src/linux-headers-2.6.22-14-generic/
drwxr-xr-x  2 root root   4096 2007-10-27 09:06 initrd/
drwxr-xr-x 10 root root   4096 2007-10-27 09:06 kernel/
drwxr-xr-x  2 root root   4096 2007-11-14 00:32 madwifi/
-rw-r--r--  1 root root 365097 2007-11-14 00:33 modules.alias
-rw-r--r--  1 root root     69 2007-11-14 00:33 modules.ccwmap
-rw-r--r--  1 root root 398608 2007-11-14 00:33 modules.dep
-rw-r--r--  1 root root    813 2007-11-14 00:33 modules.ieee1394map
-rw-r--r--  1 root root    527 2007-11-14 00:33 modules.inputmap
-rw-r--r--  1 root root  17714 2007-11-14 00:33 modules.isapnpmap
-rw-r--r--  1 root root     74 2007-11-14 00:33 modules.ofmap
-rw-r--r--  1 root root 272826 2007-11-14 00:33 modules.pcimap
-rw-r--r--  1 root root   1345 2007-11-14 00:33 modules.seriomap
-rw-r--r--  1 root root 170501 2007-11-14 00:33 modules.symbols
-rw-r--r--  1 root root 481106 2007-11-14 00:33 modules.usbmap
drwxr-xr-x 10 root root   4096 2007-10-27 09:06 ubuntu/
drwxr-xr-x  2 root root   4096 2007-11-14 00:32 volatile/

/lib/modules/2.6.22-14-server:
total 0
lrwxrwxrwx 1 root root 39 2007-11-14 16:49 build -> /usr/src/linux-headers-2.6.22-14-server/
knap@Knap:~$

#######################################################################

-rw-r--r--  1 root root   157980 2007-11-02 02:21 /usr/src/fglrx-kernel-source.tar.gz
-rw-r--r--  1 root root 45350890 2007-10-15 03:26 /usr/src/linux-source-2.6.22.tar.bz2
-rw-r--r--  1 root root   165454 2007-03-29 19:40 /usr/src/spca5xx-source.tar.bz2

/usr/src/linux-headers-2.6.22-14:
total 128
drwxr-xr-x 28 root root  4096 2007-10-27 09:25 arch/
drwxr-xr-x  2 root root  4096 2007-10-27 09:25 block/
drwxr-xr-x  2 root root  4096 2007-10-27 09:25 crypto/
drwxr-xr-x  7 root root  4096 2007-10-27 09:25 Documentation/
drwxr-xr-x 66 root root  4096 2007-10-27 09:25 drivers/
drwxr-xr-x 62 root root  4096 2007-10-27 09:25 fs/
drwxr-xr-x 43 root root  4096 2007-10-27 09:25 include/
drwxr-xr-x  2 root root  4096 2007-10-27 09:25 init/
drwxr-xr-x  2 root root  4096 2007-10-27 09:25 ipc/
-rw-r--r--  1 root root  1530 2007-07-09 01:32 Kbuild
drwxr-xr-x  5 root root  4096 2007-10-27 09:25 kernel/
drwxr-xr-x  5 root root  4096 2007-10-27 09:25 lib/
-rw-r--r--  1 root root 50403 2007-10-15 00:33 Makefile
drwxr-xr-x  2 root root  4096 2007-10-27 09:25 mm/
drwxr-xr-x 41 root root  4096 2007-10-27 09:25 net/
drwxr-xr-x  9 root root  4096 2007-10-27 09:25 scripts/
drwxr-xr-x  4 root root  4096 2007-10-27 09:25 security/
drwxr-xr-x 18 root root  4096 2007-10-27 09:25 sound/
drwxr-xr-x  2 root root  4096 2007-10-27 09:25 usr/

/usr/src/linux-headers-2.6.22-14-386:
total 428
drwxr-xr-x 3 root root   4096 2007-11-14 10:49 arch/
lrwxrwxrwx 1 root root     32 2007-11-14 10:49 block -> ../linux-headers-2.6.22-14/block/
lrwxrwxrwx 1 root root     33 2007-11-14 10:49 crypto -> ../linux-headers-2.6.22-14/crypto/
lrwxrwxrwx 1 root root     40 2007-11-14 10:49 Documentation -> ../linux-headers-2.6.22-14/Documentation/
lrwxrwxrwx 1 root root     34 2007-11-14 10:49 drivers -> ../linux-headers-2.6.22-14/drivers/
lrwxrwxrwx 1 root root     29 2007-11-14 10:49 fs -> ../linux-headers-2.6.22-14/fs/
drwxr-xr-x 5 root root   4096 2007-11-14 10:49 include/
lrwxrwxrwx 1 root root     31 2007-11-14 10:49 init -> ../linux-headers-2.6.22-14/init/
lrwxrwxrwx 1 root root     30 2007-11-14 10:49 ipc -> ../linux-headers-2.6.22-14/ipc/
lrwxrwxrwx 1 root root     33 2007-11-14 10:49 Kbuild -> ../linux-headers-2.6.22-14/Kbuild
lrwxrwxrwx 1 root root     33 2007-11-14 10:49 kernel -> ../linux-headers-2.6.22-14/kernel/
lrwxrwxrwx 1 root root     30 2007-11-14 10:49 lib -> ../linux-headers-2.6.22-14/lib/
lrwxrwxrwx 1 root root     35 2007-11-14 10:49 Makefile -> ../linux-headers-2.6.22-14/Makefile
lrwxrwxrwx 1 root root     29 2007-11-14 10:49 mm -> ../linux-headers-2.6.22-14/mm/
-rw-r--r-- 1 root root 420774 2007-10-15 03:37 Module.symvers
lrwxrwxrwx 1 root root     30 2007-11-14 10:49 net -> ../linux-headers-2.6.22-14/net/
drwxr-xr-x 6 root root   4096 2007-11-14 10:49 scripts/
lrwxrwxrwx 1 root root     35 2007-11-14 10:49 security -> ../linux-headers-2.6.22-14/security/
lrwxrwxrwx 1 root root     32 2007-11-14 10:49 sound -> ../linux-headers-2.6.22-14/sound/
lrwxrwxrwx 1 root root     30 2007-11-14 10:49 usr -> ../linux-headers-2.6.22-14/usr/

/usr/src/linux-headers-2.6.22-14-generic:
total 432
drwxr-xr-x 3 root root   4096 2007-10-27 09:25 arch/
lrwxrwxrwx 1 root root     32 2007-10-27 09:25 block -> ../linux-headers-2.6.22-14/block/
lrwxrwxrwx 1 root root     33 2007-10-27 09:25 crypto -> ../linux-headers-2.6.22-14/crypto/
lrwxrwxrwx 1 root root     40 2007-10-27 09:25 Documentation -> ../linux-headers-2.6.22-14/Documentation/
lrwxrwxrwx 1 root root     34 2007-10-27 09:25 drivers -> ../linux-headers-2.6.22-14/drivers/
lrwxrwxrwx 1 root root     29 2007-10-27 09:25 fs -> ../linux-headers-2.6.22-14/fs/
drwxr-xr-x 5 root root   4096 2007-10-27 09:25 include/
lrwxrwxrwx 1 root root     31 2007-10-27 09:25 init -> ../linux-headers-2.6.22-14/init/
lrwxrwxrwx 1 root root     30 2007-10-27 09:25 ipc -> ../linux-headers-2.6.22-14/ipc/
lrwxrwxrwx 1 root root     33 2007-10-27 09:25 Kbuild -> ../linux-headers-2.6.22-14/Kbuild
lrwxrwxrwx 1 root root     33 2007-10-27 09:25 kernel -> ../linux-headers-2.6.22-14/kernel/
lrwxrwxrwx 1 root root     30 2007-10-27 09:25 lib -> ../linux-headers-2.6.22-14/lib/
lrwxrwxrwx 1 root root     35 2007-10-27 09:25 Makefile -> ../linux-headers-2.6.22-14/Makefile
lrwxrwxrwx 1 root root     29 2007-10-27 09:25 mm -> ../linux-headers-2.6.22-14/mm/
-rw-r--r-- 1 root root 424317 2007-10-15 03:41 Module.symvers
lrwxrwxrwx 1 root root     30 2007-10-27 09:25 net -> ../linux-headers-2.6.22-14/net/
drwxr-xr-x 6 root root   4096 2007-10-27 09:25 scripts/
lrwxrwxrwx 1 root root     35 2007-10-27 09:25 security -> ../linux-headers-2.6.22-14/security/
lrwxrwxrwx 1 root root     32 2007-10-27 09:25 sound -> ../linux-headers-2.6.22-14/sound/
lrwxrwxrwx 1 root root     30 2007-10-27 09:25 usr -> ../linux-headers-2.6.22-14/usr/

/usr/src/linux-headers-2.6.22-14-server:
total 432
drwxr-xr-x 3 root root   4096 2007-11-14 16:49 arch/
lrwxrwxrwx 1 root root     32 2007-11-14 16:49 block -> ../linux-headers-2.6.22-14/block/
lrwxrwxrwx 1 root root     33 2007-11-14 16:49 crypto -> ../linux-headers-2.6.22-14/crypto/
lrwxrwxrwx 1 root root     40 2007-11-14 16:49 Documentation -> ../linux-headers-2.6.22-14/Documentation/
lrwxrwxrwx 1 root root     34 2007-11-14 16:49 drivers -> ../linux-headers-2.6.22-14/drivers/
lrwxrwxrwx 1 root root     29 2007-11-14 16:49 fs -> ../linux-headers-2.6.22-14/fs/
drwxr-xr-x 5 root root   4096 2007-11-14 16:49 include/
lrwxrwxrwx 1 root root     31 2007-11-14 16:49 init -> ../linux-headers-2.6.22-14/init/
lrwxrwxrwx 1 root root     30 2007-11-14 16:49 ipc -> ../linux-headers-2.6.22-14/ipc/
lrwxrwxrwx 1 root root     33 2007-11-14 16:49 Kbuild -> ../linux-headers-2.6.22-14/Kbuild
lrwxrwxrwx 1 root root     33 2007-11-14 16:49 kernel -> ../linux-headers-2.6.22-14/kernel/
lrwxrwxrwx 1 root root     30 2007-11-14 16:49 lib -> ../linux-headers-2.6.22-14/lib/
lrwxrwxrwx 1 root root     35 2007-11-14 16:49 Makefile -> ../linux-headers-2.6.22-14/Makefile
lrwxrwxrwx 1 root root     29 2007-11-14 16:49 mm -> ../linux-headers-2.6.22-14/mm/
-rw-r--r-- 1 root root 424317 2007-10-15 03:44 Module.symvers
lrwxrwxrwx 1 root root     30 2007-11-14 16:49 net -> ../linux-headers-2.6.22-14/net/
drwxr-xr-x 6 root root   4096 2007-11-14 16:49 scripts/
lrwxrwxrwx 1 root root     35 2007-11-14 16:49 security -> ../linux-headers-2.6.22-14/security/
lrwxrwxrwx 1 root root     32 2007-11-14 16:49 sound -> ../linux-headers-2.6.22-14/sound/
lrwxrwxrwx 1 root root     30 2007-11-14 16:49 usr -> ../linux-headers-2.6.22-14/usr/
knap@Knap:~$    

###############################################################

```

---

### Post by knap on 2007-11-15
[COLOR="Red"][SIZE="3"]:KS  :KS  I love linux  :KS  :KS 

Thanks to exist


:guitar:        :guitar:             :guitar:        
[/SIZE]
[/COLOR]

---

### Post by Carl Foxmarten on 2007-11-20
Thanks for the HOWTO, it helped!
The only thing that didn't work was camorama, when I used the -M option nothing showed up, just a black window.

I tried using moTV and it worked!

Thanks again!

---

### Post by the_monster on 2008-01-15
I have a Tek2go Mini Digital Camera and in Sidux it works fine to download any pics, but i cant get to work as webcam. I even compiled SQCAM26 hoping it might be able to use, but no. Anyone can think how to change the driver to work this camera. Below is the output from lsusb. The underlined part is the camera:

lsusb
Bus 003 Device 001: ID 0000:0000
_Bus 002 Device 004: ID 2770:905c NHJ, Ltd Che-Ez Snap SNAP-U/Digigr8/Soundstar TDC-35_
Bus 002 Device 002: ID 04b8:080c Seiko Epson Corp. ME100
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


Thanks in advance.

---

### Post by Pitxyoki on 2008-01-15
The best info I could find was this: [http://www.qbik.ch/usb/devices/showdev.php?id=4015](http://www.qbik.ch/usb/devices/showdev.php?id=4015) .

Also, on this forum there are some more requests for that webcam. Sorry, it seems to me you're out of luck.

---

### Post by Pitxyoki on 2008-02-04
To record a movie with xawtv:

First, start xawtv. If the image is displaying ugly colors, close xawtv and restart it until you get a good display. My camera must be well illuminated to capture good colours. Sometimes it shows everything in a pink-gradient if it is under a shadow or on a badly illuminated room.

With the xawtv window on focus, press R and set these options:

```

movie driver : Microsoft AVI (RIFF) format
movie/images filename
  something.avi
audio format : no sound
sample rate  : 44100
video format : JPEG (JFIF)
frames/sec   : 12.0 fps
frame size  : 384x288
```
Note: The "frame size" is adjustable by resizing the video window. Keep in mind that this will only produce a zoomed-in/out image for what you see while recording. The final image will have a 320x240 resolution.


Then just click "start/stop recording". A file named "something.avi" will be placed on the directory from where you started xawtv or on your home directory if you started it from the Gnome menu.

You can now watch your own movies with Totem or mplayer! Yeepi!

I haven't tested this under Windows yet. If someone could tell me if this method creates Windows-viewable movies, I'd appreciate it.

---

### Post by uluman on 2008-02-06
Thanks for the writeup Pitxyoki, I was able to get the camera working on RHEL4.  I have the same camera:
ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera
I use motion for my webcam software, but streamer/xawtv works nicely too.

I wonder if it is possible to get 640x480 output from the webcam function?  I can take photos at that resolution and grab them via gphoto2, but webcam only seems to do 320x240.  I tried changing sq905.c to support 640x480 but only got garbled images.  Maybe the hardware doesn't allow it (or, more likely, I didn't modify the code properly :) )  Any idea?

---

### Post by Pitxyoki on 2008-02-06
Thanks for the input.

Unfortunately, I think you are out of luck with other resolutions.
At least under Windows, the webcam has only one resolution possible. The possibilities available there are just zoom-in/outs of that same resolution.

I believe this must be an hardware limitation.

---

### Post by uluman on 2008-02-07
:-k  hmmm, oh well, you are probably right that it is a hardware limitation.

---

### Post by LOCOSLAW_PL on 2008-03-27
Ubuntu 8.04 LTS Beta - sqcam works. (kernel 2.6.24-12)

Ekiga - OK
aMSN - OK
Skype - Green lines in test (preview).

---

### Post by GothPanda on 2008-04-01
> **Pitxyoki said:**
> I'm sorry I can't help you better, but I really have not much experience on any other distro/version of linux, but I can show you the output I get so you can see where there is something different:

```
$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/luis/Downloads/Setups/Webcam/cvs/sqcam26 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-28-686'
  CC [M]  /home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sq905.o
/home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sq905.c: In function ‘sqcam_open’:
/home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sq905.c:908: warning: ISO C90 forbids mixed declarations and code
/home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sq905.c: In function ‘read_frame’:
/home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sq905.c:1071: warning: ISO C90 forbids mixed declarations and code
/home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sq905.c: In function ‘sqcam_mmap’:
/home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sq905.c:1162: warning: ISO C90 forbids mixed declarations and code
  LD [M]  /home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sqcam.o
  Building modules, stage 2.
  MODPOST
  CC      /home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sqcam.mod.o
  LD [M]  /home/luis/Downloads/Setups/Webcam/cvs/sqcam26/sqcam.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-28-686'
$
```

It seems that the error points at line 1228...
```
/home/tzi/sqcam26/sq905.c:1228: error: unknown field ‘owner’ specified in initializer
/home/tzi/sqcam26/sq905.c:1228: warning: initialization from incompatible pointer type
make[2]: *** [/home/tzi/sqcam26/sq905.o] Error 1
make[1]: *** [_module_/home/tzi/sqcam26] Error 2
```

I absolutely can't tell you what may be the problem there, as I do not have that much deep knowledge about the Linux kernel.
This may be related to something(s?) that has(ve?) changed in the kernel and the modules may not be adapted to that, but I'm not sure... Anyway, in a few days (or weeks, depending on my work.. :-s) I'm going to try to check this on a Debian machine, which currently is running a 2.6.18 kernel.
Please tell me if you can make it to work.

**P.S.- Has anyone else been able to make this camera work?**

I had the same problem, but it's easily fixable.  If you downloaded the files through cvs, then the line numbers have changed.  There are two places where .owner exists in sq905.c, and both must be commented out.  All done!  ^.^

---

### Post by Pitxyoki on 2008-04-01
> **GothPanda said:**
> I had the same problem, but it's easily fixable.  If you downloaded the files through cvs, then the line numbers have changed.  There are two places where .owner exists in sq905.c, and both must be commented out.  All done!  ^.^

Please read the posts following that one. That issue has been solved and the solution is already in the HOWTO.

---

### Post by GothPanda on 2008-04-01
> **Pitxyoki said:**
> Please read the posts following that one. That issue has been solved and the solution is already in the HOWTO.

Sorry...  I tend to not see the other pages in forums...

But, I do have a similar problem to another post on another page, and the fix isn't helping me...

make -C /lib/modules/`uname -r`/build SUBDIRS=/home/hari/sqcam26 modules
make[1]: Entering directory '/lib/modules/2.6.22-14-server/build'
make[1]: *** No rule to make target 'modules'. Stop.
make[1]: Leaving directory '/lib/modules/2.6.22-14-server/build'
make: *** [module] Error 2

I tried to install the linux headers with apt-get, substituting in my kernel version number, and it still won't run make.  Any suggestions?

---

### Post by Pitxyoki on 2008-04-01
Can you tell me the result of
```
$ echo `uname -r`
```
?

---

### Post by GothPanda on 2008-04-02
> **Pitxyoki said:**
> Can you tell me the result of
```
$ echo `uname -r`
```
?

2.6.22-14-server

I tried replacing that in the instructions for the other problem like this for downloading the linux headers, but it didn't fix the problem...

---

### Post by Pitxyoki on 2008-04-03
Does
```
sudo apt-get install linux-headers-`uname -r`
```
install anything or does it say it is already installed? And... Are you using a server on the computer where that cam is connected to?

---

### Post by GothPanda on 2008-04-04
> **Pitxyoki said:**
> Does
```
sudo apt-get install linux-headers-`uname -r`
```
install anything or does it say it is already installed? And... Are you using a server on the computer where that cam is connected to?

Already did that. And, I'm trying to put the cam on my desktop that's running server.  It works fine on my laptop that's running 7.10 regular.

---

### Post by Pitxyoki on 2008-04-04
It can work fine using the kernel for servers, but if your machine is another architecture, it can work better if you use the optimized kernel for it.
Can you please show the output of
```
uname -m
```
(it's an **m** this time),
```
ls /lib/modules
```
and ```
apt-cache policy linux-image-server linux-ubuntu-modules-2.6.22-14-server
```?

---

### Post by GothPanda on 2008-04-05
> **Pitxyoki said:**
> It can work fine using the kernel for servers, but if your machine is another architecture, it can work better if you use the optimized kernel for it.
Can you please show the output of
```
uname -m
```
(it's an **m** this time),
```
ls /lib/modules
```
and ```
apt-cache policy linux-image-server linux-ubuntu-modules-2.6.22-14-server
```?

```

hari@WhiteMage:~/sqcam26$ uname -m
i686
hari@WhiteMage:~/sqcam26$ ls /lib/modules
[COLOR="Blue"]2.6.22-14-server[/COLOR]
hari@WhiteMage:~/sqcam26$ apt-cache policy linux-image-server linux-ubuntu-modules-2.6.22-14-server
linux-image-server:
   Installed: 2.6.22.14.21
   Candidate: 2.6.22.14.21
   Version table:
  *** 2.6.22.14.21 0
            500 http://us.archive.ubuntu.com gutsy/main Packages
            100 /var/lib/dpkg/status
linux-ubuntu-modules-2.6.22-14-server:
   Installed: 2.6.22.14.37
   Candidate:  2.6.22.14.37
   Version table:
  ***  2.6.22.14.37 0
            500 http://us.archive.ubuntu.com gutsy/main Packages
            100 /var/lib/dpkg/status

```

I made sure that the one output was blue, cause that's the ONLY thing that's ever come out in color on this console that I've seen...

EDIT:  GOT IT WORKING!

Had to change the variable KERNEL_DIR in the Makefile to /usr/src/linux-headers-`uname -r`, because I don't have the headers installed to /lib/modules/`uname -r`.

And, it appears to be working!  It compiled at least. Still getting the programs to test it out...

---

### Post by Pitxyoki on 2008-04-05
:) that coloured line is normal when the 'ls' command is aliased with the '--color' parameter. If you do 'ls' on your home folder, you will probably see many colors for the many different files you have there.

Anyway, I also saw [this post](http://ubuntuforums.org/showthread.php?p=758579#post758579), but I was wondering why did the server modules not go to the normal directory as the modules for other architectures do. I was thinking of missing packages, but as it seems, you have everything installed... Only to a different directory than usual.

EDIT: Now that I see it on my computer, the '/lib/modules/`uname -r`/build' directory is just a link to the /usr/src/linux-headers-`uname -r` directory. So in the end the only thing that's missing there is a link. It works both ways, so you can just change sqcam's Makefile as you did.


But still about your computer's architecture: are you running a server or was that the kernel that Ubuntu installed by default? If you aren't, maybe you can get better performance (and sometimes compatibility) if you used the i686 kernel.

---

### Post by Kerosh on 2008-04-05
hey i have a problem iv done most of it i think but when i try to do the last bit it wont make the directory :S 
```
kerosh@kerosh-desktop:/driverwebcam/sqcam26$ make gamma.h
make: `gamma.h' is up to date.
kerosh@kerosh-desktop:/driverwebcam/sqcam26$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/driverwebcam/sqcam26 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /driverwebcam/sqcam26/sq905.o
/driverwebcam/sqcam26/sq905.c: In function ‘sqcam_open’:
/driverwebcam/sqcam26/sq905.c:908: warning: ISO C90 forbids mixed declarations and code
/driverwebcam/sqcam26/sq905.c: In function ‘read_frame’:
/driverwebcam/sqcam26/sq905.c:1071: warning: ISO C90 forbids mixed declarations and code
/driverwebcam/sqcam26/sq905.c: In function ‘sqcam_mmap’:
/driverwebcam/sqcam26/sq905.c:1162: warning: ISO C90 forbids mixed declarations and code
  LD [M]  /driverwebcam/sqcam26/sqcam.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /driverwebcam/sqcam26/sqcam.mod.o
  LD [M]  /driverwebcam/sqcam26/sqcam.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
kerosh@kerosh-desktop:/driverwebcam/sqcam26$ sudo mkdir /lib/modules/`uname -r`/kernel/drivers/usb/media
[sudo] password for kerosh:
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/kernel/drivers/usb/media': File exists
kerosh@kerosh-desktop:/driverwebcam/sqcam26$ 

```

pleasee help

---

### Post by Pitxyoki on 2008-04-06
There's no problem with that error. It just means that you are trying to create a directory that already exists. Just keep following the HOWTO and ignore that. :)

---

### Post by kilgota on 2008-04-11
> **uluman said:**
> Thanks for the writeup Pitxyoki, I was able to get the camera working on RHEL4.  I have the same camera:
ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera
I use motion for my webcam software, but streamer/xawtv works nicely too.

I wonder if it is possible to get 640x480 output from the webcam function?  I can take photos at that resolution and grab them via gphoto2, but webcam only seems to do 320x240.  I tried changing sq905.c to support 640x480 but only got garbled images.  Maybe the hardware doesn't allow it (or, more likely, I didn't modify the code properly :) )  Any idea?

Yes, it is possible to change the resolution. This has to be done by adding a digit in the USB string which is sent down to the camera as the capture command. Go and read libgphoto2/camlibs/sq905/README, and if you have one of the newer cameras then go and read libgphoto2/camlibs/digigr8/README.  For both kinds of cameras, the same capture function is also used for webcam mode which gets used in the Gphoto driver to capture one single photo. 

This resolution changing feature for capture is incidentally not used in any of the OEM drivers for any of these cameras and is otherwise undocumented, except that I discovered it. Unfortunately, right now it is only implemented if you go back and edit one line of code in the driver library (either in libgphoto2, or in the module, as the case may be), and re-compile and re-install same. However, it is possible to do it. Keep in mind that it will slow down your frame rate, though,  to switch from 320x240 to 640x480, and the frame rate for these cameras in webcam mode is not very fast in any case. 

Incidentally, I am the author and maintainer of the two above mentioned camera driver libraries in libgphoto2. I am not involved in the sqcam project at all; when those guys started it I shared a lot of information with them to help them, but I told them that I have already enough to do in the Gphoto project. We are friends, but I am not involved in their project. I do subscribe to their mailing list, where I saw a reference to this thread, and then I saw this question. 

Final remarks: The SQ905 cameras and the SQ905C cameras are similar, but not identical. The USB command  structures are for them are similar but different. The support for these two models of cameras is thus different, too. 

Also these cameras are at this point fully supported as still cameras in libgphoto2. The webcam functionality however uses sqcam not the Gphoto drivers. As far as I know, some of the functions which are used in both circumstances (decompression algorithms, for example) still need to be ported over to sqcam. 

Theodore Kilgore (from the Gphoto developer team)

---

### Post by kilgota on 2008-04-11
Replying to myself, but the previous post did not contain all of the information. The excuse: I was at work and thus not at the computer which has all the gphoto stuff on it. So here is the info on changing the resolution:

1. Obviously, the camera has to support the resolution that you want. For example, a camera with max resolution 352x288 cannot be forced to give 640x480 while doing capture. However, a camera which will do 640x480 as a still camera can be asked to do capture at that resolution, too. 

2. For the SQ905C cameras and the other cameras which are supported by libgphoto2/camlibs/digigr8, the instructions about how to change the resolution are given in the README file. But in any case, in the capture command there is the string 0x1440. The 0x40 part is the command to capture, and the 0x14 part is the width setting in hex, divided by 0x10. Thus, since 320 = 0x140, this means to do capture at width=320. If you want to capture at width 640=0x280, then change this to 0x2840 and re-compile the camera driver. However, if your camera will not do 640x480 in still camera mode, then you do have a hardware limitation, so this will not work. That is one of the reasons why I did not ever put this into code, that it will work for some of the cameras and not for others. 

3. For the old SQ905 cameras (which at this point are no longer being manufactured, the chip being discontinued and superseded by the 905C chip) I see on checking that I did not provide the instructions. So here they are. If one looks in libgphoto2/camlibs/sq905/sq905.h then there is 

#define CAPTURE 0x61

Here, the "6" is the instruction to capture, and the "1" provides the resolution option. I forget exactly what works, but you can try various values instead of 1. I think I recall that 0x62 will give 640x460, but I forget exactly what will do what. At any rate, 0x60, 0x61, 0x62, 0x63 and perhaps 0x64 will give different resolution settings for capture. IIRC the settings are something like 120x80, 160x120, 320x240, 640x280, possibly also 176x144 and 352x288. So go ahead and experiment. Again, it depends on what your camera will do. If it maxes out at 352x288 then clearly it will not do 640x480. Also some of the choices above may also depend on the max resolution setting of the camera, and will not be available for a particular camera. 

Hope this helps anyone who is curious about the matter. Probably, this functionality will never make it into the sq905 driver in gphoto, but the information ought to be more public. 

Theodore Kilgore

---

### Post by LOCOSLAW_PL on 2008-04-27
In Ubuntu 8.04 Stable (kernel 2.6.24.16) - don't work.

Everything is okay, but ... :

> 
pablo@BENQ:~/sqcam-2.6.24$ sudo modprobe sqcam
FATAL: Error inserting sqcam (/lib/modules/2.6.24-16-generic/kernel/drivers/usb/media/sqcam.ko): Unknown symbol in module, or unknown parameter (see dmesg)


dmesg says :

> 
[ 6549.887883] Linux video capture interface: v2.00
[ 6549.889644] sqcam: Unknown parameter `force_palette'
[ 6572.352308] usb 1-2: new full speed USB device using ohci_hcd and address 2
[ 6572.561130] usb 1-2: configuration #1 chosen from 1 choice
[ 6572.619307] sqcam: Unknown parameter `force_palette'
[ 6579.046849] sqcam: Unknown parameter `force_palette'
[ 6580.859421] sqcam: Unknown parameter `force_palette'
[ 6691.529319] sqcam: disagrees about version of symbol struct_module
[ 6736.982717] sqcam: Unknown parameter `force_palette'
[ 6993.409499] Linux video capture interface: v2.00
[ 6993.411361] sqcam: Unknown parameter `force_palette'


Hmmm... :-k

What we should do, **Pitxyoki** ??

---

### Post by jacl11 on 2008-05-03
is it possible to run this camera under skype without those green lines... I dont have any problems with ekiga (or with normal capture under xawtv) but I cant seem to solve this issue with skype...

---

### Post by jmb365 on 2008-05-05
Hello all,

I followed the directions of this thread and I do not have any /dev/video*

# Install the cheap USB DigiGR8 camera from Radio Shack.

lsusb 
# Bus 001 Device 006: ID 2770:905c NHJ, Ltd Che-Ez Snap SNAP-U/Digigr8/Soundstar TDC-35

sudo apt-get install gcc make cvs linux-headers-`uname -r`

# If (and only if) you are using a linux distribution with a newer kernel than 2.6.24, you will need the attachment named: sqcam26-2.6.24.tar.gz.
# All you have to do now is this:

bunzip2 sqcam-2.6.24.tar.bz2
tar -xvf sqcam-2.6.24.tar
cd sqcam-2.6.24

make gamma.h
make
sudo mkdir /lib/modules/`uname -r`/kernel/drivers/usb/media
sudo make install
sudo depmod -a
sudo modprobe sqcam

All the above steps went smoothly, except for some warnings in the "make".

sudo apt-get install xawtv
xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-16-generic)
xinerama 0: 1680x1050+0+0
xinerama 1: 1680x1050+1680+0
WARNING: remote display `localhost:10.0' not allowed, using `:10.0' instead
can't open x11 display :10.0
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

I realize the error about x11 not being able to open display: 10:0, but my bigger problem is there is no /dev/video anything.  I am using Ubuntu 8.04 Hardy (2.6.24-16-generic) and am stuck.  Could somebody please help.  Thank you.

JMB

---

### Post by mensonge on 2008-05-06
I am under **Ubuntu 8.04** with a **Compaq nx6125** and the tutorial works perfectly for me with this webcam:

**Bus 002 Device 003: ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera**

Thank you very much.

---

### Post by Pitxyoki on 2008-05-07
Wow... Thanks a lot for the information, kilgota!
I haven't tested changing the resolution yet, but your information may be useful for someone who might be interested in playing around or even developing the module some more. :)

> **LOCOSLAW_PL said:**
> In Ubuntu 8.04 Stable (kernel 2.6.24.16) - don't work.

Everything is okay, but ... :

> pablo@BENQ:~/sqcam-2.6.24$ sudo modprobe sqcam
FATAL: Error inserting sqcam (/lib/modules/2.6.24-16-generic/kernel/drivers/usb/media/sqcam.ko): Unknown symbol in module, or unknown parameter (see dmesg)
(...)
What we should do, **Pitxyoki** ??

Honestly, I don't know. :?
Try to follow the HOWTO again. As you can see, [mensonge](http://ubuntuforums.org/showthread.php?p=4892993#post4892993) has already been able to do it under Ubuntu 8.04. I really can't help you much more with that right now. :|

> **jacl11 said:**
> is it possible to run this camera under skype without those green lines... I dont have any problems with ekiga (or with normal capture under xawtv) but I cant seem to solve this issue with skype...
Sincerely, I don't know either. :) I never used Skype, but that seems to me like a bug in Skype and not on the webcam module. If it works everywhere else but not only with that program, it seems like a problem with that program. Try searching on Skype support forums...



> **jmb365 said:**
> Hello all,

I followed the directions of this thread and I do not have any /dev/video*

# Install the cheap USB DigiGR8 camera from Radio Shack.

lsusb 
# Bus 001 Device 006: ID 2770:905c NHJ, Ltd Che-Ez Snap SNAP-U/Digigr8/Soundstar TDC-35
(...)
JMB
jmb365, your webcam uses a different module. This module is for webcams with the USB ID 2770:9120 and not 2770:905c. I believe you can find support for your camera with some other module. Have you tried installing libgphoto2 and gtkam?

---

### Post by jacl11 on 2008-05-10
> **Pitxyoki said:**
> 
Sincerely, I don't know either. :) I never used Skype,...


Hmm... I found a nice thread that features a working workaround (so to speak) with the skype bug (green lines) - 

[http://ubuntuforums.org/showthread.php?t=696978](http://ubuntuforums.org/showthread.php?t=696978)

Unfortunately I am not too good with linux and this workaround seemed to work only after I compiled and installed everything but ceased to work after I rebooted :P (must be my noobishness...)

The webcam seems to work without a problem with all the other apps (ekiga,xawtv and so on). So this reaffirms the statement that -it must be a bug in skype-.

Anyhow... if anyone comes up with a working solution it would be nice if they would post it... skype is after all a quite popular cross platform chatting app :)

Cheers!

---

### Post by LOCOSLAW_PL on 2008-05-11
**Pitxyoki** - I format hard drive and installed Ubuntu 8.04 - now sqcam driver works

for **jacl11** and other who want use sqcam with skype :

How to make sqcam and skype work;)

> 
0. Camera must be unplugged
1. We need to install effectv :
	sudo apt-get install effectv

2. We need to download vloopback:

	a. write in terminal :
	svn co [http://www.lavrsen.dk/svn/vloopback/trunk/](http://www.lavrsen.dk/svn/vloopback/trunk/) vloopback
	b. go to vloopback folder :
	cd vloopback
	c. write in terminal :
	make
	sudo make install

2 .. :  sudo mv /dev/video0 /dev/video2


3. Now we need to write :

	effectv -device /dev/video2 -vloopback /dev/video1

4. If you got this answer, don't worry and keep it doing:

	This device seems not to support video capturing.
	Video initialization failed.

5. We need to back to home folder : cd..

6. We need to download gstfakevideo :

	a. svn checkout [http://gstfakevideo.googlecode.com/svn/trunk/](http://gstfakevideo.googlecode.com/svn/trunk/) gstfakevideo
	b. type in terminal : make and sudo make install
	c. If you had dependeces bug - install - libgstreamer0.10-dev :
		sudo apt-get install libgstreamer0.10-dev

Now plugin camera

7. Run Skype by command :

	 ./gstfakevideo v4lsrc device=/dev/video2 ! ffmpegcolorspace

8. Everything should be ok, In section device (video options) should be :

	GStreamer fake video (/dev/video0) 

9. gstfakevideo is a file, so we can copy it where we want (for example home folder)

10. I hope that i didin't make any mistakes and that will works.



Sorry for my poor English

If you had any problems with start skype with sqcam after next reboot try :

> sudo mv /dev/video0 /dev/video2

effectv -device /dev/video2 -vloopback /dev/video1

./gstfakevideo v4lsrc device=/dev/video2 ! ffmpegcolorspace



I sometimes had problems with turn it on - it is very dificult :O

---

### Post by jmb365 on 2008-05-13
> **Pitxyoki said:**
> 

jmb365, your webcam uses a different module. This module is for webcams with the USB ID 2770:9120 and not 2770:905c. I believe you can find support for your camera with some other module. Have you tried installing libgphoto2 and gtkam?

Thank you for your reply.  I installed gtkam and was able to view the still photos taken by this USB camera.

However I was hoping to get the video stream working.  Any ideas?

Regards,
JMB

---

### Post by GothPanda on 2008-05-30
*Sigh*

I've upgraded to 8.04, and guess what...

The cam's broken.  I can't get it working for the life of me.  I'm not getting a /dev/video0 at all...

I don't know what happened, and I'm just about done with this crap...

---

### Post by Pitxyoki on 2008-05-31
[FONT="Fixedsys"][SIZE="1"]For some reason I don't use Ubuntu anymore...[/SIZE][/FONT] :-$

---

### Post by GothPanda on 2008-05-31
> **Pitxyoki said:**
> [FONT="Fixedsys"][SIZE="1"]For some reason I don't use Ubuntu anymore...[/SIZE][/FONT] :-$

Anyway, I got some more information if someone can help me.  (Sorry to hear you don't use ubuntu anymore)

Anyway, it's failing when it's trying to send control commands to the camera.  The camera is still working on the laptop.  The usb ports on the desktop are okay.  When I run lsmod, it shows that sqcam isn't being used.

sqcam 0

Anyway.  I don't know what in the world is going on here.  Anyone have any insights, it would be awesome...

---

### Post by Pitxyoki on 2008-05-31
Don't feel sorry: I've been using Debian for quite some time and no upgrade has ever let me down until today: I'm using the most recent kernel (2.6.25) and my desktop is more stable than it ever was with Ubuntu. :)

[LOCOSLAW_PL](http://ubuntuforums.org/showthread.php?p=4931808#post4931808) and others seem to have solved the issue as you are having by formatting and re-installing Ubuntu... But those were the kind of solutions that made me get away from Ubuntu, that's why I said that. 8-)

---

### Post by quanumphaze on 2008-05-31
Thanks a lot

This has finally got my camera working but it is (just like everyone else) buggy in Skype. And it doesn't seem to work at all with Cheese though works fine in gstreamer-properties.

---

### Post by quanumphaze on 2008-06-01
I got Skype working with the gstfakevideo and you don't need effectv or vloopback. That is if you want special effects.

I have some problems with the colour. Red and blue have swapped

This is what worked for me:```
sudo mv /dev/video0 /dev/video2
sudo apt-get install libgstreamer0.10-dev
cd ~/where\ you\ put\ files
svn checkout http://gstfakevideo.googlecode.com/svn/trunk/ gstfakevideo
make
sudo make install

[COLOR="DarkRed"]# Type this to run Skype[/COLOR]
gstfakevideo v4lsrc device=/dev/video2 ! ffmpegcolorspace

```
You must leave the camera connected or you will have to restart Skype to use it again. It must also be plugged in before starting and half the time it wont work.
It seems that the camera is constantly running with gstfakevideo, even when not in video mode.
For me Red and Blue are swapped around. Anyone know how to fix it?
Good idea is to change the menu entry to the gstfakevideo line. It will still load Skype up when you don't connect the camera.

---

### Post by DaniFilth on 2008-06-10
Man, you rock, it worked perfect in Hardy, kernel 16 and 17, thanx a lot my friend

---

### Post by timwaters on 2008-06-16
:( I'm also getting
```
sudo modprobe  sqcam
FATAL: Error inserting sqcam (/lib/modules/2.6.20-15-generic/kernel/drivers/usb/media/sqcam.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

just like a[ previous poster]("http://ubuntuforums.org/showthread.php?p=4931808#post4931808") , but i do not want to reformat and reinstall my machine just to get it working!

---

### Post by Pitxyoki on 2008-06-16
timwaters,
What's the output of ```
$ dmesg | tail
``` after doing the modprobe command?

---

### Post by timwaters on 2008-06-16
dmesg | tail gives
```
[ 6202.968000] sqcam: disagrees about version of symbol video_unregister_device
[ 6202.968000] sqcam: Unknown symbol video_unregister_device
[ 6202.968000] sqcam: disagrees about version of symbol video_register_device
[ 6202.968000] sqcam: Unknown symbol video_register_device
[ 7469.348000] sqcam: disagrees about version of symbol video_devdata
[ 7469.348000] sqcam: Unknown symbol video_devdata
[ 7469.348000] sqcam: disagrees about version of symbol video_unregister_device
[ 7469.348000] sqcam: Unknown symbol video_unregister_device
[ 7469.348000] sqcam: disagrees about version of symbol video_register_device
[ 7469.348000] sqcam: Unknown symbol video_register_device

```

---

### Post by Pitxyoki on 2008-06-16
Sorry, try ```
$ dmesg | tail -n50
```
Also, what distribution are you using? And what does ```
$ uname -r
``` give?

---

### Post by timwaters on 2008-06-16
> **Pitxyoki said:**
> Sorry, try ```
$ dmesg | tail -n50
```
Also, what distribution are you using? And what does ```
$ uname -r
``` give?
ok :) here's the longer dmesg:
```
[ 3282.004000] eth0: no IPv6 routers present
[ 3662.212000] dvb-usb: bulk message failed: -71 (1/0)
[ 3662.248000] usb 4-4: USB disconnect, address 7
[ 3662.248000] dvb-usb: WideView WT-220U PenType Receiver (based on ZL353) successfully deinitialized and disconnected.
[ 3674.792000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[ 3674.960000] usb 2-2: configuration #1 chosen from 1 choice
[ 3898.220000] usb 2-2: USB disconnect, address 2
[ 3901.060000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[ 3901.228000] usb 2-2: configuration #1 chosen from 1 choice
[ 4282.244000] Linux video capture interface: v2.00
[ 6017.788000] sqcam: disagrees about version of symbol video_devdata
[ 6017.788000] sqcam: Unknown symbol video_devdata
[ 6017.788000] sqcam: disagrees about version of symbol video_unregister_device
[ 6017.788000] sqcam: Unknown symbol video_unregister_device
[ 6017.788000] sqcam: disagrees about version of symbol video_register_device
[ 6017.788000] sqcam: Unknown symbol video_register_device
[ 6048.016000] sqcam: disagrees about version of symbol video_devdata
[ 6048.016000] sqcam: Unknown symbol video_devdata
[ 6048.016000] sqcam: disagrees about version of symbol video_unregister_device
[ 6048.016000] sqcam: Unknown symbol video_unregister_device
[ 6048.016000] sqcam: disagrees about version of symbol video_register_device
[ 6048.016000] sqcam: Unknown symbol video_register_device
[ 6078.464000] usb 2-2: USB disconnect, address 3
[ 6080.400000] usb 2-2: new full speed USB device using uhci_hcd and address 4
[ 6080.568000] usb 2-2: configuration #1 chosen from 1 choice
[ 6080.760000] sqcam: disagrees about version of symbol video_devdata
[ 6080.760000] sqcam: Unknown symbol video_devdata
[ 6080.760000] sqcam: disagrees about version of symbol video_unregister_device
[ 6080.760000] sqcam: Unknown symbol video_unregister_device
[ 6080.760000] sqcam: disagrees about version of symbol video_register_device
[ 6080.760000] sqcam: Unknown symbol video_register_device
[ 6086.068000] sqcam: disagrees about version of symbol video_devdata
[ 6086.068000] sqcam: Unknown symbol video_devdata
[ 6086.068000] sqcam: disagrees about version of symbol video_unregister_device
[ 6086.068000] sqcam: Unknown symbol video_unregister_device
[ 6086.068000] sqcam: disagrees about version of symbol video_register_device
[ 6086.068000] sqcam: Unknown symbol video_register_device
[ 6202.968000] Linux video capture interface: v2.00
[ 6202.968000] sqcam: disagrees about version of symbol video_devdata
[ 6202.968000] sqcam: Unknown symbol video_devdata
[ 6202.968000] sqcam: disagrees about version of symbol video_unregister_device
[ 6202.968000] sqcam: Unknown symbol video_unregister_device
[ 6202.968000] sqcam: disagrees about version of symbol video_register_device
[ 6202.968000] sqcam: Unknown symbol video_register_device
[ 7469.348000] sqcam: disagrees about version of symbol video_devdata
[ 7469.348000] sqcam: Unknown symbol video_devdata
[ 7469.348000] sqcam: disagrees about version of symbol video_unregister_device
[ 7469.348000] sqcam: Unknown symbol video_unregister_device
[ 7469.348000] sqcam: disagrees about version of symbol video_register_device
[ 7469.348000] sqcam: Unknown symbol video_register_device

```
and uname -r gives
2.6.20-15-generic

it compiled fine with no errors using the sqcam26-new.tar.bz2

edits: distribution is feisty 7.04

---

### Post by Pitxyoki on 2008-06-16
Does ```
$ apt-cache policy linux-headers-`uname -r`
``` say the headers are installed?

---

### Post by timwaters on 2008-06-16
> **Pitxyoki said:**
> Does ```
$ apt-cache policy linux-headers-`uname -r`
``` say the headers are installed?
hmm I think it looks like it...
```
apt-cache policy linux-headers-`uname -r`
linux-headers-2.6.20-15-generic:
  Installed: 2.6.20-15.27
  Candidate: 2.6.20-15.27
  Version table:
 *** 2.6.20-15.27 0
        500 http://gb.archive.ubuntu.com feisty/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by Pitxyoki on 2008-06-16
Have you tried to ```
$ sudo depmod -a
``` before using modprobe?

The most similar situation I found was this bugreport, [https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/160814](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/160814) , which for some seem to have been solved by reinstalling the linux-image and linux-headers packages (and then I'd suggest rebooting) and running depmod... It's weird, as some people with the same kernel as you have been able to install the webcam without problems...

Also, does ```
$ lsusb
``` give you exactly "2770:9120" as the ID for the cam or something else, even if similar?

---

### Post by timwaters on 2008-06-16
> **Pitxyoki said:**
> Have you tried to ```
# depmod -a
``` before doing modprobe?

The most similar situation I found was this bugreport, [https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/160814](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/160814) , which for some seem to have been solved by reinstalling the linux-image and linux-headers packages (and then obviously rebooting) and running depmod... It's weird, as some people with the same kernel as you have been able to install the webcam without problems...

Also, does ```
$ lsusb
``` give you exactly "2770:9120" as the ID for the cam or something else, even if similar?

depmod -a and then modprobe gives same error:```
FATAL: Error inserting sqcam (/lib/modules/2.6.20-15-generic/kernel/drivers/usb/media/sqcam.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
and lsusb does indeed give the same id:
```
Bus 002 Device 005: ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera
```

Yes, I was reading elsewhere about reinstalling kernal image & headers may fix it. I will instead wait until I upgrade my distribution to the latest one. Many thanks for help in meantime, and hope that it can help anyone  else who comes across the same problem in the future.

---

### Post by ay7aga1000000 on 2008-09-17
tanxxxxxxxxxx

---

### Post by wolffangalchemist on 2008-09-24
oddly enough i installed it with out doing anything in this guide with 64bit hardy and easycam2 and it works with aMSN perfectly and in cheese everything in the room is blue but it doesn't work with skype or camorama.
i guess this means there working on this cameras compatibility with easycam2?

---

### Post by Pitxyoki on 2008-09-24
Thanks for the information, wolffangalchemist! I tested EasyCam2 on Debian and it is working well here, too.
The first post has been updated and this is now the recommended way: it is much simpler and basically it does the same thing, but automatically and with a GUI.

To test the camera with camorama, try calling it with -M:
```
$ camorama -M
```
The image will still be blue, but it would be like that too if you compiled the module yourself, without EasyCam2.

---

### Post by wolffangalchemist on 2008-10-02
i just tryied it with skype again from terminal and this time it worked but it has green lines all over it the only diffrents is i'm useing xfce instead of gnome ill go try it in gnome and up date this post.

EDIT: nope no good same thing but this is a sign the drivers are improving quickly i hope.

---

### Post by dnw on 2008-11-26
sqcam does not compile with Intrepid 8.10. Error messages start with 

make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /test/sqcam26/sq905.o                                      
/test/sqcam26/sq905.c: In function ‘sqcam_ioctl’:                    
/test/sqcam26/sq905.c:336: error: incompatible type for argument 1 of ‘dev_get_drvdata’

---

### Post by 0olong on 2008-11-26
I followed the steps on that first page to no avail.

'No camera, or no compatible camera found', says EasyCam 2.

lsusb was reporting exactly the description found on the first page before I started (though, um, now it's not mentioning the web cam!) ...my Ubuntu version is 8.04.

Any clues?

---

### Post by Kelly Jones on 2008-11-27
Pitxyoki, or Anyone else with information,

I noticed your post stating your video guide won't work with the mini digital camera, product ID 0x905c ("Digigr8/Soundstar/TTD-35").

You linked to [_crusti's guide_]("http://ubuntuforums.org/showthread.php?t=157427#10") who mentions he's updating the sq905c.c file. Also, sqcam-2.6.24.tar.bz2 uses sq905.c. The Digigr8 has the sq905c chipset. So, why wouldn't the Digigr8 work?

I haven't gotten the video streaming yet, but it may be because of an issue with the header files, or pointers to header files. Some help here would be much appreciated.

Everything alright up to:
```
linux-0fba:/home/kelly/Documents/sqcam/sqcam26 #make
make -C /usr/src/linux-2.6.25.18-0.2-obj/ SUBDIRS=/home/kelly/Documents/sqcam/sqcam26 modules
make[1]: Entering directory '/usr/src/linux-2.6.25.18-0.2-obj'
make[1]: *** No rule to make target 'modules'. Stop.
make[1]: Leaving directory '/usr/src/linux-2.6.25.18-0.2-obj'
make: *** [module] Error 2
```

Thanks in advance for your help,

Other details:
- Using openSUSE 11.0
- Installed: gcc, make, apt packages, linux-kernel-headers. 
- Can view and download still photos from Digigr8 on DigiKam. 
- Luvcview and xawtv don't seem to load (bouncing icon vanishes). 
- File manager shows no /dev/video0/.

Kelly.

---

### Post by dnw on 2008-11-28
The maintainer of sqcam has fixed the code to support linux-2.6.27 and it now works in Intrepid 8.10 with camorama and xawtv and kopete. But not yet with skype.

The code is available for the project CVS server. See [https://sourceforge.net/cvs/?group_id=92691](https://sourceforge.net/cvs/?group_id=92691)

regards

David

> **dnw said:**
> sqcam does not compile with Intrepid 8.10. Error messages start with 

make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /test/sqcam26/sq905.o                                      
/test/sqcam26/sq905.c: In function ‘sqcam_ioctl’:                    
/test/sqcam26/sq905.c:336: error: incompatible type for argument 1 of ‘dev_get_drvdata’

---

### Post by nickstephens on 2008-12-02
Here is an interesting follow on from the original post by Pitxyoki. I followed the instructions given in the first post (despite being for hardy and I am on a gutsy machine at present) and the camera seemed to be recognised and the complilation appeared to work fine. when using easycam, the drivers appeared to be recognised and all is going well and the test using exectute>webcam looks fantastic. 

Now if I try to use cheese outside of easycam, or skype the webcam isn't recognised. Guessing there is a link I have missed for skype and cheese to recognise the webcam but I can't see where at present :-s

I know that upgrading would be the simplest option but impractical at present for one reason or another. 

I am using the quickcam pro 5000 on a gutsy 7.10 build

---

### Post by cshaobui640990 on 2008-12-02
is [jordan shoes](http://www.b2bsneaker.com) good enough for play basketball?

---

### Post by nickstephens on 2008-12-09
Ok, a little bit of a pain but I found the issue was associated with the permissions. easycam etc. For the novices out there like myself, install the drivers as suggested above and then change the permssion of /dev/video0. This should work and then in my case the microphone was a bit of a pain in Gutsy as I had to enable several of the input functions to get a single microphone to work. I can't tell you which ones as my system is in French at present (but you have to enable inmux and invol in French it seems) but may just be a concequence of my system being set up the way it is. This isn't an issue with hardy as far as I am aware.

---

### Post by neomatrix2003 on 2008-12-12
Hello
i have the kernel 2.6.27-9
i take this files [here]("http://formationeuromedia.free.fr/sqcam26.tar.gz")
read readme in the folder
but:
in terminal root no sudo in user!!! su or sudo -i

plug your cam on usb

first: time in the folder install 2 DEB easycam core fist and secon gtk for GNOME

in MENU application accessory easycam
next install driver found on you CAM


second part:
make clean
make gamma.h
make 
make install
modprobe sqcam

reboot

verified you have on /dev
video0 or X = over number if you have more video record (Ex: cardTv or Sat)

enjoy

---

### Post by pacoTheMachine on 2009-02-02
> For me Red and Blue are swapped around. Anyone know how to fix it?
Good idea is to change the menu entry to the gstfakevideo line. It will still load Skype up when you don't connect the camera.

Hi!

I think, that I solved it.

In the trac of gstfakevideo;
[http://code.google.com/p/gstfakevideo/source/detail?r=3#](http://code.google.com/p/gstfakevideo/source/detail?r=3#)

You can see that in revision 3, the programmer change one line, and he named the problem, Color-reverse fixed (bad fourcc used).

Concretely it is, in gst.c file:

line 132:
	  "format", GST_TYPE_FOURCC, GST_MAKE_FOURCC ('Y', 'V', '1', '2'),

change for this other:
 
 	  "format", GST_TYPE_FOURCC, GST_MAKE_FOURCC ('I', '4', '2', '0'),

make and make install

I changed this line and all work perfect!!

---

### Post by mbelancon on 2009-02-20
Hi!
First, I'm using ubuntu hardy 64 bits now, with kernel 2.6.24-23 and all security and recommended updates already done. My webcam is:

Bus 002 Device 003: ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera

And I've done exactly the suggested on the first page of this topic. Easycam2 works ok and compiled and installed the module sqcam.
With lsmod I've got something like this:

usbcore               170288  4 sqcam,ehci_hcd,uhci_hcd
videodev               30720  1 sqcam

than, i think that the driver was compiled and installed. Otherwise, the webcam doesn't work in cheese, amsn or skype. I've already read that:

If (and only if) you are using a linux distribution with a newer kernel than 2.6.24, you will need the attachment named: sqcam26-2.6.24.tar.gz.

But, how can I do it? Don't is clear for me what I need to do. So, please, if anyone can help-me I will very thankful.

obs: sorry about my English!

---

### Post by swajime on 2009-12-15
I want to install this, but I am getting an error ... :-(

```
$ sudo dpkg -i easycam2-core.deb easycam2-gtk.deb
(Reading database ... 262505 files and directories currently installed.)
Preparing to replace easycam2-core 2.01-03 (using easycam2-core.deb) ...
Unpacking replacement easycam2-core ...
dpkg: error processing easycam2-gtk.deb (--install):
 **cannot access archive: No such file or directory**
dpkg: dependency problems prevent configuration of easycam2-core:
 easycam2-core depends on python-xml; however:
  **Package python-xml is not installed.**
dpkg: error processing easycam2-core (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 easycam2-gtk.deb
 easycam2-core
```

---

### Post by Pitxyoki on 2009-12-15
[SIZE="3"]**EDIT 3:** Although this webcam is available on the official Linux Kernel ([http://kernel.org](http://kernel.org)), Ubuntu seems to have applied patches that prevent it from working correctly. Until Ubuntu resolves this your best option is probably to [recompile an official kernel](http://kernel-handbook.alioth.debian.org/ch-common-tasks.html#s-kernel-org-package).

**Remember that if you do this you may lose support for any further problems you may have while using that compiled kernel with Ubuntu**, so don't do it if you don't understand what's going on here.[/SIZE][SIZE="1"] Or if you're not brave enough to take the risk. :)[/SIZE]

This was my original post here:
---
Hi everyone,
This webcam is supported natively on Linux [since kernel version 2.6.30](http://kernelnewbies.org/Linux_2_6_30).
This means that since Ubuntu Karmic Koala (9.10) the webcam should work out-of-the box, without any installation or configuration steps.

You may still experience problems, but these are related to the module itself or the programs that use it.
There is no need to install or configure anything manually anymore. Any bugs you find related to the module should be reported to the kernel's bugzilla. Any bugs related to the programs using the module should be reported to such program's bug trackers.

I consider this tutorial deprecated for Ubuntu starting from Karmic, and all other Linux distributions that provide a kernel version >= 2.6.30.

**EDIT:** xawtv currently seems to be having problems with various webcams. But now you can test it with VLC (just use Synaptic or whatever to install it). With VLC you can simply use the "File -> Open Capture Device" option, choose "Video for Linux 2" and click "Play".

**EDIT 2:** swajime, try to ```
apt-get -f install
```

---

### Post by swajime on 2009-12-15
VLC is not working either.

When I follow your instructions for VLC, I get "Your input can't be opened:
VLC is unable to open the MRL 'v4l2://'. Check the log for details."

If I run it from a terminal, I get this:
```
[0x244b888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x27ae268] v4l2 demux error: cannot open video device '/dev/video0' (No such file or directory)
[0x27ae268] v4l2 demux error: cannot open video device '/dev/video0' (No such file or directory)
[0x27ae7f8] v4l2 access error: cannot open video device '/dev/video0' (No such file or directory)
[0x27ae7f8] v4l2 access error: cannot open video device '/dev/video0' (No such file or directory)
[0x7f181c0011e8] main input error: open of `v4l2://' failed: (null)

```

---

### Post by Pitxyoki on 2009-12-15
> **swajime said:**
> VLC is not working either.

When I follow your instructions for VLC, I get "Your input can't be opened:
VLC is unable to open the MRL 'v4l2://'. Check the log for details."


Please post the output of:
```
$ uname -r
$ lsmod | grep gs
$ vlc --version
```

---

### Post by swajime on 2009-12-15
john@system76-pc:~$ uname -r
2.6.31-16-generic
john@system76-pc:~$ lsmod | grep gs
gspca_sq905             6112  0 
gspca_main             26816  1 gspca_sq905
videodev               43360  1 gspca_main
john@system76-pc:~$ vlc --version
VLC media player 1.0.2 Goldeneye
VLC version 1.0.2 Goldeneye
Compiled by buildd@.unknown
Compiler: gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.

---

### Post by swajime on 2009-12-15
except there is no smiley after the ubuntu ... that is supposed to be 8 )

---

### Post by Pitxyoki on 2009-12-15
> **swajime said:**
> except there is no smiley after the ubuntu ... that is supposed to be 8 )

lol, I could see that.
Apparently, that's just bad luck: trusting on [this thread](http://forum.videolan.org/viewtopic.php?f=13&t=61141) (the first result on Google), that seems to be a bug on VLC up to version 1.0.2. VLC 1.0.3 doesn't seem to have that bug anymore - it's also available at the Karmic repositories, so you might want to give that a try if you feel confident to do so.

Did you test your webcam with other programs?
What do these show?
```
$ ls -l /dev/video* /dev/vd*
```

---

### Post by swajime on 2009-12-15
No I've never been able to get this camera to work on linux.  I only just found this thread and was hoping you had the answer ...

```
john@system76-pc:~$ lsusb
Bus 001 Device 039: ID 0781:7302 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera
Bus 002 Device 002: ID 0d9f:0002 Powercom Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1130:1620 Tenx Technology, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

john@system76-pc:~$ ls -l /dev/video* /dev/vd*
ls: cannot access /dev/video*: No such file or directory
ls: cannot access /dev/vd*: No such file or directory
```

---

### Post by Pitxyoki on 2009-12-15
That's weird, swajime.
Apparently your system should have the most recent module and there should be a /dev/video0 device.

Let's try something else. First, close any program that might be using the webcam. Then open two consoles.

On the first one do:
```
$ tail -F /var/log/syslog
```
On the second console do:
```
$ sudo modprobe -rv gspca_sq905
```
If modprobe complains that the module is in use, probably you forgot to close some program(s). The browser may one of them. Retry the modprobe command until you don't get such messages.

Now disconnect your camera from the USB cable. Wait a couple of seconds and then reconnect it.
Now please show the new lines that appeared at the first terminal after the tail command. "ls -l /dev/video*" *should* also give you something more than a "No such file or directory".

---

### Post by swajime on 2009-12-15
Just to be sure, I removed the webcam and did a complete reboot.

```
john@system76-pc:~$ tail -F /var/log/syslog
```

# plugging in webcam now
```

Dec 15 16:25:51 system76-pc kernel: [  320.171321] usb 3-1: new full speed USB device using uhci_hcd and address 2
Dec 15 16:25:51 system76-pc kernel: [  320.344304] usb 3-1: configuration #1 chosen from 1 choice
Dec 15 16:25:51 system76-pc kernel: [  320.408984] Linux video capture interface: v2.00
Dec 15 16:25:51 system76-pc kernel: [  320.442038] gspca: main v2.6.0 registered
Dec 15 16:25:51 system76-pc kernel: [  320.445290] gspca: probing 2770:9120
Dec 15 16:25:51 system76-pc kernel: [  320.942060] sq905: sq905_command: usb_control_msg failed (-110)
Dec 15 16:25:51 system76-pc kernel: [  320.942081] sq905: probe of 3-1:1.0 failed with error -110
Dec 15 16:25:51 system76-pc kernel: [  320.942125] usbcore: registered new interface driver sq905
Dec 15 16:25:51 system76-pc kernel: [  320.942130] sq905: registered
Dec 15 16:25:52 system76-pc kernel: [  321.094027] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 12 len 1 ret -71
Dec 15 16:25:52 system76-pc kernel: [  321.095015] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 192 rq 12 len 1 ret -71
(repeated lines clipped)
```

```
$ sudo modprobe -rv gspca_sq905
rmmod /lib/modules/2.6.31-16-generic/kernel/drivers/media/video/gspca/gspca_sq905.ko
rmmod /lib/modules/2.6.31-16-generic/kernel/drivers/media/video/gspca/gspca_main.ko
rmmod /lib/modules/2.6.31-16-generic/kernel/drivers/media/video/videodev.ko
rmmod /lib/modules/2.6.31-16-generic/kernel/drivers/media/video/v4l1-compat.ko
rmmod /lib/modules/2.6.31-16-generic/kernel/drivers/media/video/v4l2-compat-ioctl32.ko
```
```

Dec 15 16:26:07 system76-pc kernel: [  336.860703] usbcore: deregistering interface driver sq905
Dec 15 16:26:07 system76-pc kernel: [  336.860743] sq905: deregistered
Dec 15 16:26:07 system76-pc kernel: [  336.890139] gspca: main deregistered

```
# unplugging webcam

```
Dec 15 16:27:14 system76-pc kernel: [  403.291293] usb 3-1: USB disconnect, address 2
```

# plugging in webcam again

```
Dec 15 16:27:54 system76-pc kernel: [  443.770024] usb 3-1: new full speed USB device using uhci_hcd and address 3
Dec 15 16:27:54 system76-pc kernel: [  443.945054] usb 3-1: configuration #1 chosen from 1 choice
Dec 15 16:27:54 system76-pc kernel: [  443.958189] Linux video capture interface: v2.00
Dec 15 16:27:54 system76-pc kernel: [  443.961244] gspca: main v2.6.0 registered
Dec 15 16:27:54 system76-pc kernel: [  443.962092] gspca: probing 2770:9120
Dec 15 16:27:55 system76-pc kernel: [  444.460827] sq905: sq905_command: usb_control_msg failed (-110)
Dec 15 16:27:55 system76-pc kernel: [  444.460846] sq905: probe of 3-1:1.0 failed with error -110
Dec 15 16:27:55 system76-pc kernel: [  444.460888] usbcore: registered new interface driver sq905
Dec 15 16:27:55 system76-pc kernel: [  444.460893] sq905: registered
Dec 15 16:27:55 system76-pc kernel: [  444.545813] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 12 len 1 ret -71
Dec 15 16:27:55 system76-pc kernel: [  444.546799] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 192 rq 12 len 1 ret -71
(repeated lines clipped)
```

---

### Post by Pitxyoki on 2009-12-15
Aha!

> **swajime said:**
> ```

Dec 15 16:25:51 system76-pc kernel: [  320.171321] usb 3-1: new full speed USB device using uhci_hcd and address 2
Dec 15 16:25:51 system76-pc kernel: [  320.344304] usb 3-1: configuration #1 chosen from 1 choice
Dec 15 16:25:51 system76-pc kernel: [  320.408984] Linux video capture interface: v2.00
Dec 15 16:25:51 system76-pc kernel: [  320.442038] **gspca: main v2.6.0 registered**
Dec 15 16:25:51 system76-pc kernel: [  320.445290] **gspca: probing 2770:9120**
Dec 15 16:25:51 system76-pc kernel: [  320.942060] **sq905: sq905_command: usb_control_msg failed (-110)**
Dec 15 16:25:51 system76-pc kernel: [  320.942081] **sq905: probe of 3-1:1.0 failed with error -110**
Dec 15 16:25:51 system76-pc kernel: [  320.942125] usbcore: registered new interface driver sq905
Dec 15 16:25:51 system76-pc kernel: [  320.942130] sq905: registered
Dec 15 16:25:52 system76-pc kernel: [  321.094027] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 12 len 1 ret -71
Dec 15 16:25:52 system76-pc kernel: [  321.095015] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 192 rq 12 len 1 ret -71
(repeated lines clipped)
```
There's the problem.

I am using kernel 2.6.32, which has sqcam v2.7.0. This is what I get when I connect the camera:
```
(...)
Dec 15 22:01:07 C-5 kernel: [28239.283096] Linux video capture interface: v2.00
Dec 15 22:01:07 C-5 kernel: [28239.328810] **gspca: main v2.7.0 registered**
Dec 15 22:01:08 C-5 kernel: [28239.345098] **gspca: probing 2770:9120**
Dec 15 22:01:08 C-5 kernel: [28239.415554] **gspca: probe ok**
Dec 15 22:01:08 C-5 kernel: [28239.415599] usbcore: registered new interface driver sq905
Dec 15 22:01:08 C-5 kernel: [28239.415604] sq905: registered

```
Apparently the sqcam module provided with Karmic has some issues with sq905. I would recommend you to compile the 2.6.32 kernel or maybe only the 2.7.0 module from the official kernel, if you know how to. Two good pointers for this are [here](http://kernel-handbook.alioth.debian.org/ch-common-tasks.html#s-common-building) and [here](http://www.debian-administration.org/article/Rebuilding_a_single_kernel_module).
Please note that following those steps may make it harder for you to have support for your installation later.

On the other hand, gspca version 2.7 is included with the 2.6.32 kernel. This is what Ubuntu Lucid Lynkx uses. If you can, you should try to install and test it (or perhaps try the LiveCD to see if that works). Please tell us if you have success with that. :)

---

### Post by swajime on 2009-12-15
I appreciate your help.  I'm not ready to mess with the kernel yet.  I might try to make a live cd tomorrow.
I'll post back when I get more info.

---

### Post by swajime on 2009-12-18
I set up the Lynx LiveCD, but I'm still not getting a picture ...

connecting webcam ...

```
Dec 19 02:39:38 ubuntu kernel: [31936.070026] usb 3-2: new full speed USB device using uhci_hcd and address 3
Dec 19 02:39:38 ubuntu kernel: [31936.244722] usb 3-2: configuration #1 chosen from 1 choice
Dec 19 02:39:39 ubuntu kernel: [31936.373184] Linux video capture interface: v2.00
Dec 19 02:39:39 ubuntu kernel: [31936.409926] gspca: main v2.7.0 registered
Dec 19 02:39:39 ubuntu kernel: [31936.440368] gspca: probing 2770:9120
Dec 19 02:39:39 ubuntu kernel: [31936.930494] sq905: sq905_command: usb_control_msg failed (-110)
Dec 19 02:39:39 ubuntu kernel: [31936.930514] sq905: probe of 3-2:1.0 failed with error -110
Dec 19 02:39:39 ubuntu kernel: [31936.930557] usbcore: registered new interface driver sq905
Dec 19 02:39:39 ubuntu kernel: [31936.930562] sq905: registered
Dec 19 02:39:39 ubuntu kernel: [31936.943491] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 12 len 1 ret -71
Dec 19 02:39:39 ubuntu kernel: [31936.944487] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 192 rq 12 len 1 ret -71

$ sudo modprobe -rv gspca_sq905

root@ubuntu:/home/ubuntu# sudo modprobe -rv gspca_sq905
rmmod /lib/modules/2.6.32-7-generic/kernel/drivers/media/video/gspca/gspca_sq905.ko
rmmod /lib/modules/2.6.32-7-generic/kernel/drivers/media/video/gspca/gspca_main.ko
rmmod /lib/modules/2.6.32-7-generic/kernel/drivers/media/video/videodev.ko
rmmod /lib/modules/2.6.32-7-generic/kernel/drivers/media/video/v4l1-compat.ko
rmmod /lib/modules/2.6.32-7-generic/kernel/drivers/media/video/v4l2-compat-ioctl32.ko
root@ubuntu:/home/ubuntu# Dec 19 02:41:43 ubuntu kernel: [32060.651294] usbcore: deregistering interface driver sq905
Dec 19 02:41:43 ubuntu kernel: [32060.651751] sq905: deregistered
Dec 19 02:41:43 ubuntu kernel: [32060.681273] gspca: main deregistered
```

disconnect/reconnect usb webcam

```
root@ubuntu:/home/ubuntu# Dec 19 02:42:47 ubuntu kernel: [32124.790043] usb 3-2: USB disconnect, address 3
Dec 19 02:43:06 ubuntu kernel: [32143.820019] usb 3-2: new full speed USB device using uhci_hcd and address 4
Dec 19 02:43:06 ubuntu kernel: [32143.994187] usb 3-2: configuration #1 chosen from 1 choice
Dec 19 02:43:06 ubuntu kernel: [32144.010399] Linux video capture interface: v2.00
Dec 19 02:43:06 ubuntu kernel: [32144.014508] gspca: main v2.7.0 registered
Dec 19 02:43:06 ubuntu kernel: [32144.016646] gspca: probing 2770:9120
Dec 19 02:43:07 ubuntu kernel: [32144.510990] sq905: sq905_command: usb_control_msg failed (-110)
Dec 19 02:43:07 ubuntu kernel: [32144.511007] sq905: probe of 3-2:1.0 failed with error -110
Dec 19 02:43:07 ubuntu kernel: [32144.511270] usbcore: registered new interface driver sq905
Dec 19 02:43:07 ubuntu kernel: [32144.511667] sq905: registered
Dec 19 02:43:07 ubuntu kernel: [32144.644976] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 12 len 1 ret -71
Dec 19 02:43:07 ubuntu kernel: [32144.645956] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 192 rq 12 len 1 ret -71

root@ubuntu:/home/ubuntu# uname -r
2.6.32-7-generic
root@ubuntu:/home/ubuntu# lsmod | grep gs
gspca_sq905             4562  0 
gspca_main             24151  1 gspca_sq905
videodev               39878  1 gspca_main

```

---

### Post by Pitxyoki on 2009-12-19
That's weird.
Out of curiosity, I downloaded the Alpha 1 of Lucid Lynx and tested this myself.
After inserting the camera:
```

Dec 19 17:23:51 ubuntu kernel: [ 1122.360020] usb 2-1: new full speed USB device using uhci_hcd and address 4
Dec 19 17:23:51 ubuntu kernel: [ 1122.519977] usb 2-1: configuration #1 chosen from 1 choice
Dec 19 17:23:51 ubuntu kernel: [ 1122.538092] Linux video capture interface: v2.00
Dec 19 17:23:51 ubuntu kernel: [ 1122.542907] gspca: main v2.7.0 registered
Dec 19 17:23:51 ubuntu kernel: [ 1122.545565] gspca: probing 2770:9120
Dec 19 17:23:51 ubuntu kernel: [ 1122.651026] gspca: probe ok
Dec 19 17:23:51 ubuntu kernel: [ 1122.651069] usbcore: registered new interface driver sq905
Dec 19 17:23:51 ubuntu kernel: [ 1122.651140] sq905: registered
Dec 19 17:23:51 ubuntu kernel: [ 1122.729209] **gspca: disconnect complete**

```

Compare this with the output I get on Debian:
```
(...)
Dec 15 22:01:07 C-5 kernel: [28239.283096] Linux video capture interface: v2.00
Dec 15 22:01:07 C-5 kernel: [28239.328810] gspca: main v2.7.0 registered
Dec 15 22:01:08 C-5 kernel: [28239.345098] gspca: probing 2770:9120
Dec 15 22:01:08 C-5 kernel: [28239.415554] gspca: probe ok
Dec 15 22:01:08 C-5 kernel: [28239.415599] usbcore: registered new interface driver sq905
Dec 15 22:01:08 C-5 kernel: [28239.415604] sq905: registered

```

Also, notice the modules Ubuntu loads:
```
$ lsmod | grep gs
gspca_sq905             4562  0 
gspca_main             24151  1 gspca_sq905
videodev               39878  1 gspca_main

```

And the ones loaded on Debian:
```
# lsmod | grep gs
gspca_sq905             3038  0 
gspca_main             16310  1 gspca_sq905
videodev               26748  1 gspca_main
**usbcore**                99526  9 rndis_wlan,rndis_host,**gspca_sq905**,cdc_ether,**gspca_main**,usbnet,uhci_hcd,ehci_hcd

```

I didn't get the errors you see on your syslog, either with Karmic or Lucid, but I didn't get any /dev/video0 either.

I'm not 100% sure if these outputs are related with the absence of the /dev file, but it seems to me that the Ubuntu developers have screwed something on the kernel about this. If I were you, I'd [check the bug-tracker to see if this was already reported](https://launchpad.net/ubuntu/+bugs?field.searchtext=gspca).

---

### Post by Pitxyoki on 2010-05-10
[SIZE="4"][COLOR="Red"]This message will stay here as an "historical reference". There is no need to follow these steps as of Ubuntu 10.04 Lucid Lynx. The recommended steps are on the first post of this thread.[/COLOR][/SIZE]

**[SIZE="3"][COLOR="Green"]The attachments are kept on the first post of the thread.[/COLOR][/SIZE]**


__________________________

**[SIZE="3"][DEPRECATED] HOWTO: See video with NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera[/SIZE]**

...and use it with aMSN! (After finishing this tutorial you will also be able to [download still photos](http://ubuntuforums.org/showthread.php?p=2952334#post2952334) or [record your own movies](http://ubuntuforums.org/showthread.php?p=4269912#post4269912) with it)

So, if your webcam reports something similar to this:
```
$ lsusb
Bus 001 Device 005: ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera
```
Then this guide is for you!

**ATTENTION:**
 -> If you tried any other methods before this one to get your webcam to work and you had no success, please check the last part of this HOWTO, marked with a [IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]
 -> If your linux distribution does not use the apt package management system (i.e., is not Debian-based), scroll down to the old HOWTO on this page.


It seems that EasyCam finally supports this camera. From now on, this will be the (much simpler) method I will recommend:
```
$ sudo apt-get install make build-essential gcc python python-xml python2.4-glade2 python2.4-gtk2 cheese gksu python-gnome2
$ wget http://blognux.free.fr/ubuntu/dists/hardy/main/binary-i386/easycam2-core.deb
$ wget http://blognux.free.fr/ubuntu/dists/hardy/main/binary-i386/easycam2-gtk.deb
$ sudo dpkg -i easycam2-core.deb easycam2-gtk.deb
```

Or, if you are a KDE user:
```
$ sudo apt-get install make build-essential gcc python python-xml kdesudo python-qt4
$ wget http://blognux.free.fr/ubuntu/dists/hardy/main/binary-i386/easycam2-core.deb
$ wget http://blognux.free.fr/ubuntu/dists/hardy/main/binary-i386/easycam2-qt.deb
$ sudo dpkg -i easycam2-core.deb easycam2-qt.deb
```

Now go to Applications -> Accessories -> EasyCam2, click "Forward", select the correct camera, "Forward" again and click "Start the installation". When it's over, your webcam will be ready to use.

You can test it with xawtv, using
```
$ sudo apt-get install xawtv
$ xawtv 
```


To uninstall all of this, simply type:
```
$ sudo apt-get remove --purge cheese easycam2-gtk easycam2-core xawtv
```
If you don't do anything else, the camera will still work. To make sure nothing remains on your computer, issue these commands:
```
$ sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/sqcam.ko
$ sudo rm -rf /usr/share/EasyCam2/
```


**NOTES:**
 -> If you don't use sudo, you will have to change the launcher for EasyCam2 on the gnome-menu (using alacarte) to use gksu instead of gksudo, issue the command "gksu 'python /usr/share/EasyCam2/core.py -g'" or run it as root
Also,
 -> Whenever the kernel is updated, you will have to reinstall the module. All you have to do is to follow the EasyCam2 wizard and install the driver again
 -> aMSN will recognise the camera and the image should be OK
 -> xawtv will recognise the camera and the image should be OK
 -> camorama will have to be called with an -M argument ($ camorama -M), and will show a blueish color
 -> cheese will show a blueish color
 -> Skype will show the image with some strange green lines across the it (apparently, the problem is on Skype),

_______________________


This HOWTO has been tested under:

Debian *testing*, with Linux kernel 2.6.26-1-686 on September 24th, 2008.


Also reported to work on:
Ubuntu 8.04 Hardy Heron, by [wolffangalchemist](http://ubuntuforums.org/showthread.php?p=5845362#post5845362)

Any feedback of results from other versions of Ubuntu/other Linux distributions would be appreciated.



__________________________________________________
__________________________________________________
**[SIZE="3"]The old version of this post will be kept here for people using distributions without the apt package management system:[/SIZE]**

Following [this post](http://ubuntuforums.org/showthread.php?t=157427#10), I have finally been able to see video through my webcam and use it through aMSN!

**ATTENTION:** If you tried any other methods before this one to get your webcam to work and you had no success, please check the last part of this HOWTO, marked with a [IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]

Pre-requisites:
gcc, make, cvs and the current kernel's headers:
```
$ sudo apt-get install gcc make cvs linux-headers-`uname -r`
```

These were the steps I followed:

First: Get the source files for your webcam. These will be used to create the module to recognize your cam.
This command will download some files to a directory called 'sqcam26' inside the current directory.
```

$ cvs -z3 -d:pserver:anonymous@sqcam.cvs.sourceforge.net:/cvsroot/sqcam co -P sqcam26
$ cd sqcam26
```

Now, to compile this without errors, type (you may replace 'gedit' with your text editor of choice. Say, 'vim'):
```
$ gedit Makefile
```
Edit this file's 6th line. It should be like this:
```
KERNEL_DIR := /usr/src/linux-headers-`uname -r`
```

Also, add a hash sign to the 17th line:
```
#EXTRA_CFLAGS += -Wall -DHAS_REMAP_PAGE_RANGE
```
Save and exit

Adding this hash sign is called "commenting". We are excluding that line from being interpreted, as it will produce errors while creating the module. This is possible to do because the new kernels do not have those instructions and that piece of code gets unnecessary and as so, must be excluded.

**[COLOR="Red"]VERY IMPORTANT** Only add that "#" and NOTHING else!!![/COLOR] You are warned.

_________________________
**NOTE _ONLY for users of newer versions of Ubuntu than Dapper Drake or other Linux distributions with kernel equal or superior to 2.6.17_**
If anyone using an older kernel is having any of the problems described [here](http://ubuntuforums.org/showpost.php?p=2654112&postcount=2) or [here](http://ubuntuforums.org/showpost.php?p=2671839&postcount=5), please tell me:

There are some more things you will need to do:
Keep editing sq905.c and scroll down to line 1228. Comment that one too.
```
//        .owner          = THIS_MODULE,
```
Now you can save that file and exit.

Now we must edit another file: usbvideo.h:
```
$ gedit usbvideo.h
```
Add this last line after the other "#include" lines:
```

**//#include <linux/config.h>**
#include <linux/videodev.h>
#include <linux/usb.h>
**#include <media/v4l2-dev.h>**
```

Also, notice that the #include <linux/config.h> line must be commented.
Save and exit

_________________________
**NOTE _ONLY for users of newer kernel versions (2.6.24 or superior)_**:
If you get this:
```
$ uname -r
2.6.24
```
Or a value equal or superior to that then you will also need to
```
$ gedit sq905.c
```
And edit line 1268, to be like this:
```
//	.hardware = VID_HARDWARE_SE401, /* need an own value */
```

_________________________
**All users continue here:**
There is an alternative method to do all of these steps in a simple one:
Download this post's attachment with name sqcam26.tar.gz and then type:
```
$ tar -xvzf sqcam26.tar.gz
$ cd sqcam26
```

If (and _only if_) you are using a linux distribution with a newer kernel than 2.6.17, you will need the attachment named: **sqcam26-new.tar.gz**.

If (and _only if_) you are using a linux distribution with a newer kernel than 2.6.24, you will need the attachment named: **sqcam26-2.6.24.tar.gz**.


________

All you have to do now is this:
```
$ make gamma.h
$ make
$ sudo mkdir /lib/modules/`uname -r`/kernel/drivers/usb/media
$ sudo make install
$ sudo depmod -a
$ sudo modprobe sqcam
```

The 'make' command will output [some warnings](http://ubuntuforums.org/showthread.php?p=2673144#post2673144). It is important to note that these are just warnings, not errors and so let's hope it isn't anything too bad. :-? 


And to check that the camera is working:
```
$ sudo apt-get install xawtv
$ xawtv
```
This program is able to record video (and simultaneous audio, if you have a microphone). You can do that by following [these steps](http://ubuntuforums.org/showthread.php?p=4269912#post4269912).
If you see some messages saying "Device or resource busy" and you can't see anything from your camera, you may need to restart your computer. (just type 'xawtv' from a console to check it again after you restarted)

After all this, you must now be able to see video from your webcam!


To use your webcam with aMSN, you will just have to go to Preferences -> Others and run the Video Wizard. There, choose from one of the 'devices' and 'channels'. For me, the channel "Bayer Grid 1" worked well. All others show messy images with strange colors. Sometimes, you will need to cancel the wizard and restart it, but after two or so retries I could always get a nice picture of my room. :) 



_______________________
[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]**WARNING FOR PEOPLE WHO HAVE TRIED TO INSTALL THIS WEBCAM THROUGH EASYCAM, EASYCAM2 or using the sources for sqcam without correcting the sourcefiles:**
If you used any of these methods, you will create modules which can cause errors while trying to install, rendering your webcam unusable.
Before following this HOWTO's steps, do this:
```
$ sudo updatedb     #this command may take some time to finish
$ locate sqcam.ko
```
Now, for every line you see on this command's output, you will have to remove that file. e.g.:

If this was in the output
```
/lib/modules/2.6.15-28-686/kernel/drivers/usb/media-back/sqcam.ko
```
You will have to do:
```
sudo rm /lib/modules/2.6.15-28-686/kernel/drivers/usb/media-back/sqcam.ko
```
And the same goes for every line that came out from the 'locate sqcam.ko' command.

**ATTENTION:** If you followed this HOWTO _AFTER_ trying to use easycam or easycam2 _without following these steps_, you may not be able to use your camera and will need to do these last steps and then restart the HOWTO!
_______________________


This HOWTO has been tested under:

Ubuntu 6.06 LTS - the Dapper Drake, with Linux kernel 2.6.15-28-686 on May 7th, 2007. 
Debian *testing*, with Linux kernel 2.6.18-4-686 on June 3rd, 2007.
Debian *testing*, with Linux kernel 2.6.21-2-686 on September 23rd, 2007.
Debian *testing*, with Linux kernel 2.6.22-3-686 on December 3rd, 2007.
Debian *testing*, with Linux kernel 2.6.24-1-686 on February 4th, 2008.
Debian *testing*, with Linux kernel 2.6.25-2-686 on May 31st, 2008.
Debian *testing*, with Linux kernel 2.6.26-1-686 on September 24th, 2008.

aMSN version 0.97b, from the aMSN cvs and gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5) and GNU Make 3.81beta4, both from Ubuntu repositories.

aMSN 0.97-rc1 up to version 0.97.1, gcc version 4.1 up to 4.3.1 and GNU make 3.81 from Debian *testing* repositories.

Also reported to work on:
Linux Mint, by [Tzi]("http://ubuntuforums.org/showthread.php?p=2765931#post2765931")
Puppy Linux 3.01, by [product of time]("http://ubuntuforums.org/showthread.php?p=3726215#post3726215")
Ubuntu 7.04 Feisty Fawn, by [LOCOSLAW_PL]("http://ubuntuforums.org/showthread.php?p=2814193#post2814193") and [DavidJames]("http://ubuntuforums.org/showthread.php?p=2951897#post2951897")
Ubuntu 7.10 Gutsy Gibbon, by [knap]("http://ubuntuforums.org/showthread.php?p=3775999#post3775999")
Ubuntu 8.04 Hardy Heron, by [mensonge](http://ubuntuforums.org/showthread.php?p=4892993#post4892993), [LOCOSLAW_PL]("http://ubuntuforums.org/showthread.php?p=4931808#post4931808") and [DaniFilth](http://ubuntuforums.org/showthread.php?p=5160290#post5160290)
**WARNING**: upgrades from previous versions of Ubuntu to 8.04 [don't seem](http://ubuntuforums.org/showthread.php?p=4813484#post4813484) [to work well](http://ubuntuforums.org/showthread.php?p=5082223#post5082223) with this webcam.
RedHat Enterprise 4, by [uluman](http://ubuntuforums.org/showthread.php?p=4283189#post4283189)

Any feedback of results from other versions of Ubuntu/other Linux distributions would be appreciated.
_______________________
Credit goes to [http://sqcam.sourceforge.net](http://sqcam.sourceforge.net) and [http://sourceforge.net/projects/sqcam](http://sourceforge.net/projects/sqcam) and the cvs's file README and source code.
Also to [crusti for his post](http://ubuntuforums.org/showpost.php?p=2350018#10), which has shown me that I was heading in the right direction. :)
And last, but not least, to [Lare](http://blog.tecnovm64.com/2006/02/25/breeze-cam-on-linux/#comment-1363), for his almost indecipherable post on that blog. ;)

---

### Post by swajime on 2010-06-14
> **Pitxyoki said:**
> 
If your webcam reports something similar to this:
```
$ lsusb
Bus 001 Device 005: ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera
```

Then it is now fully supported by Ubuntu (version 10.04, Lucid Lynx).

Ubuntu has, however, [a bug that needs a workaround](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255678):
```
$ sudo modprobe -rv gspca_sq905
$ sudo modprobe -v gspca_sq905

```
You have to do this after every reboot or after every time you connect the camera plug.
...


I'm still having trouble getting this camera to work. :confused:

Here is my output:
```
root@system76-pc:~# lsusb|grep -i cam
Bus 004 Device 003: ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera

root@system76-pc:~# sudo modprobe -rv gspca_sq905
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/gspca_sq905.ko
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/gspca_main.ko
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/videodev.ko
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/v4l1-compat.ko
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/v4l2-compat-ioctl32.ko


Jun 14 20:35:14 system76-pc kernel: [39046.770058] usbcore: deregistering interface driver sq905
Jun 14 20:35:14 system76-pc kernel: [39046.770119] sq905: deregistered
Jun 14 20:35:14 system76-pc kernel: [39046.791577] gspca: main deregistered

root@system76-pc:~# sudo modprobe -v gspca_sq905
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/v4l2-compat-ioctl32.ko 
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/v4l1-compat.ko 
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/videodev.ko 
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/gspca_main.ko 
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/gspca_sq905.ko 
 
Jun 14 20:35:30 system76-pc kernel: [39062.601631] Linux video capture interface: v2.00
Jun 14 20:35:30 system76-pc kernel: [39062.606158] gspca: main v2.7.0 registered
Jun 14 20:35:30 system76-pc kernel: [39062.608790] gspca: probing 2770:9120
Jun 14 20:35:30 system76-pc kernel: [39062.610840] sq905: sq905_command: usb_control_msg failed (-71)
Jun 14 20:35:30 system76-pc kernel: [39062.610857] sq905: probe of 4-2:1.0 failed with error -71
Jun 14 20:35:30 system76-pc kernel: [39062.610896] usbcore: registered new interface driver sq905
Jun 14 20:35:30 system76-pc kernel: [39062.610972] sq905: registered

root@system76-pc:~# xawtv
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.32-22-generic)
xinerama 0: 1920x1200+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
root@system76-pc:~# 
```

---

### Post by Pitxyoki on 2010-06-15
These messages don't seem very nice:
> **swajime said:**
> ```
Jun 14 20:35:30 system76-pc kernel: [39062.610840] sq905: sq905_command: usb_control_msg failed (-71)
Jun 14 20:35:30 system76-pc kernel: [39062.610857] sq905: probe of 4-2:1.0 failed with error -71
```

I suppose VLC and other programs can't use your webcam neither?

Have you tried it on Windows, where it's supposed to work? Perhaps you have an hardware problem there...

---

### Post by swajime on 2010-06-15
It worked fine on windows XP.  I don't have windows XP anymore.

---

### Post by swajime on 2010-06-19
I had it working briefly, after thrashing around a bit with stuff like MAKEDEV.v4l.
Then I decided to unplug the usb cable and plug it back in with an extention.
That messed it all up again.

Here now, I've rebooted, then:

john@system76-pc:~$ tail -f /var/log/syslog &
john@system76-pc:~$ sudo modprobe -rv gspca_sq905
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/gspca_sq905.ko
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/gspca_main.ko
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/videodev.ko
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/v4l1-compat.ko
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/v4l2-compat-ioctl32.ko
Jun 19 11:54:12 system76-pc kernel: [  105.001300] usbcore: deregistering interface driver sq905
Jun 19 11:54:12 system76-pc kernel: [  105.001360] sq905: deregistered
Jun 19 11:54:12 system76-pc kernel: [  105.031289] gspca: main deregistered

john@system76-pc:~$ sudo modprobe -rv gssudo modprobe -v gspca_sq905
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/v4l2-compat-ioctl32.ko 
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/v4l1-compat.ko 
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/videodev.ko 
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/gspca_main.ko 
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/gspca_sq905.ko 
Jun 19 11:54:27 system76-pc kernel: [  120.179094] Linux video capture interface: v2.00
Jun 19 11:54:27 system76-pc kernel: [  120.182799] gspca: main v2.7.0 registered
Jun 19 11:54:27 system76-pc kernel: [  120.184754] gspca: probing 2770:9120
Jun 19 11:54:27 system76-pc kernel: [  120.193856] gspca: probe ok
Jun 19 11:54:27 system76-pc kernel: [  120.193885] usbcore: registered new interface driver sq905
Jun 19 11:54:27 system76-pc kernel: [  120.193889] sq905: registered

john@system76-pc:~$ xawtv &
[2] 2488
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.32-22-generic)
xinerama 0: 1920x1200+0+0
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0x9e7100 [PAL_M,NTSC_M,NTSC_M_JP,?,SECAM_D,SECAM_G,SECAM_H,SECAM_K,?ATSC_8_VSB]): Invalid argument
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument

Now -- the camera appears to be working ok, but the USB cable is too short for proper placement.
So ... I unplug the USB, insert an extention, and plug it back in.  I expect to have problems again.

john@system76-pc:~$ libv4l2: error dequeuing buf: No such device
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=MMAP): No such device
Jun 19 12:04:06 system76-pc kernel: [  698.981086] sq905: sq905_read_data: usb_control_msg failed (-71)
Jun 19 12:04:06 system76-pc kernel: [  698.982079] sq905: sq905_command: usb_control_msg failed (-71)
Jun 19 12:04:06 system76-pc kernel: [  699.040077] usb 3-2: USB disconnect, address 2
Jun 19 12:04:06 system76-pc kernel: [  699.040310] gspca: disconnect complete
Jun 19 12:04:12 system76-pc kernel: [  705.070016] usb 2-2: new full speed USB device using uhci_hcd and address 3
Jun 19 12:04:12 system76-pc kernel: [  705.243216] usb 2-2: configuration #1 chosen from 1 choice
Jun 19 12:04:12 system76-pc kernel: [  705.246140] gspca: probing 2770:9120
Jun 19 12:04:12 system76-pc kernel: [  705.740847] sq905: sq905_command: usb_control_msg failed (-110)
Jun 19 12:04:12 system76-pc kernel: [  705.740874] sq905: probe of 2-2:1.0 failed with error -110
Jun 19 12:04:12 system76-pc kernel: [  705.774842] usb 2-2: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 12 len 1 ret -71
Jun 19 12:04:12 system76-pc kernel: [  705.775823] usb 2-2: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 192 rq 12 len 1 ret -71
(last two lines repeat continuously ...)
(close xawtv window)

Now:

sudo modprobe -rv gspca_sq905
FATAL: Module gspca_sq905 is in use.
john@system76-pc:~$ libv4l2: error mmapping buffer 0: No such device
libv4l2: error reading: Input/output error
v4l2: read: Input/output error
sudo modprobe -rv gsxawtv &
[3] 2543
[2]   Done                    xawtv
john@system76-pc:~$ This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.32-22-generic)
xinerama 0: 1920x1200+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
sudo modprobe -rv gspca_sq905
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/gspca_sq905.ko
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/gspca_main.ko
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/videodev.ko
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/v4l1-compat.ko
rmmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/v4l2-compat-ioctl32.ko
[3]+  Exit 1                  xawtv
john@system76-pc:~$ Jun 19 12:05:25 system76-pc kernel: [  778.311324] usbcore: deregistering interface driver sq905
Jun 19 12:05:25 system76-pc kernel: [  778.311412] sq905: deregistered
Jun 19 12:05:25 system76-pc kernel: [  778.331281] gspca: main deregistered
sudo modprobe -rv gssudo modprobe -v gspca_sq905
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/v4l2-compat-ioctl32.ko 
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/v4l1-compat.ko 
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/videodev.ko 
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/gspca_main.ko 
insmod /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/gspca_sq905.ko 
john@system76-pc:~$ Jun 19 12:05:32 system76-pc kernel: [  785.224944] Linux video capture interface: v2.00
Jun 19 12:05:32 system76-pc kernel: [  785.226682] gspca: main v2.7.0 registered
Jun 19 12:05:32 system76-pc kernel: [  785.227559] gspca: probing 2770:9120
Jun 19 12:05:32 system76-pc kernel: [  785.229049] sq905: sq905_command: usb_control_msg failed (-71)
Jun 19 12:05:32 system76-pc kernel: [  785.229064] sq905: probe of 2-2:1.0 failed with error -71
Jun 19 12:05:32 system76-pc kernel: [  785.229098] usbcore: registered new interface driver sq905
Jun 19 12:05:32 system76-pc kernel: [  785.229103] sq905: registered
sudo modprobe -rv gsxawtv &
[2] 2561
john@system76-pc:~$ This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.32-22-generic)
xinerama 0: 1920x1200+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
Jun 19 12:06:08 system76-pc kernel: [  821.451759] ath5k phy0: unsupported jumbo
Jun 19 12:07:47 system76-pc kernel: [  920.499226] ath5k phy0: unsupported jumbo
Jun 19 12:09:01 system76-pc CRON[2571]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)

Any further efforts fail with the -71 until reboot.
The last time I tried this, the reboot gave me video that was garbled.
To try it again now, I'll need to reboot.  brb

---

### Post by swajime on 2010-06-19
After the reboot, now my video is messed up ... it looks like 5 tall skinny boxes are scrolling up the screen.  orange, blue, orange, blue, orange; followed by blue, orange, blue, orange, blue. Over and over again.

---

### Post by Pitxyoki on 2010-06-19
Pleeeeeeeeeeeease, use one terminal for tailing the syslog (without sending it to the background) and another one to enter the commands.
When you are testing it, don't unplug the camera when you are using it. Try to do it tidier:
0. plug the cam
1. modprobe commands;
2. xawtv, other programs
[B]3. exit xawtv, other programs
4. modprobe -rv
5. *THEN* unplug[/B]

modprobe loads and unload modules (analogous to Windows' device drivers). "modprobe" loads modules. "modprobe -r" unloads them. When trying modules that apparently give problems, always treat them as if they were made of glass. :)

Also, please use the forum's [code] blocks.



[EDIT]
> **swajime said:**
> After the reboot, now my video is messed up ... it looks like 5 tall skinny boxes are scrolling up the screen.  orange, blue, orange, blue, orange; followed by blue, orange, blue, orange, blue. Over and over again.

If you close the program and reopen it (without unplugging or removing the module), does that happen again? I remember sometimes having to retry opening programs two or three times (I haven't used the cam lately).
[/EDIT]

---

### Post by swajime on 2010-06-20
Thanks for your help :)

It's working right now, and I don't want to mess with it anymore, for fear it might stop working.

---

