---
title: "How to compile???"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by necronzero on 2008-06-17
I downloaded gutenprint-5.2.0-beta3 for my Cx6500 to work on Ubuntu, and i wanted to know how to install it. anyone?
Thanks in advance

---

### Post by the_doc on 2008-06-17
There should be a README with installation instructions.

---

### Post by bufsabre666 on 2008-06-17
for most instances its the basic

untar the file

cd [directory extracted to]

./configure

make

sudo make install

but differnt packages vary, the best bet is the search '"the package name" ubuntu' into google and youll get a better list on a per package basis ((most of the time))

---

### Post by Corrupt3d on 2008-06-17
Hi, 
I'm assuming you donwloaded the source and want to compile and install that.

First download your file to the desktop,
it should be something like this: [_gutenprint-5.2.0-beta3.tar.bz2_]("http://sourceforge.net/project/downloading.php?group_id=1537&use_mirror=voxel&filename=gutenprint-5.2.0-beta3.tar.bz2&14338409")  

$ bunzip2 gutenprint-5.2.0-beta3.tar.bz2 [COLOR="Red"]#unzips the file[/COLOR]
$ tar -xf gutenprint-5.2.0-beta3.tar [COLOR="Red"]# uncompress the tarball[/COLOR]
$ cd gutenprint-5.2.0-beta3 [COLOR="Red"]# switch into its folder[/COLOR]
$ ls [COLOR="Red"]# list files[/COLOR]

you should see a README file with instructions

$ cat README | less [COLOR="Red"]# looks at the requirements to compile it[/COLOR]

>>>Download any libraries it might need<<<

$ ./configure [COLOR="Red"]#creates a makefile and checks to make sure you have everything installed (look for any errors displayed)[/COLOR]

$make [COLOR="Red"]#compile[/COLOR]

$sudo make install [COLOR="Red"]# moves files into proper directories, done ^-^[/COLOR]

---

### Post by the_doc on 2008-06-17
Seriously I wasn't being sarcastic, there's a README with installation instructions included!

---

### Post by dnaga57 on 2008-06-17
> **Corrupt3d said:**
> Hi, 
I'm assuming you donwloaded the source and want to compile and install that.

First download your file to the desktop,
it should be something like this: [_gutenprint-5.2.0-beta3.tar.bz2_]("http://sourceforge.net/project/downloading.php?group_id=1537&use_mirror=voxel&filename=gutenprint-5.2.0-beta3.tar.bz2&14338409")  

$ bunzip2 gutenprint-5.2.0-beta3.tar.bz2 [COLOR="Red"]#unzips the file[/COLOR]
$ tar -xf gutenprint-5.2.0-beta3.tar [COLOR="Red"]# uncompress the tarball[/COLOR]
$ cd gutenprint-5.2.0-beta3 [COLOR="Red"]# switch into its folder[/COLOR]
$ ls [COLOR="Red"]# list files[/COLOR]

you should see a README file with instructions

$ cat README | less [COLOR="Red"]# looks at the requirements to compile it[/COLOR]

>>>Download any libraries it might need<<<

$ ./configure [COLOR="Red"]#creates a makefile and checks to make sure you have everything installed (look for any errors displayed)[/COLOR]

$make [COLOR="Red"]#compile[/COLOR]

$sudo make install [COLOR="Red"]# moves files into proper directories, done ^-^[/COLOR]

I have a Philips Fun cam. I downloaded the drivers from net on to desk top as you have said. When I try your method I get the following

[SIZE="5"]dnubuntu-laptop:~$ bunzip2 pwc-10.0.10.tar.bz2
bunzip2: Can't open input file pwc-10.0.10.tar.bz2: No such file or directory.
dnubuntu@dnubuntu-laptop:~$ tar -xf  pwc-10.0.10.tar.bz2
tar: pwc-10.0.10.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
dnubuntu@dnubuntu-laptop:~$ 
[/SIZE]

Please advise m,e where am I going wrong. Many thanks in advance

---

### Post by the_doc on 2008-06-17
Are you sure pwc-10.0.10.tar.bz2 is in your current working directory?

---

### Post by Duck2006 on 2008-06-17
If the file that you want to install is on the desktop, then cd to the desktop and do it from there.

cd ~/Desktop

---

### Post by dnaga57 on 2008-06-17
> **the_doc said:**
> Are you sure pwc-10.0.10.tar.bz2 is in your current working directory?

I frankly do not know what you are asking - newbee 15 days old, still learning.
I have downloaded the following files on to desktop just in case
pwc-10.0.10.tar.bz2
pwc-10.0.11.tar.bz2
pwc-10.0.12.tar.bz2
libpwc-20060101.tar.bz2

