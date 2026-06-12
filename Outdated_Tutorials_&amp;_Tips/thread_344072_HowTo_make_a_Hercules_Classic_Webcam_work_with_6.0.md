---
title: "HowTo make a Hercules Classic Webcam work with 6.06 Dapper (0v519 driver)"
date: 2007-01-22
forum: Outdated Tutorials &amp; Tips
---

### Post by gentle_turtle on 2007-01-22
It toook me quite a while to figure this one out, so I post how I did it:

 I tested this procedure on my server running the server 6.06 Ubuntu installation, integrated by the XUbuntu desktop...

The Hercules Classic Webcam is an el-chepo webcam incorporating 4LEDs for low lighting usage. "lsusb" sees the camera as "Omnivision Technologies, Inc". The drivers needed to make it work are the ov51x and ov519_decomp modules.

I assume in this description that your camera is seen on the USB bus, otherwise yo have to activate and make sure that USB works properly by activating the bus. You can find in this site enough descriptions on how to do that..

Once the cam is seen on the USB bus, the following procedure gives you a fuly functional cam on your Ubuntu 6.06 dapper machine:

1. Get the linux headers for your system, so that you can compile the drivers once you downloaded them. To do this, open a terminal window (Applications -> Terminal on XUbuntu) and type

sudo apt-get install build-essential linux-headers-`uname -r`

2. Get the modules for your webcam: 

wget [http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-0.5.4.tar.gz](http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-0.5.4.tar.gz)

Ensure the drivers landed into a directory you know ;-)

3. Move to the directory where your downloaded drivers are, and extract the source files from the tar files.

tar -xvf ov51x-jpeg-0.5.4.tar.gz

4. Change directory to where your sources are:

cd ov51x-jpeg-0.5.4

5. Compile and install the modules:

sudo make install

This will compile the  drivers and install them into the subdirectory of /lib/modules/your-linux-version called extra

6. If all went well, we can install the modules by hand now:

sudo modprobe videodev
sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

7. test your installation by using a camera viewing application, such as xawtv.

If all goes well, you will be able to see the output of your webcam in xawtv.

Now comes the tricky part: making such modules permanent, so that your machine recognizes the Hercules webcam both at bootup as well when you plug it in. The problem here with respect to other module installations is that for some obscure reason, the ov519_decomp module insists in loading the ov511 module when loading through modprobe, and ov511 knows nothing of some of the functions in ov519_decomp and therefore complains. 

We will thus load ov51x normally through modprobe, but we will load ov519_decomp through insmod. Let us look at the steps to do this:

1. Make sure you load the vidoedev and i2c_core modules at bootup: to do this, in the terminal type:

sudo vi /etc/modules

We use here vi, but you can actually substitute vi with any other text editor of your preference (I know, I am old and I used vi for decades ;-P). At the end of the files, add the following two lines:

videodev
i2c_core

Now save the file and quit the editor. This will guarantee that from now on at bootup the videodev and the i2c_core modules are loaded.

2. Tell Ubuntu what to do whenever it notices the camera is plugged in:

sudo touch /etc/modprobe.d/ov51x
sudo vi /etc/modprobe.d/ov51x

add to the file the following line: 

install ov51x /sbin/modprobe --ignore-install ov51x; insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

This has to be ONLY on one line.
Save the file and quit the editor.

And voila, at next rebbot your Hercules Classic webcam is there, ready to use.... Have fun!

---

### Post by total wormage on 2007-03-22
nice howto! :]]

there seems to be a new version of the modules which doesn't include ov519_decomp.ko or ov519-jpeg_decomp.ko or whatever, so my webcam doesn't get recognized after booting

installing the older version (the one in this howto) doesn't seem to work for me either...

i'm running ubuntu feisty on a 64 bit system

---

### Post by frederik.nnaji on 2007-10-12
i have a webcam classic from Hercules..

neither easycam nor easycam2 would help me install drivers for it.
who knows help?

---

### Post by frederik.nnaji on 2007-10-12
**here the output of my terminal while trying to do this with easycam2:**