In all these cases when I try as in my post I get similar error messages.
Would be grateful for help, advise:confused:

---

### Post by the_doc on 2008-06-17
You need to follow the directions in post #8 namely,

cd ~/Desktop

and try it from there.

---

### Post by Titan8990 on 2008-06-17
I found this guide very useful when I first started with Linux: [How to Install ANYTHING in Ubuntu](http://monkeyblog.org/ubuntu/installing/)

---

### Post by dnaga57 on 2008-06-17
> **the_doc said:**
> You need to follow the directions in post #8 namely,

cd ~/Desktop

and try it from there.

I have reached this far & getting stuck as no Read me file. Also it dos not accept ./configure command
Pls help


[SIZE="3"]dnubuntu@dnubuntu-laptop:~$ bunzip2 pwc-10.0.11.tar.bz2
bunzip2: Can't open input file pwc-10.0.11.tar.bz2: No such file or directory.
dnubuntu@dnubuntu-laptop:~$ cd ~/Desktop
dnubuntu@dnubuntu-laptop:~/Desktop$  bunzip2 pwc-10.0.11.tar.bz2
dnubuntu@dnubuntu-laptop:~/Desktop$ tar -xf pwc-10.0.11.tar
dnubuntu@dnubuntu-laptop:~/Desktop$ cd pwc-10.0.11
dnubuntu@dnubuntu-laptop:~/Desktop/pwc-10.0.11$ ls
Makefile    pwc-dec23.c  pwc-ioctl.h  pwc-nala.h        pwc-uncompress.h
pwc-ctrl.c  pwc-dec23.h  pwc-kiara.c  pwc-timon.c       pwc-v4l.c
pwc-dec1.c  pwc.h        pwc-kiara.h  pwc-timon.h
pwc-dec1.h  pwc-if.c     pwc-misc.c   pwc-uncompress.c
dnubuntu@dnubuntu-laptop:~/Desktop/pwc-10.0.11$ ./configure
bash: ./configure: No such file or directory
dnubuntu@dnubuntu-laptop:~/Desktop/pwc-10.0.11$ 

[/SIZE]

---

### Post by the_doc on 2008-06-17
There doesn't seem to be a configure script.  Try this.

make
su root
make install

---

### Post by dnaga57 on 2008-06-17
Also I proceeded using cat command on Makefile.
I got the following

# Makefile for the Linux Philips USB Webcam driver
#
# NOTE: This make file can serve as both an external Makefile (launched
#       directly by the user), or as the sub-dir Makefile used by the kernel
#       build system.

# If CONFIG_USB_PWC isn't set, we'll assume the user want to build this driver h
as a module

ifndef CONFIG_USB_PWC
CONFIG_USB_PWC=m
# Comment the next line, if you don't want debug message and a smaller binary
CONFIG_PWC_DEBUG=y
endif

ifneq ($(KERNELRELEASE),)

pwc-objs        := pwc-if.o pwc-misc.o pwc-ctrl.o pwc-v4l.o pwc-uncompress.o
pwc-objs        += pwc-dec1.o pwc-dec23.o pwc-kiara.o pwc-timon.o

obj-$(CONFIG_USB_PWC) += pwc.o

:
EXTRA_CFLAGS=-Wall -DXAWTV_HAS_BEEN_FIXED=1

ifeq ($(CONFIG_PWC_DEBUG),y)
EXTRA_CFLAGS += -DCONFIG_PWC_DEBUG=1
else
EXTRA_CFLAGS += -DCONFIG_PWC_DEBUG=0
endif

else
KVER  := $(shell uname -r)
KLINK := $(shell test -e /lib/modules/${KVER}/source/ && echo source || echo build)
KSRC  := /lib/modules/$(KVER)/$(KLINK)
KMISC := /lib/modules/$(KVER)/kernel/drivers/usb/media
PWD := $(shell pwd)

# Fix some problem with suse < 9.2 and suse >= 9.2
is_suse := $(shell test -e /etc/SuSE-release && echo 1 || echo 0)
:
ifeq ($(is_suse_92_or_greater),1)
    KSRC := /lib/modules/$(KVER)/build
  endif
endif



all default:
        $(MAKE) -C $(KSRC) SUBDIRS=$(PWD) modules

install: default
        install -d $(KMISC)
        install -m 644 -c pwc.ko $(KMISC)
        -/sbin/depmod -a

uninstall:
        -rm -rf $(KMISC)/pwc.ko

endif

clean:
        rm -f *.[oas] .*.flags *.ko .*.cmd .*.d .*.tmp *.mod.c
        rm -rf .tmp_versions
:END


Now what do I do?
Sorry to bother you so much. I thank your patience

---

### Post by the_doc on 2008-06-17
make
su root
make install

See if that helps.

---

### Post by dnaga57 on 2008-06-17
> **the_doc said:**
> make
su root
make install

See if that helps.

I tried. The results are
dnubuntu@dnubuntu-laptop:~$ cd ~/Desktop
dnubuntu@dnubuntu-laptop:~/Desktop$ cd pwc.10.0.11
bash: cd: pwc.10.0.11: No such file or directory
dnubuntu@dnubuntu-laptop:~/Desktop$ pwc-10.0.11
bash: pwc-10.0.11: command not found
dnubuntu@dnubuntu-laptop:~/Desktop$ cd pwc-10.0.11
dnubuntu@dnubuntu-laptop:~/Desktop/pwc-10.0.11$ make
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/dnubuntu/Desktop/pwc-10.0.11 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.o
In file included from /home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:69:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc.h:28:26: error: linux/config.h: No such file or directory
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:164: error: variable ‘pwc_template’ has initializer but incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:165: error: unknown field ‘owner’ specified in initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:165: warning: excess elements in struct initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:165: warning: (near initialization for ‘pwc_template’)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:166: error: unknown field ‘name’ specified in initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:166: warning: excess elements in struct initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:166: warning: (near initialization for ‘pwc_template’)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:167: error: unknown field ‘type’ specified in initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:167: warning: excess elements in struct initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:167: warning: (near initialization for ‘pwc_template’)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:168: error: unknown field ‘hardware’ specified in initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:168: error: ‘VID_HARDWARE_PWC’ undeclared here (not in a function)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:168: warning: excess elements in struct initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:168: warning: (near initialization for ‘pwc_template’)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:169: error: unknown field ‘release’ specified in initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:169: error: ‘video_device_release’ undeclared here (not in a function)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:169: warning: excess elements in struct initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:169: warning: (near initialization for ‘pwc_template’)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:170: error: unknown field ‘fops’ specified in initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:170: warning: excess elements in struct initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:170: warning: (near initialization for ‘pwc_template’)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:171: error: unknown field ‘minor’ specified in initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:171: warning: excess elements in struct initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:171: warning: (near initialization for ‘pwc_template’)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_isoc_init’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:885: warning: assignment from incompatible pointer type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘cd_to_pwc’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:981: error: implicit declaration of function ‘to_video_device’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:981: warning: initialization makes pointer from integer without a cast
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:982: error: implicit declaration of function ‘video_get_drvdata’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:982: warning: return makes pointer from integer without a cast
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_create_sysfs_files’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1024: warning: initialization makes pointer from integer without a cast
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1026: error: implicit declaration of function ‘video_device_create_file’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_remove_sysfs_files’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1032: warning: initialization makes pointer from integer without a cast
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1034: error: implicit declaration of function ‘video_device_remove_file’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_video_open’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1074: error: implicit declaration of function ‘video_devdata’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1074: warning: initialization makes pointer from integer without a cast
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1079: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_video_close’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1187: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_video_read’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1247: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_video_poll’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1311: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_video_ioctl’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1327: error: implicit declaration of function ‘video_usercopy’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_video_mmap’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1340: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘usb_pwc_probe’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1648: error: implicit declaration of function ‘video_device_alloc’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1648: warning: assignment makes pointer from integer without a cast
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1655: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1655: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1655: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1656: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1657: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1658: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1659: error: implicit declaration of function ‘video_set_drvdata’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1682: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1683: error: implicit declaration of function ‘video_register_device’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1683: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1683: error: (Each undeclared identifier is reported only once
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1683: error: for each function it appears in.)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1686: error: implicit declaration of function ‘video_device_release’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1691: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘usb_pwc_disconnect’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1745: error: implicit declaration of function ‘video_unregister_device’
make[2]: *** [/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.o] Error 1
make[1]: *** [_module_/home/dnubuntu/Desktop/pwc-10.0.11] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2
dnubuntu@dnubuntu-laptop:~/Desktop/pwc-10.0.11$ su root
Password: 
su: Authentication failure
dnubuntu@dnubuntu-laptop:~/Desktop/pwc-10.0.11$ su root
Password: 
su: Authentication failure
dnubuntu@dnubuntu-laptop:~/Desktop/pwc-10.0.11$ make install
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/dnubuntu/Desktop/pwc-10.0.11 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.o
In file included from /home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:69:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc.h:28:26: error: linux/config.h: No such file or directory
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:164: error: variable ‘pwc_template’ has initializer but incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:165: error: unknown field ‘owner’ specified in initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:165: warning: excess elements in struct initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:165: warning: (near initialization for ‘pwc_template’)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:166: error: unknown field ‘name’ specified in initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:166: warning: excess elements in struct initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:166: warning: (near initialization for ‘pwc_template’)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:167: error: unknown field ‘type’ specified in initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:167: warning: excess elements in struct initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:167: warning: (near initialization for ‘pwc_template’)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:168: error: unknown field ‘hardware’ specified in initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:168: error: ‘VID_HARDWARE_PWC’ undeclared here (not in a function)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:168: warning: excess elements in struct initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:168: warning: (near initialization for ‘pwc_template’)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:169: error: unknown field ‘release’ specified in initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:169: error: ‘video_device_release’ undeclared here (not in a function)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:169: warning: excess elements in struct initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:169: warning: (near initialization for ‘pwc_template’)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:170: error: unknown field ‘fops’ specified in initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:170: warning: excess elements in struct initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:170: warning: (near initialization for ‘pwc_template’)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:171: error: unknown field ‘minor’ specified in initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:171: warning: excess elements in struct initializer
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:171: warning: (near initialization for ‘pwc_template’)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_isoc_init’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:885: warning: assignment from incompatible pointer type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘cd_to_pwc’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:981: error: implicit declaration of function ‘to_video_device’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:981: warning: initialization makes pointer from integer without a cast
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:982: error: implicit declaration of function ‘video_get_drvdata’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:982: warning: return makes pointer from integer without a cast
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_create_sysfs_files’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1024: warning: initialization makes pointer from integer without a cast
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1026: error: implicit declaration of function ‘video_device_create_file’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_remove_sysfs_files’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1032: warning: initialization makes pointer from integer without a cast
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1034: error: implicit declaration of function ‘video_device_remove_file’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_video_open’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1074: error: implicit declaration of function ‘video_devdata’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1074: warning: initialization makes pointer from integer without a cast
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1079: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_video_close’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1187: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_video_read’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1247: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_video_poll’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1311: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_video_ioctl’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1327: error: implicit declaration of function ‘video_usercopy’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘pwc_video_mmap’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1340: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘usb_pwc_probe’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1648: error: implicit declaration of function ‘video_device_alloc’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1648: warning: assignment makes pointer from integer without a cast
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1655: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1655: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1655: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1656: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1657: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1658: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1659: error: implicit declaration of function ‘video_set_drvdata’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1682: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1683: error: implicit declaration of function ‘video_register_device’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1683: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1683: error: (Each undeclared identifier is reported only once
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1683: error: for each function it appears in.)
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1686: error: implicit declaration of function ‘video_device_release’
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1691: error: dereferencing pointer to incomplete type
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c: In function ‘usb_pwc_disconnect’:
/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.c:1745: error: implicit declaration of function ‘video_unregister_device’
make[2]: *** [/home/dnubuntu/Desktop/pwc-10.0.11/pwc-if.o] Error 1
make[1]: *** [_module_/home/dnubuntu/Desktop/pwc-10.0.11] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
dnubuntu@dnubuntu-laptop:~/Desktop/pwc-10.0.11$ 

What to do?
Thanks for our patience again

---

### Post by cariboo on 2008-06-17
If you double click on any of those files a program called file-roller will open and you can extract the files to what ever directory you want. From there you can go into the directory just created and checkout the readme file it will tell you what to do next. If there are any terms you don't understand, the answer is just a couple of clicks away using Google.

Jim

---

### Post by dnaga57 on 2008-06-17
> **cariboo907 said:**
> If you double click on any of those files a program called file-roller will open and you can extract the files to what ever directory you want. From there you can go into the directory just created and checkout the readme file it will tell you what to do next. If there are any terms you don't understand, the answer is just a couple of clicks away using Google.

Jim

I tried on a file called libpwc. on cat Readme I giot this
libpwc - Small library for Philips Webcam Linux Driver
------------------------------------------------------

This is a small library used to decode the raw compressed stream send by the
linux pwc driver. Currently the library is only a wrapper aroung the linux
kernel code, but in the future we can write the decompressor using assembler or
a faster decoder.

I've made a small example how to decode the stream sent by the linux driver. In
the future, i'll produce a real example that grab and image, convert it, and
output in a known format.

Stream format
-------------

Currently the format return by the driver is not the raw format, but i've add a
small header (8 bytes), to help decoding it.

struct pwc_raw_frame {
   __le16 type;         /* type of the webcam (645, ..., 750)                   */
   __le16 vbandlength;  /* Size of 4lines compressed (used by the decompressor) */
:
What do I make of it?

---

### Post by the_doc on 2008-06-18
I think the pwc version that you are using is out of date and inludes code that references a deprecated header file (linux/config.h).

Try downloading the latest source from here, extract to your desktop (or wherever) and try again.

EDIT:

Link would be useful!

[http://packages.debian.org/stable/graphics/pwc-source](http://packages.debian.org/stable/graphics/pwc-source)

---