root@x2:/# apt-get install easycam2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  easycam2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1040kB of archives.
After unpacking 0B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  easycam2
Install these packages without verification [y/N]? y
Get:1 [http://blognux.free.fr](http://blognux.free.fr) unstable/main easycam2 1.99-10c [1040kB]
Fetched 1040kB in 27s (38.2kB/s)                                                                                                                  
Selecting previously deselected package easycam2.
(Reading database ... 134053 files and directories currently installed.)
Unpacking easycam2 (from .../easycam2_1.99-10c_all.deb) ...
Setting up easycam2 (1.99-10c) ...
root@x2:/# lauchcam2

(easycam.py:8727): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ln: creating symbolic link `/lib/modules/2.6.22-14-generic/build/linux-headers-2.6.22-14-generic' to `/usr/src/linux-headers-2.6.22-14-generic': File exists
ERROR: Module ov518_decomp does not exist in /proc/modules
ERROR: Module ov51x does not exist in /proc/modules
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/kernel/drivers/usb/media-back': File exists
cp: cannot stat `/lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/*': No such file or directory
cd: 1: can't cd to /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/
mknod: `/dev/video0': File exists
mknod: `/dev/video1': File exists
ln: creating symbolic link `/dev/video' to `/dev/video0': File exists
make -C /lib/modules/2.6.22-14-generic/build M=/usr/share/EasyCam2/drivers/ov51x clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make -C /lib/modules/2.6.22-14-generic/build M=/usr/share/EasyCam2/drivers/ov51x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/share/EasyCam2/drivers/ov51x/ov51x.o
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:42:26: error: linux/config.h: No such file or directory
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:207: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:209: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:211: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:213: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:216: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:220: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:223: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:227: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:229: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:231: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:234: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:236: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:239: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:242: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:244: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:246: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:248: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:250: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:252: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:254: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:256: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:258: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:260: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:262: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:264: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:267: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:270: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:272: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:274: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:276: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:278: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:280: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:282: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:285: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:288: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:290: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:292: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:294: error: expected ‘)’ before string constant
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_init_isoc’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:5449: warning: assignment from incompatible pointer type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_v4l1_open’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:5705: warning: implicit declaration of function ‘video_devdata’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:5705: warning: initialization makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:5707: warning: implicit declaration of function ‘video_get_drvdata’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:5707: warning: initialization makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_v4l1_close’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:5784: warning: initialization makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_v4l1_ioctl_internal’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:5842: warning: initialization makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6246: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_v4l1_ioctl’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6358: warning: initialization makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6364: warning: implicit declaration of function ‘video_usercopy’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_v4l1_read’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6384: warning: initialization makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_v4l1_mmap’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6554: warning: initialization makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: At top level:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6625: error: variable ‘vdev_template’ has initializer but incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6626: error: unknown field ‘owner’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6626: warning: excess elements in struct initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6626: warning: (near initialization for ‘vdev_template’)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6627: error: unknown field ‘name’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6627: warning: excess elements in struct initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6627: warning: (near initialization for ‘vdev_template’)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6628: error: unknown field ‘type’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6628: warning: excess elements in struct initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6628: warning: (near initialization for ‘vdev_template’)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6629: error: unknown field ‘hardware’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6629: warning: excess elements in struct initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6629: warning: (near initialization for ‘vdev_template’)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6630: error: unknown field ‘fops’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6630: warning: excess elements in struct initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6630: warning: (near initialization for ‘vdev_template’)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6632: error: unknown field ‘release’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6632: error: ‘video_device_release’ undeclared here (not in a function)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6632: warning: excess elements in struct initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6632: warning: (near initialization for ‘vdev_template’)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6634: error: unknown field ‘minor’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6634: warning: excess elements in struct initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:6634: warning: (near initialization for ‘vdev_template’)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: In function ‘ov51x_probe’:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8298: warning: implicit declaration of function ‘video_device_alloc’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8298: warning: assignment makes pointer from integer without a cast
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8302: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8302: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8302: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8304: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8306: warning: implicit declaration of function ‘video_set_drvdata’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8314: warning: implicit declaration of function ‘video_register_device’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8314: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8314: error: (Each undeclared identifier is reported only once
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8314: error: for each function it appears in.)
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8321: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8331: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8354: error: dereferencing pointer to incomplete type
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8355: warning: implicit declaration of function ‘video_device_release’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8357: warning: implicit declaration of function ‘video_unregister_device’
/usr/share/EasyCam2/drivers/ov51x/ov51x.c: At top level:
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8464: error: unknown field ‘owner’ specified in initializer
/usr/share/EasyCam2/drivers/ov51x/ov51x.c:8464: warning: initialization from incompatible pointer type
make[2]: *** [/usr/share/EasyCam2/drivers/ov51x/ov51x.o] Error 1
make[1]: *** [_module_/usr/share/EasyCam2/drivers/ov51x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2

---

